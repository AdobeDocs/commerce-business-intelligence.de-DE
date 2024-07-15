---
title: Anführungstabelle
description: Erfahren Sie, wie Sie mit der Anführungszeichentabelle arbeiten.
exl-id: 3a1e9239-33a7-429e-bfc8-628c68701710
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Anführungstabelle

Die `quote` -Tabelle (`sales_flat_quote` auf M1) enthält Datensätze zu jedem Warenkorb, der in Ihrem Geschäft erstellt wurde, unabhängig davon, ob er abgebrochen oder in einen Kauf umgewandelt wurde. Jede Zeile stellt einen Warenkorb dar. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind.

>[!NOTE]
>
>Die Analyse von historischen, abgebrochenen Warenkörben ist nur möglich, wenn Sie keine Datensätze aus der `quote` -Tabelle löschen. Wenn Sie Datensätze löschen, können Sie nur die noch nicht aus Ihrer Datenbank entfernten Warenkörbe sehen.

## Allgemeine native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_currency_code` | Währung für alle in `base_*` -Feldern erfassten Werte (d. h. `base_grand_total`, `base_subtotal` usw.). Dies spiegelt normalerweise die Standardwährung des Commerce-Stores wider |
| `base_grand_total` | Endpreis, der dem Kunden für den Warenkorb angeboten wird, nach Anwendung aller Steuern, Versand und Rabatte. Obwohl die genaue Berechnung anpassbar ist, wird im Allgemeinen der `base_grand_total` als `base_subtotal` + `base_tax_amount` + `base_shipping_amount` + `base_discount_amount` - `base_gift_cards_amount` - `base_customer_balance_amount` berechnet |
| `base_subtotal` | Bruttokaufwert aller im Warenkorb enthaltenen Artikel. Steuern, Versand, Rabatte usw. sind nicht inbegriffen |
| `created_at` | Erstellungszeitstempel des Warenkorbs, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] konvertiert werden, die sich von Ihrer Zeitzone in der Datenbank unterscheidet |
| `customer_email` | E-Mail-Adresse des Kunden, der den Warenkorb erstellt hat |
| `customer_id` | `Foreign key`, die mit der `customer_entity` -Tabelle verknüpft ist, wenn der Kunde registriert ist. Treten Sie `customer_entity.entity_id` bei, um Kundenattribute zu ermitteln, die dem Benutzer zugeordnet sind, der den Warenkorb erstellt hat. Wenn der Warenkorb durch einen Gastkasse erstellt wurde, lautet dieses Feld `NULL` |
| `entity_id` (PK) | Eindeutige Kennung für die Tabelle, die häufig in Verbindung mit anderen Tabellen innerhalb der Commerce-Instanz verwendet wird |
| `is_active` | Boolesches Feld, das &quot;1&quot;zurückgibt, wenn der Warenkorb von einem Kunden erstellt wurde und noch nicht in eine Bestellung konvertiert wurde. Gibt &quot;0&quot;für konvertierte Warenkörbe oder Warenkörbe zurück, die vom Administrator erstellt wurden |
| `items_qty` | Summe der Gesamtmenge aller im Warenkorb enthaltenen Artikel |
| `reserved_order_id` | `Foreign key`, die mit der `sales_order`-Tabelle verknüpft ist. Melden Sie sich bei `sales_order.increment_id` an, um die Bestelldetails zu ermitteln, die mit einem konvertierten Warenkorb verbunden sind. Bei Warenkörben, die nicht mit einer konvertierten Bestellung verknüpft sind, bleibt der `reserved_order_id` `NULL` |
| `store_id` | `Foreign key`, die mit der `store`-Tabelle verknüpft ist. Treten Sie `store` bei.`store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit dem Warenkorb verknüpft ist |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Order date` | Zeitstempel, die das Erstellungsdatum der Bestellung für konvertierte Warenkörbe widerspiegeln. Wird berechnet, indem `quote.reserved_order_id` zu `sales_order.increment_id` addiert und das Feld `sales_order.created_at` zurückgegeben wird |
| `Seconds between cart creation and order` | Verstrichene Zeit zwischen der Erstellung des Warenkorbs und der Erstellung der Bestellung. Wird berechnet, indem `created_at` von `Order date` abgezogen wird, der als ganzzahlige Anzahl von Sekunden zurückgegeben wird |
| `Seconds since cart creation` | Verstrichene Zeit zwischen dem Erstellungsdatum des Warenkorbs und jetzt. Wird berechnet, indem `created_at` vom Zeitstempel des Servers zum Zeitpunkt der Ausführung der Abfrage abgezogen wird und als ganzzahlige Anzahl von Sekunden zurückgegeben wird. Wird am häufigsten verwendet, um das Alter eines Warenkorbs zu ermitteln |
| `Store name` | Der Name des mit dieser Bestellung verknüpften Commerce-Stores. Wird berechnet, indem `quote.store_id` zu `store.store_id` addiert und das Feld `name` zurückgegeben wird |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Konstruktion** |
|---|---|---|
| `Number of abandoned carts` | Anzahl der Warenkörbe, die bestimmte &quot;Abbruch&quot;-Bedingungen erfüllen | `Operation: Count`<br/>`Operand:` `entity_id`<br/>`Timestamp:` `created_at`<br/>Filter:<br><br>- \[`A`\] `is_active` = 1<br>- \[`B`\] `items_count` > 0<br>- \[`C`\] `Seconds since cart creation` > x, wobei &quot;x&quot;der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als verworfen gilt |
| `Avg time to cart conversion` | Durchschnittliche Zeit zwischen der Erstellung eines Warenkorbs und der Erstellung einer Bestellung für konvertierte Warenkörbe | `Operation: Average`<br>`Operand:` `Seconds between cart creation and order`<br>`Timestamp:` `created_at` |
| `Abandoned cart value` | Die Summe des potenziellen Gesamtumsatzes aus dem abgebrochenen Warenkorb, wobei der Umsatz als das Feld `base_grand_total` definiert ist | `Operation: Sum`<br>`Operand:` `base_grand_total`<br>`Timestamp:` `created_at`<br>Filter:<br><br>- \[A\] `is_active` = 1<br>- \[`B`\] `items_count` > 0<br>- \[`C`\] `Seconds since cart creation` > x, wobei &quot;x&quot;der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als verworfen gilt |

{style="table-layout:auto"}

## Verbindungswege für Fremdschlüssel

`customer_entity`

* Treten Sie der Tabelle `customer_entity` bei, um neue Spalten auf Kundenebene zu erstellen, die mit dem Kunden verknüpft sind, der den Warenkorb erstellt hat.
   * Pfad: `quote.customer_id` (viele) => `customer_entity.entity_id` (eins)

`sales_order`

* Join to `sales_order` table , um Spalten zu erstellen, die Bestelldetails zurückgeben, die mit einem konvertierten Warenkorb verknüpft sind.
   * Pfad:`quote.reserved_order_id` (viele) => `sales_order.increment_id` (eins)

`store`

* Treten Sie der Tabelle `store` bei, um Spalten zu erstellen, die Details zum mit dem Warenkorb verknüpften Commerce-Store zurückgeben.
   * Pfad: `quote.store_id` (viele) => `store.store_id` (eins)
