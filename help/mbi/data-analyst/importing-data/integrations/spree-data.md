---
title: Erwartete Spreedaten
description: Erkunden Sie die wichtigsten Datentabellen, die Sie von Spree in Ihr - [!DNL Commerce Intelligence]  importieren können.
exl-id: 203a2d4b-e7ad-4704-a3c1-8e22ff0bf2d6
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/DhJhNDqTEki-evyidC-9d08qq-XSDPRu1jJqG1lOijI
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 263
ht-degree: 0%

---

# Erwartete [!DNL Spree]

Nachdem Sie [Ihren [!DNL Spree] Store](../../../data-analyst/importing-data/integrations/spree.md) verbunden haben, können Sie den [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder von Ihrer [!DNL Spree] zur Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Spree] in Ihr [!DNL Commerce Intelligence]-Konto importieren können, einschließlich Links zu [zusätzlichen ](https://guides.spreecommerce.org/developer/addresses.html#address)) [!DNL Spree].

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
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
