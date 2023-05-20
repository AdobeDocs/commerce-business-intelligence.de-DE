---
title: Erwartete Google Adwords-Daten
description: Erfahren Sie, wie Sie mit Data Warehouse Manager relevante Datenfelder einfach für die Analyse verfolgen können.
exl-id: b0085683-7bb1-4da2-b343-4309e4796f0c
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Erwartet [!DNL Google Adwords] data

Nachher [Sie haben Ihre [!DNL Google Adwords] account](../integrations/google-adwords.md), können Sie die [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse.

Dort sind zwei Tabellen für die Replikation in Ihrer Data Warehouse verfügbar:

* `campaigns[account-id]`
* `adwords[account-id]`

Die `campaigns` table *sollte standardmäßig verwendet werden*, damit Sie mit der Synchronisierung aller relevanten Felder aus dieser Tabelle beginnen können.

Die `adwords` -Tabelle enthält vier Spalten, die nicht im `campaigns` table:

1. `keyword`
1. `adContent`
1. `adDestinationUrl`
1. `adGroup`

Wenn Sie eine Analyse durchführen möchten, die diese Attribute berücksichtigt, müssen Sie die `adwords` Tabelle.

>[!IMPORTANT]
>
>Diese Tabelle schließt Zeilen aus, in denen alle vier dieser Spalten `null`.

Im Folgenden finden Sie einen Überblick über das erwartete Schema für beide Tabellen.

## [!DNL Campaigns] table

Die `campaigns` enthält die folgenden Spalten:

| **Spalte** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adwordscampaignid) | [!DNL Adwords] Kampagnen-ID |
| [`campaign`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=traffic_sources&amp;jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=time&amp;jump=ga_date) | Das Datum, an dem die Kampagne ausgeführt wurde |
| [`impressions`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |

{style="table-layout:auto"}

## [!DNL AdWords] table

Die `adwords` enthält die folgenden Spalten:

| **Spalte** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_adwordscampaignid) | [!DNL Adwords] Kampagnen-ID |
| [`campaign`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=traffic_sources&amp;jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=time&amp;jump=ga_date) | Das Datum, an dem die Kampagne ausgeführt wurde |
| [`impressions`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&amp;group=adwords&amp;jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |
| `keyword` | Der Suchbegriff der Kampagne |
| `adContent` | Die erste Zeile des Textes für die Online-Kampagne |
| `adDestinationUrl` | Die URL, zu der die [!DNL Adwords] Anzeigen auf Traffic |
| `adGroup` | Der Name der [!DNL Adwords] Anzeigengruppe |

{style="table-layout:auto"}

Mithilfe dieser Daten können Sie mit der Erstellung von [Metriken](../../../data-user/reports/ess-manage-data-metrics.md) und [Berichte](../../../tutorials/using-visual-report-builder.md) auf der Grundlage der Ausgabedaten und [ihn mit Ihrem Lebensdauerumsatz zu verbinden, um den ROI zu berechnen](../../analysis/roi-ad-camp.md).

## Konsolidierte Tabellen

[!DNL Adobe] empfiehlt, eine `consolidated ad spend` -Tabelle verwenden, um die Daten aus all Ihren verschiedenen Werbequellen in einer einzigen Tabelle zu kombinieren. Auf diese Weise können Sie einen einzigen Metriksatz für die Werbeanalyse verwenden.

Wenn Sie keine konsolidierte Tabelle haben und ein schönes Dashboard auf der `adwords` müssen Sie die Berichterstellung replizieren oder doppelte Metriken erstellen, um diese Daten mit Ihren [!DNL Facebook Ads] Daten. Mithilfe einer konsolidierten Tabelle können Sie nahtlos Folgendes integrieren: [!DNL Facebook Ads] mit vorhandenen [!DNL Adwords] Berichte. Sie können auch nach Anzeigenplattform segmentieren.

Wenn Sie die oben genannten Felder bereits synchronisiert haben, [Kontakt](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) um Ihre Werbeausgaben zu konsolidieren.
