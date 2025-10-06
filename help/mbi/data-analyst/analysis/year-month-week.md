---
title: Jährliche, monatliche und wöchentliche Berichte
description: Erfahren Sie, wie Sie Trends im Zeitverlauf einfach erkennen und die Perspektive für Zeiträume ändern können, die Sie vergleichen möchten.
exl-id: 74cf11c3-7ce0-477f-9a28-9d782e5da3d9
role: Admin, Data Architect, Data Engineer, Leader, User
feature: Reports, Dashboards
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Reporting über Zeiträume

>[!NOTE]
>
>Dieses Thema enthält Anweisungen für Clients, die die ursprüngliche und die neue Architektur verwenden. Sie befinden sich auf der [neuen Architektur](../../administrator/account-management/new-architecture.md), wenn der Abschnitt [!DNL _Data Warehouse-_] verfügbar ist, nachdem Sie [!DNL Manage Data] in der Hauptsymbolleiste ausgewählt haben.

Mit Report Builder können Sie Trends im Zeitverlauf leicht erkennen und die Perspektive für Zeiträume ändern, die Sie vergleichen möchten. In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, um eine tiefere Ebene zu betreten und Berichte für die Analyse von Woche zu Woche, von Monat zu Monat und von Jahr zu Jahr zu erstellen.

![Dashboard zeigt Vergleiche von Woche zu Woche, von Monat zu Monat und von Jahr zu Jahr an](../../assets/Wow__mom__yoy.png)

Bevor Sie anfangen, sollten Sie Perspektiven detaillierter erkunden [hier](../../tutorials/using-visual-report-builder.md) und unabhängige Zeitoptionen [hier](../../tutorials/time-options-visual-rpt-bldr.md).

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Berechnete Spalten

* **`Sales_flat_order`**
* **Ursprüngliche Architektur:** Die folgenden Spalten werden von einem Analyst als Teil Ihres `[YoY WoW MoM ANALYSIS]`-Tickets erstellt
* `created_at (month-day)`
* `created_at (month)`
* `created_at (day of the month)`
* `created_at (day of the week)`
* `created_at (hour of the day)`

* **Neue Architektur:** unten aufgeführte SQL mit einem Foto eines Beispiels zur Erstellung dieser Berechnung
   * `created_at (month-day)` [!UICONTROL Calculation]: **to_char(A, &#39;mm-dd&#39;)**
   * `created_at (month)` [!UICONTROL Calculation]: **to_char(A, &#39;mm-month&#39;)**
   * `created_at (day of the month)`&lt; [!UICONTROL Calculation]: **to_char(A, &#39;dd&#39;)**
   * `created_at (day of the week)` [!UICONTROL Calculation]: **to_char(A, &#39;d-Day&#39;)**
   * **`created_at (hour of the day)` [!UICONTROL Calculation]: &#x200B;** to_char(A, &#39;hh24&#39;)**
     ![Erstellen der Benutzeroberfläche für berechnete Spalten in Data Warehouse Manager](../../assets/new-arch-create-calc.png)

## Metriken

Keine.

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **YoY-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Time options]: `Time range (Custom)`: `2 years ago to 1 year ago`

   * [!UICONTROL Show top/bottom]: Top 100% sortiert nach **`created_at (month-day)`***

* `A`: `This year`
* `B`: `Last year`
* [!UICONTROL Time period]: `1 year ago to 0 years ago`
* &#x200B;
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `created_at (month-day)`
* &#x200B;
  [!UICONTROL Chart Type]: `Line`

* **MoM-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * Zeitoptionen: `Time range (Custom)`: `2 months ago to 1 month ago`

   * Oben/Unten anzeigen: Top 100% sortiert nach **`created_at (day of month)`***

* `A`: Diesen Monat*
* `B`: Letzter Monat*
* [!UICONTROL Time period]: Vor einem Monat bis vor 0 Monaten
* &#x200B;
  [!UICONTROL Interval]: None
* [!UICONTROL Group by]: `created_at (day of month)`
* &#x200B;
  [!UICONTROL Chart Type]: Line

* **WoW-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Time options]: `Time range (Custom)`: `2 weeks ago to 1 week ago`

   * [!UICONTROL Show top/bottom]: Top 100% sortiert nach `created_at (day of week)`

* `A`: `This week`
* `B`: `Last week`
* [!UICONTROL Time period]: `1 week ago to 0 weeks ago`
* &#x200B;
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `created_at (day of week)`
* &#x200B;
  [!UICONTROL Chart Type]: `Line`

* **DoD-Diagramm**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Time options]: `Time range (Custom)`: `2 days ago to 1 day ago`

   * [!UICONTROL Show top/bottom]: Top 100% sortiert nach `created_at (hour of day)`

* `A`: `Today`
* Metrik B: `Yesterday`
* [!UICONTROL Time period]: `1 day ago to 0 days ago`
* &#x200B;
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `created_at (hour of day)`
* &#x200B;
  [!UICONTROL Chart Type]: `Line`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis könnte wie das Bild oben auf dieser Seite aussehen.
