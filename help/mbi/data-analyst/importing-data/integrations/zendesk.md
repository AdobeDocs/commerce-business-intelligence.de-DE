---
title: Zendesk verbinden
description: Erfahren Sie, wie Sie Ihre Helpdesk-Berichte konsolidieren in [!DNL Commerce Intelligence].
exl-id: 1c7f7c5c-4b1c-4bcf-8f1d-2b4cf9cdb0fb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Verbinden [!DNL Zendesk]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/Zendesk_logo.png)

Verbinden Ihrer [!DNL Zendesk] Mit den -Daten können Sie Ihre Helpdesk-Berichte in [!DNL Commerce Intelligence]. Auf diese Weise können Sie den Kundensupport optimieren und die Leistung des Helpdesk neben Ihrem Umsatz überwachen.

Verbinden Ihrer [!DNL Zendesk] -Daten sind ein einfacher dreistufiger Prozess:

1. [Öffnen Sie die [!DNL Zendesk] Anmeldeseite in [!DNL Commerce Intelligence]](#stepone)
1. [Abrufen Ihrer [!DNL Zendesk] API-Token](#steptwo)
1. [Geben Sie Ihre [!DNL Zendesk] Anmelde-Info und Token in [!DNL Commerce Intelligence]](#stepthree)

Um diesen Vorgang abzuschließen, müssen Sie zwei Browser-Fenster oder -Registerkarten öffnen - eine für [!DNL Commerce Intelligence], der andere für Ihre [!DNL Zendesk] -Konto.

## Öffnen Sie die [!DNL Zendesk] Anmeldeseite in [!DNL Commerce Intelligence] {#stepone}

1. Navigieren Sie zu `Integrations` Seite unter **[!UICONTROL Manage Data** > ** Data Sources **> **Integrationen]**.
1. Klicken **[!UICONTROL Add Integration]** auf der rechten Seite des Bildschirms.
1. Klicken Sie auf [!DNL Zendesk] Symbol. Dadurch wird die [!DNL Zendesk] Seite mit Anmeldeinformationen.

## Abrufen Ihrer [!DNL Zendesk] API-Token {#steptwo}

1. Im Fenster/auf der Registerkarte, in dem Sie bei Ihrem [!DNL Zendesk] klicken Sie auf das Symbol Einstellungen (Zahnrad) in der linken unteren Ecke des Bildschirms.
1. Wenn die `Settings` angezeigt wird, suchen Sie die `Channels` Abschnitt. Klicken **[!UICONTROL API]** in diesem Abschnitt.
1. Im `Token Access` auf dieser Seite klicken Sie auf das Kontrollkästchen neben `Enabled`. Eine Liste aktiver API-Token wird angezeigt.
1. Klicken **[!UICONTROL Add New Token]**.
1. Geben Sie bei Aufforderung eine Beschriftung für das Token ein. Adobe empfiehlt die Verwendung von `Commerce Intelligence`, sodass Sie auf einen Blick wissen, welche Anwendung das Token verwendet.
1. Klicken **[!UICONTROL Create]**.
1. Es wird ein API-Token erstellt. Kopieren Sie dieses Token. Sie wird im nächsten Schritt verwendet.

## Eingabe [!DNL Zendesk] Anmelde-Info und API-Token in [!DNL Commerce Intelligence] {#stepthree}

1. Geben Sie Ihre [!DNL Zendesk] Site-Präfix und Anmelde-E-Mail im [!DNL Zendesk] Anmeldeseite in [!DNL Commerce Intelligence].
1. Geben Sie Ihr API-Token ein.
1. Klicken **[!UICONTROL Save & Connect]**. Wenn die Verbindung erfolgreich hergestellt wurde, wird ein *Verbindung erfolgreich!* wird oben im Bildschirm angezeigt.

## Verwandte:

* [Erwartet [!DNL Zendesk] data](../integrations/exp-zendesk-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
