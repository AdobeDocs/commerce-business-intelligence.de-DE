---
title: sales_order_item table
description: Erfahren Sie, wie Sie mit der Tabelle sales_order_item arbeiten.
exl-id: 5c48e985-3ba2-414b-bd1f-555b3da763bd
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# `sales_order_item` Tabelle

Die Tabelle `sales_order_item` (`sales_flat_order_item` auf M1) enthält Datensätze aller Produkte, die in einer Bestellung gekauft wurden. Jede Zeile stellt einen eindeutigen `sku` dar, der in einer Reihenfolge enthalten ist. Die Menge der Einheiten, die für ein bestimmtes `sku` gekauft wurden, wird am häufigsten durch das Feld `qty_ordered` repräsentiert.

## Produkttypen

Die `sales_order_item` erfasst Details zu allen gekauften [Produktarten](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types). Eine gängige Praxis in [!DNL Adobe Commerce] besteht darin, konfigurierbare Produkte anzubieten, d. h. ein Produkt, das je nach Größe, Farbe und anderen Produktattributen angepasst werden kann. Ein konfigurierbares Produkt hat zwar seinen eigenen &quot;`sku`&quot;, kann jedoch mehrere einfache Produkte betreffen, bei denen jedes einfache Produkt eine eindeutige Produktkonfiguration darstellt. Weitere Informationen finden Sie unter [Konfigurieren von Produkten](https://developer.adobe.com/commerce/webapi/rest/tutorials/configurable-product/) .

Betrachten Sie beispielsweise ein konfigurierbares Produkt wie ein T-Shirt. Wenn ein Kunde auscheckt, wählt er Optionen aus, um Farbe und Größe zu ändern. Wenn der Kunde eine Farbe von `blue` und eine Größe von `small` auswählt, kauft er am Ende ein einfaches Produkt wie `t-shirt-blue-small`, das sich auf das übergeordnete Produkt von `t-shirt` bezieht.

Wenn ein konfigurierbares Produkt in einer Reihenfolge enthalten ist, werden in der Tabelle `sales_order_item` zwei Zeilen generiert: eine für die übergeordnete Zeile [simple](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-simple.html) `sku` und eine für die übergeordnete Tabelle [konfigurierbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html). Diese beiden Datensätze in der Tabelle `sales_order_item` können durch folgenden Join miteinander verknüpft werden:

* (einfach) `sales_order_item.parent_item_id` => (konfigurierbar) `sales_order_item.item_id`

Daher ist es möglich, auf einfacher oder konfigurierbarer Ebene über den Verkauf von Produkten zu berichten. Standardmäßig sind alle standardmäßigen `order-item-level` -Metriken in [!DNL Commerce Intelligence] so konfiguriert, dass die einfachen Produkte ausgeschlossen werden, und der Bericht *nur* für die konfigurierbaren Versionen. Dies wird durch den `Ordered products we count` -Filtersatz erreicht, der nach der Bedingung filtert, bei der `parent_item_id` `NULL` ist.

## Allgemeine Spalten

| **Spaltenname** | **Beschreibung** |
|----|----|
| `base_price` | Preis einer einzelnen Einheit eines Produkts zum Zeitpunkt des Verkaufs nach Anwendung von [Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) und bevor Steuern, Versand oder Warenkorbnachlässe angewendet werden. Dies wird in der Basiswährung des Stores dargestellt. |
| `created_at` | Erstellungszeitstempel des Bestellelements, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] konvertiert werden, die sich von Ihrer Zeitzone in der Datenbank unterscheidet. |
| `item_id` (PK) | Eindeutige Kennung für die Tabelle. |
| `name` | Textname des Bestellelements. |
| `order_id` | `Foreign key`, die mit der `sales_order`-Tabelle verknüpft ist. Verbinden Sie `sales_order.entity_id` , um die mit dem Bestellelement verknüpften Bestellattribute zu bestimmen. |
| `parent_item_id` | `Foreign key` , das ein einfaches Produkt mit seinem übergeordneten Bundle oder konfigurierbaren Produkt verknüpft. Treten Sie zu `sales_order_item.item_id` bei, um übergeordnete Produktattribute zu ermitteln, die mit einem einfachen Produkt verknüpft sind. Für übergeordnete Bestellelemente (d. h. Bundle oder konfigurierbare Produktarten) ist `parent_item_id` `NULL`. |
| `product_id` | `Foreign key`, die mit der `catalog_product_entity`-Tabelle verknüpft ist. Melden Sie sich bei `catalog_product_entity.entity_id` an, um die Produktattribute zu bestimmen, die mit dem Bestellelement verknüpft sind. |
| `product_type` | Typ des verkauften Produkts. Mögliche [Produktarten](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) sind: einfach, konfigurierbar, gruppiert, virtuell, gebündelt und herunterladbar. |
| `qty_ordered` | Menge der Einheiten, die zum Zeitpunkt des Verkaufs im Warenkorb für die jeweilige Bestellposition enthalten sind. |
| `sku` | Eindeutige Kennung für den gekauften Bestellartikel. |
| `store_id` | `Foreign key`, die mit der `store`-Tabelle verknüpft ist. Melden Sie sich bei `store.store_id` an, um zu bestimmen, welche Commerce Store-Ansicht mit dem Bestellelement verknüpft ist. |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's email` | E-Mail-Adresse des Bestellers. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `customer_email` zurückgegeben wird. |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `Customer's lifetime number of orders` zurückgegeben wird. |
| `Customer's lifetime revenue` | Summe des Umsatzes für alle Bestellungen dieses Kunden. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `Customer's lifetime revenue` zurückgegeben wird. |
| `Customer's order number` | Sequenzieller Bestellrang für die Bestellung dieses Kunden. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `Customer's order number` zurückgegeben wird. |
| `Order item total value (quantity * price)` | Gesamtwert eines Bestellartikels zum Zeitpunkt des Verkaufs nach Anwendung von [Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) und vor Anwendung von Steuern, Versand- oder Warenkorbrabatten. Wird durch Multiplizieren der `qty_ordered` mit der `base_price` berechnet. |
| `Order's coupon_code` | Auf die Bestellung angewendeter Coupon. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `coupon_code` zurückgegeben wird. |
| `Order's increment_id` | Eindeutige Kennung der Bestellung. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `increment_id` zurückgegeben wird. |
| `Order's status` | Status der Bestellung. Wird berechnet, indem `sales_order_item.order_id` mit `sales_order.entity_id` verbunden und das Feld `status` zurückgegeben wird. |
| `Store name` | Name des mit dem Bestellelement verknüpften Commerce-Stores. Wird berechnet, indem `sales_order_item.store_id` mit `store.store_id` verbunden und das Feld `name` zurückgegeben wird. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Konstruktion** |
|---|---|---|
| `Products ordered` | Die Gesamtmenge der zum Zeitpunkt des Verkaufs in den Warenkörben enthaltenen Erzeugnisse | `Operation: Sum`<br>`Operand: qty_ordered`<br>`Timestamp: created_at` |
| `Revenue by products ordered` | Gesamtwert der Produkte, die zum Zeitpunkt des Verkaufs im Warenkorb enthalten waren, nach Anwendung von Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen sowie vor Anwendung von Steuern, Versand- oder Warenkorbrabatten | `Operation: Sum`<br>`Operand: Order item total value (quantity * price)`<br>`Timestamp: created_at` |

