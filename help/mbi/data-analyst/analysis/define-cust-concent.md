---
title: Kundenkonzentration definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihren Kundenstamm verteilt wird.
exl-id: 6242019f-a6a5-48d3-b214-94acd7842e00
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '472'
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
* [!UICONTROL Calculation]: - **wenn A null ist, dann andernfalls null (A/B)* 100 end &#x200B;**
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
* [!UICONTROL Calculation]: - **wenn A null ist, dann andernfalls null (A/B)* 100 end &#x200B;**
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

* &#x200B;
  [!UICONTROL Gruppieren nach]: `Independent`
* `A`: `Total customer lifetime revenue by percentile`
* `B`: `Total customer lifetime revenue (ungrouped)`
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Customer's revenue percentile`
* Oben/unten anzeigen: `100% of Customer's revenue percentile Name`
* &#x200B;
  [!UICONTROL Chart type]: `Line`

* **Top 10% Konzentration**
* [!UICONTROL Filter]: `Customer's revenue percentile <= 10`

* `A`: `Total customer lifetime revenue`
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Email`
* &#x200B;
  [!UICONTROL Chart type]: `Table`

* **Unten 50 % Konzentration mit nur einem Kauf**

* `A`: `Total customer lifetime revenue`
* `Customer's revenue percentile <= 50`
* `Customer's lifetime number of orders = 1`
* [!UICONTROL Filter]:

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Email`
* &#x200B;
  [!UICONTROL Chart type]: `Table`

* **untere 10%-Konzentration**
* [!UICONTROL Filter]: `Customer's revenue percentile > 90`

* `A`: `Total customer lifetime revenue`
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Email`
* &#x200B;
  [!UICONTROL Chart type]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [&#x200B; sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).
