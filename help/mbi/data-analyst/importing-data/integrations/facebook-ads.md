---
title: Facebook-Anzeigen verbinden
description: Erfahren Sie, wie Sie Ihre Anzeigenausgabendaten analysieren und feststellen können, ob Ihr Geld effektiv ausgegeben wird.
exl-id: 219a868b-f17c-4299-9e29-94db9156c9b6
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/6TR559YyeTHT3KWl3oA4Bdnpr-HCowTXTTkvmP0I0tg
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: bd989d82-1e15-4534-88db-f1f51dd77ffa
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 0%

---

# [!DNL Facebook Ads] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Facebook Ads-Logo](../../../assets/facebook-ads-logo.png)

Sie haben recherchiert, Ihre Anzeigen erstellt und Ihre Kampagne auf [!DNL Facebook] gestartet. Jetzt ist es an der Zeit, Ihre Anzeigenausgabendaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mit Ihren Werbeausgabendaten können Sie [Kampagnen-ROI messen, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (Customer Lifetime Value, CLV) der ](../../../data-analyst/analysis/roi-ad-camp.md) Ihrer Kampagnen erworbenen Benutzer zusammenfassen.

Die Verbindung Ihrer [!DNL Facebook Ad] mit [!DNL Commerce Intelligence] ist ein einfacher dreistufiger Prozess:

1. [ [!DNL Facebook]  als Datenquelle hinzufügen in [!DNL Commerce Intelligence]](#stepone)
1. [ [!DNL Commerce Intelligence]  Zugriff auf Ihre  [!DNL Facebook Ads]  zulassen](#steptwo)
1. [Select [!DNL Facebook Ads] Accounts für Datenabruf](#stepthree)

## Hinzufügen von [!DNL Facebook] als Datenquelle in [!DNL Commerce Intelligence] {#stepone}

1. Um die [!DNL Facebook]-Integration zu Ihrem -[!DNL Commerce Intelligence] hinzuzufügen, gehen Sie zur Seite `Connections` unter **[!UICONTROL Manage Data** > **Integrations]**.
1. Klicken Sie rechts auf **[!UICONTROL Add Integration]** .
1. Klicken Sie auf das Symbol [!DNL Facebook] . Dadurch wird die [!DNL Facebook] Autorisierungsseite angezeigt.
1. Klicken Sie auf **[!UICONTROL Authorize]**.

## [!DNL Commerce Intelligence] Zugriff auf [!DNL Facebook Ads] Daten zulassen {#steptwo}

Nach dem Klicken auf **[!DNL Facebook Authorize]** wird ein kleines Popup-Fenster angezeigt:

![Dialogfeld für Facebook-Zugriffsberechtigungen für Commerce Intelligence](../../../assets/Facebook_Access_Popup.png)

Sie führen eine Reihe von Schritten aus, um [!DNL Commerce Intelligence] den Zugriff auf Daten aus Ihrem öffentlichen Profil, [!DNL Facebook Ads] und verwandten Statistiken zu ermöglichen. Klicken Sie auf **[!UICONTROL OK]** Schritte, um fortzufahren.

## [!DNL Facebook Ads] Konten zum Abrufen von Daten auswählen {#stepthree}

1. Nach Abschluss der Authentifizierung werden Sie aufgefordert, die [!DNL Facebook Ads] Konten auszuwählen, von denen Sie Daten abrufen möchten. Wählen Sie die gewünschten Konten aus, indem Sie in der Spalte `Connect` auf das Kontrollkästchen klicken.

   ![Benutzeroberfläche zur Auswahl von Facebook-Werbekonten](../../../assets/Facebook_Ad_Accounts.png)

1. Klicken Sie auf **[!UICONTROL Save Connections]**.

   Wenn die Verbindung erfolgreich hergestellt wurde, wählen Sie *Verbindung erfolgreich!* Nachricht wird oben auf der Seite angezeigt.

## Wie geht es weiter? {#next}

Vergewissern Sie sich, dass Sie [!DNL Facebook] Kampagnen in [!DNL Google Analytics] verfolgen. Dadurch wird sichergestellt, dass das `utm\_campaign` Feld in [!DNL Google Analytics] für Ihre [!DNL Facebook] Kampagnen ordnungsgemäß ausgefüllt ist.

## verwandt

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Konto  [!DNL Google Adwords] ](../integrations/google-ecommerce.md)
* [Verfolgen Sie die Quelle der Bestellungsreferenz über [!DNL Google eCommerce]](../integrations/google-ecommerce.md)
* [Verfolgen Sie die Quelle der Benutzerreferenz in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Benutzergeräte-, Browser- und Betriebssystemdaten in der Datenbank tracken](../../analysis/track-usr-dev-browser.md)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI Ihrer Werbekampagnen](../../analysis/roi-ad-camp.md)
* [Wie funktioniert  [!DNL Google Analytics]  UTM-Attribution?](../../analysis/utm-attributes.md)
