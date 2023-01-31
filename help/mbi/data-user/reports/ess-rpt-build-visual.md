---
title: Visual Report Builder
description: Erfahren Sie, wie Sie Visual Report Builder verwenden.
exl-id: 1101f43d-e014-4df2-be21-12d90a9d8a56
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---

# `Visual Report Builder`

`Visual Report Builder` erleichtert die Erstellung von Schnellberichten auf der Grundlage vordefinierter Metriken. Jede Metrik enthält eine Abfrage, die den Datensatz für den Bericht definiert.

Das folgende Beispiel zeigt, wie Sie einen einfachen Bericht erstellen, die Daten nach einer zusätzlichen Dimension gruppieren, das Datums- und Uhrzeitintervall festlegen, den Diagrammtyp ändern und den Bericht in einem Dashboard speichern.

## So erstellen Sie einen einfachen Bericht:

1. Im [!DNL MBI] Menü, klicken Sie **[!UICONTROL Report Builder]**.

1. under `Visual Report Builder`klicken **[!UICONTROL Create Report]** und gehen Sie wie folgt vor:

   * Klicken **[!UICONTROL Add Metric]**.

      Die verfügbaren Metriken können alphabetisch oder nach Tabelle aufgelistet werden.

      ![Visual Report Builder](../../assets/magento-bi-visual-report-builder-add-metric.png)

   * Wählen Sie die [Metrik](../../data-user/reports/ess-manage-data-metrics.md) beschreibt den Datensatz, den Sie für den Bericht verwenden möchten.

      Die `New Customers` -Metrik, die in diesem Beispiel verwendet wird, zählt alle Kunden und sortiert die Liste nach dem Datum, an dem sich der Kunde für ein Konto angemeldet hat. Der erste Bericht enthält ein einfaches Liniendiagramm, gefolgt von der Datentabelle.

      Die Zusammenfassung auf der linken Seite zeigt den Namen der aktuellen Metrik, gefolgt vom Ergebnis aller Berechnungen zu Spaltendaten, die in der Metrik angegeben sind. In diesem Beispiel zeigt die Zusammenfassung die Gesamtanzahl der Kunden an.

      ![Visual Report Builder](../../assets/magento-bi-report-builder-untitled.png)

1. Bewegen Sie im Diagramm den Mauszeiger über jeden Datenpunkt auf der Zeile. Jeder Datenpunkt zeigt die Gesamtzahl neuer Kunden an, die sich während dieses Monats angemeldet haben.

