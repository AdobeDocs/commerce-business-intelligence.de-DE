---
title: sales_order_item table
description: Erfahren Sie, wie Sie mit der Tabelle sales_order_item arbeiten.
exl-id: 5c48e985-3ba2-414b-bd1f-555b3da763bd
source-git-commit: 9974cc5c5cf89829ca522ba620b8c0c2d509610c
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# `sales_order_item` Verzeichnis

Die `sales_order_item` table (`sales_flat_order_item` auf M1 1) enthält Aufzeichnungen aller Produkte, die bei einer Bestellung gekauft wurden. Jede Zeile stellt eine eindeutige `sku` in einer Bestellung enthalten ist. Die Menge der Einheiten, die für einen bestimmten `sku` wird am häufigsten durch `qty_ordered` -Feld.

## Produkttypen

Die `sales_order_item` erfasst Details zu allen [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) die gekauft wurden. Eine gängige Praxis in Commerce besteht darin, konfigurierbare Produkte anzubieten, d. h. ein Produkt, das je nach Größe, Farbe und anderen Produktattributen angepasst werden kann. Ein konfigurierbares Produkt verfügt zwar über eine eigene `sku`, kann es sich auf mehrere einfache Produkte beziehen, bei denen jedes einfache Produkt eine eindeutige Produktkonfiguration darstellt. Siehe [Produkte konfigurieren](https://developer.adobe.com/commerce/webapi/rest/tutorials/configurable-product/) für weitere Informationen.

Betrachten Sie beispielsweise ein konfigurierbares Produkt wie ein T-Shirt. Wenn ein Kunde auscheckt, wählt er Optionen aus, um Farbe und Größe zu ändern. Wenn der Kunde eine Farbe von `blue`und eine Größe von `small`, kaufen sie am Ende ein einfaches Produkt wie `t-shirt-blue-small` die sich auf das übergeordnete Produkt von `t-shirt`.

Wenn ein konfigurierbares Produkt in einer Bestellung enthalten ist, werden im `sales_order_item` table: einer für [einfach](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-simple.html) `sku`und einer für die [konfigurierbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html) übergeordnet. Diese beiden Datensätze im `sales_order_item` -Tabelle kann über den folgenden Join miteinander verbunden werden:

* (einfach) `sales_order_item.parent_item_id` => (konfigurierbar) `sales_order_item.item_id`

Daher ist es möglich, über den Verkauf von Produkten entweder auf einfacher Ebene oder auf konfigurierbarer Ebene zu berichten. Standardmäßig sind alle Standardwerte `order-item-level` Metriken in [!DNL MBI] so konfiguriert sind, dass die einfachen Produkte ausgeschlossen werden, und *only* Berichte zu den konfigurierbaren Versionen erstellen. Dies wird durch das `Ordered products we count` Filtersatz, der nach der Bedingung filtert, bei der `parent_item_id` is `NULL`.

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|----|----|
| `base_price` | Preis einer einzelnen Einheit eines Erzeugnisses zum Zeitpunkt des Verkaufs nach [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) vor Anwendung von Steuern, Versand- oder Warenkorbrabatten in der Basiswährung des Stores |
| `created_at` | Erstellungszeitstempel des Bestellelements, der normalerweise lokal in UTC gespeichert wird. Abhängig von Ihrer Konfiguration in [!DNL MBI], kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL MBI] , die sich von der Zeitzone Ihrer Datenbank unterscheidet |
| `item_id` (PK) | Eindeutige Kennung für die Tabelle |
| `name` | Textname des Bestellelements |
| `order_id` | `Foreign key` mit `sales_order` Tabelle. Mitglied werden `sales_order.entity_id` zur Bestimmung der mit dem Bestellelement verknüpften Bestellattribute |
| `parent_item_id` | `Foreign key` , das ein einfaches Produkt mit seinem übergeordneten Bundle oder konfigurierbaren Produkt verknüpft. Mitglied werden `sales_order_item.item_id` , um übergeordnete Produktattribute zu bestimmen, die mit einem einfachen Produkt verknüpft sind. Bei übergeordneten Bestellelementen (d. h. Bundle- oder konfigurierbaren Produktarten) muss die `parent_item_id` wird `NULL` |
| `product_id` | `Foreign key` mit `catalog_product_entity` Tabelle. Mitglied werden `catalog_product_entity.entity_id` zur Bestimmung der Produktattribute, die mit dem Bestellelement verknüpft sind |
| `product_type` | Typ des verkauften Produkts. Potenzial [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) include: einfach, konfigurierbar, gruppiert, virtuell, gebündelt und herunterladbar |
| `qty_ordered` | Menge der zum Zeitpunkt des Verkaufs im Warenkorb für die jeweilige Bestellung enthaltenen Einheiten |
| `sku` | Eindeutige Kennung für den gekauften Bestellartikel |
| `store_id` | `Foreign key` mit `store` Tabelle. Mitglied werden `store.store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit dem Bestellelement verknüpft ist |

{style=&quot;table-layout:auto&quot;}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's email` | E-Mail-Adresse des Kunden, der die Bestellung aufgibt. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `customer_email` field |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `Customer's lifetime number of orders` field |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle von diesem Kunden aufgegebenen Bestellungen. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `Customer's lifetime revenue` field |
| `Customer's order number` | Sequenzieller Bestellrang für die Bestellung dieses Kunden. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `Customer's order number` field |
| `Order item total value (quantity * price)` | Gesamtwert eines Bestellartikels zum Zeitpunkt des Verkaufs nach [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) werden angewendet und bevor Steuern, Versand- oder Warenkorbrabatte angewendet werden. Wird durch Multiplikation der `qty_ordered` durch `base_price` |
| `Order's coupon_code` | Auf die Bestellung angewendeter Coupon. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `coupon_code` field |
| `Order's increment_id` | Eindeutige Kennung der Bestellung. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `increment_id` field |
| `Order's status` | Status der Bestellung. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und die `status` field |
| `Store name` | Name des Commerce-Stores, der mit dem Bestellelement verknüpft ist. Errechnet durch Verbinden `sales_order_item.store_id` nach `store.store_id` und die `name` field |

