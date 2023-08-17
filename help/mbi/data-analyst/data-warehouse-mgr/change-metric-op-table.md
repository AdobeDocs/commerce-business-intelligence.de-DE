---
title: Arbeitstabelle einer Metrik ändern
description: Erfahren Sie, wie Sie die Datentabelle ändern, mit der eine Metrik ihren Vorgang ausführt.
exl-id: c7a074ca-31f4-43e5-85d9-b64dca95dc23
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Arbeitstabelle einer Metrik ändern

In bestimmten Fällen können Sie die Datentabelle ändern, mit der eine Metrik ihren Vorgang ausführt. Wenn Sie beispielsweise eine neue Benutzertabelle haben, möchten Sie Ihre benutzerbezogenen Metriken aus dem  `Users\_Old` -Tabelle, die verwendet werden soll `Users\_New` -Tabelle.

1. Navigieren Sie zu **[!UICONTROL Data]** > **[!UICONTROL Metrics]**
1. Klicks **[!UICONTROL Edit]** neben der Metrik, für die Sie die `operational` Tabelle.
1. Klicken Sie im Editor auf **[!UICONTROL Change]**.

   ![](../../assets/change-metrics-1.png)
1. Wählen Sie die neue Tabelle aus, auf der diese Metrik basieren soll.
1. Ordnen Sie die vorhandenen Datendimensionen den entsprechenden Dimensionen in der neuen Tabelle zu. Wenn Sie beispielsweise eine Spalte mit dem Namen `User's registration date`wählen Sie einfach aus, welche Spalte in der neuen Tabelle die gleichen Datumsdaten enthält. (Siehe nächsten Schritt, wenn die neue Tabelle keine übereinstimmenden Spalten enthält)

   ![](../../assets/change-metrics-2.png)

1. Wenn die neue Tabelle keine übereinstimmende Spalte enthält, können Sie entweder **Erstellen in der Datentabelle** oder [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) wenn es sich um eine Berechnungsspalte oder -dimension handelt, die von [!DNL Commerce Intelligence]. Sie können auch **Dimension aus der Metrik löschen**. Um eine Dimension zu löschen, die Sie nicht mehr benötigen, gehen Sie einfach zum Editor der Metrik zurück und wählen Sie unter die zu löschenden Dimensionen aus `Dimensions`.

   ![](../../assets/change-metrics-3.png)
