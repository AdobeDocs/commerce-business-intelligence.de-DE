---
title: Allgemeine Commerce-Tabellen
description: Erfahren Sie mehr über einige der häufigsten Tabellen, die [!DNL MBI] -Kunden verwenden.
exl-id: 8b316130-55c6-4771-ae6e-97ac605fc6cc
source-git-commit: 9974cc5c5cf89829ca522ba620b8c0c2d509610c
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Allgemeine Commerce-Tabellen

Wenn Sie eine Commerce-Instanz zum ersten Mal mit [[!DNL MBI]](../importing-data/integrations/magento.md), [!DNL MBI] repliziert automatisch Daten aus einigen Ihrer Commerce-Tabellen (normalerweise 4 bis 6 Tabellen), um den anfänglichen Satz von Dashboards und Berichten zu konfigurieren. Dies ist zwar ein guter Ausgangspunkt, aber die meisten Store-Instanzen generieren zehnte, wenn nicht gar Hunderte zusätzlicher Tabellen, die wichtige Einblicke in die Leistung Ihres Unternehmens bieten können.

Nachfolgend finden Sie eine Liste der häufigsten Tabellen, die [!DNL MBI] -Kunden verwenden. Nach [Ihre Commerce-Instanz mit MBI verbinden](../../data-analyst/importing-data/integrations/magento.md), können Sie die [Data Warehouse Manager](../../data-analyst/data-warehouse-mgr/tour-dwm.md) , um relevante Datenfelder zu verfolgen.

| Tabellenname | Beschreibung |
|---|---|
| `catalog_category_entity` | Jede Zeile im `catalog_category_entity` -Tabelle beschreibt eine bestimmte Kategorie. Mit dem verknüpften `catalog_category_entity_varchar` und `catalog_category_product` Zuordnungstabelle können Sie Kategoriedaten für jedes Produkt abrufen. |
| `catalog_category_product` | Jede Zeile im `catalog_category_product` -Tabelle enthält eine Kombination aus einem Produkt und einer Kategorie. Daher kann ein bestimmtes Produkt mehrmals in verschiedenen Kategorien auf dieser Tabelle vorhanden sein, und eine bestimmte Kategorie kann auf dieser Tabelle mehrmals in Verbindung mit verschiedenen Produkten vorhanden sein. Diese Tabelle indiziert die `catalog_category_entity` -Tabelle (die Details auf Kategoriestufe enthält) und die `catalog_product_entity` -Tabelle (enthält Details auf Produktebene). |
| `catalog_product_entity` | Jede Zeile im `catalog_product_entity` -Tabelle steht für ein bestimmtes Produkt. Dies schließt ein, wenn das Produkt in Ihrem Commerce-Konto und seiner SKU erstellt wurde. |
| `customer_entity` | Jede Zeile im [`customer_entity`](../data-warehouse-mgr/cust-ent-table.md) -Tabelle stellt einen registrierten Benutzer auf Ihrer Website dar. Grundlegende Details auf Kundenebene wie das Registrierungsdatum und die E-Mail-Adresse werden in dieser Tabelle aufgeführt. |
| `quote` | Jede Zeile im [`quote`](../data-warehouse-mgr/sales-flat-quote-table.md) -Tabelle steht für einen Warenkorb, der im Checkout-Prozess erstellt wurde, unabhängig davon, ob dieser Warenkorb schließlich in eine Bestellung umgewandelt wurde oder nicht. Aufgrund der potenziellen Größe dieser Tabelle wird empfohlen, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind. |
| `quote_item` | Jede Zeile im [`quote_item`](../data-warehouse-mgr/sales-flat-quote-item-table.md) -Tabelle steht für ein einem Warenkorb hinzugefügtes Element, unabhängig davon, ob der Warenkorb schließlich in eine Bestellung umgewandelt wurde oder nicht. Aufgrund der potenziellen Größe dieser Tabelle wird empfohlen, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind. |
| `sales_order` | Jede Zeile im [`sales_order`](../data-warehouse-mgr/sales-flat-order-table.md) -Tabelle stellt eine auf Ihrer Site platzierte Bestellung dar. Diese Tabelle enthält Informationen auf Bestellebene wie das Datum der Bestellung, den Kunden, der die Bestellung aufgegeben hat, die Bestellsumme sowie die Verwendung von Rabatt- und Couponcode. |
| `sales_order_address` | Jede Zeile auf der `sales_order_address` -Tabelle enthält Versand- und Rechnungsinformationen für eine bestimmte Bestellung. Im `sales_order` -Tabelle, `billing_address_id` und `shipping_address_id` für eine bestimmte Bestellung eine bestimmte Zeile (identifiziert durch `entity_id`) im `sales_order_address` Tabelle. |
| `sales_order_item` | Jede Zeile im [`sales_order_item`](../data-warehouse-mgr/sales-flat-quote-item-table.md) -Tabelle ein bestimmtes Element aus einer bestimmten Reihenfolge identifiziert. Jede Zeile enthält Details wie das Produkt, die gekaufte Menge und die Reihenfolge, mit der der jeweilige Artikel verknüpft ist. |

{style=&quot;table-layout:auto&quot;}

## Verwandte Dokumentation

[Diagramme zur Entitätsbeziehung](../data-warehouse-mgr/entity-rel-diag.md)
