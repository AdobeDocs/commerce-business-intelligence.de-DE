---
title: customer_entity table
description: Erfahren Sie, wie Sie auf Datensätze aller registrierten Konten zugreifen können.
exl-id: 24bf0e66-eea0-45ea-8ce6-4ff99b678201
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---

# customer_entity_table

Die Tabelle `customer_entity` enthält Datensätze aller registrierten Konten. Ein Konto gilt als registriert, wenn er sich für ein Konto anmeldet, unabhängig davon, ob er einen Kauf tätigt. Jede Zeile entspricht einem eindeutigen registrierten Konto, wie durch die `entity_id` dieses Kontos identifiziert.

Diese Tabelle enthält keine Datensätze zu Kunden, die eine Bestellung über einen Gastkasse aufgeben. Wenn Ihr Store einen Gastkassengang akzeptiert, finden Sie unter [Berücksichtigung von Gastbestellungen](../data-warehouse-mgr/guest-orders.md) weitere Informationen zu diesen Bestellungen.

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `created_at` | Zeitstempel, der dem Registrierungsdatum des Kontos entspricht und lokal in UTC gespeichert ist. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] konvertiert werden, die sich von Ihrer Zeitzone in der Datenbank unterscheidet |
| `email` | Mit dem Konto verknüpfte E-Mail-Adresse |
| `entity_id` (PK) | Eindeutige Kennung für die Tabelle und wird häufig in Joins mit dem `customer_id` in anderen Tabellen innerhalb der Instanz verwendet |
| `group_id` | Fremdschlüssel, der mit der Tabelle `customer_group` verknüpft ist. Treten Sie `customer_group.customer_group_id` bei, um die mit dem registrierten Konto verbundene Kundengruppe zu ermitteln. |
| `store_id` | Fremdschlüssel, der mit der Tabelle `store` verknüpft ist. Treten Sie `store` bei.`store_id` zur Bestimmung, welche Commerce Store-Ansicht mit dem registrierten Konto verknüpft ist |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's first 30 day revenue` | Summe des Umsatzes für alle von diesem Kunden aufgegebenen Bestellungen innerhalb von 30 Tagen nach dem ersten Bestelldatum des Kunden. Wird berechnet, indem `customer_entity.entity_id` zu `sales_order.customer_id` addiert und das Feld `base_grand_total` für alle Bestellungen summiert wird, bei denen `sales_order.Seconds between customer's first order date and this order` ≤ 2592000 ist, was der Anzahl der Sekunden in 30 Tagen entspricht |
| `Customer's first order date` | Zeitstempel der ersten von diesem Kunden aufgegebenen Bestellung. Wird berechnet, indem `customer_entity.entity_id` mit `sales_order.customer_id` verbunden wird und die minimale `sales_order` zurückgegeben wird.`created_at` Wert |
| `Customer's first order's billing region` | Rechnungsregion im Zusammenhang mit der ersten Bestellung des Kunden. Wird berechnet, indem `customer_entity.entity_id` zu `sales_order.customer_id` addiert und die `Billing address region` zurückgegeben wird, wobei `sales_order.Customer's order number` = 1 ist |
| `Customer's first order's coupon_code` | Couponcode, der der ersten Bestellung des Kunden zugeordnet ist. Wird berechnet, indem `customer_entity.entity_id` zu `sales_order.customer_id` addiert und die `sales_order.coupon_code` zurückgegeben wird, wobei `sales_order.Customer's order number` = 1 ist |
| `Customer's group code` | Gruppenname des registrierten Kunden. Errechnet durch Anreicherung von `customer_entity.group_id` an `customer_group`.`customer_group_id` und gibt das Feld `customer_group_code` zurück |
| `Customer's lifetime number of coupons` | Gesamtzahl der Gutscheine, die auf alle von diesem Kunden aufgegebenen Bestellungen angewendet wurden. Wird berechnet, indem `customer_entity.entity_id` zu `sales_order.customer_id` addiert und die Anzahl der Bestellungen gezählt wird, bei denen der `sales_order.coupon_code` nicht `NULL` ist |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Wird berechnet, indem `customer_entity.entity_id` mit `sales_order.customer_id` angefügt und die Anzahl der Zeilen in der `sales_order`-Tabelle gezählt wird |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle Bestellungen dieses Kunden. Wird berechnet, indem `customer_entity.entity_id` zu `sales_order.customer_id` addiert und das Feld `base_grand_total` für alle von diesem Kunden aufgegebenen Bestellungen summiert wird |
| `Seconds since customer's first order date` | Verstrichene Zeit zwischen dem ersten Bestelldatum des Kunden und jetzt. Wird berechnet, indem `Customer's first order date` vom Zeitstempel des Servers zum Zeitpunkt der Ausführung der Abfrage abgezogen wird und als ganzzahlige Anzahl von Sekunden zurückgegeben wird |
| `Store name` | Der Name des mit diesem registrierten Konto verknüpften Commerce-Stores. Wird berechnet, indem `customer_entity.store_id` zu `store.store_id` addiert und das Feld `name` zurückgegeben wird |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Konstruktion** |
|---|---|---|
| `Avg first 30 day revenue` | Durchschnittlicher Umsatz pro Kunde bei Bestellungen, die innerhalb von 30 Tagen nach der ersten Bestellung des Kunden aufgegeben werden | Vorgang: Average<br/>Operand: `Customer's first 30 day revenue`<br/>Timestamp: `created_at`<br/>Filters:<br/><br/>- \[A\] `Seconds since customer's first order date` ≥ 2592000 (schließt Kunden aus, die seit ihrer ersten Bestellung noch 30 Tage nicht erreicht haben) |
| `Avg lifetime coupons` | Durchschnittliche Anzahl der Gutscheine, die auf Bestellungen pro Kunde über deren Lebensdauer angewendet wurden | Vorgang: Average<br/>Operand: `Customer's lifetime number of coupons`<br/>Timestamp: `created_at` |
| `Avg lifetime orders` | Durchschnittliche Anzahl der Bestellungen pro Kunde über seine Lebensdauer | Vorgang: Average<br/>Operand: `Customer's lifetime number of orders`<br/>Timestamp: `created_at` |
| `Avg lifetime revenue` | Durchschnittlicher Gesamtumsatz pro Kunde für alle Bestellungen, die über seine Lebensdauer aufgegeben wurden | Vorgang: Average<br/>Operand: `Customer's lifetime revenue`<br/>Timestamp: `created_at` |
| `New customers` | Die Anzahl der Kunden mit mindestens einer Bestellung, die zum Datum ihrer ersten Bestellung gezählt werden. Schließt Konten aus, die sich registrieren, aber nie eine Bestellung aufgeben | Vorgang: Count<br/>Operand: `entity_id`<br/>Zeitstempel: `Customer's first order date` |
| `Registered accounts` | Die Anzahl der registrierten Konten. Umfasst alle registrierten Konten, unabhängig davon, ob das Konto jemals eine Bestellung aufgegeben hat | Vorgang: Count<br/>Operand: `entity_id`<br/>Zeitstempel: `created_at` |

{style="table-layout:auto"}

## Verbindungswege für Fremdschlüssel

`customer_group`

* Treten Sie der Tabelle `customer_group` bei, um Spalten zu erstellen, die den Kundengruppennamen des registrierten Kontos zurückgeben.
   * Pfad: `customer_entity.group_id` (viele) => `customer_group.customer_group_id` (eins)

`store`

* Treten Sie der Tabelle `store` bei, um Spalten zu erstellen, die Details zum Store zurückgeben, der mit dem registrierten Konto verknüpft ist.
   * Pfad: `customer_entity.store_id` (viele) => `store.store_id` (eins)
