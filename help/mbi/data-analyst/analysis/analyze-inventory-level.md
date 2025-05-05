---
title: Analysieren von Lagerbeständen
description: Erfahren Sie, wie Sie Lagerbestände analysieren.
exl-id: 620156c5-7bea-4b36-84c7-e0cb4b5cc8be
role: Admin, Data Architect, Data Engineer, User
feature: Dashboards, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Lagerbestände analysieren

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Einblicke in Ihr aktuelles Inventar bietet und Anweisungen für Clients sowohl zur alten als auch zur neuen Architektur enthält. Sie befinden sich auf der alten Architektur, wenn die Option **[!UICONTROL Data Warehouse Views]** nicht im Menü **[!UICONTROL Manage Data]** vorhanden ist. Wenn Sie die veraltete Architektur verwenden, senden Sie eine [neue Support-Anfrage](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) mit dem Betreff **[!UICONTROL INVENTORY ANALYSIS]**, sobald Sie den entsprechenden Abschnitt in den Anweisungen unter _Berechnete Spalten_ erreicht haben.

## Nachzuverfolgende Spalten:

### Spalten zum Nachverfolgen von Anweisungen

* **[!UICONTROL cataloginventory_stock_item]**:
   * **`item_id`**
   * **`product_id`**
   * **`qty`**

* **[!UICONTROL catalog_product_entity]**:
   * **`entity_id`**
   * **`sku`**
   * **`created_at`**

## Berechnete Spalten:

+++ Neue Architektur

* **[!UICONTROL catalog_product_entity]**:
   * **`Product's most recent order date`**
      * [!UICONTROL Column type]: `Many to One`
      * &#x200B;

        [!UICONTROL Column equation]: `MAX`
      * [!UICONTROL Path]: `sales_order_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `created_at`
      * [!UICONTROL Filters]:
         * [A] `Ordered products we count`

   * **`Product's first order date`**
      * [!UICONTROL Column type]: `Many to One`
      * &#x200B;

        [!UICONTROL Column equation]: `MIN`
      * [!UICONTROL Path]: `sales_order_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `created_at`
      * [!UICONTROL Filters]:
         * [A] `Ordered products we count`

   * **`Seconds since product's most recent order date`**
      * [!UICONTROL Column type]: `Same Table`
      * &#x200B;

        [!UICONTROL Column equation]: `AGE`
      * [!UICONTROL DATETIME column] auswählen: `Product's most recent order date`

   * **`Product's lifetime number of items sold`**
      * [!UICONTROL Column type]: `Many to One`
      * &#x200B;

        [!UICONTROL Column equation]: `SUM`
      * [!UICONTROL Path]: `sales_order_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `qty_ordered`
      * [!UICONTROL Filters]:
         * [A] `Ordered products we count`

   * **`Avg products sold per week (all time)`**
      * [!UICONTROL Column type]: `Same Table`
      * &#x200B;

        [!UICONTROL Column equation]: `CALCULATION`
      * [!UICONTROL Column] Eingaben:
         * A: `Product's lifetime number of items sold`
         * B: `Product's first order date`
      * &#x200B;

        [!UICONTROL Datatype]: `Decimal`
      * Definition:
         * Fall, wenn A null ist oder B null ist, dann wird null else round(A::decimal/(extract(Epoch from (current_timestamp - B))::decimal/604800.0),2) end

* **[!UICONTROL cataloginventory_stock_item]**:
   * **`Sku`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `sku`

   * **`Product's lifetime number of items sold`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `Product's lifetime number of items sold`

   * **`Seconds since product's most recent order date`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `Seconds since product's most recent order date`

   * **`Avg products sold per week (all time)`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `Avg products sold per week (all time)`

   * **`Weeks on hand`**
      * [!UICONTROL Column type]: `Same Table`
      * &#x200B;

        [!UICONTROL Column equation]: `CALCULATION`
      * [!UICONTROL Column] Eingaben:
         * A: `qty`
         * B: `Avg products sold per week (all time)`
      * &#x200B;

        [!UICONTROL Datatype]: `Decimal`
      * Definition:
         * Fall, wenn A null ist oder B null ist oder B = 0,0, dann wird null else round(A::decimal/B,2) end

