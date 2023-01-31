---
title: Erwartete Mixpanel-Daten
description: Die wichtigsten Datentabellen, die Sie aus Mixpanel in Ihre [!DNL MBI] -Konto.
exl-id: 87bd337a-63fa-44cf-b1fe-c2f34ca86029
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Erwartet [!DNL Mixpanel] data

Nachher [Sie haben Ihre [!DNL Mixpanel] account](../integrations/mixpanel.md), können Sie die [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse.

In diesem Artikel untersuchen wir die wichtigsten Datentabellen, aus denen Sie importieren können [!DNL Mixpanel] in [!DNL MBI] -Konto. Die folgenden Tabellen werden in Ihrem Data Warehouse erstellt, nachdem Mixpanel verbunden wurde. Um alle für die Verfolgung verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Tabellennamenspalte.

>[!NOTE]
>
>Aufgrund der Einschränkungen der [!DNL Mixpanel] API, historische Daten - Daten, die älter als sieben (7) Tage ab dem Datum der Verbindung zu [!DNL MBI] - wird nicht repliziert.

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`mixpanel\_export`](https://mixpanel.com/docs/api-documentation/exporting-raw-data-you-inserted-into-mixpanel#datafeed) | Diese Tabelle enthält Rohdaten zu Ereignissen, einschließlich Ereignis-, Ereignis- und Plattform-Bucket. |
| [`mixpanel\_funnels`](https://mixpanel.com/docs/api-documentation/data-export-api#funnels-default) | Diese Tabelle enthält Daten zu Ihren Trichter, einschließlich der Trichterkennung, der Trichterlänge (Anzahl der Tage, die der Benutzer den Trichter abschließen muss) sowie des Start- und Enddatums des Trichters. |
| [`mixpanel\_engage`](https://mixpanel.com/docs/api-documentation/data-export-api#engage-default) | Dies enthält Daten aus People Analytics, einschließlich Sitzungs-IDs, Seiten- und Benutzerinformationen sowie Datum/Uhrzeit der letzten Anzeige des Benutzers. |

{style=&quot;table-layout:auto&quot;}

## Verwandte Dokumentation

* [Verbinden [!DNL Mixpanel]](../integrations/mixpanel.md)
* [Erneutes Authentifizieren von Integrationen](https://support.magento.com/hc/en-us/articles/360016733151-Reauthenticating-integrations)
