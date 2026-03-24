---
title: Google AdWords verbinden
description: Erfahren Sie, wie Sie den Kampagnen-ROI messen, indem Sie Ihre Werbekosten und den Lebenszeitwert (CLV) der von Ihren Kampagnen erworbenen Benutzer vereinen.
exl-id: db99f817-2a2e-4194-9dd2-ec2d6b27a118
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/mZ8R2vPyFy8pGpYi4KhqocVnP-OlgMPGU3KJ4C9vsTo
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# [!DNL Google Adwords] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Google AdWords-Logo](../../../assets/Google_Adwords_logo.png)

Sie haben recherchiert, Ihre Anzeigen erstellt und Ihre [!DNL Google] gestartet. Jetzt ist es an der Zeit, Ihre Anzeigenausgabendaten zu analysieren und festzustellen, ob Ihr Geld effektiv ausgegeben wird. Mit Ihren Werbeausgabendaten können Sie [Kampagnen-ROI messen, indem Sie Ihre Werbekosten und den Kundenlebenszeitwert (Customer Lifetime Value, CLV) der &#x200B;](../../analysis/roi-ad-camp.md) Ihrer Kampagnen erworbenen Benutzer zusammenfassen.

Beginnen Sie, indem Sie Ihre [!DNL Google Adwords] Anmeldedaten in [!DNL Commerce Intelligence] eingeben.

1. Navigieren Sie zur `Connections` unter **Daten verwalten > Integrationen**.
1. Klicken Sie **oben rechts** Bildschirm auf „Integration hinzufügen“.
1. Klicken Sie auf das Symbol **[!DNL Google Adwords]** . Dadurch wird die Seite mit den [!DNL Google Adwords]-Anmeldeinformationen geöffnet.
1. Geben Sie Ihre [!DNL Google Analytics] ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.
1. Eine Liste der Profil-IDs wird angezeigt. Markieren Sie die Profile, mit denen Sie eine Verbindung herstellen möchten[!DNL Commerce Intelligence].

   ![Google AdWords-Verbindungsdialogfeld mit Profilauswahl](../../../assets/cnnct-profile.png)

1. Änderungen werden automatisch gespeichert. Klicken Sie abschließend auf **[!UICONTROL Back to Connections]**.

Wenn Sie mehrere Profile haben und Hilfe bei der Identifizierung des richtigen Profils benötigen, lesen Sie den folgenden Abschnitt `Connecting Multiple Google Analytics profiles` .

## Mehrere [!DNL Google Analytics] verbinden

Möglicherweise sind mehrere Websites mit einem einzigen [!DNL Google Analytics]-Konto verbunden, das durch seine eigene [!DNL Google Analytics]-Profil-ID identifiziert wird. In diesem Fall haben Sie die Möglichkeit, alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einzuschließen. Markieren Sie die Profil-IDs, die Sie in den Schritt zur Profilauswahl einbeziehen möchten.

**So identifizieren Sie die Google Analytics-Profil-ID einer bestimmten Website:**

1. Anmelden bei [!DNL Google Analytics]
1. Zum [!DNL Google Analytics]-Dashboard der jeweiligen Website wechseln
1. Sehen Sie sich die URL an. Die Profil-ID entspricht den acht Zahlen, die am Ende der Zeile nach `p` folgen:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**`

## [!DNL Google Adwords] trennen

1. Rufen Sie [!DNL Google] Seite [Kontoeinstellungen](https://www.google.com/account/about/?hl=en) auf.
1. Klicken Sie im Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]**.

## verwandt

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verfolgen Sie die Quelle der Bestellungsreferenz über [!DNL Google ECommerce]](../integrations/google-ecommerce.md)
* [Verfolgen Sie die Quelle der Benutzerreferenz in Ihrer Datenbank](../../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI Ihrer Werbekampagnen](../../analysis/roi-ad-camp.md)
* [Wie funktioniert  [!DNL Google Analytics]  UTM-Attribution?](../../analysis/utm-attributes.md)
