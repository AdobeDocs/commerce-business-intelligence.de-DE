---
title: Tracking von Zielen mit Metriken
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können, einschließlich Umsatz, neu registrierten Benutzern und Bestellungen im Laufe der Zeit.
exl-id: 9d621f40-f9c2-4310-bd96-a46ab7159930
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Tracking von Zielen mit Leistungsmetriken

Die meisten Kunden möchten ihre **Geschäftsziele**, aber nicht erkennen, dass dies möglich ist in [!DNL Adobe Commerce Intelligence]. In diesem Thema erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können - einschließlich Umsatz, neu registrierten Benutzern und Bestellungen im Zeitverlauf. Außerdem erfahren Sie, wie Sie die Leistung von Jahr zu Jahr in einem Dashboard wie folgt vergleichen:

![](../../assets/Goals-_dashboard_2.png)

Bevor Sie beginnen, sollten Sie die [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und stellen Sie sicher, dass Sie Ihre Geschäftsziele für einen bestimmten Zeitraum definiert haben.

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die bestimmte tägliche/monatliche/vierteljährliche Ziele für Ihr Unternehmen enthält.

Sie können die [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild, um Ihre Datei zu formatieren. Die gängigsten Ziele, die Kunden in verfolgen [!DNL Commerce Intelligence] umfassen Bestellungen, Umsatz und neue registrierte Konten.

![](../../assets/Goals-_Excel.png)

## Metriken

Erstellen Sie für jedes Ziel eine neue Metrik. Wenn Sie beispielsweise monatliche Umsatz- und Bestellziele hochladen, müssen Sie zwei neue Metriken erstellen:

* **Monatliches Umsatzziel**
* Im **`Monthly goals`** table
* Diese Metrik führt eine **Summe**
* Im **`Revenue target`** column
* Bestellt von der **`Month`** timestamp

* **Monatliches Bestellziel**
* Im **`Monthly goals`** table
* Diese Metrik führt eine **Summe**
* Im **`Orders target`** column
* Bestellt von der **`Month`** timestamp

* **Monatliches Ziel neuer registrierter Konten**
* Im **`Monthly goals`** table
* Diese Metrik führt eine **Summe**
* Im **`New registered accounts target`** column
* Bestellt von der **`Month`** timestamp

## Berichte

Es ist hilfreich, bei der Analyse Ihrer Ziele eine Mischung aus statischen Werten und visuellen Diagrammen zu verwenden. Im Folgenden finden Sie drei Beispielberichte, mit denen Sie Ihre Umsatzleistung verfolgen können.

* **Erzielter Umsatz**
* Metrik `A`: `Revenue`
* 
  [!UICONTROL Metrik]: `Revenue`

* Metrik `B`: `Target Revenue`
* [!UICONTROL Metric]: `Monthly Revenue Target`

* [!UICONTROL Formula]: `Revenue left to achieve target`
* 
  [!UICONTROL Formel]: `(B-A)`
* 
  [!UICONTROL Format]: `Number`

* [!UICONTROL Time period]: (Welchen relevanten Zeitraum Sie wünschen)
* 
  [!UICONTROL Interval]: `Month`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Umsatzziele**
* Metrik `A`: `Revenue`
* 
  [!UICONTROL Metrik]: `Revenue`

* Metrik `B`: `Target Revenue`
* [!UICONTROL Metric]: `Monthly Revenue Target`

* Metrik `C`: `Revenue (amount change since previous year)` (ausblenden)
* 
  [!UICONTROL Metrik]: `Revenue`
* [!UICONTROL Perspective]: `Amount change vs. Previous year`

* [!UICONTROL Formula]: (Dieser Monat letztes Jahr)
* 
  [!UICONTROL Formel]: `(A-C)`
* 
  [!UICONTROL Format]: `Currency`

* Ausschalten `Multiple Y-Axes`
* [!UICONTROL Time period]: (Welchen relevanten Zeitraum Sie wünschen)*
* 
  [!UICONTROL Interval]: `Month`
* [!UICONTROL Chart Type]: `Line Chart`

Nachdem Sie die oben genannten Berichte für Umsatzziele abgeschlossen haben, können Sie identische Berichte für Ziele in Bezug auf Bestellungen, registrierte Konten oder andere Werte erstellen, die Sie in den Upload der Zieldatei aufgenommen haben.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das Bild oben auf dieser Seite aussehen.
