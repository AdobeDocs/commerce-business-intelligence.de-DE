---
title: Dashboards verwalten
description: Erfahren Sie, wie Sie Benutzerberechtigungen für Dashboards verwalten, die Ihnen gehören, Dashboards löschen, die Sie nicht mehr benötigen, und ein Standard-Dashboard einrichten.
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

In **[!DNL Manage Data** > **Dashboards]** können Sie Benutzerberechtigungen für Dashboards verwalten, die Ihnen gehören, Dashboards löschen, die Sie nicht mehr benötigen, und ein Standard-Dashboard einrichten. Dieses Thema behandelt:

1. [Umbenennen von Dashboards](#rename)

1. [Verwalten von Dashboard-Berechtigungen](#userperm)

1. [Standard-Dashboard ändern](#default)

1. [Löschen von Dashboards](#delete)

## Umbenennen eines Dashboards {#rename}

So benennen Sie ein Dashboard um:

1. Klicken Sie auf den Namen des Dashboards, das Sie ändern möchten.

2. Geben Sie den neuen Namen in die `Dashboard Name` -Feld.

## Verwalten von Benutzerberechtigungen {#userperm}

Es gibt drei Zugriffsebenen in [!DNL Commerce Intelligence] für Dashboards - `View`, `Edit`, und `None`.

* `View` ermöglicht ausgewählten Benutzern, das Dashboard anzuzeigen, es jedoch nicht zu bearbeiten. Benutzer können auch die Größe von Diagrammen ändern, Daten exportieren und die Diagramme mithilfe der Funktion Speichern unter in ihre eigenen Dashboards kopieren, sofern sie über Standard- oder Administratorberechtigungen verfügen.

* `Edit` ermöglicht ausgewählten Benutzern das Bearbeiten und Speichern von Diagrammen in diesem Dashboard, wenn sie über Standard- oder Admin-Berechtigungen verfügen. Außerdem können Benutzer mit Bearbeitungsberechtigungen Dashboards auch für andere Benutzer freigeben.

* `None` bedeutet, dass ausgewählte Benutzer dieses Dashboard nicht anzeigen oder bearbeiten können.

Benutzerberechtigungen können auf zwei Arten geändert werden - für alle Benutzer oder für einzelne Benutzer.

1. *So ändern Sie die Berechtigungen aller Benutzer:* Verwenden Sie das Dropdown-Menü neben `Set all users' permissions to…` Beschriftung.

1. *So ändern Sie die Berechtigungen einzelner Benutzer:* Verwenden Sie das Dropdown-Menü neben dem Namen des Benutzers, um die gewünschte Zugriffsebene festzulegen.

## Standard-Dashboard ändern {#default}

So ändern Sie Ihr Standard-Dashboard für das Konto:

1. Klicken Sie auf den Namen des Dashboards, das Sie als Standard festlegen möchten.

1. Klicken **[!UICONTROL Make Default]**.

## Dashboards löschen {#delete}

So löschen Sie ein Dashboard:

1. Klicken Sie auf den Namen des Dashboards, das Sie löschen möchten.

1. Klicken **[!UICONTROL Delete Dashboard]**.
