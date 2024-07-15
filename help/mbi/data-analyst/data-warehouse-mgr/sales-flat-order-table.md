---
title: sales_order-Tabelle
description: Erfahren Sie, wie Sie mit der Tabelle sales_order arbeiten.
exl-id: 19a8ab88-de51-48f8-af39-ae4897834afe
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# `sales_order` Tabelle

In der Tabelle `sales_order` (`sales_flat_order` bei M1) wird jede Bestellung erfasst. Normalerweise stellt jede Zeile eine eindeutige Reihenfolge dar, obwohl es einige benutzerdefinierte Implementierungen von Commerce gibt, die dazu führen, dass eine Reihenfolge in separate Zeilen unterteilt wird.

Diese Tabelle enthält alle Kundenbestellungen, unabhängig davon, ob diese Bestellung über einen Gastkasse verarbeitet wurde. Wenn Ihr Store einen Gast-Checkout akzeptiert, finden Sie weitere Informationen zu diesem [Anwendungsfall](../data-warehouse-mgr/guest-orders.md).

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_currency_code` | Währung für alle in `base_*` -Feldern erfassten Werte (d. h. `base_grand_total`, `base_subtotal` usw.). Dies spiegelt normalerweise die Standardwährung des Commerce-Stores wider |
| `base_discount_amount` | Auf Bestellung angewendeter Rabattwert |
| `base_grand_total` | Endpreis, der vom Kunden bei der Bestellung gezahlt wird, nach Anwendung aller Steuern, Versand und Rabatte. Obwohl die genaue Berechnung anpassbar ist, wird im Allgemeinen der `base_grand_total` als `base_subtotal` + `base_tax_amount` + `base_shipping_amount` `+` `base_discount_amount` `-` `base_gift_cards_amount` `-` `base_customer_balance_amount` berechnet |
| `base_subtotal` | Bruttokaufwert aller in der Bestellung enthaltenen Artikel. Steuern, Versand, Rabatte usw. sind nicht inbegriffen |
| `base_shipping_amount` | Auf Bestellung angewendeter Versandwert |
| `base_tax_amount` | Auf Bestellung angewendeter Steuerwert |
| `billing_address_id` | `Foreign key`, die mit der `sales_order_address`-Tabelle verknüpft ist. Melden Sie sich bei `sales_order_address.entity_id` an, um die Details der Rechnungsadresse zu ermitteln, die mit der Bestellung verbunden sind. |
| `coupon_code` | Auf Bestellung angewendeter Coupon. Wenn kein Coupon angewendet wird, ist dieses Feld `NULL` |
| `created_at` | Erstellungszeitstempel der Bestellung, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] konvertiert werden, die sich von Ihrer Zeitzone in der Datenbank unterscheidet |
| `customer_email` | E-Mail-Adresse des Bestellers. Dies wird in allen Situationen aufgefüllt, einschließlich der Bestellungen, die über den Gastkauf verarbeitet werden |
| `customer_group_id` | Fremdschlüssel, der mit der Tabelle `customer_group` verknüpft ist. Treten Sie `customer_group.customer_group_id` bei, um die mit der Bestellung verbundene Kundengruppe zu ermitteln. |
| `customer_id` | `Foreign key`, die mit der `customer_entity` -Tabelle verknüpft ist, wenn der Kunde registriert ist. Treten Sie `customer_entity.entity_id` bei, um Kundenattribute zu ermitteln, die mit der Bestellung verbunden sind. Wenn die Bestellung über einen Gastkasse aufgegeben wurde, lautet dieses Feld `NULL` |
| `entity_id` (PK) | Eindeutige Kennung für die Tabelle, die häufig in Verbindung mit anderen Tabellen innerhalb der Commerce-Instanz verwendet wird |
| `increment_id` | Eindeutige Kennung für eine Bestellung, die in Adobe Commerce häufig als `order_id` bezeichnet wird. Der `increment_id` wird am häufigsten für Verbindungen zu externen Quellen wie [!DNL Google Ecommerce] verwendet |
| `shipping_address_id` | Fremdschlüssel, der mit der Tabelle `sales_order_address` verknüpft ist. Melden Sie sich bei `sales_order_address.entity_id` an, um die Details der Versandadresse zu ermitteln, die mit der Bestellung verbunden sind. |
| `status` | Bestellstatus. Kann Werte wie &quot;complete&quot;, &quot;processing&quot;, &quot;cancelled&quot;, &quot;refund&quot;und alle benutzerdefinierten Status zurückgeben, die auf der Commerce-Instanz implementiert wurden. Vorbehaltlich Änderungen bei der Verarbeitung der Bestellung |
| `store_id` | `Foreign key`, die mit der `store`-Tabelle verknüpft ist. Treten Sie `store` bei.`store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit der Bestellung verknüpft ist |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Billing address city` | Abrechnungsort für die Bestellung. Wird durch Anfügen von `sales_order` berechnet.`billing_address_id` bis `sales_order_address``entity_id` und gibt das Feld `city` zurück |
| `Billing address country` | Rechnungslandescode für die Bestellung. Wird durch Anfügen von `sales_order` berechnet.`billing_address_id` bis `sales_order_address``entity_id` und die `country_id` zurückgeben |
| `Billing address region` | Rechnungsregion (am häufigsten Bundesland oder Provinz) für die Bestellung. Wird durch Anfügen von `sales_order` berechnet.`billing_address_id` bis `sales_order_address``entity_id` und gibt das Feld `region` zurück |
| `Customer's first order date` | Zeitstempel der ersten von diesem Kunden aufgegebenen Bestellung. Wird häufig als &quot;Akquisedatum&quot;für einen Kunden betrachtet. Wird durch Rückgabe des Mindestwerts von `sales_order` berechnet.`created_at` Wert für jeden Unique Customer |
| `Customer's first order's billing region` | Akquise-Abrechnungsregion für den Kunden, der die Bestellung aufgegeben hat. Wird durch Rückgabe des mit der ersten Bestellung des Kunden verknüpften `Billing address region` berechnet |
| `Customer's first order's coupon_code` | Akquise-Gutscheincode für den Kunden, der diese Bestellung aufgegeben hat. Wird durch Rückgabe des mit der ersten Bestellung des Kunden verknüpften `coupon_code` berechnet |
| `Customer's group code` | Gruppenname des Kunden, der diese Bestellung aufgegeben hat. Wird durch Anfügen von `sales_order` berechnet.`customer_group_id` bis `customer_group``customer_group_id` und gibt das Feld `customer_group_code` zurück |
| `Customer's lifetime number of coupons` | Gesamtbetrag der Gutscheine, die auf alle von diesem Kunden aufgegebenen Bestellungen angewendet werden. Wird berechnet, indem die Anzahl der Bestellungen gezählt wird, bei denen der `coupon_code` nicht `NULL` für jeden einzelnen Kunden ist |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Wird durch Zählung der Zeilenanzahl in der Tabelle `sales_order` für jeden Unique Customer berechnet |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle Bestellungen dieses Kunden. Wird durch Addition des Felds `base_grand_total` für alle Bestellungen eines einzelnen Kunden berechnet |
| `Customer's order number` | Sequenzieller Bestellrang für die Bestellung dieses Kunden. Wird berechnet, indem alle von einem Kunden aufgegebenen Bestellungen identifiziert, in aufsteigender Reihenfolge nach dem Zeitstempel `created_at` sortiert und jeder Bestellung ein inkrementierender ganzzahliger Wert zugewiesen wird. Beispielsweise gibt die erste Bestellung des Kunden den Wert &quot;`Customer's order number`&quot;von 1 zurück, die zweite Bestellung des Kunden den Wert &quot;`Customer's order number`&quot;von 2 usw. |
| `Customer's order number (previous-current)` | Rang der vorherigen Bestellung des Kunden, verkettet mit dem Rang dieser Bestellung, getrennt durch das Zeichen `-`. Wird durch Verkettung (&quot;`Customer's order number` - 1&quot;) mit &quot;`-`&quot; gefolgt von &quot;`Customer's order number`&quot; berechnet. Beispielsweise gibt diese Spalte für die Bestellung, die mit dem zweiten Kauf des Kunden verknüpft ist, den Wert `1-2` zurück. Wird am häufigsten verwendet, wenn die Zeit zwischen zwei Bestellereignissen dargestellt wird (d. h. im Diagramm &quot;Zeit zwischen Bestellungen&quot;) |
| `Is customer's last order?` | Bestimmt, ob die Bestellung der letzten oder letzten Bestellung des Kunden entspricht. Wird durch Vergleich des Werts `Customer's order number` mit `Customer's lifetime number of orders` berechnet. Wenn diese beiden Felder für die angegebene Reihenfolge gleich sind, gibt diese Spalte `Yes` zurück; sonst wird `No` zurückgegeben. |
| `Number of items in order` | Gesamtzahl der in der Bestellung enthaltenen Artikel. Wird durch Anfügen von `sales_order` berechnet.`entity_id` bis `sales_order_item``order_id` und summieren die `sales_order_item`.Feld `qty_ordered` |
| `Seconds between customer's first order date and this order` | Verstrichene Zeit zwischen dieser Bestellung und der ersten Bestellung des Kunden. Wird berechnet, indem `Customer's first order date` von den `created_at` für jede Bestellung abgezogen wird, die als Ganzzahl in Sekunden zurückgegeben wird |
| `Seconds since previous order` | Verstrichene Zeit zwischen dieser Bestellung und dem unmittelbar vorhergehenden Auftrag des Kunden. Wird berechnet, indem der Wert `created_at` für die vorherige Bestellung von dem Wert `created_at` dieser Bestellung abgezogen wird, der als Ganzzahl in Sekunden zurückgegeben wird. Beispielsweise gibt diese Spalte für den Bestelldatensatz, der der dritten Bestellung eines Kunden entspricht, die Anzahl der Sekunden zwischen der zweiten und dritten Bestellung des Kunden zurück. Für die erste Bestellung des Kunden gibt dieses Feld `NULL` zurück. |
| `Shipping address city` | Versandort für die Bestellung. Wird durch Anfügen von `sales_order` berechnet.`shipping_address_id` bis `sales_order_address``entity_id` und gibt das Feld `city` zurück |
| `Shipping address country` | Versandland-Code für die Bestellung. Wird durch Anfügen von `sales_order` berechnet.`Shipping_address_id` bis `sales_order_address``entity_id` und die `country_id` zurückgeben |
| `Shipping address region` | Versandregion (meist Bundesland oder Provinz) für die Bestellung. Wird durch Anfügen von `sales_order` berechnet.`shipping_address_id` bis `sales_order_address``entity_id` und gibt das Feld `region` zurück |
| `Store name` | Der Name des mit dieser Bestellung verknüpften Commerce-Stores. Wird durch Anfügen von `sales_order` berechnet.`store_id` bis `store``store_id` und gibt das Feld `name` zurück |

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Konstruktion** |
|---|---|---|
| `Avg order value` | Durchschnittlicher Umsatz pro Bestellung, wobei Umsatz als `base_grand_total` definiert ist | `Operation: Average`<br/>`Operand: base_grand_total`<br/>`Timestamp: created_at` |
| `Avg time between orders` | Durchschnittliche Zeit zwischen der Bestellung eines Kunden (n-1) und der n-ten Bestellung, für alle Kunden und Bestellungen | `Operation: Average`<br/>`Operand: Seconds since previous order`<br/>`Timestamp:` `created_at` |
| `GMV` | Summe des Bruttowertwerts der Waren für alle Bestellungen, wobei GMV als Zwischensumme definiert ist, bevor alle Steuern und Rabatte angewendet werden | `Operation: Sum`<br/>`Operand: base_subtotal`<br/>`Timestamp: created_at` |
| `Median time between orders` | Die mittlere Zeit zwischen der Bestellung eines Kunden (n-1) und der n-ten Bestellung für alle Kunden und Bestellungen | `Operation: Median`<br/>`Operand: Seconds since previous order`<br/>`Timestamp:` `created_at` |
| `Orders` | Die Gesamtzahl der aufgegebenen Bestellungen | `Operation: Count`<br/>`Operand: entity_id`<br/>`Timestamp:` `created_at` |
| `Revenue` | Die Summe des Umsatzes für alle Bestellungen, wobei der Umsatz als der vom Kunden gezahlte Endpreis definiert wird, nachdem alle Steuern, Rabatte, Versand usw. angewendet werden. | `Operation: Sum`<br/>`Operand: base_grand_total`<br/>`Timestamp:` `created_at` |
| `Shipping` | Die Summe der Versandkosten für alle Bestellungen. | `Operation: Sum`<br/>`Operand: base_shipping_amount`<br/>`Timestamp:` `created_at` |
| `Tax` | Summe der Steuern, die auf alle Bestellungen erhoben werden | `Operation: Sum`<br/>`Operand:` `base_tax_amount`<br/>`Timestamp:` `created_at` |
| `Unique Customers` | Die Anzahl der Unique Customers, die eine Bestellung im angegebenen Berichtszeitintervall aufgeben. Wenn das Intervall des Berichts beispielsweise wöchentlich war, wird jeder Kunde, der in einer bestimmten Woche mindestens eine Bestellung aufgibt, genau einmal gezählt, unabhängig von der Anzahl der Bestellungen, die er in dieser Woche aufgegeben hat | `Operation: Count Distinct`<br/>`Operand:` `customer_email`<br/>`Timestamp:` `created_at` |

