---
title: Importieren von Linkshare-Daten
description: Erfahren Sie, wie Sie Linkshare-Daten in importieren [!DNL Commerce Intelligence].
exl-id: 1c2025a6-746c-4929-bbb1-62af1afcbc49
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# Import [!DNL Linkshare] data

Mit [!DNL Linkshare] Daten in [!DNL Adobe Commerce Intelligence]müssen Sie zwei Dinge tun:

1. [Exportieren Sie die Linkshare-Daten in ](#export)
1. [Hochladen der Tabelle in [!DNL Commerce Intelligence]](../connecting-data/using-file-uploader.md)

## Daten aus Linkshare exportieren {#export}

1. In [!DNL Linkshare] Konto, gehen Sie zu **[!UICONTROL Reports** > **Run Reports].**

1. Im `Report` Dropdown-Liste auswählen **[!UICONTROL Sales & Activity Report]**.

1. Behalten Sie alle anderen Dropdown-Optionen als Standardauswahl bei.

1. Im `Date Range` Dropdown-Liste auswählen, welche Option (`Sun - Sat`, `Mon - Sun`) stimmt mit Ihrer `Start of Week` Einstellungen in [!DNL Commerce Intelligence].

1. Löschen Sie die `Compare Year-Over-Year Data` aktivieren.

1. under `Data Type`auswählen `Transaction Date`.

   ![import\_linkshare\_data.png](../../../assets/importing_linkshare_data.png)

1. Klicken **[!UICONTROL View Report]**.

1. Klicken **[!UICONTROL Download]**.

   An dieser Stelle wird ein `.csv` und heruntergeladen.

Nachdem die Datei heruntergeladen wurde, können Sie sie in [!DNL Commerce Intelligence] mithilfe der [`File Upload` Funktion](../connecting-data/using-file-uploader.md).
