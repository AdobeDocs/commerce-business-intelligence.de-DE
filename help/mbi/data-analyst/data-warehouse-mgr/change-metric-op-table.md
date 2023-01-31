---
title: Arbeitstabelle einer Metrik ändern
description: Erfahren Sie, wie Sie die Datentabelle ändern, mit der eine Metrik ihren Vorgang ausführt.
exl-id: c7a074ca-31f4-43e5-85d9-b64dca95dc23
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Arbeitstabelle einer Metrik ändern

In bestimmten Fällen können Sie die Datentabelle ändern, mit der eine Metrik ihren Vorgang ausführt. Wenn Sie beispielsweise über eine neue Benutzertabelle verfügen, sollten Sie Ihre benutzerbezogenen Metriken aus der Tabelle &quot;Benutzer\_alt&quot;migrieren, um stattdessen die Tabelle &quot;Benutzer\_Neu&quot;zu verwenden.

1. Navigieren Sie zu **[!UICONTROL Data]** > **[!UICONTROL Metrics]**
1. Klicken **[!UICONTROL Edit]** neben der Metrik, für die Sie die `operational` Tabelle.
1. Klicken Sie im Editor auf **[!UICONTROL Change]**.

   ![](../../assets/change-metrics-1.png)
1. Wählen Sie nun die neue Tabelle aus, auf der diese Metrik basieren soll.
1. Als Nächstes müssen Sie die vorhandenen Datendimensionen mit den entsprechenden Dimensionen in der neuen Tabelle abgleichen. Wenn Sie beispielsweise eine Spalte mit dem Namen `User's registration date`wählen Sie einfach aus, welche Spalte in der neuen Tabelle die gleichen Datumsdaten enthält. (Siehe nächsten Schritt, wenn die neue Tabelle keine übereinstimmenden Spalten enthält)

   ![](../../assets/change-metrics-2.png)

1. Wenn die neue Tabelle keine übereinstimmende Spalte enthält, können Sie entweder **Erstellen in der Datentabelle** oder [Support kontaktieren](../../guide-overview.md) wenn es sich um eine Berechnungsspalte oder -dimension handelt, die von [!DNL MBI]) oder einfach **Dimension aus der Metrik löschen**. Um eine Dimension zu löschen, die Sie nicht mehr benötigen, gehen Sie einfach zum Editor der Metrik zurück und wählen Sie unter die zu löschenden Dimensionen aus `Dimensions`.

   ![](../../assets/change-metrics-3.png)
