---
title: Speichern von Daten in Adobe Commerce
description: Erfahren Sie, wie Daten generiert werden, wodurch eine neue Zeile eingefügt wird und wie Aktionen in der Adobe Commerce-Datenbank aufgezeichnet werden.
exl-id: 436ecdc1-7112-4dec-9db7-1f3757a2a938
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 2%

---

# Speichern von Daten in [!DNL Adobe Commerce]

Die [!DNL Adobe Commerce]-Plattform erfasst und organisiert eine Vielzahl wertvoller Commerce-Daten über Hunderte von Tabellen hinweg. In diesem Thema wird Folgendes beschrieben:

* So werden diese Daten generiert
* was dazu führt, dass eine neue Zeile in eine der [Commerce-Kerntabellen“ eingefügt ](../data-warehouse-mgr/common-mage-tables.md)
* Wie Aktionen wie der Kauf oder die Erstellung eines Kontos in der [!DNL Adobe Commerce]-Datenbank aufgezeichnet werden

Um diese Konzepte zu besprechen, sehen Sie sich das folgende Beispiel an:

`Clothes4U` ist ein Bekleidungseinzelhändler, der sowohl online als auch aus Ziegeln und Mörtel besteht. Sie verwendet [!DNL Magento Open Source] hinter ihrer Website, um Daten zu sammeln und zu organisieren.

## `catalog\_product\_entity`

Es ist der 22. September, und `Clothes4U` führt drei neue Elemente zu seiner Herbstlinie ein: `Throwback Bellbottoms`, `Straight Leg Jeans` und `V-Neck T-Shirts`. Ein `Clothes4U` Mitarbeiter öffnet seinen Commerce Admin, klickt auf **[!UICONTROL Add Product]** und gibt alle Informationen für die `Throwback Bellbottoms` ein.

Zufrieden mit allen Einstellungen für `Throwback Bellbottoms` klickt der Mitarbeiter auf **[!UICONTROL Save]**, wodurch die erste Zeile unten in die `catalog_product_entity` eingefügt wird. Der Mitarbeiter wiederholt diesen Vorgang und erstellt ein weiteres Commerce-Produkt für die `Straight Leg Jeans`, gefolgt von einer dritten für die `V-Neck T-Shirt`. Fügen Sie die zweite und dritte Zeile unten in die `catalog_product_entity` ein:

| **`entity\_id`** | **`entity\_type\_id`** | **`attribute\_set\_id`** | **`sku`** | **`created\_at`** |
|---|---|---|---|---|
| 205 | 4 | 8 | Hose10 | 22.09.2016 09:15:43 |
| 206 | 4 | 8 | Hose11 | 22.09.2016 09:18:17 |
| 207 | 4 | 12 | Hemden6 | 22.09.2016 09:24:02 |

* `entity_id` - Dies ist der Primärschlüssel der `catalog_product_entity`, d. h. jede Zeile der Tabelle muss eine andere `entity_id` haben. Jeder `entity_id` in dieser Tabelle kann nur einem Produkt zugeordnet werden und jedes Produkt kann nur einem `entity_id` zugeordnet werden
   * Die oberste Zeile der obigen Tabelle, `entity_id` = 205, ist die neue Zeile, die für „Throwback Bellbottom“ erstellt wurde. Wo immer `entity_id` = 205 in der Commerce-Plattform angezeigt wird, bezieht sich dies auf das Produkt „Throwback Bellboths“
* `entity_type_id` - Commerce verfügt über mehrere Objektkategorien (z. B. Kunden, Adressen und Produkte, um nur einige zu nennen). Diese Spalte wird verwendet, um die Kategorie zu kennzeichnen, in die diese bestimmte Zeile fällt.
   * Da dies die `catalog_product_entity` Tabelle ist, hat jede Zeile denselben Entitätstyp: product. In Adobe Commerce lautet der `entity_type_id` für Produkt 4. Aus diesem Grund geben alle drei neu erstellten Produkte 4 für diese Spalte zurück.
* `attribute_set_id` - Attributsätze werden verwendet, um Produkte mit denselben Deskriptoren zu identifizieren.
   * Die beiden obersten Zeilen der Tabelle sind die `Throwback Bellbottoms` und `Straight Leg Jeans` Produkte, die beide Hosen sind. Diese Produkte hätten die gleichen Deskriptoren (z. B. Name, Einnahmung, Taille) und daher die gleiche `attribute_set_id`. Der dritte Artikel, `V-Neck T-Shirt`, hat einen anderen `attribute_set_id`, weil er nicht die gleichen Deskriptoren wie die Hose hätte; Hemden haben keine Taillenbänder oder Innähte.
* `sku` : Hierbei handelt es sich um eindeutige Werte, die den einzelnen Produkten vom Benutzer beim Erstellen eines Produkts in Adobe Commerce zugewiesen werden.
* `created_at` - Diese Spalte gibt den Zeitstempel zurück, an dem jedes Produkt erstellt wurde

## `customer\_entity`

Kurz nach dem Hinzufügen der drei neuen Produkte besucht ein neuer Kunde, `Sammy Customer`, zum ersten Mal die Website von `Clothes4U`. Da `Clothes4U` keine Gastbestellungen zulässt, müssen `Sammy Customer` zunächst ein Konto auf der Website erstellen. Der Kunde gibt die erforderlichen Anmeldeinformationen ein und klickt auf „Senden“, was zu folgendem neuen Eintrag im [`customer\_entity table`](../data-warehouse-mgr/cust-ent-table.md) führt:

