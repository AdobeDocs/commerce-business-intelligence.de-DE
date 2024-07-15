---
title: Importieren von MailChimp-Daten
description: Erfahren Sie, wie Sie MailChimp-Daten in [!DNL Commerce Intelligence] importieren.
exl-id: 5595c6a6-5476-4a0e-a493-ddc32161894e
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Mailchimp] Daten importieren

Um ein umfassendes Bild Ihrer Kampagnenbemühungen zu erhalten, können Sie Ihre [!DNL Mailchimp] E-Mail-Kampagnendaten in [!DNL Commerce Intelligence] importieren. Um den Import abzuschließen, müssen Sie für jede vorhandene [!DNL Mailchimp]-Kampagne die folgenden Schritte ausführen:

## Exportieren von Daten zu Öffnungen {#opens}

1. Gehen Sie nach dem Anmelden bei [!DNL Mailchimp] zur Registerkarte `Campaigns` .

   ![import mailchimp 1](../../../assets/import-mailchimp-1.png)

1. Klicken Sie neben dem Kampagnennamen auf **[!UICONTROL View Report]**.

   ![import mailchimp 2](../../../assets/import-mailchimp-2.png)

1. Klicken Sie auf die Nummer **[!UICONTROL Opened]** .

   ![import mailchimp 3](../../../assets/import-mailchimp-3.png)

1. Klicken Sie auf &quot;**[!UICONTROL Export]**&quot;und speichern Sie die Datei &quot;`.csv`&quot;.

   Sie müssen dieser Datei die Spalten `primary key`, `date (mm/dd/yyyy)` und `campaign name` hinzufügen. Stellen Sie sicher, dass die `primary keys` für jede Zeile eindeutig sind.

   ![import mailchimp 4](../../../assets/import-mailchimp-4.png)

## Klickdaten exportieren {#clicks}

1. Navigieren Sie zurück zum Bildschirm `View Report` für die Kampagne.

1. Klicken Sie auf die Zahl &quot;`Clicked`&quot;.

   ![import mailchimp 5](../../../assets/import-mailchimp-5.png)

1. Klicken Sie entweder auf die Zahl unter der Spalte `Total Clicks` ODER `Unique Clicks` .

   ![import mailchimp 6](../../../assets/import-mailchimp-6.png)

1. Klicken Sie auf &quot;**[!UICONTROL Export]**&quot;und speichern Sie die Datei &quot;`.csv`&quot;.

   Sie müssen dieser Datei die Spalten `Primary Key`, `date (mm/dd/yyyy)`, `campaign name` und `URL` hinzufügen. Sie müssen nicht die vollständige URL hinzufügen, sondern nur etwas, das Ihnen mitteilt, worauf geklickt wurde.

   ![import mailchimp 7](../../../assets/import-mailchimp-7.png)

1. Wiederholen Sie die Schritte 3 und 4 für jede in Ihrer E-Mail angeklickte URL, wobei Sie alle Daten zum Abschluss in derselben `.csv`-Datei zusammenfassen.

## Versanddaten exportieren {#sent}

1. Gehen Sie in den Tab `Campaigns` von [!DNL Mailchimp].

1. Klicken Sie neben dem Kampagnennamen auf **[!UICONTROL View Report]** .

1. Klicken Sie auf die Zahl neben `Recipients`.

   ![import mailchimp 8](../../../assets/import-mailchimp-8.png)

1. Klicken Sie auf &quot;**[!UICONTROL Export]**&quot;und speichern Sie die Datei &quot;`.csv`&quot;.

   Sie müssen dieser Datei die Spalten `Primary Key`, `date (mm/dd/yyyy)` und `campaign name` hinzufügen.

   ![import mailchimp 9](../../../assets/import-mailchimp-9.png)

## Vorbereiten von Dateien auf den Upload in [!DNL Commerce Intelligence] {#upload}

Jede Datei - `Opens`, `Clicks` und `Sent` - sollte als separate Datei in [!DNL Commerce Intelligence] hochgeladen werden. Adobe empfiehlt, die Dateien mit dieser Namenskonvention zu benennen: `MailChimp\_ACTION\_DATE`. Ersetzen Sie `ACTION` durch `Open`, `Click` oder `Sent` und ersetzen Sie `DATE` durch das Datum des Exports.

Wenn Sie zum Hochladen der Dateien bereit sind, verwenden Sie die [`File Upload`-Funktion](../connecting-data/using-file-uploader.md) , um die Daten in Ihre Data Warehouse zu übertragen.
