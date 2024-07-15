---
title: Formeln
description: Erfahren Sie, wie Sie Formeln verwenden.
exl-id: b6432d93-739f-410c-b732-e09a278f8dae
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Formeln

Eine Formel kombiniert mehrere Metriken und mathematische Logik, um eine Frage zu beantworten. Wie viel vom Umsatz pro Produkt während der Weihnachtszeit wurde beispielsweise von neuen Kunden generiert?

![Feiertagsumsätze im Dashboard](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-holiday-sales-dashboard.png)

## Schritt 1: Erstellen des Basisberichts

1. Wählen Sie im Menü `Report Builder` aus.

1. Klicken Sie auf **[!UICONTROL Add Metric]** und wählen Sie die erste Metrik für den Bericht aus.

   In diesem Beispiel wird die Metrik `Revenue by products ordered` verwendet.

1. Klicken Sie erneut auf **[!UICONTROL Add Metric]** und wählen Sie die zweite Metrik für den Bericht aus.

   In diesem Beispiel wird die Metrik `New Customers` verwendet.

1. Klicken Sie in der Seitenleiste auf **[!UICONTROL Details]** , um Informationen zu den einzelnen Metriken anzuzeigen.

   ![Umsatz durch bestellte Produkte](../../assets/magento-bi-report-builder-revenue-by-products.png)

1. Klicken Sie in der Seitenleiste auf den Namen jeder Metrik, um die Einstellungsseite in einer neuen Browser-Registerkarte zu öffnen. Scrollen Sie nach unten, um die einzelnen Komponenten der Metrik anzuzeigen, einschließlich der Metrikabfrage, des Filters und der Dimensionen.

   ![Metrikeinstellungen](../../assets/magento-bi-report-builder-revenue-by-products-metric-detail.png)

1. Um zu Ihrem Bericht zurückzukehren, klicken Sie auf die Registerkarte &quot;Vorheriger Browser&quot;.

1. Bewegen Sie im Diagramm den Mauszeiger über einige Datenpunkte in jeder Zeile, um die mit den einzelnen Metriken verbundenen Beträge anzuzeigen.

## Schritt 2: Hinzufügen einer Formel

1. Klicken Sie oben in der Seitenleiste auf **[!UICONTROL Add Formula]**.

   Das Formelfeld zeigt die Metriken als verfügbare Eingabe `A` und `B` an und enthält ein Eingabefeld, in das Sie die Formel eingeben können.

   Gehen Sie wie folgt vor:

   * Geben Sie in das Eingabefeld `Enter your Formula` den Wert `A/B` ein.

     Dadurch wird der Umsatz durch die bestellten Produkte durch die Anzahl neuer Kunden dividiert.

   * Setzen Sie `Select format` auf `123Number`.

   * Ersetzen Sie in der Seitenleiste `Untitled` durch einen Namen für die Formel.

   ![Formeleinstellungen](../../assets/magento-bi-report-builder-revenue-by-products-add-formula-detail.png)

1. Klicken Sie nach Abschluss des Vorgangs auf **[!UICONTROL Apply]**.

   Der Bericht enthält jetzt eine neue Zeile für die Formel &quot;`New Customer Revenue`&quot;, und die Seitenleiste zeigt den Gesamtumsatz an, der von neuen Kunden generiert wurde.

   ![Bericht mit Formel](../../assets/magento-bi-report-builder-revenue-by-products-formula-report.png)

## Schritt 3: Datumsbereich hinzufügen

1. Klicken Sie oben rechts auf **[!UICONTROL Date Range]** .

1. Gehen Sie auf der Registerkarte `Fixed Date Range` wie folgt vor:

   * Wählen Sie in den Kalendern den Datumsbereich aus.

     In diesem Beispiel ist die Weihnachtszeit von `November 1` bis `December 31`.

   * Wählen Sie unter &quot;`Select Time Interval`&quot;die Option &quot;`Day`&quot;.

     ![Fester Datumsbereich](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-fixed-date-range.png)

   * Klicken Sie nach Abschluss des Vorgangs auf **[!UICONTROL Apply]**.

   Der Bericht ist nun auf die Weihnachtszeit beschränkt und enthält für jeden Tag einen Datenpunkt.

   ![Fester Datumsbereich](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-fixed-date-range-report.png)

## Schritt 4: Bericht speichern

In diesem Schritt speichern Sie den Bericht als Grafik und auch als Tabelle.

1. Klicken Sie oben auf der Seite auf `Untitled Report` und geben Sie einen beschreibenden Titel ein. In diesem Beispiel ist der Berichtstitel `2017 Holiday Sales`.

   Führen Sie dann die folgenden Schritte aus:

   * Klicken Sie oben rechts auf **[!UICONTROL Save]**.

   * Nehmen Sie für `Type` die standardmäßige Einstellung `Chart` an.

   * Wählen Sie die `Dashboard` aus, für die der Bericht verfügbar sein soll.

   * Klicken Sie auf **[!UICONTROL Save to Dashboard]**.

1. Klicken Sie auf den Berichtstitel und ändern Sie den Namen. In diesem Beispiel wird der Berichtstitel in `2017 Holiday Sales Data` geändert.

   Führen Sie dann die folgenden Schritte aus:

   * Klicken Sie in der oberen rechten Ecke auf **[!UICONTROL Save a Copy]**.

   * Setzen Sie `Type` auf `Table`.

   * Wählen Sie die `Dashboard` aus, für die der Bericht verfügbar sein soll.

   * Klicken Sie auf **[!UICONTROL Save a Copy to Dashboard]**.

1. Führen Sie einen der folgenden Schritte aus, um die Berichte in Ihrem Dashboard anzuzeigen:

   * Klicken Sie oben auf der Seite in der Nachricht auf **[!UICONTROL Go to Dashboard]** .

   * Wählen Sie im Menü **[!UICONTROL Dashboards]** aus. Klicken Sie auf den Namen des aktuellen Dashboards, um die Liste anzuzeigen. Klicken Sie dann auf den Namen des Dashboards, in dem der Bericht gespeichert wurde.
