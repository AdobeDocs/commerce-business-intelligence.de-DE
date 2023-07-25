---
title: Erwartete Salesforce-Daten
description: Erfahren Sie mehr über unterstützte und nicht unterstützte Objekte in Salesforce-Daten.
exl-id: 6625349f-2ec0-402d-8635-889a1f29811c
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Erwartet [!DNL Salesforce] data

Nach dem [[!DNL Salesforce] Setup](../integrations/salesforce.md) ist abgeschlossen, eine Tabelle für jede Abfrageoption [Objekt](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_objects_concepts.htm) - benannt `sf_/\{sobject-name}` - wird in Ihrer Data Warehouse erstellt.

>[!NOTE]
>
>Die Struktur (Spalten) der einzelnen Tabellen hängt von den im Objekt enthaltenen Feldern ab.

Eine Liste der für Ihre Organisation verfügbaren Objekte erhalten Sie im Abschnitt [!DNL Salesforce] [Dokumentation zu Objekten abrufen](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/dome_describeGlobal.htm). Nachdem Sie über eine Liste von Objekten verfügen, sehen Sie sich die [Abschnitt &quot;Entitäts-Beziehungsdiagramm (ERD)&quot;](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_erd_knowledge.htm) von [!DNL Salesforce] Dokumentation, um zu sehen, wie Entitäten zueinander in Beziehung stehen.

## Nicht unterstützte Objekte

Zurzeit [!DNL Salesforce] stellt die folgenden Objekte derzeit nicht in ihrer API bereit:

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

## Verwandte:

* [Verbinden [!DNL Salesforce]](../integrations/salesforce.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
