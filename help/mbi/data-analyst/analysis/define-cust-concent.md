---
title: Kundenkonzentration definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihre Kundenbasis verteilt wird.
exl-id: 6242019f-a6a5-48d3-b214-94acd7842e00
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Kundenkonzentration

In diesem Artikel erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihre Kundenbasis verteilt wird. Erfahren Sie, welcher Prozentsatz der Kunden zu welchem Prozentsatz des Umsatzes beitragen, und erstellen Sie segmentierte Listen, um Ihre wichtigsten Kunden am besten zu vermarkten und zu halten.

Diese Analyse enthält [Erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Zunächst müssen Sie eine Datei hochladen, die nur einen Primärschlüssel mit dem Wert 1 enthält. Dies ermöglicht die Erstellung einiger für die Analyse erforderlicher berechneter Spalten.

Sie können [Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) sowie das folgende Bild, um Ihre Datei zu formatieren.

## Berechnete Spalten

Wenn Sie sich in der ursprünglichen Architektur befinden (z. B. wenn Sie nicht über die `Data Warehouse Views` Option unter `Manage Data` ), kontaktieren Sie unser Supportteam, um die unten stehenden Spalten zu erstellen. In der neuen Architektur können diese Spalten aus dem `Manage Data > Data Warehouse` Seite. Im Folgenden finden Sie ausführliche Anweisungen.

Eine weitere Unterscheidung wird getroffen, wenn Ihr Unternehmen Gastaufträge zulässt. Wenn dies der Fall ist, können Sie alle Schritte für die `customer_entity` Tabelle. Wenn Gastaufträge nicht zulässig sind, ignorieren Sie alle Schritte für die `sales_flat_order` Tabelle.

Zu erstellende Spalten

* `Sales_flat_order/customer_entity` table
* (Eingabe) `reference`
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `entity_id`
* [!UICONTROL Calculation]: - **Wenn A null ist, dann null else 1 end**
* [!UICONTROL Datatype]: - `Integer`

* `Customer concentration` Tabelle (dies ist die Datei, die Sie gerade mit der Nummer hochgeladen haben) `1`)
* Anzahl der Kunden
* [!UICONTROL Column type]: - `Many to One > Count Distinct`
* Pfad - `sales_flat_order.(input) reference > Customer Concentration.Primary Key` ODER `customer_entity.(input)reference > Customer Concentration.Primary Key`
* Ausgewählte Spalte - `sales_flat_order.customer_email` ODER `customer_entity.entity_id`

* `customer_entity` table
* Anzahl der Kunden
* [!UICONTROL Column type]: - `One to Many > JOINED_COLUMN`
* Pfad - `customer_entity.(input) reference > Customer Concentration. Primary Key`
* Ausgewählte Spalte - `Number of customers`

* (Eingabe) `Ranking by customer lifetime revenue`
* [!UICONTROL Column type]: - `Same table > Event Number`
* Ereigniseigentümer - `Number of customers`
* Ereignisrang - `Customer's lifetime revenue`

* Umsatz-Perzentil des Kunden
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: - **Wenn A null ist, dann null else (A/B)* 100 Ende **
* [!UICONTROL Datatype]: - `Decimal`

* `Sales_flat_order` table
* Anzahl der Kunden
* [!UICONTROL Column type]: - `One to Many > JOINED_COLUMN`
* Pfad - `sales_flat_order.(input) reference > Customer Concentration.Primary Key`
* Ausgewählte Spalte - `Number of customers`

* (Eingabe) Rangfolge nach Kundenlebenszeitumsatz
* [!UICONTROL Column type]: - `Same table > Event Number`
* Ereigniseigentümer - `Number of customers`
* Ereignisrang - `Customer's lifetime revenue`
* Filter - `Customer's order number = 1`

* Umsatz-Perzentil des Kunden
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: - **Wenn A null ist, dann null else (A/B)* 100 Ende **
* [!UICONTROL Datatype]: - `Decimal`

>[!NOTE]
>
>Die verwendeten Perzentile sind sogar Kundenaufteilungen, die das Xte Perzentil Ihrer Kundenbasis darstellen. Jeder Kunde wird mit einer Ganzzahl von 1 bis 100 verknüpft, die als Umsatz für die gesamte Lebensdauer betrachtet werden kann *rank*. Wenn beispielsweise das Umsatzperzentil des Kunden für einen bestimmten Kunden **5**, befindet sich dieser Kunde im ***5. Perzentil*** des Gesamtumsatzes aller Kunden.

## Metriken

* **Gesamtwert der Kundenlebensdauer**
* Im `customer_entity` table
* Diese Metrik führt eine **Summe**
* Im `Customer's lifetime revenue` column
* Bestellt von der `Customer's first order date` timestamp

## Berichte

* **Kundenkonzentration**
* [!UICONTROL Metric]: `Total customer lifetime value`
* [!UICONTROL Filter]: `Customer's revenue percentile IS NOT NULL`

* [!UICONTROL Metric]: `Total customer lifetime value`
* [!UICONTROL Filter]: `Customer's revenue percentile IS NOT NULL`

* 
   [!UICONTROL Gruppe von]: `Independent`
* Metrik `A`: `Total customer lifetime revenue by percentile`
* Metrik `B`: `Total customer lifetime revenue (ungrouped)`
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Customer's revenue percentile`
* Oben/unten anzeigen: `100% of Customer's revenue percentile Name`
* 

   [!UICONTROL Chart type]: `Line`

* **Top-10-%-Konzentration**
* [!UICONTROL Filter]: `Customer's revenue percentile <= 10`

* Metrik `A`: `Total customer lifetime revenue`
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* 
   [!UICONTROL Gruppe von]: `Email`
* 

   [!UICONTROL Chart type]: `Table`

* **Unterste Konzentration von 50 % bei nur einem Kauf**

* Metrik `A`: `Total customer lifetime revenue`
* `Customer's revenue percentile <= 50`
* `Customer's lifetime number of orders = 1`
* [!UICONTROL Filter]:

* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* 
   [!UICONTROL Gruppe von]: `Email`
* 

   [!UICONTROL Chart type]: `Table`

* **Konzentration unter 10 %**
* [!UICONTROL Filter]: `Customer's revenue percentile > 90`

* Metrik `A`: `Total customer lifetime revenue`
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* 
   [!UICONTROL Gruppe von]: `Email`
* 

   [!UICONTROL Chart type]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Endergebnis kann wie das obige Beispiel-Dashboard aussehen.

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach unser Professional Services-Team einbinden möchten, [Support kontaktieren](../../guide-overview.md).
