---
title: Erwartete Salesforce-Daten
description: Erfahren Sie mehr über unterstützte und nicht unterstützte Objekte in Salesforce-Daten.
exl-id: 6625349f-2ec0-402d-8635-889a1f29811c
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 5e80ff8f8ec76996b88a22b115be696b110581be
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Erwartete [!DNL Salesforce]

Nachdem [[!DNL Salesforce] Setup](../integrations/salesforce.md) abgeschlossen ist, wird eine Tabelle für jedes abfragbare [Objekt](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_objects_concepts.htm) - namens `sf_/\{sobject-name}` - in Ihrer Data Warehouse erstellt.

>[!NOTE]
>
>Die Struktur (Spalten) jeder Tabelle hängt von den Feldern ab, die im -Objekt enthalten sind.

Eine Liste der für Ihr Unternehmen verfügbaren Objekte finden Sie in der [!DNL Salesforce] [Abrufen einer Liste von Objekten](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/dome_describeGlobal.htm). Nachdem Sie eine Liste von Objekten haben, lesen Sie den Abschnitt [Entitätsbeziehungsdiagramm (ERD)](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_erd_knowledge.htm) [!DNL Salesforce] Dokumentation, um zu sehen, wie Entitäten miteinander zusammenhängen.

## Nicht unterstützte Objekte

Derzeit macht [!DNL Salesforce] die folgenden Objekte in ihrer API nicht verfügbar:

* `Announcement`
* `Attachment`
* `ContentDocumentLink`
* `External objects` - [Was ist ein externes Objekt?](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_objects_external_objects.htm)
* `CollaborationGroupRecord`
* `ContentDocument`
* `ContentDocumentLink`
* `FeedItem`
* `FieldDefinition`
* `IdeaComment`
* `ListViewChartInstance`
* `Order`
* `PlatformAction`

* `KnowledgeArticleVersion`
* `NewsFeed`
* `RecentlyViewed`
* `TopicAssignment`
* `UserRecordAccess`
* `UserProfileFeed`
* `Vote`

## Verwandt:

* [Verbinden [!DNL Salesforce]](../integrations/salesforce.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
