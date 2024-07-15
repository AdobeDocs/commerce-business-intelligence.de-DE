---
title: Analyse zurückgegebener Bestellungen
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das eine detaillierte Analyse der Ergebnisse Ihres Stores bietet.
exl-id: 6a948561-45b7-4813-9661-ab42197ca5bd
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Zurückgegebene Bestellungen

In diesem Thema wird gezeigt, wie ein Dashboard eingerichtet wird, das eine detaillierte Analyse der Ergebnisse Ihres Stores bietet.

![](../../assets/detailed-returns-dboard.png)

Bevor Sie beginnen, müssen Sie ein [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) -Kunde sein und sicherstellen, dass Ihr Unternehmen die `enterprise\_rma` -Tabelle für die Rückgabe verwendet.

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Zu verfolgende Spalten

* Tabelle **`enterprise_rma`** oder **`rma`**
* **`entity_id`**
* **`status`**
* **`order_id`**
* **`customer_id`**
* **`date_requested`**

* Tabelle **`enterprise_rma_item_entity`** oder **`rma_item_entity`**
* **`entity_id`**
* **`rma_entity_id`**
* **`qty_returned`**
* **`status`**
* **`order_item_id`**
* **`product_name`**
* **`product_sku`**

Sets filtern, um sie zu erstellen

* **`enterprise_rma`** table
* Name des Filtersatzes: `Returns we count`
* Filtersatzlogik:
   * Platzhalter - Geben Sie Ihre benutzerdefinierte Logik hier ein

* **`enterprise_rma_item_entity`** table
* Name des Filtersatzes: `Returns items we count`
* Filtersatzlogik:
   * Platzhalter - Geben Sie Ihre benutzerdefinierte Logik hier ein

### Berechnete Spalten

Zu erstellende Spalten

* **`enterprise_rma`** table
* **`Order's created at`**
* Wählen Sie eine Definition aus: `Joined Column`
* [!UICONTROL Create Path]:
* 
  [!UICONTROL Many]: `enterprise_rma.order_id`
* 
  [!UICONTROL One]: `sales_flat_order.entity_id`

* Wählen Sie einen [!UICONTROL table]: `sales_flat_order`
* Wählen Sie einen [!UICONTROL column]: `created_at`
   * `enterprise_rma.order_id = sales_flat_order.entity_id`

* **`Customer's order number`**
* Wählen Sie eine Definition aus: `Joined Column`
* Wählen Sie einen [!UICONTROL table]: `sales_flat_order`
* Wählen Sie einen [!UICONTROL column]: `Customer's order number`
   * `enterprise_rma.order_id = sales_flat_order.entity_id`

* **`Time between order's created_at and date_requested`** wird von einem Analysten im Rahmen Ihres `[RETURNS ANALYSIS]`-Tickets erstellt

* **`enterprise_rma_item_entity`** table
* **`return_date_requested`**
* Wählen Sie eine Definition aus: `Joined Column`
* [!UICONTROL Create Path]:
   * 
     [!UICONTROL Many]: `enterprise_rma_item_entity.rma_entity_id`
   * 
     [!UICONTROL One]: `enterprise_rma.entity_id`

* Wählen Sie einen [!UICONTROL table]: `enterprise_rma`
* Wählen Sie einen [!UICONTROL column]: `date_requested`
   * `enterprise_rma_item_entity.rma_entity_id = enterprise_rma.entity_id`

* **`Return item total value (qty_returned * price)`** wird von einem Analysten im Rahmen Ihres `[RETURNS ANALYSIS]`-Tickets erstellt

* **`sales_flat_order`** table
* **`Order contains a return? (1=yes/0=No)`**
* Wählen Sie eine Definition aus: `Exists`
* Wählen Sie einen [!UICONTROL table]: `enterprise_rma`
   * `enterprise_rma.order_id = sales_flat_order.entity_id`

* **`Customer's previous order number`** wird von einem Analysten im Rahmen Ihres `[RETURNS ANALYSIS]`-Tickets erstellt
* **`Customer's previous order contains return? (1=yes/0=no)`** wird von einem Analysten im Rahmen Ihres `[RETURNS ANALYSIS]`-Tickets erstellt

