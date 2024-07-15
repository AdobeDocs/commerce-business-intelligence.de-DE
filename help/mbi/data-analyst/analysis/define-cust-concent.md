---
title: Kundenkonzentration definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihre Kundenbasis verteilt ist.
exl-id: 6242019f-a6a5-48d3-b214-94acd7842e00
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Kundenkonzentration

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, mit dem Sie messen können, wie der Gesamtumsatz auf Ihre Kundenbasis verteilt wird. Erfahren Sie, welcher Prozentsatz der Kunden zu welchem Prozentsatz des Umsatzes beitragen, und erstellen Sie segmentierte Listen, um Ihre wichtigsten Kunden am besten zu vermarkten und zu halten.

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die nur einen Primärschlüssel mit dem Wert 1 enthält. Dies ermöglicht die Erstellung einiger erforderlicher berechneter Spalten für die Analyse.

Sie können [den Datei-Uploader](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild verwenden, um Ihre Datei zu formatieren.

## Berechnete Spalten

Wenn Sie sich in der Originalarchitektur befinden (z. B. wenn Sie die Option `Data Warehouse Views` unter dem Menü `Manage Data` nicht haben), wenden Sie sich an das Supportteam, um die folgenden Spalten zu erstellen. In der neuen Architektur können diese Spalten über die Seite `Manage Data > Data Warehouse` erstellt werden. Im Folgenden finden Sie ausführliche Anweisungen.

Eine weitere Unterscheidung wird getroffen, wenn Ihr Unternehmen Gastaufträge zulässt. Wenn dies der Fall ist, können Sie alle Schritte für die Tabelle `customer_entity` ignorieren. Wenn Gastaufträge nicht zulässig sind, ignorieren Sie alle Schritte für die Tabelle `sales_flat_order` .

Zu erstellende Spalten

* `Sales_flat_order/customer_entity` table
* (input) `reference`
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `entity_id`
* [!UICONTROL Calculation]: - **Fall, wenn A null ist, dann null else 1 end**
* [!UICONTROL Datatype]: - `Integer`

* `Customer concentration` Tabelle (dies ist die Datei, die Sie mit der Zahl `1` hochgeladen haben)
* Anzahl der Kunden
* [!UICONTROL Column type]: - `Many to One > Count Distinct`
* Pfad - `sales_flat_order.(input) reference > Customer Concentration.Primary Key` ODER `customer_entity.(input)reference > Customer Concentration.Primary Key`
* Ausgewählte Spalte - `sales_flat_order.customer_email` ODER `customer_entity.entity_id`

* `customer_entity` table
* Anzahl der Kunden
* [!UICONTROL Column type]: - `One to Many > JOINED_COLUMN`
* Pfad - `customer_entity.(input) reference > Customer Concentration. Primary Key`
* Ausgewählte Spalte - `Number of customers`

* (input) `Ranking by customer lifetime revenue`
* [!UICONTROL Column type]: - `Same table > Event Number`
* Ereigniseigentümer - `Number of customers`
* Ereignisrang - `Customer's lifetime revenue`

* Umsatz-Perzentil des Kunden
* [!UICONTROL Column type]: - `Same table > Calculation`
* [!UICONTROL Inputs]: - `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: - **Fall, wenn A null ist, dann null else (A/B)* 100 end **
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
* [!UICONTROL Calculation]: - **Fall, wenn A null ist, dann null else (A/B)* 100 end **
* [!UICONTROL Datatype]: - `Decimal`

>[!NOTE]
>
>Die verwendeten Perzentile sind sogar Kundenaufteilungen, die das Xte Perzentil Ihrer Kundenbasis darstellen. Jeder Kunde ist mit einer Ganzzahl von 1 bis 100 verknüpft, die als ihr Lebensdauerumsatz *rank* betrachtet werden kann. Wenn beispielsweise das Umsatzperzentil des Kunden für einen bestimmten Kunden **5** beträgt, liegt dieser Kunde im ***fünften Perzentil*** aller Kunden in Bezug auf den Umsatz während der Lebensdauer.

## Metriken

* **Gesamtwert der Kundenlebensdauer**
* In der Tabelle `customer_entity`
* Diese Metrik führt eine **Summe** aus.
* In der Spalte `Customer's lifetime revenue`
* Durch den Zeitstempel `Customer's first order date` geordnet

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

* **Top 10% Konzentration**
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

* **Unterste Konzentration von 50 % mit nur einem Kauf**

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

* **Unterste 10 % Konzentration**
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

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.

Wenn Sie beim Erstellen dieser Analyse Fragen haben oder einfach das Professional Services-Team kontaktieren möchten, wenden Sie sich an den Support [.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)
