---
title: Angebotstabelle
description: Erfahren Sie, wie Sie mit der Angebotstabelle arbeiten.
exl-id: 3a1e9239-33a7-429e-bfc8-628c68701710
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Angebotstabelle

Die `quote` Tabelle (`sales_flat_quote` auf M1) enthält Datensätze zu jedem in Ihrem Geschäft erstellten Warenkorb, unabhängig davon, ob diese aufgegeben oder in einen Kauf umgewandelt wurden. Jede Zeile stellt einen Warenkorb dar. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind.

>[!NOTE]
>
>Die Analyse historischer, Transaktionsabbrüche ist nur möglich, wenn keine Datensätze aus der `quote` gelöscht werden. Wenn Sie Datensätze löschen, können Sie nur die noch nicht aus Ihrer Datenbank entfernten Warenkörbe sehen.

## Gemeinsame native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_currency_code` | Währung für alle in `base_*` Feldern erfassten Werte (d. h. `base_grand_total`, `base_subtotal` usw.) Dies entspricht normalerweise der Standardwährung des Commerce-Stores |
| `base_grand_total` | Endgültiger Preis, der dem Kunden für den Warenkorb angeboten wird, nachdem alle Steuern, Versand und Rabatte angewendet werden. Obwohl die genaue Berechnung anpassbar ist, wird die `base_grand_total` im Allgemeinen als `base_subtotal` + `base_tax_amount` + `base_shipping_amount` + `base_discount_amount` - `base_gift_cards_amount` - `base_customer_balance_amount` berechnet |
| `base_subtotal` | Bruttowert aller Artikel im Warenkorb. Steuern, Versandkosten, Rabatte usw. sind nicht enthalten |
| `created_at` | Erstellungszeitstempel des Warenkorbs, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone umgewandelt werden, [!DNL Commerce Intelligence] sich von Ihrer Datenbankzeitzone unterscheidet |
| `customer_email` | E-Mail-Adresse des Kunden, der den Warenkorb erstellt hat |
| `customer_id` | `Foreign key`, die mit der `customer_entity` verknüpft sind, wenn der Kunde registriert ist. Join an `customer_entity.entity_id`, um Kundenattribute zu bestimmen, die mit dem Benutzer verknüpft sind, der den Warenkorb erstellt hat. Wenn der Warenkorb durch den Gast-Checkout erstellt wurde, ist dieses Feld `NULL` |
| `entity_id` (K) | Eindeutige Kennung für die Tabelle, die häufig bei Verknüpfungen mit anderen Tabellen in der Commerce-Instanz verwendet wird |
| `is_active` | Boolesches Feld, das „1“ zurückgibt, wenn der Warenkorb von einem Kunden erstellt wurde und noch nicht in eine Bestellung konvertiert wurde. Gibt „0“ für konvertierte Warenkörbe oder Warenkörbe zurück, die über den Administrator erstellt wurden. |
| `items_qty` | Summe der Gesamtmenge aller Artikel im Warenkorb |
| `reserved_order_id` | Der `Foreign key` Tabelle zugeordnete `sales_order` Join to `sales_order.increment_id` , um die Bestelldetails zu bestimmen, die einem konvertierten Warenkorb zugeordnet sind. Bei Warenkörben, die nicht mit einer konvertierten Bestellung verknüpft sind, bleibt die `reserved_order_id` `NULL` |
| `store_id` | Der `Foreign key` Tabelle zugeordnete `store` Mit `store` verbinden.`store_id` Sie, um zu bestimmen, welche Commerce-Store-Ansicht mit dem Warenkorb verknüpft ist |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Order date` | Zeitstempel, der das Erstellungsdatum der Bestellung für konvertierte Warenkörbe widerspiegelt. Berechnet durch Verbinden von `quote.reserved_order_id` mit `sales_order.increment_id` und Zurückgeben des `sales_order.created_at` |
| `Seconds between cart creation and order` | Verstrichene Zeit zwischen der Erstellung des Warenkorbs und der Bestellung. Berechnet durch Subtrahieren von `created_at` von `Order date`, zurückgegeben als ganzzahlige Anzahl von Sekunden |
| `Seconds since cart creation` | Verstrichene Zeit zwischen dem Erstellungsdatum des Warenkorbs und jetzt. Wird berechnet, indem `created_at` zum Zeitpunkt der Ausführung der Abfrage vom Server-Zeitstempel abgezogen und als ganzzahlige Anzahl von Sekunden zurückgegeben werden. Wird am häufigsten verwendet, um das Alter eines Warenkorbs zu identifizieren |
| `Store name` | Der Name des Commerce-Stores, der mit dieser Bestellung verknüpft ist. Berechnet durch Verbinden von `quote.store_id` mit `store.store_id` und Zurückgeben des `name` |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Number of abandoned carts` | Anzahl der Warenkörbe, die bestimmte Bedingungen für den „Abbruch“ erfüllen | `Operation: Count`<br/>`Operand:` `entity_id`<br/>`Timestamp:` `created_at`<br/>Filter:<br><br>- \[`A`\] `is_active` = 1<br>- \[`B`\] `items_count` > 0<br>- \[`C`\] `Seconds since cart creation` > x, wobei „x“ der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als verlassen gilt |
| `Avg time to cart conversion` | Die durchschnittliche Zeit zwischen Warenkorberstellung und Bestellerstellung für konvertierte Warenkörbe | `Operation: Average`<br>`Operand:` `Seconds between cart creation and order`<br>`Timestamp:` `created_at` |
| `Abandoned cart value` | Die Summe der potenziellen Gesamteinnahmen aus dem Transaktionsabbruch, wobei „Umsatz“ als `base_grand_total` definiert ist | `Operation: Sum`<br>`Operand:` `base_grand_total`<br>`Timestamp:` `created_at`<br>Filter:<br><br>- \[A\] `is_active` = 1<br>- \[`B`\] `items_count` > 0<br>- \[`C`\] `Seconds since cart creation` > x, wobei „x“ der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als verlassen gilt |

{style="table-layout:auto"}

## Fremdschlüssel-Verknüpfungspfade

`customer_entity`

* Join in `customer_entity` Tabelle, um neue Spalten auf Kundenebene zu erstellen, die mit dem Kunden verknüpft sind, der den Warenkorb erstellt hat.
   * Pfad: `quote.customer_id` (viele) => `customer_entity.entity_id` (eins)

`sales_order`

* Mit `sales_order` Tabelle verbinden, um Spalten zu erstellen, die mit einem konvertierten Warenkorb verknüpfte Bestelldetails zurückgeben.
   * Pfad: `quote.reserved_order_id` (viele) => `sales_order.increment_id` (eins)

`store`

* Join `store` Tabelle, um Spalten zu erstellen, die Details zum mit dem Warenkorb verknüpften Commerce-Store zurückgeben.
   * Pfad: `quote.store_id` (viele) => `store.store_id` (eins)
