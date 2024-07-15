---
title: Importieren von Marketing-Daten für CJ Affiliate (Dienststelle der Kommission)
description: Erfahren Sie, wie Sie CJ Affiliate-Daten (Commission Junktion) in [!DNL Commerce Intelligence].L Commerce Intelligence importieren.
exl-id: 1db83f34-15a1-4599-ab0a-65d527ccae01
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# [!DNL CJ Affiliate] Daten importieren

Um [!DNL CJ Affiliate (Commission Junction)] Daten in [!DNL Adobe Commerce Intelligence] zu importieren, führen Sie einfach die folgenden Schritte aus und hängen Sie die resultierende Datei an ein [Supportticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) an. Adobe richtet die Datentabelle Ihres Kontos ein und ermöglicht es Ihnen, das Hochladen von Daten unabhängig fortzusetzen.

## Exportieren von [!DNL CJ Affiliate] Daten

1. Gehen Sie in Ihrem [!DNL CJ Affiliate] -Konto zur Registerkarte `Reports` .

1. Wählen Sie auf der Registerkarte `Performance` die Option `Report Options` aus.

1. Setzen Sie `Performance By` gleich `Program`, `Trend` gleich `Daily` und `Date Range` gleich dem geprüften Datumsbereich.

   ![export-cj-Affiliate-data](../../../assets/export-cj-affiliate-data-1.png)<!--{:.zoom}-->

1. Wählen Sie `Run Report` aus.

1. Wählen Sie im Dropdown-Menü `File Format` die Option `CSV` aus.  Klicken Sie auf **[!UICONTROL Download]**.

   ![cj-Partnerdaten exportieren](../../../assets/export-an-individual-order-2.jpg)<!--{:.zoom}-->

1. Nachdem Sie die Datei heruntergeladen haben, können Sie [die Datei](../connecting-data/using-file-uploader.md) auf Ihre [!DNL Commerce Intelligence]-Data Warehouse hochladen.

   Dadurch wird eine Tabelle in Ihrer [!DNL Commerce Intelligence]-Data Warehouse erstellt, in die Sie weiterhin neue Daten regelmäßig hochladen können. Befolgen Sie beim Hochladen der Datei die unter [Verwenden des Datei-Uploaders](../connecting-data/using-file-uploader.md) aufgeführten Formatierungsanforderungen.
