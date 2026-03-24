---
title: Importieren von Linkshare-Daten
description: Erfahren Sie, wie Sie Linkshare-Daten in  [!DNL Commerce Intelligence].
exl-id: 1c2025a6-746c-4929-bbb1-62af1afcbc49
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/TsQYXEwH-8m1rpKg6It8wa-B2eQH0oqDkLcgx-tRBWU
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 94
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

Nachdem die Datei heruntergeladen wurde, können Sie sie mit der [!DNL Commerce Intelligence]-Funktion in [`File Upload` hochladen](../connecting-data/using-file-uploader.md).
