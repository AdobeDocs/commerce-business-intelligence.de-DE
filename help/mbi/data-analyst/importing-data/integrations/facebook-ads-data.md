---
title: Erwartete Daten von Facebook-Anzeigen
description: Erfahren Sie einen kurzen Überblick über die Tabellen, die Sie mit Ihrer Data Warehouse synchronisieren sollten
exl-id: 0c8b907b-1a98-470b-bb2c-55327e88e502
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Erwartete [!DNL Facebook Ads]

Nachdem Sie [Ihr [!DNL Facebook Ads] Konto](../integrations/facebook-ads.md) verbunden haben, können Sie den [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Abschnitt erhalten Sie einen kurzen Überblick über die Tabellen, die Adobe zum Synchronisieren mit Data Warehouse empfiehlt. Dies hebt nur die Kerntabellen hervor, da es einige Untertabellen gibt.

## Zentrale Anzeigenkampagnentabellen

Diese Tabellen enthalten Daten zu Kern- und Kampagnenkomponenten.

### [`facebook _campaigns_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign-group)

Diese Tabelle stellt die Kerntabelle der Kampagnen eines [!DNL Facebook Ads] dar. Die Spalten umfassen `campaign id`, `name`, `status (active/paused)`, `objective`.

### [`facebook _adsets_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign)

Dieser Tabelleneintrag ist die Kerntabelle der [!DNL Facebook Ads] in einem [!DNL Facebook Ads]. Spalten enthalten die Anzeige, `Campaign id/name` der der Anzeigensatz gehört, die Budgetierung, den Bid-Typ, die Planung und Informationen zur Zielgruppenbestimmung.

### [`facebook _ads_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/adgroup)

In dieser Tabelle werden alle Anzeigen in einem [!DNL Facebook Ads]-Konto aufgezeichnet. Die Spalten enthalten die Anzeigeninformationen einschließlich des Anzeigensatzes und der Anzeigenkampagne, zu der er gehört, des Anzeigengebots und des Anzeigen-Targeting und des Verweises auf bestimmte kreative Elemente (Bild/Text), die die Anzeige verwendet.

### [`facebook _adcreative_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-creative)

Diese Tabelle zeichnet Kreative auf, die in [!DNL Facebook Ads] verwendet werden. Creatives umfasst kreativen Namen, Beschreibung und relevante Bild-URLs, wo zutreffend.

## Segmentierte Kampagnentabellen

Die folgenden Tabellen enthalten einen Eintrag für jede Kombination aus Kampagne/Set/Anzeige für jeden Tag, segmentiert nach Dimensionen wie Alter, Geschlecht und Land.

### `facebook _ads insights_ (account-id)`

Diese Tabelle enthält einen Eintrag für jede Kombination aus Kampagne/Set/Anzeige für jeden Tag zusammen mit Statistiken einschließlich Impressionen, Klicks, Kosten, CPC, CPM, CPP, CTR, Reichweite, sozialer Reichweite und Ausgaben.

### `facebook _ads insights_ (account-id)_~\_actions`

Dies ist eine Untertabelle der `facebook_ads_insights_{account_id}`. Sie enthält Konversionsdaten für Aktionen, die auf der Grundlage verschiedener Kampagnen durchgeführt werden.

### `facebook _ads insights country_ (account-id)`

Diese Tabelle enthält dieselben Informationen wie die `facebook_ads_insights_{account_id}` Tabelle und segmentiert sie nach Land.

### `facebook ads insights age and gender (account-id)`

Diese Tabelle enthält dieselben Informationen wie die `facebook_ads_insights_{account_id}` Tabelle und segmentiert sie nach Alter und Geschlecht.

## verwandt

* [Verbinden [!DNL Facebook Ads]](../integrations/facebook-ads.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
