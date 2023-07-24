---
title: Speichern von Daten in Adobe Commerce
description: Erfahren Sie, wie Daten generiert werden, was dazu führt, dass eine neue Zeile eingefügt wird und wie Aktionen in die Adobe Commerce-Datenbank aufgenommen werden.
exl-id: 436ecdc1-7112-4dec-9db7-1f3757a2a938
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 3%

---

# Speichern von Daten in [!DNL Adobe Commerce]

Die [!DNL Adobe Commerce] Plattform erfasst und organisiert eine Vielzahl wertvoller Commerce-Daten über Hunderte von Tabellen hinweg. Dieses Thema beschreibt:

* wie diese Daten generiert werden
* was dazu führt, dass eine neue Zeile in eine der [Commerce-Haupttabellen](../data-warehouse-mgr/common-mage-tables.md)
* wie Aktionen wie der Kauf oder die Erstellung eines Kontos in der Variablen [!DNL Adobe Commerce] Datenbank

Weitere Informationen zu diesen Konzepten finden Sie im folgenden Beispiel:

`Clothes4U` ist ein Bekleidungshändler, der sowohl online als auch über eine Vorstellung von Ziegelsteinen und Mörtel verfügt. Sie verwendet [!DNL Magento Open Source] hinter der Website, um Daten zu sammeln und zu organisieren.

## `catalog\_product\_entity`

Es ist der 22. September und `Clothes4U` stellt drei neue Artikel zur Herbstlinie bereit: `Throwback Bellbottoms`, `Straight Leg Jeans`und `V-Neck T-Shirts`. A `Clothes4U` Mitarbeiter öffnet ihren Commerce Admin, klickt auf **[!UICONTROL Add Product]** und gibt alle Informationen für `Throwback Bellbottoms`.

Mit allen Einstellungen für `Throwback Bellbottoms`, klickt der Mitarbeiter auf **[!UICONTROL Save]**, wodurch die erste Zeile unten in die `catalog_product_entity` Tabelle. Der Mitarbeiter wiederholt den Prozess und erstellt ein weiteres Commerce-Produkt für `Straight Leg Jeans`und dann ein Drittel für `V-Neck T-Shirt`, indem die zweite und dritte Zeile unten in die `catalog_product_entity` table:

| **`entity\_id`** | **`entity\_type\_id`** | **`attribute\_set\_id`** | **`sku`** | **`created\_at`** |
|---|---|---|---|---|
| 205 | 4 | 8 | Pants10 | 2016/09/22 09:15:43 |
| 206 | 4 | 8 | Pants11 | 2016/09/22 09:18:17 |
| 207 | 4 | 12 | Shirts6 | 2016/09/22 09:24:02 |

* `entity_id` - Dies ist der Primärschlüssel der `catalog_product_entity` -Tabelle, d. h. jede Tabellenzeile muss eine andere `entity_id`. Jeder `entity_id` auf dieser Tabelle kann nur mit einem Produkt verknüpft werden und jedes Produkt kann nur mit einem `entity_id`
   * die oberste Zeile der obigen Tabelle, `entity_id` = 205, ist die neue Zeile, die für &quot;Throwback Bellbottom&quot;erstellt wurde. Wherever `entity_id` = 205 in der Commerce-Plattform angezeigt wird, es bezieht sich auf das Produkt &quot;Throwback Bellbottom&quot;
* `entity_type_id` - Commerce hat mehrere Objektkategorien (z. B. Kunden, Adressen und Produkte, um einige zu nennen). Diese Spalte dient zur Bezeichnung der Kategorie, in die diese bestimmte Zeile fällt.
   * Dies ist die `catalog_product_entity` -Tabelle verwenden, weist jede Zeile denselben Entitätstyp auf: Produkt. In Adobe Commerce wird die `entity_type_id` für das Produkt ist 4, weshalb alle drei neu erstellten Produkte 4 für diese Spalte zurückgeben.
* `attribute_set_id` - Attributsätze werden verwendet, um Produkte zu identifizieren, die dieselben Deskriptoren aufweisen.
   * Die oberen beiden Zeilen der Tabelle sind die `Throwback Bellbottoms` und `Straight Leg Jeans` Produkte, bei denen es sich jeweils um Hosen handelt. Diese Produkte hätten dieselben Deskriptoren (z. B. Name, inseam, waistline) und hätten daher die gleichen `attribute_set_id`. dritter Punkt, `V-Neck T-Shirt` hat eine andere `attribute_set_id` weil sie nicht dieselben Deskriptoren wie die Hosen hätte; Hemden haben keine Bänder oder Inseams.
* `sku` - Hierbei handelt es sich um eindeutige Werte, die dem jeweiligen Produkt vom Benutzer beim Erstellen eines Produkts in Adobe Commerce zugewiesen werden.
* `created_at` - Diese Spalte gibt den Zeitstempel zurück, zu dem die einzelnen Produkte erstellt wurden.

## `customer\_entity`

Kurz nach dem Hinzufügen der drei neuen Produkte hat ein neuer Kunde `Sammy Customer`, Besuche `Clothes4U`ist zum ersten Mal auf der Website. Seit `Clothes4U` erlaubt keine Gastaufträge, `Sammy Customer` muss zunächst ein Konto auf der Website erstellen. Der Kunde gibt die erforderlichen Anmeldeinformationen ein und klickt auf &quot;Senden&quot;. Daraufhin wird der folgende neue Eintrag in der [`customer\_entity table`](../data-warehouse-mgr/cust-ent-table.md):

