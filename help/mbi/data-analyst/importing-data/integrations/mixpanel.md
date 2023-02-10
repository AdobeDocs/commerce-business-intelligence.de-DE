---
title: Mixpanel verbinden
description: Erfahren Sie, wie Sie analysieren können, wie Benutzer auf Ihren Websites und Apps navigieren und diese nutzen.
exl-id: e6a9f08f-1063-4d92-93e6-971280239fdb
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Verbinden [!DNL Mixpanel]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Mixpanel_logo.png)

Mit [!DNL Mixpanel]können Sie analysieren, wie Benutzer auf Ihren Websites und Apps navigieren und diese nutzen. Wenn Sie sich die Verhaltensdaten der Benutzer genauer ansehen, können Sie intelligentere Design- und Entwicklungsentscheidungen treffen, was insgesamt ein besseres Produkt bedeutet. Verbinden [!DNL Mixpanel] nach [!DNL MBI] können Sie analysieren, wie sich Ihre Benutzer verhalten und wie sich dieses Verhalten im Umsatz niederschlägt.

Verbinden Ihrer [!DNL Mixpanel] Daten an [!DNL MBI] einen einfachen dreistufigen Prozess:

1. [Öffnen Sie die [!DNL Mixpanel] Anmeldeseite in [!DNL MBI]](#stepone)
1. [Abrufen Ihrer [!DNL Mixpanel] API-Anmeldeinformationen](#steptwo)
1. [Geben Sie Ihre [!DNL Mixpanel] API-Anmeldeinformationen in MBI](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browser-Fenster oder -Registerkarten öffnen - eines für [!DNL MBI], der andere für Ihre [!DNL Mixpanel] -Konto.

## Öffnen der [!DNL Mixpanel] Anmeldungsseite {#stepone}

Fangen wir an:

1. Navigieren Sie zu `Connections` Seite unter **[!DNL Manage Data** > **Connections]**.
1. Klicken **[!UICONTROL Add a New Source]** auf der rechten Seite des Bildschirms über dem `Data Sources` Tabelle.
1. Klicken Sie auf [!DNL Mixpanel] und die Seite mit den Anmeldedaten wird geöffnet.

Lassen Sie diese Seite zunächst geöffnet und wechseln Sie mit Ihrem [!DNL Mixpanel] -Konto.

## Abrufen Ihrer [!DNL Mixpanel] API-Anmeldeinformationen {#steptwo}

Wenn Sie sich nicht bei Ihrer [!DNL Mixpanel] -Konto hinzugefügt haben, tun Sie dies und führen Sie dann die folgenden Schritte aus:

1. Klicken **[!UICONTROL Account]** in der oberen rechten Ecke.
1. Klicken Sie im angezeigten Dialogfeld auf **[!UICONTROL Projects]**.
1. Ihre API-Anmeldeinformationen werden angezeigt:

![Abrufen von Mixpanel-API-Anmeldeinformationen](../../../assets/Mixpanel_API_creds.png)

Lassen Sie es offen - wir brauchen es, um es zu verpacken.

## Eingabe Ihrer [!DNL Mixpanel] API-Anmeldeinformationen in [!DNL MBI] {#stepthree}

1. Kopieren Sie die `API Key` und `Secret` in [!DNL Mixpanel] Anmeldeseite in [!DNL MBI].
1. Klicken **[!UICONTROL Connect to Mixpanel]** , um das Setup abzuschließen.

Das ist es! Wenn die Verbindung erfolgreich hergestellt wurde, wird ein _Erfolg!_ wird oben auf der Seite angezeigt.

### Verwandte

* [Erwartet [!DNL Mixpanel] data](../integrations/mixpanel-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
