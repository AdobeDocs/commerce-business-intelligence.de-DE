---
title: Erwartete Mixpanel-Daten
description: Informieren Sie sich über die wichtigsten Datentabellen, die Sie aus Mixpanel in Ihr - [!DNL Commerce Intelligence]  importieren können.
exl-id: 87bd337a-63fa-44cf-b1fe-c2f34ca86029
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '187'
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
| [`mixpanel\_funnels`](https://developer.mixpanel.com/reference/raw-data-export-api#funnels-default) | Diese Tabelle enthält Daten zu Ihren Trichtern, einschließlich der Trichterkennung, der Trichterlänge (Anzahl der Tage, an denen der Benutzer den Trichter abschließen muss) und des Start- und Enddatums des Trichters. |
| [`mixpanel\_engage`](https://developer.mixpanel.com/reference/raw-data-export-api#engage-default) | Diese enthält Daten aus People Analytics, einschließlich Sitzungs-IDs, Seiten- und Benutzerinformationen sowie Datum und Uhrzeit des letzten Besuchs des Benutzers. |

{style="table-layout:auto"}

## Verwandte Dokumentation

* [Verbinden [!DNL Mixpanel]](../integrations/mixpanel.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
