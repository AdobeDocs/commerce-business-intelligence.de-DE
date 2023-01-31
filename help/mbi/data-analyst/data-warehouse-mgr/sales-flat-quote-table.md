---
title: Anführungstabelle
description: Erfahren Sie, wie Sie mit der Anführungszeichentabelle arbeiten.
exl-id: 3a1e9239-33a7-429e-bfc8-628c68701710
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Anführungstabelle

Die `quote` table (`sales_flat_quote` auf M1) enthält Datensätze zu jedem Warenkorb, der in Ihrem Geschäft erstellt wurde, unabhängig davon, ob er abgebrochen oder in einen Kauf umgewandelt wurde. Jede Zeile stellt einen Warenkorb dar. Aufgrund der potenziellen Größe dieser Tabelle wird empfohlen, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind.

>[!NOTE]
>
>Die Analyse historischer Warenkorbvorgänge ist nur möglich, wenn Sie keine Datensätze aus dem `quote` Tabelle. Wenn Sie Datensätze löschen, können Sie nur die noch nicht aus Ihrer Datenbank entfernten Warenkörbe sehen.

## Allgemeine native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_currency_code` | Währung für alle Werte, die in `base_*` -Felder (d. h. `base_grand_total`, `base_subtotal`usw.). Dies spiegelt normalerweise die Standardwährung des Commerce-Stores wider |
| `base_grand_total` | Endpreis, der dem Kunden für den Warenkorb angeboten wird, nach Anwendung aller Steuern, Versand und Rabatte. Obwohl die genaue Berechnung anpassbar ist, ist im Allgemeinen die `base_grand_total` berechnet als `base_subtotal` + `base_tax_amount` + `base_shipping_amount` + `base_discount_amount` - `base_gift_cards_amount` - `base_customer_balance_amount` |
| `base_subtotal` | Bruttokaufwert aller im Warenkorb enthaltenen Artikel. Steuern, Versand, Rabatte usw. sind nicht inbegriffen |
| `created_at` | Erstellungszeitstempel des Warenkorbs, der normalerweise lokal in UTC gespeichert wird. Abhängig von Ihrer Konfiguration in [!DNL MBI], kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL MBI] , die sich von der Zeitzone Ihrer Datenbank unterscheidet |
| `customer_email` | E-Mail-Adresse des Kunden, der den Warenkorb erstellt hat |
| `customer_id` | `Foreign key` mit `customer_entity` -Tabelle, wenn der Kunde registriert ist. Mitglied werden `customer_entity.entity_id` , um Kundenattribute zu ermitteln, die mit dem Benutzer verknüpft sind, der den Warenkorb erstellt hat. Wenn der Warenkorb durch einen Gastkasse erstellt wurde, wird dieses Feld `NULL` |
| `entity_id` (PK) | Eindeutige Kennung für die Tabelle und wird häufig in Verknüpfungen zu anderen Tabellen innerhalb der Commerce-Instanz verwendet |
| `is_active` | Boolesches Feld, das &quot;1&quot;zurückgibt, wenn der Warenkorb von einem Kunden erstellt wurde und noch nicht in eine Bestellung konvertiert wurde. Gibt &quot;0&quot;für konvertierte Warenkörbe oder Warenkörbe zurück, die vom Administrator erstellt wurden |
| `items_qty` | Summe der Gesamtmenge aller im Warenkorb enthaltenen Artikel |
| `reserved_order_id` | `Foreign key` mit `sales_order` Tabelle. Mitglied werden `sales_order.increment_id` um Bestelldetails zu ermitteln, die mit einem konvertierten Warenkorb verknüpft sind. Bei Warenkörben, die nicht mit einer konvertierten Bestellung verknüpft sind, wird die `reserved_order_id` verbleiben `NULL` |
| `store_id` | `Foreign key` mit `store` Tabelle. Mitglied werden `store`.`store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit dem Warenkorb verknüpft ist |

{style=&quot;table-layout:auto&quot;}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Order date` | Zeitstempel, die das Erstellungsdatum der Bestellung für konvertierte Warenkörbe widerspiegeln. Errechnet durch Verbinden `quote.reserved_order_id` nach `sales_order.increment_id` und die `sales_order.created_at` field |
| `Seconds between cart creation and order` | Verstrichene Zeit zwischen der Erstellung des Warenkorbs und der Erstellung der Bestellung. Berechnet durch Subtraktion `created_at` von `Order date`zurückgegeben als ganzzahlige Anzahl von Sekunden |
| `Seconds since cart creation` | Verstrichene Zeit zwischen dem Erstellungsdatum des Warenkorbs und jetzt. Berechnet durch Subtraktion `created_at` vom Server-Zeitstempel zum Zeitpunkt der Ausführung der Abfrage zurückgegeben, wobei eine Ganzzahl von Sekunden zurückgegeben wird. Wird am häufigsten verwendet, um das Alter eines Warenkorbs zu ermitteln |
| `Store name` | Der Name des mit dieser Bestellung verknüpften Commerce-Stores. Errechnet durch Verbinden `quote.store_id` nach `store.store_id` und die `name` field |

{style=&quot;table-layout:auto&quot;}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Number of abandoned carts` | Anzahl der Warenkörbe, die bestimmte &quot;Abbruch&quot;-Bedingungen erfüllen | `Operation: Count`<br/>`Operand:` `entity_id`<br/>`Timestamp:` `created_at`<br/>Filter:<br><br>- \[`A`\] `is_active` = 1<br>- \[`B`\] `items_count` > 0<br>- \[`C`\] `Seconds since cart creation` > x, wobei &quot;x&quot;der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als abgebrochen gilt |
| `Avg time to cart conversion` | Durchschnittliche Zeit zwischen der Erstellung eines Warenkorbs und der Erstellung einer Bestellung für konvertierte Warenkörbe | `Operation: Average`<br>`Operand:` `Seconds between cart creation and order`<br>`Timestamp:` `created_at` |
| `Abandoned cart value` | Die Summe des potenziellen Gesamtumsatzes aus dem abgebrochenen Warenkorb, wobei der Umsatz als `base_grand_total` field | `Operation: Sum`<br>`Operand:` `base_grand_total`<br>`Timestamp:` `created_at`<br>Filter:<br><br>- \[A\] `is_active` = 1<br>- \[`B`\] `items_count` > 0<br>- \[`C`\] `Seconds since cart creation` > x, wobei &quot;x&quot;der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als abgebrochen gilt |

{style=&quot;table-layout:auto&quot;}

## Verbindungswege für Fremdschlüssel

`customer_entity`

* Mitglied werden `customer_entity` , um neue Spalten auf Kundenebene zu erstellen, die mit dem Kunden verknüpft sind, der den Warenkorb erstellt hat.
   * Pfad: `quote.customer_id` (viele) => `customer_entity.entity_id` (eins)

`sales_order`

* Mitglied werden `sales_order` , um neue Spalten zu erstellen, die Bestelldetails zurückgeben, die mit einem konvertierten Warenkorb verknüpft sind.
   * Pfad:`quote.reserved_order_id` (viele) => `sales_order.increment_id` (eins)

`store`

* Mitglied werden `store` , um neue Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Warenkorb verknüpft ist.
   * Pfad: `quote.store_id` (viele) => `store.store_id` (eins)
