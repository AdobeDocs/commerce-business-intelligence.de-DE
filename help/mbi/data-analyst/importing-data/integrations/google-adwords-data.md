---
title: Erwartete Google Adwords-Daten
description: Erfahren Sie, wie Sie mit dem Data Warehouse-Manager relevante Datenfelder für die Analyse einfach nachverfolgen können.
exl-id: b0085683-7bb1-4da2-b343-4309e4796f0c
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Erwartete [!DNL Google Adwords] Daten

Nachdem [Sie Ihr [!DNL Google Adwords] Konto](../integrations/google-adwords.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

Dort sind zwei Tabellen für die Replikation auf Ihrem Data Warehouse verfügbar:

* `campaigns[account-id]`
* `adwords[account-id]`

Die `campaigns` Tabelle *sollte standardmäßig verwendet werden*, sodass Sie mit der Synchronisierung aller relevanten Felder aus dieser Tabelle beginnen können.

Die Tabelle `adwords` enthält vier Spalten, die nicht in der Tabelle `campaigns` enthalten sind:

1. `keyword`
1. `adContent`
1. `adDestinationUrl`
1. `adGroup`

Wenn Sie eine Analyse durchführen möchten, die diese Attribute berücksichtigt, müssen Sie die Tabelle `adwords` verwenden.

>[!IMPORTANT]
>
>Diese Tabelle schließt Zeilen aus, in denen alle vier dieser Spalten `null` sind.

Im Folgenden finden Sie einen Überblick über das erwartete Schema für beide Tabellen.

## [!DNL Campaigns] table

Die Tabelle `campaigns` enthält die folgenden Spalten:

| **Column** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adwordscampaignid) | [!DNL Adwords] Kampagnen-ID |
| [`campaign`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=traffic_sources&amp;jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=time&amp;jump=ga_date) | Das Datum der Ausführung der Kampagne |
| [`impressions`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |

{style="table-layout:auto"}

## [!DNL AdWords] table

Die Tabelle `adwords` enthält die folgenden Spalten:

| **Column** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adwordscampaignid) | [!DNL Adwords] Kampagnen-ID |
| [`campaign`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=traffic_sources&amp;jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=time&amp;jump=ga_date) | Das Datum der Ausführung der Kampagne |
| [`impressions`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |
| `keyword` | Der Suchbegriff der Kampagne |
| `adContent` | Die erste Zeile des Textes für die Online-Kampagne |
| `adDestinationUrl` | Die URL, auf die die [!DNL Adwords] -Anzeigen Traffic verwiesen haben |
| `adGroup` | Der Name der Anzeigengruppe [!DNL Adwords] |

{style="table-layout:auto"}

Mithilfe dieser Daten können Sie die Erstellung von [Metriken](../../../data-user/reports/ess-manage-data-metrics.md) und [Berichten](../../../tutorials/using-visual-report-builder.md) auf der Grundlage der Ausgabedaten und [heiraten, um den ROI zu berechnen](../../analysis/roi-ad-camp.md).

## Konsolidierte Tabellen

[!DNL Adobe] empfiehlt, eine `consolidated ad spend` -Tabelle zu erstellen, um die Daten aus allen Ihren verschiedenen Werbequellen in einer einzigen Tabelle zu kombinieren. Auf diese Weise können Sie einen einzigen Metriksatz für die Werbeanalyse verwenden.

Wenn Sie keine konsolidierte Tabelle haben und ein schönes Dashboard auf der `adwords` -Tabelle erstellen, müssen Sie die Berichterstellung replizieren oder doppelte Metriken erstellen, um diese Daten mit Ihren [!DNL Facebook Ads] -Daten zu vergleichen. Mithilfe einer konsolidierten Tabelle können Sie [!DNL Facebook Ads] -Daten nahtlos in Ihre vorhandenen [!DNL Adwords] -Berichte integrieren. Sie können auch nach Anzeigenplattform segmentieren.

Wenn Sie die oben genannten Felder bereits synchronisiert haben, kontaktieren Sie uns [1}, um Ihre Werbeausgaben zu konsolidieren.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)
