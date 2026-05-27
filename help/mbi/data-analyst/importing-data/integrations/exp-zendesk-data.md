---
title: Erwartete Zendesk-Daten
description: Erfahren Sie mehr über die wichtigsten Datentabellen, die Sie von Zendesk in Commerce Intelligence importieren können, einschließlich Links zu zusätzlichen Dokumentationen zu Zendesk-Daten.
exl-id: 838d8d13-e2e1-44c2-a416-f1792200ee6f
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/0p4SOrpj7wM-y5j3CMpHTs7HpysB5znJu3jSNiVJ2YY
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 432
ht-degree: 0%

---

# Erwartete [!DNL Zendesk]

Nachdem [Sie Ihr [!DNL Zendesk] Konto verbunden haben](../integrations/zendesk.md) können Sie den [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Zendesk] in [!DNL Adobe Commerce Intelligence] importieren können, einschließlich Links zu zusätzlichen Dokumentationen zu [!DNL Zendesk].

| Tabellenname | Beschreibung |
|-----|-----|
| [`Audits`](https://developer.zendesk.com/rest_api/docs/core/ticket_audits) | In der `Audits` Tabelle werden die mit einem Ticket verbundenen Aktivitäten aufgezeichnet, einschließlich Statusänderungen und sowohl Kunden- als auch Agentenantworten. Diese Tabelle enthält eine Ticket-ID, die mit der `Tickets` verknüpft ist. Damit können Sie für jedes Ticket die Zeit bis zur ersten Antwort und die Zeit bis zur Lösung analysieren. |
| [`Audit_~\_Events`](https://developer.zendesk.com/rest_api/docs/core/ticket_audits#audit-events) | Die `audit_~\_events` ist das untergeordnete Element der `audits` und zeichnet zusätzliche Details eines Ticket-Ereignisses auf. |
| [`Organizations`](https://developer.zendesk.com/rest_api/docs/core/organizations) | In der `Organizations` werden Unternehmensinformationen zu Ihren Endbenutzern wie Name, ID, zugehörige Domain-Namen, Tags und benutzerdefinierte Felder aufgezeichnet. |
| [`Tickets`](https://developer.zendesk.com/rest_api/docs/core/tickets) | In der `Tickets` Tabelle werden alle Ticket-Details aufgezeichnet, einschließlich des `created_at` Zeitstempels und der `requester\_id` und `assignee\_id`, sodass Sie ein Ticket mit einem Endbenutzer bzw. Agenten in der `Users` Tabelle verknüpfen können. |
| [`Ticket_~\_Fields`](https://developer.zendesk.com/rest_api/docs/core/ticket_fields) | Die Tabelle `ticket fields` enthält Informationen zu den grundlegenden Textfeldern und benutzerdefinierten Ticketfeldern in Ihrem Konto. Zu den Attributen dieser Tabelle gehören die `ID`, `URL`, `type`, `title`, `description`, `position`, `requirement setting`, agenten- und endbenutzerspezifische Informationen sowie Informationen zur Erstellung und Aktualisierung. |
| [`Users`](https://developer.zendesk.com/rest_api/docs/core/users) | Die `Users` Tabelle enthält alle Details zu Endbenutzern und Agenten, einschließlich des Namens und der E-Mail-Adresse der Person. Auf diese Weise können Sie sowohl die Interaktion Ihrer Endbenutzer als auch die Leistung Ihrer Agenten analysieren. |
| [`Zendesk\_Groups`](https://developer.zendesk.com/rest_api/docs/core/groups) | Gruppen sind die Art und Weise, wie Agenten in Ihrem Zendesk-Konto organisiert sind. Die `Groups`-Tabelle zeichnet Informationen wie die `group ID`-, `URL`-, `name`- und Erstellungs- und Aktualisierungsinformationen auf. |
| [`Zendesk\_Macro`](https://developer.zendesk.com/rest_api/docs/core/macros) | Makros sind von Ihnen definierte Aktionen, die die Werte der Felder eines Tickets ändern. Diese Tabelle enthält Attribute wie den Titel des Makros, die ID, Aktionen, Einschränkungen und Informationen zur Erstellung und Aktualisierung. |
| [`Zendesk\_Tags`](https://developer.zendesk.com/rest_api/docs/core/tags) | Die Tabelle `Tags` enthält eine Liste aller Tags in Ihrem Konto. |
| [`Zendesk\_Ticket\_Metrics`](https://developer.zendesk.com/rest_api/docs/core/ticket_metrics#ticket-metrics) | Diese Tabelle enthält Daten zu Ticket-Metriken. Die Felder enthalten die `ticket ID`, die `URL` und die Anzahl der Gruppen, der Verantwortlichen, der erneuten Öffnungen, der Antworten, der Antwortzeit (in Minuten), der vollständigen Auflösungszeit und der Informationen zur letzten Aktualisierung (z. B. Status, Verantwortlicher oder Auftraggeber). |

{style="table-layout:auto"}

## verwandt

* [Verbinden von Zendesk](../integrations/zendesk.md)
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