>[!NOTE]
>
>Wenn Sie nur Geschäftszeiten für die Auflösung in Sekunden oder die erste Antwort in Sekunden analysieren möchten, teilen Sie dies dem Analysten bei der Anforderung des Tickets mit.

### Metriken

* **Gibt** zurück
* In der Tabelle **`enterprise_rma`**
* Diese Metrik führt eine **Zählung** aus
* In der Spalte **`entity_id`**
* Bestellt von der **`date_requested`**
* [!UICONTROL Filter]: `Returns we count`

* **Zurückgegebene Elemente**
* In der Tabelle **`enterprise_rma_item_entity`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`qty_approved`**
* Bestellt von der **`return date_requested`**
* [!UICONTROL Filter]: `Returns we count`

* **Gesamtwert des zurückgegebenen Elements**
* In der Tabelle **`enterprise_rma_item_entity`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`Returned item total value (qty_returned * price)`**
* Bestellt von der **`return date_requested`**
* [!UICONTROL Filter]: `Returns we count`

* **Durchschnittliche Zeit zwischen Bestellung und Rückgabe**
* In der Tabelle **`enterprise_rma`**
* Diese Metrik führt einen **Durchschnitt** aus
* In der Spalte **`Time between order's created_at and date_requested`**
* Bestellt von der **`date_requested`**
* [!UICONTROL Filter]: `Returns we count`

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

### Berichte

* **Wiederholungsreihenwahrscheinlichkeit nach einer Rückgabe**
* Metrik `A`: `Number of orders with returns`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Order contains a return? (1=yes/0=No) = 1`
   * `Is in current month? = No`

* Metrik `B`: `Non-last orders with returns`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Is customer's last order? (1=yes/0=no) = 0`
   * `Order contains a return? (1=yes/0=No) = 1`

* Formel: Wiederholungsreihenwahrscheinlichkeit
* [!UICONTROL Formula]: `B / A`
* 
  [!UICONTROL Format]: `Percentage`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's order number`
* 
  [!UICONTROL Diagrammtyp]: `Bar`

* **Durchschnittliche Zeit bis zur Rückgabe (alle Zeit)**
* Metrik `A`: `Avg time between order and return`
* [!UICONTROL Metric]: `Avg time between order and return`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Number`

* **Prozentsatz der Bestellungen mit Rückgabe**
* Metrik `A`: `Number of orders`
* [!UICONTROL Metric]: `Number of orders`

* Metrik `B`: `Orders w/ return`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Order contains a return? (1=yes/0=No) = 1`

* Formel: % der Bestellungen mit Rückgabe
* [!UICONTROL Formula]: `B / A`
* 
  [!UICONTROL Format]: `Percentage`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Chart Type]: `Number - % of orders with return`

* **Nach Monat zurückgegebener Umsatz**
* Metrik `A`: `Returned item total value`
* [!UICONTROL Metric]: `Returned item total value`

* [!UICONTROL Time period]: `All time`
* [!UICONTROL Interval]: `By month`
* 
  [!UICONTROL Diagrammtyp]: `Line`

* **Kunden, die eine Rückgabe getätigt und nicht erneut gekauft haben**
* Metrik `A`: `Number of orders with returns`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Order contains a return? (1=yes/0=No) = 1`
   * `Is customer's last order? (1=yes/0=no) = 1`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Gruppe von]: `Customer_email`
* 
  [!UICONTROL Diagrammtyp]: `Table`

* **Rückkehrrate nach Element**
* Metrik `A`: `Returned items` (Ausblenden)
* [!UICONTROL Metric]: Zurückgegebene Elemente

* Metrik `B`: `Items sold` (Ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:

* [!UICONTROL Formula]: `Return %`
* [!UICONTROL Formula]: `B / A`
* 
  [!UICONTROL Format]: `Percentage`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `product_sku AND/OR product_name`
* 
  [!UICONTROL Diagrammtyp]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.

Wenn Sie beim Erstellen dieser Analyse Fragen haben oder das Professional Services-Team kontaktieren möchten, wenden Sie sich an den Support [.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)
