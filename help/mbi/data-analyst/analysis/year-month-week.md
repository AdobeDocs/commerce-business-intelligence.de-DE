---
title: Jährliche, monatliche und wöchentliche Berichte
description: Erfahren Sie, wie Sie Trends im Zeitverlauf einfach erkennen und die Perspektive für Zeiträume ändern können, die Sie vergleichen möchten.
exl-id: 74cf11c3-7ce0-477f-9a28-9d782e5da3d9
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# Berichterstellung über Zeiträume

>[!NOTE]
>
>Dieser Artikel enthält Anweisungen für Clients, die die ursprüngliche Architektur und die neue Architektur verwenden. Sie befinden sich auf der [neue Architektur](../../administrator/account-management/new-architecture.md) Wenn Sie über _Data Warehouse-Ansichten_ -Bereich nach Auswahl `Manage Data` aus der Hauptsymbolleiste.

Mit ReportBuilder können Sie Trends im Zeitverlauf einfach anzeigen und die Perspektive für Zeiträume ändern, die Sie vergleichen möchten. Dieser Artikel zeigt, wie Sie ein Dashboard einrichten, das eine Ebene tiefer geht und es Ihnen ermöglicht, Berichte für die Analyse von Woche zu Woche, Monat zu Monat und Jahr zu Jahr zu erstellen.

![](../../assets/Wow__mom__yoy.png)

Bevor Sie beginnen, möchten Sie sich mit Perspektiven im Detail vertraut machen [here](../../tutorials/using-visual-report-builder.md) und unabhängige Zeitoptionen [here](../../tutorials/time-options-visual-rpt-bldr.md).

Diese Analyse enthält [Erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Berechnete Spalten

* **`Sales_flat_order`** table
* **Originalarchitektur:** Die folgenden Spalten werden von einem Analytiker im Rahmen Ihrer `[YoY WoW MoM ANALYSIS]` Ticket
* `created_at (month-day)`
* `created_at (month)`
* `created_at (day of the month)`
* `created_at (day of the week)`
* `created_at (hour of the day)`

* **Neue Architektur:** Unten aufgeführte SQL mit einem Foto eines Beispiels für die Erstellung dieser Berechnung
   * `created_at (month-day)` [!UICONTROL Calculation]: **to_char(A, &#39;mm-dd&#39;)**
   * `created_at (month)` [!UICONTROL Calculation]: **to_char(A, &#39;mm-month&#39;)**
   * `created_at (day of the month)`&lt; [!UICONTROL Calculation]: **to_char(A, &#39;dd&#39;)**
   * `created_at (day of the week)` [!UICONTROL Calculation]: **to_char(A, &#39;d-Day&#39;)**
   * **`created_at (hour of the day)` [!UICONTROL Calculation]: **to_char(A, &#39;hh24&#39;)**

      ![](../../assets/new-arch-create-calc.png)

## Metriken

Keine.

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

## Berichte

* **YoY-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Time options]: `Time range (Custom)`: `2 years ago to 1 year ago`

   * [!UICONTROL Show top/bottom]: Top 100 % sortiert nach **`created_at (month-day)`***

* Metrik `A`: `This year`
* Metrik `B`: `Last year`
* [!UICONTROL Time period]: `1 year ago to 0 years ago`
* 
   [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `created_at (month-day)`
* 
   [!UICONTROL Chart Type]: `Line`

* **MoM-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * Zeitoptionen: `Time range (Custom)`: `2 months ago to 1 month ago`

   * Oben/unten anzeigen: Top 100 % sortiert nach **`created_at (day of month)`***

* Metrik `A`: Dieser Monat*
* Metrik `B`: Letzter Monat*
* [!UICONTROL Time period]: vor einem Monat vor 0 Monaten
* 
   [!UICONTROL Interval]: None
* [!UICONTROL Group by]: `created_at (day of month)`
* 
   [!UICONTROL Chart Type]: Line

* **WoW-Grafik**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Time options]: `Time range (Custom)`: `2 weeks ago to 1 week ago`

   * [!UICONTROL Show top/bottom]: Top 100 % sortiert nach `created_at (day of week)`

* Metrik `A`: `This week`
* Metrik `B`: `Last week`
* [!UICONTROL Time period]: `1 week ago to 0 weeks ago`
* 
   [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `created_at (day of week)`
* 
   [!UICONTROL Chart Type]: `Line`

* **DoD-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Time options]: `Time range (Custom)`: `2 days ago to 1 day ago`

   * [!UICONTROL Show top/bottom]: Top 100 % sortiert nach `created_at (hour of day)`

* Metrik `A`: `Today`
* Metrik B: `Yesterday`
* [!UICONTROL Time period]: `1 day ago to 0 days ago`
* 
   [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `created_at (hour of day)`
* 
   [!UICONTROL Chart Type]: `Line`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das Bild oben auf dieser Seite aussehen.
