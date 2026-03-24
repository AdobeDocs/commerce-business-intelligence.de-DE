---
title: Zugriff auf Metriken einschränken
description: Erfahren Sie, wie Sie mit Metriken und Zugriffsbeschränkungen arbeiten.
exl-id: 88f5ca7a-8073-4968-9685-95f141b2a87f
role: Admin, User
feature: User Management
TQID: https://experienceleague.adobe.com/e87ix3NAqY6xZQbNbQkXuCnvvH2B-8H3APYpKtshs9w
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 238
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
