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

[!DNL Adobe Commerce Intelligence] Dashboards geben Ihnen einen Überblick über die Leistung und Verkaufsaktivitäten Ihres Stores auf einen Blick. Einzelne Dashboards können für andere Benutzer freigegeben und in logische Gruppen unterteilt werden. Sie können auch verschiedene Berechtigungsstufen für andere Benutzer festlegen.

Es ist einfach, einen Bericht zu erstellen, ihn einem Dashboard hinzuzufügen und die Daten nach Excel zu exportieren. Grafiken und Berichte können in der Größe angepasst und in die Position des Dashboards gezogen werden.

![Dashboard](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-holiday-sales-dashboard.png)

## Erstellen von Dashboards {#createdash}

Dashboards sind freigebbare thematische Behälter für die Analysen, die Sie in den Report Buildern erstellen. Auf diese Weise können Sie Ihr Team ermutigen, zusammenzuarbeiten und eine einzige Quelle der Wahrheit in Ihrem Unternehmen zu erhalten.

*Wenn Sie Administrator oder Standardbenutzer sind*, können Sie ein Dashboard erstellen, indem Sie auf das Dropdown-Menü `Dashboard Options` klicken und `Create New dashboard` auswählen.

Wie die von Ihnen erstellten Dashboards aussehen, liegt ganz bei Ihnen. Sie können die Elemente im Dashboard beliebig anordnen und ihre Größe ändern.

![Größe des Dashboard-Elements anordnen](../../assets/arrange_resize_dashboard_element.gif)

### Dashboard erstellen

1. Klicken Sie im Menü auf **[!UICONTROL Dashboards]**.

1. Der Name des Standard-Dashboards wird in der oberen linken Ecke der Dashboard-Kopfzeile angezeigt. Klicken Sie auf den Abwärtspfeil (![](../../assets/magento-bi-btn-down.png)), um die verfügbaren Optionen anzuzeigen.

   ![Dashboard erstellen](../../assets/magento-bi-dashboard-create.png)

1. Klicken Sie auf **[!UICONTROL Create Dashboard]**. Führen Sie dann die folgenden Schritte aus:

   * Geben Sie einen `Name` für Ihr Dashboard ein.

   * Um eine `Group` für das Dashboard zu erstellen, geben Sie den Namen der Gruppe ein.

     Wenn Ihre Commerce-Installation beispielsweise über mehrere Store-Ansichten verfügt, können Sie für jede Store-Ansicht eine Gruppe erstellen.

   * Klicken Sie auf **[!UICONTROL Create]**.

   ![Dashboard-Name](../../assets/magento-bi-dashboard-create-name.png)

   * Der Name Ihres neuen Dashboards wird oben links angezeigt. Klicken Sie auf den Abwärtspfeil (![](../../assets/magento-bi-btn-down.png)), um die Optionen anzuzeigen. Wenn Sie eine Gruppe erstellt haben, wird das neue Dashboard unter der Gruppe in der Liste angezeigt.

### Bericht hinzufügen

1. Führen Sie einen der folgenden Schritte aus, um einen Bericht hinzuzufügen:

   * Klicken Sie auf die Eingabeaufforderung **[!UICONTROL Add a report]** auf der Seite.

   * Klicken Sie in der Dashboard-Kopfzeile auf **[!UICONTROL Add Report]**.

     ![Bericht hinzufügen](../../assets/magento-bi-dashboard-create-add-report.png)

1. Klicken Sie auf **[!UICONTROL Create Report]** , um den **[!UICONTROL Report Builder Options]** anzuzeigen.

   ![Report Builder Options](../../assets/magento-bi-report-builder.png)

## Elemente in einem Dashboard anordnen

* Um die Größe eines Diagramms oder Berichts zu ändern, ziehen Sie die untere rechte Ecke auf die neue Größe.

* Um ein Diagramm oder einen Bericht zu verschieben, bewegen Sie den Mauszeiger über den Titel oder die Kopfzeile, bis der Cursor in ein Kreuz geändert wird. Ziehen Sie es dann an die gewünschte Position.

## Verwalten von Dashboards {#managedash}

In **[!DNL Manage Data** > **Dashboards]** können Sie Benutzerberechtigungen für Dashboards verwalten, die Ihnen gehören, Dashboards löschen, die Sie nicht mehr benötigen, und ein Standard-Dashboard einrichten.

### Dashboards freigeben {#sharingdash}

Um in Ihrer Organisation wirklich [!DNL Commerce Intelligence] zu skalieren und wertvolle Einblicke zu erhalten, empfiehlt Ihnen Adobe, Dashboards, die Sie erstellen, mit anderen Team-Mitgliedern zu teilen. *Sie können Dashboards freigeben, deren Inhaber Sie sind*, indem Sie oben auf der Seite auf die Option `Share Dashboard` klicken.

Wenn Sie ein Dashboard freigeben, können Sie Ihrer gesamten Organisation ODER individuell Berechtigungen zuweisen, sodass Sie entscheiden können, wer Ihre Berichte anzeigen und bearbeiten kann.

>[!NOTE]
>
>`Read-Only` Benutzer haben nur Zugriff auf Dashboards, die direkt für sie freigegeben sind. Sie können nicht allein nach Dashboards suchen und diese hinzufügen. Vergessen Sie nicht, sie in der Schleife zu halten!

### Zugreifen auf freigegebene Dashboards {#accessshared}

*Wenn Sie Administrator oder Standardbenutzer sind* und Ihrem Konto ein freigegebenes Dashboard hinzufügen möchten, können Sie dies tun, indem Sie auf **[!UICONTROL Dashboard Options]** klicken und dann im Dropdown-Menü auf **[!UICONTROL Find]** klicken.

![Dashboard suchen](../../assets/find_dashboard.png)<!--{: width="1000" height="535"}-->

### Dashboard-Einstellungen verwalten

1. Klicken Sie im Menü auf **[!DNL Manage Data** > **Dashboards]**.

1. Falls zutreffend, geben Sie einen neuen `Dashboard Name` ein.

1. Um das Dashboard einer bestimmten `Dashboard Group` zuzuweisen, wählen Sie aus der Gruppenliste aus.

   **`Permissions`**

   Gehen Sie wie folgt vor, um allen Benutzern denselben Zugriff auf das Dashboard zu gewähren:

   1. Wählen Sie unter **`Shared with`** eine der folgenden Optionen aus:

      * `View`
      * `Edit`
      * `None`

   1. Wenn Sie zur Bestätigung aufgefordert werden, klicken Sie auf **[!UICONTROL OK]** , um die Berechtigungsebene für jeden Benutzer zu aktualisieren.

   1. Um die Berechtigungsstufe einer Person zu ändern, suchen Sie den Benutzer in der Liste, um die Berechtigungsebene zu ändern. Die Änderung wird automatisch gespeichert.

   **`Default`**

   1. Um dieses Dashboard als Standard für Ihr [!DNL Commerce Intelligence] -Konto festzulegen, klicken Sie auf **[!UICONTROL Make Default]**.

   **`Remove`**

   1. Um das Dashboard zu entfernen, klicken Sie auf **[!UICONTROL Delete Dashboard]**.
