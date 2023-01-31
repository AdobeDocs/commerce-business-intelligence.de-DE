---
title: Importieren von Linkshare-Daten
description: Erfahren Sie, wie Sie Linkshare-Daten in importieren [!DNL MBI].
exl-id: 1c2025a6-746c-4929-bbb1-62af1afcbc49
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Import `Linkshare` data

Mit `Linkshare` Daten in [!DNL MBI]müssen Sie zwei Dinge tun:

1. [Exportieren Sie die Linkshare-Daten in ](#export)
1. [Hochladen der Tabelle in [!DNL MBI]](../connecting-data/using-file-uploader.md)

## Daten aus Linkshare exportieren {#export}

1. In `Linkshare` Konto, gehen Sie zu **[!UICONTROL Reports** > **Run Reports].**

1. Im `Report` Dropdown-Liste auswählen **[!UICONTROL Sales & Activity Report]**.

1. Behalten Sie alle anderen Dropdown-Optionen als Standardauswahl bei.

1. Im `Date Range` Dropdown-Liste auswählen, welche Option (`Sun - Sat`, `Mon - Sun`) stimmt mit Ihrer `Start of Week` Einstellungen in [!DNL MBI].

1. Löschen Sie die `Compare Year-Over-Year Data` aktivieren.

1. under `Data Type`auswählen `Transaction Date`.

   ![import\_linkshare\_data.png](../../../assets/importing_linkshare_data.png)

1. Klicken **[!UICONTROL View Report]**.

1. Klicken **[!UICONTROL Download]**.

   An dieser Stelle wird ein `.csv` wird erstellt und heruntergeladen.

Nachdem die Datei heruntergeladen wurde, können Sie sie in [!DNL MBI] mithilfe der [`File Upload` Funktion](../connecting-data/using-file-uploader.md).
