---
title: Erwartete Mixpanel-Daten
description: Informieren Sie sich über die wichtigsten Datentabellen, die Sie aus Mixpanel in Ihr [!DNL Commerce Intelligence]-Konto importieren können.
exl-id: 87bd337a-63fa-44cf-b1fe-c2f34ca86029
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: 'https://experienceleague.adobe.com/iM6GzisImrjed7uCZf6lf6HIze9MwWdhq2gEP-IrIXA'
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
    internal-label: Commerce Intelligence
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
    internal-label: Data Warehouse Manager
  - id: 5d2a63cb-5675-5572-9de5-bc904157ef45
    internal-label: Commerce Tables
  - id: 4d217dbe-2c9a-5839-94d7-471fd31623b7
    internal-label: Data Integration
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
source-git-commit: fdbaf74705fb224414ac8cb69f6a1b34277e3f79
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%
---
# Erwartete [!DNL Mixpanel]

Nachdem [Sie Ihr [!DNL Mixpanel] Konto verbunden haben](../integrations/mixpanel.md) können Sie den [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Mixpanel] in Ihr [!DNL Commerce Intelligence]-Konto importieren können. Die folgenden Tabellen werden in Ihrer Data Warehouse nach dem Verbinden von [!DNL Mixpanel] erstellt. Um alle für das Tracking verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Spalte „Tabellenname“.

>[!NOTE]
>
>Aufgrund der Einschränkungen der [!DNL Mixpanel]-API werden historische Daten - Daten, die älter als sieben (7) Tage ab dem Datum der Verbindung mit [!DNL Commerce Intelligence] sind - nicht repliziert.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`mixpanel\_export`](https://developer.mixpanel.com/reference/raw-data-export-api#datafeed) | Diese Tabelle enthält unformatierte Ereignisdaten, einschließlich Ereignis, Ereignisdaten und Plattform-Bucket. |
| [`mixpanel\_funnels`](https://developer.mixpanel.com/reference/raw-data-export-api#funnels-default) | Diese Tabelle enthält Daten zu Ihren Trichtern, einschließlich der funnel-ID, der funnel-Dauer (Anzahl der Tage, die der Benutzer bzw. die Benutzerin zum Abschließen der funnel benötigt) sowie des Start- und Enddatums der funnel. |
| [`mixpanel\_engage`](https://developer.mixpanel.com/reference/raw-data-export-api#engage-default) | Diese enthält Daten aus People Analytics, einschließlich Sitzungs-IDs, Seiten- und Benutzerinformationen sowie Datum und Uhrzeit des letzten Besuchs des Benutzers. |

{style="table-layout:auto"}

## Verwandte Dokumentation

* [Verbinden [!DNL Mixpanel]](../integrations/mixpanel.md)
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations)
