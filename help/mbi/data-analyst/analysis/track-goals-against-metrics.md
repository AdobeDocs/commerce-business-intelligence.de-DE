---
title: Tracking von Zielen anhand von Metriken
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können - einschließlich Umsatz, neu registrierte Benutzer und Bestellungen im Zeitverlauf.
exl-id: 9d621f40-f9c2-4310-bd96-a46ab7159930
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Tracking von Zielen anhand von Leistungsmetriken

Die meisten Kunden möchten ihre **Geschäftsziele** verfolgen, wissen aber nicht, dass dies in [!DNL Adobe Commerce Intelligence] möglich ist. In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können - einschließlich Umsatz, neu registrierte Benutzer und Bestellungen im Zeitverlauf. Außerdem erfahren Sie, wie Sie die Leistung von Jahr zu Jahr vergleichen können, und das alles in einem Dashboard wie diesem:

![](../../assets/Goals-_dashboard_2.png)

Bevor Sie beginnen, sollten Sie den [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) überprüfen und sicherstellen, dass Sie Ihre Geschäftsziele für einen bestimmten Zeitraum definiert haben.

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die bestimmte tägliche/monatliche/vierteljährliche Ziele für Ihr Unternehmen enthält.

Sie können den [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild verwenden, um Ihre Datei zu formatieren. Zu den häufigsten Zielen, die Kunden in [!DNL Commerce Intelligence] verfolgen, gehören Bestellungen, Umsatz und neue registrierte Konten.

![](../../assets/Goals-_Excel.png)

## Metriken

Erstellen Sie für jede Zielgruppe eine neue Metrik. Wenn Sie beispielsweise monatliche Umsatz- und Bestellziele hochladen, müssen Sie zwei neue Metriken erstellen:

* **Monatliches Umsatzziel**
* In der **`Monthly goals`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`Revenue target`**
* Sortiert nach dem **`Month`** Zeitstempel

* **Ziel für monatliche Bestellungen**
* In der **`Monthly goals`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`Orders target`**
* Sortiert nach dem **`Month`** Zeitstempel

* **Monatliches Ziel für neue registrierte Konten**
* In der **`Monthly goals`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`New registered accounts target`**
* Sortiert nach dem **`Month`** Zeitstempel

## Berichte

Es ist hilfreich, bei der Analyse Ihrer Ziele einen Mix aus statischen Werten und visuellen Diagrammen zu verwenden. Nachfolgend finden Sie drei Beispielberichte, die Ihnen den Einstieg in die Verfolgung Ihrer Umsatzentwicklung erleichtern.

* **Zum Erreichen des Ziels verbleibender Umsatz**
* `A`: `Revenue`
* &#x200B;
  [!UICONTROL -Metrik]: `Revenue`

* `B`: `Target Revenue`
* [!UICONTROL Metric]: `Monthly Revenue Target`

* [!UICONTROL Formula]: `Revenue left to achieve target`
* &#x200B;
  [!UICONTROL -Formel]: `(B-A)`
* &#x200B;
  [!UICONTROL Format]: `Number`

* [!UICONTROL Time period]: (Welcher relevante Zeitraum gewünscht wird)
* &#x200B;
  [!UICONTROL Interval]: `Month`
* &#x200B;
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Umsatzziele**
* `A`: `Revenue`
* &#x200B;
  [!UICONTROL -Metrik]: `Revenue`

* `B`: `Target Revenue`
* [!UICONTROL Metric]: `Monthly Revenue Target`

* `C`: `Revenue (amount change since previous year)` (ausblenden)
* &#x200B;
  [!UICONTROL -Metrik]: `Revenue`
* [!UICONTROL Perspective]: `Amount change vs. Previous year`

* [!UICONTROL Formula]: (Diesen Monat letztes Jahr)
* &#x200B;
  [!UICONTROL -Formel]: `(A-C)`
* &#x200B;
  [!UICONTROL Format]: `Currency`

* `Multiple Y-Axes` ausschalten
* [!UICONTROL Time period]: (Welcher relevante Zeitraum gewünscht wird)*
* &#x200B;
  [!UICONTROL Interval]: `Month`
* [!UICONTROL Chart Type]: `Line Chart`

Nachdem Sie die oben genannten Berichte zu Umsatzzielen abgeschlossen haben, können Sie identische Berichte für Ziele rund um Bestellungen, registrierte Konten oder andere Werte erstellen, die Sie in Ihren Zieldatei-Upload aufgenommen haben.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis könnte wie das Bild oben auf dieser Seite aussehen.
