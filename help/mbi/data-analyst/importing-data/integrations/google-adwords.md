---
title: Google Adwords verbinden
description: Erfahren Sie, wie Sie den ROI Ihrer Kampagne messen können, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (CLV) der durch Ihre Kampagnen erworbenen Benutzer miteinander verbinden.
exl-id: db99f817-2a2e-4194-9dd2-ec2d6b27a118
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Verbinden [!DNL Google Adwords]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Google_Adwords_logo.png)

Sie haben Ihre Recherchen durchgeführt, Ihre Anzeigen erstellt und Ihre Kampagne gestartet. Jetzt ist es an der Zeit, Ihre Anzeigenausgabedaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mithilfe Ihrer Anzeigenausgabedaten können Sie [Messen Sie den Kampagnen-ROI durch die Verknüpfung Ihrer Werbe- und des Kundenlebenszeitwerts (CLV).](../../analysis/roi-ad-camp.md) der Benutzer, die durch Ihre Kampagnen erworben wurden.

Beginnen wir mit der Eingabe von [!DNL Google Adwords] Anmeldedaten [!DNL MBI]:

1. Navigieren Sie zur Seite Verbindungen unter **Daten verwalten > Integrationen**.
1. Klicken **Integration hinzufügen**, rechts oben auf dem Bildschirm.
1. Klicken Sie auf **[!DNL Google Adwords]** Symbol. Dadurch wird die [!DNL Google Adwords] Seite mit Anmeldeinformationen.
1. Geben Sie Ihre [!DNL Google Analytics] Anmeldedaten. Nach Abschluss des Autorisierungsprozesses werden Sie zu [!DNL MBI].
1. Daraufhin wird eine Liste der Profil-IDs angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL MBI].

   ![](../../../assets/cnnct-profile.png)

1. Änderungen werden automatisch gespeichert. Klicken Sie daher auf **[!UICONTROL Back to Connections]** wenn Sie fertig sind.

Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt `Connecting Multiple Google Analytics profiles` unten.

## `Connecting multiple Google Analytics profiles`

Möglicherweise sind mehrere Websites mit einer [!DNL Google Analytics] eigenem [!DNL Google Analytics] Profil-ID. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL MBI]. Überprüfen Sie einfach die Profil-IDs, die Sie während des Profilauswahlschritts einbeziehen möchten.

**So identifizieren Sie die Google Analytics-ID einer bestimmten Website:**

1. Anmelden [!DNL Google Analytics]
1. Rufen Sie die Website auf [!DNL Google Analytics] Dashboard
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht Zahlen im Folgenden `p` am Ende der Zeile:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**`

## Verbindung [!DNL Google Adwords]

1. Besuchen Sie Ihre [!DNL Google] [Kontoeinstellungen](https://www.google.com/accounts/) Seite.
1. Unter dem `Security` und klicken Sie auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken **[!UICONTROL revoke access]** neben [!DNL MBI].

## Verwandte

* [Erneutes Authentifizieren von Integrationen](https://support.magento.com/hc/en-us/articles/360016733151)
* [Verweisquelle für Bestellungen verfolgen über [!DNL Google ECommerce]](../integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](https://support.magento.com/hc/en-us/articles/360016732911)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Erhöhen Sie den ROI Ihrer Werbekampagnen.](../../analysis/roi-ad-camp.md)
* [Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../../analysis/utm-attributes.md)
