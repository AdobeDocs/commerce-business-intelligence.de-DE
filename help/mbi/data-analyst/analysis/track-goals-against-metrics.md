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

Die meisten Kunden möchten ihre **Geschäftsziele** verfolgen, aber wissen nicht, dass dies in [!DNL Adobe Commerce Intelligence] möglich ist. In diesem Thema erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können - einschließlich Umsatz, neu registrierten Benutzern und Bestellungen im Zeitverlauf. Außerdem erfahren Sie, wie Sie die Leistung von Jahr zu Jahr in einem Dashboard wie folgt vergleichen:

![](../../assets/Goals-_dashboard_2.png)

Bevor Sie beginnen, sollten Sie den [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) überprüfen und sicherstellen, dass Sie Ihre Geschäftsziele für einen bestimmten Zeitraum definiert haben.

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die bestimmte tägliche/monatliche/vierteljährliche Ziele für Ihr Unternehmen enthält.

Sie können den [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild verwenden, um Ihre Datei zu formatieren. Zu den gängigsten Zielen, die Kunden in [!DNL Commerce Intelligence] verfolgen, gehören Bestellungen, Umsatz und neu registrierte Konten.

![](../../assets/Goals-_Excel.png)

## Metriken

Erstellen Sie für jedes Ziel eine neue Metrik. Wenn Sie beispielsweise monatliche Umsatz- und Bestellziele hochladen, müssen Sie zwei neue Metriken erstellen:

* **Monatliches Umsatzziel**
* In der Tabelle **`Monthly goals`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`Revenue target`**
* Durch den Zeitstempel **`Month`** geordnet

* **Monatsbestellziel**
* In der Tabelle **`Monthly goals`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`Orders target`**
* Durch den Zeitstempel **`Month`** geordnet

* **Monatliches Ziel neuer registrierter Konten**
* In der Tabelle **`Monthly goals`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`New registered accounts target`**
* Durch den Zeitstempel **`Month`** geordnet

## Berichte

Es ist hilfreich, bei der Analyse Ihrer Ziele eine Mischung aus statischen Werten und visuellen Diagrammen zu verwenden. Im Folgenden finden Sie drei Beispielberichte, mit denen Sie Ihre Umsatzleistung verfolgen können.

* **Ertrag links zum Erreichen des Ziels**
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

* [!UICONTROL Time period]: (Welchen relevanten Zeitraum Sie verwenden möchten)
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

* `Multiple Y-Axes` ausschalten
* [!UICONTROL Time period]: (Welchen relevanten Zeitraum Sie auch immer wünschen)*
* 
  [!UICONTROL Interval]: `Month`
* [!UICONTROL Chart Type]: `Line Chart`

Nachdem Sie die oben genannten Berichte für Umsatzziele abgeschlossen haben, können Sie identische Berichte für Ziele in Bezug auf Bestellungen, registrierte Konten oder andere Werte erstellen, die Sie in den Upload der Zieldatei aufgenommen haben.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das Bild oben auf dieser Seite aussehen.
