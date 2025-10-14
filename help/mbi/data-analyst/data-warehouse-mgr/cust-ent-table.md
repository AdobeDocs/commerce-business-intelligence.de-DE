---
title: Tabelle customer_entity
description: Erfahren Sie, wie Sie auf Datensätze aller registrierten Konten zugreifen können.
exl-id: 24bf0e66-eea0-45ea-8ce6-4ff99b678201
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---

# customer_entity-Tabelle

Die Tabelle `customer_entity` enthält Einträge aller registrierten Konten. Ein Konto gilt als registriert, wenn er sich für ein Konto anmeldet, unabhängig davon, ob er jemals einen Kauf abschließt. Jede Zeile entspricht einem eindeutigen registrierten Konto, das durch die `entity_id` dieses Kontos identifiziert wird.

Diese Tabelle enthält keine Datensätze von Kunden, die eine Bestellung per Gast-Checkout aufgeben. Wenn Ihr Geschäft einen Gast-Checkout akzeptiert, finden Sie [&#x200B; diesen Bestellungen unter &quot;](../data-warehouse-mgr/guest-orders.md) für Gastbestellungen“.

## Gemeinsame Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `created_at` | Zeitstempel, der dem Registrierungsdatum des Kontos entspricht und lokal in UTC gespeichert wird. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone umgewandelt werden, [!DNL Commerce Intelligence] sich von Ihrer Datenbankzeitzone unterscheidet |
| `email` | Dem Konto zugeordnete E-Mail-Adresse |
| `entity_id` (K) | Eindeutige Kennung für die Tabelle, die häufig bei Verknüpfungen mit dem `customer_id` in anderen Tabellen innerhalb der Instanz verwendet wird |
| `group_id` | Fremdschlüssel, der der `customer_group`-Tabelle zugeordnet ist. `customer_group.customer_group_id` beitreten, um die mit dem registrierten Konto verknüpfte Kundengruppe zu bestimmen |
| `store_id` | Fremdschlüssel, der der `store`-Tabelle zugeordnet ist. Mit `store` verbinden.`store_id`, um zu bestimmen, welche Commerce-Store-Ansicht mit dem registrierten Konto verknüpft ist |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's first 30 day revenue` | Summe des Umsatzes für alle Bestellungen dieses Kunden innerhalb von 30 Tagen nach dem ersten Bestelldatum des Kunden. Berechnet durch Verbinden von `customer_entity.entity_id` mit `sales_order.customer_id` und Summieren des `base_grand_total`-Felds für alle Bestellungen, bei denen `sales_order.Seconds between customer's first order date and this order` ≤ 2592000, d. h. die Anzahl der Sekunden in 30 Tagen |
| `Customer's first order date` | Zeitstempel der ersten Bestellung dieses Kunden. Berechnet durch Verbinden von `customer_entity.entity_id` mit `sales_order.customer_id` und Zurückgeben der `sales_order`.`created_at` |
| `Customer's first order's billing region` | Rechnungsregion, die mit der ersten Bestellung des Kunden verknüpft ist. Berechnet durch Verbinden von `customer_entity.entity_id` mit `sales_order.customer_id` und Zurückgeben der `Billing address region` mit `sales_order.Customer's order number` = 1 |
| `Customer's first order's coupon_code` | Couponcode, der mit der ersten Bestellung des Kunden verknüpft ist. Berechnet durch Verbinden von `customer_entity.entity_id` mit `sales_order.customer_id` und Zurückgeben der `sales_order.coupon_code` mit `sales_order.Customer's order number` = 1 |
| `Customer's group code` | Gruppenname des registrierten Kunden. Berechnet durch Verbinden von `customer_entity.group_id` mit `customer_group`.`customer_group_id` und Zurückgeben des `customer_group_code` |
| `Customer's lifetime number of coupons` | Gesamtzahl der Coupons, die auf alle von diesem Kunden aufgegebenen Bestellungen angewendet wurden. Berechnet durch Verbinden von `customer_entity.entity_id` mit `sales_order.customer_id` und Zählen der Anzahl der Bestellungen, bei denen die `sales_order.coupon_code` nicht `NULL` ist |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Berechnet durch Verbinden von `customer_entity.entity_id` mit `sales_order.customer_id` und Zählen der Anzahl der Zeilen in der `sales_order` |
| `Customer's lifetime revenue` | Summe des Gesamtumsatzes für alle Bestellungen dieses Kunden. Berechnet, indem `customer_entity.entity_id` mit `sales_order.customer_id` verbunden und das Feld `base_grand_total` für alle Bestellungen dieses Kunden zusammengefasst wird |
| `Seconds since customer's first order date` | Verstrichene Zeit zwischen dem ersten Bestelldatum des Kunden und jetzt. Wird berechnet, indem `Customer's first order date` zum Zeitpunkt der Ausführung der Abfrage vom Server-Zeitstempel abgezogen und als ganzzahlige Anzahl von Sekunden zurückgegeben werden |
| `Store name` | Der Name des mit diesem registrierten Konto verknüpften Commerce-Stores. Berechnet durch Verbinden von `customer_entity.store_id` mit `store.store_id` und Zurückgeben des `name` |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Avg first 30 day revenue` | Der durchschnittliche Umsatz pro Kunde für Bestellungen, die innerhalb von 30 Tagen nach der ersten Bestellung des Kunden aufgegeben werden | Vorgang: Durchschnitt<br/>Operand: `Customer's first 30 day revenue`<br/>Zeitstempel: `created_at`<br/>Filter:<br/><br/>- \[A\] `Seconds since customer's first order date` ≥ 2592000 (umfasst Kunden, die seit ihrer ersten Bestellung noch keine 30 Tage erreicht haben) |
| `Avg lifetime coupons` | Die durchschnittliche Anzahl der Coupons, die auf Bestellungen pro Kunde während ihrer Lebensdauer angewendet werden | Vorgang: Durchschnitt<br/>Operand: `Customer's lifetime number of coupons`<br/>Zeitstempel: `created_at` |
| `Avg lifetime orders` | Die durchschnittliche Anzahl der Bestellungen pro Kunde während seines Lebenszyklus | Vorgang: Durchschnitt<br/>Operand: `Customer's lifetime number of orders`<br/>Zeitstempel: `created_at` |
| `Avg lifetime revenue` | Der durchschnittliche Gesamtumsatz pro Kunde für alle Bestellungen über ihre gesamte Lebensdauer | Vorgang: Durchschnitt<br/>Operand: `Customer's lifetime revenue`<br/>Zeitstempel: `created_at` |
| `New customers` | Die Anzahl der Kunden mit mindestens einer Bestellung, gezählt am Datum ihrer ersten Bestellung. Schließt Konten aus, die sich registrieren, aber nie bestellen | Vorgang: Anzahl<br/>Operand: `entity_id`<br/>Zeitstempel: `Customer's first order date` |
| `Registered accounts` | Die Anzahl der registrierten Konten. Umfasst alle registrierten Konten, unabhängig davon, ob das Konto jemals eine Bestellung aufgegeben hat | Vorgang: Anzahl<br/>Operand: `entity_id`<br/>Zeitstempel: `created_at` |

{style="table-layout:auto"}

## Fremdschlüssel-Verknüpfungspfade

`customer_group`

* Mit `customer_group` Tabelle verbinden, um Spalten zu erstellen, die den Kundengruppennamen des registrierten Kontos zurückgeben.
   * Pfad: `customer_entity.group_id` (viele) => `customer_group.customer_group_id` (eins)

`store`

* Mit `store` Tabelle verbinden, um Spalten zu erstellen, die Details zum Store zurückgeben, der mit dem registrierten Konto verknüpft ist.
   * Pfad: `customer_entity.store_id` (viele) => `store.store_id` (eins)
