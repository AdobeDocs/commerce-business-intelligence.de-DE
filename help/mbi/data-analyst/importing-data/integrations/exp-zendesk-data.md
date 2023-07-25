---
title: Erwartete Zendesk-Daten
description: Erfahren Sie mehr über die wichtigsten Datentabellen, die Sie aus Zendesk in Commerce Intelligence importieren können, einschließlich Links zur zusätzlichen Dokumentation zu Zendesk-Daten.
exl-id: 838d8d13-e2e1-44c2-a416-f1792200ee6f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Erwartet [!DNL Zendesk] data

Nachher [Sie haben Ihre [!DNL Zendesk] account](../integrations/zendesk.md), können Sie die [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse.

In diesem Thema werden die wichtigsten Datentabellen untersucht, aus denen Sie importieren können. [!DNL Zendesk] in [!DNL Adobe Commerce Intelligence], einschließlich Links zur zusätzlichen Dokumentation zu [!DNL Zendesk] Daten.

| Tabellenname | Beschreibung |
|-----|-----|
| [`Audits`](https://developer.zendesk.com/rest_api/docs/core/ticket_audits) | Die `Audits` -Tabelle erfasst Aktivitäten, die mit einem Ticket verknüpft sind, einschließlich Statusänderungen sowie Kunden- und Agentenantworten. Diese Tabelle enthält eine Ticket-ID, die auf die `Tickets` -Tabelle, in der Sie die Zeit bis zur ersten Antwort und die Zeit bis zur Auflösung für jedes Ticket analysieren können. |
| [`Audit_~\_Events`](https://developer.zendesk.com/rest_api/docs/core/ticket_audits#audit-events) | Die `audit_~\_events` -Tabelle ist das untergeordnete Element der `audits` -Tabelle und zeichnet zusätzliche Details zu einem Ticketereignis auf. |
| [`Organizations`](https://developer.zendesk.com/rest_api/docs/core/organizations) | Die `Organizations` -Tabelle enthält Unternehmensinformationen zu Ihren Endbenutzern, wie z. B. Name, ID, zugehörige Domänennamen, Tags und alle benutzerdefinierten Felder. |
| [`Tickets`](https://developer.zendesk.com/rest_api/docs/core/tickets) | Die `Tickets` -Tabelle enthält alle Ticketdetails, einschließlich der `created_at` Zeitstempel und `requester\_id` und `assignee\_id`, mit dem Sie ein Ticket mit einem Endbenutzer und Agenten im `Users` -Tabelle. |
| [`Ticket_~\_Fields`](https://developer.zendesk.com/rest_api/docs/core/ticket_fields) | Die `ticket fields` enthält Informationen zu den grundlegenden Textfeldern und benutzerdefinierten Feldern für Tickets in Ihrem Konto. Attribute dieser Tabelle umfassen das Feld `ID`, `URL`, `type`, `title`, `description`, `position`, `requirement setting`, agenten- und benutzerspezifische Informationen sowie Informationen zur Erstellung und Aktualisierung. |
| [`Users`](https://developer.zendesk.com/rest_api/docs/core/users) | Die `Users` enthält alle Details zu Endbenutzern und Agenten, einschließlich des Namens und der E-Mail-Adresse des Kontakts. Auf diese Weise können Sie die Interaktion Ihrer Endbenutzer und die Leistung Ihrer Agenten analysieren. |
| [`Zendesk\_Groups`](https://developer.zendesk.com/rest_api/docs/core/groups) | Gruppen zeigen, wie Agenten in Ihrem Zendesk-Konto organisiert werden. Die `Groups` -Tabelle enthält Informationen, z. B. `group ID`, `URL`, `name`, sowie Informationen zur Erstellung und Aktualisierung. |
| [`Zendesk\_Macro`](https://developer.zendesk.com/rest_api/docs/core/macros) | Makros sind von Ihnen definierte Aktionen, die die Werte der Felder eines Tickets ändern. Diese Tabelle enthält Attribute wie Titel, Kennung, Aktionen, Einschränkungen sowie Erstellungs- und Aktualisierungsinformationen des Makros. |
| [`Zendesk\_Tags`](https://developer.zendesk.com/rest_api/docs/core/tags) | Die `Tags` enthält eine Liste aller Tags in Ihrem Konto. |
| [`Zendesk\_Ticket\_Metrics`](https://developer.zendesk.com/rest_api/docs/core/ticket_metrics#ticket-metrics) | Diese Tabelle enthält Daten zu Ticketmetriken. Die Felder enthalten die `ticket ID`, `URL`und die Anzahl der Gruppen, Bevollmächtigten, erneuten Öffnungen, Antworten, Antwortzeiten (in Minuten), vollen Auflösungszeiten und der letzten Aktualisierung (z. B. Status, Bevollmächtigter oder Anforderer). |

{style="table-layout:auto"}

## Verwandte

* [Zendesk verbinden](../integrations/zendesk.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
