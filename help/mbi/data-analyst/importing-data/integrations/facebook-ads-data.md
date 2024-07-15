---
title: Erwartete Facebook Ads-Daten
description: Hier erhalten Sie einen kurzen Überblick über die Tabellen, für die eine Synchronisierung mit Ihrer Data Warehouse empfohlen wird.
exl-id: 0c8b907b-1a98-470b-bb2c-55327e88e502
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Erwartete [!DNL Facebook Ads] Daten

Nachdem Sie [ mit Ihrem [!DNL Facebook Ads] Konto](../integrations/facebook-ads.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

Dieses Thema gibt Ihnen einen kurzen Überblick über die Tabellen, die Adobe empfiehlt, mit Ihrer Data Warehouse zu synchronisieren. Hier werden nur die Kerntabellen hervorgehoben, da es einige Untertabellen gibt.

## Kernkampagnentabellen

Diese Tabellen enthalten Daten zu Kernkomponenten der Anzeigenkampagne.

### [`facebook _campaigns_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign-group)

Diese Tabelle ist die Kerntabelle der Kampagnen eines [!DNL Facebook Ads] -Kontos. Die Spalten umfassen `campaign id`, `name`, `status (active/paused)`, `objective`.

### [`facebook _adsets_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign)

Dieser Tabellendatensatz ist die Kerntabelle der [!DNL Facebook Ads] Sets in einem [!DNL Facebook Ads] -Konto. Zu den Spalten gehören die Anzeige &quot;`Campaign id/name`&quot;, zu der das Anzeigenset gehört, die Budgetierung, der Angebotstyp, die Planung und die Zielgruppen-Targeting-Informationen.

### [`facebook _ads_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/adgroup)

Diese Tabelle zeichnet alle Anzeigen in einem [!DNL Facebook Ads] -Konto auf. Die Spalten enthalten die Anzeigeninformationen einschließlich des Anzeigensets und der Anzeigenkampagne, zu der es gehört, das Anzeigenangebot, das Anzeigen-Targeting und den Verweis auf bestimmte kreative Inhalte (Bild/Text), die von der Anzeige verwendet werden.

### [`facebook _adcreative_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-creative)

In dieser Tabelle werden kreative Elemente aufgezeichnet, die in [!DNL Facebook Ads] verwendet werden. Kreative Elemente umfassen ggf. kreative Namen, Beschreibungen und relevante Bild-URLs.

## Segmentierte Kampagnentabellen

Die folgenden Tabellen enthalten einen Eintrag für jede Kombination aus Kampagne/Satz/Anzeige für jeden Tag, segmentiert nach Dimensionen wie Alter, Geschlecht und Land.

### `facebook _ads insights_ (account-id)`

Diese Tabelle enthält einen Eintrag für jede Kombination aus Kampagne/Satz/Anzeige für jeden Tag, zusammen mit Statistiken wie Impressionen, Klicks, Kosten, cpc, cpm, cpp, ctr, Reichweite, soziale Reichweite und Ausgaben.

### `facebook _ads insights_ (account-id)_~\_actions`

Dies ist eine Untertabelle der `facebook_ads_insights_{account_id}` -Tabelle. Sie enthält Konversionsdaten für Aktionen, die basierend auf verschiedenen Kampagnen durchgeführt werden.

### `facebook _ads insights country_ (account-id)`

Diese Tabelle enthält dieselben Informationen wie die Tabelle `facebook_ads_insights_{account_id}` und segmentiert sie nach Land.

### `facebook ads insights age and gender (account-id)`

Diese Tabelle enthält dieselben Informationen wie die Tabelle `facebook_ads_insights_{account_id}` und segmentiert sie nach Alter und Geschlecht.

## Verwandte

* [Verbinden [!DNL Facebook Ads]](../integrations/facebook-ads.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
