---
title: Importieren von Marketing-Daten für CJ Affiliate (Dienststelle der Kommission)
description: Erfahren Sie, wie Sie CJ Affiliate-Daten (Commission Junktion) in importieren [!DNL Commerce Intelligence].L Commerce Intelligence].
exl-id: 1db83f34-15a1-4599-ab0a-65d527ccae01
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Import [!DNL CJ Affiliate] data

Zu importieren [!DNL CJ Affiliate (Commission Junction)] Daten in [!DNL Adobe Commerce Intelligence]führen Sie einfach die folgenden Schritte aus und fügen Sie die resultierende Datei an eine [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html). Adobe richtet die Datentabelle Ihres Kontos ein und ermöglicht es Ihnen, das Hochladen von Daten unabhängig fortzusetzen.

## Export [!DNL CJ Affiliate] Daten

1. In der [!DNL CJ Affiliate] -Konto, navigieren Sie zum `Reports` Registerkarte.

1. Im `Performance` Registerkarte auswählen `Report Options`.

1. Satz `Performance By` gleich `Program`, `Trend` gleich `Daily`, und `Date Range` entspricht dem geprüften Datumsbereich.

   ![export-cj-Affiliate-data](../../../assets/export-cj-affiliate-data-1.png)<!--{:.zoom}-->

1. Auswählen `Run Report`.

1. Im `File Format` Dropdown-Liste auswählen `CSV`.  Klicken **[!UICONTROL Download]**.

   ![Export von CJ-Partnerdaten](../../../assets/export-an-individual-order-2.jpg)<!--{:.zoom}-->

1. Nach dem Herunterladen der Datei können Sie [Datei hochladen](../connecting-data/using-file-uploader.md) auf [!DNL Commerce Intelligence] Data Warehouse.

   Dadurch wird eine Tabelle in Ihrem [!DNL Commerce Intelligence] Data Warehouse, dass Sie weiterhin neue Daten regelmäßig hochladen können. Befolgen Sie beim Hochladen der Datei die Formatierungsanforderungen, die unter [Verwenden des Datei-Uploaders](../connecting-data/using-file-uploader.md).
