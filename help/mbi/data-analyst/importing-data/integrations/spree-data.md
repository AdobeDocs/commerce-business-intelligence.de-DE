---
title: Erwartete Ersatzdaten
description: Die wichtigsten Datentabellen, die Sie aus Spree in Ihre [!DNL MBI] -Konto.
exl-id: 203a2d4b-e7ad-4704-a3c1-8e22ff0bf2d6
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Erwartet [!DNL Spree] data

Nachdem Sie [mit [!DNL Spree] store](../../../data-analyst/importing-data/integrations/spree.md), können Sie die [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) die einfache Verfolgung relevanter Datenfelder über Ihre [!DNL Spree] Plattform zur Analyse.

In diesem Artikel werden die wichtigsten Datentabellen untersucht, aus denen Sie importieren können. [!DNL Spree] in [!DNL MBI] -Konto, einschließlich Links zu [Zusätzliche Dokumentation](https://guides.spreecommerce.org/developer/addresses.html#address) about [!DNL Spree] Daten.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Users` | Die `users` enthält die Kontodetails für registrierte Kunden, einschließlich E-Mail, Name und Registrierungsdatum der Person. Auf diese Weise können Sie verschiedene Kundensegmente und deren Kaufverhalten analysieren. |
| [`Orders`](https://guides.spreecommerce.org/developer/orders.html#overview) | Die `orders` -Tabelle dient als Grundlage für alle Metriken auf Bestellebene. Hier aufgezeichnet sind alle Bestelldetails der Käufe von [!DNL Spree] Store, einschließlich `completed\_at` (Zeitstempel der Bestellung), `user\_id` (ID des registrierten Benutzers, der die Bestellung aufgegeben hat). Wenn die Bestellung von einem registrierten Benutzer getätigt wurde, wird die `user\_id` Links zurück zu `users` -Tabelle, um eine Analyse des Kaufverhaltens der Benutzer zu ermöglichen. |
| `Line items` | Die `line\_items` -Tabelle ist ein untergeordnetes Element der `orders` Tabelle oder `subscriptions`. Er zeichnet die Zeileneinträge einer Bestellung oder eines Abonnements auf. Für Bestellungen mit mehreren Produkten verfügt jedes Produkt über eine eigene Datenzeile in dieser Tabelle, einschließlich einer `product\_id` , mit der Sie ihn mit der `Products` Tabelle. |
| `Products` | Die `products` -Tabelle erfasst alle Produktdetails für einen verkäuflichen Artikel in Ihrem Spree-Katalog. Auf diese Weise können Sie Ihre Metriken auf Zeileneinträgen nach Produktattributen segmentieren. |
| `Subscriptions` | Wenn Sie [!DNL Spree] Abonnementerweiterung, die `subscriptions` -Tabelle enthält die Informationen jedes einzelnen Abonnements, einschließlich `created\_at` (Startdatum), `cancelled\_at` (Datum, an dem ein Abonnement abgebrochen wurde) und `interval` des Abonnements. |

{style="table-layout:auto"}

## Verwandte:

* [Verbinden [!DNL Spree]](../integrations/spree.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
