---
title: Mixpanel verbinden
description: Erfahren Sie, wie Sie analysieren können, wie Benutzer Ihre Websites und Programme navigieren und verwenden.
exl-id: e6a9f08f-1063-4d92-93e6-971280239fdb
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/ap-nWiPVnPSpvUT4uiimZ7iC4fiuKvKH0ZMVkOTDcK8
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 246
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

* [ [!DNL Mixpanel]  Daten](../integrations/mixpanel-data.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
