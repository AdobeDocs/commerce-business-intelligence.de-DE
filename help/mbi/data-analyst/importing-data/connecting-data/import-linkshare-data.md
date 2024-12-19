---
title: Importieren von Linkshare-Daten
description: Erfahren Sie, wie Sie Linkshare-Daten in  [!DNL Commerce Intelligence].
exl-id: 1c2025a6-746c-4929-bbb1-62af1afcbc49
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# [!DNL Linkshare] importieren

Um Ihre [!DNL Linkshare]-Daten in [!DNL Adobe Commerce Intelligence] einzubringen, müssen Sie zwei Dinge tun:

1. [Exportieren der Linkshare-Daten in ](#export)
1. [Tabelle hochladen in [!DNL Commerce Intelligence]](../connecting-data/using-file-uploader.md)

## Exportieren von Daten aus Linkshare {#export}

1. Navigieren Sie in Ihrem [!DNL Linkshare]-Konto zu **[!UICONTROL Reports** > **Run Reports].**

1. Wählen Sie in der Dropdown-Liste `Report` die Option **[!UICONTROL Sales & Activity Report]** aus.

1. Belassen Sie alle anderen Dropdown-Optionen als Standardauswahl.

1. Wählen Sie in der Dropdown-Liste `Date Range` aus, welche Option (`Sun - Sat`, `Mon - Sun`) Ihren `Start of Week` in [!DNL Commerce Intelligence] entspricht.

1. Deaktivieren Sie das Kontrollkästchen `Compare Year-Over-Year Data` .

1. Wählen Sie unter `Data Type` die Option `Transaction Date`.

   ![import\_linkshare\_data.png](../../../assets/importing_linkshare_data.png)

1. Klicken Sie auf **[!UICONTROL View Report]**.

1. Klicken Sie auf **[!UICONTROL Download]**.

   An dieser Stelle wurde eine `.csv`-Datei heruntergeladen und.

Nachdem die Datei heruntergeladen wurde, können Sie sie mit der [`File Upload`-Funktion in [!DNL Commerce Intelligence] hochladen](../connecting-data/using-file-uploader.md).
