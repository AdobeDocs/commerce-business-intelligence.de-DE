---
title: Importieren von MailChimp-Daten
description: Erfahren Sie, wie Sie MailChimp-Daten in  [!DNL Commerce Intelligence].
exl-id: 5595c6a6-5476-4a0e-a493-ddc32161894e
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/HJJYKfqc1sbslQimSNituG6Pm6wi6QpU-vn6GtKvV-Y
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 274
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

Jede Datei - `Opens`, `Clicks` und `Sent` - sollte als separate Datei in [!DNL Commerce Intelligence] hochgeladen werden. Adobe empfiehlt, die Dateien mit dieser Namenskonvention zu benennen: `MailChimp\_ACTION\_DATE`. Ersetzen Sie `ACTION` durch `Open`, `Click` oder `Sent` und ersetzen Sie `DATE` durch das Exportdatum.

Wenn Sie bereit sind, die Dateien hochzuladen, verwenden Sie die [`File Upload`-Funktion](../connecting-data/using-file-uploader.md) um die Daten in Ihre Data Warehouse zu übertragen.
