---
title: Erwartete Mixpanel-Daten
description: Erkunden Sie die Hauptdatentabellen, die Sie aus Mixpanel in Ihr [!DNL Commerce Intelligence] Konto importieren können.
exl-id: 87bd337a-63fa-44cf-b1fe-c2f34ca86029
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Erwartete [!DNL Mixpanel] Daten

Nachdem [Sie Ihr [!DNL Mixpanel] Konto](../integrations/mixpanel.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Thema werden die wichtigsten Datentabellen untersucht, die Sie aus [!DNL Mixpanel] in Ihr [!DNL Commerce Intelligence] -Konto importieren können. Die folgenden Tabellen werden nach dem Verbinden von [!DNL Mixpanel] in Ihrer Data Warehouse erstellt. Um alle für die Verfolgung verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Tabellennamenspalte.

>[!NOTE]
>
>Aufgrund der Einschränkungen der [!DNL Mixpanel] -API werden historische Daten - Daten, die älter als sieben (7) Tage ab dem Datum der Verbindung zu [!DNL Commerce Intelligence] sind - nicht repliziert.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`mixpanel\_export`](https://developer.mixpanel.com/reference/raw-data-export-api#datafeed) | Diese Tabelle enthält Rohdaten zu Ereignissen, einschließlich Ereignis-, Ereignis- und Plattform-Bucket. |
| [`mixpanel\_funnels`](https://developer.mixpanel.com/reference/raw-data-export-api#funnels-default) | Diese Tabelle enthält Daten zu Ihren Trichter, einschließlich der Trichterkennung, der Trichterlänge (Anzahl der Tage, die der Benutzer den Trichter abschließen muss) sowie des Start- und Enddatums des Trichters. |
| [`mixpanel\_engage`](https://developer.mixpanel.com/reference/raw-data-export-api#engage-default) | Dies enthält Daten aus People Analytics, einschließlich Sitzungs-IDs, Seiten- und Benutzerinformationen sowie Datum/Uhrzeit der letzten Anzeige des Benutzers. |

{style="table-layout:auto"}

## Verwandte Dokumentation

* [Verbinden [!DNL Mixpanel]](../integrations/mixpanel.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
