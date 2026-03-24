---
title: Neuigkeit, Häufigkeit, monetäre (RFM) Analyse
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Kundinnen und Kunden nach ihrer Aktualität, Häufigkeit und ihrem geldpolitischen Ranking segmentieren können.
exl-id: 8f0f08fd-710b-4810-9faf-3d0c3cc0a25d
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
TQID: https://experienceleague.adobe.com/AaRzdTdV7-a4ApO-TA5jbyaJ3sr6sqP9HCToKG--uQ0
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 542
ht-degree: 0%

---

# RFM-Analyse

In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, mit dem Sie Ihre Kundinnen und Kunden nach ihrer Aktualität, Häufigkeit und Geld-Rankings segmentieren können. Die RFM-Analyse ist eine Marketing-Technik, die das Kundenverhalten berücksichtigt, um die Segmentierung für die Reichweite zu ermitteln. Er umfasst drei Aspekte:

1. Neueste Informationen dazu, wie kürzlich eine Kundin oder ein Kunde in Ihrem Geschäft gekauft hat
1. Häufigkeit, mit der Kunden bei Ihnen einkaufen
1. Geldwert, wie viel der Kunde ausgibt

![Dashboard der RFM-Analyse mit Segmenten für Neuigkeit, Häufigkeit und Geldwert](../../assets/blobid0.png)

Die RFM-Analyse kann nur konfiguriert werden, wenn Sie den [!DNL Adobe Commerce Intelligence] Pro Plan auf der neuen Architektur haben (zum Beispiel, wenn Sie die `Data Warehouse Views` Option im `Manage Data` Menü haben). Diese Spalten können über die **[!DNL Manage Data > Data Warehouse]** erstellt werden. Detaillierte Anweisungen finden Sie unten.

## Erste Schritte

Sie müssen zunächst eine Datei hochladen, die nur einen Primärschlüssel mit dem Wert 1 enthält. Dies ermöglicht die Erstellung einiger erforderlicher berechneter Spalten für die Analyse.

Sie können diesen [Artikel](../importing-data/connecting-data/using-file-uploader.md) und das folgende Bild verwenden, um Ihre Datei zu formatieren.

## Berechnete Spalten

Eine weitere Unterscheidung wird getroffen, wenn Ihr Unternehmen Gastbestellungen erlaubt. In diesem Fall können Sie alle Schritte für die `customer_entity` ignorieren. Wenn keine Gastbestellungen zulässig sind, ignorieren Sie alle Schritte für die `sales_flat_order`.

Zu erstellende Spalten

* **`Sales_flat_order/customer_entity`**
* `Customer's last order date`
* [!UICONTROL Column type]: `Many to one > Max`
* [!UICONTROL Pat]: `sales_flat_order.customer_id > customer_entity.entity_id`
* Ausgewählte [!UICONTROL column]: `created_at`
* [!UICONTROL Filter]: `Orders we count`

* &#x200B;
      Sekunden seit dem letzten Bestelldatum des Kunden
  * [!UICONTROL Column type]:     „Selbe Tabelle > Alter
* Ausgewählte [!UICONTROL column]: `Customer's last order date`

* (Eingabe) Zählerreferenz
* [!UICONTROL Column type]: `Same table > Calculation`
* &#x200B;
  [!UICONTROL Eingänge]: `entity_id`
* [!UICONTROL Calculation]: `**case when A is null then null else 1 end**`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* Tabelle **Referenz zählen** (dies ist die Datei, die Sie mit der Zahl „1“ hochgeladen haben)
* Anzahl der Kunden
* [!UICONTROL Column type]: `Many to One > Count Distinct`
* [!UICONTROL Path]: `ales_flat_order.(input) reference > Count reference.Primary Key` ODER `customer_entity.(input)reference > Count Reference`. `Primary Key`
* Ausgewählte [!UICONTROL column]: `sales_flat_order.customer_email` ODER `customer_entity.entity_id`

* **Customer_entity**-Tabelle
* Anzahl der Kunden
* [!UICONTROL Column type]: `One to Many > JOINED_COLUMN`
* [!UICONTROL Path]: `customer_entity`.(Eingabe) Referenz > Kundenkonzentration. `Primary Key`
* Ausgewählte [!UICONTROL column]: `Number of customers`

* (Eingabe) `Ranking by customer lifetime revenue`
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Customer's lifetime revenue`

* Rangfolge nach Kundenlebensdauerumsatz
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: `case when A is null then null else (B-(A-1)) end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* Geldwert des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: `Case when round((B-A+1)*100/B,0) <= 20 then 5 when round((B-A+1)*100/B,0) <= 40 then 4 when round((B-A+1)*100/B,0) <= 60 then 3 when round((B-A+1)*100/B,0) <= 80 then 2 when round((B-A+1)*100/B,0) <= 100 then 1 else 0 end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* (Eingabe) Rangfolge nach Kundenlebensdauer Anzahl der Bestellungen
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Customer's lifetime number of orders`

* Rangfolge nach Kundenlebensdauer Anzahl der Bestellungen
* &#x200B;
  [!UICONTROL Spaltentyp]: – "Gleiche Tabelle > Berechnung"
* [!UICONTROL Inputs]: - **(Eingabe) Rangfolge nach Kundenlebensdauer Anzahl der Bestellungen**, **Anzahl der Kunden**
* [!UICONTROL Calculation]: - **Wenn A null ist, endet andernfalls null (B-(A-1))**
* [!UICONTROL Datatype]: - Ganzzahl

