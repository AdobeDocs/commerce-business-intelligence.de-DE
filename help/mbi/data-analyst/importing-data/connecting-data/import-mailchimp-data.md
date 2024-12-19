---
title: Importieren von MailChimp-Daten
description: Erfahren Sie, wie Sie MailChimp-Daten in  [!DNL Commerce Intelligence].
exl-id: 5595c6a6-5476-4a0e-a493-ddc32161894e
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Mailchimp] importieren

Um sich einen umfassenden Überblick über Ihre Kampagnen zu verschaffen, können Sie Ihre [!DNL Mailchimp] E-Mail-Kampagnendaten in [!DNL Commerce Intelligence] importieren. Um den Import abzuschließen, müssen Sie für jede [!DNL Mailchimp] Kampagne, die Sie haben, Folgendes tun:

## Öffnen von Daten exportieren {#opens}

1. Navigieren Sie nach der Anmeldung bei [!DNL Mailchimp] zur Registerkarte `Campaigns` .

   ![Importieren von MailChimp 1](../../../assets/import-mailchimp-1.png)

1. Klicken Sie **[!UICONTROL View Report]** neben dem Kampagnennamen.

   ![Importieren von MailChimp 2](../../../assets/import-mailchimp-2.png)

1. Klicken Sie auf die **[!UICONTROL Opened]**.

   ![Importieren von MailChimp 3](../../../assets/import-mailchimp-3.png)

1. Klicken Sie auf **[!UICONTROL Export]** und speichern Sie die `.csv`.

   Sie müssen dieser Datei `primary key`, `date (mm/dd/yyyy)` und `campaign name` Spalten hinzufügen. Stellen Sie sicher, dass die `primary keys` für jede Zeile eindeutig sind.

   ![Importieren von MailChimp 4](../../../assets/import-mailchimp-4.png)

## Exportieren von Klickdaten {#clicks}

1. Navigieren Sie zurück zum `View Report` für die Kampagne.

1. Klicken Sie auf die `Clicked` Zahl.

   ![Importieren von MailChimp 5](../../../assets/import-mailchimp-5.png)

1. Klicken Sie entweder auf die Zahl unter der Spalte `Total Clicks` ODER `Unique Clicks` .

   ![Importieren von MailChimp 6](../../../assets/import-mailchimp-6.png)

1. Klicken Sie auf **[!UICONTROL Export]** und speichern Sie die `.csv`.

   Sie müssen dieser Datei `Primary Key`, `date (mm/dd/yyyy)`, `campaign name` und `URL` Spalten hinzufügen. Sie müssen nicht die vollständige URL hinzufügen, nur etwas, das Ihnen mitteilt, was angeklickt wurde.

   ![Importieren von MailChimp 7](../../../assets/import-mailchimp-7.png)

1. Wiederholen Sie die Schritte 3 und 4 für jede in Ihrer E-Mail angeklickte URL und kombinieren Sie alle Daten in derselben `.csv`.

## Gesendete Daten exportieren {#sent}

1. Wechseln Sie zur Registerkarte `Campaigns` von [!DNL Mailchimp].

1. Klicken Sie **[!UICONTROL View Report]** neben dem Kampagnennamen.

1. Klicken Sie auf die Zahl neben `Recipients`.

   ![Importieren von MailChimp 8](../../../assets/import-mailchimp-8.png)

1. Klicken Sie auf **[!UICONTROL Export]** und speichern Sie die `.csv`.

   Sie müssen dieser Datei `Primary Key`, `date (mm/dd/yyyy)` und `campaign name` Spalten hinzufügen.

   ![Importieren von MailChimp 9](../../../assets/import-mailchimp-9.png)

## Vorbereiten von Dateien für den Upload in [!DNL Commerce Intelligence] {#upload}

Jede Datei - `Opens`, `Clicks` und `Sent` - sollte als separate Datei in [!DNL Commerce Intelligence] hochgeladen werden. Adobe empfiehlt, die Dateien nach dieser Namenskonvention zu benennen: `MailChimp\_ACTION\_DATE`. Ersetzen Sie `ACTION` durch `Open`, `Click` oder `Sent` und ersetzen Sie `DATE` durch das Exportdatum.

Wenn Sie bereit sind, die Dateien hochzuladen, verwenden Sie die [`File Upload`-Funktion](../connecting-data/using-file-uploader.md) um die Daten auf Ihren Data Warehouse zu bringen.
