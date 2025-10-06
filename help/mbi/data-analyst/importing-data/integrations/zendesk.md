---
title: Connect Zendesk
description: Erfahren Sie, wie Sie die Helpdesk-Berichte in  [!DNL Commerce Intelligence].
exl-id: 1c7f7c5c-4b1c-4bcf-8f1d-2b4cf9cdb0fb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# [!DNL Zendesk] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Zendesk-Logo](../../../assets/Zendesk_logo.png)

Durch das Verbinden Ihrer [!DNL Zendesk] können Sie die Helpdesk-Berichte in [!DNL Commerce Intelligence] konsolidieren. Auf diese Weise können Sie den Kunden-Support optimieren und die Helpdesk-Leistung neben Ihrem Umsatz überwachen.

Die Verbindung Ihrer [!DNL Zendesk] ist ein einfacher dreistufiger Prozess:

1. [Öffnen Sie die  [!DNL Zendesk] Anmeldeinformationen“ in  [!DNL Commerce Intelligence]](#stepone)
1. [Abrufen Ihres  [!DNL Zendesk] -API-Tokens](#steptwo)
1. [Geben Sie Ihre  [!DNL Zendesk] -Anmeldeinformationen und Ihr Token in ein [!DNL Commerce Intelligence]](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browser-Fenster oder Registerkarten öffnen - eines für [!DNL Commerce Intelligence], das andere für Ihr [!DNL Zendesk].

## Öffnen Sie die Seite [!DNL Zendesk] in [!DNL Commerce Intelligence] {#stepone}

1. Navigieren Sie zur `Integrations` unter **[!UICONTROL Manage Data** > **&#x200B; Datenquellen &#x200B;**> **Integrationen]**.
1. Klicken Sie auf **[!UICONTROL Add Integration]** rechts im Bildschirm.
1. Klicken Sie auf das Symbol [!DNL Zendesk] . Dadurch wird die Seite mit den [!DNL Zendesk]-Anmeldeinformationen geöffnet.

## Abrufen Ihres [!DNL Zendesk] API-Tokens {#steptwo}

1. Klicken Sie im Fenster/in der Registerkarte, in dem/der Sie bei Ihrem [!DNL Zendesk]-Konto angemeldet sind, auf das Zahnradsymbol in der linken unteren Ecke des Bildschirms.
1. Wenn das `Settings` angezeigt wird, suchen Sie den `Channels`. Klicken Sie in diesem Abschnitt auf **[!UICONTROL API]** .
1. Klicken Sie im `Token Access` Abschnitt dieser Seite auf das Kontrollkästchen neben `Enabled`. Eine Liste der aktiven API-Token wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Add New Token]**.
1. Geben Sie bei Aufforderung einen Titel für das Token ein. Adobe empfiehlt die Verwendung von `Commerce Intelligence`, damit Sie auf einen Blick wissen, welche Anwendung das Token verwendet.
1. Klicken Sie auf **[!UICONTROL Create]**.
1. Ein API-Token wird erstellt. Kopieren Sie dieses Token. Es wird im nächsten Schritt verwendet.

## [!DNL Zendesk] Anmeldeinformationen und API-Token in [!DNL Commerce Intelligence] eingeben {#stepthree}

1. Geben Sie das Präfix Ihrer [!DNL Zendesk]-Site und Ihre Anmelde-E-Mail auf der Seite mit den [!DNL Zendesk]-Anmeldeinformationen in [!DNL Commerce Intelligence] ein.
1. Geben Sie Ihr API-Token ein.
1. Klicken Sie auf **[!UICONTROL Save & Connect]**. Wenn die Verbindung erfolgreich hergestellt wurde, wählen Sie *Verbindung erfolgreich!* Meldung wird oben im Bildschirm angezeigt.

## Verwandt:

* [&#x200B; [!DNL Zendesk]  Daten](../integrations/exp-zendesk-data.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
