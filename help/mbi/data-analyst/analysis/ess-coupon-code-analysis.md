---
title: Analyse des Couponcodes (Basisversion)
description: Informieren Sie sich über die Couponleistung Ihres Unternehmens, um Ihre Bestellungen zu segmentieren und Kundengewohnheiten besser zu verstehen.
exl-id: 0d486259-b210-42ae-8f79-cd91cc15c2c2
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: d8fc96a58b72c601a5700f35ea1f3dc982d76571
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Grundlegende Analyse von Coupon-Codes

Das Verständnis der Couponleistung Ihres Unternehmens ist eine interessante Möglichkeit, Ihre Bestellungen zu unterteilen und Kundengewohnheiten besser zu verstehen.

In diesem Thema werden die Schritte beschrieben, die zur Erstellung dieser Analyse erforderlich sind, um die Leistung von mit Gutscheinen erworbenen Kunden zu verstehen, Trends zu sehen und die Verwendung von individuellen Gutscheincodes zu verfolgen.

![](../../assets/coupon_analysis_dash_720.png)<!--{: width="807" height="471"}-->

## Erste Schritte

Zunächst ein Hinweis zur Verfolgung von Coupon-Codes. Wenn ein Kunde einen Gutschein auf eine Bestellung angewendet hat, geschieht Folgendes:

* Ein Rabatt wird im Betrag `base_grand_total` angezeigt (Ihre Metrik `Revenue` in Commerce Intelligence).
* Der Gutscheincode wird im Feld `coupon_code` gespeichert. Wenn dieses Feld NULL (leer) ist, ist der Bestellung kein Gutschein zugeordnet.
* Der abgezinste Betrag wird in `base_discount_amount` gespeichert. Dieser Wert kann je nach Konfiguration negativ oder positiv aussehen.

Ab Commerce 2.4.7 kann ein Kunde mehr als einen Couponcode auf eine Bestellung anwenden. In diesem Fall:

* Alle angewendeten Couponcodes werden im Feld `coupon_code` von `sales_order_coupons` gespeichert. Der erste angewendete Couponcode wird ebenfalls im Feld `coupon_code` von `sales_order` gespeichert. Wenn dieses Feld NULL (leer) ist, ist der Bestellung kein Gutschein zugeordnet.

## Erstellen einer Metrik

Der erste Schritt besteht darin, eine neue Metrik mit den folgenden Schritten zu erstellen:

* Navigieren Sie zu **[!UICONTROL Manage Data > Metrics > Create New Metric]**.

* Wählen Sie den Wert `sales_order` aus.
* Diese Metrik führt eine **Summe** für die Spalte **base_discount_amount** aus, geordnet nach **created_at**.
   * [!UICONTROL Filters]:
      * Hinzufügen von &quot;`Orders we count`&quot;(gespeicherten Filtersatz)
      * Fügen Sie Folgendes hinzu:
         * `coupon_code`**IS NOT**`[NULL]`
      * Geben Sie der Metrik einen Namen, z. B. `Coupon discount amount`.

## Dashboard erstellen

* Nachdem die Metrik erstellt wurde:
   * Navigieren Sie zu [!UICONTROL Dashboards > Dashboard Options > Create New Dashboard]**.
   * Geben Sie dem Dashboard einen Namen wie `_Coupon Analysis_`.

* Hier können Sie alle Berichte erstellen und hinzufügen.

## Erstellen von Berichten

* **Neue Berichte:**

>[!NOTE]
>
>Die [!UICONTROL Time Period]** für jeden Bericht wird als `All-time` aufgelistet. Sie können dies nach Ihren Analyseanforderungen ändern. Adobe empfiehlt, dass alle Berichte in diesem Dashboard denselben Zeitraum abdecken, z. B. `All time`, `Year-to-date` oder `Last 365 days`.

* **Bestellungen mit Coupons**
   * 
     [!UICONTROL Metrik]: `Orders`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IST NICHT** `[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]:`Number (scalar)`

* **Bestellungen ohne Gutscheine**
   * 
     [!UICONTROL Metrik]: `Orders`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IS** `[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]:`Number (scalar)`

