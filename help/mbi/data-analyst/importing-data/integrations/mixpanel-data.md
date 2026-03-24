---
title: Erwartete Mixpanel-Daten
description: Informieren Sie sich über die wichtigsten Datentabellen, die Sie aus Mixpanel in Ihr - [!DNL Commerce Intelligence]  importieren können.
exl-id: 87bd337a-63fa-44cf-b1fe-c2f34ca86029
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/iM6GzisImrjed7uCZf6lf6HIze9MwWdhq2gEP-IrIXA
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
source-wordcount: 187
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
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
