---
title: Adobe Analytics verbinden
description: Erfahren Sie, wie Sie den Journey-Schwerpunkt von End-to-End-Kunden zusammenführen können. [!DNL Adobe Analytics] und dem eCommerce-Fokus, auf den Sie sich verlassen [!DNL Commerce Intelligence].
exl-id: 824e1ee4-6b88-42f7-b265-29330dbc4407
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Verbinden [!DNL Adobe Analytics]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/adobe-analytic-slogo.png)

Die [!DNL Adobe Analytics] Integration für [!DNL Adobe Commerce Intelligence] ermöglicht es Ihnen, den End-to-End-Journey-Fokus von [!DNL Adobe Analytics] und dem eCommerce-Fokus, auf den Sie sich verlassen [!DNL Commerce Intelligence]. Damit erhalten Sie ein vollständiges Bild der Gesamtleistung Ihres Stores.

Genauer gesagt, wird die [!DNL Adobe Analytics] Integration für [!DNL Commerce Intelligence] bietet Händlern die Möglichkeit, ihre [!DNL Adobe Commerce] und [!DNL Adobe Analytics] Datensätzen.

- Erstellen Sie eine Verbindung aus Ihrer bestehenden [!DNL Adobe Analytics] Konto [!DNL Commerce Intelligence].

- Wählen Sie bis zu 25 Metriken und Dimensionen aus einer Report Suite aus, die in Ihrer Data Warehouse repliziert werden sollen.

- Verwenden Sie alle standardmäßigen [!DNL Commerce Intelligence] Funktionen zum Transformieren, Verknüpfen und Berichten zu replizierten [!DNL Adobe Analytics] Daten.

## Verbindungsvoraussetzungen

Die folgenden Informationen sind erforderlich, um eine Verbindung herzustellen:

- [!DNL Adobe Analytics] Anmeldedaten

- `Name` und/oder `ID` von [!DNL Adobe Analytics] Report Suite, aus der Daten repliziert werden sollen

- Liste der zu replizierenden Metriken und Dimensionen [!DNL Commerce Intelligence]

## Verbinden des [!DNL Adobe Analytics] Integration für [!DNL Commerce Intelligence]

1. Navigieren Sie zu `Integrations` Seite unter **[!DNL Manage Data** > **Integrations]**.

1. Klicken **[!UICONTROL Add an Integration]**.

1. Klicken Sie auf **[!UICONTROL Adobe Analytics]** -Symbol, um auf die Seite zuzugreifen, über die Sie Ihre [!DNL Adobe Analytics] Kontoverbindung.

1. Klicken **[!UICONTROL Authorize with Adobe Analytics]**.

1. Geben Sie Ihre [!DNL Adobe Analytics] Anmeldedaten. Nach erfolgreicher Autorisierung werden Sie zu [!DNL Commerce Intelligence].

1. Eine Liste der verfügbaren Report Suites wird angezeigt. Wählen Sie die Report Suite aus, aus der Sie die Daten importieren möchten, und klicken Sie auf **[!UICONTROL Continue]**.

1. Der Bildschirm zur Auswahl der Metriken und Dimensionen wird angezeigt. Wählen Sie mindestens eine Metrik und mindestens eine Dimension bis zu einer Gesamtsumme von 25 Metriken und Dimensionen aus. Suchen Sie nach Namen oder scrollen Sie nach Ihren Komponenten, und klicken Sie dann auf die Kontrollkästchen, um sie auszuwählen. Klicken **[!UICONTROL Continue]**.

1. Die ausgewählte Report Suite wird in einer Tabelle angezeigt. Klicken **[!UICONTROL Save]** um Ihre Auswahl zu bestätigen.

1. Informieren Sie die [!DNL Commerce Intelligence] [Supportteam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) dass Ihre Integration autorisiert ist und der erste Verbindungsprozess für Sie ausgeführt wird.

Nach Ausführung des anfänglichen Verbindungsprozesses ist Ihre Tabelle auf der Seite &quot;Data Warehouse&quot;unter der `All Tables` Registerkarte. Wählen Sie die Spalten aus, die Sie replizieren möchten. Die Daten werden nach der nächsten vollständigen Aktualisierung angezeigt.
