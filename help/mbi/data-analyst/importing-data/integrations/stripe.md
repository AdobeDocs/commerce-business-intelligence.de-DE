---
title: Verbindungsstreifen
description: Erfahren Sie, wie Sie die Zahlungs- und Rechnungsdaten Ihres Unternehmens verwalten und verfolgen können.
exl-id: c038f2a9-b2bd-4e45-93f9-12d2e5077b31
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Verbindungsstreifen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/stripe-logo.png)

[!DNL Stripe] ermöglicht Ihnen, die Zahlungs- und Rechnungsdaten Ihres Unternehmens zu verwalten und zu verfolgen. Verbinden Ihrer [!DNL Stripe] Konto [!DNL MBI] ist ein einfacher zweistufiger Prozess:

1. [Hinzufügen [!DNL Stripe] als Datenquelle in [!DNL MBI]](#stepone)
1. [Zulassen [!DNL MBI] Zugriff auf Ihre [!DNL Stripe] Daten](#steptwo)

## Hinzufügen [!DNL Stripe] als Datenquelle {#stepone}

1. Navigieren Sie zu `Connections` Seite unter **[!UICONTROL Admin** > **Connections]**.
1. Klicken **[!UICONTROL Add a Data Source]** auf der rechten Seite des Bildschirms über dem `Data Sources` Tabelle.
1. Klicken Sie auf [!DNL Stripe] Symbol. Dadurch wird die `[!DNL Stripe] authorization` Seite.
1. Klicken **[!UICONTROL Connect with Stripe]**.

## Zulassen [!DNL MBI] Zugriff auf Ihre [!DNL Stripe] data {#steptwo}

Nach dem Klicken **[!UICONTROL Connect with Stripe]**, wird eine Seite mit Zugriffsanfragen angezeigt.

1. Klicken **[!UICONTROL Sign in with Stripe to Continue]**.

1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf **[!UICONTROL Sign in to your account]**.

1. Nach dem Klicken werden Ihre Anmeldedaten validiert und Sie werden zu [!DNL MBI].

1. Wenn die Verbindung erfolgreich hergestellt wurde, wird ein *Verbindung erfolgreich!* wird oben auf dem Bildschirm angezeigt.

## Verwandte:

Wenn man ein bisschen technisch versiert ist, ist die [[!DNL Stripe] API-Dokumentation](https://stripe.com/docs/api) kann eine nützliche Ressource sein, um mehr darüber zu erfahren, wie [!DNL Stripe] ist integriert in [!DNL MBI].

* [Erwartet [!DNL Stripe] data](../integrations/stripe-data.md)
* [Erneutes Authentifizieren von Integrationen](https://support.magento.com/hc/en-us/articles/360016733151)
