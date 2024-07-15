---
title: Erwartete Zendesk-Daten
description: Erfahren Sie mehr über die wichtigsten Datentabellen, die Sie aus Zendesk in Commerce Intelligence importieren können, einschließlich Links zur zusätzlichen Dokumentation zu Zendesk-Daten.
exl-id: 838d8d13-e2e1-44c2-a416-f1792200ee6f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Erwartete [!DNL Zendesk] Daten

Nachdem [Sie Ihr [!DNL Zendesk] Konto](../integrations/zendesk.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Zendesk] in [!DNL Adobe Commerce Intelligence] importieren können, einschließlich Links zu zusätzlicher Dokumentation zu [!DNL Zendesk] -Daten.

| Tabellenname | Beschreibung |
|-----|-----|
| [`Audits`](https://developer.zendesk.com/rest_api/docs/core/ticket_audits) | Die Tabelle `Audits` zeichnet die mit einem Ticket verknüpfte Aktivität auf, einschließlich Statusänderungen sowie Kunden- und Agentenantworten. Diese Tabelle enthält eine Ticket-ID, die zur Tabelle `Tickets` zurückverweist. Diese ermöglicht es Ihnen, die Zeit bis zur ersten Antwort und die Zeit bis zur Auflösung für jedes Ticket zu analysieren. |
| [`Audit_~\_Events`](https://developer.zendesk.com/rest_api/docs/core/ticket_audits#audit-events) | Die Tabelle `audit_~\_events` ist das untergeordnete Element der Tabelle `audits` und zeichnet zusätzliche Details eines Ticketereignisses auf. |
| [`Organizations`](https://developer.zendesk.com/rest_api/docs/core/organizations) | In der Tabelle &quot;`Organizations`&quot;werden Unternehmensinformationen zu Ihren Endbenutzern wie Name, ID, zugewiesene Domänennamen, Tags und beliebige benutzerdefinierte Felder aufgezeichnet. |
| [`Tickets`](https://developer.zendesk.com/rest_api/docs/core/tickets) | In der Tabelle `Tickets` werden alle Ticketdetails aufgezeichnet, einschließlich des Zeitstempels `created_at` und des Zeitstempels `requester\_id` und des Felds `assignee\_id`, wodurch Sie ein Ticket jeweils mit einem Endbenutzer und Agenten in der Tabelle `Users` verknüpfen können. |
| [`Ticket_~\_Fields`](https://developer.zendesk.com/rest_api/docs/core/ticket_fields) | Die Tabelle `ticket fields` enthält Informationen zu den grundlegenden Textfeldern und benutzerdefinierten Feldern für Tickets in Ihrem Konto. Zu den Attributen dieser Tabelle gehören das Feld `ID`, `URL`, `type`, `title`, `description`, `position`, `requirement setting`, agent und endbenutzerspezifische Informationen sowie Erstellungs- und Aktualisierungsinformationen. |
| [`Users`](https://developer.zendesk.com/rest_api/docs/core/users) | Die Tabelle `Users` enthält alle Details zu Endbenutzern und Agenten, einschließlich des Namens und der E-Mail-Adresse des Kontakts. Auf diese Weise können Sie die Interaktion Ihrer Endbenutzer und die Leistung Ihrer Agenten analysieren. |
| [`Zendesk\_Groups`](https://developer.zendesk.com/rest_api/docs/core/groups) | Gruppen zeigen, wie Agenten in Ihrem Zendesk-Konto organisiert werden. Die Tabelle `Groups` enthält Informationen wie die `group ID`, `URL`, `name` sowie Erstellungs- und Aktualisierungsinformationen. |
| [`Zendesk\_Macro`](https://developer.zendesk.com/rest_api/docs/core/macros) | Makros sind von Ihnen definierte Aktionen, die die Werte der Felder eines Tickets ändern. Diese Tabelle enthält Attribute wie Titel, Kennung, Aktionen, Einschränkungen sowie Erstellungs- und Aktualisierungsinformationen des Makros. |
| [`Zendesk\_Tags`](https://developer.zendesk.com/rest_api/docs/core/tags) | Die Tabelle `Tags` enthält eine Liste aller Tags in Ihrem Konto. |
| [`Zendesk\_Ticket\_Metrics`](https://developer.zendesk.com/rest_api/docs/core/ticket_metrics#ticket-metrics) | Diese Tabelle enthält Daten zu Ticketmetriken. Zu den Feldern gehören die Felder `ticket ID`, `URL` und die Anzahl der Gruppen, Bevollmächtigten, erneuten Öffnungen, Antworten, Antwortzeiten (in Minuten), die volle Auflösungszeit und die letzte Aktualisierung (z. B. Status, Bevollmächtigter oder Anforderer). |

{style="table-layout:auto"}

## Verwandte

* [Zendesk verbinden](../integrations/zendesk.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
