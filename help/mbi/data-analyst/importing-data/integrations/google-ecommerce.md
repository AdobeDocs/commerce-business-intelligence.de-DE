---
title: Google E-Commerce verbinden
description: Erfahren Sie mehr über Ihre wertvollsten Empfehlungskanäle.
exl-id: c80f52f3-894a-4084-8c0e-aee618ed77f5
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/iBVf-dkbm1NbELZUYjLp1TzypO7Cu55tIzd93lQ1zo0
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 305
ht-degree: 0%

---

# [!DNL Google ECommerce] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Google eCommerce-Logo](../../../assets/google-ecommerce-logo.png)

Sie haben einen stetigen Fluss von Traffic und Bestellungen, was bedeutet, dass Sie Kunden effektiv erreichen und gewinnen. Aber was sind Ihre wertvollsten Empfehlungskanäle? Wie hoch ist der durchschnittliche Lebenszeitwert von Kunden, die aus einer Quelle im Vergleich zu einer anderen akquiriert wurden? Durch die Verbindung Ihrer Quelldaten für Auftragsverweise von [!DNL Google ECommerce] zu [!DNL Commerce Intelligence] können Sie Analysen erstellen, mit denen Sie Ihre [wertvollsten Marketing-Kanäle“ ](../../../data-analyst/analysis/most-value-source-channel.md).

Beginnen Sie, indem Sie Ihre [!DNL Google ECommerce]-Anmeldedaten in [!DNL Commerce Intelligence]:

1. Navigieren Sie zur `Connections` unter **[!UICONTROL Admin** > **Connections]**.

1. Klicken Sie auf **[!UICONTROL Add a New Source]** rechts im Bildschirm über der `Data Sources`.

1. Klicken Sie auf das Symbol [!DNL Google ECommerce] . Dadurch wird die Seite mit den [!DNL Google ECommerce]-Anmeldeinformationen geöffnet.

1. Geben Sie Ihre [!DNL Google Analytics] ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.

1. Eine Liste der Profil-IDs wird angezeigt. Markieren Sie die Profile, mit denen Sie eine Verbindung herstellen möchten[!DNL Commerce Intelligence].

   Wenn Sie mehrere Profile haben und Hilfe bei der Identifizierung des richtigen Profils benötigen, lesen Sie den Abschnitt **Mehrere [!DNL Google Analytics] verbinden“ unten.

   ![Formular mit Optionen zum Verbinden mehrerer Google Analytics-Profile](../../../assets/conn-mult-ga-profiles.png)<!--{: width="500"}-->

1. Änderungen werden automatisch gespeichert. Klicken Sie abschließend auf **[!UICONTROL Back to Connections]**.

## Verbinden mehrerer [!DNL Google Analytics] mit [!DNL Commerce Intelligence]

Möglicherweise sind mehrere Websites mit einem einzigen [!DNL Google Analytics]-Konto verbunden, das durch seine eigene [!DNL Google Analytics]-Profil-ID identifiziert wird. In diesem Fall haben Sie die Möglichkeit, alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einzuschließen. Markieren Sie die Profil-IDs, die Sie in den Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics]-Profil-ID einer bestimmten Website:

1. Anmelden bei [!DNL Google Analytics].
1. Zum [!DNL Google Analytics]-Dashboard der jeweiligen Website wechseln.
1. URL anzeigen : Die Profil-ID entspricht den acht Zahlen, die auf die `p` am Ende der Zeile folgen.

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Trennen von [!DNL Google ECommerce] von [!DNL Commerce Intelligence] {#disconnect}

1. Rufen Sie [!DNL Google Analytics] Seite [Kontoeinstellungen](https://www.google.com/account/about/?hl=en) auf.
1. Klicken Sie im Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandt:

* [ [!DNL Google ECommerce]  Daten](../integrations/google-ecommerce-data.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Einrichten [!DNL Google ECommerce] Tracking](https://support.google.com/analytics/answer/1009612?hl=en)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI Ihrer Werbekampagnen](../../analysis/roi-ad-camp.md)
