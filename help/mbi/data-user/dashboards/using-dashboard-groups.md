---
title: Dashboard-Gruppen verwenden
description: Erfahren Sie, wie Sie Dashboards besser organisieren können.
exl-id: e48b7345-62d0-4898-997e-3c3c02040ad3
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Dashboard-Gruppen verwenden

Dashboard-Gruppen ermöglichen eine bessere Organisation von Dashboards. Der häufigste Anwendungsfall besteht darin, ähnliche Dashboards unter derselben „Gruppe“ zu gruppieren. Beispielsweise können alle Dashboards, die sich auf das Marketing beziehen, unter einer Dashboard-Gruppe „Marketing“ gruppiert werden.

Im Dropdown-Menü für die Dashboard-Auswahl werden Dashboard-Gruppen in alphabetischer Reihenfolge angezeigt, wobei alle Dashboards unter „Keine Gruppe“ zuletzt angezeigt werden. Dashboards in derselben Gruppe werden zusammen und in alphabetischer Reihenfolge innerhalb jeder Gruppe angezeigt.

## Dashboard-Gruppenfreigabe

Dashboard-Gruppen können nicht direkt zwischen Benutzern freigegeben werden. Wenn ein Dashboard für Benutzende freigegeben wird, wird die Dashboard-Gruppe, unter der es sich befindet, automatisch für diese Benutzenden erstellt, wenn sie nicht vorhanden ist. Wenn die Dashboard-Gruppe vorhanden ist, wird das Dashboard an die Liste angehängt.

Wenn die Gruppe eines Dashboards durch den Eigentümer geändert wird, wird die Änderung automatisch für alle Benutzer übernommen, für die das Dashboard freigegeben wurde. Benutzende können die Dashboard-Gruppe für Dashboards, deren Inhaber sie nicht sind, nicht ändern.

## Erstellen von Dashboard-Gruppen

Dashboard-Gruppen können auf zwei Arten erstellt werden:

1. Beim Erstellen eines Dashboards:

   ![Dashboard-Gruppe erstellen](../../assets/create-dashboard-groups-new-dashboard.png)

1. Beim Ändern der Gruppe eines vorhandenen Dashboards über die Seite `Manage Data > Dashboards` :

   1. Klicken Sie auf das Dashboard, für das Sie die Gruppe erstellen möchten.

   1. Unter `Dashboard Group (optional)` wird die aktuelle Dashboard-Gruppe angezeigt.

   1. Um eine Gruppe zu erstellen, geben Sie den Namen der neuen Gruppe ein und klicken Sie dann außerhalb des Felds.

      ![Dashboard-Gruppe erstellen](../../assets/create-dashboard-groups-existing-dashboard.png)

## Hinzufügen vorhandener Dashboards zu vorhandenen Gruppen

1. Wählen Sie auf der Seite `Manage Data > Dashboards` das Dashboard aus, für das Sie die Gruppe ändern möchten.

1. Der Text unter `Dashboard Group (optional)` zeigt die aktuelle Dashboard-Gruppe des Dashboards an.

1. Um die Gruppe des Dashboards zu ändern, wählen Sie eine andere Gruppe aus der Liste aus - in diesem Fall `PS`, `Campaigns`.

   ![Gruppen-Dashboard ändern](../../assets/add-existing-dashboard-existing-group.png)

## Dashboard-Gruppen löschen

Wenn eine Dashboard-Gruppe keine Dashboards enthält, wird sie automatisch gelöscht.
