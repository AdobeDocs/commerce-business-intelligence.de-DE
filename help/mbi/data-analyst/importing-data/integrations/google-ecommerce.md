---
title: Google ECommerce verbinden
description: Erfahren Sie mehr über Ihre bevorzugten Verweiskanäle.
exl-id: c80f52f3-894a-4084-8c0e-aee618ed77f5
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Verbinden [!DNL Google ECommerce]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-ecommerce-logo.png)

Sie haben einen stetigen Traffic- und Auftragsfluss, was bedeutet, dass Sie effektiv Kunden erreichen und gewinnen. Aber was sind Ihre wertvollsten Verweiskanäle? Welchen durchschnittlichen Lebenszeitwert haben Kunden von einer Quelle im Vergleich zur anderen erworben? Durch die Verbindung Ihrer Bestellungsreferenz-Quelldaten aus [!DNL Google ECommerce] nach [!DNL MBI]können Sie Analysen erstellen, die Ihnen bei der Identifizierung Ihrer [wertvollste Marketingkanäle](../../../data-analyst/analysis/most-value-source-channel.md).

Beginnen wir mit der Eingabe von [!DNL Google ECommerce] Anmeldedaten [!DNL MBI]:

1. Navigieren Sie zu `Connections` Seite unter **[!UICONTROL Admin** > **Connections]**.
1. Klicken **[!UICONTROL Add a New Source]** auf der rechten Seite des Bildschirms über dem `Data Sources` Tabelle.
1. Klicken Sie auf [!DNL Google ECommerce] Symbol. Dadurch wird die [!DNL Google ECommerce] Seite mit Anmeldeinformationen.
1. Geben Sie Ihre [!DNL Google Analytics] Anmeldedaten. Nach Abschluss des Autorisierungsprozesses werden Sie zu [!DNL MBI].
1. Daraufhin wird eine Liste der Profil-IDs angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL MBI].

   Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt &quot;Mehrere Profile verbinden&quot;. [!DNL Google Analytics] Profile weiter unten.

   ![](../../../assets/conn-mult-ga-profiles.png)<!--{: width="500"}-->

1. Änderungen werden automatisch gespeichert. Klicken Sie also einfach auf **[!UICONTROL Back to Connections]** wenn Sie fertig sind.

## Mehrere Verbindungen herstellen [!DNL Google Analytics] Profile in [!DNL MBI]

Möglicherweise sind mehrere Websites mit einer [!DNL Google Analytics] eigenem [!DNL Google Analytics] Profil-ID. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL MBI]. Überprüfen Sie einfach die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID:

1. Anmelden [!DNL Google Analytics]
1. Rufen Sie die Website auf [!DNL Google Analytics] Dashboard
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht Zahlen im Folgenden `p` am Zeilenende

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Verbindung [!DNL Google ECommerce] von [!DNL MBI] {#disconnect}

1. Besuchen Sie Ihre [!DNL Google Analytics] [Kontoeinstellungen](https://www.google.com/accounts/) Seite.
1. Unter dem `Security` Abschnitt, klicken Sie auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken **[!UICONTROL revoke access]** neben [!DNL MBI].

## Verwandte:

* [Erwartet [!DNL Google ECommerce] data](../integrations/google-ecommerce-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
* [Einrichten [!DNL Google ECommerce] tracking](https://support.google.com/analytics/answer/1009612?hl=en)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../../analysis/most-value-source-channel.md)
* [Erhöhen Sie den ROI Ihrer Werbekampagnen.](../../analysis/roi-ad-camp.md)
