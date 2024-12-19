---
title: Couponleistung
description: Erfahren Sie mehr über die Analyse der Couponleistung.
exl-id: f6565e33-18ee-4f85-ade0-fd361854475b
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: d8fc96a58b72c601a5700f35ea1f3dc982d76571
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---

# Erweiterte Couponcode-Analyse

Die Couponleistung Ihres Unternehmens zu verstehen, ist eine interessante Möglichkeit, Ihre Bestellungen zu segmentieren und auch Ihre Kunden besser zu verstehen. Dieses Thema führt Sie durch die Schritte zum Erstellen von Analysen, um zu verstehen, welche Kunden Sie mit Coupons gewinnen, wie diese funktionieren und wie die allgemeine Couponnutzung verfolgt wird.

![](../../assets/coupon_analysis_-_analysis_library.png)<!--{: width="800" height="375"}-->

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Als ersten Schritt müssen Sie sicherstellen, dass die folgenden Spalten mit Ihrem Data Warehouse synchronisiert werden. Wenn nicht, verfolgen Sie sie, indem Sie zu `Manage Data` > `Data Warehouse` navigieren und Folgendes synchronisieren:

* **sales\_flat\_order** Tabelle
* **Coupon\_code**
* **BASE\_DISCOUNT\_AMOUNT**

## Berechnete Spalten

Unabhängig von der Gastauftragsrichtlinie zu erstellende Spalten:

* `sales\_flat\_order`
* **Hat die Bestellung einen Coupon angewendet?**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `coupon\_code`

   * 
     [!UICONTROL Datentyp]: `String`
   * [!UICONTROL Calculation]: Wenn `A` null ist, wird `No coupon` andere `Coupon` beendet

* **\[INPUT\] customer\_id - Gutscheincode**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `customer\_id`
      * `B`: `coupon\_code`

   * [!UICONTROL Datatype]
   * [!UICONTROL Calculation]: `concat(A,' - ',B)`

* **Anzahl der Bestellungen mit diesem Coupon**
   * [!UICONTROL Column type]: `Same Table => EVENT\_NUMBER`
   * Ereignisbesitzer:`INPUT customer_id - coupon code`
   * Ereignisrang: `created\_at`
   * [!UICONTROL Filters]: Filtersatz `Orders we count`

Zusätzliche Spalten, die erstellt werden, wenn keine Gastbestellungen unterstützt werden:

* `customer\_entity`
   * **Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon)**
   * [!UICONTROL Column type]: `Many to One => MAX`
   * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
   * [!UICONTROL column] auswählen: `Order has coupon applied? (Coupon/No coupon)`
   * [!UICONTROL Filters]:
      * `A`: `Orders we count`
      * `B`: `Customer's order number = 1`

   * **Gutschein der ersten Bestellung des Kunden**
      * [!UICONTROL Column type]: `Many to One => MAX`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * [!UICONTROL column] auswählen: `coupon\_code`
      * [!UICONTROL Filter]:
         * `A`: `Orders we count`
         * `B`: `Customer's order number = 1`

   * **Lebensdauernummer des Kunden bzw. der Kundin, wie viele Coupons verwendet wurden**
      * [!UICONTROL Column type]: `Many to One => COUNT`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * [!UICONTROL Filter]:
         * `A`: `Orders we count`
         * `B`: `Order has coupon applied? (Coupon/No coupon) = Coupon`

   * **Coupon-Akquise-Kunde oder Nicht-Coupon-Akquise-Kunde**
      * [!UICONTROL Column type]: `Same Table => CALCULATION`
      * [!UICONTROL Inputs]:
         * `A`: `Customer's first order included a coupon? (Coupon/No coupon)`

      * 
        [!UICONTROL Datentyp]: `String`
      * [!UICONTROL Calculation]: **Wenn A=&#39;Coupon&#39; dann &#39;Coupon-Akquise-Kunde&#39; Sonst &#39;Nicht-Coupon-Akquise-Kunde&#39; Ende**

   * **Prozent der Kundenbestellungen mit Coupon**
      * [!UICONTROL Column type]: `Same Table => CALCULATION`
      * [!UICONTROL Inputs]:
         * `A`: `User's lifetime number of coupons used`
         * `B`: `User's lifetime number of orders`

      * 
        [!UICONTROL Datentyp]: `Decimal`
      * [!UICONTROL Calculation]: **Wenn A null oder B null oder B=0 ist, dann ist ansonsten A/B-Ende null**

   * **Couponnutzung des Kunden**
      * [!UICONTROL Column type]: `Same Table => Calculation`
      * [!UICONTROL Inputs]:
         * `A`: `Percent of customer's orders with coupon`

      * 
        [!UICONTROL Datentyp]: `String`
      * [!UICONTROL Calculation]: **Wenn A null ist, dann null, wenn A=0 dann „Nie verwendeter Coupon“ ist, wenn A&lt;0,5 dann „Meistens voller Preis“ ist, wenn A=0,5 dann „50/50“ ist, wenn A=1 dann „Nur Coupons“ ist, wenn A>0,5 dann „Meistens Coupon“ oder „Nicht definiert“ endet**

