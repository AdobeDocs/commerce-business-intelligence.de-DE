---
title: Erwartete Stripe-Daten
description: Erkunden Sie die wichtigsten Datentabellen, die Sie aus Stripe in Commerce Intelligence importieren können.
exl-id: 694577b2-48f9-4376-850d-acae1776afe3
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/dCiDusso9q9gvZOXKeHcDcuVK-jCXkqR3pQg6eTKzdo
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
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
source-wordcount: 323
ht-degree: 0%

---

# Erwartete [!DNL Stripe]

Nachdem [Sie Ihr [!DNL Stripe] Konto verbunden haben](../integrations/stripe.md) können Sie den [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Stripe] in [!DNL Commerce Intelligence] importieren können. Nach Abschluss des Setups werden die folgenden Tabellen in Ihrer Data Warehouse erstellt. Klicken Sie auf die Links in der Spalte „Tabellenname“, um mehr über die Attribute in den einzelnen Tabellen zu erfahren.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`Customers`](https://stripe.com/docs/sources/customers) | Mit Kundenobjekten können Sie wiederkehrende Gebühren durchführen und mehrere Gebühren verfolgen, die demselben Kunden zugeordnet sind. |
| [`Charges`](https://stripe.com/docs/payments/payment-intents/migration/charges) | Diese Tabelle enthält Informationen zu Gebühren für Kredit- und Debitkarten, einschließlich Betrag, Währung, Status, Kunden-ID und mehr. |
| [`Coupons`](https://stripe.com/docs/api/coupons/object) | Diese Tabelle enthält Informationen zu einem Rabatt in Prozent oder einem Rabattbetrag, den Sie möglicherweise auf einen Kunden anwenden möchten. Coupons gelten nur für Rechnungen, nicht aber für einmalige Gebühren. |
| [`Invoices`](https://stripe.com/docs/billing/migration/invoice-states) | Diese Tabelle enthält Informationen zu Rechnungen, einschließlich geschuldetem Betrag, Abonnements, Rechnungsartikeln, automatischen Verteilungskorrekturen und mehr. |
| [`Plans`](https://stripe.com/docs/api/plans/object) | Diese Tabelle enthält die Preisinformationen für verschiedene Produkte und Funktionsstufen auf Ihrer Site. Beispielsweise können Sie einen Plan für 10 USD/Monat für grundlegende Funktionen und einen Plan für 20 USD/Monat für Premium-Funktionen haben. |
| [`Subscriptions`](https://stripe.com/docs/api/subscriptions/object) | Diese Tabelle enthält die Details der Abonnementpläne, denen Ihre Kunden angehören. Zu den Attributen gehören Kunden-ID, Status, Stornierungen/Beendigung am Datum, Steuerprozentsatz, Testinformationen und mehr. |
| [`Events`](https://stripe.com/docs/development/dashboard/events) | Ereignisse informieren Sie über interessante Ereignisse, die in einem Konto aufgetreten sind. [Wenn ein interessantes Ereignis auftritt](https://stripe.com/docs/api/events/types) wird ein neues Ereignisobjekt erstellt. Beispiel: Wenn eine Belastung erfolgreich ist `charge.succeeded` ein Ereignis erstellt wird; oder wenn eine Rechnung nicht bezahlt werden kann, wird ein `invoice.payment\_failed` erstellt. |

{style="table-layout:auto"}

>[!NOTE]
>
>Viele API-Anfragen können dazu führen, dass mehrere Ereignisse erstellt werden. Wenn Sie beispielsweise ein Abonnement für eine Kundin oder einen Kunden erstellen, erhalten Sie sowohl ein `customer.subscription.created` als auch ein `charge.succeeded`.

## Verwandt:

* [Verbinden [!DNL Stripe]](../integrations/stripe.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
