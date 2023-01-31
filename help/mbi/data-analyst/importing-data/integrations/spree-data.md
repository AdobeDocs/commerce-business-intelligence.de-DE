---
title: Erwartete Ersatzdaten
description: Die wichtigsten Datentabellen, die Sie aus Spree in Ihre [!DNL MBI] -Konto.
exl-id: 203a2d4b-e7ad-4704-a3c1-8e22ff0bf2d6
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Erwartet [!DNL Spree] data

Nachdem Sie [mit [!DNL Spree] store](../../../data-analyst/importing-data/integrations/spree.md), können Sie die [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) die einfache Verfolgung relevanter Datenfelder über Ihre [!DNL Spree] Plattform zur Analyse.

In diesem Artikel untersuchen wir die wichtigsten Datentabellen, aus denen Sie importieren können [!DNL Spree] in [!DNL MBI] -Konto, einschließlich Links zu [Zusätzliche Dokumentation](https://guides.spreecommerce.org/developer/addresses.html#address) about [!DNL Spree] Daten.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Users` | Die `users` enthält die Kontodetails für registrierte Kunden, einschließlich E-Mail, Name und Registrierungsdatum der Person. Auf diese Weise können Sie verschiedene Kundensegmente und deren Kaufverhalten analysieren. |
| [`Orders`](https://guides.spreecommerce.org/developer/orders.html#overview) | Die `orders` -Tabelle dient als Grundlage für alle Metriken auf Bestellebene. Hier aufgezeichnet sind alle Bestelldetails der Käufe von [!DNL Spree] Store, einschließlich `completed\_at` (Zeitstempel der Bestellung), `user\_id` (ID des registrierten Benutzers, der die Bestellung aufgegeben hat). Wenn die Bestellung von einem registrierten Benutzer getätigt wurde, wird die `user\_id` verknüpft zurück zu `users` -Tabelle, um eine Analyse des Kaufverhaltens der Benutzer zu ermöglichen. |
| `Line items` | Die `line\_items` -Tabelle ist ein untergeordnetes Element der `orders` Tabelle oder `subscriptions`. Er zeichnet die Zeileneinträge einer Bestellung oder eines Abonnements auf. Bei Bestellungen mit mehreren Produkten enthält jedes Produkt eine eigene Datenzeile in dieser Tabelle, einschließlich einer `product\_id` , mit der Sie ihn mit der `Products` Tabelle. |
| [`Products`](https://guides.spreecommerce.com/developer/products.html#overview) | Die `products` -Tabelle erfasst alle Produktdetails für einen verkäuflichen Artikel in Ihrem Spree-Katalog. Auf diese Weise können Sie Ihre Metriken auf Zeileneinträgen nach Produktattributen segmentieren. |
| `Subscriptions` | Wenn Sie [!DNL Spree] Abonnementerweiterung, die `subscriptions` -Tabelle enthält die Informationen jedes einzelnen Abonnements, einschließlich `created\_at` (Startdatum), `cancelled\_at` (Datum, an dem ein Abonnement abgebrochen wurde) und `interval` des Abonnements. |

{style=&quot;table-layout:auto&quot;}

## Verwandte:

* [Verbinden [!DNL Spree]](../integrations/spree.md)
* [Erneutes Authentifizieren von Integrationen](https://support.magento.com/hc/en-us/articles/360016733151)
