---
title: Datendimensionen verwalten
description: Erfahren Sie, was eine Dimension ist und wie sie zum Filtern oder Segmentieren von Diagrammen basierend auf einer Metrik verwendet werden kann.
exl-id: 143a4b1e-2e6f-438a-90e6-bdda13b39cb9
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Datendimensionen verwalten

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Eine Dimension ist ein Feld in derselben Tabelle wie eine Metrik, mit der Diagramme basierend auf dieser Metrik gefiltert oder segmentiert werden können. Eine Umsatzmetrik kann beispielsweise Stadt, Bundesland, Land, Bestellstatus, Couponcode und andere Dimensionstypen enthalten.

## Dimensionen zu mehreren Metriken hinzufügen

So fügen Sie eine oder mehrere Dimensionen gleichzeitig zu mehreren Metriken hinzu:

1. Wechseln Sie zu &quot;**[!UICONTROL Manage Data > Metrics]**&quot;.

1. Klicken Sie auf **[!UICONTROL Add Dimensions To Metric(s)]**.

1. Wählen Sie die Tabelle aus, die die Dimensionen enthält.

1. Wählen Sie in der Spalte `Choose Metric(s) to Add Dimensions` die Metriken aus, denen Sie Dimensionen hinzufügen möchten. Nach der Auswahl wird die Spalte `Choose Dimensions to Add` rechts angezeigt. Überprüfen Sie die Dimensionen, die Sie zur ausgewählten Metrik hinzufügen möchten.

   ![](../../assets/Add_Dimensions.png)

1. Wenn Sie eine Segmentierung oder Gruppierung nach einer der Datendimensionen in Berichten durchführen möchten, geben Sie an, dass es sich um _Groupable_ handelt.

1. Klicken Sie auf **[!UICONTROL Add]**.

## Dimensionen aus mehreren Metriken löschen

So löschen Sie eine oder mehrere Dimensionen aus mehreren Metriken:

1. Wechseln Sie zu &quot;**[!UICONTROL Data > Metrics]**&quot;.

1. Klicken Sie auf **[!UICONTROL Remove Dimensions From Metric(s)]**.

1. Wählen Sie die Tabelle aus, die die Dimensionen enthält.

1. Wählen Sie die Metriken aus, aus denen Sie die Dimensionen links entfernen möchten, und die Dimensionen, die Sie entfernen möchten, auf der rechten Seite.

1. Klicken Sie auf **[!UICONTROL Remove]**.

1. Wenn die Dimensionen in Berichten verwendet werden, wird ein Warnhinweis mit der Liste der Diagramme angezeigt, die die Dimensionen verwenden. Klicken Sie auf **[!UICONTROL Delete]** , um die aktivierten Dimensionen und alle abhängigen Elemente, einschließlich Berichten, zu löschen.

## Dimensionen in Metriken verwalten

**So fügen Sie einer Metrik Dimension(en) hinzu:**

1. Wechseln Sie zu &quot;**[!UICONTROL Data > Metrics]**&quot;.

1. Klicken Sie auf **[!UICONTROL Edit]** für die Metrik, die Sie eine neue Dimension erstellen möchten.

1. Verwenden Sie im Abschnitt `Dimensions` das Dropdown-Menü `Add a dimension` , um eine hinzuzufügende Dimension auszuwählen.

>[!NOTE]
>
>Jede Dimension, nach der Sie filtern oder gruppieren möchten, muss bereits in [!DNL Commerce Intelligence] verfolgt werden. Wenn Sie die gewünschte Dimension nicht finden, müssen Sie möglicherweise mit dem Tracking einer neuen Datenspalte in Ihrer Datenbank über die Seite [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) beginnen.


**So löschen Sie Dimensionen aus einer Metrik:**

1. Wechseln Sie zu &quot;**[!UICONTROL Manage Data > Metrics]**&quot;.

1. Klicken Sie auf **[!UICONTROL Edit]** für die Metrik, die Sie eine neue Dimension erstellen möchten.

1. Aktivieren Sie unter dem Abschnitt `Dimensions` das Kontrollkästchen in der Spalte &quot;Löschen&quot;neben den Dimensionen, die Sie entfernen möchten.

>[!NOTE]
>
>Auch nach dem Löschen einer Dimension ist sie weiterhin als Spalte auf Ihrer Tabelle in Ihrer Data Warehouse vorhanden. Sie können sie wieder zu einer beliebigen Metrik hinzufügen und mithilfe dieser Dimensionen neue Metriken erstellen. Um die Datenspalte zu entfernen, der eine Dimension von [!DNL Commerce Intelligence] entspricht, heben Sie einfach die Datenspalte über die Seite [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) auf.

## Verwandte Dokumentation

* [Best Practices für Segmentierung und Filterung](../../best-practices/segment-filter.md)
