---
title: Neuigkeit, Häufigkeit, monetäre (RFM) Analyse
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Kunden nach Neuigkeit, Häufigkeit und Geldwert segmentieren können.
exl-id: 8f0f08fd-710b-4810-9faf-3d0c3cc0a25d
source-git-commit: 4cad1e05502630e13f7a2d341f263140a02b3d82
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# RFM-Analyse

In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Kunden nach Neuigkeit, Häufigkeit und geldlichem Rang segmentieren können. Die RFM-Analyse ist eine Marketing-Technik, die das Kundenverhalten berücksichtigt, um Sie bei der Bestimmung der Segmentierung für die Reichweite zu unterstützen. Er umfasst drei Aspekte:

1. Neuigkeit darüber, wie kürzlich ein Kunde in Ihrem Geschäft gekauft hat
1. Häufigkeit des Kaufs bei Ihnen
1. Geldbetrag in der Höhe, die der Kunde ausgibt

![](../../assets/blobid0.png)

Die RFM-Analyse kann nur konfiguriert werden, wenn Sie über die [!DNL Adobe Commerce Intelligence] Pro Plan für die neue Architektur (z. B. wenn Sie über die `Data Warehouse Views` Option unter `Manage Data` Menü). Diese Spalten können aus der **[!DNL Manage Data > Data Warehouse]** Seite. Detaillierte Anweisungen finden Sie unten.

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die nur einen Primärschlüssel mit dem Wert 1 enthält. Dies ermöglicht die Erstellung einiger erforderlicher berechneter Spalten für die Analyse.

