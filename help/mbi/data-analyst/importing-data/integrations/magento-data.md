---
title: Erwartete Commerce-Daten
description: Erkunden der wichtigsten Datentabellen, die Commerce-Benutzende in Commerce Intelligence importieren
exl-id: b481c8fc-41b6-4094-8901-17d57f26bfc0
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/D-GNfk1-kMscgF1xBKM5xG7wRV4IkIDh9wEBCMGb630
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 253
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
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