* `sales\_flat\_order`
   * **Die erste Bestellung des Kunden enthält einen Gutschein? (Coupon/Kein Coupon)**
      * [!UICONTROL Column type]: `One to Many => JOINED\_COLUMN`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * [!UICONTROL column] auswählen: `Customer's first order included a coupon? (Coupon/No coupon)`
^

   * **Gutschein der ersten Bestellung des Kunden**
      * [!UICONTROL Column type]: `One to Many => JOINED\_COLUMN`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * [!UICONTROL column] auswählen: `Customer's first order coupon?`

Zusätzliche Spalten, die erstellt werden, wenn keine Gastbestellungen unterstützt werden:

* `sales\_flat\_order`
   * **Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon)** **-** von Analyst im Rahmen Ihres \[COUPON ANALYSIS\] Tickets erstellt
   * **Der Gutschein des Kunden für die erste Bestellung**{::}**-** wurde von Analyst im Rahmen Ihres \[COUPON ANALYSIS\]-Tickets erstellt

* **Anzahl der Gutscheine, die während der gesamten Lebensdauer des Kunden verwendet**{::}**-**, erstellt von Analyst im Rahmen Ihres \[COUPON ANALYSIS\]-Tickets
* **Coupon-Akquise-Kunde oder Nicht-Coupon-Akquise-Kunde**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `Customer's first order included a coupon? (Coupon/No coupon)`

   * 
     [!UICONTROL Datentyp]: `String`
   * [!UICONTROL Calculation]: **Wenn A=&#39;Coupon&#39; dann &#39;Coupon-Akquise-Kunde&#39; Sonst &#39;Nicht-Coupon-Akquise-Kunde&#39; Ende**

* **Prozent der Kundenbestellungen mit Coupon**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `User's lifetime number of coupons used`
      * `B`: `User's lifetime number of orders`

   * 
     [!UICONTROL Datentyp]: `Decimal`
   * [!UICONTROL Calculation]: **Wenn A null oder B null oder B=0 ist, dann ist ansonsten A/B-Ende null**

* **Couponnutzung des Kunden**
   * [!UICONTROL Column type]: `Same Table => Calculation`
   * [!UICONTROL Inputs]:
      * `A`: `Percent of customer's orders with coupon`

   * 
     [!UICONTROL Datentyp]: `String`
   * [!UICONTROL Calculation]: **Wenn A null ist, dann null, wenn A=0 dann „Nie verwendeter Coupon“ ist, wenn A&lt;0,5 dann „Meistens voller Preis“ ist, wenn A=0,5 dann „50/50“ ist, wenn A=1 dann „Nur Coupons“ ist, wenn A>0,5 dann „Meistens Coupon“ oder „Nicht definiert“ endet**

## Metriken

* **Coupon-Rabattbetrag**
   * `Orders we count`
   * `Order has coupon applied? (Coupon/No coupon)= Coupon`

* In der `sales\_flat\_order`
* Diese Metrik führt eine **Summe“**
* In der Spalte `discount\_amount`
* Sortiert nach dem `created\_at` Zeitstempel
* [!UICONTROL Filter]:

* **Anzahl der verwendeten Coupons**
   * `Orders we count`
   * `Order has coupon applied? (Coupon/No coupon)= Coupon`