* Häufigkeitsbewertung des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime number of orders`, `Number of customers`
* [!UICONTROL Calculation]: `Case when round((B-A+1)*100/B,0) <= 20 then 5 when round((B-A+1)*100/B,0) <= 40 then 4 when round((B-A+1)*100/B,0) <= 60 then 3 when round((B-A+1)*100/B,0) <= 80 then 2 when round((B-A+1)*100/B,0) <= 100 then 1 else 0 end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* Rangfolge nach Sekunden seit dem letzten Bestelldatum des Kunden
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Seconds since customer's last order date`

* Aktualitätswert des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime number of orders`, `Number of customers`
* [!UICONTROL Calculation]: `Case when (A * 100/B,0) <= 20 then 5 when (A * 100/B,0) <= 40 then 4 when (A * 100/B,0) <= 60 then 3 when (A * 100/B,0) <= 80 then 2 when (A * 100/B,0) <= 100 then 1 else 0 end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* Aktualitätswert des Kunden (nach Perzentilen)
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `Customer's recency score (by percentiles)`, `Customer's frequency score (by percentiles)`, `Customer's monetary score (by percentiles)`
* [!UICONTROL Calculation]: `case when (A IS NULL or B IS NULL or C IS NULL) then null else concat(A,B,C) end`
* &#x200B;
  [!UICONTROL Datentyp]: String

* **Referenz zählen** Tabelle
* [!UICONTROL Number of customers]: `(RFM > 0)`
* [!UICONTROL Column type]: `Many to One > Count Distinct`
* [!UICONTROL Path]: `sales_flat_order.(input) reference > Customer Concentration. Primary Key` ODER `customer_entity.(input)reference > Customer Concentration.Primary Key`
* Ausgewählte [!UICONTROL column]: `sales_flat_order.customer_email` ODER `customer_entity.entity_id`
* [!UICONTROL Filter]: `Customer's RFM score (by percentile)` nicht gleich 000

* **Customer_entity**-Tabelle
* [!UICONTROL Number of customers]: `(RFM > 0)`
* [!UICONTROL Column type]: `One to Many > JOINED_COLUMN`
* [!UICONTROL Path]: `customer_entity.(input) reference > Customer Concentration.Primary Key`
* Ausgewählte [!UICONTROL column]: - `Number of customers`

* Aktualitätswert des Kunden `(R+F+M)`
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: - `Customer's recency score (by percentiles)`, `Customer's frequency score (by percentiles)`, `Customer's monetary score (by percentiles)`
* [!UICONTROL Calculation]: `case when (A IS NULL or B IS NULL or C IS NULL) then null else A+B+C end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* (Eingabe) Rangfolge nach dem RFM-Gesamtergebnis des Kunden
* [!UICONTROL Column type]: `Same table > Event Number`
* [!UICONTROL Event owner]: `(input) reference for count`
* [!UICONTROL Event rank]: `Customer's recency score (R+F+M)`
* [!UICONTROL Filter]: `Customer's RFM score (by percentile)` nicht gleich 000

* Rangfolge nach dem RFM-Gesamtergebnis des Kunden
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer's overall RFM score`, `Number of customers (RFM > 0)`
* [!UICONTROL Calculation]: `case when A is null then null else (B-(A-1)) end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

* RFM-Gruppe des Kunden
* [!UICONTROL Column type]: `Same table > Calculation`
* [!UICONTROL Inputs]: `(input) Ranking by customer lifetime revenue`, `Number of customers`
* [!UICONTROL Calculation]: `Case when round(A * 100/B,0) <= 20 then '5. copper' when round(A * 100/B,0) <= 40 then '4. bronze' when round(A * 100/B,0) <= 60 then '3. silver' when round(A * 100/B,0)<= 80 then '2. gold' else '1. Platinum' end`
* &#x200B;
  [!UICONTROL Datentyp]: `Integer`

>[!NOTE]
>
>Die verwendeten Perzentile sind sogar Aufspaltungen von Kundinnen und Kunden (z. B. 20 Prozent Buckets , um 1-5 zurückzugeben). Wenn Sie eine benutzerdefinierte Methode zur Gewichtung verwenden möchten, teilen Sie dies dem Analyst mit, wenn Sie das Ticket senden.

## Metriken

Keine neuen Metriken!

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **Kunden nach RFM-Gruppierung**
* `A`: `New customers`
* [!UICONTROL Metric]: `New customers`
* [!UICONTROL Filter]: `Customer's RFM score (by percentiles) Not Equal to 000`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* Diagramm ausblenden
* [!UICONTROL Group by]: `Customer's RFM group`
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Email`
* &#x200B;
  [!UICONTROL Chart type]: `Table`

* **Kunden mit fünf Neuigkeiten**
* `A`: `New customers`
* [!UICONTROL Metric]: `New customers`
* [!UICONTROL Filter]: `Customer's recency score (by percentiles) Equal to 5`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* &#x200B;
  [!UICONTROL Chart Type]: `Scalar`
* Diagramm ausblenden
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Email`
* [!UICONTROL Group by]: `Customer's RFM score (R+F+M)`
* &#x200B;
  [!UICONTROL Chart type]: `Table`

* **Kunden mit einem Recency Score**
* `A`: `New customers`
* [!UICONTROL Metric]: `New customers`
* [!UICONTROL Filter]: `Customer's recency score (by percentiles) Equal to 1`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* &#x200B;
  [!UICONTROL Chart Type]: `Scalar`
* Diagramm ausblenden
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Email`
* [!UICONTROL Group by]: `Customer's RFM score (R+F+M)`
* &#x200B;
  [!UICONTROL Chart type]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis mag wie im obigen Beispiel-Dashboard aussehen, aber die drei generierten Tabellen sind nur Beispiele für die Arten der Kundensegmentierung, die Sie durchführen können.
