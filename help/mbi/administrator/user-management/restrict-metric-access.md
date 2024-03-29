---
title: Zugriff auf Metriken beschränken
description: Erfahren Sie, wie Sie mit dem Zugriff auf Metriken und Einschränkungen arbeiten.
exl-id: 88f5ca7a-8073-4968-9685-95f141b2a87f
role: Admin, User
feature: User Management
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Benutzer von Metriken verwalten

Sie können nicht nur Benutzerberechtigungsstufen festlegen, sondern auch den Zugriff auf Metriken für einzelne Benutzer einschränken. Wenn Sie beispielsweise möchten, dass Ihre Buchhaltungsabteilung Zugriff auf umsatzbezogene Metriken hat, aber keine Benutzerakquise-Metriken, können Sie den Zugriff auf diese Metriken beschränken.

In solchen Fällen empfiehlt Adobe, das Benutzerkonto auf **[[!UICONTROL Standard]](../../administrator/user-management/user-management.md)**. **[!UICONTROL Standard]** -Berechtigungen sollten Benutzern erteilt werden, die keine Metriken, berechneten Spalten, Integrationen oder Benutzer erstellen oder ändern müssen, aber Zugriff auf Daten im Data Warehouse benötigen. Wenn Sie den Zugriff auf Daten vollständig beschränken möchten, verwenden Sie die **[!UICONTROL Read Only]** -Berechtigungen.

Nachdem Sie die Berechtigungsebene festgelegt haben, können Sie die Metriken a **[!UICONTROL Standard]** Der Benutzer kann wie folgt darauf zugreifen:

1. Navigieren Sie zu **[!UICONTROL Account Settings]** > **[!UICONTROL Manage Users]**.
1. Wählen Sie das gewünschte Benutzerkonto aus.
1. Die **[!UICONTROL Metrics]** zeigt eine Liste der verfügbaren Metriken an. Überprüfen Sie die Metriken, auf die der Benutzer Zugriff haben soll, und heben Sie die Auswahl für die Metriken auf, auf die der Benutzer keinen Zugriff haben soll.
1. [!DNL Adobe Commerce Intelligence] speichert die Änderungen automatisch. Wenn die Änderung erfolgreich ist, [!DNL Commerce Intelligence] Displays **[!UICONTROL Saved!]** oben auf der Seite.

>[!NOTE]
>
>Alle Benutzer mit **[!UICONTROL Standard]** -Berechtigungen können über den Datenexport auf alle Daten in der Data Warehouse zugreifen, zusätzlich zu allen Metriken aus [!DNL Google Analytics].

Sie können den Zugriff auf eine Metrik auch beschränken, indem Sie die Metrik bearbeiten und **[!UICONTROL Standard]** Benutzer in der **[[!UICONTROL User Rights]](../../data-user/reports/ess-manage-data-metrics.md)** Abschnitt.

>[!NOTE]
>
>Wenn Sie eine Metrik duplizieren, [!DNL Commerce Intelligence] kopiert die in der ursprünglichen Metrik festgelegten Benutzerberechtigungen.
