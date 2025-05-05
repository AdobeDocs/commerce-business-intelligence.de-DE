---
title: Tabelle sales_order_item
description: Erfahren Sie, wie Sie mit der Tabelle sales_order_item arbeiten.
exl-id: 5c48e985-3ba2-414b-bd1f-555b3da763bd
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# `sales_order_item`

Die `sales_order_item` Tabelle (`sales_flat_order_item` auf M1) enthält Datensätze zu allen Produkten, die in einer Bestellung gekauft wurden. Jede Zeile stellt eine eindeutige `sku` dar, die in einer Bestellung enthalten ist. Die Menge der Einheiten, die für eine bestimmte `sku` gekauft wurden, wird am häufigsten durch das Feld `qty_ordered` dargestellt.

## Produktarten

Die `sales_order_item` erfasst Details zu allen [Produktarten](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html?lang=de#product-types) die gekauft wurden. Eine gängige Praxis in [!DNL Adobe Commerce] besteht darin, konfigurierbare Produkte anzubieten, d. h. ein Produkt, das anhand von Größe, Farbe und anderen Produktattributen angepasst werden kann. Obwohl ein konfigurierbares Produkt über eine eigene `sku` verfügt, kann es sich auf mehrere einfache Produkte beziehen, wobei jedes einfache Produkt eine eindeutige Produktkonfiguration darstellt. Weitere Informationen finden [ unter &quot;](https://developer.adobe.com/commerce/webapi/rest/tutorials/configurable-product/) konfigurieren“.

Betrachten Sie beispielsweise ein konfigurierbares Produkt wie ein T-Shirt. Beim Auschecken wählt der Kunde Optionen aus, um die Farbe und Größe zu ändern. Wenn der Kunde eine Farbe für `blue` und eine Größe für `small` auswählt, kauft er am Ende ein einfaches Produkt wie `t-shirt-blue-small`, das sich auf das übergeordnete Produkt von `t-shirt` bezieht.

Wenn ein konfigurierbares Produkt in einer Bestellung enthalten ist, werden zwei Zeilen in der `sales_order_item` generiert: eine für die [einfache](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-simple.html?lang=de) `sku` und eine für das [konfigurierbare](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html?lang=de) übergeordnete Element. Diese beiden Datensätze in der `sales_order_item` Tabelle können über den folgenden Join miteinander verknüpft werden:

* (einfach) `sales_order_item.parent_item_id` => (konfigurierbar) `sales_order_item.item_id`

Daher ist es möglich, den Verkauf von Produkten entweder auf der einfachen Ebene oder auf der konfigurierbaren Ebene zu melden. Standardmäßig sind alle standardmäßigen `order-item-level` in [!DNL Commerce Intelligence] so konfiguriert, dass die einfachen Produkte ausgeschlossen werden und *nur* Berichte über die konfigurierbaren Versionen erstellt. Dies wird durch den `Ordered products we count` Filtersatz erreicht, der nach der Bedingung filtert, in der `parent_item_id` `NULL` ist.

## Gemeinsame Spalten

| **Spaltenname** | **Beschreibung** |
|----|----|
| `base_price` | Der Preis einer einzelnen Einheit eines Produkts zum Zeitpunkt des Verkaufs wird nach [Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=de) angewendet und bevor Steuern, Versand oder Warenkorb-Rabatte angewendet werden. Dies wird in der Basiswährung des Stores dargestellt. |
| `created_at` | Erstellungszeitstempel des Bestellelements, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Reporting-Zeitzone umgewandelt werden, [!DNL Commerce Intelligence] sich von Ihrer Datenbank-Zeitzone unterscheidet. |
| `item_id` (K) | Eindeutige Kennung für die Tabelle. |
| `name` | Textname des Bestellartikels. |
| `order_id` | Der `sales_order` Tabelle zugeordnete `Foreign key` Mit `sales_order.entity_id` verbinden, um die mit dem Auftragselement verknüpften Auftragsattribute zu bestimmen. |
| `parent_item_id` | `Foreign key`, das ein einfaches Produkt auf sein übergeordnetes Bundle oder konfigurierbares Produkt bezieht. Join-`sales_order_item.item_id`, um übergeordnete Produktattribute zu bestimmen, die mit einem einfachen Produkt verknüpft sind. Bei übergeordneten Bestellartikeln (d. h. Bundle oder konfigurierbare Produkttypen) wird die `parent_item_id` `NULL`. |
| `product_id` | Der `catalog_product_entity` Tabelle zugeordnete `Foreign key` Mit `catalog_product_entity.entity_id` verbinden, um Produktattribute zu bestimmen, die mit dem Auftragselement verknüpft sind. |
| `product_type` | Typ des verkauften Produkts. Mögliche [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html?lang=de#product-types) sind: einfach, konfigurierbar, gruppiert, virtuell, gebündelt und herunterladbar. |
| `qty_ordered` | Menge der Einheiten, die zum Zeitpunkt des Verkaufs für den jeweiligen Bestellartikel im Warenkorb enthalten sind. |
| `sku` | Eindeutige Kennung für den gekauften Bestellartikel. |
| `store_id` | Der `store` Tabelle zugeordnete `Foreign key` Mit `store.store_id` verbinden, um zu bestimmen, welche Commerce-Store-Ansicht mit dem Bestellartikel verknüpft ist. |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Customer's email` | E-Mail-Adresse des Bestellers. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `customer_email`. |
| `Customer's lifetime number of orders` | Gesamtzahl der von diesem Kunden aufgegebenen Bestellungen. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `Customer's lifetime number of orders`. |
| `Customer's lifetime revenue` | Summe des Gesamtumsatzes für alle Bestellungen dieses Kunden. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `Customer's lifetime revenue`. |
| `Customer's order number` | Sequenzieller Auftragsrang für die Bestellung dieses Kunden. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `Customer's order number`. |
| `Order item total value (quantity * price)` | Der Gesamtwert eines Bestellartikels zum Zeitpunkt des Verkaufs nach Anwendung [Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=de) und vor Anwendung von Steuern, Versand- oder Warenkorbabschlägen. Berechnet durch Multiplizieren des `qty_ordered` mit dem `base_price`. |
| `Order's coupon_code` | Auf die Bestellung angewendeter Coupon. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `coupon_code`. |
| `Order's increment_id` | Eindeutige Kennung der Bestellung. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `increment_id`. |
| `Order's status` | Status der Bestellung. Berechnet durch Verbinden von `sales_order_item.order_id` mit `sales_order.entity_id` und Zurückgeben des `status`. |
| `Store name` | Name des Commerce-Stores, der mit dem Auftragselement verknüpft ist. Berechnet durch Verbinden von `sales_order_item.store_id` mit `store.store_id` und Zurückgeben des `name`. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Products ordered` | Die Gesamtmenge der Produkte, die zum Zeitpunkt des Verkaufs in den Warenkorb gelegt wurden | `Operation: Sum`<br>`Operand: qty_ordered`<br>`Timestamp: created_at` |
| `Revenue by products ordered` | Gesamtwert der in den Warenkörben enthaltenen Produkte zum Zeitpunkt des Verkaufs nach Anwendung der Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen und vor Anwendung von Steuern, Versand oder Warenkorbabschlägen | `Operation: Sum`<br>`Operand: Order item total value (quantity * price)`<br>`Timestamp: created_at` |

{style="table-layout:auto"}

## `Foreign Key` von Verbindungswegen

`catalog_product_entity`

* Mit `catalog_product_entity` Tabelle verbinden, um Spalten zu erstellen, die dem Auftragselement zugeordnete Produktattribute zurückgeben.
   * Pfad: `sales_order_item.product_id` (viele) => `catalog_product_entity.entity_id` (eins)

`sales_order`

* Mit `sales_order` Tabelle verbinden, um neue Spalten auf Auftragsebene zu erstellen, die mit dem Auftragselement verknüpft sind.
   * Pfad: `sales_order_item.order_id` (viele) => `sales_order.entity_id` (eins)

`sales_order_item`

* Verbinden Sie sich mit `sales_order_item` , um Spalten zu erstellen, die Details der übergeordneten konfigurierbaren oder Bundle-SKU mit dem einfachen Produkt verknüpfen. [Wenden Sie sich an den ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de), um Unterstützung bei der Konfiguration dieser Berechnungen zu erhalten, falls Sie im Data Warehouse-Manager erstellen.
   * Pfad: `sales_order_item.parent_item_id` (viele) => `sales_order_item.item_id` (eins)

`store`

* Mit `store` Tabelle verbinden, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Bestellelement verknüpft ist.
   * Pfad: `sales_order_item.store_id` (viele) => `store.store_id` (eins)