{style=&quot;table-layout:auto&quot;}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Products ordered` | Die Gesamtmenge der zum Zeitpunkt des Verkaufs in den Warenkörben enthaltenen Erzeugnisse | `Operation: Sum`<br>`Operand: qty_ordered`<br>`Timestamp: created_at` |
| `Revenue by products ordered` | Gesamtwert der Produkte, die zum Zeitpunkt des Verkaufs im Warenkorb enthalten waren, nach Anwendung von Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen sowie vor Anwendung von Steuern, Versand- oder Warenkorbrabatten | `Operation: Sum`<br>`Operand: Order item total value (quantity * price)`<br>`Timestamp: created_at` |

{style=&quot;table-layout:auto&quot;}

## `Foreign Key` Verknüpfungspfade

`catalog_product_entity`

* Mitglied werden `catalog_product_entity` , um neue Spalten zu erstellen, die Produktattribute zurückgeben, die mit dem Bestellelement verknüpft sind.
   * Pfad: `sales_order_item.product_id` (viele) => `catalog_product_entity.entity_id` (eins)

`sales_order`

* Mitglied werden `sales_order` , um neue mit dem Bestellelement verknüpfte Spalten auf Bestellebene zu erstellen.
   * Pfad: `sales_order_item.order_id` (viele) => `sales_order.entity_id` (eins)

`sales_order_item`

* Mitglied werden `sales_order_item` , um neue Spalten zu erstellen, die Details der übergeordneten konfigurierbaren oder Bundle-SKU mit dem einfachen Produkt verknüpfen. Beachten Sie, dass Sie [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en) Hilfe bei der Konfiguration dieser Berechnungen, wenn sie im Data Warehousen-Manager erstellt werden.
   * Pfad: `sales_order_item.parent_item_id` (viele) => `sales_order_item.item_id` (eins)

`store`

* Mitglied werden `store` , um neue Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Bestellelement verknüpft ist.
   * Pfad: `sales_order_item.store_id` (viele) => `store.store_id` (eins)
