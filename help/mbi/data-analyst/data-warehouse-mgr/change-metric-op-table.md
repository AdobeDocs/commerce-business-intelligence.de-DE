---
title: Operationstabelle einer Metrik ändern
description: Erfahren Sie, wie Sie die Datentabelle ändern, die eine Metrik verwendet, um ihren Vorgang auszuführen.
exl-id: c7a074ca-31f4-43e5-85d9-b64dca95dc23
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '231'
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

1. Wenn in der neuen Tabelle keine entsprechende Spalte vorhanden ist, können Sie diese entweder **in Ihrer Datentabelle erstellen** oder [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) wenn es sich um eine von [!DNL Commerce Intelligence] erstellte Berechnungsspalte oder Dimension handelt. Sie können auch **Dimension aus der Metrik löschen**. Um eine nicht mehr benötigte Dimension zu löschen, gehen Sie einfach zurück zum Editor der Metrik und wählen Sie unter `Dimensions` aus, welche Dimensionen gelöscht werden sollen.

   ![Dropdown-Menü für die operative Spaltenauswahl](../../assets/change-metrics-3.png)
