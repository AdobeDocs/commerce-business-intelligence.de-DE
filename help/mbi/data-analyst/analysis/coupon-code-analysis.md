---
title: Couponleistung
description: Erfahren Sie mehr über die Analyse Ihrer Couponleistung.
exl-id: f6565e33-18ee-4f85-ade0-fd361854475b
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: d8fc96a58b72c601a5700f35ea1f3dc982d76571
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---

# Erweiterte Coupon-Code-Analyse

Das Verständnis der Couponleistung Ihres Unternehmens ist eine interessante Möglichkeit, Ihre Bestellungen zu unterteilen und auch Ihre Kunden besser zu verstehen. Dieses Thema führt Sie durch die Schritte zum Erstellen von Analysen, um zu verstehen, welche Kunden Sie mit Coupons erwerben, wie sie die allgemeine Nutzung von Coupons durchführen und verfolgen.

![](../../assets/coupon_analysis_-_analysis_library.png)<!--{: width="800" height="375"}-->

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Als ersten Schritt müssen Sie sicherstellen, dass die folgenden Spalten mit Ihrer Data Warehouse synchronisiert werden. Ist dies nicht der Fall, führen Sie eine Verfolgung durch, indem Sie zu `Manage Data` > `Data Warehouse` navigieren und Folgendes synchronisieren:

* Tabelle **sales\_flach\_order**
* **coupon\_code**
* **base\_discount\_amount**

## Berechnete Spalten

Spalten, die unabhängig von der Gastbestellungsrichtlinie erstellt werden sollen:

* `sales\_flat\_order` table
* **Der Coupon wurde angewendet?**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `coupon\_code`

   * 
     [!UICONTROL Datatype]: `String`
   * [!UICONTROL Calculation]: Wenn `A` null ist, dann `No coupon` else `Coupon` end

* **\[INPUT\] customer\_id - Couponcode**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `customer\_id`
      * `B`: `coupon\_code`

   * [!UICONTROL Datatype] Zeichenfolge
   * [!UICONTROL Calculation]: `concat(A,' - ',B)`

* **Anzahl der Bestellungen mit diesem Coupon**
   * [!UICONTROL Column type]: `Same Table => EVENT\_NUMBER`
   * Ereigniseigentümer:`INPUT customer_id - coupon code`
   * Ereignis-Rang: `created\_at`
   * [!UICONTROL Filters]: `Orders we count` Filtersatz

Zusätzliche Spalten, die erstellt werden, wenn Gastaufträge NICHT unterstützt werden:

* `customer\_entity` table
   * **Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon)**
   * [!UICONTROL Column type]: `Many to One => MAX`
   * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
   * Wählen Sie einen [!UICONTROL column]: `Order has coupon applied? (Coupon/No coupon)`
   * [!UICONTROL Filters]:
      * `A`: `Orders we count`
      * `B`: `Customer's order number = 1`

   * **Coupon des Kunden für die erste Bestellung**
      * [!UICONTROL Column type]: `Many to One => MAX`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * Wählen Sie einen [!UICONTROL column]: `coupon\_code`
      * [!UICONTROL Filter]:
         * `A`: `Orders we count`
         * `B`: `Customer's order number = 1`

   * **Anzahl der verwendeten Coupons während der Lebensdauer des Kunden**
      * [!UICONTROL Column type]: `Many to One => COUNT`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * [!UICONTROL Filter]:
         * `A`: `Orders we count`
         * `B`: `Order has coupon applied? (Coupon/No coupon) = Coupon`

   * **Akquise-Kunde oder Akquise-Kunde ohne Coupon**
      * [!UICONTROL Column type]: `Same Table => CALCULATION`
      * [!UICONTROL Inputs]:
         * `A`: `Customer's first order included a coupon? (Coupon/No coupon)`

      * 
        [!UICONTROL Datatype]: `String`
      * [!UICONTROL Calculation]: **Fall, wenn A=&#39;Coupon&#39;, dann &#39;Coupon-Akquise-Kunde&#39;, andernfalls &#39;Nicht-Coupon-Akquise-Kunde&#39; Ende**

   * **Prozentsatz der Bestellungen des Kunden mit Coupon**
      * [!UICONTROL Column type]: `Same Table => CALCULATION`
      * [!UICONTROL Inputs]:
         * `A`: `User's lifetime number of coupons used`
         * `B`: `User's lifetime number of orders`

      * 
        [!UICONTROL Datatype]: `Decimal`
      * [!UICONTROL Calculation]: **Fall, wenn A null oder B null oder B=0 ist, dann null andernfalls A/B end**

   * **Nutzung des Gutscheins durch den Kunden**
      * [!UICONTROL Column type]: `Same Table => Calculation`
      * [!UICONTROL Inputs]:
         * `A`: `Percent of customer's orders with coupon`

      * 
        [!UICONTROL Datatype]: `String`
      * [!UICONTROL Calculation]: **Fall, wenn A null ist, dann null bei A=0, dann bei A&lt;0.5 &quot;Coupon nie verwendet&quot;, dann bei A&lt;0.5 &quot;Nahezu vollständiger Preis&quot; bei A=0.5, dann bei A=1 &quot;50/50&quot; bei A=1, dann bei A>0.5 &quot;Coupons&quot;und dann bei &quot;Nahezu Coupon&quot;bei nicht definiertem Ende**

