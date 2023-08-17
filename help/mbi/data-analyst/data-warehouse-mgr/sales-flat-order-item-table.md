---
title: sales_order_item table
description: Erfahren Sie, wie Sie mit der Tabelle sales_order_item arbeiten.
exl-id: 5c48e985-3ba2-414b-bd1f-555b3da763bd
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# `sales_order_item` Verzeichnis

Die `sales_order_item` table (`sales_flat_order_item` auf M1) enthält Aufzeichnungen aller Produkte, die bei einer Bestellung gekauft wurden. Jede Zeile stellt eine eindeutige `sku` in einer Bestellung enthalten ist. Die Menge der Einheiten, die für einen bestimmten `sku` wird am häufigsten durch `qty_ordered` -Feld.

## Produkttypen

Die `sales_order_item` erfasst Details zu allen [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) die gekauft wurden. Eine gängige Praxis in [!DNL Adobe Commerce] ist es, konfigurierbare Produkte anzubieten, d. h. ein Produkt, das entsprechend der Größe, Farbe und anderen Produktattributen angepasst werden kann. Ein konfigurierbares Produkt verfügt zwar über eine eigene `sku`, kann es sich auf mehrere einfache Produkte beziehen, bei denen jedes einfache Produkt eine eindeutige Produktkonfiguration darstellt. Siehe Abschnitt [Produkte konfigurieren](https://developer.adobe.com/commerce/webapi/rest/tutorials/configurable-product/) für weitere Informationen.

Betrachten Sie beispielsweise ein konfigurierbares Produkt wie ein T-Shirt. Wenn ein Kunde auscheckt, wählt er Optionen aus, um Farbe und Größe zu ändern. Wenn der Kunde eine Farbe von `blue`und eine Größe von `small`, kaufen sie am Ende ein einfaches Produkt wie `t-shirt-blue-small` die sich auf das übergeordnete Produkt von `t-shirt`.

Wenn ein konfigurierbares Produkt in einer Bestellung enthalten ist, werden im `sales_order_item` table: eine für die [einfach](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-simple.html) `sku` und eines für die [konfigurierbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html) übergeordnet. Diese beiden Datensätze im `sales_order_item` -Tabelle kann über den folgenden Join miteinander verbunden werden:

* (einfach) `sales_order_item.parent_item_id` => (konfigurierbar) `sales_order_item.item_id`

Daher ist es möglich, auf einfacher oder konfigurierbarer Ebene über den Verkauf von Produkten zu berichten. Standardmäßig sind alle Standardwerte `order-item-level` Metriken in [!DNL Commerce Intelligence] so konfiguriert sind, dass die einfachen Produkte ausgeschlossen werden, und *only* Berichte zu den konfigurierbaren Versionen erstellen. Dies wird durch das `Ordered products we count` Filtersatz, der nach der Bedingung filtert, bei der `parent_item_id` is `NULL`.

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|----|----|
| `base_price` | Preis einer einzelnen Einheit eines Erzeugnisses zum Zeitpunkt des Verkaufs nach [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) werden angewendet und bevor Steuern, Versand- oder Warenkorbrabatte angewendet werden. Dies wird in der Basiswährung des Stores dargestellt. |
| `created_at` | Erstellungszeitstempel des Bestellelements, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence], kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] , die sich von der Zeitzone Ihrer Datenbank unterscheidet. |
| `item_id` (PK) | Eindeutige Kennung für die Tabelle. |
| `name` | Textname des Bestellelements. |
| `order_id` | `Foreign key` mit `sales_order` Tabelle. Mitglied werden `sales_order.entity_id` um die mit dem Bestellelement verknüpften Bestellattribute zu bestimmen. |
| `parent_item_id` | `Foreign key` , das ein einfaches Produkt mit seinem übergeordneten Bundle oder konfigurierbaren Produkt verknüpft. Mitglied werden `sales_order_item.item_id` , um übergeordnete Produktattribute zu bestimmen, die mit einem einfachen Produkt verknüpft sind. Bei übergeordneten Bestellelementen (d. h. Bundle- oder konfigurierbaren Produktarten) muss die `parent_item_id` is `NULL`. |
| `product_id` | `Foreign key` mit `catalog_product_entity` Tabelle. Mitglied werden `catalog_product_entity.entity_id` , um Produktattribute zu bestimmen, die mit dem Bestellelement verknüpft sind. |
| `product_type` | Typ des verkauften Produkts. Potenzial [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) include: einfach, konfigurierbar, gruppiert, virtuell, gebündelt und herunterladbar. |
| `qty_ordered` | Menge der Einheiten, die zum Zeitpunkt des Verkaufs im Warenkorb für die jeweilige Bestellposition enthalten sind. |
| `sku` | Eindeutige Kennung für den gekauften Bestellartikel. |
| `store_id` | `Foreign key` mit `store` Tabelle. Mitglied werden `store.store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit dem Bestellelement verknüpft ist. |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's email` | E-Mail-Adresse des Bestellers. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `customer_email` -Feld. |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `Customer's lifetime number of orders` -Feld. |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle Bestellungen dieses Kunden. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `Customer's lifetime revenue` -Feld. |
| `Customer's order number` | Sequenzieller Bestellrang für die Bestellung dieses Kunden. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `Customer's order number` -Feld. |
| `Order item total value (quantity * price)` | Gesamtwert eines Bestellartikels zum Zeitpunkt des Verkaufs nach [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) werden angewendet und bevor Steuern, Versand- oder Warenkorbrabatte angewendet werden. Wird durch Multiplikation der `qty_ordered` durch die `base_price`. |
| `Order's coupon_code` | Auf die Bestellung angewendeter Coupon. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `coupon_code` -Feld. |
| `Order's increment_id` | Eindeutige Kennung der Bestellung. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `increment_id` -Feld. |
| `Order's status` | Status der Bestellung. Errechnet durch Verbinden `sales_order_item.order_id` nach `sales_order.entity_id` und gibt die `status` -Feld. |
| `Store name` | Name des mit dem Bestellelement verknüpften Commerce-Stores. Errechnet durch Verbinden `sales_order_item.store_id` nach `store.store_id` und gibt die `name` -Feld. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Products ordered` | Die Gesamtmenge der zum Zeitpunkt des Verkaufs in den Warenkörben enthaltenen Erzeugnisse | `Operation: Sum`<br>`Operand: qty_ordered`<br>`Timestamp: created_at` |
| `Revenue by products ordered` | Gesamtwert der Produkte, die zum Zeitpunkt des Verkaufs im Warenkorb enthalten waren, nach Anwendung von Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen sowie vor Anwendung von Steuern, Versand- oder Warenkorbrabatten | `Operation: Sum`<br>`Operand: Order item total value (quantity * price)`<br>`Timestamp: created_at` |

{style="table-layout:auto"}

## `Foreign Key` Verknüpfungspfade

`catalog_product_entity`

* Mitglied werden `catalog_product_entity` -Tabelle verwenden, um Spalten zu erstellen, die mit dem Bestellelement verknüpfte Produktattribute zurückgeben.
   * Pfad: `sales_order_item.product_id` (viele) => `catalog_product_entity.entity_id` (eins)

`sales_order`

* Mitglied werden `sales_order` , um neue mit dem Bestellelement verknüpfte Spalten auf Bestellebene zu erstellen.
   * Pfad: `sales_order_item.order_id` (viele) => `sales_order.entity_id` (eins)

`sales_order_item`

* Mitglied werden `sales_order_item` , um Spalten zu erstellen, die Details der übergeordneten konfigurierbaren oder Bundle-SKU mit dem einfachen Produkt verknüpfen. [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) für Hilfe bei der Konfiguration dieser Berechnungen, wenn sie im Data Warehouse-Manager erstellt werden.
   * Pfad: `sales_order_item.parent_item_id` (viele) => `sales_order_item.item_id` (eins)

`store`

* Mitglied werden `store` -Tabelle verwenden, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Bestellelement verknüpft ist.
   * Pfad: `sales_order_item.store_id` (viele) => `store.store_id` (eins)