* In der `sales\_flat\_order`
* Diese Metrik führt eine **Anzahl** aus
* In der Spalte `entity\_id`
* Sortiert nach dem `created\_at` Zeitstempel
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher[ dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **% der mit und ohne Coupon erworbenen Kunden**
   * [!UICONTROL Metric]: `New customers`

* `A`: `Coupon acquisitions`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Coupon acquisitions customer` oder `Non coupon acquisition customer`
* 
  [!UICONTROL Diagrammtyp]: `Pie`

* **Anzahl der mit und ohne Coupon erworbenen Kunden**
   * [!UICONTROL Metric]: `New customers`

* Metrik A: `Coupon acquisitions`
* [!UICONTROL Time period]: `All time`
* [!UICONTROL Interval]: `By Month`
* [!UICONTROL Group by]: `Coupon acquisitions customer` oder `Non coupon acquisition customer`
* [!UICONTROL Chart type]: `Stacked column`

* **Durchschnittlicher Lebensdauerumsatz: Coupon Acq. (Alter ab 90 Tagen)**
   * [!UICONTROL Metric]: `Average lifetime revenue`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Coupon

* `A`: `Average lifetime revenue (at least 3 months age)`
* [!UICONTROL Time period]: `X years ago to 90 days ago`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Durchschnittlicher Lebensdauerumsatz: Acq ohne Coupon. (Alter ab 90 Tagen)**
   * [!UICONTROL Metric]: Durchschnittlicher Lebensdauerumsatz
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/No Coupon) = No Coupon

* `A`: `Average lifetime revenue (at least 3 months age)`
* [!UICONTROL Time period]: `X years ago to 90 days ago`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Durchschnittlicher Lebensdauerumsatz nach Erstbestellung**
   * [!UICONTROL Metric]: `Average lifetime revenue`

* `A`: `Average lifetime revenue`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's first order's coupon`
* 
  [!UICONTROL Diagrammtyp]: `Column`

>[!NOTE]
>
>Wenn Sie wie viele Kunden viele Gutscheincodes haben, sollten Sie eine Top/Bottom-Regel anwenden, z. B. Top 10 sortiert nach dem durchschnittlichen Lebensdauerumsatz

* **Wahrscheinlichkeit der Wiederholungsreihenfolge: Couponakquisitionen**
   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Coupon

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Coupon
      * Ist die letzte Bestellung des Kunden? = Nein
   * 
     [!UICONTROL-Formel]: `B/A`
   * [!UICONTROL Format]: `Percentage %`

   * Wählen Sie eine statistisch signifikante Zahl aus `Customer's by lifetime orders` Diagramm. Wenn Sie sich die Grafik ansehen, ist eine gute Regel, nach Auftragsnummern mit 30 oder mehr Kunden im Bucket zu suchen. Je nach Datensatz kann dies eine große Zahl sein. Sie können also 1-10 hinzufügen.

* `A`: `Number of orders`
* `B`: `Number of non last orders`
* [!UICONTROL Formula]: `Repeat order probability`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's order number`
* [!UICONTROL Chart type]: `Bar chart`

* **Wiederholungsauftragswahrscheinlichkeit: Nicht-Coupon-Akquisitionen**
   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/No Coupon) = No Coupon

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/No Coupon) = No Coupon
      * Ist die letzte Bestellung des Kunden? = Nein

   * 
     [!UICONTROL-Formel]: `B/A`
   * [!UICONTROL Format]: `Percentage %`

   * Wählen Sie eine statistisch signifikante Zahl aus `Customer's by lifetime orders` Diagramm oder 1-5.

* `A`: `Number of orders`
* `B`: `Number of non last orders`
* [!UICONTROL Formula]: `Repeat order probability`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's order number`
* [!UICONTROL Chart type]: `Bar chart`

* **Couponnutzungsrate erworbener Kunden (Wiederholungsaufträge)**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filter]:
      * Coupon-Akquise-Kunde oder Nicht-Coupon-Akquise-Kunde = Coupon-Akquise

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Coupon

   * [!UICONTROL Metric]:`Number of orders`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Coupon
      * Bestellung mit Coupon angewendet? (Coupon/Kein Coupon) = Coupon

   * 
     [!UICONTROL-Formel]: `C/B`
   * [!UICONTROL Format]: `Percentage %`

* `A`: `Coupon-acquired customers`
* `B`: `Number of repeat orders`
* `C`: `Number of repeat orders with coupon`
* [!UICONTROL Formula]: `% of repeat orders with coupon`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Table` (Kann diese Tabelle für eine bessere Visualisierung umsetzen)

* **Couponnutzungsrate nicht mit Coupons erworbener Kunden (Wiederholungsaufträge)**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filter]:
      * Coupon-Akquise-Kunde oder Nicht-Coupon-Akquise-Kunde = Nicht-Coupon-Akquise

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Kein Coupon

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Kein Coupon
      * Bestellung mit Coupon angewendet? (Coupon/Kein Coupon) = Coupon

   * 
     [!UICONTROL-Formel]: `C/B`
   * [!UICONTROL Format]: `Percentage %`

* `A`: `Non-coupon-acquired customers`
* `B`: `Number of repeat orders`
* `C`: `Number of repeat orders with coupon`
* [!UICONTROL Formula]: `% of repeat orders with coupon`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Table` (Kann diese Tabelle für eine bessere Visualisierung umsetzen)