* `sales\_flat\_order` table
   * **Der erste Auftrag des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon)**
      * [!UICONTROL Column type]: `One to Many => JOINED\_COLUMN`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * Wählen Sie einen [!UICONTROL column]: `Customer's first order included a coupon? (Coupon/No coupon)`
^

   * **Coupon des Kunden für die erste Bestellung**
      * [!UICONTROL Column type]: `One to Many => JOINED\_COLUMN`
      * [!UICONTROL Path]: `sales\_flat\_order.customer\_id = customer\_entity.entity\_id`
      * Wählen Sie einen [!UICONTROL column]: `Customer's first order coupon?`

Zusätzliche Spalten, die erstellt werden, wenn Gastaufträge NICHT unterstützt werden:

* `sales\_flat\_order` table
   * **Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon)** **-**, der von einem Analytiker im Rahmen Ihres \[COUPON ANALYSIS\]-Tickets erstellt wurde
   * **Coupon des Kunden für die erste Bestellung**{::}**-**, der vom Analytiker im Rahmen Ihres \[COUPON ANALYSIS\]-Tickets erstellt wurde

* **Anzahl der vom Kunden verwendeten Gutscheine für die Lebensdauer**{::}**-**, die vom Analytiker im Rahmen Ihres \[COUPON ANALYSIS\]-Tickets erstellt wurden
* **Akquise-Kunde oder Akquise-Kunde ohne Coupon**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `Customer's first order included a coupon? (Coupon/No coupon)`

   * 
     [!UICONTROL Datatype]: `String`
   * [!UICONTROL Calculation]: **Fall, wenn A=&#39;Coupon&#39;, dann &#39;Coupon-Akquise-Kunde&#39;, andernfalls &#39;Nicht-Coupon-Akquise-Kunde&#39; Ende**

* **Prozentsatz der Bestellungen des Kunden mit Coupon**
   * [!UICONTROL Column type]: `Same Table => CALCULATION`
   * [!UICONTROL Inputs]:
      * `A`: `User's lifetime number of coupons used`
      * `B`: `User's lifetime number of orders`

   * 
     [!UICONTROL Datatype]: `Decimal`
   * [!UICONTROL Calculation]: **Fall, wenn A null oder B null oder B=0 ist, dann null andernfalls A/B end**

