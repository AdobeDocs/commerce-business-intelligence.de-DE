---
title: Connect Zendesk
description: Erfahren Sie, wie Sie die Helpdesk-Berichte in  [!DNL Commerce Intelligence].
exl-id: 1c7f7c5c-4b1c-4bcf-8f1d-2b4cf9cdb0fb
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/KBUuqTDD9s3qXDktcV3RzLx4zxtAFwAkKPbsQE2YGtI
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 261
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