* **Nettoumsatz aus Bestellungen mit Coupons**
   * 
     [!UICONTROL Metrik]: `Revenue`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IST NICHT** `[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]: `Number (scalar)`

* **Rabatte aus Gutscheinen**
   * [!UICONTROL Metric]: `Coupon discount amount`
   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]: `Number (scalar)`

* **Durchschnittlicher Umsatz während der Lebensdauer: Mit Coupon erworbene Kunden**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
      * Filter hinzufügen:
         * [`A`] `Customer's first order's coupon_code` **IST NICHT** `[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]: `Number (scalar)`

* **Durchschnittlicher Umsatz während der Lebensdauer: Mit Kupon versehene Kunden**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
      * Filter hinzufügen:
         * [A] `Customer's first order's coupon_code` **IS**`[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]: `Number (scalar)`

* **Nutzungsdetails des Coupons (Erstbestellungen)**
   * Metrik `1`: `Orders`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IST NICHT**`[NULL]`
         * [`B`] `Customer's order number` **Entspricht** `1`

   * Metrik `2`: `Revenue`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IST NICHT**`[NULL]`
         * [`B`] `Customer's order number` **Entspricht** `1`

      * Umbenennen: `Net revenue`

   * Metrik `3`: `Coupon discount amount`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IST NICHT**`[NULL]`
         * [`B`] `Customer's order number` **Entspricht** `1`

   * Formel erstellen: `Gross revenue`
      * [!UICONTROL Formula]: `(B – C)`
      * 
        [!UICONTROL Format]: `Currency`

   * Formel erstellen:**% discount**
      * Formel: `(C / (B - C))`
      * 
        [!UICONTROL Format]: `Percentage`

   * Formel erstellen: `Average order discount`
      * [!UICONTROL Formula]: `(C / A)`
      * 
        [!UICONTROL Format]: `Percentage`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * 
     [!UICONTROL Diagrammtyp]: `Table`

* **Durchschnittlicher Umsatz während der Lebensdauer nach Coupon der ersten Bestellung**
   * [!UICONTROL Metric]:**Durchschnittlicher Umsatz während der Lebensdauer**
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IS**`[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Chart type]: `Number (scalar)`

* **Nutzungsdetails des Coupons (Erstbestellungen)**
   * [!UICONTROL Metric]: `Avg lifetime revenue`
      * Filter hinzufügen:
         * [`A`] `Customer's first order's coupon_code` **IST NICHT** `[NULL]`

   * [!UICONTROL Time period]: `All time`
   * 
     [!UICONTROL Intervall]: `None`
   * [!UICONTROL Group by]: `Customer's first order's coupon_code`
   * 
     [!UICONTROL Diagrammtyp]: **Column**

* **Neue Kunden nach Coupon-/Nicht-Couponakquise**
   * Metrik `1`: `New customers`
      * Filter hinzufügen:
         * [`A`] `Customer's first order's coupon_code` **IST NICHT** `[NULL]`

      * [!UICONTROL Rename]: `Coupon acquisition customer`

   * Metrik `2`: `New customers`
      * Filter hinzufügen:
         * [`A`] `coupon_code` **IS**`[NULL]`

      * [!UICONTROL Rename]: `Non-coupon acquisition customer`

   * [!UICONTROL Time period]: `All time`
   * [!UICONTROL Interval]: `By Month`
   * [!UICONTROL Chart type]: `Stacked Column`

Nachdem Sie die Berichte erstellt haben, erfahren Sie im Bild oben in diesem Thema, wie Sie die Berichte in Ihrem Dashboard organisieren können.

>[!NOTE]
>
>Ab Adobe Commerce 2.4.7 können Kunden die Tabellen **Anführungszeichen** und **sales_order_coupons** verwenden, um Einblicke dazu zu erhalten, wie Kunden mehrere Gutscheine verwenden.

![](../../assets/multicoupon_relationship_tables.png)
