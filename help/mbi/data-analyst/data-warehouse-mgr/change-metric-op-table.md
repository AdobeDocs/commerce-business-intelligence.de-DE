---
title: Operationstabelle einer Metrik ändern
description: Erfahren Sie, wie Sie die Datentabelle ändern, die eine Metrik verwendet, um ihren Vorgang auszuführen.
exl-id: c7a074ca-31f4-43e5-85d9-b64dca95dc23
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/9yJ1Zc2NLDvXYO16UvDkeWE0hD1jx0-Ne3AyFFHX5ns
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 02934da4962380494ab8a2becf5f06efb15d84dc
workflow-type: tm+mt
source-wordcount: 244
ht-degree: 0%

---

# Operationstabelle einer Metrik ändern

In bestimmten Fällen können Sie sich entscheiden, die Datentabelle zu ändern, die eine Metrik verwendet, um ihren Vorgang auszuführen. Wenn Sie beispielsweise über eine neue Benutzertabelle verfügen, möchten Sie Ihre benutzerbezogenen Metriken aus der `Users\_Old` migrieren, um stattdessen die `Users\_New` zu verwenden.

1. Navigieren Sie zu **[!UICONTROL Data]** > **[!UICONTROL Metrics]**
1. Klicken Sie **[!UICONTROL Edit]** neben der Metrik, für die Sie die `operational` wechseln möchten.
1. Klicken Sie im Editor auf **[!UICONTROL Change]**.

   ![Seite zur Metrikdefinition mit der Einstellung der Operationstabelle](../../assets/change-metrics-1.png)
1. Wählen Sie die neue Tabelle aus, auf der Sie diese Metrik basieren möchten.
1. Ordnen Sie die vorhandenen Datendimensionen den entsprechenden Dimensionen in der neuen Tabelle zu. Wenn Sie beispielsweise eine Spalte mit dem Namen `User's registration date` haben, wählen Sie einfach aus, welche Spalte in der neuen Tabelle dieselben Datumsdaten aufzeichnet. (Siehe nächster Schritt, wenn die neue Tabelle keine übereinstimmenden Spalten enthält)

   ![Dropdown-Liste zur Tabellenauswahl mit verfügbaren Tabellen](../../assets/change-metrics-2.png)

1. Wenn in der neuen Tabelle keine entsprechende Spalte vorhanden ist, können Sie diese entweder **in Ihrer Datentabelle erstellen** oder [Support kontaktieren](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies) wenn es sich um eine von [!DNL Commerce Intelligence] erstellte Berechnungsspalte oder Dimension handelt. Sie können auch **Dimension aus der Metrik löschen**. Um eine nicht mehr benötigte Dimension zu löschen, gehen Sie einfach zurück zum Editor der Metrik und wählen Sie unter `Dimensions` aus, welche Dimensionen gelöscht werden sollen.

   ![Dropdown-Menü für die operative Spaltenauswahl](../../assets/change-metrics-3.png)
