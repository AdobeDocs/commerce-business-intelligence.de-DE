---
title: Kundenkonzentration definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihren Kundenstamm verteilt wird.
exl-id: 6242019f-a6a5-48d3-b214-94acd7842e00
role: Admin, Developer, User
feature: Data Warehouse Manager, Reports, Dashboards
TQID: https://experienceleague.adobe.com/kayq-ci-AiHHgNoaX09h6dqKQX14MudLvEqFmos3hQE
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 483
ht-degree: 0%

---

# Kundenkonzentration

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihren Kundenstamm verteilt wird. Erfahren Sie, welcher Prozentsatz der Kundinnen und Kunden welchen Prozentsatz des Umsatzes beiträgt, und erstellen Sie segmentierte Listen, um Ihre Kundinnen und Kunden mit hohem Beitragsanteil am besten zu vermarkten und zu binden.

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die nur einen Primärschlüssel mit dem Wert 1 enthält. Dies ermöglicht die Erstellung einiger erforderlicher berechneter Spalten für die Analyse.

Sie können [den Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild verwenden, um Ihre Datei zu formatieren.

## Berechnete Spalten

Wenn Sie sich auf der ursprünglichen Architektur befinden (z. B. wenn Sie die Option `Data Warehouse Views` nicht im Menü `Manage Data` haben), sollten Sie sich an das Supportteam wenden, um die folgenden Spalten zu erstellen. In der neuen Architektur können diese Spalten von der `Manage Data > Data Warehouse` Seite aus erstellt werden. Detaillierte Anweisungen finden Sie unten.

Eine weitere Unterscheidung wird getroffen, wenn Ihr Unternehmen Gastbestellungen erlaubt. In diesem Fall können Sie alle Schritte für die `customer_entity` ignorieren. Wenn keine Gastbestellungen zulässig sind, ignorieren Sie alle Schritte für die `sales_flat_order`.

Zu erstellende Spalten

* `Sales_flat_order/customer_entity`
* (Eingabe) `reference`
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `entity_id`
* [!UICONTROL Calculation]: - **wenn A null ist, dann null andernfalls 1 Ende**
* [!UICONTROL Datatype]: - `Integer`

* `Customer concentration` Tabelle (das ist die Datei, die Sie mit der Nummer `1` hochgeladen haben)
* Anzahl der Kunden
* [!UICONTROL Column type]: - `Many to One > Count Distinct`
* Pfad - `sales_flat_order.(input) reference > Customer Concentration.Primary Key` ODER `customer_entity.(input)reference > Customer Concentration.Primary Key`
* Ausgewählte Spalte - `sales_flat_order.customer_email` ODER `customer_entity.entity_id`

* `customer_entity`
* Anzahl der Kunden
* [!UICONTROL Column type]: - `One to Many > JOINED_COLUMN`
* Pfad - `customer_entity.(input) reference > Customer Concentration. Primary Key`
* Ausgewählte Spalte - `Number of customers`

* (Eingabe) `Ranking by customer lifetime revenue`
* [!UICONTROL Column type]: - `Same table > Event Number`
* Ereignisbesitzer - `Number of customers`
* Ereignisrang - `Customer's lifetime revenue`

* Perzentil des Umsatzes des Kunden
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: - ** wenn A null ist, dann andernfalls null (A/B)*100 end **
* [!UICONTROL Datatype]: - `Decimal`

* `Sales_flat_order`
* Anzahl der Kunden
* [!UICONTROL Column type]: - `One to Many > JOINED_COLUMN`
* Pfad - `sales_flat_order.(input) reference > Customer Concentration.Primary Key`
* Ausgewählte Spalte - `Number of customers`

* (Eingabe) Rangfolge nach Kundenlebensdauerumsatz
* [!UICONTROL Column type]: - `Same table > Event Number`
* Ereignisbesitzer - `Number of customers`
* Ereignisrang - `Customer's lifetime revenue`
* Filter - `Customer's order number = 1`

* Perzentil des Umsatzes des Kunden
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: - ** wenn A null ist, dann andernfalls null (A/B)*100 end **
* [!UICONTROL Datatype]: - `Decimal`

>[!NOTE]
>
>Die verwendeten Perzentile sind sogar Aufspaltungen von Kundinnen und Kunden, die das Xth-Perzentil Ihres Kundenstamms darstellen. Jeder Kunde ist mit einer Ganzzahl zwischen 1 und 100 verknüpft, die als sein Lebensdauerumsatz (Rang) *werden*. Wenn beispielsweise das Umsatzperzentil des Kunden für einen bestimmten Kunden **5** beträgt, liegt dieser Kunde im ***fünften Perzentil*** des Gesamtumsatzes aller Kunden.

## Metriken

* **Gesamtwert der Kundenlebensdauer**
* In der `customer_entity`
* Diese Metrik führt eine **Summe“**
* In der Spalte `Customer's lifetime revenue`
* Sortiert nach dem `Customer's first order date` Zeitstempel

## Berichte

* **Kundenkonzentration**
* [!UICONTROL Metric]: `Total customer lifetime value`
* [!UICONTROL Filter]: `Customer's revenue percentile IS NOT NULL`

* [!UICONTROL Metric]: `Total customer lifetime value`
* [!UICONTROL Filter]: `Customer's revenue percentile IS NOT NULL`

* 
  [!UICONTROL Gruppieren nach]: `Independent`
* `A`: `Total customer lifetime revenue by percentile`
* `B`: `Total customer lifetime revenue (ungrouped)`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Customer's revenue percentile`
* Oben/unten anzeigen: `100% of Customer's revenue percentile Name`
* 
  [!UICONTROL Chart type]: `Line`

* **Top 10% Konzentration**
* [!UICONTROL Filter]: `Customer's revenue percentile <= 10`

* `A`: `Total customer lifetime revenue`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* 
  [!UICONTROL Gruppieren nach]: `Email`
* 
  [!UICONTROL Chart type]: `Table`

* **Unten 50 % Konzentration mit nur einem Kauf**

* `A`: `Total customer lifetime revenue`
* `Customer's revenue percentile <= 50`
* `Customer's lifetime number of orders = 1`
* [!UICONTROL Filter]:

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* 
  [!UICONTROL Gruppieren nach]: `Email`
* 
  [!UICONTROL Chart type]: `Table`

* **untere 10%-Konzentration**
* [!UICONTROL Filter]: `Customer's revenue percentile > 90`

* `A`: `Total customer lifetime revenue`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* 
  [!UICONTROL Gruppieren nach]: `Email`
* 
  [!UICONTROL Chart type]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [ sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
