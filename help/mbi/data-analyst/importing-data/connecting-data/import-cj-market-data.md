---
title: Importieren von Marketing-Daten der CJ-Tochtergesellschaft (Commission Junction)
description: Erfahren Sie, wie Sie Daten von CJ Affiliate (Commission Junction) in  [!DNL Commerce Intelligence].L Commerce Intelligence] importieren.
exl-id: 1db83f34-15a1-4599-ab0a-65d527ccae01
TQID: https://experienceleague.adobe.com/tZ2fzAKou0fBmkmKD5zdLFBNCSiAGpT3GNgkHp9ptx4
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 141
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