1. Befolgen Sie diese Anweisungen, um die Daten zu gruppieren, den Datumsbereich und den Diagrammtyp zu ändern.

   **`Group By`**

   Die `Group By` -Kontrolle bietet Ihnen die Möglichkeit, mehrere Dimensionen nach Gruppe oder Segment hinzuzufügen. Dimensionen sind Tabellenspalten, die zur Gruppierung der Daten verwendet werden können.

   * Wählen Sie eine der verfügbaren Dimensionen aus der Liste der `Group By` Optionen.

      In diesem Beispiel hat das System fünf Coupon-Codes gefunden, die von Kunden bei der ersten Bestellung verwendet wurden.

      ![Gruppieren nach](../../assets/magento-bi-report-builder-group-by-dimensions.png)

      Die `Group By` detail listet jeden von Kunden verwendeten Gutschein auf. Die Gutscheine, die zum Platzieren der ursprünglichen Bestellung verwendet wurden, sind mit einem Kontrollkästchen markiert. Das Diagramm enthält jetzt mehrere farbige Linien, die den jeweiligen Gutschein darstellen, der für eine erste Bestellung verwendet wurde. Die Legende ist farbcodiert und entspricht jeder Datenzeile.

   * Klicken **[!UICONTROL Apply]** um die Gruppe nach Detail zu schließen.

      ![Mehrere Dimensionen](../../assets/magento-bi-report-builder-group-by-dimension-detail.png)

   * Bewegen Sie den Mauszeiger über einige Datenpunkte in jeder Zeile, um die Anzahl der Kunden während des Monats anzuzeigen, die diesen Coupon bei der ersten Bestellung verwendet haben.

   * Die Datentabelle verfügt jetzt über eine Hinzufüge -Dimension mit einer Spalte für jeden Monat und einer Zeile für jeden Couponcode.

      ![Nach Tabellendaten gruppieren](../../assets/magento-bi-report-builder-group-by-table-data.png)

   * Klicken Sie auf Transponieren (![](../../assets/magento-bi-btn-transpose.png)) in der rechten oberen Ecke der Tabelle, um die Ausrichtung der Daten zu ändern.

      Die Datenachse wird gespiegelt, und die Tabelle enthält jetzt eine Spalte für jeden Couponcode und eine Zeile für jeden Monat. Vielleicht ist diese Ausrichtung leichter zu lesen.

      ![Übertragene Daten](../../assets/magento-bi-report-builder-group-by-table-data-transposed.png)
   **`Date Range`**

   Die `Date Range` Die Kontrolle zeigt den aktuellen Datumsbereich und die Zeitintervalleinstellungen an und befindet sich direkt über dem Diagramm auf der rechten Seite.

   * Klicken Sie auf `Date Range` -Steuerelement, das in diesem Beispiel auf `All-Time by Month`.

      ![Datumsbereich](../../assets/magento-bi-report-builder-date-range.png)

   * Nehmen Sie die folgenden Änderungen vor:

      * Um für eine genauere Ansicht einzoomen, ändern Sie den Datumsbereich in `Last Full Quarter`.
      * under `Select Time Interval`auswählen `Week`.
      * Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save]**.

      Der Bericht enthält jetzt nur die Daten des letzten Quartals nach Woche.

      ![Bericht für das letzte Quartal nach Woche](../../assets/magento-bi-report-builder-date-range-quarter-by-week-chart.png)
   **Diagrammtyp**

   * Klicken Sie auf die Steuerelemente in der oberen rechten Ecke, um das beste Diagramm für die Daten zu finden.

      Einige Diagrammtypen sind nicht mit multidimensionalen Daten kompatibel.

      |  |  |
      |-----|-----|
      | ![](../../assets/magento-bi-btn-chart-line.png) | Kantengraph |
      | ![](../../assets/magento-bi-btn-chart-horz-bar.png) | Horizontalbalken |
      | ![](../../assets/magento-bi-btn-chart-horz-stacked-bar.png) | Horizontaler gestapelter Balken |
      | ![](../../assets/magento-bi-btn-chart-vert-bar.png) | Vertikalbalken |
      | ![](../../assets/magento-bi-btn-chart-vert-stacked-bar.png) | Vertikaler gestapelter Balken |
      | ![](../../assets/magento-bi-btn-chart-pie.png) | Torte |
      | ![](../../assets/magento-bi-btn-chart-area.png) | Bereich |
      | ![](../../assets/magento-bi-btn-chart-funnel.png) | Trichter |

      {style=&quot;table-layout:auto&quot;}




1. So geben Sie dem Bericht einen `title`, ersetzen Sie die `Untitled Report` Text oben auf der Seite mit einem beschreibenden Titel.

1. Klicken Sie oben rechts auf **[!UICONTROL Save]** und gehen Sie wie folgt vor:

   * Für `Type`, die Standardeinstellung akzeptieren, `Chart`.

   * Wählen Sie die `Dashboard` wo der Bericht verfügbar sein soll.

   * Klicken **[!UICONTROL Save to Dashboard]**.

      ![In Dashboard speichern](../../assets/magento-bi-report-builder-save-to-dashboard.png)

1. Führen Sie einen der folgenden Schritte aus, um die Grafik in einem Dashboard anzuzeigen:

   * Klicken **[!UICONTROL Go to Dashboard]** in der Nachricht oben auf der Seite.

   * Wählen Sie im Menü `Dashboards` und klicken Sie auf den Namen des aktuellen Dashboards, um die Liste anzuzeigen. Klicken Sie dann auf den Namen des Dashboards, in dem der Bericht gespeichert wurde.

      ![Bericht im Dashboard](../../assets/magento-bi-report-builder-my-dashboard.png)
