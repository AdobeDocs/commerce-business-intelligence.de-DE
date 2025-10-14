---
title: Erwartete Spreedaten
description: Erkunden Sie die wichtigsten Datentabellen, die Sie von Spree in Ihr - [!DNL Commerce Intelligence]  importieren können.
exl-id: 203a2d4b-e7ad-4704-a3c1-8e22ff0bf2d6
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Erwartete [!DNL Spree]

Nachdem Sie [Ihren [!DNL Spree] Store](../../../data-analyst/importing-data/integrations/spree.md) verbunden haben, können Sie den [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder von Ihrer [!DNL Spree] zur Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Spree] in Ihr [!DNL Commerce Intelligence]-Konto importieren können, einschließlich Links zu [zusätzlichen &#x200B;](https://guides.spreecommerce.org/developer/addresses.html#address)) [!DNL Spree].

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Users` | Die `users` Tabelle enthält die Kontodetails für registrierte Kunden, einschließlich der E-Mail-Adresse, des Namens und des Registrierungsdatums der Person. Auf diese Weise können Sie verschiedene Kundensegmente und deren Kaufverhalten analysieren. |
| [`Orders`](https://guides.spreecommerce.org/developer/orders.html#overview) | Die `orders` Tabelle dient als Grundlage für alle Metriken auf Bestellebene. Hier werden alle Bestelldetails von Käufen aus Ihrem [!DNL Spree] gespeichert, einschließlich `completed\_at` (Zeitstempel der Bestellung), `user\_id` (ID des registrierten Benutzers, der die Bestellung aufgegeben hat). Wenn die Bestellung von einem registrierten Benutzer vorgenommen wurde, ist die `user\_id` mit der `users`-Tabelle verknüpft, um eine Analyse des Kaufverhaltens der Benutzer zu ermöglichen. |
| `Line items` | Die `line\_items` Tabelle ist ein untergeordnetes Element der `orders` Tabelle oder der `subscriptions`. Es werden die Positionsdetails einer Bestellung oder eines Abonnements aufgezeichnet. Für Bestellungen mit mehreren Produkten verfügt jedes Produkt über eine eigene Datenzeile in dieser Tabelle, einschließlich einer `product\_id`, mit der Sie es mit der `Products` verknüpfen können. |
| `Products` | Die `products` Tabelle enthält alle Produktdetails für einen verkaufsfähigen Artikel in Ihrem Spree-Katalog. Auf diese Weise können Sie Ihre Metriken auf Einzelpostenebene nach Produktattributen segmentieren. |
| `Subscriptions` | Wenn Sie über eine [!DNL Spree] Abonnementerweiterung verfügen, enthält die `subscriptions` die Informationen jedes einzelnen Abonnements, einschließlich `created\_at` (Startdatum), `cancelled\_at` (Datum, an dem ein Abonnement storniert wurde) und `interval` des Abonnements. |

{style="table-layout:auto"}

## Verwandt:

* [Verbinden [!DNL Spree]](../integrations/spree.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
