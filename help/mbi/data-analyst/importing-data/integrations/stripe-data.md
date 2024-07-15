---
title: Erwartete Stripe-Daten
description: Hier erhalten Sie Informationen zu den wichtigsten Datentabellen, die Sie von Stripe in Commerce Intelligence importieren können.
exl-id: 694577b2-48f9-4376-850d-acae1776afe3
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Erwartete [!DNL Stripe] Daten

Nachdem [Sie Ihr [!DNL Stripe] Konto](../integrations/stripe.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Stripe] in [!DNL Commerce Intelligence] importieren können. Nach Abschluss der Einrichtung werden die folgenden Tabellen in Ihrer Data Warehouse erstellt. Klicken Sie auf die Links in der Spalte Tabellenname , um mehr über die Attribute in den einzelnen Tabellen zu erfahren.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`Customers`](https://stripe.com/docs/sources/customers) | Kundenobjekte ermöglichen es Ihnen, wiederkehrende Gebühren zu erheben und mehrere Gebühren zu verfolgen, die demselben Kunden zugeordnet sind. |
| [`Charges`](https://stripe.com/docs/payments/payment-intents/migration/charges) | Diese Tabelle enthält Informationen zu Gebühren für Kredit- und Debitkarten, einschließlich Betrag, Währung, Status, Kunden-ID und mehr. |
| [`Coupons`](https://stripe.com/docs/api/coupons/object) | Diese Tabelle enthält Informationen über einen prozentualen oder Rabatt, den Sie möglicherweise auf einen Kunden anwenden möchten. Gutscheine gelten nur für Rechnungen; sie gelten nicht für einmalige Gebühren. |
| [`Invoices`](https://stripe.com/docs/billing/migration/invoice-states) | Diese Tabelle enthält Informationen zu den Rechnungen, einschließlich des geschuldeten Betrags, der Abonnements, der Rechnungseinträge, aller automatischen Anpassungen des Anteils und mehr. |
| [`Plans`](https://stripe.com/docs/api/plans/object) | Diese Tabelle enthält die Preisinformationen für verschiedene Produkte und Funktionsstufen auf Ihrer Site. Beispielsweise verfügen Sie möglicherweise über einen 10-Dollar-Vertrag pro Monat für grundlegende Funktionen und einen 20-Dollar-Vertrag pro Monat für Premium-Funktionen. |
| [`Subscriptions`](https://stripe.com/docs/api/subscriptions/object) | Diese Tabelle enthält Details zu Abonnementplänen, zu denen Ihre Kunden gehören. Zu den Attributen gehören Kunden-ID, Status, abgebrochen/zu Daten beendet, Steuersatz, Testinformationen und mehr. |
| [`Events`](https://stripe.com/docs/development/dashboard/events) | Ereignisse informieren Sie über etwas Interessantes, das in einem Konto passiert ist. [Wenn ein interessantes Ereignis auftritt](https://stripe.com/docs/api/events/types), wird ein neues Ereignisobjekt erstellt. Beispiel: Wenn eine Ladung das `charge.succeeded` -Ereignis erfolgreich durchläuft, oder wenn eine Rechnung nicht bezahlt werden kann, wird ein `invoice.payment\_failed` -Ereignis erstellt. |

{style="table-layout:auto"}

>[!NOTE]
>
>Viele API-Anfragen können dazu führen, dass mehrere Ereignisse erstellt werden. Wenn Sie beispielsweise ein Abonnement für einen Kunden erstellen, erhalten Sie sowohl ein `customer.subscription.created` -Ereignis als auch ein `charge.succeeded` -Ereignis.

## Verwandte:

* [Verbinden [!DNL Stripe]](../integrations/stripe.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
