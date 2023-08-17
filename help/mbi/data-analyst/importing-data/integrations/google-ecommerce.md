---
title: Google ECommerce verbinden
description: Erfahren Sie mehr über Ihre bevorzugten Verweiskanäle.
exl-id: c80f52f3-894a-4084-8c0e-aee618ed77f5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Verbinden [!DNL Google ECommerce]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-ecommerce-logo.png)

Sie haben einen stetigen Traffic- und Auftragsfluss, was bedeutet, dass Sie effektiv Kunden erreichen und gewinnen. Aber was sind Ihre wertvollsten Verweiskanäle? Wie hoch ist der durchschnittliche Lebenszeitwert von Kunden, die aus einer Quelle im Vergleich zu einer anderen erworben wurden? Durch die Verbindung Ihrer Bestellungsreferenz-Quelldaten aus [!DNL Google ECommerce] nach [!DNL Commerce Intelligence]können Sie Analysen erstellen, die Ihnen bei der Identifizierung Ihrer [wertvollste Marketingkanäle](../../../data-analyst/analysis/most-value-source-channel.md).

Erste Schritte mit der Eingabe Ihrer [!DNL Google ECommerce] Anmeldedaten [!DNL Commerce Intelligence]:

1. Navigieren Sie zu `Connections` Seite unter **[!UICONTROL Admin** > **Connections]**.

1. Klicks **[!UICONTROL Add a New Source]** auf der rechten Seite des Bildschirms über dem `Data Sources` Tabelle.

1. Klicken Sie auf [!DNL Google ECommerce] Symbol. Dadurch wird die [!DNL Google ECommerce] Seite mit Anmeldeinformationen.

1. Geben Sie Ihre [!DNL Google Analytics] Anmeldedaten. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence].

1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten [!DNL Commerce Intelligence].

   Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt &quot;Mehrere Profile verbinden&quot;. [!DNL Google Analytics] Profile weiter unten.

   ![](../../../assets/conn-mult-ga-profiles.png)<!--{: width="500"}-->

1. Änderungen werden automatisch gespeichert. Klicken Sie daher auf **[!UICONTROL Back to Connections]** wenn Sie fertig sind.

## Mehrere Verbindungen [!DNL Google Analytics] Profile in [!DNL Commerce Intelligence]

Möglicherweise sind mehrere Websites mit einer [!DNL Google Analytics] eigenem Konto [!DNL Google Analytics] Profil-ID. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence]. Überprüfen Sie die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID:

1. Anmelden [!DNL Google Analytics].
1. Rufen Sie die Website auf [!DNL Google Analytics] Dashboard.
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht folgenden Zahlen `p` am Ende der Zeile.

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Verbindung [!DNL Google ECommerce] von [!DNL Commerce Intelligence] {#disconnect}

1. Besuchen Sie Ihre [!DNL Google Analytics] [Kontoeinstellungen](https://www.google.com/account/about/?hl=en) Seite.
1. Unter dem `Security` Abschnitt, klicken Sie auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicks **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte:

* [Erwartet [!DNL Google ECommerce] data](../integrations/google-ecommerce-data.md)
* [Neu authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Einrichten [!DNL Google ECommerce] tracking](https://support.google.com/analytics/answer/1009612?hl=en)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Steigerung des ROI bei Werbekampagnen](../../analysis/roi-ad-camp.md)
