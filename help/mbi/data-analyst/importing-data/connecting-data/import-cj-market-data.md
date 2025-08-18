---
title: Importieren von Marketing-Daten der CJ-Tochtergesellschaft (Commission Junction)
description: Erfahren Sie, wie Sie Daten von CJ Affiliate (Commission Junction) in  [!DNL Commerce Intelligence].L Commerce Intelligence] importieren.
exl-id: 1db83f34-15a1-4599-ab0a-65d527ccae01
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# [!DNL CJ Affiliate] importieren

Um [!DNL CJ Affiliate (Commission Junction)] Daten in [!DNL Adobe Commerce Intelligence] zu importieren, führen Sie einfach die folgenden Schritte aus und fügen Sie die entsprechende Datei an ein [Support-Ticket“ ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html). Adobe richtet die Datentabelle für Ihr Konto ein und ermöglicht es Ihnen, Daten unabhängig hochzuladen.

## [!DNL CJ Affiliate] exportieren

1. Rufen Sie in Ihrem [!DNL CJ Affiliate]-Konto die Registerkarte `Reports` auf.

1. Wählen Sie auf der Registerkarte `Performance` die Option `Report Options` aus.

1. Legen Sie `Performance By` auf `Program`, `Trend` auf `Daily` und `Date Range` auf den geprüften Datumsbereich fest.

   ![export-cj-afffiliate-data](../../../assets/export-cj-affiliate-data-1.png)<!--{:.zoom}-->

1. Wählen Sie `Run Report` aus.

1. Wählen Sie in der Dropdown-Liste `File Format` die Option `CSV` aus.  Klicken Sie auf **[!UICONTROL Download]**.

   ![Exportieren von CJ-Affiliate-Daten](../../../assets/export-an-individual-order-2.jpg)<!--{:.zoom}-->

1. Nachdem Sie die Datei heruntergeladen haben, können Sie [die Datei hochladen](../connecting-data/using-file-uploader.md) in Ihre [!DNL Commerce Intelligence] Data Warehouse hochladen.

   Dadurch wird in Ihrer [!DNL Commerce Intelligence] Data Warehouse eine Tabelle erstellt, in die Sie weiterhin regelmäßig neue Daten hochladen können. Befolgen Sie beim Hochladen der Datei die unter [Verwenden des Datei-Uploaders](../connecting-data/using-file-uploader.md) aufgeführten Formatierungsanforderungen.
