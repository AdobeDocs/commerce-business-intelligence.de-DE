---
title: Speichern von Daten in Adobe Commerce
description: Erfahren Sie, wie Daten generiert werden, was dazu führt, dass eine neue Zeile eingefügt wird und wie Aktionen in die Adobe Commerce-Datenbank aufgenommen werden.
exl-id: 436ecdc1-7112-4dec-9db7-1f3757a2a938
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 2%

---

# Speichern von Daten in [!DNL Adobe Commerce]

Die [!DNL Adobe Commerce]-Plattform zeichnet eine Vielzahl wertvoller Commerce-Daten auf und organisiert sie über Hunderte von Tabellen. Dieses Thema beschreibt:

* wie diese Daten generiert werden
* was bewirkt, dass eine neue Zeile in eine der [Kern-Commerce-Tabellen](../data-warehouse-mgr/common-mage-tables.md) eingefügt wird
* wie Aktionen wie Einkäufe oder die Erstellung eines Kontos in der [!DNL Adobe Commerce]-Datenbank aufgezeichnet werden

Weitere Informationen zu diesen Konzepten finden Sie im folgenden Beispiel:

`Clothes4U` ist ein Bekleidungshändler, der sowohl online als auch mit einer Ziegel- und einer Mörserpräsenz arbeitet. Es verwendet [!DNL Magento Open Source] hinter seiner Website, um Daten zu sammeln und zu organisieren.

## `catalog\_product\_entity`

Es ist der 22. September, und `Clothes4U` wird drei neue Artikel in seine Herbstlinie einfließen lassen: `Throwback Bellbottoms`, `Straight Leg Jeans` und `V-Neck T-Shirts`. Ein `Clothes4U` Mitarbeiter öffnet seinen Commerce-Admin, klickt auf **[!UICONTROL Add Product]** und gibt alle Informationen für `Throwback Bellbottoms` ein.

In Übereinstimmung mit allen Einstellungen für `Throwback Bellbottoms` klickt der Mitarbeiter auf **[!UICONTROL Save]**, wodurch die erste Zeile darunter in die Tabelle `catalog_product_entity` eingefügt wird. Der Mitarbeiter wiederholt den Vorgang, erstellt ein weiteres Commerce-Produkt für `Straight Leg Jeans` und anschließend ein drittes für `V-Neck T-Shirt` und fügt die zweite und dritte Zeile unten in die Tabelle `catalog_product_entity` ein:

| **`entity\_id`** | **`entity\_type\_id`** | **`attribute\_set\_id`** | **`sku`** | **`created\_at`** |
|---|---|---|---|---|
| 205 | 4 | 8 | Pants10 | 22.09.2016:15:43 |
| 206 | 4 | 8 | Pants11 | 22.09.2016:18:17 |
| 207 | 4 | 12 | Shirts6 | 22.9.2016:24:02 |

* `entity_id` - Dies ist der Primärschlüssel der Tabelle `catalog_product_entity`, d. h. jede Zeile der Tabelle muss einen anderen `entity_id` aufweisen. Jede `entity_id` auf dieser Tabelle kann nur mit einem Produkt verknüpft werden und jedes Produkt kann nur mit einem `entity_id` verknüpft werden.
   * Die oberste Zeile der obigen Tabelle, `entity_id` = 205, ist die neue Zeile, die für &quot;Throwback Bellbottom&quot;erstellt wurde. Wohin `entity_id` = 205 auf der Commerce-Plattform angezeigt wird, bezieht sich dies auf das Produkt &quot;Throwback Bellbooms&quot;.
* `entity_type_id` - Commerce hat mehrere Objektkategorien (z. B. Kunden, Adressen und Produkte, um einige zu nennen). Diese Spalte dient zur Bezeichnung der Kategorie, in die diese bestimmte Zeile fällt.
   * Da es sich um die Tabelle `catalog_product_entity` handelt, weist jede Zeile denselben Entitätstyp auf: product. In Adobe Commerce beträgt der Wert für &quot;`entity_type_id`&quot;für das Produkt 4. Daher geben alle drei neu erstellten Produkte 4 für diese Spalte zurück.