* **Details zur Couponnutzung (Erstbestellungen)**
   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * 
     [!UICONTROL-Metrik]: `Revenue`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * [!UICONTROL Metric]: `Coupon discount amount`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * [!UICONTROL Formula]: `B-C` (wenn C negativ ist); B+C (wenn C positiv ist)
   * 
     [!UICONTROL-Format]: `Currency`

   * [!UICONTROL Metric]: `Average order value`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Coupon > 10

* `A`: `First time orders (FTO)`
* `B`: `Revenue from FTO`
* `C`: `Discounts applied to FTO`
* [!UICONTROL Formula]: `Gross revenue from FTO`
* `E`: `Average order value for FTO`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `coupon code`
* 
  [!UICONTROL Diagrammtyp]: `Table`
>[!NOTE]
>
>Die Menge von 10 für „Anzahl der Bestellungen mit diesem Coupon“ ist willkürlich. Verwenden Sie für diesen Filter die am besten geeignete Menge.

* **Anzahl der Bestellungen mit Coupon (alle Zeiten)**
   * [!UICONTROL Metric]: `Number of coupons used`

* `A`: `Number or orders with coupon`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Nettoumsatz aus Bestellungen mit Coupons (alle Zeiten)**
   * 
     [!UICONTROL-Metrik]: `Revenue`
   * [!UICONTROL Filter]:
      * Bestellung mit Coupon angewendet? (Coupon/Kein Coupon) = Coupon

* `A`: `Net revenue from orders with coupons`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Rabatte auf Gutscheine (alle Zeiten)**
   * [!UICONTROL Metric]: `Number of coupons used`

* `A`: `Coupon discount amount`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Anzahl der Bestellungen mit und ohne Coupons**
   * [!UICONTROL Metric]: `Number of orders`

* `A`: `Number of orders`
* [!UICONTROL Time period]: `Last 24 months`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Order has coupon applied? (Coupon/No coupon)`
* [!UICONTROL Chart type]: `Stacked column`

* **Couponnutzung unter Wiederholungsbenutzern**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen über die gesamte Kundenlebensdauer > 1

* `A`: `New customers`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's coupon usage`
* 
  [!UICONTROL Diagrammtyp]: `Pie`

* **Details zur Couponnutzung**
   * [!UICONTROL Metric]: `Number of orders with coupon`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * 
     [!UICONTROL-Metrik]: `Revenue`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * [!UICONTROL Metric]: `Coupon discount amount`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * [!UICONTROL Formula]: `B-C` (wenn `C` negativ ist); `B+C` (wenn `C` positiv ist)
   * 
     [!UICONTROL-Format]: `Currency`

   * [!UICONTROL Formula]: `C/(B-C)` (wenn `C` negativ ist); `C/(B+C)` (wenn `C` positiv ist)
   * 
     [!UICONTROL-Format]: `Percentage`

   * [!UICONTROL Metric]: `Average order value`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Coupon > 10

   * 
     [!UICONTROL-Formel]: `C/A`
   * 
     [!UICONTROL-Format]: `Currency`

   * [!UICONTROL Metric]: `Distinct buyers`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Coupon > 10

* `A`: `Number of orders`
* `B`: `Net revenue from orders`
* `C`: `Total discounts applied`
* [!UICONTROL Formula]: `Gross revenue`
* [!UICONTROL Formula]: `% discounted`
* `F`: `Average net order value`
* [!UICONTROL Formula]: `Average order discount`
* `H`: `Distinct buyers`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `coupon code`
* 
  [!UICONTROL Diagrammtyp]: `Table`

>[!NOTE]
>
>Die Menge von 10 für „Anzahl der Bestellungen mit diesem Coupon“ ist willkürlich. Verwenden Sie für diesen Filter die am besten geeignete Menge.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie das Bild oben auf der Seite aussehen.

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [ sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

>[!NOTE]
>
>Ab Adobe Commerce 2.4.7 können Kunden die Tabellen **quote_coupons** und **sales_order_coupons** verwenden, um Einblicke in die Verwendung mehrerer Gutscheine durch Kunden zu erhalten.

![](../../assets/multicoupon_relationship_tables.png)
