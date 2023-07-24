---
title: customer_entity table
description: Erfahren Sie, wie Sie auf Datensätze aller registrierten Konten zugreifen können.
exl-id: 24bf0e66-eea0-45ea-8ce6-4ff99b678201
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# customer_entity_table

Die `customer_entity` enthält die Datensätze aller registrierten Konten. Ein Konto gilt als registriert, wenn er sich für ein Konto anmeldet, unabhängig davon, ob er einen Kauf tätigt. Jede Zeile entspricht einem eindeutigen registrierten Konto, wie durch das `entity_id`.

Diese Tabelle enthält keine Datensätze zu Kunden, die eine Bestellung über einen Gastkasse aufgeben. Wenn Ihr Geschäft einen Gast-Checkout akzeptiert, lesen Sie [Wie werden Gastbestellungen erfasst?](../data-warehouse-mgr/guest-orders.md) für diese Aufträge.

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `created_at` | Zeitstempel, der dem Registrierungsdatum des Kontos entspricht und lokal in UTC gespeichert ist. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence], kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] , die sich von der Zeitzone Ihrer Datenbank unterscheidet |
| `email` | Mit dem Konto verknüpfte E-Mail-Adresse |
| `entity_id` (PK) | Eindeutige Kennung für die Tabelle und wird häufig in Joins zum `customer_id` in anderen Tabellen innerhalb der Instanz |
| `group_id` | Fremdschlüssel, der mit dem `customer_group` Tabelle. Mitglied werden `customer_group.customer_group_id` zur Bestimmung der Kundengruppe, die mit dem registrierten Konto verknüpft ist |
| `store_id` | Fremdschlüssel, der mit dem `store` Tabelle. Mitglied werden `store`.`store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit dem registrierten Konto verknüpft ist |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's first 30 day revenue` | Summe des Umsatzes für alle von diesem Kunden aufgegebenen Bestellungen innerhalb von 30 Tagen nach dem ersten Bestelldatum des Kunden. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und die `base_grand_total` -Feld für alle Bestellungen, bei denen `sales_order.Seconds between customer's first order date and this order` ≤ 2592000, d. h. die Anzahl der Sekunden in 30 Tagen |
| `Customer's first order date` | Zeitstempel der ersten von diesem Kunden aufgegebenen Bestellung. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und die Angabe des Mindestwerts `sales_order`.`created_at` value |
| `Customer's first order's billing region` | Rechnungsregion im Zusammenhang mit der ersten Bestellung des Kunden. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und die `Billing address region` where `sales_order.Customer's order number` = 1 |
| `Customer's first order's coupon_code` | Couponcode, der der ersten Bestellung des Kunden zugeordnet ist. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und die `sales_order.coupon_code` where `sales_order.Customer's order number` = 1 |
| `Customer's group code` | Gruppenname des registrierten Kunden. Errechnet durch Verbinden `customer_entity.group_id` nach `customer_group`.`customer_group_id` und die `customer_group_code` field |
| `Customer's lifetime number of coupons` | Gesamtzahl der Gutscheine, die auf alle von diesem Kunden aufgegebenen Bestellungen angewendet wurden. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und Zählung der Anzahl der Bestellungen, bei denen die Variable `sales_order.coupon_code` ist nicht `NULL` |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und die Anzahl der Zeilen in der `sales_order` table |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle von diesem Kunden aufgegebenen Bestellungen. Errechnet durch Verbinden `customer_entity.entity_id` nach `sales_order.customer_id` und die `base_grand_total` Feld für alle von diesem Kunden aufgegebenen Bestellungen |
| `Seconds since customer's first order date` | Verstrichene Zeit zwischen dem ersten Bestelldatum des Kunden und jetzt. Berechnet durch Subtraktion `Customer's first order date` vom Server-Zeitstempel zum Zeitpunkt der Ausführung der Abfrage zurückgegeben, als ganzzahlige Anzahl von Sekunden |
| `Store name` | Der Name des mit diesem registrierten Konto verknüpften Commerce-Stores. Errechnet durch Verbinden `customer_entity.store_id` nach `store.store_id` und die `name` field |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Avg first 30 day revenue` | Durchschnittlicher Umsatz pro Kunde bei Bestellungen, die innerhalb von 30 Tagen nach der ersten Bestellung des Kunden aufgegeben werden | Vorgang: Durchschnittlich<br/>Operand: `Customer's first 30 day revenue`<br/>Zeitstempel: `created_at`<br/>Filter:<br/><br/>- \[A\] `Seconds since customer's first order date` ≥ 2592000 (ausgenommen Kunden, die seit ihrer ersten Bestellung noch 30 Tage nicht erreicht haben) |
| `Avg lifetime coupons` | Durchschnittliche Anzahl der Gutscheine, die auf Bestellungen pro Kunde über deren Lebensdauer angewendet wurden | Vorgang: Durchschnittlich<br/>Operand: `Customer's lifetime number of coupons`<br/>Zeitstempel: `created_at` |
| `Avg lifetime orders` | Durchschnittliche Anzahl der Bestellungen pro Kunde über seine Lebensdauer | Vorgang: Durchschnittlich<br/>Operand: `Customer's lifetime number of orders`<br/>Zeitstempel: `created_at` |
| `Avg lifetime revenue` | Durchschnittlicher Gesamtumsatz pro Kunde für alle Bestellungen, die über seine Lebensdauer aufgegeben wurden | Vorgang: Durchschnittlich<br/>Operand: `Customer's lifetime revenue`<br/>Zeitstempel: `created_at` |
| `New customers` | Die Anzahl der Kunden mit mindestens einer Bestellung, die zum Datum ihrer ersten Bestellung gezählt werden. Schließt Konten aus, die sich registrieren, aber nie eine Bestellung aufgeben | Vorgang: Count<br/>Operand: `entity_id`<br/>Zeitstempel: `Customer's first order date` |
| `Registered accounts` | Die Anzahl der registrierten Konten. Umfasst alle registrierten Konten, unabhängig davon, ob das Konto jemals eine Bestellung aufgegeben hat | Vorgang: Count<br/>Operand: `entity_id`<br/>Zeitstempel: `created_at` |

{style="table-layout:auto"}

## Verbindungswege für Fremdschlüssel

`customer_group`

* Mitglied werden `customer_group` -Tabelle, um Spalten zu erstellen, die den Kundengruppennamen des registrierten Kontos zurückgeben.
   * Pfad: `customer_entity.group_id` (viele) => `customer_group.customer_group_id` (eins)

`store`

* Mitglied werden `store` -Tabelle verwenden, um Spalten zu erstellen, die Details zum Store zurückgeben, der mit dem registrierten Konto verknüpft ist.
   * Pfad: `customer_entity.store_id` (viele) => `store.store_id` (eins)
