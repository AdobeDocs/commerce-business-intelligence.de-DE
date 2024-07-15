---
title: Stripe verbinden
description: Erfahren Sie, wie Sie die Zahlungs- und Rechnungsdaten Ihres Unternehmens verwalten und verfolgen können.
exl-id: c038f2a9-b2bd-4e45-93f9-12d2e5077b31
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# [!DNL Stripe] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/stripe-logo.png)

Mit [!DNL Stripe] können Sie die Zahlungs- und Rechnungsdaten Ihres Unternehmens verwalten und verfolgen. Das Verbinden Ihres [!DNL Stripe]-Kontos mit [!DNL Commerce Intelligence] ist ein einfacher zweistufiger Prozess:

1. [Hinzufügen von [!DNL Stripe] als Datenquelle in  [!DNL Commerce Intelligence]](#stepone)
1. [Zugriff auf Ihre [!DNL Stripe] Daten zulassen [!DNL Commerce Intelligence] ](#steptwo)

## Hinzufügen von [!DNL Stripe] als Datenquelle {#stepone}

1. Wechseln Sie zur Seite `Connections` unter **[!UICONTROL Admin** > **Connections]**.
1. Klicken Sie auf **[!UICONTROL Add a Data Source]** rechts neben dem Bildschirm über der Tabelle `Data Sources`.
1. Klicken Sie auf das Symbol &quot;[!DNL Stripe]&quot;. Dadurch wird die Seite &quot;`[!DNL Stripe] authorization`&quot;angezeigt.
1. Klicken Sie auf **[!UICONTROL Connect with Stripe]**.

## [!DNL Commerce Intelligence] Zugriff auf Ihre [!DNL Stripe] -Daten zulassen {#steptwo}

Nachdem Sie auf **[!UICONTROL Connect with Stripe]** geklickt haben, wird eine Seite mit einer Zugriffsanfrage angezeigt.

1. Klicken Sie auf **[!UICONTROL Sign in with Stripe to Continue]**.

1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf **[!UICONTROL Sign in to your account]**.

1. Ihre Anmeldedaten werden validiert und Sie werden zurück zu [!DNL Commerce Intelligence] geleitet.

1. Wenn die Verbindung erfolgreich hergestellt wurde, ist eine *Verbindung erfolgreich!Die Meldung* wird oben auf dem Bildschirm angezeigt.

## Verwandte:

Die [[!DNL Stripe] API-Dokumentation](https://stripe.com/docs/api) kann eine nützliche Ressource sein, um mehr darüber zu erfahren, wie [!DNL Stripe] in [!DNL Commerce Intelligence] integriert ist.

* [Erwartete [!DNL Stripe] Daten](../integrations/stripe-data.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
