---
title: Allgemeine Commerce-Tabellen
description: Erfahren Sie mehr über einige der gebräuchlichsten Tabellen,  [!DNL Commerce Intelligence]  Kunden verwenden.
exl-id: 8b316130-55c6-4771-ae6e-97ac605fc6cc
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Allgemeine Commerce-Tabellen

Wenn Sie zum ersten Mal eine [!DNL Adobe Commerce] mit [[!DNL Adobe Commerce Intelligence]](../importing-data/integrations/magento.md) verbinden, repliziert [!DNL Commerce Intelligence] automatisch Daten aus einigen Ihrer Commerce-Tabellen (in der Regel 4-6 Tabellen), um den anfänglichen Satz von Dashboards und Berichten zu konfigurieren. Dies bietet zwar einen guten Ausgangspunkt, aber die meisten Store-Instanzen generieren Dutzende, wenn nicht Hunderte von zusätzlichen Tabellen, die wichtige Einblicke in die Leistung Ihres Unternehmens bieten können.

Nachfolgend finden Sie eine Liste einiger der häufigsten Tabellen, die [!DNL Commerce Intelligence] Kunden verwenden. Nachdem Sie [Ihre Commerce-Instanz mit Commerce Intelligence verbinden](../../data-analyst/importing-data/integrations/magento.md) können Sie den [Data Warehouse-Manager](../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder zu verfolgen.

| Tabellenname | Beschreibung |
|---|---|
| `catalog_category_entity` | Jede Zeile in der `catalog_category_entity` Tabelle beschreibt eine bestimmte Kategorie. Mit der zugehörigen `catalog_category_entity_varchar` und der `catalog_category_product` Zuordnungstabelle können Sie Kategorieinformationen für jedes Produkt abrufen. |
| `catalog_category_product` | Jede Zeile in der `catalog_category_product` Tabelle listet eine Kombination aus einem Produkt und einer Kategorie auf. Daher kann ein bestimmtes Produkt mehrmals mit verschiedenen Kategorien in dieser Tabelle vorhanden sein. Eine bestimmte Kategorie kann in dieser Tabelle mehrmals mit verschiedenen Produkten verknüpft sein. Diese Tabelle indiziert die `catalog_category_entity`-Tabelle (die Details auf Kategorieebene enthält) und die `catalog_product_entity`-Tabelle (die Details auf Produktebene enthält). |
| `catalog_product_entity` | Jede Zeile in der `catalog_product_entity` stellt ein bestimmtes Produkt dar. Dazu gehört auch der Zeitpunkt, zu dem dieses Produkt in Ihrem Commerce-Konto und seiner SKU erstellt wurde. |
| `customer_entity` | Jede Zeile in der [`customer_entity`](../data-warehouse-mgr/cust-ent-table.md) stellt einen registrierten Benutzer auf Ihrer Website dar. In dieser Tabelle sind grundlegende Details auf Kundenebene wie das Registrierungsdatum und die E-Mail-Adresse verfügbar. |
| `quote` | Jede Zeile in der [`quote`](../data-warehouse-mgr/sales-flat-quote-table.md) stellt einen Warenkorb dar, der beim Checkout-Prozess erstellt wurde, unabhängig davon, ob dieser Warenkorb schließlich in eine Bestellung konvertiert wurde. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind. |
| `quote_item` | Jede Zeile in der [`quote_item`](../data-warehouse-mgr/sales-flat-quote-item-table.md) stellt einen Artikel dar, der einem Warenkorb hinzugefügt wurde, unabhängig davon, ob der Warenkorb letztendlich in eine Bestellung konvertiert wurde. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind. |
| `sales_order` | Jede Zeile in der [`sales_order`](../data-warehouse-mgr/sales-flat-order-table.md) stellt eine auf Ihrer Site platzierte Reihenfolge dar. Diese Tabelle enthält Informationen auf Auftragsebene wie das Datum der Bestellung, den Kunden, der die Bestellung aufgegeben hat, die Bestellsumme sowie die Nutzung von Rabatt- und Couponcodes. |
| `sales_order_address` | Jede Zeile der `sales_order_address` enthält Versand- und Rechnungsinformationen für eine bestimmte Bestellung. In der `sales_order` Tabelle beziehen sich die `billing_address_id` und die `shipping_address_id` für eine bestimmte Reihenfolge auf eine bestimmte Zeile (durch `entity_id` gekennzeichnet) in der `sales_order_address`. |
| `sales_order_item` | Jede Zeile in der [`sales_order_item`](../data-warehouse-mgr/sales-flat-quote-item-table.md) Tabelle identifiziert ein bestimmtes Element aus einer bestimmten Reihenfolge. Jede Zeile enthält Details wie das Produkt, die gekaufte Menge und die Bestellung, mit der der angegebene Artikel verknüpft ist. |

{style="table-layout:auto"}

## Verwandte Dokumentation

[Entitätsbeziehungsdiagramme](../data-warehouse-mgr/entity-rel-diag.md)
