---
title: Adobe Analytics verbinden
description: Erfahren Sie, wie Sie den End-to-End-Journey-Fokus von [!DNL Adobe Analytics] und den eCommerce-Fokus, auf den Sie sich von [!DNL Commerce Intelligence] verlassen, miteinander verbinden können.
exl-id: 824e1ee4-6b88-42f7-b265-29330dbc4407
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# [!DNL Adobe Analytics] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/adobe-analytic-slogo.png)

Die [!DNL Adobe Analytics] -Integration für [!DNL Adobe Commerce Intelligence] ermöglicht es Ihnen, den End-to-End-Journey-Fokus von [!DNL Adobe Analytics] auf Kunden und den eCommerce-Fokus, auf den Sie von [!DNL Commerce Intelligence] angewiesen sind, zusammenzuführen. Damit erhalten Sie ein vollständiges Bild der Gesamtleistung Ihres Stores.

Genauer gesagt bietet die [!DNL Adobe Analytics] -Integration für [!DNL Commerce Intelligence] den Händlern die Möglichkeit, ihre [!DNL Adobe Commerce] - und [!DNL Adobe Analytics] -Datensätze zu kombinieren.

- Erstellen Sie eine Verbindung aus Ihrem vorhandenen [!DNL Adobe Analytics]-Konto in [!DNL Commerce Intelligence].

- Wählen Sie bis zu 25 Metriken und Dimensionen aus einer Report Suite aus, um sie auf Ihrer Data Warehouse zu replizieren.

- Verwenden Sie alle standardmäßigen [!DNL Commerce Intelligence] -Funktionen, um replizierte [!DNL Adobe Analytics] -Daten umzuwandeln, zu verknüpfen und zu berichten.

## Verbindungsvoraussetzungen

Die folgenden Informationen sind erforderlich, um eine Verbindung herzustellen:

- [!DNL Adobe Analytics] Anmeldedaten

- `Name` und/oder `ID` der [!DNL Adobe Analytics] Report Suite, aus der Daten repliziert werden sollen

- Liste der in [!DNL Commerce Intelligence] zu replizierenden Metriken und Dimensionen

## Verbinden der [!DNL Adobe Analytics]-Integration für [!DNL Commerce Intelligence]

1. Wechseln Sie zur Seite `Integrations` unter **[!DNL Manage Data** > **Integrations]**.

1. Klicken Sie auf **[!UICONTROL Add an Integration]**.

1. Klicken Sie auf das Symbol &quot;**[!UICONTROL Adobe Analytics]**&quot;, um auf die Seite zuzugreifen, über die Sie Ihre [!DNL Adobe Analytics]-Kontoverbindung autorisieren können.

1. Klicken Sie auf **[!UICONTROL Authorize with Adobe Analytics]**.

1. Geben Sie Ihre [!DNL Adobe Analytics] -Anmeldedaten ein. Nach erfolgreicher Autorisierung werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.

1. Eine Liste der verfügbaren Report Suites wird angezeigt. Wählen Sie die Report Suite aus, aus der Sie die Daten importieren möchten, und klicken Sie dann auf **[!UICONTROL Continue]**.

1. Der Bildschirm zur Auswahl der Metriken und Dimensionen wird angezeigt. Wählen Sie mindestens eine Metrik und mindestens eine Dimension bis zu einer Gesamtsumme von 25 Metriken und Dimensionen aus. Suchen Sie nach Namen oder scrollen Sie nach Ihren Komponenten, und klicken Sie dann auf die Kontrollkästchen, um sie auszuwählen. Klicken Sie auf **[!UICONTROL Continue]**.

1. Die ausgewählte Report Suite wird in einer Tabelle angezeigt. Klicken Sie auf **[!UICONTROL Save]** , um Ihre Auswahl zu bestätigen.

1. Informieren das [!DNL Commerce Intelligence] [Supportteam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) darüber, dass Ihre Integration autorisiert ist und den anfänglichen Verbindungsprozess für Sie durchführt.

Nachdem der anfängliche Verbindungsprozess ausgeführt wurde, ist Ihre Tabelle auf der Data Warehouse-Seite auf der Registerkarte `All Tables` verfügbar. Wählen Sie die Spalten aus, die Sie replizieren möchten. Die Daten werden nach der nächsten vollständigen Aktualisierung angezeigt.
