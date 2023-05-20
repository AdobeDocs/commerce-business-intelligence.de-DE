---
title: Google Adwords verbinden
description: Erfahren Sie, wie Sie den ROI Ihrer Kampagne messen können, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (CLV) der durch Ihre Kampagnen erworbenen Benutzer miteinander verbinden.
exl-id: db99f817-2a2e-4194-9dd2-ec2d6b27a118
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Verbinden [!DNL Google Adwords]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Google_Adwords_logo.png)

Sie recherchierten, erstellten Ihre Anzeigen, starteten Ihre [!DNL Google] Kampagne. Jetzt ist es an der Zeit, Ihre Anzeigenausgabedaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mithilfe Ihrer Anzeigenausgabedaten können Sie [Messen Sie den Kampagnen-ROI durch die Verknüpfung Ihrer Werbe- und des Kundenlebenszeitwerts (CLV).](../../analysis/roi-ad-camp.md) der Benutzer, die durch Ihre Kampagnen erworben wurden.

Erste Schritte mit der Eingabe Ihrer [!DNL Google Adwords] Anmeldedaten [!DNL Commerce Intelligence].

1. Navigieren Sie zu `Connections` Seite unter **Daten verwalten > Integrationen**.
1. Klicken **Integration hinzufügen**, rechts oben auf dem Bildschirm.
1. Klicken Sie auf **[!DNL Google Adwords]** Symbol. Dadurch wird die [!DNL Google Adwords] Seite mit Anmeldeinformationen.
1. Geben Sie Ihre [!DNL Google Analytics] Anmeldedaten. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence].
1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL Commerce Intelligence].

   ![](../../../assets/cnnct-profile.png)

1. Änderungen werden automatisch gespeichert. Klicken Sie daher auf **[!UICONTROL Back to Connections]** wenn Sie fertig sind.

Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt `Connecting Multiple Google Analytics profiles` unten.

## Mehrere Verbindungen herstellen [!DNL Google Analytics] profiles

Möglicherweise sind mehrere Websites mit einer [!DNL Google Analytics] eigenem Konto [!DNL Google Analytics] Profil-ID. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence]. Überprüfen Sie die Profil-IDs, die Sie während des Schritts zur Profilauswahl einbeziehen möchten.

**So identifizieren Sie die Google Analytics-ID einer bestimmten Website:**

1. Anmelden [!DNL Google Analytics]
1. Rufen Sie die Website auf [!DNL Google Analytics] Dashboard
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht folgenden Zahlen `p` am Ende der Zeile:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**`

## Verbindung [!DNL Google Adwords]

1. Besuchen Sie Ihre [!DNL Google] [Kontoeinstellungen](https://www.google.com/account/about/?hl=en) Seite.
1. Unter dem `Security` Abschnitt, klicken Sie auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken **[!UICONTROL revoke access]**.

## Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verweisquelle für Bestellungen verfolgen über [!DNL Google ECommerce]](../integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Erhöhen Sie den ROI Ihrer Werbekampagnen.](../../analysis/roi-ad-camp.md)
* [Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../../analysis/utm-attributes.md)
