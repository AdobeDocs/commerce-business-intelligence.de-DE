---
title: Sales_order-Tabelle
description: Erfahren Sie, wie Sie mit der Tabelle „sales_order“ arbeiten.
exl-id: 19a8ab88-de51-48f8-af39-ae4897834afe
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# `sales_order`

In der `sales_order` (`sales_flat_order` M1) wird jede Bestellung erfasst. Normalerweise stellt jede Zeile eine eindeutige Reihenfolge dar, obwohl es einige benutzerdefinierte Implementierungen von Commerce gibt, die dazu führen, dass eine Reihenfolge in separate Zeilen aufgeteilt wird.

Diese Tabelle enthält alle Kundenbestellungen, unabhängig davon, ob diese Bestellung über den Gast-Checkout verarbeitet wurde. Wenn Ihr Geschäft einen Gast-Checkout akzeptiert, finden Sie weitere Informationen zu diesem [Anwendungsfall](../data-warehouse-mgr/guest-orders.md).

## Gemeinsame Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_currency_code` | Währung für alle in `base_*` Feldern erfassten Werte (d. h. `base_grand_total`, `base_subtotal` usw.) Dies entspricht normalerweise der Standardwährung des Commerce-Stores |
| `base_discount_amount` | Auf die Bestellung angewendeter Rabattwert |
| `base_grand_total` | Endgültiger Preis, der vom Kunden für die Bestellung bezahlt wird, nachdem alle Steuern, Versand und Rabatte angewendet werden. Obwohl die genaue Berechnung anpassbar ist, wird die `base_grand_total` im Allgemeinen als `base_subtotal` + `base_tax_amount` + `base_shipping_amount` `+` `base_discount_amount` `-` `base_gift_cards_amount` `-` `base_customer_balance_amount` berechnet |
| `base_subtotal` | Bruttowarenwert aller in der Bestellung enthaltenen Artikel. Steuern, Versandkosten, Rabatte usw. sind nicht enthalten |
| `base_shipping_amount` | Auf Bestellung angewendeter Versandwert |
| `base_tax_amount` | Auf Bestellung angewendeter Steuerwert |
| `billing_address_id` | Der `sales_order_address` Tabelle zugeordnete `Foreign key` `sales_order_address.entity_id` Sie die mit der Bestellung verbundenen Details der Rechnungsadresse an. |
| `coupon_code` | Coupon auf Bestellung angewendet. Wenn kein Coupon angewendet wird, wird dieses Feld `NULL` |
| `created_at` | Erstellungszeitstempel der Bestellung, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone umgewandelt werden, [!DNL Commerce Intelligence] sich von Ihrer Datenbankzeitzone unterscheidet |
| `customer_email` | E-Mail-Adresse des Bestellers. Dies wird in allen Situationen ausgefüllt, einschließlich Bestellungen, die über den Gast-Checkout verarbeitet werden |
| `customer_group_id` | Fremdschlüssel, der der `customer_group`-Tabelle zugeordnet ist. `customer_group.customer_group_id` beitreten, um die mit der Bestellung verknüpfte Kundengruppe zu bestimmen |
| `customer_id` | `Foreign key`, die mit der `customer_entity` verknüpft sind, wenn der Kunde registriert ist. Mit `customer_entity.entity_id` verbinden, um Kundenattribute zu bestimmen, die mit der Bestellung verknüpft sind. Wenn die Bestellung über den Gast-Checkout aufgegeben wurde, ist dieses Feld `NULL` |
| `entity_id` (K) | Eindeutige Kennung für die Tabelle, die häufig bei Verknüpfungen mit anderen Tabellen in der Commerce-Instanz verwendet wird |
| `increment_id` | Eindeutige Kennung für eine Bestellung, die in Adobe Commerce häufig als `order_id` bezeichnet wird. Der `increment_id` wird am häufigsten für Joins mit externen Quellen verwendet, z. B. [!DNL Google Ecommerce] |
| `shipping_address_id` | Fremdschlüssel, der der `sales_order_address`-Tabelle zugeordnet ist. `sales_order_address.entity_id` Sie mit , um die mit der Bestellung verbundenen Details der Versandadresse zu bestimmen |
| `status` | Status der Bestellung. Kann Werte wie „abgeschlossen“, „Verarbeitung läuft“, „abgebrochen“, „rückerstattet“ und alle benutzerdefinierten Status zurückgeben, die auf der Commerce-Instanz implementiert sind. Änderungen vorbehalten, sobald die Bestellung bearbeitet wird |
| `store_id` | Der `store` Tabelle zugeordnete `Foreign key` Mit `store` verbinden.`store_id`, um zu bestimmen, welche Commerce Store-Ansicht mit der Bestellung verknüpft ist |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Billing address city` | Rechnungsort für die Bestellung. Berechnet durch `sales_order`.`billing_address_id` zu `sales_order_address`.`entity_id` und Zurückgeben des `city` |
| `Billing address country` | Ländercode der Rechnungsstellung für die Bestellung. Berechnet durch `sales_order`.`billing_address_id` zu `sales_order_address`.`entity_id` und Zurückgeben der `country_id` |
| `Billing address region` | Rechnungsregion (meistens Bundesland oder Provinz) für die Bestellung. Berechnet durch `sales_order`.`billing_address_id` zu `sales_order_address`.`entity_id` und Zurückgeben des `region` |
| `Customer's first order date` | Zeitstempel der ersten Bestellung dieses Kunden. Wird häufig als „Akquisitionsdatum“ für einen Kunden betrachtet. Berechnet durch Rückgabe der `sales_order`.`created_at` Wert für jeden einzelnen Kunden |
| `Customer's first order's billing region` | Abrechnungsregion für die Akquise für den Kunden, der die Bestellung aufgegeben hat Berechnet durch Rückgabe der `Billing address region`, die mit der ersten Bestellung des Kunden verbunden sind |
| `Customer's first order's coupon_code` | Gutscheincode für den Kunden, der diese Bestellung aufgegeben hat. Berechnet durch Rückgabe der `coupon_code`, die mit der ersten Bestellung des Kunden verbunden sind |
| `Customer's group code` | Gruppenname des Kunden, der diese Bestellung aufgegeben hat. Berechnet durch `sales_order`.`customer_group_id` zu `customer_group`.`customer_group_id` und Zurückgeben des `customer_group_code` |
| `Customer's lifetime number of coupons` | Die Gesamtmenge der Coupons, die auf alle von diesem Kunden aufgegebenen Bestellungen angewendet wurden. Berechnet durch Zählen der Bestellungen, bei denen die `coupon_code` nicht für jeden einzelnen Kunden `NULL` ist |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Berechnet durch Zählen der Zeilen in der `sales_order` für jeden einzelnen Kunden |
| `Customer's lifetime revenue` | Summe des Gesamtumsatzes für alle Bestellungen dieses Kunden. Berechnet durch Summierung des Felds &quot;`base_grand_total`&quot; für alle Bestellungen für jeden einzelnen Kunden |
| `Customer's order number` | Sequenzieller Auftragsrang für die Bestellung dieses Kunden. Berechnet, indem alle von einem Kunden aufgegebenen Bestellungen identifiziert, in aufsteigender Reihenfolge nach dem `created_at` Zeitstempel sortiert und jeder Bestellung ein inkrementierender ganzzahliger Wert zugewiesen wird. Beispiel: Bei der ersten Bestellung eines Kunden wird die `Customer's order number` 1 zurückgegeben, bei der zweiten Bestellung des Kunden wird die `Customer's order number` 2 zurückgegeben usw. |
| `Customer's order number (previous-current)` | Rang der vorherigen Bestellung eines Kunden, verkettet mit dem Rang dieser Bestellung, getrennt durch ein `-` Zeichen. Wird durch Verketten (“`Customer's order number` - 1„) mit &quot;`-`&quot; gefolgt von &quot;`Customer's order number`&quot; berechnet. Beispiel: Für die Bestellung, die mit dem zweiten Kauf des Kunden verknüpft ist, gibt diese Spalte einen Wert von `1-2` zurück. Wird am häufigsten verwendet, wenn die Zeit zwischen zwei Bestellereignissen dargestellt wird (d. h. im Diagramm „Zeit zwischen Bestellungen„) |
| `Is customer's last order?` | Bestimmt, ob die Bestellung der letzten oder letzten Bestellung des Kunden entspricht. Wird durch Vergleich des `Customer's order number` mit `Customer's lifetime number of orders` berechnet. Wenn diese beiden Felder für die angegebene Reihenfolge gleich sind, gibt diese Spalte `Yes` zurück. Andernfalls gibt sie `No` zurück |
| `Number of items in order` | Die Gesamtmenge der Artikel, die in der Bestellung enthalten sind. Berechnet durch `sales_order`.`entity_id` zu `sales_order_item`.`order_id` und Zusammenfassung der `sales_order_item`.`qty_ordered` |
| `Seconds between customer's first order date and this order` | Zeit zwischen dieser Bestellung und der ersten Bestellung des Kunden. Berechnet durch Subtrahieren von `Customer's first order date` vom `created_at` für jede Bestellung, zurückgegeben als ganzzahlige Anzahl von Sekunden |
| `Seconds since previous order` | Verstrichene Zeit zwischen dieser Bestellung und der unmittelbar vorangehenden Bestellung des Kunden. Berechnet durch Subtrahieren der `created_at` für die vorherige Reihenfolge von der `created_at` dieser Reihenfolge, zurückgegeben als ganzzahlige Anzahl von Sekunden. Beispiel: Für den Bestelldatensatz, der der dritten Bestellung eines Kunden entspricht, gibt diese Spalte die Anzahl der Sekunden zwischen der zweiten und dritten Bestellung des Kunden zurück. Für die erste Bestellung des Kunden gibt dieses Feld `NULL` zurück. |
| `Shipping address city` | Versandstadt für die Bestellung. Berechnet durch `sales_order`.`shipping_address_id` zu `sales_order_address`.`entity_id` und Zurückgeben des `city` |
| `Shipping address country` | Lieferland-Code für die Bestellung. Berechnet durch `sales_order`.`Shipping_address_id` zu `sales_order_address`.`entity_id` und Zurückgeben der `country_id` |
| `Shipping address region` | Versandregion (meistens Bundesland oder Provinz) für die Bestellung. Berechnet durch `sales_order`.`shipping_address_id` zu `sales_order_address`.`entity_id` und Zurückgeben des `region` |
| `Store name` | Der Name des Commerce-Stores, der mit dieser Bestellung verknüpft ist. Berechnet durch `sales_order`.`store_id` zu `store`.`store_id` und Zurückgeben des `name` |

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Avg order value` | Der durchschnittliche Umsatz pro Bestellung, bei dem der Umsatz als `base_grand_total` definiert ist | `Operation: Average`<br/>`Operand: base_grand_total`<br/>`Timestamp: created_at` |
| `Avg time between orders` | Die durchschnittliche Zeit zwischen der Bestellung eines Kunden (n-1) und der n-ten Bestellung für alle Kunden und Bestellungen | `Operation: Average`<br/>`Operand: Seconds since previous order`<br/>`Timestamp:` `created_at` |
| `GMV` | Die Summe des Bruttowarenwerts für alle Bestellungen, wobei GMV als Zwischensumme definiert ist, bevor alle Steuern und Rabatte angewendet werden | `Operation: Sum`<br/>`Operand: base_subtotal`<br/>`Timestamp: created_at` |
| `Median time between orders` | Die mediane Zeit zwischen der Bestellung eines Kunden (n-1) und der n-ten Bestellung für alle Kunden und Bestellungen | `Operation: Median`<br/>`Operand: Seconds since previous order`<br/>`Timestamp:` `created_at` |
| `Orders` | Die Gesamtzahl der aufgegebenen Bestellungen | `Operation: Count`<br/>`Operand: entity_id`<br/>`Timestamp:` `created_at` |
| `Revenue` | Die Summe des Umsatzes für alle Bestellungen, wobei der Umsatz als der vom Kunden gezahlte Endpreis definiert wird, nachdem alle Steuern, Rabatte, Versandkosten usw. angewendet wurden | `Operation: Sum`<br/>`Operand: base_grand_total`<br/>`Timestamp:` `created_at` |
| `Shipping` | Die Summe des Versandbetrags für alle Bestellungen | `Operation: Sum`<br/>`Operand: base_shipping_amount`<br/>`Timestamp:` `created_at` |
| `Tax` | Die Summe der Steuern, die auf alle Bestellungen angewendet werden | `Operation: Sum`<br/>`Operand:` `base_tax_amount`<br/>`Timestamp:` `created_at` |
| `Unique Customers` | Die Anzahl der Unique Customers, die eine Bestellung im angegebenen Berichtszeitintervall aufgeben. Wenn der Bericht beispielsweise ein wöchentliches Intervall hatte, wird jeder Kunde, der mindestens eine Bestellung in einer bestimmten Woche aufgibt, genau einmal gezählt, unabhängig davon, wie viele Bestellungen er in dieser Woche aufgegeben hat | `Operation: Count Distinct`<br/>`Operand:` `customer_email`<br/>`Timestamp:` `created_at` |

## `Foreign Key` von Verbindungswegen

`customer_entity`

* Join in `customer_entity` Tabelle, um neue Spalten auf Kundenebene zu erstellen, die mit dem Kunden verknüpft sind, der die Bestellung aufgegeben hat.
   * Pfad: `sales_order.customer_id` (viele) => `customer_entity.entity_id` (eins)

`customer_group`

* Mit `customer_group` Tabelle verbinden, um Spalten zu erstellen, die den Namen der Kundengruppe des Kunden zurückgeben, der die Bestellung aufgegeben hat.
   * Pfad: `sales_order.customer_group_id` (viele) => `customer_group.customer_group_id` (eins)

`sales_order_address`

* Mit `sales_order_address` Tabelle verbinden, um Spalten zu erstellen, die die mit der Bestellung verbundenen Abrechnungs- und Versandspeicherorte zurückgeben. Je nachdem, ob die Abrechnungs- oder Versanddaten erforderlich sind, sind zwei Fügewege möglich.
   * Pfade:
      * Versand: `sales_order.shipping_address_id`(viele) => `sales_order_address.entity_id` (eine)
      * Abrechnung: `sales_order.billing_address_id`(viele) => `sales_order_address.entity_id` (eine)

`store`

* Mit `store` Tabelle verbinden, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit der Bestellung verknüpft ist.
   * Pfad: `sales_order.store_id` (viele) => `store.store_id` (eins)
