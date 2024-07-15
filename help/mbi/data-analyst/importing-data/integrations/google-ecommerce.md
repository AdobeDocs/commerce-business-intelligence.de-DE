---
title: Google ECommerce verbinden
description: Erfahren Sie mehr über Ihre bevorzugten Verweiskanäle.
exl-id: c80f52f3-894a-4084-8c0e-aee618ed77f5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# [!DNL Google ECommerce] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-ecommerce-logo.png)

Sie haben einen stetigen Traffic- und Auftragsfluss, was bedeutet, dass Sie effektiv Kunden erreichen und gewinnen. Aber was sind Ihre wertvollsten Verweiskanäle? Wie hoch ist der durchschnittliche Lebenszeitwert von Kunden, die aus einer Quelle im Vergleich zu einer anderen erworben wurden? Durch die Verbindung Ihrer Bestellungsreferrer-Quelldaten von [!DNL Google ECommerce] mit [!DNL Commerce Intelligence] können Sie Analysen erstellen, die Ihnen dabei helfen, Ihre [wertvollsten Marketing-Kanäle](../../../data-analyst/analysis/most-value-source-channel.md) zu identifizieren.

Geben Sie zunächst Ihre [!DNL Google ECommerce] -Anmeldedaten in [!DNL Commerce Intelligence] ein:

1. Wechseln Sie zur Seite `Connections` unter **[!UICONTROL Admin** > **Connections]**.

1. Klicken Sie auf **[!UICONTROL Add a New Source]** rechts neben dem Bildschirm über der Tabelle `Data Sources`.

1. Klicken Sie auf das Symbol &quot;[!DNL Google ECommerce]&quot;. Dadurch wird die Seite mit den Anmeldedaten für [!DNL Google ECommerce] geöffnet.

1. Geben Sie Ihre [!DNL Google Analytics] -Anmeldedaten ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] umgeleitet.

1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten.[!DNL Commerce Intelligence]

   Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt **Mehrere Profile verbinden [!DNL Google Analytics] weiter unten.

   ![](../../../assets/conn-mult-ga-profiles.png)<!--{: width="500"}-->

1. Änderungen werden automatisch gespeichert. Klicken Sie also auf **[!UICONTROL Back to Connections]** , wenn Sie fertig sind.

## Mehrere [!DNL Google Analytics] Profile mit [!DNL Commerce Intelligence] verbinden

Möglicherweise sind mehrere Websites mit einem einzelnen [!DNL Google Analytics] -Konto verbunden, das durch ihre eigene [!DNL Google Analytics] -Profil-ID identifiziert wird. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einschließen. Überprüfen Sie die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID einer bestimmten Website:

1. Melden Sie sich bei [!DNL Google Analytics] an.
1. Gehen Sie zum Dashboard [!DNL Google Analytics] der jeweiligen Website.
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht Zahlen nach `p` am Ende der Zeile.

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## [!DNL Google ECommerce] von [!DNL Commerce Intelligence] trennen {#disconnect}

1. Besuchen Sie die Seite [!DNL Google Analytics] [Kontoeinstellungen](https://www.google.com/account/about/?hl=en) .
1. Klicken Sie unter dem Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte:

* [Erwartete [!DNL Google ECommerce] Daten](../integrations/google-ecommerce-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Einrichten von [!DNL Google ECommerce] tracking](https://support.google.com/analytics/answer/1009612?hl=en)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI bei Werbekampagnen](../../analysis/roi-ad-camp.md)