| **`entity id`** | **`entity type id`** | **`email`** | **`created at`** |
|---|---|---|---|
| `214` | `1` | `sammy.customer@gmail.com` | `2016/09/23 15:27:12` |

* `entity_id` - Genau wie die vorherige Tabelle, `entity_id` ist der Primärschlüssel der `customer_entity` Tabelle.
   * Wann `Sammy Customer` ein Konto erstellt und die obige Zeile in die `customer_entity` Tabelle, wurde dem Kunden zugewiesen `entity_id` = 214. In allen Tabellen identifiziert der Kunde `entity_id` = 214 bezieht sich immer auf den Benutzer Sammy Customer
* `entity_type_id` - Diese Spalte identifiziert, welcher Entitätstyp in dieser Tabelle aufgelistet wird, und funktioniert auf die gleiche Weise wie in der `catalog_product_entity` table
   * Jede Zeile auf der `customer_entity` -Tabelle ist ein Kunde und Commerce definiert Kunden als `entity_type_id` 1 standardmäßig
* `email` - Dieses Feld wird durch die E-Mail-Adresse gefüllt, die ein neuer Kunde bei der Kontoerstellung eingibt.
* `created_at` - Diese Spalte gibt den Zeitstempel für den Zeitpunkt zurück, zu dem jeder Benutzer Mitglied wurde

## `sales\_flat\_order (or Sales\_order` wenn Sie [!DNL Adobe Commerce 2.x]

Mit Abschluss der Kontoerstellung `Sammy Customer` ist bereit, einen Kauf zu tätigen. Auf der Website fügt der Kunde zwei Paare der `Throwback Bellbottoms` und einem `V-Neck T-Shirt` in den Warenkorb. Mit der Auswahl zufrieden, wechselt der Kunde zum Checkout und sendet die Bestellung, wodurch der folgende Eintrag auf der [Verkaufstabelle](../data-warehouse-mgr/sales-flat-order-table.md):

| **`entity id`** | **`customer id**` | **`subtotal`** | **`created at`** |
|---|---|---|---|
| 227 | 214 | 94.85 | 2016/09/23 15:41:39 |

* `entity_id` - dies ist der Primärschlüssel der `sales_flat_order` Tabelle.
   * Als Sammy Customer diese Bestellung aufgab und die obige Zeile in die `sales_flat_order` -Tabelle, wurde die Reihenfolge zugewiesen. `entity_id` = 227.
* `customer_id` - Diese Spalte ist die eindeutige Kennung des Kunden, der diese bestimmte Bestellung aufgegeben hat.
   * Die `customer_id` mit dieser Bestellung verknüpft ist, ist 214, das ist der von Sammy-Kunden `entity_id` auf `customer_entity` Tabelle.
* `subtotal` - Diese Spalte ist der Gesamtbetrag, der einem Kunden für die Bestellung in Rechnung gestellt wird.
   * Die beiden Paare von &quot;Throwback Bellboden&quot;und &quot;V-Neck T-Shirt&quot;kosten insgesamt 94,85 Dollar
* `created_at` - Diese Spalte gibt den Zeitstempel für den Zeitpunkt der Erstellung jeder Bestellung zurück.

## `sales\_flat\_order\_item ( or Sales\_order\_item`

(bei Commerce 2.0 oder höher)

Zusätzlich zur einzelnen Zeile auf der `Sales\_flat\_order` Tabelle, wann `Sammy Customer` sendet die Reihenfolge. Eine Zeile für jedes eindeutige Element in dieser Reihenfolge wird in die [`sales\_flat\_order\_item` table](../data-warehouse-mgr/sales-flat-order-item-table.md):

| **`item\_id`** | **`name`** | **`product\_id`** | **`order\_id`** | **`qty\_ordered`** | **`price`** |
|---|---|---|---|---|---|
| 822 | `Throwback Bellbottoms` | 205 | 227 | 2 | 39.95 |
| 823 | `V-Neck T-Shirt` | 207 | 227 | 1 | 14.95 |

* `item_id` - Diese Spalte ist der Primärschlüssel der `sales_flat_order_item` table
   * `Sammy Customer`Die Bestellung von hat zwei Zeilen für diese Tabelle erstellt, da die Bestellung zwei verschiedene Produkte enthielt
* `name` - Diese Spalte ist der Name des Produkts.
* `product_id` - Diese Spalte ist die eindeutige Kennung des Produkts, auf das diese Zeile verweist.
   * Die erste Zeile oben hat `product_id` = 205, weil `Throwback Bellbottoms` über eine `entity_id` von 2005 über die `catalog_product_entity` table
* `order_id` - Diese Spalte ist die `entity_id` der Reihenfolge, die diese bestimmten Bestellelemente enthält
   * Beide Zeilen oben haben `order_id` = 227, da beide Teil der von `Sammy Customer`, die `entity_id` = 227 auf der `sales_flat_order` table
* `qty_ordered` - Diese Spalte ist die Anzahl der Einheiten des Produkts, die in dieser spezifischen Reihenfolge enthalten sind
   * `Sammy Customer`Die -Reihenfolge enthielt zwei Paare von `Throwback Bellbottoms`
* `price` - Diese Spalte ist der Preis einer einzelnen Einheit des Bestellartikels.
   * Die `subtotal` von `Sammy Customer`&quot;s -Reihenfolge in der `sales_flat_order` -Tabelle war 94,85, was der Summe zweier Paare von `Throwback Bellbottoms` jeweils 39,95 $ und 1 $ `V-Neck T-Shirt` 14,95 $.
