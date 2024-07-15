---
title: Erwartete Commerce-Daten
description: Wichtigste Datentabellen, die Commerce-Benutzer in Commerce Intelligence importieren
exl-id: b481c8fc-41b6-4094-8901-17d57f26bfc0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Erwartete [!DNL Adobe Commerce] Daten

Nachdem Sie [ mit Ihrem [!DNL Adobe Commerce] store](../../../data-analyst/importing-data/integrations/magento.md) verbunden haben, können Sie den Data Warehouse-Manager verwenden, um relevante Datenfelder aus Ihrer Commerce-Datenbank einfach für die Analyse zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Commerce-Benutzer in [!DNL Commerce Intelligence] importieren.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Customers` | Die Tabellen `customer\_entity` und zugehörige Informationen beschreiben die Informationen, die jedem *registrierten Kunden* in Ihrer Datenbank zugeordnet sind, z. B. seine E-Mail-Adresse und sein Registrierungsdatum. Mit diesen Informationen können Sie mit der Segmentierung nach Attributen und Kohorten auf Kundenebene beginnen. |
| `Orders` | Die Tabelle `sales\_flat\_order` zeichnet alle Bestellungen auf, einschließlich des `created\_at` Zeitstempels, in dem die Bestellung aufgegeben wurde, und des `base\_grand\_total` -Felds, in dem der Umsatz zusammengefasst wird. Diese Felder bilden die Grundlage für Ihre Metriken auf Bestellebene. Wenn die Bestellung von einem *registrierten Kunden* getätigt wurde, verknüpft das Feld `customer\_id` zurück mit der Tabelle `customer\_entity`, um eine Analyse des Kundenkaufverhaltens zu ermöglichen. |
| `Order items` | Die Tabelle `sales\_flat\_order\_item` zeichnet jedes Element auf, das zu einer Bestellung gehört. Dazu gehören die Felder `price` und `qty\_ordered` sowie das Feld `order\_id`, das eine Verbindung zur Tabelle `sales\_flat\_order` herstellt. Diese Tabelle bildet die Grundlage für Metriken wie `Item sold` und ermöglicht die Segmentierung nach `product` und `product type`. |
| `Products` | Die Tabelle `catalog\_product\_entity` speichert Informationen zu Attributen auf Produktebene wie Kategorie, Größe und Farbe. |
| `Categories` | Ihre Produkte gehören zu einem oder mehreren verschiedenen `product categories`, je nachdem, wie Ihr Commerce-Build eingerichtet ist. Die Tabelle `catalog\_category\_entity` speichert die Hierarchie dieser Kategorien (z. B. Bekleidung > Tops > T-Shirts) und die Tabelle `catalog\_category\_product` protokolliert die Verbindungen zwischen Ihren Produkten und diesen Kategorien. |

{style="table-layout:auto"}

## Verwandte

* [Verbinden [!DNL Adobe Commerce]](../integrations/magento.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
