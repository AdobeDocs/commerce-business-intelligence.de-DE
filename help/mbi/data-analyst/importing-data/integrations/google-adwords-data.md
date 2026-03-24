---
title: Erwartete Google AdWords-Daten
description: Erfahren Sie, wie Sie mit Data Warehouse Manager relevante Datenfelder für die Analyse einfach verfolgen können.
exl-id: b0085683-7bb1-4da2-b343-4309e4796f0c
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/iCKOCRAELybmKfHS8F7XaKpEx9blpkRK0i0e-eEYJgU
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 436
ht-degree: 0%

---

# Erwartete [!DNL Google Adwords]

Nachdem [Sie Ihr [!DNL Google Adwords] Konto verbunden haben](../integrations/google-adwords.md) können Sie den [Data Warehouse Manager](../../data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

Dort werden Sie feststellen, dass zwei Tabellen für die Replikation in Ihre Data Warehouse verfügbar sind:

* `campaigns[account-id]`
* `adwords[account-id]`

Die `campaigns` Tabelle *sollte standardmäßig verwendet werden* sodass Sie mit der Synchronisierung aller relevanten Felder aus dieser Tabelle beginnen können.

Die `adwords` Tabelle enthält vier Spalten, die nicht in der `campaigns` Tabelle enthalten sind:

1. `keyword`
1. `adContent`
1. `adDestinationUrl`
1. `adGroup`

Wenn Sie an einer Analyse interessiert sind, die diese Attribute berücksichtigt, müssen Sie die `adwords` verwenden.

>[!IMPORTANT]
>
>Diese Tabelle schließt Zeilen aus, in denen alle vier dieser Spalten `null` sind.

Nachfolgend finden Sie einen Überblick über das erwartete Schema für beide Tabellen.

## [!DNL Campaigns]

Die `campaigns` Tabelle enthält die folgenden Spalten:

| **Spalte** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_adwordscampaignid) | Kampagnen-ID [!DNL Adwords] |
| [`campaign`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=traffic_sources&jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=time&jump=ga_date) | Das Datum, an dem die Kampagne ausgeführt wurde |
| [`impressions`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |

{style="table-layout:auto"}

## [!DNL AdWords]

Die `adwords` Tabelle enthält die folgenden Spalten:

| **Spalte** | **Beschreibung** |
|-----|-----|
| `\_id` | Der Primärschlüssel für die Tabelle |
| `accountId` | Die Konto-ID |
| [`adClicks`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_adclicks) | Gesamtzahl der Klicks für den Tag |
| [`adCost`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_adcost) | Gesamtkosten der Kampagne für den Tag |
| [`adwordsCampaignID`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_adwordscampaignid) | Kampagnen-ID [!DNL Adwords] |
| [`campaign`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=traffic_sources&jump=ga_campaign) | Kampagnenname (z. B. [utm\_campaign](https://support.google.com/analytics/answer/1033867?hl=en)) |
| [`date`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=time&jump=ga_date) | Das Datum, an dem die Kampagne ausgeführt wurde |
| [`impressions`](https://ga-dev-tools.google/dimensions-metrics-explorer/#view=detail&group=adwords&jump=ga_impressions) | Anzahl der Impressionen für den Tag |
| `profileId` | Die Profil-ID |
| `profileName` | Der Profilname |
| `\_updated\_at` | Datum und Uhrzeit der letzten Aktualisierung für diese Zeile |
| `keyword` | Das Keyword der Kampagne |
| `adContent` | Die erste Zeile des Textes der Online-Kampagne |
| `adDestinationUrl` | Die URL, auf die sich die [!DNL Adwords]-Anzeigen auf den Traffic bezogen haben |
| `adGroup` | Der Name der [!DNL Adwords] Anzeigengruppe |

{style="table-layout:auto"}

Mithilfe dieser Daten können Sie mit der Erstellung von [Metriken](../../../data-user/reports/ess-manage-data-metrics.md) und [Berichten](../../../tutorials/using-visual-report-builder.md) auf der Grundlage von Ausgabendaten beginnen und [diese mit Ihrem Lebensdauerumsatz zu verbinden, um den ROI zu ](../../analysis/roi-ad-camp.md).

## Konsolidierte Tabellen

[!DNL Adobe] wird empfohlen, eine `consolidated ad spend` zu erstellen, um die Daten aus allen Ihren Werbequellen in einer einzigen Tabelle zu kombinieren. Auf diese Weise können Sie einen einzigen Satz von Metriken für die Werbeanalyse verwenden.

Wenn Sie keine konsolidierte Tabelle haben und ein schönes Dashboard auf der `adwords` erstellen, müssen Sie die Berichte replizieren oder doppelte Metriken erstellen, um diese Daten mit Ihren [!DNL Facebook Ads] zu vergleichen. Durch die Verwendung einer konsolidierten Tabelle können Sie [!DNL Facebook Ads] Daten nahtlos in Ihre vorhandenen [!DNL Adwords] Berichte integrieren. Sie können auch nach Anzeigenplattform segmentieren.

Wenn Sie die oben genannten Felder bereits synchronisiert haben, [ Sie uns ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um Ihre Werbeausgaben zu konsolidieren.
