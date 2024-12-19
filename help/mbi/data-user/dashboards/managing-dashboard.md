---
title: Dashboards verwalten
description: Erfahren Sie, wie Sie Benutzerberechtigungen für Dashboards verwalten, deren Inhaber Sie sind, nicht mehr benötigte Dashboards löschen und ein Standard-Dashboard festlegen.
exl-id: 32c21093-2a7d-4d8e-afc0-19bd702f9b36
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Dashboard verwalten

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

In **[!DNL Manage Data** > **Dashboards]** können Sie Benutzerberechtigungen für Dashboards verwalten, deren Inhaber Sie sind, nicht mehr benötigte Dashboards löschen und ein Standard-Dashboard festlegen. Dieses Thema behandelt:

1. [Umbenennen von Dashboards](#rename)

1. [Dashboard-Berechtigungen verwalten](#userperm)

1. [Standard-Dashboard ändern](#default)

1. [Löschen von Dashboards](#delete)

## Dashboard umbenennen {#rename}

So benennen Sie ein Dashboard um:

1. Klicken Sie auf den Namen des Dashboards, das Sie ändern möchten.

2. Geben Sie den neuen Namen in das Feld `Dashboard Name` ein.

## Verwalten von Benutzerberechtigungen {#userperm}

In [!DNL Commerce Intelligence] für Dashboards gibt es drei Zugriffsebenen: `View`, `Edit` und `None`.

* `View` können ausgewählte Benutzer das Dashboard anzeigen, es jedoch nicht bearbeiten. Benutzer können auch mit der Funktion Speichern unter die Größe von Diagrammen ändern, Daten exportieren und die Diagramme in ihre eigenen Dashboards kopieren, wenn sie über Standard- oder Administratorberechtigungen verfügen.

* `Edit` können ausgewählte Benutzer Diagramme bearbeiten und in diesem Dashboard speichern, wenn sie über Standard- oder Administratorberechtigungen verfügen. Benutzende mit Bearbeitungsberechtigungen können Dashboards auch für andere Benutzende freigeben.

* `None` bedeutet, dass ausgewählte Benutzer dieses Dashboard nicht anzeigen oder bearbeiten können.

Benutzerberechtigungen können auf zwei Arten geändert werden: für alle Benutzer oder für einzelne Benutzer.

1. *Um die Berechtigungen aller Benutzer zu ändern, verwenden* das Dropdown-Menü neben der `Set all users' permissions to…`.

1. *Um die Berechtigungen eines einzelnen Benutzers zu ändern,* Sie das Dropdown-Menü neben dem Namen des Benutzers verwenden, um die gewünschte Zugriffsebene festzulegen.

## Standard-Dashboard ändern {#default}

So ändern Sie Ihr Standard-Dashboard für das Konto:

1. Klicken Sie auf den Namen des Dashboards, das Sie als Standard verwenden möchten.

1. Klicken Sie auf **[!UICONTROL Make Default]**.

## Dashboards löschen {#delete}

So löschen Sie ein Dashboard:

1. Klicken Sie auf den Namen des Dashboards, das Sie löschen möchten.

1. Klicken Sie auf **[!UICONTROL Delete Dashboard]**.
