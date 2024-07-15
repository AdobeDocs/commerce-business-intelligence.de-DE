---
title: Google Adwords verbinden
description: Erfahren Sie, wie Sie den ROI Ihrer Kampagne messen können, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (CLV) der durch Ihre Kampagnen erworbenen Benutzer miteinander verbinden.
exl-id: db99f817-2a2e-4194-9dd2-ec2d6b27a118
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# [!DNL Google Adwords] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Google_Adwords_logo.png)

Sie haben Ihre Recherchen durchgeführt, Ihre Anzeigen erstellt und Ihre [!DNL Google]-Kampagne gestartet. Jetzt ist es an der Zeit, Ihre Anzeigenausgabedaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mithilfe Ihrer Anzeigenausgabedaten können Sie den ROI Ihrer Kampagne [messen, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (CLV)](../../analysis/roi-ad-camp.md) der durch Ihre Kampagnen erworbenen Benutzer miteinander verbinden.

Geben Sie zunächst Ihre [!DNL Google Adwords] -Anmeldedaten in [!DNL Commerce Intelligence] ein.

1. Wechseln Sie zur Seite `Connections` unter **Daten verwalten > Integrationen**.
1. Klicken Sie oben rechts im Bildschirm auf **Integration hinzufügen** .
1. Klicken Sie auf das Symbol &quot;**[!DNL Google Adwords]**&quot;. Dadurch wird die Seite mit den Anmeldedaten für [!DNL Google Adwords] geöffnet.
1. Geben Sie Ihre [!DNL Google Analytics] -Anmeldedaten ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] umgeleitet.
1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten.[!DNL Commerce Intelligence]

   ![](../../../assets/cnnct-profile.png)

1. Die Änderungen werden automatisch gespeichert. Klicken Sie daher nach Abschluss des Vorgangs auf **[!UICONTROL Back to Connections]** .

Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt &quot;`Connecting Multiple Google Analytics profiles`&quot;unten.

## Mehrere [!DNL Google Analytics] Profile verbinden

Möglicherweise sind mehrere Websites mit einem einzelnen [!DNL Google Analytics]-Konto verbunden, das durch ihre eigene [!DNL Google Analytics] Profil-ID identifiziert wird. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einschließen. Überprüfen Sie die Profil-IDs, die Sie während des Schritts zur Profilauswahl einbeziehen möchten.

**So identifizieren Sie die Google Analytics-ID einer bestimmten Website:**

1. Anmelden bei [!DNL Google Analytics]
1. Gehen Sie zum Dashboard der jeweiligen Website mit dem Tag &quot;[!DNL Google Analytics]&quot;
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht Zahlen nach `p` am Ende der Zeile:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**`

## Trennen von [!DNL Google Adwords]

1. Besuchen Sie die Seite [!DNL Google] [Kontoeinstellungen](https://www.google.com/account/about/?hl=en) .
1. Klicken Sie unter dem Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]**.

## Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verweisquelle für Bestellungen über  [!DNL Google ECommerce] verfolgen](../integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI bei Werbekampagnen](../../analysis/roi-ad-camp.md)
* [Wie funktioniert die  [!DNL Google Analytics] UTM-Attribution?](../../analysis/utm-attributes.md)