| **`entity id`** | **`entity type id`** | **`email`** | **`created at`** |
|---|---|---|---|
| `214` | `1` | `sammy.customer@gmail.com` | `2016/09/23 15:27:12` |

* `entity_id` - Wie die vorherige Tabelle ist `entity_id` der Primärschlüssel der `customer_entity`.
   * Als `Sammy Customer` ein Konto erstellt und die obige Zeile in die `customer_entity`-Tabelle geschrieben wurde, wurde dem Kunden `entity_id` = 214 zugewiesen. In allen Tabellen bezieht sich der als `entity_id` = 214 identifizierte Kunde immer auf den Benutzer Sammy Customer
* `entity_type_id` - Diese Spalte identifiziert, welcher Entitätstyp in dieser Tabelle aufgeführt wird, und funktioniert genauso wie in der `catalog_product_entity`
   * Jede Zeile in der `customer_entity` ist ein Kunde, und Commerce definiert Kunden standardmäßig als `entity_type_id` 1
* `email` - Dieses Feld wird mit der E-Mail ausgefüllt, die ein neuer Kunde bei der Kontoerstellung eingibt
* `created_at` - Diese Spalte gibt den Zeitstempel für den Zeitpunkt zurück, zu dem jeder Benutzer Mitglied wurde

## `sales\_flat\_order (or Sales\_order`, wenn Sie [!DNL Adobe Commerce 2.x] haben

Nachdem die Kontoerstellung abgeschlossen ist, ist `Sammy Customer` bereit, einen Kauf zu tätigen. Auf der Website fügt der Kunde zwei `Throwback Bellbottoms` und ein `V-Neck T-Shirt` zum Warenkorb hinzu. Wenn der Kunde mit der Auswahl zufrieden ist, wechselt er zur Kasse und reicht die Bestellung ein, wodurch folgender Eintrag in der Tabelle [Einfache Bestellung“ erstellt ](../data-warehouse-mgr/sales-flat-order-table.md):

| **`entity id`** | **`customer id**` | **`subtotal`** | **`created at`** |
|---|---|---|---|
| 227 | 214 | 94,85 | 23.09.2016 15:41:39 |

* `entity_id` : Dies ist der Primärschlüssel der `sales_flat_order`.
   * Als Sammy Customer diese Bestellung aufgab und die obige Zeile in die `sales_flat_order`-Tabelle geschrieben wurde, wurde die Bestellung `entity_id` = 227 zugewiesen.
* `customer_id` - Diese Spalte ist die eindeutige Kennung des Kunden, der diese bestimmte Bestellung aufgegeben hat
   * Der mit dieser Bestellung verknüpfte `customer_id` ist 214, was der `entity_id` von Sammy Customer auf der `customer_entity` ist.
* `subtotal` - Diese Spalte ist der Gesamtbetrag, der einem Kunden für die Bestellung in Rechnung gestellt wird
   * Die beiden Paare „Throwback Bellboths“ und „V-Neck T-Shirt“ kosteten insgesamt 94,85 Dollar
* `created_at` - Diese Spalte gibt den Zeitstempel für die Erstellung jeder Bestellung zurück

## `sales\_flat\_order\_item ( or Sales\_order\_item`

(wenn Sie Commerce 2.0 oder höher haben)

Wenn `Sammy Customer` die Bestellung übermitteln, wird zusätzlich zur einzelnen Zeile in der `Sales\_flat\_order` Tabelle eine Zeile für jedes eindeutige Element in dieser Reihenfolge in die [`sales\_flat\_order\_item` Tabelle eingefügt](../data-warehouse-mgr/sales-flat-order-item-table.md):

| **`item\_id`** | **`name`** | **`product\_id`** | **`order\_id`** | **`qty\_ordered`** | **`price`** |
|---|---|---|---|---|---|
| 822 | `Throwback Bellbottoms` | 205 | 227 | 2 | 39,95 |
| 823 | `V-Neck T-Shirt` | 207 | 227 | 1 | 14,95 |

* `item_id` - Diese Spalte ist der Primärschlüssel der `sales_flat_order_item`
   * Die Bestellung von `Sammy Customer` hat zwei Zeilen in dieser Tabelle erstellt, da die Bestellung zwei verschiedene Produkte enthielt
* `name` - Diese Spalte ist der Name des Produkts.
* `product_id` - Diese Spalte ist die eindeutige Kennung des Produkts, auf das sich diese Zeile bezieht
   * Die erste obige Zeile hat `product_id` = 205, da `Throwback Bellbottoms` in der `catalog_product_entity` Tabelle einen `entity_id` von 205 haben
* `order_id` - Diese Spalte ist die `entity_id` der Bestellung, die diese bestimmten Bestellelemente enthält.
   * Beide Zeilen oben haben `order_id` = 227, da sie beide Teil der von `Sammy Customer` aufgegebenen Reihenfolge sind, die in der `sales_flat_order`-Tabelle `entity_id` = 227 hat
* `qty_ordered` - Diese Spalte ist die Anzahl der Einheiten des Produkts, die in dieser spezifischen Reihenfolge enthalten sind
   * `Sammy Customer` Bestellung enthielt zwei `Throwback Bellbottoms`
* `price` - Diese Spalte ist der Preis einer einzelnen Einheit des Bestellartikels
   * Die `subtotal` aus `Sammy Customer` Bestellung in der `sales_flat_order` Tabelle war 94,85, was die Summe von zwei Paaren von `Throwback Bellbottoms` bei jeweils 39,95 US-Dollar und 1 `V-Neck T-Shirt` bei 14,95 US-Dollar ist.
