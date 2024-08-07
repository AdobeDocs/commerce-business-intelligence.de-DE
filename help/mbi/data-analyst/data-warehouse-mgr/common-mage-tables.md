---
title: Allgemeine Commerce-Tabellen
description: Erfahren Sie mehr über einige der gängigeren Tabellen, die [!DNL Commerce Intelligence] Kunden verwenden.
exl-id: 8b316130-55c6-4771-ae6e-97ac605fc6cc
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Allgemeine Commerce-Tabellen

Wenn Sie eine [!DNL Adobe Commerce] -Instanz zum ersten Mal mit [[!DNL Adobe Commerce Intelligence]](../importing-data/integrations/magento.md) verbinden, repliziert [!DNL Commerce Intelligence] automatisch Daten aus einigen Ihrer Commerce-Tabellen (normalerweise 4 bis 6 Tabellen), um den anfänglichen Satz von Dashboards und Berichten zu konfigurieren. Dies ist zwar ein guter Ausgangspunkt, aber die meisten Store-Instanzen generieren zehnte, wenn nicht gar Hunderte zusätzlicher Tabellen, die wichtige Einblicke in die Leistung Ihres Unternehmens bieten können.

Nachstehend finden Sie eine Liste der gängigeren Tabellen, die von Kunden mit [!DNL Commerce Intelligence] verwendet werden. Nachdem Sie [Ihre Commerce-Instanz mit Commerce Intelligence](../../data-analyst/importing-data/integrations/magento.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder zu verfolgen.

| Tabellenname | Beschreibung |
|---|---|
| `catalog_category_entity` | Jede Zeile in der Tabelle `catalog_category_entity` beschreibt eine bestimmte Kategorie. Mit der zugehörigen Tabelle `catalog_category_entity_varchar` und der Tabelle `catalog_category_product` für die Zuordnung können Sie Kategoriedaten für jedes Produkt abrufen. |
| `catalog_category_product` | Jede Zeile in der Tabelle `catalog_category_product` listet eine Kombination aus einem Produkt und einer Kategorie auf. Daher kann ein bestimmtes Produkt mehrmals in verschiedenen Kategorien auf dieser Tabelle vorhanden sein, und eine bestimmte Kategorie kann auf dieser Tabelle mehrmals in Verbindung mit verschiedenen Produkten vorhanden sein. Diese Tabelle indiziert die `catalog_category_entity` -Tabelle (die Details auf Kategorieebene enthält) und die `catalog_product_entity` -Tabelle (die Details auf Produktebene enthält). |
| `catalog_product_entity` | Jede Zeile in der Tabelle `catalog_product_entity` stellt ein bestimmtes Produkt dar. Dies schließt ein, wenn das Produkt in Ihrem Commerce-Konto und seiner SKU erstellt wurde. |
| `customer_entity` | Jede Zeile in der Tabelle [`customer_entity`](../data-warehouse-mgr/cust-ent-table.md) stellt einen registrierten Benutzer auf Ihrer Website dar. Grundlegende Details auf Kundenebene wie das Registrierungsdatum und die E-Mail-Adresse werden in dieser Tabelle aufgeführt. |
| `quote` | Jede Zeile in der Tabelle [`quote`](../data-warehouse-mgr/sales-flat-quote-table.md) stellt einen Warenkorb dar, der im Checkout-Prozess erstellt wurde, unabhängig davon, ob dieser Warenkorb schließlich in eine Bestellung umgewandelt wurde. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind. |
| `quote_item` | Jede Zeile in der Tabelle &quot;[`quote_item`](../data-warehouse-mgr/sales-flat-quote-item-table.md)&quot; stellt ein einem Warenkorb hinzugefügtes Element dar, unabhängig davon, ob der Warenkorb schließlich in eine Bestellung umgewandelt wurde. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind. |
| `sales_order` | Jede Zeile in der Tabelle [`sales_order`](../data-warehouse-mgr/sales-flat-order-table.md) stellt eine Reihenfolge dar, die auf Ihrer Site platziert wird. Diese Tabelle enthält Informationen auf Bestellebene wie das Datum der Bestellung, den Kunden, der die Bestellung aufgegeben hat, die Bestellsumme sowie die Verwendung von Rabatt- und Couponcode. |
| `sales_order_address` | Jede Zeile der Tabelle `sales_order_address` enthält Versand- und Rechnungsinformationen für eine bestimmte Bestellung. Auf der Tabelle `sales_order` beziehen sich die `billing_address_id` und die `shipping_address_id` für eine bestimmte Reihenfolge auf eine bestimmte Zeile (identifiziert durch `entity_id`) in der Tabelle `sales_order_address`. |
| `sales_order_item` | Jede Zeile in der Tabelle [`sales_order_item`](../data-warehouse-mgr/sales-flat-quote-item-table.md) identifiziert ein bestimmtes Element aus einer bestimmten Reihenfolge. Jede Zeile enthält Details wie das Produkt, die gekaufte Menge und die Reihenfolge, mit der der jeweilige Artikel verknüpft ist. |

{style="table-layout:auto"}

## Verwandte Dokumentation

[Diagramme zur Entitätsbeziehung](../data-warehouse-mgr/entity-rel-diag.md)
