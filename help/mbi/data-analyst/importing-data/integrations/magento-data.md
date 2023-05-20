---
title: Erwartete Commerce-Daten
description: Wichtigste Datentabellen, die Commerce-Benutzer in Commerce Intelligence importieren
exl-id: b481c8fc-41b6-4094-8901-17d57f26bfc0
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Erwartet [!DNL Adobe Commerce] Daten

Nachdem Sie [mit [!DNL Adobe Commerce] store](../../../data-analyst/importing-data/integrations/magento.md)können Sie den Data Warehouse Manager verwenden, um relevante Datenfelder aus Ihrer Commerce-Datenbank einfach zur Analyse zu verfolgen.

Hier werden die wichtigsten Datentabellen untersucht, in die Commerce-Benutzer importieren. [!DNL Commerce Intelligence].

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Customers` | Die `customer\_entity` und die zugehörigen Tabellen beschreiben die Informationen, die den einzelnen *registrierter Kunde* in Ihrer Datenbank, wie E-Mail-Adresse und Registrierungsdatum. Mit diesen Informationen können Sie mit der Segmentierung nach Attributen und Kohorten auf Kundenebene beginnen. |
| `Orders` | Die `sales\_flat\_order` -Tabelle enthält alle Bestellungen, einschließlich der `created\_at` Zeitstempel, mit dem die Bestellung aufgegeben wurde, und `base\_grand\_total` -Feld, das den Umsatz zusammenfasst. Diese Felder bilden die Grundlage für Ihre Metriken auf Bestellebene. Wenn die Bestellung von einem *registrierter Kunde*, die `customer\_id` -Felderlinks zurück zu  `customer\_entity` -Tabelle, um eine Analyse des Kundenkaufverhaltens zu ermöglichen. |
| `Order items` | Die `sales\_flat\_order\_item` -Tabelle erfasst jedes Element, das zu einer Bestellung gehört. Dazu gehört die `price` und `qty\_ordered` und die `order\_id` -Feld, das eine Verbindung zum `sales\_flat\_order` Tabelle. Diese Tabelle bildet die Grundlage für Metriken wie `Item sold`und ermöglicht Ihnen die Segmentierung nach `product` und `product type`. |
| `Products` | Die `catalog\_product\_entity` -Tabelle speichert Informationen zu Attributen auf Produktebene wie Kategorie, Größe und Farbe. |
| `Categories` | Ihre Produkte gehören zu einer oder mehreren verschiedenen `product categories`, je nachdem, wie Ihr Commerce-Build eingerichtet ist. Die `catalog\_category\_entity` -Tabelle speichert die Hierarchie dieser Kategorien (z. B. Bekleidung > Tops > T-Shirts) und die `catalog\_category\_product` -Tabelle protokolliert die Verbindungen zwischen Ihren Produkten und diesen Kategorien. |

{style="table-layout:auto"}

## Verwandte

* [Verbinden [!DNL Adobe Commerce]](../integrations/magento.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
