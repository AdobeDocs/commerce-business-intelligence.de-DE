---
title: Verbinden von Facebook-Anzeigen
description: Erfahren Sie, wie Sie Ihre Anzeigenausgabedaten analysieren und feststellen können, ob Ihr Geld effektiv ausgegeben wird.
exl-id: 219a868b-f17c-4299-9e29-94db9156c9b6
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# [!DNL Facebook Ads] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/facebook-ads-logo.png)

Sie haben Ihre Forschung durchgeführt, Ihre Anzeigen erstellt und Ihre Kampagne am [!DNL Facebook] gestartet. Jetzt ist es an der Zeit, Ihre Anzeigenausgabedaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mithilfe Ihrer Anzeigenausgabedaten können Sie den ROI Ihrer Kampagne [messen, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (CLV)](../../../data-analyst/analysis/roi-ad-camp.md) der durch Ihre Kampagnen erworbenen Benutzer miteinander verbinden.

Das Verbinden Ihrer [!DNL Facebook Ad] -Daten mit [!DNL Commerce Intelligence] ist ein einfacher dreistufiger Prozess:

1. [Hinzufügen von [!DNL Facebook] als Datenquelle in  [!DNL Commerce Intelligence]](#stepone)
1. [Ermöglichen des Zugriffs von [!DNL Commerce Intelligence] auf Ihre [!DNL Facebook Ads] Daten](#steptwo)
1. [Auswählen von [!DNL Facebook Ads] Konten zum Abrufen von Daten](#stepthree)

## Hinzufügen von [!DNL Facebook] als Datenquelle in [!DNL Commerce Intelligence] {#stepone}

1. Um die Integration [!DNL Facebook] zu Ihrem [!DNL Commerce Intelligence]Konto hinzuzufügen, navigieren Sie zur Seite `Connections` unter **[!UICONTROL Manage Data** > **Integrations]**.
1. Klicken Sie rechts auf &quot;**[!UICONTROL Add Integration]**&quot;.
1. Klicken Sie auf das Symbol &quot;[!DNL Facebook]&quot;. Dadurch wird die Seite mit der [!DNL Facebook] -Autorisierung angezeigt.
1. Klicken Sie auf **[!UICONTROL Authorize]**.

## [!DNL Commerce Intelligence] Zugriff auf Ihre [!DNL Facebook Ads] -Daten zulassen {#steptwo}

Nach dem Klicken auf **[!DNL Facebook Authorize]** wird ein kleines Popup-Fenster angezeigt:

![](../../../assets/Facebook_Access_Popup.png)

Führen Sie eine Reihe von Schritten aus, um [!DNL Commerce Intelligence] den Zugriff auf Daten aus Ihrem öffentlichen Profil, [!DNL Facebook Ads] und den zugehörigen Statistiken zu ermöglichen. Klicken Sie auf &quot;**[!UICONTROL OK]**&quot;, um fortzufahren.

## Auswählen von [!DNL Facebook Ads] Konten zum Abrufen von Daten {#stepthree}

1. Nach Abschluss der Authentifizierung werden Sie aufgefordert, die [!DNL Facebook Ads] Konten auszuwählen, aus denen Sie Daten abrufen möchten. Wählen Sie die gewünschten Konten aus, indem Sie auf das Kontrollkästchen in der Spalte `Connect` klicken.

   ![](../../../assets/Facebook_Ad_Accounts.png)

1. Klicken Sie auf **[!UICONTROL Save Connections]**.

   Wenn die Verbindung erfolgreich hergestellt wurde, ist eine *Verbindung erfolgreich!Die Meldung* wird oben auf der Seite angezeigt.

## Wie geht es weiter? {#next}

Vergewissern Sie sich, dass Sie [!DNL Facebook]-Kampagnen in [!DNL Google Analytics] verfolgen. Dadurch wird sichergestellt, dass das Feld `utm\_campaign` in [!DNL Google Analytics] für Ihre [!DNL Facebook]-Kampagnen ordnungsgemäß ausgefüllt ist.

## Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [ [!DNL Google Adwords] Konto verbinden](../integrations/google-ecommerce.md)
* [Verweisquelle für Bestellungen über  [!DNL Google eCommerce] verfolgen](../integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](../../analysis/track-usr-dev-browser.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI bei Werbekampagnen](../../analysis/roi-ad-camp.md)
* [Wie funktioniert die  [!DNL Google Analytics] UTM-Attribution?](../../analysis/utm-attributes.md)
