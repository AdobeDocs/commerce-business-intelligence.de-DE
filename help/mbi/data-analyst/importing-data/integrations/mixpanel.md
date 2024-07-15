---
title: Mixpanel verbinden
description: Erfahren Sie, wie Sie analysieren können, wie Benutzer zu Ihren Websites und Apps navigieren und diese verwenden.
exl-id: e6a9f08f-1063-4d92-93e6-971280239fdb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# [!DNL Mixpanel] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Mixpanel_logo.png)

Mit [!DNL Mixpanel] können Sie analysieren, wie Benutzer auf Ihren Websites und Apps navigieren und diese verwenden. Wenn Sie sich die Verhaltensdaten der Benutzer genauer ansehen, können Sie intelligentere Design- und Entwicklungsentscheidungen treffen, was insgesamt ein besseres Produkt bedeutet. Durch die Verbindung von [!DNL Mixpanel] mit [!DNL Commerce Intelligence] können Sie analysieren, wie sich Ihre Benutzer verhalten und wie sich dieses Verhalten in Umsatz auswirkt.

Verbinden Ihrer [!DNL Mixpanel] -Daten mit [!DNL Commerce Intelligence] einem einfachen dreistufigen Prozess:

1. [Öffnen Sie die Seite mit den [!DNL Mixpanel] Anmeldedaten in  [!DNL Commerce Intelligence].](#stepone)
1. [Abrufen Ihrer [!DNL Mixpanel] API-Anmeldeinformationen](#steptwo)
1. [Geben Sie Ihre [!DNL Mixpanel] API-Anmeldeinformationen in  [!DNL Commerce Intelligence] ein.](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browserfenster oder -registerkarten öffnen, eines für [!DNL Commerce Intelligence] und das andere für Ihr [!DNL Mixpanel]-Konto.

## Öffnen der Anmeldeseite für [!DNL Mixpanel] {#stepone}

Erste Schritte:

1. Wechseln Sie zur Seite `Connections` unter **[!DNL Manage Data** > **Connections]**.

1. Klicken Sie auf **[!UICONTROL Add a New Source]** rechts neben dem Bildschirm über der Tabelle `Data Sources`.

1. Klicken Sie auf das Symbol &quot;[!DNL Mixpanel]&quot;, und die Seite mit den Anmeldeinformationen wird geöffnet.

Lassen Sie diese Seite vorerst geöffnet und wechseln Sie mit Ihrem [!DNL Mixpanel] -Konto zum Browser-Fenster.

## Abrufen Ihrer [!DNL Mixpanel]-API-Anmeldeinformationen {#steptwo}

Wenn Sie sich noch nicht bei Ihrem [!DNL Mixpanel] -Konto angemeldet haben, führen Sie dies aus und gehen Sie dann wie folgt vor:

1. Klicken Sie oben rechts auf **[!UICONTROL Account]** .

1. Klicken Sie im angezeigten Dialogfeld auf **[!UICONTROL Projects]**.

1. Ihre API-Anmeldeinformationen werden angezeigt:

![Abrufen von Mixpanel-API-Anmeldeinformationen](../../../assets/Mixpanel_API_creds.png)

Lassen Sie das offen, Sie brauchen es, um es zu verpacken.

## Eingabe Ihrer [!DNL Mixpanel] API-Anmeldeinformationen in [!DNL Commerce Intelligence] {#stepthree}

1. Kopieren Sie die `API Key` und `Secret` in die Seite mit den [!DNL Mixpanel]-Anmeldeinformationen in [!DNL Commerce Intelligence].
1. Klicken Sie auf **[!UICONTROL Connect to Mixpanel]** , um das Setup abzuschließen.

Wenn die Verbindung erfolgreich hergestellt wurde, wird ein _Erfolg!Die Meldung_ wird oben auf der Seite angezeigt.

### Verwandte

* [Erwartete [!DNL Mixpanel] Daten](../integrations/mixpanel-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
