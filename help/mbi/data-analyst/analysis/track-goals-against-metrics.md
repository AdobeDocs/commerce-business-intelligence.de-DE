---
title: Tracking von Zielen anhand von Metriken
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können - einschließlich Umsatz, neu registrierte Benutzer und Bestellungen im Zeitverlauf.
exl-id: 9d621f40-f9c2-4310-bd96-a46ab7159930
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards, Reports
TQID: https://experienceleague.adobe.com/gT-FJxqVg3X9fuXe-4kWErttYJ6qSMD4eqNvOITNNtQ
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 402
ht-degree: 0%

---

# Tracking von Zielen anhand von Leistungsmetriken

Die meisten Kunden möchten ihre **Geschäftsziele** verfolgen, wissen aber nicht, dass dies in [!DNL Adobe Commerce Intelligence] möglich ist. In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Geschäftsziele anhand Ihrer tatsächlichen Daten verfolgen können - einschließlich Umsatz, neu registrierte Benutzer und Bestellungen im Zeitverlauf. Außerdem erfahren Sie, wie Sie die Leistung von Jahr zu Jahr vergleichen können, und das alles in einem Dashboard wie diesem:

![Dashboard mit Zielen, die anhand der tatsächlichen Leistungsmetriken verfolgt werden](../../assets/Goals-_dashboard_2.png)

Bevor Sie beginnen, sollten Sie den [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) überprüfen und sicherstellen, dass Sie Ihre Geschäftsziele für einen bestimmten Zeitraum definiert haben.

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die bestimmte tägliche/monatliche/vierteljährliche Ziele für Ihr Unternehmen enthält.

Sie können den [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild verwenden, um Ihre Datei zu formatieren. Zu den häufigsten Zielen, die Kunden in [!DNL Commerce Intelligence] verfolgen, gehören Bestellungen, Umsatz und neue registrierte Konten.

![Excel-Tabellenvorlage zum Tracking von Zielen und Metriken](../../assets/Goals-_Excel.png)

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
* 
  [!UICONTROL-Metrik]: `Revenue`

* `B`: `Target Revenue`
* [!UICONTROL Metric]: `Monthly Revenue Target`

* [!UICONTROL Formula]: `Revenue left to achieve target`
* 
  [!UICONTROL-Formel]: `(B-A)`
* 
  [!UICONTROL Format]: `Number`

* [!UICONTROL Time period]: (Welcher relevante Zeitraum gewünscht wird)
* 
  [!UICONTROL Interval]: `Month`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Umsatzziele**
* `A`: `Revenue`
* 
  [!UICONTROL-Metrik]: `Revenue`

* `B`: `Target Revenue`
* [!UICONTROL Metric]: `Monthly Revenue Target`

* `C`: `Revenue (amount change since previous year)` (ausblenden)
* 
  [!UICONTROL-Metrik]: `Revenue`
* [!UICONTROL Perspective]: `Amount change vs. Previous year`

* [!UICONTROL Formula]: (Diesen Monat letztes Jahr)
* 
  [!UICONTROL-Formel]: `(A-C)`
* 
  [!UICONTROL Format]: `Currency`

* `Multiple Y-Axes` ausschalten
* [!UICONTROL Time period]: (Welcher relevante Zeitraum gewünscht wird)*
* 
  [!UICONTROL Interval]: `Month`
* [!UICONTROL Chart Type]: `Line Chart`

Nachdem Sie die oben genannten Berichte zu Umsatzzielen abgeschlossen haben, können Sie identische Berichte für Ziele rund um Bestellungen, registrierte Konten oder andere Werte erstellen, die Sie in Ihren Zieldatei-Upload aufgenommen haben.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis könnte wie das Bild oben auf dieser Seite aussehen.
