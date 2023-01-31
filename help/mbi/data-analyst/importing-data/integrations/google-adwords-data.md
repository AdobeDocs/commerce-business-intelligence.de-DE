---
title: Erwartete Google Adwords-Daten
description: Erfahren Sie, wie Sie mit Data Warehouse Manager relevante Datenfelder einfach für die Analyse verfolgen können.
exl-id: b0085683-7bb1-4da2-b343-4309e4796f0c
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Erwartete Google Adwords-Daten

Nachher [Sie haben Ihre [!DNL Google Adwords] account](../integrations/google-adwords.md), können Sie die [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse.

Dort sind zwei Tabellen für die Replikation in Ihrem Data Warehouse verfügbar: `campaigns[account-id]` und `adwords[account-id]`.

Die `campaigns` table *sollte standardmäßig verwendet werden*, damit Sie mit der Synchronisierung aller relevanten Felder aus dieser Tabelle beginnen können.

Die `adwords` -Tabelle enthält vier Spalten, die nicht im `campaigns` table:

* `keyword`
* `adContent`
* `adDestinationUrl`
* `adGroup`

Wenn Sie eine Analyse durchführen möchten, die diese Attribute berücksichtigt, müssen Sie die `adwords` Tabelle.

>[!IMPORTANT]
>
>Diese Tabelle schließt Zeilen aus, bei denen alle vier dieser Spalten `null`.

Im Folgenden finden Sie einen Überblick über das erwartete Schema für beide Tabellen:

## `Campaigns` table

Die `campaigns` enthält die folgenden Spalten:

| **Spalte** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_adwordscampaignid) | [!DNL Adwords] Kampagnen-ID |
| [`campaign`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=traffic_sources&amp;jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=time&amp;jump=ga_date) | Das Datum, an dem die Kampagne ausgeführt wurde |
| [`impressions`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |

{style=&quot;table-layout:auto&quot;}

## AdWords-Tabelle

Die `adwords` enthält die folgenden Spalten:

| **Spalte** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_adwordscampaignid) | [!DNL Adwords] Kampagnen-ID |
| [`campaign`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=traffic_sources&amp;jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=time&amp;jump=ga_date) | Das Datum, an dem die Kampagne ausgeführt wurde |
| [`impressions`](https://developers.google.com/analytics/devguides/reporting/core/dimsmets#view=detail&amp;group=adwords&amp;jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |
| `keyword` | Der Suchbegriff der Kampagne |
| `adContent` | Die erste Zeile des Textes für die Online-Kampagne |
| `adDestinationUrl` | Die URL, zu der die [!DNL Adwords] Anzeigen auf Traffic |
| `adGroup` | Der Name der [!DNL Adwords] Anzeigengruppe |

{style=&quot;table-layout:auto&quot;}

Mithilfe dieser Daten können Sie mit der Erstellung von [Metriken ](../../../data-user/reports/ess-manage-data-metrics.md) und [Berichte](../../../tutorials/using-visual-report-builder.md) auf der Grundlage der Ausgabedaten und [ihn mit Ihrem Lebensdauerumsatz zu verbinden, um den ROI zu berechnen](../../analysis/roi-ad-camp.md).

## Konsolidierte Tabellen

Es wird immer empfohlen, eine `consolidated ad spend` -Tabelle verwenden, um die Daten aus all Ihren verschiedenen Werbequellen in einer einzigen Tabelle zu kombinieren. Auf diese Weise können Sie einen einzigen Metriksatz für die Werbeanalyse verwenden.

Ohne eine konsolidierte Tabelle, wenn Sie ein schönes Dashboard auf der `adwords` müssen Sie die Berichterstellung replizieren oder doppelte Metriken erstellen, um diese Daten mit Ihren [!DNL Facebook Ads] Daten. Mithilfe einer konsolidierten Tabelle können Sie nahtlos Folgendes integrieren: [!DNL Facebook Ads] mit vorhandenen [!DNL Adwords] Berichte. (Machen Sie sich keine Gedanken - Sie können auch nach Anzeigenplattform segmentieren!)

Wenn Sie die oben genannten Felder bereits synchronisiert haben, wenden Sie sich an uns, um Ihre Werbeausgaben zu konsolidieren.
