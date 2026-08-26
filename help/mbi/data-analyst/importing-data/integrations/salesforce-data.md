---
title: Erwartete Salesforce-Daten
description: Erfahren Sie mehr über unterstützte und nicht unterstützte Objekte in Salesforce-Daten.
exl-id: 6625349f-2ec0-402d-8635-889a1f29811c
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/eBX3Y0luu60A8PSAF43H6O3fsYjJnSWzyIybSOcSELE
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
source-git-commit: 02934da4962380494ab8a2becf5f06efb15d84dc
workflow-type: tm+mt
source-wordcount: 153
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
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations)