+++
+++ Alte Architektur

* **[!UICONTROL catalog_product_entity]**:
   * **`Product's most recent order date`**
      * [!UICONTROL Column type]: `Many to One`
      * &#x200B;

        [!UICONTROL Column equation]: `MAX`
      * [!UICONTROL Path]: `sales_order_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `created_at`
      * [!UICONTROL Filters]:
         * [A] `Ordered products we count`

   * **`Product's first order date`**
      * [!UICONTROL Column type]: `Many to One`
      * &#x200B;

        [!UICONTROL Column equation]: `MIN`
      * [!UICONTROL Path]: `sales_order_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `created_at`
      * [!UICONTROL Filters]:
         * [A] `Ordered products we count`

   * **`Seconds since product's most recent order date`**
      * [!UICONTROL Column type]: `Same Table`
      * &#x200B;

        [!UICONTROL Column equation]: `AGE`
      * Select DATETIME column: **`Product's most recent order date`**

   * **`Product's lifetime number of items sold`**
      * [!UICONTROL Column type]: `Many to One`
      * &#x200B;

        [!UICONTROL Column equation]: `SUM`
      * [!UICONTROL Path]: **`sales_order_item.product_id => catalog_product_entity.entity_id`**
      * [!UICONTROL column] auswählen: **`qty_ordered`**
      * [!UICONTROL Filters]:
         * [A] `Ordered products we count`

   * **`Avg products sold per week (all time)`**
      * Wird von einem Analyst erstellt, wenn Sie Ihre Support-Anfrage **[INVENTARANALYSE]** einreichen

* **[!UICONTROL cataloginventory_stock_item]**:
   * **`Sku`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `sku`

   * **`Product's lifetime number of items sold`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `Product's lifetime number of items sold`

   * **`Seconds since product's most recent order date`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `Seconds since product's most recent order date`

   * **`Avg products sold per week (all time)`**
      * [!UICONTROL Column type]: `One to Many`
      * &#x200B;

        [!UICONTROL Column equation]: `JOINED_COLUMN`
      * [!UICONTROL Path]: `cataloginventory_stock_item.product_id => catalog_product_entity.entity_id`
      * [!UICONTROL column] auswählen: `Avg products sold per week (all time)`

   * **`Weeks on hand`**
      * Wird von einem Analyst erstellt, wenn Sie Ihre **[!UICONTROL INVENTORY ANALYSIS]** Support-Anfrage einreichen

+++

## Metriken

### Anweisungen zu Metriken

* **[!UICONTROL cataloginventory_stock_item]**:
   * **`Inventory on hand`**: Diese Metrik führt eine
      * **Summe** auf dem
      * **`qty`** Spalte sortiert nach
      * [Keine] Spalte

## Berichte

### Berichtsanweisungen

* **`Inventory on hand by sku`**
   * [!UICONTROL Metric]: `Inventory on hand`
   * [!UICONTROL Time period]: `All time`
   * Zeitintervall: `None`
   * [!UICONTROL Group by]:
      * `Sku`
      * `Weeks on hand`
   * &#x200B;

     [!UICONTROL Chart type]: `Table`

* **`Inventory with less than 2 weeks on hand (order now)`**
   * [!UICONTROL Metric]: `Inventory on hand`
      * [!UICONTROL Filters]:
         * [A] `Weeks on hand` `< 2`

   * [!UICONTROL Time period]: `All time`
   * Zeitintervall: `None`
   * &#x200B;

     [!UICONTROL Gruppieren nach]: `Sku`
   * &#x200B;

     [!UICONTROL Chart type]: `Table`

* **`Inventory with more than 26 weeks on hand (put on sale)`**
   * [!UICONTROL Metric]: `Inventory on hand`
      * [!UICONTROL Filters]:
         * [A] `Weeks on hand` `> 26`

   * [!UICONTROL Time period]: `All time`
   * Zeitintervall: `None`
   * &#x200B;

     [!UICONTROL Gruppieren nach]: `Sku`
   * &#x200B;

     [!UICONTROL Chart type]: `Table`

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [ sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
