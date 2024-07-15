---
title: Zendesk verbinden
description: Erfahren Sie, wie Sie die Berichterstellung für Ihren Helpdesk in [!DNL Commerce Intelligence] konsolidieren.
exl-id: 1c7f7c5c-4b1c-4bcf-8f1d-2b4cf9cdb0fb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# [!DNL Zendesk] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Zendesk_logo.png)

Durch das Verbinden Ihrer [!DNL Zendesk] -Daten können Sie Ihre Helpdesk-Berichte in [!DNL Commerce Intelligence] konsolidieren. Auf diese Weise können Sie den Kundensupport optimieren und die Leistung des Helpdesk neben Ihrem Umsatz überwachen.

Das Verbinden Ihrer [!DNL Zendesk] -Daten ist ein einfacher dreistufiger Prozess:

1. [Öffnen Sie die Seite mit den [!DNL Zendesk] Anmeldedaten in  [!DNL Commerce Intelligence].](#stepone)
1. [Abrufen Ihres [!DNL Zendesk] API-Tokens](#steptwo)
1. [Geben Sie Ihre [!DNL Zendesk] Anmeldeinformationen und Ihr Token in [!DNL Commerce Intelligence] ein.](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browser-Fenster oder -Registerkarten öffnen - eines für [!DNL Commerce Intelligence], das andere für Ihr [!DNL Zendesk]-Konto.

## Öffnen Sie die Seite mit den Anmeldedaten für [!DNL Zendesk] in [!DNL Commerce Intelligence] {#stepone}

1. Wechseln Sie zur Seite `Integrations` unter **[!UICONTROL Manage Data** > ** Datenquellen **> **Integrationen]**.
1. Klicken Sie auf **[!UICONTROL Add Integration]** rechts auf dem Bildschirm.
1. Klicken Sie auf das Symbol &quot;[!DNL Zendesk]&quot;. Dadurch wird die Seite mit den Anmeldedaten für [!DNL Zendesk] geöffnet.

## Abrufen Ihres [!DNL Zendesk]-API-Tokens {#steptwo}

1. Klicken Sie im Fenster/auf der Registerkarte, auf der Sie bei Ihrem [!DNL Zendesk]-Konto angemeldet sind, auf das Zahnradsymbol unten links im Bildschirm.
1. Wenn das Menü `Settings` angezeigt wird, suchen Sie den Abschnitt `Channels` . Klicken Sie in diesem Abschnitt auf **[!UICONTROL API]** .
1. Klicken Sie im Abschnitt `Token Access` dieser Seite auf das Kontrollkästchen neben `Enabled`. Eine Liste aktiver API-Token wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Add New Token]**.
1. Geben Sie bei Aufforderung eine Beschriftung für das Token ein. Adobe empfiehlt die Verwendung von `Commerce Intelligence`, sodass Sie auf einen Blick wissen, welche Anwendung das Token verwendet.
1. Klicken Sie auf **[!UICONTROL Create]**.
1. Es wird ein API-Token erstellt. Kopieren Sie dieses Token. Es wird im nächsten Schritt verwendet.

## Geben Sie [!DNL Zendesk] Anmeldeinformationen und API-Token in [!DNL Commerce Intelligence] ein. {#stepthree}

1. Geben Sie Ihr [!DNL Zendesk] Site-Präfix und Ihre Anmelde-E-Mail auf der Seite mit den Anmeldedaten für [!DNL Zendesk] in [!DNL Commerce Intelligence] ein.
1. Geben Sie Ihr API-Token ein.
1. Klicken Sie auf **[!UICONTROL Save & Connect]**. Wenn die Verbindung erfolgreich hergestellt wurde, ist eine *Verbindung erfolgreich!Die Meldung* wird oben auf dem Bildschirm angezeigt.

## Verwandte:

* [Erwartete [!DNL Zendesk] Daten](../integrations/exp-zendesk-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