## `Foreign Key` Verbindungswege

`customer_entity`

* Treten Sie der Tabelle `customer_entity` bei, um neue Spalten auf Kundenebene zu erstellen, die mit dem Kunden verknüpft sind, der die Bestellung aufgegeben hat.
   * Pfad: `sales_order.customer_id` (viele) => `customer_entity.entity_id` (eins)

`customer_group`

* Treten Sie der Tabelle `customer_group` bei, um Spalten zu erstellen, die den Kundengruppennamen des Kunden zurückgeben, der die Bestellung aufgegeben hat.
   * Pfad: `sales_order.customer_group_id` (viele) => `customer_group.customer_group_id` (eins)

`sales_order_address`

* Treten Sie der Tabelle `sales_order_address` bei, um Spalten zu erstellen, die mit der Bestellung verbundene Abrechnungs- und Versandspeicherorte zurückgeben. Je nachdem, ob die Abrechnungs- oder Versanddetails benötigt werden, sind zwei Verbindungswege möglich.
   * Pfade:
      * Versand: `sales_order.shipping_address_id`(viele) => `sales_order_address.entity_id` (eins)
      * Rechnungsstellung: `sales_order.billing_address_id`(viele) => `sales_order_address.entity_id` (eins)

`store`

* Treten Sie der Tabelle `store` bei, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit der Bestellung verknüpft ist.
   * Pfad: `sales_order.store_id` (viele) => `store.store_id` (eins)
