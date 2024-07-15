---
title: Visual Report Builder
description: Erfahren Sie, wie Sie Visual Report Builder verwenden.
exl-id: 1101f43d-e014-4df2-be21-12d90a9d8a56
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# [!DNL Visual Report Builder]

Mit [!DNL Visual Report Builder] können Sie schnell Berichte auf der Basis vordefinierter Metriken erstellen. Jede Metrik enthält eine Abfrage, die den Datensatz für den Bericht definiert.

Das folgende Beispiel zeigt, wie Sie einen einfachen Bericht erstellen, die Daten nach einer zusätzlichen Dimension gruppieren, das Datums- und Uhrzeitintervall festlegen, den Diagrammtyp ändern und den Bericht in einem Dashboard speichern.

## So erstellen Sie einen einfachen Bericht:

1. Klicken Sie im Menü [!DNL Commerce Intelligence] auf **[!UICONTROL Report Builder]**.

1. Klicken Sie unter [!UICONTROL Visual Report Builder] auf **[!UICONTROL Create Report]** und führen Sie folgende Schritte aus:

   * Klicken Sie auf **[!UICONTROL Add Metric]**.

     Die verfügbaren Metriken können alphabetisch oder nach Tabelle aufgelistet werden.

     ![Visual Report Builder](../../assets/magento-bi-visual-report-builder-add-metric.png)

   * Wählen Sie die [Metrik](../../data-user/reports/ess-manage-data-metrics.md) aus, die den Datensatz beschreibt, den Sie für den Bericht verwenden möchten.

     Die in diesem Beispiel verwendete Metrik `New Customers` zählt alle Kunden und sortiert die Liste nach dem Datum, an dem sich der Kunde für ein Konto angemeldet hat. Der erste Bericht enthält ein einfaches Liniendiagramm, gefolgt von der Datentabelle.

     Die Zusammenfassung auf der linken Seite zeigt den Namen der aktuellen Metrik, gefolgt vom Ergebnis aller Berechnungen zu Spaltendaten, die in der Metrik angegeben sind. In diesem Beispiel zeigt die Zusammenfassung die Gesamtanzahl der Kunden an.

     ![Visual Report Builder](../../assets/magento-bi-report-builder-untitled.png)

1. Bewegen Sie im Diagramm den Mauszeiger über jeden Datenpunkt auf der Zeile. Jeder Datenpunkt zeigt die Gesamtzahl neuer Kunden an, die sich während dieses Monats angemeldet haben.