* `attribute_set_id` - Attributsätze werden verwendet, um Produkte zu identifizieren, die dieselben Deskriptoren aufweisen.
   * Die oberen beiden Zeilen der Tabelle sind die `Throwback Bellbottoms` - und `Straight Leg Jeans` -Produkte, bei denen es sich jeweils um Hosen handelt. Diese Produkte hätten dieselben Deskriptoren (z. B. Name, inseam, waistline) und haben daher denselben `attribute_set_id`. Das dritte Element, `V-Neck T-Shirt`, hat einen anderen `attribute_set_id`, da es nicht die gleichen Deskriptoren wie die Hosen hätte; Hemden haben keine Striche oder Inseams.
* `sku` - Hierbei handelt es sich um eindeutige Werte, die dem jeweiligen Produkt vom Benutzer beim Erstellen eines Produkts in Adobe Commerce zugewiesen werden.
* `created_at` - Diese Spalte gibt den Zeitstempel zurück, zu dem die einzelnen Produkte erstellt wurden

## `customer\_entity`

Kurz nach dem Hinzufügen der drei neuen Produkte besucht ein neuer Kunde, `Sammy Customer`, erstmals die Website von `Clothes4U`. Da `Clothes4U` keine Gastaufträge zulässt, muss `Sammy Customer` zunächst ein Konto auf der Website erstellen. Der Kunde gibt die erforderlichen Anmeldeinformationen ein und klickt auf &quot;Senden&quot;, was zu dem folgenden neuen Eintrag in der [`customer\_entity table`](../data-warehouse-mgr/cust-ent-table.md) führt:

| **`entity id`** | **`entity type id`** | **`email`** | **`created at`** |
|---|---|---|---|
| `214` | `1` | `sammy.customer@gmail.com` | `2016/09/23 15:27:12` |

* `entity_id` - Genau wie die vorherige Tabelle ist `entity_id` der Primärschlüssel der `customer_entity` Tabelle.
   * Als `Sammy Customer` ein Konto erstellt und die obige Zeile in die Tabelle `customer_entity` geschrieben wurde, wurde dem Kunden `entity_id` = 214 zugewiesen. In allen Tabellen bezieht sich der als `entity_id` = 214 identifizierte Kunde immer auf den Benutzer Sammy Customer
* `entity_type_id` - Diese Spalte identifiziert, welcher Entitätstyp in dieser Tabelle aufgelistet wird, und funktioniert genauso wie in der `catalog_product_entity`-Tabelle
   * Jede Zeile der Tabelle `customer_entity` ist ein Kunde, und Commerce definiert Kunden standardmäßig als `entity_type_id` 1
* `email` - Dieses Feld wird durch die E-Mail ausgefüllt, die ein neuer Kunde bei der Kontoerstellung eingibt.
* `created_at` - Diese Spalte gibt den Zeitstempel für den Zeitpunkt zurück, zu dem jeder Benutzer Mitglied wurde

## `sales\_flat\_order (or Sales\_order` , wenn Sie [!DNL Adobe Commerce 2.x] haben

Nachdem die Kontoerstellung abgeschlossen ist, ist `Sammy Customer` bereit, einen Kauf zu tätigen. Auf der Website fügt der Kunde dem Warenkorb zwei Paare von `Throwback Bellbottoms` und einem `V-Neck T-Shirt` hinzu. Mit der Auswahl zufrieden, wechselt der Kunde zum Checkout und sendet die Bestellung. Dadurch wird der folgende Eintrag in der Tabelle [für die pauschale Bestellung](../data-warehouse-mgr/sales-flat-order-table.md) für den Vertrieb erstellt:

| **`entity id`** | **`customer id**` | **`subtotal`** | **`created at`** |
|---|---|---|---|
| 227 | 214 | 94,85 | 23.9.2016 15:41:39 |

* `entity_id` - Dies ist der Primärschlüssel der Tabelle `sales_flat_order`.
   * Als Sammy Customer diese Bestellung aufgab und die obige Zeile in die Tabelle `sales_flat_order` geschrieben wurde, wurde der Bestellung `entity_id` = 227 zugewiesen.
* `customer_id` - Diese Spalte ist die eindeutige Kennung des Kunden, der diese bestimmte Bestellung aufgegeben hat.
   * Die mit dieser Bestellung verbundene `customer_id` ist 214, was der `entity_id` des Sammy-Kunden in der `customer_entity`-Tabelle entspricht.
* `subtotal` - Diese Spalte ist der Gesamtbetrag, der einem Kunden für die Bestellung in Rechnung gestellt wird.
   * Die beiden Paare von &quot;Throwback Bellboden&quot;und &quot;V-Neck T-Shirt&quot;kosten insgesamt 94,85 Dollar
* `created_at` - Diese Spalte gibt den Zeitstempel für die Erstellung jeder Bestellung zurück

## `sales\_flat\_order\_item ( or Sales\_order\_item`

(wenn Sie über Commerce 2.0 oder höher verfügen)

Zusätzlich zur einzelnen Zeile in der Tabelle `Sales\_flat\_order` wird beim Senden der Reihenfolge durch `Sammy Customer` eine Zeile für jedes eindeutige Element in dieser Reihenfolge in die Tabelle [`sales\_flat\_order\_item` Tabelle](../data-warehouse-mgr/sales-flat-order-item-table.md) eingefügt:

| **`item\_id`** | **`name`** | **`product\_id`** | **`order\_id`** | **`qty\_ordered`** | **`price`** |
|---|---|---|---|---|---|
| 822 | `Throwback Bellbottoms` | 205 | 227 | 2 | 39,95 |
| 823 | `V-Neck T-Shirt` | 207 | 227 | 1 | 14,95 |

* `item_id` - Diese Spalte ist der Primärschlüssel der Tabelle `sales_flat_order_item`
   * Die Reihenfolge von `Sammy Customer` hat für diese Tabelle zwei Zeilen erstellt, da die Bestellung zwei verschiedene Produkte enthielt
* `name` - Diese Spalte ist der Name des Produkts
* `product_id` - Diese Spalte ist die eindeutige Kennung des Produkts, auf das diese Zeile verweist.
   * Die erste Zeile oben hat `product_id` = 205, da `Throwback Bellbottoms` auf der Tabelle `catalog_product_entity` den Wert 205 hat.`entity_id`
* `order_id` - Diese Spalte ist die `entity_id` der Reihenfolge, die diese bestimmten Bestellelemente enthält
   * Beide Zeilen oben haben &quot;`order_id` = 227&quot;, da sie beide Teil der Reihenfolge sind, die von &quot;`Sammy Customer`&quot;platziert wird, was &quot;`entity_id` = 227&quot;auf der Tabelle &quot;`sales_flat_order`&quot;hat
* `qty_ordered` - Diese Spalte ist die Anzahl der Einheiten des Produkts, die in dieser bestimmten Reihenfolge enthalten sind
   * Die Reihenfolge `Sammy Customer` enthielt zwei Paare von `Throwback Bellbottoms`
* `price` - Diese Spalte ist der Preis einer einzelnen Einheit des Bestellartikels
   * Die `subtotal` aus der Reihenfolge `Sammy Customer` in der Tabelle `sales_flat_order` betrug 94,85, was der Summe zweier Paare von `Throwback Bellbottoms` bei jeweils 39,95 USD und 1 `V-Neck T-Shirt` bei 14,95 USD entspricht.
