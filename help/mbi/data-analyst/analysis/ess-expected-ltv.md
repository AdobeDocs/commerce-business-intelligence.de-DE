---
title: Analyse des erwarteten Lebenszeitwerts (LTV) (Standard)
description: Erfahren Sie, wie Sie Analysen erstellen, um den Lebenszeitwert Ihrer aktuellen Kunden zu verstehen und vorherzusagen, wie der Lebenszeitwert mit mehr Bestellungen zunimmt.
exl-id: e6f02cf6-f542-4768-969c-3ec998a7caa9
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Analyse des erwarteten Lebenszeitwerts

Die Vorhersage des Lebenszeitwerts von Kunden, wenn sie mehr Aufträge aufgeben, ist einer der wichtigsten Aspekte jedes Unternehmens jeder Größe.

Im Folgenden finden Sie die Schritte zum Erstellen von Analysen, um den Lebenszeitwert Ihrer aktuellen Kunden zu verstehen und vorherzusagen, wie der Lebenszeitwert mit mehr Bestellungen zunimmt.

![Erwarteter Lebenszeitwert](../../assets/expected_ltv_720.png)

## Erstellen einer Metrik

Der erste Schritt besteht darin, eine neue Metrik mit den folgenden Schritten zu erstellen:
* Navigieren Sie zu **[!UICONTROL Manage Data > Metrics]**
   * Anzeigen der vorhandenen **[!UICONTROL Avg lifetime revenue]**.

  >[!NOTE]
  >
  >Die Tabelle, in der diese Metrik erstellt wird (wahrscheinlich `customer_entity` oder `sales_order` je nach der Fähigkeit Ihres Geschäfts, einen Gast-Checkout zu akzeptieren).

   * Klicken Sie auf **[!UICONTROL Create New Metric]** und wählen Sie die Tabelle oben aus.
   * Diese Metrik führt einen **Median** für die `Customer's lifetime revenue` Spalte durch, sortiert nach `created_at`.
      * [!UICONTROL Filters]:
         * `Customers we count (Saved Filter Set)` (oder `Registered accounts we count`) hinzufügen

   * Benennen Sie die Metrik, z. B. `Median lifetime revenue`.

## Dashboard erstellen

Nachdem die Metrik erstellt wurde, können Sie **ein Dashboard erstellen** indem Sie Folgendes tun:
* Navigieren Sie zu **[!UICONTROL Dashboards > Dashboard Options > Create New Dashboard]**.
* Geben Sie dem Dashboard einen Namen wie `Expected LTV`.

* Hier können Sie alle Berichte erstellen und hinzufügen.

## Erstellen von Berichten

>[!NOTE]
>
>Am **[!UICONTROL Time Period:]** wird der Zeitraum für jeden Bericht als `All-time` aufgeführt. Sie können dies an Ihre Analyseanforderungen anpassen. Adobe empfiehlt, dass alle Berichte in diesem Dashboard denselben Zeitraum abdecken, z. B. `All time`, `Year-to-date` oder `Last 365 days`.

* **[!UICONTROL Average LTV (all)]**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
   * [!UICONTROL Time period]: `All time`
   * &#x200B;
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart Type]: `Number (scalar)`

* **[!UICONTROL Average LTV (customers / non-guest checkout)]**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
      * [!UICONTROL filters] hinzufügen:
         * [`A`] `Customer's group code` **ungleich** `Not Logged In`
         * [`B`] `Customer's lifetime number of orders` **größer als**`0`

   * [!UICONTROL Time period]: `All time`
   * &#x200B;
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart Type]: `Number (scalar)`

* **[!UICONTROL Average and Median LTV]**
   * `1`: `Avg lifetime revenue`
   * `2`: `Median lifetime revenue`
   * [!UICONTROL Time period]: `All time`
   * [!UICONTROL Interval]: `By Month`
   * &#x200B;
     [!UICONTROL Diagrammtyp]: `Line`
   * `Multiple Y-Axes` deaktivieren

* **LTV nach Lebenszeitanzahl der Bestellungen**
   * `1`: `Avg lifetime revenue`
   * `2`: `New customers`
   * [!UICONTROL Time period]: `All time`
   * &#x200B;
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Group by]: `Customer's lifetime number of orders`
   * &#x200B;
     [!UICONTROL Diagrammtyp]: `Line`

  >[!NOTE]
  >
  >Fügen Sie nicht alle Werte für `Customer's lifetime number of orders` hinzu. Schauen Sie sich stattdessen einen Punkt an, an dem die Anzahl der Neukunden eine geringe Anzahl erreicht, und fügen Sie manuell die lebenslange Anzahl der Bestellungen jedes Kunden zu diesem Punkt hinzu. Wenn beispielsweise 200 Kunden bei einer Bestellung, 75 bei zwei, 15 bei drei und 3 bei vier Kunden vorhanden sind, fügen Sie *1, 2 und 3* hinzu.

* Fügen Sie den vorhandenen [!UICONTROL Avg customer lifetime revenue by cohort] hinzu.

Nachdem Sie die Berichte erstellt haben, sehen Sie im Bild oben in diesem Thema nach, wie Sie die Berichte in Ihrem Dashboard organisieren können.
