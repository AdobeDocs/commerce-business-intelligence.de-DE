---
title: Adobe Analytics verbinden
description: Erfahren Sie, wie Sie den End-to-End-Journey-Fokus von  [!DNL Adobe Analytics]  und den E-Commerce-Fokus von zusammenführen [!DNL Commerce Intelligence].
exl-id: 824e1ee4-6b88-42f7-b265-29330dbc4407
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# [!DNL Adobe Analytics] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Adobe Analytics-Logo](../../../assets/adobe-analytic-slogo.png)

Die [!DNL Adobe Analytics] Integration für [!DNL Adobe Commerce Intelligence] ermöglicht es Ihnen, den End-to-End-Kunden-Journey-Fokus von [!DNL Adobe Analytics] und den E-Commerce-Fokus von [!DNL Commerce Intelligence] zusammenzuführen. Dadurch erhalten Sie einen vollständigen Überblick über die Gesamtleistung Ihres Stores.

Genauer gesagt bietet die [!DNL Adobe Analytics]-Integration für [!DNL Commerce Intelligence] Funktionen, mit denen Händler ihre [!DNL Adobe Commerce] und [!DNL Adobe Analytics] Datensätze kombinieren können.

- Erstellen Sie eine Verbindung von Ihrem bestehenden [!DNL Adobe Analytics]-Konto in [!DNL Commerce Intelligence].

- Wählen Sie bis zu 25 Metriken und Dimensionen aus einer Report Suite aus, die in Ihre Data Warehouse repliziert werden sollen.

- Verwenden Sie alle standardmäßigen [!DNL Commerce Intelligence], um replizierte [!DNL Adobe Analytics]-Daten zu transformieren, zusammenzuführen und Berichte dazu zu erstellen.

## Voraussetzungen für die Verbindung

Die folgenden Informationen werden für die Verbindung benötigt:

- [!DNL Adobe Analytics] Anmeldedaten

- `Name` und/oder `ID` [!DNL Adobe Analytics] Report Suite, aus der Daten repliziert werden sollen

- Liste der Metriken und Dimensionen, die nach [!DNL Commerce Intelligence] repliziert werden sollen

## Verbinden der [!DNL Adobe Analytics] für [!DNL Commerce Intelligence]

1. Navigieren Sie zur `Integrations` unter **[!DNL Manage Data** > **Integrations]**.

1. Klicken Sie auf **[!UICONTROL Add an Integration]**.

1. Klicken Sie auf das Symbol **[!UICONTROL Adobe Analytics]** , um auf die Seite zuzugreifen, auf der Sie die Verbindung Ihres [!DNL Adobe Analytics] Kontos autorisieren können.

1. Klicken Sie auf **[!UICONTROL Authorize with Adobe Analytics]**.

1. Geben Sie Ihre [!DNL Adobe Analytics] ein. Nach erfolgreicher Autorisierung werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.

1. Eine Liste der verfügbaren Report Suites wird angezeigt. Wählen Sie die Report Suite aus, aus der Sie die Daten importieren möchten, und klicken Sie dann auf **[!UICONTROL Continue]**.

1. Der Bildschirm zur Auswahl von Metriken und Dimensionen wird angezeigt. Wählen Sie mindestens eine Metrik und mindestens eine Dimension aus, bis zu einer kombinierten Summe von 25 Metriken und Dimensionen. Suchen Sie nach Namen oder scrollen Sie, um Ihre Komponenten zu finden, und klicken Sie dann auf die Kontrollkästchen, um sie auszuwählen. Klicken Sie auf **[!UICONTROL Continue]**.

1. Die ausgewählte Report Suite wird in einer Tabelle angezeigt. Klicken Sie auf **[!UICONTROL Save]** , um Ihre Auswahl zu bestätigen.

1. Informieren Sie das [!DNL Commerce Intelligence] [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de)Team, dass Ihre Integration autorisiert ist, und es führt den ersten Verbindungsprozess für Sie aus.

Nachdem der anfängliche Verbindungsprozess ausgeführt wurde, ist Ihre Tabelle auf der Data Warehouse-Seite auf der Registerkarte `All Tables` verfügbar. Wählen Sie die Spalten aus, die Sie replizieren möchten, und die Daten werden nach der nächsten vollständigen Aktualisierung angezeigt.
