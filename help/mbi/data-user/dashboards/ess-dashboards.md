---
title: Dashboards
description: Erfahren Sie, wie Sie ein Dashboard erstellen und verwenden.
exl-id: a872344b-ac66-41eb-a471-5a69f8802527
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 0%

---

# Dashboards

[!DNL Adobe Commerce Intelligence] Dashboards bieten einen Überblick über die Leistung und Verkaufsaktivitäten Ihres Stores. Einzelne Dashboards können für andere Benutzer freigegeben und in logische Gruppen unterteilt werden. Sie können auch verschiedene Berechtigungsstufen für andere Benutzer festlegen.

Es ist einfach, einen Bericht zu erstellen, ihn einem Dashboard hinzuzufügen und die Daten nach Excel zu exportieren. Grafiken und Berichte können in der Größe angepasst und in die Position des Dashboards gezogen werden.

![Dashboard](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-holiday-sales-dashboard.png)

## Erstellen von Dashboards {#createdash}

Dashboards sind freigebbare thematische Behälter für die Analysen, die Sie in den Report Buildern erstellen. Auf diese Weise können Sie Ihr Team ermutigen, zusammenzuarbeiten und eine einzige Quelle der Wahrheit in Ihrem Unternehmen zu erhalten.

*Wenn Sie Administrator oder Standardbenutzer sind*, können Sie ein Dashboard erstellen, indem Sie auf `Dashboard Options` Dropdown und Auswählen `Create New dashboard`.

Wie die von Ihnen erstellten Dashboards aussehen, liegt ganz bei Ihnen. Sie können die Elemente im Dashboard beliebig anordnen und ihre Größe ändern.

![Größe des Dashboard-Elements ändern](../../assets/arrange_resize_dashboard_element.gif)

### Dashboard erstellen

1. Klicken Sie im Menü auf **[!UICONTROL Dashboards]**.

1. Der Name des Standard-Dashboards wird in der oberen linken Ecke der Dashboard-Kopfzeile angezeigt. Klicken Sie auf den Abwärtspfeil (![](../../assets/magento-bi-btn-down.png)), um die verfügbaren Optionen anzuzeigen.

   ![Dashboard erstellen](../../assets/magento-bi-dashboard-create.png)

1. Klicken **[!UICONTROL Create Dashboard]**. Führen Sie dann die folgenden Schritte aus:

   * Geben Sie einen `Name` für Ihr Dashboard.

   * So erstellen Sie eine `Group` Geben Sie für das Dashboard den Namen der Gruppe ein.

     Wenn Ihre Commerce-Installation beispielsweise über mehrere Store-Ansichten verfügt, können Sie für jede Store-Ansicht eine Gruppe erstellen.

   * Klicken **[!UICONTROL Create]**.

   ![Dashboard-Name](../../assets/magento-bi-dashboard-create-name.png)

   * Der Name Ihres neuen Dashboards wird oben links angezeigt. Klicken Sie auf den Abwärtspfeil (![](../../assets/magento-bi-btn-down.png)), um die Optionen anzuzeigen. Wenn Sie eine Gruppe erstellt haben, wird das neue Dashboard unter der Gruppe in der Liste angezeigt.

### Bericht hinzufügen

1. Führen Sie einen der folgenden Schritte aus, um einen Bericht hinzuzufügen:

   * Klicken Sie auf **[!UICONTROL Add a report]** auf der Seite.

   * Klicken Sie in der Dashboard-Kopfzeile auf **[!UICONTROL Add Report]**.

     ![Bericht hinzufügen](../../assets/magento-bi-dashboard-create-add-report.png)

1. Klicks **[!UICONTROL Create Report]** , um **[!UICONTROL Report Builder Options]**.

   ![Report Builder Options](../../assets/magento-bi-report-builder.png)

## Elemente in einem Dashboard anordnen

* Um die Größe eines Diagramms oder Berichts zu ändern, ziehen Sie die untere rechte Ecke auf die neue Größe.

* Um ein Diagramm oder einen Bericht zu verschieben, bewegen Sie den Mauszeiger über den Titel oder die Kopfzeile, bis der Cursor in ein Kreuz geändert wird. Ziehen Sie es dann an die gewünschte Position.

## Verwalten von Dashboards {#managedash}

In **[!DNL Manage Data** > **Dashboards]** können Sie Benutzerberechtigungen für Dashboards verwalten, die Ihnen gehören, Dashboards löschen, die Sie nicht mehr benötigen, und ein Standard-Dashboard einrichten.

### Dashboards freigeben {#sharingdash}

Skalierbarkeit [!DNL Commerce Intelligence] Adobe ermutigt Sie, Dashboards, die Sie erstellen, für andere Teammitglieder freizugeben und wertvolle Einblicke zu bieten. *Sie können eigene Dashboards freigeben* durch Klicken auf `Share Dashboard` -Option oben auf der Seite.

Wenn Sie ein Dashboard freigeben, können Sie Ihrer gesamten Organisation ODER individuell Berechtigungen zuweisen, sodass Sie entscheiden können, wer Ihre Berichte anzeigen und bearbeiten kann.

>[!NOTE]
>
>`Read-Only` -Benutzer haben nur Zugriff auf Dashboards, die direkt für sie freigegeben sind. Sie können nicht allein nach Dashboards suchen und diese hinzufügen. Vergessen Sie nicht, sie in der Schleife zu halten!

### Zugreifen auf freigegebene Dashboards {#accessshared}

*Wenn Sie Administrator- oder Standardbenutzer sind* Sie möchten Ihrem Konto ein freigegebenes Dashboard hinzufügen, indem Sie auf **[!UICONTROL Dashboard Options]** und klicken Sie anschließend auf **[!UICONTROL Find]** in der Dropdown-Liste.

![Dashboard finden](../../assets/find_dashboard.png)<!--{: width="1000" height="535"}-->

### Dashboard-Einstellungen verwalten

1. Klicken Sie im Menü auf **[!DNL Manage Data** > **Dashboards]**.

1. Falls zutreffend, geben Sie eine neue `Dashboard Name`.

1. So weisen Sie das Dashboard einer bestimmten `Dashboard Group`, wählen Sie aus der Liste der Gruppen aus.

   **`Permissions`**

   Gehen Sie wie folgt vor, um allen Benutzern denselben Zugriff auf das Dashboard zu gewähren:

   1. under **`Shared with`** wählen Sie eine der folgenden Optionen aus:

      * `View`
      * `Edit`
      * `None`

   1. Klicken Sie bei Aufforderung zur Bestätigung auf **[!UICONTROL OK]** , um die Berechtigungsebene für jeden Benutzer zu aktualisieren.

   1. Um die Berechtigungsstufe einer Person zu ändern, suchen Sie den Benutzer in der Liste, um die Berechtigungsebene zu ändern. Die Änderung wird automatisch gespeichert.

   **`Default`**

   1. Damit dieses Dashboard zum Standard für Ihre [!DNL Commerce Intelligence] Konto, klicken Sie **[!UICONTROL Make Default]**.

   **`Remove`**

   1. Um das Dashboard zu entfernen, klicken Sie auf **[!UICONTROL Delete Dashboard]**.
