---
title: Mixpanel verbinden
description: Erfahren Sie, wie Sie analysieren können, wie Benutzer Ihre Websites und Programme navigieren und verwenden.
exl-id: e6a9f08f-1063-4d92-93e6-971280239fdb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# [!DNL Mixpanel] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Mixpanel-Logo](../../../assets/Mixpanel_logo.png)

Mit [!DNL Mixpanel] können Sie analysieren, wie Benutzer Ihre Websites und Programme navigieren und verwenden. Ein genauer Blick auf die Daten des Benutzerverhaltens führt zu intelligenteren Design- und Entwicklungsentscheidungen und damit zu einem insgesamt besseren Produkt. Wenn Sie [!DNL Mixpanel] mit [!DNL Commerce Intelligence] verbinden, können Sie analysieren, wie sich Ihre Benutzer verhalten und wie sich dieses Verhalten in Umsätzen niederschlägt.

Verbinden Ihrer [!DNL Mixpanel] Daten, um einen einfachen dreistufigen Prozess zu [!DNL Commerce Intelligence]:

1. [Öffnen Sie die  [!DNL Mixpanel] Anmeldeinformationen“ in  [!DNL Commerce Intelligence]](#stepone)
1. [Abrufen Ihrer  [!DNL Mixpanel] -API-Anmeldedaten](#steptwo)
1. [Geben Sie Ihre  [!DNL Mixpanel] -API-Anmeldedaten ein in [!DNL Commerce Intelligence]](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browser-Fenster oder Registerkarten öffnen, eines für [!DNL Commerce Intelligence] und eines für Ihr [!DNL Mixpanel].

## Öffnen der Seite mit den [!DNL Mixpanel] Anmeldedaten {#stepone}

Erste Schritte:

1. Navigieren Sie zur `Connections` unter **[!DNL Manage Data** > **Connections]**.

1. Klicken Sie auf **[!UICONTROL Add a New Source]** rechts im Bildschirm über der `Data Sources`.

1. Klicken Sie auf das Symbol [!DNL Mixpanel] und die Seite mit den Anmeldedaten wird geöffnet.

Lassen Sie diese Seite vorerst geöffnet und wechseln Sie mit Ihrem [!DNL Mixpanel]-Konto zum Browser-Fenster.

## Abrufen Ihrer [!DNL Mixpanel] API-Anmeldedaten {#steptwo}

Wenn Sie sich noch nicht bei Ihrem [!DNL Mixpanel]-Konto angemeldet haben, führen Sie diese Schritte aus und führen Sie dann folgende Schritte aus:

1. Klicken Sie oben rechts auf **[!UICONTROL Account]** .

1. Klicken Sie im angezeigten Dialogfeld auf **[!UICONTROL Projects]**.

1. Ihre API-Anmeldedaten werden angezeigt:

![Abrufen von Mixpanel-API-Anmeldeinformationen](../../../assets/Mixpanel_API_creds.png)

Lassen Sie es offen, Sie brauchen es, um es zu verpacken.

## Eingeben Ihrer [!DNL Mixpanel]-API-Anmeldedaten in [!DNL Commerce Intelligence] {#stepthree}

1. Kopieren Sie die `API Key` und `Secret` in die Seite [!DNL Mixpanel] Anmeldedaten in [!DNL Commerce Intelligence].
1. Klicken Sie auf **[!UICONTROL Connect to Mixpanel]** , um die Einrichtung abzuschließen.

Wenn die Verbindung erfolgreich hergestellt wurde, wird ein _Erfolgreich!_ Nachricht wird oben auf der Seite angezeigt.

### verwandt

* [&#x200B; [!DNL Mixpanel]  Daten](../integrations/mixpanel-data.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
