---
title: Erwartete Daten von Facebook-Anzeigen
description: Erfahren Sie einen kurzen Überblick über die Tabellen, die Sie mit Ihrer Data Warehouse synchronisieren sollten
exl-id: 0c8b907b-1a98-470b-bb2c-55327e88e502
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/LBpqIMm4nGx-Vu-zxw-iPLgNg1yfDsYi0yDyFHCyxvA
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: c8d7097b4f841a4fe8c5777f207ea0ea53202a0f
workflow-type: tm+mt
source-wordcount: 342
ht-degree: 0%

---

# Erwartete [!DNL Facebook Ads]

Nachdem Sie [Ihr [!DNL Facebook Ads] Konto](../integrations/facebook-ads.md) verbunden haben, können Sie den [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen.

In diesem Abschnitt erhalten Sie einen kurzen Überblick über die Tabellen, die Adobe zum Synchronisieren mit Data Warehouse empfiehlt. Dies hebt nur die Kerntabellen hervor, da es einige Untertabellen gibt.

## Zentrale Anzeigenkampagnentabellen

Diese Tabellen enthalten Daten zu Kern- und Kampagnenkomponenten.

### `facebook _campaigns_ (account-id)`

[`facebook _campaigns_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign-group)

Diese Tabelle stellt die Kerntabelle der Kampagnen eines [!DNL Facebook Ads] dar. Die Spalten umfassen `campaign id`, `name`, `status (active/paused)`, `objective`.

### `facebook _adsets_ (account-id)`

[`facebook _adsets_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-campaign)

Dieser Tabelleneintrag ist die Kerntabelle der [!DNL Facebook Ads] in einem [!DNL Facebook Ads]. Spalten enthalten die Anzeige, `Campaign id/name` der der Anzeigensatz gehört, die Budgetierung, den Bid-Typ, die Planung und Informationen zur Zielgruppenbestimmung.

### `facebook _ads_ (account-id)`

[`facebook _ads_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/adgroup)

In dieser Tabelle werden alle Anzeigen in einem [!DNL Facebook Ads]-Konto aufgezeichnet. Die Spalten enthalten die Anzeigeninformationen einschließlich des Anzeigensatzes und der Anzeigenkampagne, zu der er gehört, des Anzeigengebots und des Anzeigen-Targeting und des Verweises auf bestimmte kreative Elemente (Bild/Text), die die Anzeige verwendet.

### `facebook _adcreative_ (account-id)`

[`facebook _adcreative_ (account-id)`](https://developers.facebook.com/docs/marketing-api/reference/ad-creative)

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
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
