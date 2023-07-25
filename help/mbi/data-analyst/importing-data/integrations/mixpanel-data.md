---
title: Erwartete Mixpanel-Daten
description: Die wichtigsten Datentabellen, die Sie aus Mixpanel in Ihre [!DNL Commerce Intelligence] -Konto.
exl-id: 87bd337a-63fa-44cf-b1fe-c2f34ca86029
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Erwartet [!DNL Mixpanel] data

Nachher [Sie haben Ihre [!DNL Mixpanel] account](../integrations/mixpanel.md), können Sie die [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse.

In diesem Thema werden die wichtigsten Datentabellen untersucht, aus denen Sie importieren können. [!DNL Mixpanel] in [!DNL Commerce Intelligence] -Konto. Die folgenden Tabellen werden in Ihrer Data Warehouse erstellt, nachdem Sie eine Verbindung hergestellt haben [!DNL Mixpanel]. Um alle für die Verfolgung verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Tabellennamenspalte.

>[!NOTE]
>
>Aufgrund der Einschränkungen der [!DNL Mixpanel] API, historische Daten - Daten, die älter als sieben (7) Tage ab dem Datum der Verbindung zu [!DNL Commerce Intelligence] - wird nicht repliziert.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`mixpanel\_export`](https://developer.mixpanel.com/reference/raw-data-export-api#datafeed) | Diese Tabelle enthält Rohdaten zu Ereignissen, einschließlich Ereignis-, Ereignis- und Plattform-Bucket. |
| [`mixpanel\_funnels`](https://developer.mixpanel.com/reference/raw-data-export-api#funnels-default) | Diese Tabelle enthält Daten zu Ihren Trichter, einschließlich der Trichterkennung, der Trichterlänge (Anzahl der Tage, die der Benutzer den Trichter abschließen muss) sowie des Start- und Enddatums des Trichters. |
| [`mixpanel\_engage`](https://developer.mixpanel.com/reference/raw-data-export-api#engage-default) | Dies enthält Daten aus People Analytics, einschließlich Sitzungs-IDs, Seiten- und Benutzerinformationen sowie Datum/Uhrzeit der letzten Anzeige des Benutzers. |

{style="table-layout:auto"}

## Verwandte Dokumentation

* [Verbinden [!DNL Mixpanel]](../integrations/mixpanel.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