* **Nutzung des Gutscheins durch den Kunden**
   * [!UICONTROL Column type]: `Same Table => Calculation`
   * [!UICONTROL Inputs]:
      * `A`: `Percent of customer's orders with coupon`

   * 
     [!UICONTROL Datatype]: `String`
   * [!UICONTROL Calculation]: **Fall, wenn A null ist, dann null bei A=0, dann bei A&lt;0.5 &quot;Coupon nie verwendet&quot;, dann bei A&lt;0.5 &quot;Nahezu vollständiger Preis&quot; bei A=0.5, dann bei A=1 &quot;50/50&quot; bei A=1, dann bei A>0.5 &quot;Coupons&quot;und dann bei &quot;Nahezu Coupon&quot;bei nicht definiertem Ende**

## Metriken

* **Rabattbetrag für Coupons**
   * `Orders we count`
   * `Order has coupon applied? (Coupon/No coupon)= Coupon`

* In der Tabelle `sales\_flat\_order`
* Diese Metrik führt eine **Summe** aus.
* In der Spalte `discount\_amount`
* Durch den Zeitstempel `created\_at` geordnet
* [!UICONTROL Filter]:

* **Anzahl der verwendeten Gutscheine**
   * `Orders we count`
   * `Order has coupon applied? (Coupon/No coupon)= Coupon`

* In der Tabelle `sales\_flat\_order`
* Diese Metrik führt eine **Zählung** aus
* In der Spalte `entity\_id`
* Durch den Zeitstempel `created\_at` geordnet
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

## Berichte

* **% der mit Coupons erworbenen und nicht mit Coupons erworbenen Kunden**
   * [!UICONTROL Metric]: `New customers`

* Metrik `A`: `Coupon acquisitions`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Coupon acquisitions customer` oder `Non coupon acquisition customer`
* 
  [!UICONTROL Diagrammtyp]: `Pie`

* **Anzahl der mit Coupons erworbenen und nicht mit Coupons erworbenen Kunden**
   * [!UICONTROL Metric]: `New customers`

* Metrik A: `Coupon acquisitions`
* [!UICONTROL Time period]: `All time`
* [!UICONTROL Interval]: `By Month`
* [!UICONTROL Group by]: `Coupon acquisitions customer` oder `Non coupon acquisition customer`
* [!UICONTROL Chart type]: `Stacked column`

* **Durchschnittlicher Umsatz während der Lebensdauer: Coupon-Acq. (90+ Tage alt)**
   * [!UICONTROL Metric]: `Average lifetime revenue`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Coupon

* Metrik `A`: `Average lifetime revenue (at least 3 months age)`
* [!UICONTROL Time period]: `X years ago to 90 days ago`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Durchschnittlicher Umsatz während der Lebensdauer: Nicht-Coupon-Acq. (90+ Tage alt)**
   * [!UICONTROL Metric]: Durchschnittlicher Umsatz während der Lebensdauer
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Kein Coupon

* Metrik `A`: `Average lifetime revenue (at least 3 months age)`
* [!UICONTROL Time period]: `X years ago to 90 days ago`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Durchschnittlicher Umsatz während der Lebensdauer nach Coupon der ersten Bestellung**
   * [!UICONTROL Metric]: `Average lifetime revenue`

* Metrik `A`: `Average lifetime revenue`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's first order's coupon`
* 
  [!UICONTROL Diagrammtyp]: `Column`

>[!NOTE]
>
>Wenn Sie wie viele Kunden über viele Couponcodes verfügen, sollten Sie einen Top-/Bottom-Ansatz (z. B. Top 10) anwenden, der nach dem durchschnittlichen Umsatz während der Lebensdauer sortiert ist.

* **Wiederholungsbestellwahrscheinlichkeit: Couponakquisitionen**
   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Coupon

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Coupon
      * Ist die letzte Bestellung des Kunden? = Nein
   * 
     [!UICONTROL Formel]: `B/A`
   * [!UICONTROL Format]: `Percentage %`

   * Wählen Sie eine statistisch signifikante Zahl aus dem `Customer's by lifetime orders` Diagramm aus. Wenn Sie sich die Grafik ansehen, besteht eine gute Regel darin, nach Bestellnummern mit 30 oder mehr Kunden im Behälter zu suchen. Je nach Datensatz kann dies eine große Zahl sein. Sie können also 1-10 hinzufügen.

