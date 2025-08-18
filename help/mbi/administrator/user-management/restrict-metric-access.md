---
title: Zugriff auf Metriken einschränken
description: Erfahren Sie, wie Sie mit Metriken und Zugriffsbeschränkungen arbeiten.
exl-id: 88f5ca7a-8073-4968-9685-95f141b2a87f
role: Admin, User
feature: User Management
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Verwalten von Metriken für Benutzer

Zusätzlich zur Festlegung von Benutzerberechtigungsebenen können Sie den Zugriff auf Metriken auch benutzerspezifisch einschränken. Wenn Sie beispielsweise möchten, dass Ihre Buchhaltungsabteilung Zugriff auf umsatzbezogene Metriken, aber nicht auf Metriken zur Benutzerakquise hat, können Sie den Zugriff auf diese Metriken einschränken.

In Fällen wie diesen empfiehlt Adobe, das Konto dieses Benutzers auf **[[!UICONTROL Standard]](../../administrator/user-management/user-management.md)** festzulegen. **[!UICONTROL Standard]** Berechtigungen sollten Benutzenden erteilt werden, die keine Metriken, berechneten Spalten, Integrationen oder Benutzenden erstellen oder ändern müssen, aber Zugriff auf Daten in der Data Warehouse benötigen. Wenn Sie den Zugriff auf Daten vollständig einschränken möchten, verwenden Sie stattdessen die **[!UICONTROL Read Only]** .

Nachdem Sie die Berechtigungsstufe festgelegt haben, können Sie die Metriken auswählen, auf die ein **[!UICONTROL Standard]** Benutzer zugreifen kann, indem Sie folgende Schritte ausführen:

1. Navigieren Sie zu **[!UICONTROL Account Settings]** > **[!UICONTROL Manage Users]**.
1. Das gewünschte Benutzerkonto auswählen.
1. Auf der Registerkarte **[!UICONTROL Metrics]** wird eine Liste der verfügbaren Metriken angezeigt. Markieren Sie die Metriken, auf die der Benutzer Zugriff haben soll, und heben Sie die Auswahl der Metriken auf, auf die der Benutzer keinen Zugriff haben soll.
1. [!DNL Adobe Commerce Intelligence] speichert die Änderungen automatisch. Wenn die Änderung erfolgreich war, zeigt [!DNL Commerce Intelligence] oben auf der Seite **[!UICONTROL Saved!]** an.

>[!NOTE]
>
>Alle Benutzer mit **[!UICONTROL Standard]** Berechtigungen können zusätzlich zu allen Metriken aus [!DNL Google Analytics] über den Datenexport auf alle Daten in der Data Warehouse zugreifen.

Sie können den Zugriff auf eine Metrik auch einschränken, indem Sie die Metrik bearbeiten und **[!UICONTROL Standard]** im Abschnitt **[[!UICONTROL User Rights]](../../data-user/reports/ess-manage-data-metrics.md)** Benutzer auswählen.

>[!NOTE]
>
>Wenn Sie eine Metrik duplizieren, kopiert [!DNL Commerce Intelligence] die in der ursprünglichen Metrik festgelegten Benutzerberechtigungen.
