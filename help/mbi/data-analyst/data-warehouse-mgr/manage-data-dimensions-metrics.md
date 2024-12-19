---
title: Verwalten von Datendimensionen
description: Erfahren Sie, was eine Dimension ist und wie sie verwendet werden kann, um Diagramme basierend auf einer Metrik zu filtern oder zu segmentieren.
exl-id: 143a4b1e-2e6f-438a-90e6-bdda13b39cb9
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Verwalten von Datendimensionen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Eine Dimension ist ein Feld in derselben Tabelle wie eine Metrik, das zum Filtern oder Segmentieren von Diagrammen basierend auf dieser Metrik verwendet werden kann. Beispielsweise kann eine Umsatzmetrik Stadt, Bundesland, Land, Bestellstatus, Couponcode und andere Arten von Dimensionen enthalten.

## Hinzufügen von Dimensionen zu mehreren Metriken

So fügen Sie einer oder mehreren Dimensionen mehreren Metriken gleichzeitig hinzu:

1. Gehe zu **[!UICONTROL Manage Data > Metrics]**.

1. Klicken Sie auf **[!UICONTROL Add Dimensions To Metric(s)]**.

1. Wählen Sie die Tabelle aus, die die Dimensionen enthält.

1. Wählen Sie in der Spalte `Choose Metric(s) to Add Dimensions` die Metriken aus, denen Sie Dimensionen hinzufügen möchten. Nach der Auswahl wird die Spalte `Choose Dimensions to Add` rechts angezeigt. Markieren Sie die Dimensionen, die Sie zur ausgewählten Metrik hinzufügen möchten.

   ![](../../assets/Add_Dimensions.png)

1. Wenn Sie nach einer der Datendimensionen in Berichten segmentieren oder gruppieren möchten, stellen Sie sicher, dass Sie angeben, dass sie &quot;_&quot;_.

1. Klicken Sie auf **[!UICONTROL Add]**.

## Löschen von Dimensionen aus mehreren Metriken

So löschen Sie eine oder mehrere Dimensionen aus mehreren Metriken:

1. Gehe zu **[!UICONTROL Data > Metrics]**.

1. Klicken Sie auf **[!UICONTROL Remove Dimensions From Metric(s)]**.

1. Wählen Sie die Tabelle aus, die die Dimensionen enthält.

1. Wählen Sie links die Metriken aus, aus denen Sie die Dimensionen entfernen möchten, und rechts die Dimensionen, die Sie entfernen möchten.

1. Klicken Sie auf **[!UICONTROL Remove]**.

1. Wenn Dimensionen in Berichten verwendet werden, wird eine Warnung mit der Liste der Diagramme angezeigt, die die Dimensionen verwenden. Klicken Sie auf **[!UICONTROL Delete]** , um die ausgewählten Dimensionen und alle abhängigen Elemente, einschließlich der Berichte, zu löschen.

## Verwalten von Dimensionen in Metriken

**So fügen Sie Dimensionen in einer Metrik hinzu:**

1. Gehe zu **[!UICONTROL Data > Metrics]**.

1. Klicken Sie auf **[!UICONTROL Edit]** für die Metrik, für die Sie eine neue Dimension erstellen möchten.

1. Wählen Sie im Abschnitt `Dimensions` im Dropdown-Menü `Add a dimension` eine hinzuzufügende Dimension aus.

>[!NOTE]
>
>Jede Dimension, nach der Sie filtern oder gruppieren möchten, muss bereits in [!DNL Commerce Intelligence] verfolgt werden. Wenn Sie die gewünschte Dimension nicht finden, müssen Sie möglicherweise mit dem Tracking einer neuen Datenspalte in Ihrer Datenbank über die Seite [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) beginnen.


**So löschen Sie Dimensionen aus einer Metrik:**

1. Gehe zu **[!UICONTROL Manage Data > Metrics]**.

1. Klicken Sie auf **[!UICONTROL Edit]** für die Metrik, für die Sie eine neue Dimension erstellen möchten.

1. Aktivieren Sie im Abschnitt `Dimensions` das Kontrollkästchen in der Spalte „Löschen“ neben den Dimensionen, die Sie entfernen möchten.

>[!NOTE]
>
>Selbst nach dem Löschen einer Dimension ist sie weiterhin als Spalte auf der Tabelle auf Ihrem Data Warehouse vorhanden. Sie können sie zu jeder Metrik zurück hinzufügen und neue Metriken mithilfe dieser Dimensionen erstellen. Um die Datenspalte, der eine Dimension entspricht, aus [!DNL Commerce Intelligence] zu entfernen, heben Sie einfach die Nachverfolgung der Datenspalte über die Seite [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) auf.

## Verwandte Dokumentation

* [Best Practices für Segmentierung und Filterung](../../best-practices/segment-filter.md)
