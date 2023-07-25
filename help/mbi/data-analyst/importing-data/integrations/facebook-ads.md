---
title: Verbinden von Facebook-Anzeigen
description: Erfahren Sie, wie Sie Ihre Anzeigenausgabedaten analysieren und feststellen können, ob Ihr Geld effektiv ausgegeben wird.
exl-id: 219a868b-f17c-4299-9e29-94db9156c9b6
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Verbinden [!DNL Facebook Ads]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/facebook-ads-logo.png)

Sie haben Ihre Forschung durchgeführt, Ihre Anzeigen erstellt, Ihre Kampagne gestartet, [!DNL Facebook]. Jetzt ist es an der Zeit, Ihre Anzeigenausgabedaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mithilfe Ihrer Anzeigenausgabedaten können Sie [Messen Sie den Kampagnen-ROI durch die Verknüpfung Ihrer Werbe- und des Kundenlebenszeitwerts (CLV).](../../../data-analyst/analysis/roi-ad-camp.md) der Benutzer, die durch Ihre Kampagnen erworben wurden.

Verbinden Ihrer [!DNL Facebook Ad] Daten an [!DNL Commerce Intelligence] ist ein einfacher dreistufiger Prozess:

1. [Hinzufügen [!DNL Facebook] als Datenquelle in [!DNL Commerce Intelligence]](#stepone)
1. [Zulassen [!DNL Commerce Intelligence] Zugriff auf Ihre [!DNL Facebook Ads] data](#steptwo)
1. [Auswählen [!DNL Facebook Ads] Konten zum Abrufen von Daten](#stepthree)

## Hinzufügen [!DNL Facebook] als Datenquelle in [!DNL Commerce Intelligence] {#stepone}

1. So fügen Sie die [!DNL Facebook] Integration in Ihre [!DNL Commerce Intelligence]-Konto, navigieren Sie zum `Connections` Seite unter **[!UICONTROL Manage Data** > **Integrations]**.
1. Klicken **[!UICONTROL Add Integration]**, auf der rechten Seite.
1. Klicken Sie auf [!DNL Facebook] Symbol. Dadurch wird die [!DNL Facebook] Autorisierungsseite.
1. Klicken **[!UICONTROL Authorize]**.

## Zulassen [!DNL Commerce Intelligence] Zugriff auf Ihre [!DNL Facebook Ads] data {#steptwo}

Nach dem Klicken **[!DNL Facebook Authorize]**, wird ein kleines Popup-Fenster angezeigt:

![](../../../assets/Facebook_Access_Popup.png)

Führen Sie eine Reihe von Schritten aus, um [!DNL Commerce Intelligence] , um auf Daten aus Ihrem öffentlichen Profil zuzugreifen, [!DNL Facebook Ads] und zugehörige Statistiken. Klicken **[!UICONTROL OK]** auf diese Schritte folgen, um fortzufahren.

## Auswählen [!DNL Facebook Ads] Konten zum Abrufen von Daten {#stepthree}

1. Nach Abschluss der Authentifizierung werden Sie aufgefordert, die [!DNL Facebook Ads] Konten, aus denen Sie Daten abrufen möchten. Wählen Sie die gewünschten Konten aus, indem Sie auf das Kontrollkästchen im `Connect` Spalte.

   ![](../../../assets/Facebook_Ad_Accounts.png)

1. Klicken **[!UICONTROL Save Connections]**.

   Wenn die Verbindung erfolgreich hergestellt wurde, wird ein *Verbindung erfolgreich!* wird oben auf der Seite angezeigt.

## Wie geht es weiter? {#next}

Vergewissern Sie sich, dass Sie das Tracking durchführen [!DNL Facebook] Kampagnen in [!DNL Google Analytics]. Dadurch wird sichergestellt, dass `utm\_campaign` -Feld in [!DNL Google Analytics] für Ihre [!DNL Facebook] Kampagnen.

## Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verbinden Sie Ihre [!DNL Google Adwords] account](../integrations/google-ecommerce.md)
* [Verweisquelle für Bestellungen verfolgen über [!DNL Google eCommerce]](../integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](../../analysis/track-usr-dev-browser.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Erhöhen Sie den ROI Ihrer Werbekampagnen.](../../analysis/roi-ad-camp.md)
* [Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../../analysis/utm-attributes.md)
