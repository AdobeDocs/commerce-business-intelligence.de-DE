---
title: Importieren von MailChimp-Daten
description: Informationen zum Importieren von MailChimp-Daten in [!DNL MBI].
exl-id: 5595c6a6-5476-4a0e-a493-ddc32161894e
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Import `MailChimp` data

Um ein umfassendes Bild Ihrer Kampagnenbemühungen zu erhalten, können Sie Ihre `MailChimp` E-Mail-Kampagnendaten in [!DNL MBI]. Um den Import abzuschließen, müssen Sie für jede `MailChimp` Kampagne:

## Exportieren von Daten zu Öffnungen {#opens}

1. Nach der Anmeldung bei `MailChimp`, navigieren Sie zu `Campaigns` Registerkarte.

   ![import mailchimp 1](../../../assets/import-mailchimp-1.png)

1. Klicken **[!UICONTROL View Report]** neben dem Kampagnennamen.

   ![import mailchimp 2](../../../assets/import-mailchimp-2.png)

1. Klicken Sie auf **[!UICONTROL Opened]** Zahl.

   ![import mailchimp 3](../../../assets/import-mailchimp-3.png)

1. Klicken **[!UICONTROL Export]** und speichern Sie die `.csv` -Datei.

   Sie müssen `primary key`, `date (mm/dd/yyyy)`und `campaign name` -Spalten zu dieser Datei. Stellen Sie sicher, dass `primary keys` sind für jede Zeile eindeutig.

   ![import mailchimp 4](../../../assets/import-mailchimp-4.png)

## Klickdaten exportieren {#clicks}

1. Navigieren Sie zurück zum `View Report` -Bildschirm für die Kampagne.

1. Klicken Sie auf die Zahl, die `Clicked`.

   ![import mailchimp 5](../../../assets/import-mailchimp-5.png)

1. Klicken Sie auf ENTWEDER auf die Zahl unter `Total Clicks` ODER `Unique Clicks` Spalte.

   ![import mailchimp 6](../../../assets/import-mailchimp-6.png)

1. Klicken **[!UICONTROL Export]** und speichern Sie die `.csv` -Datei.

   Sie müssen `Primary Key`, `date (mm/dd/yyyy)`, `campaign name`und `URL` -Spalten zu dieser Datei. Sie müssen nicht die vollständige URL hinzufügen, sondern nur etwas, das Ihnen mitteilt, worauf geklickt wurde.

   ![import mailchimp 7](../../../assets/import-mailchimp-7.png)

1. Wiederholen Sie die Schritte 3 und 4 für jede in Ihrer E-Mail angeklickte URL, wobei Sie alle Daten zu derselben URL kombinieren `.csv` -Datei.

## Versanddaten exportieren {#sent}

1. Wechseln Sie zu `Campaigns` Registerkarte von MailChimp.

1. Klicken **[!UICONTROL View Report]** neben dem Kampagnennamen.

1. Klicken Sie auf die Zahl neben `Recipients`.

   ![import mailchimp 8](../../../assets/import-mailchimp-8.png)

1. Klicken **[!UICONTROL Export]** und speichern Sie die `.csv` -Datei.

   Sie müssen `Primary Key`, `date (mm/dd/yyyy)`und `campaign name` -Spalten zu dieser Datei.

   ![import mailchimp 9](../../../assets/import-mailchimp-9.png)

## Vorbereiten von Dateien auf den Upload in [!DNL MBI] {#upload}

Jede Datei - `Opens`, `Clicks`und `Sent` - sollte in hochgeladen werden. [!DNL MBI] als separate Datei. Adobe empfiehlt, die Dateien mithilfe dieser Benennungsregel zu benennen: `MailChimp\_ACTION\_DATE`. Ersetzen `ACTION` mit `Open`, `Click`oder `Sent`und ersetzen `DATE` mit dem Datum der Ausfuhr.

Wenn Sie zum Hochladen der Dateien bereit sind, verwenden Sie die [`File Upload` Funktion](../connecting-data/using-file-uploader.md) , um die Daten in Ihre Data Warehouse zu übertragen.