{style="table-layout:auto"}

## `Foreign Key` Verbindungswege

`catalog_product_entity`

* Treten Sie der Tabelle `catalog_product_entity` bei, um Spalten zu erstellen, die Produktattribute zurückgeben, die mit dem Bestellelement verknüpft sind.
   * Pfad: `sales_order_item.product_id` (viele) => `catalog_product_entity.entity_id` (eins)

`sales_order`

* Treten Sie der Tabelle `sales_order` bei, um neue Spalten auf Bestellebene zu erstellen, die mit dem Bestellelement verknüpft sind.
   * Pfad: `sales_order_item.order_id` (viele) => `sales_order.entity_id` (eins)

`sales_order_item`

* Join to `sales_order_item` , um Spalten zu erstellen, die Details der übergeordneten konfigurierbaren oder Bundle-SKU mit dem einfachen Produkt verknüpfen. [Wenden Sie sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um Unterstützung bei der Konfiguration dieser Berechnungen zu erhalten, wenn Sie sie im Data Warehouse-Manager erstellen.
   * Pfad: `sales_order_item.parent_item_id` (viele) => `sales_order_item.item_id` (eins)

`store`

* Treten Sie der Tabelle `store` bei, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Bestellelement verknüpft ist.
   * Pfad: `sales_order_item.store_id` (viele) => `store.store_id` (eins)
