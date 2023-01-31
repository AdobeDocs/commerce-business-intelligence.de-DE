---
title: Erwartete Lebenszeitwert-Analyse (Basis)
description: Erfahren Sie, wie Sie Analysen erstellen, um den Lebenszeitwert Ihrer aktuellen Kunden zu verstehen und vorherzusagen, wie der Lebenszeitwert mit mehr Bestellungen steigt.
exl-id: e6f02cf6-f542-4768-969c-3ec998a7caa9
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Erwartete Lebenszeitwertanalyse

Die Vorhersage des Lebenszeitwerts von Kunden, die mehr Bestellungen aufgeben, ist einer der wichtigsten Aspekte jedes Geschäfts jeder Größe.

Im Folgenden finden Sie die Schritte zum Erstellen von Analysen, um den Lebenszeitwert Ihrer aktuellen Kunden zu verstehen und vorherzusagen, wie der Lebenszeitwert mit mehr Bestellungen steigt:

![erwarteter Lebenszeitwert](../../assets/expected_ltv_720.png)

## Erstellen einer Metrik

Der erste Schritt besteht darin, eine neue Metrik mit den folgenden Schritten zu erstellen:
* Navigieren Sie zu **[!UICONTROL Manage Data > Metrics]**
   * Vorhandene anzeigen **[!UICONTROL Avg lifetime revenue]**.

   >[!NOTE]
   >
   >Die Tabelle, auf der diese Metrik erstellt wird (wahrscheinlich `customer_entity` oder `sales_order` abhängig von der Fähigkeit Ihres Stores, einen Gast-Checkout zu akzeptieren.)

   * Klicken **[!UICONTROL Create New Metric]** und wählen Sie die Tabelle oben aus.
   * Diese Metrik führt eine **Median** auf `Customer's lifetime revenue` Spalte, sortiert nach `created_at`.
      * [!UICONTROL Filters]:
         * Fügen Sie die `Customers we count (Saved Filter Set)` (oder `Registered accounts we count`)
   * Geben Sie der Metrik einen Namen, z. B. `Median lifetime revenue`.



## Dashboard erstellen

Nachdem die Metrik erstellt wurde, können Sie **Dashboard erstellen** indem Sie dies tun:
* Navigieren Sie zu **[!UICONTROL Dashboards > Dashboard Options > Create New Dashboard]**.
* Benennen Sie das Dashboard, z. B. `Expected LTV`.

* Hier werden wir alle Berichte erstellen und hinzufügen.

## Erstellen von Berichten

* Wenn Sie es noch nicht getan haben, checken Sie aus. [dieses Video](https://fast.wistia.net/embed/iframe/24zz7wmjrt) über die Verwendung von **[!UICONTROL Visual Report Builder] um Diagramme, Tabellen und skalare Werte zu erstellen.

>[!NOTE]
>
>on **[!UICONTROL Time Period:]** festgelegt ist, wird der Zeitraum für jeden Bericht als `All-time`. Sie können dies nach Ihren Analyseanforderungen ändern. Wir empfehlen, alle Berichte in diesem Dashboard für denselben Zeitraum abzudecken, z. B. `All time`, `Year-to-date`oder `Last 365 days`.

* **[!UICONTROL Average LTV (all)]**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
   * [!UICONTROL Time period]: `All time`
   * 
      [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart Type]: `Number (scalar)`

* **[!UICONTROL Average LTV (customers / non-guest checkout)]**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
      * Hinzufügen [!UICONTROL filters]:
         * [`A`] `Customer's group code` **Ungleich** `Not Logged In`
         * [`B`] `Customer's lifetime number of orders` **Größer als**`0`
   * [!UICONTROL Time period]: `All time`
   * 
      [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart Type]: `Number (scalar)`


* **[!UICONTROL Average and Median LTV]**
   * Metrik `1`: `Avg lifetime revenue`
   * Metrik `2`: `Median lifetime revenue`
   * [!UICONTROL Time period]: `All time`
   * [!UICONTROL Interval]: `By Month`
   * 
      [!UICONTROL Diagrammtyp]: `Line`
   * Deaktivieren `Multiple Y-Axes`

* **LTV nach Lebensdauer der Bestellungen**
   * Metrik `1`: `Avg lifetime revenue`
   * Metrik `2`: `New customers`
   * [!UICONTROL Time period]: `All time`
   * 
      [!UICONTROL Intervall]: `None`
   * [!UICONTROL Group by]: `Customer's lifetime number of orders`
   * 

      [!UICONTROL Diagrammtyp]: `Line`
   >[!NOTE]
   >
   >Fügen Sie nicht alle Werte für `Customer's lifetime number of orders`, sehen Sie sich stattdessen einen Punkt an, an dem die Anzahl neuer Kunden eine kleine Zahl erreicht, und fügen Sie manuell die Anzahl der Bestellwerte für die gesamte Lebensdauer jedes Kunden zu diesem Punkt hinzu. Wenn es beispielsweise 200 Kunden bei einer Bestellung gibt, 75 bei zwei, 15 bei drei und 3 bei vier, fügen Sie *1, 2 und 3*.

* Vorhandenen hinzufügen [!UICONTROL Avg customer lifetime revenue by cohort] Bericht.

Nachdem Sie die Berichte erstellt haben, erfahren Sie im Bild oben in diesem Thema, wie Sie die Berichte in Ihrem Dashboard organisieren können.
