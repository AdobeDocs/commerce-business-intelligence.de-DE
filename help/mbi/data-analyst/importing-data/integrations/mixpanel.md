---
title: Mixpanel verbinden
description: Erfahren Sie, wie Sie analysieren können, wie Benutzer zu Ihren Websites und Apps navigieren und diese verwenden.
exl-id: e6a9f08f-1063-4d92-93e6-971280239fdb
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Verbinden [!DNL Mixpanel]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Mixpanel_logo.png)

Mit [!DNL Mixpanel]können Sie analysieren, wie Benutzer auf Ihren Websites und Apps navigieren und diese verwenden. Wenn Sie sich die Verhaltensdaten der Benutzer genauer ansehen, können Sie intelligentere Design- und Entwicklungsentscheidungen treffen, was insgesamt ein besseres Produkt bedeutet. Verbinden [!DNL Mixpanel] nach [!DNL Commerce Intelligence] können Sie analysieren, wie sich Ihre Benutzer verhalten und wie sich dieses Verhalten im Umsatz niederschlägt.

Verbinden Ihrer [!DNL Mixpanel] Daten an [!DNL Commerce Intelligence] einen einfachen dreistufigen Prozess:

1. [Öffnen Sie die [!DNL Mixpanel] Anmeldeseite in [!DNL Commerce Intelligence]](#stepone)
1. [Abrufen Ihrer [!DNL Mixpanel] API-Anmeldeinformationen](#steptwo)
1. [Geben Sie Ihre [!DNL Mixpanel] API-Anmeldeinformationen in [!DNL Commerce Intelligence]](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browserfenster oder -registerkarten öffnen, eine für [!DNL Commerce Intelligence] und der andere für Ihre [!DNL Mixpanel] -Konto.

## Öffnen der [!DNL Mixpanel] Anmeldungsseite {#stepone}

Erste Schritte:

1. Navigieren Sie zu `Connections` Seite unter **[!DNL Manage Data** > **Connections]**.

1. Klicken **[!UICONTROL Add a New Source]** auf der rechten Seite des Bildschirms über dem `Data Sources` Tabelle.

1. Klicken Sie auf [!DNL Mixpanel] und die Seite mit den Anmeldedaten geöffnet.

Lassen Sie diese Seite zunächst geöffnet und wechseln Sie mit Ihrem [!DNL Mixpanel] -Konto.

## Abrufen Ihrer [!DNL Mixpanel] API-Anmeldeinformationen {#steptwo}

Wenn Sie sich nicht bei Ihrer [!DNL Mixpanel] -Konto hinzugefügt haben, tun Sie dies und führen Sie dann die folgenden Schritte aus:

1. Klicken **[!UICONTROL Account]** in der oberen rechten Ecke.

1. Klicken Sie im angezeigten Dialogfeld auf **[!UICONTROL Projects]**.

1. Ihre API-Anmeldeinformationen werden angezeigt:

![Abrufen von Mixpanel-API-Anmeldeinformationen](../../../assets/Mixpanel_API_creds.png)

Lassen Sie das offen, Sie brauchen es, um es zu verpacken.

## Eingabe Ihrer [!DNL Mixpanel] API-Anmeldeinformationen in [!DNL Commerce Intelligence] {#stepthree}

1. Kopieren Sie die `API Key` und `Secret` in [!DNL Mixpanel] Anmeldeseite in [!DNL Commerce Intelligence].
1. Klicken **[!UICONTROL Connect to Mixpanel]** , um das Setup abzuschließen.

Wenn die Verbindung erfolgreich hergestellt wurde, wird ein _Erfolg!_ wird oben auf der Seite angezeigt.

### Verwandte

* [Erwartet [!DNL Mixpanel] data](../integrations/mixpanel-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