Sie können dies [Artikel](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild, um Ihre Datei zu formatieren.

## Berechnete Spalten

Eine weitere Unterscheidung wird getroffen, wenn Ihr Unternehmen Gastaufträge zulässt. Wenn dies der Fall ist, können Sie alle Schritte für die `customer_entity` Tabelle. Wenn Gastaufträge nicht zulässig sind, ignorieren Sie alle Schritte für die `sales_flat_order` Tabelle.

Zu erstellende Spalten

* **`Sales_flat_order/customer_entity`** table
* `Customer's last order date`
* [!UICONTROL Column type]: `Many to one > Max`
* [!UICONTROL Pat]: `sales_flat_order.customer_id > customer_entity.entity_id`
* Ausgewählt [!UICONTROL column]: `created_at`
* [!UICONTROL Filter]: `Orders we count`

* 

       Sekunden seit dem letzten Bestelldatum des Kunden
   * [!UICONTROL Column type]: - &quot;Same table > Age
* Ausgewählt [!UICONTROL column]: `Customer's last order date`

* (input) Count reference
* [!UICONTROL Column type]: `Same table > Calculation`
* 
   [!UICONTROL-Eingaben]: `entity_id`
* [!UICONTROL Calculation]: `**case when A is null then null else 1 end**`
* 

   [!UICONTROL Datatype]: `Integer`

* **Count reference** table (dies ist die Datei, die Sie mit der Zahl &quot;1&quot;hochgeladen haben)
* Anzahl der Kunden
* [!UICONTROL Column type]: `Many to One > Count Distinct`
* [!UICONTROL Path]: `ales_flat_order.(input) reference > Count reference.Primary Key` ODER `customer_entity.(input)reference > Count Reference`. `Primary Key`
* Ausgewählt [!UICONTROL column]: `sales_flat_order.customer_email` ODER `customer_entity.entity_id`

* **Customer_entity** table
* Anzahl der Kunden
* [!UICONTROL Column type]: `One to Many > JOINED_COLUMN`
* [!UICONTROL Path]: `customer_entity`.(Eingabe)-Referenz > Kundenkonzentration. `Primary Key`
* Ausgewählt [!UICONTROL column]: `Number of customers`

* (Eingabe) `Ranking by customer lifetime revenue`
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Customer's lifetime revenue`

* Rangfolge nach Kundenlebenszeitumsatz
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: `case when A is null then null else (B-(A-1)) end`
* 

   [!UICONTROL Datatype]: `Integer`

* Geldwert des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: `Case when round((B-A+1)*100/B,0) <= 20 then 5 when round((B-A+1)*100/B,0) <= 40 then 4 when round((B-A+1)*100/B,0) <= 60 then 3 when round((B-A+1)*100/B,0) <= 80 then 2 when round((B-A+1)*100/B,0) <= 100 then 1 else 0 end`
* 

   [!UICONTROL Datatype]: `Integer`

* (Eingabe) Rangfolge nach Kundenlebensdauer Anzahl der Bestellungen
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Customer's lifetime number of orders`

* Rangfolge nach Kundenlebensdauer und Anzahl der Bestellungen
* 
   [!UICONTROL Spaltentyp]: – "Dieselbe Tabelle > Berechnung"
* [!UICONTROL Inputs]: - **(Eingabe) Rangfolge nach Kundenlebensdauer Anzahl der Bestellungen**, **Anzahl der Kunden**
* [!UICONTROL Calculation]: - **Wenn A null ist, dann wird das Ende von null else (B-(A-1))**
* [!UICONTROL Datatype]: - Ganzzahl

* Frequenzwert des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime number of orders`, `Number of customers`
* [!UICONTROL Calculation]: `Case when round((B-A+1)*100/B,0) <= 20 then 5 when round((B-A+1)*100/B,0) <= 40 then 4 when round((B-A+1)*100/B,0) <= 60 then 3 when round((B-A+1)*100/B,0) <= 80 then 2 when round((B-A+1)*100/B,0) <= 100 then 1 else 0 end`
* 

   [!UICONTROL Datatype]: `Integer`

* Rangfolge nach Sekunden seit dem letzten Bestelldatum des Kunden
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Seconds since customer's last order date`

* Neuigkeitsergebnis des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime number of orders`, `Number of customers`
* [!UICONTROL Calculation]: `Case when (A * 100/B,0) <= 20 then 5 when (A * 100/B,0) <= 40 then 4 when (A * 100/B,0) <= 60 then 3 when (A * 100/B,0) <= 80 then 2 when (A * 100/B,0) <= 100 then 1 else 0 end`
* 

   [!UICONTROL Datatype]: `Integer`

* Neuigkeitsergebnis des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `Customer's recency score (by percentiles)`, `Customer's frequency score (by percentiles)`, `Customer's monetary score (by percentiles)`
* [!UICONTROL Calculation]: `case when (A IS NULL or B IS NULL or C IS NULL) then null else concat(A,B,C) end`
* 

   [!UICONTROL Datatype]: String

* **Count reference** table
* [!UICONTROL Number of customers]: `(RFM > 0)`
* [!UICONTROL Column type]: `Many to One > Count Distinct`
* [!UICONTROL Path]: `sales_flat_order.(input) reference > Customer Concentration. Primary Key` ODER `customer_entity.(input)reference > Customer Concentration.Primary Key`
* Ausgewählt [!UICONTROL column]: `sales_flat_order.customer_email` ODER `customer_entity.entity_id`
* [!UICONTROL Filter]: `Customer's RFM score (by percentile)` nicht gleich 000

* **Customer_entity** table
* [!UICONTROL Number of customers]: `(RFM > 0)`
* [!UICONTROL Column type]: `One to Many > JOINED_COLUMN`
* [!UICONTROL Path]: `customer_entity.(input) reference > Customer Concentration.Primary Key`
* Ausgewählt [!UICONTROL column]: - `Number of customers`

* Neuigkeitsbewertung des Kunden `(R+F+M)`
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: – `Customer's recency score (by percentiles)`, `Customer's frequency score (by percentiles)`, `Customer's monetary score (by percentiles)`
* [!UICONTROL Calculation]: `case when (A IS NULL or B IS NULL or C IS NULL) then null else A+B+C end`
* 

   [!UICONTROL Datatype]: `Integer`

* (Eingabe) Rangfolge nach RFM-Gesamtwert des Kunden
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Customer's recency score (R+F+M)`
* [!UICONTROL Filter]: `Customer's RFM score (by percentile)` nicht gleich 000

* Rangordnung nach dem RFM-Gesamtwert des Kunden
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer's overall RFM score`, `Number of customers (RFM > 0)`
* [!UICONTROL Calculation]: `case when A is null then null else (B-(A-1)) end`
* 

   [!UICONTROL Datatype]: `Integer`

* RFM-Gruppe des Kunden
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: `Case when round(A * 100/B,0) <= 20 then '5. copper' when round(A * 100/B,0) <= 40 then '4. bronze' when round(A * 100/B,0) <= 60 then '3. silver' when round(A * 100/B,0)<= 80 then '2. gold' else '1. Platinum' end`
* 

   [!UICONTROL Datatype]: `Integer`

>[!NOTE]
>
>Die verwendeten Perzentile sind sogar Aufspaltungen von Kunden (z. B. 20 Prozent Behälter, um 1-5 zurückzugeben). Wenn Sie eine benutzerdefinierte Methode haben, wie Sie diese gewichten möchten, teilen Sie dies dem Analysten mit, wenn Sie das Ticket übermitteln.

## Metriken

Keine neuen Metriken!

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

## Berichte

* **Kunden nach RFM-Gruppierung**
* Metrik `A`: `New customers`
* [!UICONTROL Metric]: `New customers`
* [!UICONTROL Filter]: `Customer's RFM score (by percentiles) Not Equal to 000`

* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* [!UICONTROL Group by]: `Customer's RFM group`
* 
   [!UICONTROL Gruppe von]: `Email`
* 

   [!UICONTROL Chart type]: `Table`

* **Kunden mit fünf Neuigkeitsergebnissen**
* Metrik `A`: `New customers`
* [!UICONTROL Metric]: `New customers`
* [!UICONTROL Filter]: `Customer's recency score (by percentiles) Equal to 5`

* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* 
   [!UICONTROL Chart Type]: `Scalar`
* Diagramm ausblenden
* 
   [!UICONTROL Gruppe von]: `Email`
* [!UICONTROL Group by]: `Customer's RFM score (R+F+M)`
* 

   [!UICONTROL Chart type]: `Table`

* **Kunden mit einer Neuigkeitsbewertung**
* Metrik `A`: `New customers`
* [!UICONTROL Metric]: `New customers`
* [!UICONTROL Filter]: `Customer's recency score (by percentiles) Equal to 1`

* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* 
   [!UICONTROL Chart Type]: `Scalar`
* Diagramm ausblenden
* 
   [!UICONTROL Gruppe von]: `Email`
* [!UICONTROL Group by]: `Customer's RFM score (R+F+M)`
* 

   [!UICONTROL Chart type]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das obige Beispiel-Dashboard aussehen, aber die drei generierten Tabellen sind nur Beispiele für die Arten der Kundensegmentierung, die Sie durchführen können.
