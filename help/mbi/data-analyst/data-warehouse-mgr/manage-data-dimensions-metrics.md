---
title: Datendimensionen verwalten
description: Erfahren Sie, wie Daten generiert werden und was genau dazu führt, dass eine neue Zeile in einen der Core Commerce-Anwendungen eingefügt wird, wie Aktionen wie Kauf getätigt werden oder ein Konto erstellt wird, das in die Commerce-Datenbank aufgenommen wird.
exl-id: 143a4b1e-2e6f-438a-90e6-bdda13b39cb9
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Datendimensionen verwalten

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Eine Dimension ist ein Feld in derselben Tabelle wie eine Metrik, mit der Diagramme basierend auf dieser Metrik gefiltert oder segmentiert werden können. Beispielsweise kann eine Umsatzmetrik Stadt, Bundesland, Land, Bestellstatus, Couponcode und andere Dimensionstypen enthalten.

## Dimensionen zu mehreren Metriken hinzufügen

So fügen Sie eine oder mehrere Dimensionen gleichzeitig zu mehreren Metriken hinzu:

1. Navigieren Sie in der Hauptnavigationsleiste zu **[!UICONTROL Manage Data > Metrics]**.

1. Klicken Sie oben auf der Seite auf **[!UICONTROL Add Dimensions To Metric(s)]**.

1. Wählen Sie die Tabelle aus, die die Dimensionen enthält.

1. Im `Choose Metric(s) to Add Dimensions` die Metriken, denen Sie Dimensionen hinzufügen möchten. Nach der Auswahl wird die `Choose Dimensions to Add` wird rechts angezeigt. Überprüfen Sie die Dimensionen, die Sie zur ausgewählten Metrik hinzufügen möchten.

   ![](../../assets/Add_Dimensions.png)

1. Wenn Sie eine Segmentierung oder Gruppierung nach einer der Datendimensionen in Berichten vornehmen möchten, geben Sie an, dass _Gruppierbar_.

1. Klicken **[!UICONTROL Add]**.

## Dimensionen aus mehreren Metriken löschen

So löschen Sie eine oder mehrere Dimensionen aus mehreren Metriken:

1. Navigieren Sie in der Hauptnavigationsleiste zu **[!UICONTROL Data > Metrics]**.

1. Klicken Sie oben auf der Seite auf **[!UICONTROL Remove Dimensions From Metric(s)]**.

1. Wählen Sie die Tabelle aus, die die Dimensionen enthält.

1. Wählen Sie links die Metriken aus, aus denen die Dimensionen entfernt werden sollen, und rechts die Dimensionen, die Sie entfernen möchten.

1. Klicken **[!UICONTROL Remove]**.

1. Wenn die Dimensionen in Berichten verwendet werden, werden eine Warnung und eine Liste mit Diagrammen angezeigt, die die Dimensionen verwenden. Klicken **[!UICONTROL Delete]** , um die aktivierten Dimensionen und alle abhängigen Elemente, einschließlich Berichten, zu löschen.

## Dimensionen in Metriken verwalten

**So fügen Sie einer Metrik Dimension(en) hinzu:**

1. Navigieren Sie in der Hauptnavigationsleiste zu **[!UICONTROL Data > Metrics]**.

1. Klicken **[!UICONTROL Edit]** für die Metrik, die Sie eine neue Dimension wünschen.

1. Unter dem `Dimensions` -Abschnitt verwenden Sie die `Add a dimension` zur Auswahl einer hinzuzufügenden Dimension.

>[!NOTE]
>
>Jede Dimension, nach der Sie filtern oder gruppieren möchten, muss bereits nachverfolgt werden [!DNL MBI]. Wenn Sie die gewünschte Dimension nicht finden, müssen wir möglicherweise mit dem Tracking einer neuen Datenspalte in Ihrer Datenbank über die [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) Seite.


**So löschen Sie Dimensionen aus einer Metrik:**

1. Navigieren Sie in der Hauptnavigationsleiste zu **[!UICONTROL Manage Data > Metrics]**.

1. Klicken **[!UICONTROL Edit]** für die Metrik, die Sie eine neue Dimension wünschen.

1. Unter dem `Dimensions` aktivieren, aktivieren Sie das Kontrollkästchen in der Spalte Löschen neben den Dimensionen, die Sie entfernen möchten.

>[!NOTE]
>
>Selbst nach dem Löschen einer Dimension ist sie weiterhin als Spalte auf Ihrer Tabelle in unserem Data Warehouse vorhanden. Sie können sie wieder zu einer beliebigen Metrik hinzufügen und mithilfe dieser Dimensionen neue Metriken erstellen. Um die Datenspalte zu entfernen, entspricht eine Dimension [!DNL MBI]die Datenspalte einfach über die [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) Seite.

## Verwandte Dokumentation

* [Best Practices für Segmentierung und Filterung](../../best-practices/segment-filter.md)
