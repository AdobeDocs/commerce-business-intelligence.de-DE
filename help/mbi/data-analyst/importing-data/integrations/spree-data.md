---
title: Erwartete Ersatzdaten
description: Sehen Sie sich die Hauptdatentabellen an, die Sie von Spree in Ihr [!DNL Commerce Intelligence] Konto importieren können.
exl-id: 203a2d4b-e7ad-4704-a3c1-8e22ff0bf2d6
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Erwartete [!DNL Spree] Daten

Nachdem Sie [ mit Ihrem [!DNL Spree] store](../../../data-analyst/importing-data/integrations/spree.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder aus Ihrer [!DNL Spree]-Plattform einfach für die Analyse zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Spree] in Ihr [!DNL Commerce Intelligence] -Konto importieren können, einschließlich Links zu [zusätzlichen Dokumentationstabellen](https://guides.spreecommerce.org/developer/addresses.html#address) zu [!DNL Spree] -Daten.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| `Users` | Die Tabelle `users` enthält die Kontodetails für registrierte Kunden, einschließlich E-Mail-Adresse, Name und Registrierungsdatum des Kontakts. Auf diese Weise können Sie verschiedene Kundensegmente und deren Kaufverhalten analysieren. |
| [`Orders`](https://guides.spreecommerce.org/developer/orders.html#overview) | Die Tabelle `orders` dient als Grundlage für alle Metriken auf Bestellebene. Hier werden alle Bestelldetails von Käufen aus Ihrem [!DNL Spree]-Store aufgezeichnet, einschließlich `completed\_at` (Zeitstempel der Bestellung), `user\_id` (ID des registrierten Benutzers, der die Bestellung aufgegeben hat). Wenn die Bestellung von einem registrierten Benutzer getätigt wurde, verknüpft der `user\_id` wieder mit der Tabelle `users`, um eine Analyse des Kaufverhaltens der Benutzer zu ermöglichen. |
| `Line items` | Die Tabelle `line\_items` ist ein untergeordnetes Element der Tabelle `orders` oder der Tabelle `subscriptions`. Er zeichnet die Zeileneinträge einer Bestellung oder eines Abonnements auf. Bei Bestellungen mit mehreren Produkten verfügt jedes Produkt über eine eigene Datenzeile in dieser Tabelle, einschließlich einer `product\_id` , mit der Sie eine Verknüpfung mit der `Products` -Tabelle herstellen können. |
| `Products` | In der Tabelle `products` werden alle Produktdetails für ein verkäufliches Element in Ihrem Spree-Katalog aufgezeichnet. Auf diese Weise können Sie Ihre Metriken auf Zeileneinträgen nach Produktattributen segmentieren. |
| `Subscriptions` | Wenn Sie eine Abonnementerweiterung von [!DNL Spree] haben, enthält die Tabelle `subscriptions` die Informationen jedes einzelnen Abonnements, einschließlich `created\_at` (Startdatum), `cancelled\_at` (Datum, an dem ein Abonnement abgebrochen wurde) und der `interval` des Abonnements. |

{style="table-layout:auto"}

## Verwandte:

* [Verbinden [!DNL Spree]](../integrations/spree.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