* Metrik `A`: `Number of orders`
* Metrik `B`: `Number of non last orders`
* [!UICONTROL Formula]: `Repeat order probability`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's order number`
* [!UICONTROL Chart type]: `Bar chart`

* **Wiederholungsbestellwahrscheinlichkeit: Nichtkupon-Akquise**
   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Kein Coupon

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Die erste Bestellung des Kunden enthielt einen Coupon (Coupon/Kein Coupon) = Kein Coupon
      * Ist die letzte Bestellung des Kunden? = Nein

   * 
     [!UICONTROL Formel]: `B/A`
   * [!UICONTROL Format]: `Percentage %`

   * Wählen Sie eine statistisch signifikante Zahl aus dem `Customer's by lifetime orders` Diagramm oder 1-5 aus.

* Metrik `A`: `Number of orders`
* Metrik `B`: `Number of non last orders`
* [!UICONTROL Formula]: `Repeat order probability`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's order number`
* [!UICONTROL Chart type]: `Bar chart`

* **Couponverwendungsrate von durch Gutscheine erworbenen Kunden (Wiederholungsaufträge)**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filter]:
      * Couponakquise-Kunde oder Nicht-Couponakquise-Kunde = Couponakquise-Akquise

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Kundennummer > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Coupon

   * [!UICONTROL Metric]:`Number of orders`
   * [!UICONTROL Filter]:
      * Kundennummer > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Coupon
      * Auf die Bestellung wurde Coupon angewendet? (Coupon/Kein Coupon) = Coupon

   * 
     [!UICONTROL Formel]: `C/B`
   * [!UICONTROL Format]: `Percentage %`

* Metrik `A`: `Coupon-acquired customers`
* Metrik `B`: `Number of repeat orders`
* Metrik `C`: `Number of repeat orders with coupon`
* [!UICONTROL Formula]: `% of repeat orders with coupon`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Table` (kann diese Tabelle für eine bessere Visualisierung übertragen)

* **Couponverwendungsrate nicht mit Coupons erworbener Kunden (Wiederholungsaufträge)**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filter]:
      * Couponakquise-Kunde oder Nicht-Couponakquise-Kunde = Nicht-Couponakquise-Akquise

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Kundennummer > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Kein Coupon

   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Kundennummer > 1
      * Die erste Bestellung des Kunden enthielt einen Gutschein? (Coupon/Kein Coupon) = Kein Coupon
      * Auf die Bestellung wurde Coupon angewendet? (Coupon/Kein Coupon) = Coupon

   * 
     [!UICONTROL Formel]: `C/B`
   * [!UICONTROL Format]: `Percentage %`

* Metrik `A`: `Non-coupon-acquired customers`
* Metrik `B`: `Number of repeat orders`
* Metrik `C`: `Number of repeat orders with coupon`
* [!UICONTROL Formula]: `% of repeat orders with coupon`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Table` (kann diese Tabelle für eine bessere Visualisierung übertragen)

* **Nutzungsdetails des Coupons (Erstbestellungen)**
   * [!UICONTROL Metric]: `Number of orders`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * 
     [!UICONTROL Metrik]: `Revenue`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * [!UICONTROL Metric]: `Coupon discount amount`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * [!UICONTROL Formula]: `B-C` (wenn C negativ ist); B+C (wenn C positiv ist)
   * 
     [!UICONTROL Format]: `Currency`

   * [!UICONTROL Metric]: `Average order value`
   * [!UICONTROL Filter]:
      * Bestellnummer des Kunden = 1
      * Anzahl der Bestellungen mit diesem Gutschein > 10

* Metrik `A`: `First time orders (FTO)`
* Metrik `B`: `Revenue from FTO`
* Metrik `C`: `Discounts applied to FTO`
* [!UICONTROL Formula]: `Gross revenue from FTO`
* Metrik `E`: `Average order value for FTO`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `coupon code`
* 
  [!UICONTROL Diagrammtyp]: `Table`
