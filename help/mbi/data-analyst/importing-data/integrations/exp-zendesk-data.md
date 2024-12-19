---
title: Erwartete Zendesk-Daten
description: Erfahren Sie mehr über die wichtigsten Datentabellen, die Sie von Zendesk in Commerce Intelligence importieren können, einschließlich Links zu zusätzlichen Dokumentationen zu Zendesk-Daten.
exl-id: 838d8d13-e2e1-44c2-a416-f1792200ee6f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Erwartete [!DNL Zendesk]

Nachdem [Sie Ihr [!DNL Zendesk] Konto verbunden haben](../integrations/zendesk.md) können Sie den [Data Warehouse-Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

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
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