1. Befolgen Sie diese Anweisungen, um die Daten zu gruppieren, den Datumsbereich und den Diagrammtyp zu ändern.

   **`Group By`**

   Mit dem Steuerelement `Group By` können Sie mehrere Dimensionen nach Gruppe oder Segment hinzufügen. Dimensionen sind Tabellenspalten, die zur Gruppierung der Daten verwendet werden können.

   * Wählen Sie eine der verfügbaren Dimensionen aus der Liste der `Group By` -Optionen.

     In diesem Beispiel hat das System fünf Coupon-Codes gefunden, die von Kunden bei der ersten Bestellung verwendet wurden.

     ![Gruppieren nach ](../../assets/magento-bi-report-builder-group-by-dimensions.png)

     Im Detail `Group By` werden die einzelnen von Kunden verwendeten Gutscheine aufgelistet. Die Gutscheine, die zum Platzieren der ursprünglichen Bestellung verwendet wurden, sind mit einem Kontrollkästchen markiert. Das Diagramm enthält jetzt mehrere farbige Linien, die jeden Gutschein darstellen, der für eine erste Bestellung verwendet wurde. Die Legende ist farbcodiert und entspricht jeder Datenzeile.

   * Klicken Sie auf **[!UICONTROL Apply]** , um die Gruppe nach Detail zu schließen.

     ![Mehrere Dimensionen](../../assets/magento-bi-report-builder-group-by-dimension-detail.png)

   * Bewegen Sie den Mauszeiger über einige Datenpunkte in jeder Zeile, um die Anzahl der Kunden während des Monats anzuzeigen, die diesen Coupon bei der ersten Bestellung verwendet haben.

   * Die Datentabelle verfügt jetzt über eine Hinzufüge -Dimension mit einer Spalte für jeden Monat und einer Zeile für jeden Couponcode.

     ![Nach Tabellendaten gruppieren](../../assets/magento-bi-report-builder-group-by-table-data.png)

   * Klicken Sie oben rechts in der Tabelle auf das Steuerelement Transponieren (![](../../assets/magento-bi-btn-transpose.png)), um die Ausrichtung der Daten zu ändern.

     Die Datenachse wird gespiegelt, und die Tabelle enthält jetzt eine Spalte für jeden Couponcode und eine Zeile für jeden Monat. Vielleicht ist diese Ausrichtung leichter zu lesen.

     ![Transpodierte Daten](../../assets/magento-bi-report-builder-group-by-table-data-transposed.png)

   **`Date Range`**

   Das Steuerelement `Date Range` zeigt den aktuellen Datumsbereich und die Zeitintervalleinstellungen an und befindet sich direkt über dem Diagramm rechts.

   * Klicken Sie auf das Steuerelement `Date Range` , das in diesem Beispiel auf `All-Time by Month` festgelegt ist.

     ![Datumsbereich](../../assets/magento-bi-report-builder-date-range.png)

   * Nehmen Sie die folgenden Änderungen vor:

      * Um für eine genauere Ansicht einzoomen, ändern Sie den Datumsbereich in &quot;`Last Full Quarter`&quot;.
      * Wählen Sie unter &quot;`Select Time Interval`&quot;die Option &quot;`Week`&quot;.
      * Klicken Sie nach Abschluss des Vorgangs auf **[!UICONTROL Save]**.

     Der Bericht enthält jetzt nur die Daten des letzten Quartals nach Woche.

     ![Bericht für das letzte Quartal nach Woche](../../assets/magento-bi-report-builder-date-range-quarter-by-week-chart.png)

   **Diagrammtyp**

   * Klicken Sie auf die Steuerelemente in der oberen rechten Ecke, um das beste Diagramm für die Daten zu finden.

     Einige Diagrammtypen sind nicht mit multidimensionalen Daten kompatibel.

     | | |
     |-----|-----|
     | ![](../../assets/magento-bi-btn-chart-line.png) | Kantengraph |
     | ![](../../assets/magento-bi-btn-chart-horz-bar.png) | Horizontalbalken |
     | ![](../../assets/magento-bi-btn-chart-horz-stacked-bar.png) | Horizontalbalken |
     | ![](../../assets/magento-bi-btn-chart-vert-bar.png) | Vertikalbalken |
     | ![](../../assets/magento-bi-btn-chart-vert-stacked-bar.png) | Vertikaler gestapelter Balken |
     | ![](../../assets/magento-bi-btn-chart-pie.png) | Torte |
     | ![](../../assets/magento-bi-btn-chart-area.png) | Bereich |
     | ![](../../assets/magento-bi-btn-chart-funnel.png) | Trichter |

     {style="table-layout:auto"}

1. Um dem Bericht den Wert &quot;`title`&quot;zu geben, ersetzen Sie den Text &quot;`Untitled Report`&quot;oben auf der Seite durch einen beschreibenden Titel.

1. Klicken Sie oben rechts auf **[!UICONTROL Save]** und führen Sie folgende Schritte aus:

   * Nehmen Sie für `Type` die Standardeinstellung `Chart` an.

   * Wählen Sie die `Dashboard` aus, für die der Bericht verfügbar sein soll.

   * Klicken Sie auf **[!UICONTROL Save to Dashboard]**.

     ![In Dashboard speichern](../../assets/magento-bi-report-builder-save-to-dashboard.png)

1. Führen Sie einen der folgenden Schritte aus, um die Grafik in einem Dashboard anzuzeigen:

   * Klicken Sie oben auf der Seite in der Nachricht auf **[!UICONTROL Go to Dashboard]** .

   * Wählen Sie im Menü `Dashboards` aus und klicken Sie auf den Namen des aktuellen Dashboards, um die Liste anzuzeigen. Klicken Sie dann auf den Namen des Dashboards, in dem der Bericht gespeichert wurde.

     ![Bericht im Dashboard](../../assets/magento-bi-report-builder-my-dashboard.png)