>[!NOTE]
>
>Die Menge von 10 für &quot;Anzahl der Bestellungen mit diesem Gutschein&quot;ist willkürlich. Sie können die für diesen Filter am besten geeignete Menge verwenden.

* **Anzahl der Bestellungen mit Coupon (ganze Zeit)**
   * [!UICONTROL Metric]: `Number of coupons used`

* Metrik `A`: `Number or orders with coupon`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Nettoumsatz aus Bestellungen mit Coupons (alle Zeit)**
   * 
     [!UICONTROL Metrik]: `Revenue`
   * [!UICONTROL Filter]:
      * Auf die Bestellung wurde Coupon angewendet? (Coupon/Kein Coupon) = Coupon

* Metrik `A`: `Net revenue from orders with coupons`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Rabatte aus Gutscheinen (immer)**
   * [!UICONTROL Metric]: `Number of coupons used`

* Metrik `A`: `Coupon discount amount`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Diagrammtyp]: `Scalar`

* **Anzahl der Bestellungen mit und ohne Coupons**
   * [!UICONTROL Metric]: `Number of orders`

* Metrik `A`: `Number of orders`
* [!UICONTROL Time period]: `Last 24 months`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Order has coupon applied? (Coupon/No coupon)`
* [!UICONTROL Chart type]: `Stacked column`

* **Nutzung des Coupons bei wiederkehrenden Benutzern**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filter]:
      * Kundenlebensdauer Anzahl von Bestellungen > 1

* Metrik `A`: `New customers`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's coupon usage`
* 
  [!UICONTROL Diagrammtyp]: `Pie`

* **Verwendungsdetails des Gutscheins**
   * [!UICONTROL Metric]: `Number of orders with coupon`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * 
     [!UICONTROL Metrik]: `Revenue`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * [!UICONTROL Metric]: `Coupon discount amount`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * [!UICONTROL Formula]: `B-C` (wenn `C` negativ ist); `B+C` (wenn `C` positiv ist)
   * 
     [!UICONTROL Format]: `Currency`

   * [!UICONTROL Formula]: `C/(B-C)` (wenn `C` negativ ist); `C/(B+C)` (wenn `C` positiv ist)
   * 
     [!UICONTROL Format]: `Percentage`

   * [!UICONTROL Metric]: `Average order value`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Gutschein > 10

   * 
     [!UICONTROL Formel]: `C/A`
   * 
     [!UICONTROL Format]: `Currency`

   * [!UICONTROL Metric]: `Distinct buyers`
   * [!UICONTROL Filter]:
      * Anzahl der Bestellungen mit diesem Gutschein > 10

* Metrik `A`: `Number of orders`
* Metrik `B`: `Net revenue from orders`
* Metrik `C`: `Total discounts applied`
* [!UICONTROL Formula]: `Gross revenue`
* [!UICONTROL Formula]: `% discounted`
* Metrik `F`: `Average net order value`
* [!UICONTROL Formula]: `Average order discount`
* Metrik `H`: `Distinct buyers`
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `coupon code`
* 
  [!UICONTROL Diagrammtyp]: `Table`

>[!NOTE]
>
>Die Menge von 10 für &quot;Anzahl der Bestellungen mit diesem Gutschein&quot;ist willkürlich. Sie können die für diesen Filter am besten geeignete Menge verwenden.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das Bild oben auf der Seite aussehen.

Wenn Sie beim Erstellen dieser Analyse Fragen haben oder einfach das Professional Services-Team kontaktieren möchten, wenden Sie sich an den Support [.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)

>[!NOTE]
>
>Ab Adobe Commerce 2.4.7 können Kunden die Tabellen **Anführungszeichen** und **sales_order_coupons** verwenden, um Einblicke dazu zu erhalten, wie Kunden mehrere Gutscheine verwenden.

![](../../assets/multicoupon_relationship_tables.png)
