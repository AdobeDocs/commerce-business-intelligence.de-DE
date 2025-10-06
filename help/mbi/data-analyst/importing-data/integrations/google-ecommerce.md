---
title: Google E-Commerce verbinden
description: Erfahren Sie mehr über Ihre wertvollsten Empfehlungskanäle.
exl-id: c80f52f3-894a-4084-8c0e-aee618ed77f5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Google ECommerce] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Google eCommerce-Logo](../../../assets/google-ecommerce-logo.png)

Sie haben einen stetigen Fluss von Traffic und Bestellungen, was bedeutet, dass Sie Kunden effektiv erreichen und gewinnen. Aber was sind Ihre wertvollsten Empfehlungskanäle? Wie hoch ist der durchschnittliche Lebenszeitwert von Kunden, die aus einer Quelle im Vergleich zu einer anderen akquiriert wurden? Durch die Verbindung Ihrer Quelldaten für Auftragsverweise von [!DNL Google ECommerce] zu [!DNL Commerce Intelligence] können Sie Analysen erstellen, mit denen Sie Ihre [wertvollsten Marketing-Kanäle“ &#x200B;](../../../data-analyst/analysis/most-value-source-channel.md).

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

* [&#x200B; [!DNL Google ECommerce]  Daten](../integrations/google-ecommerce-data.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Einrichten [!DNL Google ECommerce] Tracking](https://support.google.com/analytics/answer/1009612?hl=en)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI Ihrer Werbekampagnen](../../analysis/roi-ad-camp.md)
