---
title: Erwartete Facebook Ads-Daten
description: Hier erhalten Sie einen kurzen Überblick über die Tabellen, für die eine Synchronisierung mit Ihrer Data Warehouse empfohlen wird.
exl-id: 0c8b907b-1a98-470b-bb2c-55327e88e502
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Erwartet [!DNL Facebook Ads] data

Nachdem Sie [mit [!DNL Facebook Ads] account](../integrations/facebook-ads.md), können Sie die [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse.

In diesem Thema erhalten Sie einen kurzen Überblick über die Tabellen. Die Adobe empfiehlt die Synchronisierung mit Ihrer Data Warehouse. Hier werden nur die Kerntabellen hervorgehoben, da es einige Untertabellen gibt.

## Kernkampagnentabellen

Diese Tabellen enthalten Daten zu Kernkomponenten der Anzeigenkampagne.

### [`facebook _campaigns_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign-group)

Diese Tabelle enthält die Kerntabelle der Kampagnen in einer [!DNL Facebook Ads] -Konto. Spalten enthalten `campaign id`, `name`, `status (active/paused)`, `objective`.

### [`facebook _adsets_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign)

Dieser Tabellendatensatz ist die Kerntabelle von [!DNL Facebook Ads] Sets in [!DNL Facebook Ads] -Konto. Spalten beinhalten die Anzeige `Campaign id/name` das Anzeigenset gehört, die Budgetierung, den Angebotstyp, die Planung und die Zielgruppen-Targeting-Informationen.

### [`facebook _ads_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/adgroup)

Diese Tabelle enthält alle Anzeigen in einer [!DNL Facebook Ads] -Konto. Die Spalten enthalten die Anzeigeninformationen, darunter das Anzeigenset und die Anzeigenkampagne, zu der es gehört, das Anzeigenangebot, das Anzeigen-Targeting und den Verweis auf bestimmte kreative Inhalte (Bild/Text), die von der Anzeige verwendet werden.

### [`facebook _adcreative_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-creative)

In dieser Tabelle werden kreative Elemente aufgeführt, die in [!DNL Facebook Ads]. Kreative Elemente umfassen ggf. kreative Namen, Beschreibungen und relevante Bild-URLs.

## Segmentierte Kampagnentabellen

Die folgenden Tabellen enthalten einen Eintrag für jede Kombination aus Kampagne/Satz/Anzeige für jeden Tag, segmentiert nach Dimensionen wie Alter, Geschlecht und Land.

### `facebook _ads insights_ (account-id)`

Diese Tabelle enthält einen Eintrag für jede Kombination aus Kampagne/Satz/Anzeige für jeden Tag, zusammen mit Statistiken wie Impressionen, Klicks, Kosten, cpc, cpm, cpp, ctr, Reichweite, soziale Reichweite und Ausgaben.

### `facebook _ads insights_ (account-id)_~\_actions`

Dies ist eine Untertabelle der `facebook_ads_insights_{account_id}` Tabelle. Sie enthält Konversionsdaten für Aktionen, die basierend auf verschiedenen Kampagnen durchgeführt werden.

### `facebook _ads insights country_ (account-id)`

Diese Tabelle enthält dieselben Informationen wie die `facebook_ads_insights_{account_id}` -Tabelle und segmentiert sie nach Land.

### `facebook ads insights age and gender (account-id)`

Diese Tabelle enthält dieselben Informationen wie die `facebook_ads_insights_{account_id}` und segmentiert sie nach Alter und Geschlecht.

## Verwandte

* [Verbinden [!DNL Facebook Ads]](../integrations/facebook-ads.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
