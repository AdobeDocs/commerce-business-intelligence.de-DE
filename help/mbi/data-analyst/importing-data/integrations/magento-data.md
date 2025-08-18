---
title: Erwartete Commerce-Daten
description: Erkunden der wichtigsten Datentabellen, die Commerce-Benutzende in Commerce Intelligence importieren
exl-id: b481c8fc-41b6-4094-8901-17d57f26bfc0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Erwartete [!DNL Adobe Commerce]

Nachdem Sie [Ihren [!DNL Adobe Commerce] Store](../../../data-analyst/importing-data/integrations/magento.md) verbunden haben, können Sie mit dem Data Warehouse-Manager relevante Datenfelder aus Ihrer Commerce-Datenbank einfach zur Analyse verfolgen.

In diesem Abschnitt werden die wichtigsten Datentabellen untersucht, die Commerce-Benutzende in [!DNL Commerce Intelligence] importieren.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Customers` | Die `customer\_entity` und zugehörigen Tabellen beschreiben die Informationen, die mit jedem *registrierten Kunden* in Ihrer Datenbank verbunden sind, z. B. seine E-Mail-Adresse und das Registrierungsdatum. Mit diesen Informationen können Sie mit der Segmentierung nach Attributen und Kohorten auf Kundenebene beginnen. |
| `Orders` | In der `sales\_flat\_order` Tabelle werden alle Bestellungen aufgezeichnet, einschließlich des `created\_at` Zeitstempels, an dem die Bestellung aufgegeben wurde, und des `base\_grand\_total` Felds, das den Umsatz zusammenfasst. Diese Felder sind die Grundlage für Metriken auf Bestellebene. Wenn die Bestellung von einem *registrierten Kunden* getätigt wurde, wird das Feld `customer\_id` wieder mit der `customer\_entity` verknüpft, um eine Analyse des Kaufverhaltens von Kunden zu ermöglichen. |
| `Order items` | In der `sales\_flat\_order\_item` Tabelle werden alle Elemente aufgezeichnet, die zu einer Bestellung gehören. Dazu gehören die Felder `price` und `qty\_ordered` sowie das Feld `order\_id` , das eine Verbindung zur `sales\_flat\_order` herstellt. Diese Tabelle bildet die Grundlage für Metriken wie `Item sold` und ermöglicht die Segmentierung nach `product` und `product type`. |
| `Products` | Die `catalog\_product\_entity` speichert Informationen zu Attributen auf Produktebene, wie Kategorie, Größe und Farbe. |
| `Categories` | Ihre Produkte gehören zu einem oder mehreren verschiedenen `product categories`, je nachdem, wie Ihr Commerce-Build eingerichtet wurde. Die `catalog\_category\_entity` Tabelle speichert die Hierarchie dieser Kategorien (z. B. Bekleidung > Oberteile > T-Shirts), und die `catalog\_category\_product` Tabelle protokolliert die Verbindungen zwischen Ihren Produkten und diesen Kategorien. |

{style="table-layout:auto"}

## verwandt

* [Verbinden [!DNL Adobe Commerce]](../integrations/magento.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
