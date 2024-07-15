---
title: Importieren von Linkshare-Daten
description: Erfahren Sie, wie Sie Linkshare-Daten in [!DNL Commerce Intelligence] importieren.
exl-id: 1c2025a6-746c-4929-bbb1-62af1afcbc49
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# [!DNL Linkshare] Daten importieren

Um Ihre [!DNL Linkshare] -Daten in [!DNL Adobe Commerce Intelligence] zu übertragen, müssen Sie zwei Schritte durchführen:

1. [Exportieren Sie die Linkshare-Daten in ](#export)
1. [Hochladen der Tabelle in  [!DNL Commerce Intelligence]](../connecting-data/using-file-uploader.md)

## Daten aus Linkshare exportieren {#export}

1. Gehen Sie in Ihrem [!DNL Linkshare]-Konto zu **[!UICONTROL Reports** > **Run Reports].**

1. Wählen Sie im Dropdown-Menü `Report` die Option **[!UICONTROL Sales & Activity Report]** aus.

1. Behalten Sie alle anderen Dropdown-Optionen als Standardauswahl bei.

1. Wählen Sie im Dropdown-Menü `Date Range` aus, welche Option (`Sun - Sat`, `Mon - Sun`) mit Ihren `Start of Week`-Einstellungen in [!DNL Commerce Intelligence] übereinstimmt.

1. Deaktivieren Sie das Kontrollkästchen `Compare Year-Over-Year Data` .

1. Wählen Sie unter &quot;`Data Type`&quot;die Option &quot;`Transaction Date`&quot;.

   ![Importieren\_linkshare\_data.png](../../../assets/importing_linkshare_data.png)

1. Klicken Sie auf **[!UICONTROL View Report]**.

1. Klicken Sie auf **[!UICONTROL Download]**.

   An dieser Stelle wurde eine `.csv` -Datei heruntergeladen.

Nachdem die Datei heruntergeladen wurde, können Sie sie mit der Funktion [`File Upload` ](../connecting-data/using-file-uploader.md) in [!DNL Commerce Intelligence] hochladen.
