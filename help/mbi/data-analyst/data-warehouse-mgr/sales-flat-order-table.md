---
title: sales_order-Tabelle
description: Erfahren Sie, wie Sie mit der Tabelle sales_order arbeiten.
exl-id: 19a8ab88-de51-48f8-af39-ae4897834afe
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 0%

---

# `sales_order` Verzeichnis

Die `sales_order` table (`sales_flat_order` auf M1) ist, wo jede Bestellung erfasst wird. Normalerweise stellt jede Zeile eine eindeutige Reihenfolge dar, obwohl es einige benutzerdefinierte Implementierungen von Commerce gibt, die dazu führen, dass eine Bestellung in separate Zeilen unterteilt wird.

Diese Tabelle enthält alle Kundenbestellungen, unabhängig davon, ob diese Bestellung über einen Gastkasse verarbeitet wurde. Wenn Ihr Geschäft einen Gast-Checkout akzeptiert, finden Sie weitere Informationen dazu [Anwendungsfall](../data-warehouse-mgr/guest-orders.md).

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_currency_code` | Währung für alle in `base_*` -Felder (das heißt `base_grand_total`, `base_subtotal`usw.). Dies spiegelt normalerweise die Standardwährung des Commerce-Stores wider |
| `base_discount_amount` | Auf Bestellung angewendeter Rabattwert |
| `base_grand_total` | Endpreis, der vom Kunden bei der Bestellung gezahlt wird, nach Anwendung aller Steuern, Versand und Rabatte. Obwohl die genaue Berechnung anpassbar ist, ist im Allgemeinen die `base_grand_total` berechnet als `base_subtotal` + `base_tax_amount` + `base_shipping_amount` `+` `base_discount_amount` `-` `base_gift_cards_amount` `-` `base_customer_balance_amount` |
| `base_subtotal` | Bruttokaufwert aller in der Bestellung enthaltenen Artikel. Steuern, Versand, Rabatte usw. sind nicht inbegriffen |
| `base_shipping_amount` | Auf Bestellung angewendeter Versandwert |
| `base_tax_amount` | Auf Bestellung angewendeter Steuerwert |
| `billing_address_id` | `Foreign key` mit `sales_order_address` Tabelle. Mitglied werden `sales_order_address.entity_id` zur Bestimmung der Rechnungsadressen, die mit der Bestellung verbunden sind |
| `coupon_code` | Auf Bestellung angewendeter Coupon. Wenn kein Coupon angewendet wird, wird dieses Feld `NULL` |
| `created_at` | Erstellungszeitstempel der Bestellung, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence], kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] , die sich von der Zeitzone Ihrer Datenbank unterscheidet |
| `customer_email` | E-Mail-Adresse des Bestellers. Dies wird in allen Situationen aufgefüllt, einschließlich der Bestellungen, die über den Gastkauf verarbeitet werden |
| `customer_group_id` | Fremdschlüssel, der mit dem `customer_group` Tabelle. Mitglied werden `customer_group.customer_group_id` zur Bestimmung der Kundengruppe, die der Bestellung zugeordnet ist |
| `customer_id` | `Foreign key` mit `customer_entity` -Tabelle, wenn der Kunde registriert ist. Mitglied werden `customer_entity.entity_id` , um Kundenattribute zu bestimmen, die mit der Bestellung verknüpft sind. Wenn die Bestellung über einen Gastkasse aufgegeben wurde, lautet dieses Feld `NULL` |
| `entity_id` (PK) | Eindeutige Kennung für die Tabelle und wird häufig in Verknüpfungen zu anderen Tabellen innerhalb der Commerce-Instanz verwendet |
| `increment_id` | Eindeutige Kennung für eine Bestellung, die häufig als `order_id` innerhalb von Adobe Commerce. Die `increment_id` wird am häufigsten für Verknüpfungen zu externen Quellen verwendet, z. B. [!DNL Google Ecommerce] |
| `shipping_address_id` | Fremdschlüssel, der mit dem `sales_order_address` Tabelle. Mitglied werden `sales_order_address.entity_id` zur Bestimmung der Versandadressen, die mit der Bestellung verbunden sind |
| `status` | Bestellstatus. Kann Werte wie &quot;complete&quot;, &quot;processing&quot;, &quot;cancelled&quot;, &quot;refund&quot;und alle benutzerdefinierten Status zurückgeben, die in der Commerce-Instanz implementiert sind. Vorbehaltlich Änderungen bei der Verarbeitung der Bestellung |
| `store_id` | `Foreign key` mit `store` Tabelle. Mitglied werden `store`.`store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit der Bestellung verknüpft ist. |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Billing address city` | Abrechnungsort für die Bestellung. Errechnet durch Verbinden `sales_order`.`billing_address_id` nach `sales_order_address`.`entity_id` und gibt die `city` field |
| `Billing address country` | Rechnungslandescode für die Bestellung. Errechnet durch Verbinden `sales_order`.`billing_address_id` nach `sales_order_address`.`entity_id` und gibt die `country_id` |
| `Billing address region` | Rechnungsregion (am häufigsten Bundesland oder Provinz) für die Bestellung. Errechnet durch Verbinden `sales_order`.`billing_address_id` nach `sales_order_address`.`entity_id` und gibt die `region` field |
| `Customer's first order date` | Zeitstempel der ersten von diesem Kunden aufgegebenen Bestellung. Wird häufig als &quot;Akquisedatum&quot;für einen Kunden betrachtet. Wird durch Rückgabe des Mindestwerts berechnet `sales_order`.`created_at` Wert für jeden Unique Customer |
| `Customer's first order's billing region` | Akquise-Abrechnungsregion für den Kunden, der die Bestellung aufgegeben hat. Wird durch Rückgabe der `Billing address region` mit der ersten Bestellung des Kunden verknüpft ist |
| `Customer's first order's coupon_code` | Akquise-Gutscheincode für den Kunden, der diese Bestellung aufgegeben hat. Wird durch Rückgabe der `coupon_code` mit der ersten Bestellung des Kunden verknüpft ist |
| `Customer's group code` | Gruppenname des Kunden, der diese Bestellung aufgegeben hat. Errechnet durch Verbinden `sales_order`.`customer_group_id` nach `customer_group`.`customer_group_id` und gibt die `customer_group_code` field |
| `Customer's lifetime number of coupons` | Gesamtbetrag der Gutscheine, die auf alle von diesem Kunden aufgegebenen Bestellungen angewendet werden. Wird durch Zählung der Bestellungen berechnet, bei denen die Variable `coupon_code` ist nicht `NULL` für jeden einzelnen Kunden |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Wird durch Zählung der Zeilenanzahl im `sales_order` Tabelle für jeden Unique Customer |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle Bestellungen dieses Kunden. Wird durch Addition der `base_grand_total` Feld für alle Bestellungen für jeden Unique Customer |
| `Customer's order number` | Sequenzieller Bestellrang für die Bestellung dieses Kunden. Wird berechnet, indem alle von einem Kunden aufgegebenen Bestellungen identifiziert und in aufsteigender Reihenfolge von der `created_at` Zeitstempel und Zuweisen eines inkrementellen ganzzahligen Werts zu jeder Bestellung. Beispielsweise gibt die erste Bestellung des Kunden eine `Customer's order number` von 1 gibt die zweite Bestellung des Kunden eine `Customer's order number` von 2 usw. |
| `Customer's order number (previous-current)` | Rang der vorherigen Bestellung des Kunden, verkettet mit dem Rang dieser Bestellung, getrennt durch eine `-` Zeichen. Wird durch Verkettung (&quot;`Customer's order number` - 1&quot;) mit &quot;`-`&quot;, gefolgt von &quot;`Customer's order number`&quot;. Beispielsweise gibt diese Spalte für die Bestellung, die mit dem zweiten Kauf des Kunden verknüpft ist, den Wert `1-2`. Wird am häufigsten verwendet, wenn die Zeit zwischen zwei Bestellereignissen dargestellt wird (d. h. im Diagramm &quot;Zeit zwischen Bestellungen&quot;) |
| `Is customer's last order?` | Bestimmt, ob die Bestellung der letzten oder letzten Bestellung des Kunden entspricht. Wird durch Vergleich der `Customer's order number` Wert mit `Customer's lifetime number of orders`. Wenn diese beiden Felder für die angegebene Reihenfolge gleich sind, gibt diese Spalte `Yes`; gibt andernfalls zurück `No` |
| `Number of items in order` | Gesamtzahl der in der Bestellung enthaltenen Artikel. Errechnet durch Verbinden `sales_order`.`entity_id` nach `sales_order_item`.`order_id` und die `sales_order_item`.`qty_ordered` field |
| `Seconds between customer's first order date and this order` | Verstrichene Zeit zwischen dieser Bestellung und der ersten Bestellung des Kunden. Berechnet durch Subtraktion `Customer's first order date` aus dem `created_at` für jede Bestellung, die als Ganzzahl in Sekunden zurückgegeben wird |
| `Seconds since previous order` | Verstrichene Zeit zwischen dieser Bestellung und dem unmittelbar vorhergehenden Auftrag des Kunden. Berechnet durch Subtraktion der `created_at` für die vorherige Bestellung der `created_at` dieser Reihenfolge, die als ganzzahlige Anzahl von Sekunden zurückgegeben wird. Beispielsweise gibt diese Spalte für den Bestelldatensatz, der der dritten Bestellung eines Kunden entspricht, die Anzahl der Sekunden zwischen der zweiten und dritten Bestellung des Kunden zurück. Bei der ersten Bestellung des Kunden gibt dieses Feld `NULL` |
| `Shipping address city` | Versandort für die Bestellung. Errechnet durch Verbinden `sales_order`.`shipping_address_id` nach `sales_order_address`.`entity_id` und gibt die `city` field |
| `Shipping address country` | Versandland-Code für die Bestellung. Errechnet durch Verbinden `sales_order`.`Shipping_address_id` nach `sales_order_address`.`entity_id` und gibt die `country_id` |
| `Shipping address region` | Versandregion (meist Bundesland oder Provinz) für die Bestellung. Errechnet durch Verbinden `sales_order`.`shipping_address_id` nach `sales_order_address`.`entity_id` und gibt die `region` field |
| `Store name` | Der Name des mit dieser Bestellung verknüpften Commerce-Stores. Errechnet durch Verbinden `sales_order`.`store_id` nach `store`.`store_id` und gibt die `name` field |

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Avg order value` | Durchschnittlicher Umsatz pro Bestellung, wobei Umsatz als `base_grand_total` | `Operation: Average`<br/>`Operand: base_grand_total`<br/>`Timestamp: created_at` |
| `Avg time between orders` | Durchschnittliche Zeit zwischen der Bestellung eines Kunden (n-1) und der n-ten Bestellung, für alle Kunden und Bestellungen | `Operation: Average`<br/>`Operand: Seconds since previous order`<br/>`Timestamp:` `created_at` |
| `GMV` | Summe des Bruttowertwerts der Waren für alle Bestellungen, wobei GMV als Zwischensumme definiert ist, bevor alle Steuern und Rabatte angewendet werden | `Operation: Sum`<br/>`Operand: base_subtotal`<br/>`Timestamp: created_at` |
| `Median time between orders` | Die mittlere Zeit zwischen der Bestellung eines Kunden (n-1) und der n-ten Bestellung für alle Kunden und Bestellungen | `Operation: Median`<br/>`Operand: Seconds since previous order`<br/>`Timestamp:` `created_at` |
| `Orders` | Die Gesamtzahl der aufgegebenen Bestellungen | `Operation: Count`<br/>`Operand: entity_id`<br/>`Timestamp:` `created_at` |
| `Revenue` | Die Summe des Umsatzes für alle Bestellungen, wobei der Umsatz als der vom Kunden gezahlte Endpreis definiert wird, nachdem alle Steuern, Rabatte, Versand usw. angewendet werden. | `Operation: Sum`<br/>`Operand: base_grand_total`<br/>`Timestamp:` `created_at` |
| `Shipping` | Die Summe der Versandkosten für alle Bestellungen. | `Operation: Sum`<br/>`Operand: base_shipping_amount`<br/>`Timestamp:` `created_at` |
| `Tax` | Summe der Steuern, die auf alle Bestellungen erhoben werden | `Operation: Sum`<br/>`Operand:` `base_tax_amount`<br/>`Timestamp:` `created_at` |
| `Unique Customers` | Die Anzahl der Unique Customers, die eine Bestellung im angegebenen Berichtszeitintervall aufgeben. Wenn das Intervall des Berichts beispielsweise wöchentlich war, wird jeder Kunde, der in einer bestimmten Woche mindestens eine Bestellung aufgibt, genau einmal gezählt, unabhängig von der Anzahl der Bestellungen, die er in dieser Woche aufgegeben hat | `Operation: Count Distinct`<br/>`Operand:` `customer_email`<br/>`Timestamp:` `created_at` |

## `Foreign Key` Verknüpfungspfade

`customer_entity`

* Mitglied werden `customer_entity` , um neue Spalten auf Kundenebene zu erstellen, die mit dem Kunden verknüpft sind, der die Bestellung aufgegeben hat.
   * Pfad: `sales_order.customer_id` (viele) => `customer_entity.entity_id` (eins)

`customer_group`

* Mitglied werden `customer_group` -Tabelle, um Spalten zu erstellen, die den Kundengruppennamen des Kunden zurückgeben, der die Bestellung aufgegeben hat.
   * Pfad: `sales_order.customer_group_id` (viele) => `customer_group.customer_group_id` (eins)

`sales_order_address`

* Mitglied werden `sales_order_address` -Tabelle, um Spalten zu erstellen, die Abrechnungs- und Versandspeicherorte zurückgeben, die mit der Bestellung verknüpft sind. Je nachdem, ob die Abrechnungs- oder Versanddetails benötigt werden, sind zwei Verbindungswege möglich.
   * Pfade:
      * Versand: `sales_order.shipping_address_id`(viele) => `sales_order_address.entity_id` (eins)
      * Rechnungsstellung: `sales_order.billing_address_id`(viele) => `sales_order_address.entity_id` (eins)

`store`

* Mitglied werden `store` -Tabelle verwenden, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit der Bestellung verknüpft ist.
   * Pfad: `sales_order.store_id` (viele) => `store.store_id` (eins)
