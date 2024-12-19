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

Eine Formel kombiniert mehrere Metriken und mathematische Logik zur Beantwortung einer Frage. Wie hoch war beispielsweise der Umsatz pro Produkt während der Urlaubszeit, der durch neue Kunden generiert wurde?

![Verkäufe an Feiertagen im Dashboard](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-holiday-sales-dashboard.png)

## Schritt 1: Erstellen des Basisberichts

1. Wählen Sie im Menü `Report Builder` aus.

1. Klicken Sie auf **[!UICONTROL Add Metric]** und wählen Sie die erste Metrik für den Bericht aus.

   In diesem Beispiel wird die Metrik `Revenue by products ordered` verwendet.

1. Klicken Sie erneut auf **[!UICONTROL Add Metric]** und wählen Sie die zweite Metrik für den Bericht aus.

   In diesem Beispiel wird die Metrik `New Customers` verwendet.

1. Klicken Sie in der Seitenleiste auf **[!UICONTROL Details]** , um Informationen zu den einzelnen Metriken anzuzeigen.

   ![Umsatz nach bestellten Produkten](../../assets/magento-bi-report-builder-revenue-by-products.png)

1. Klicken Sie in der Seitenleiste auf den Namen der einzelnen Metriken, um die Einstellungsseite in einer neuen Browser-Registerkarte zu öffnen. Scrollen Sie nach unten, um die einzelnen Komponenten der Metrik anzuzeigen, einschließlich der Metrikabfrage, des Filters und der Dimensionen.

   ![Metrikeinstellungen](../../assets/magento-bi-report-builder-revenue-by-products-metric-detail.png)

1. Um zu Ihrem Bericht zurückzukehren, klicken Sie auf die vorherige Browser-Registerkarte.

1. Bewegen Sie im Diagramm den Mauszeiger über einige Datenpunkte auf jeder Zeile, um die mit den einzelnen Metriken verbundenen Beträge anzuzeigen.

## Schritt 2: Formel hinzufügen

1. Klicken Sie oben in der Seitenleiste auf **[!UICONTROL Add Formula]**.

   Im Feld Formel werden die Metriken als verfügbare `A` und `B` angezeigt. Es enthält ein Eingabefeld, in das Sie die Formel eingeben können.

   Gehen Sie folgendermaßen vor:

   * Geben Sie in das `Enter your Formula` Eingabefeld `A/B` ein.

     Dies teilt den Umsatz nach bestellten Produkten durch die Anzahl der neuen Kunden.

   * Legen Sie `Select format` auf `123Number` fest.

   * Ersetzen Sie in der Randleiste `Untitled` durch einen Namen für die Formel .

   ![Formeleinstellungen](../../assets/magento-bi-report-builder-revenue-by-products-add-formula-detail.png)

1. Klicken Sie abschließend auf **[!UICONTROL Apply]**.

   Der Bericht hat jetzt eine neue Zeile für die Formel, `New Customer Revenue`, und die Seitenleiste zeigt die Gesamtmenge des Umsatzes an, der von neuen Kunden generiert wurde.

   ![Bericht mit Formel](../../assets/magento-bi-report-builder-revenue-by-products-formula-report.png)

## Schritt 3: Hinzufügen eines Datumsbereichs

1. Klicken Sie oben rechts auf **[!UICONTROL Date Range]** .

1. Gehen Sie auf der Registerkarte `Fixed Date Range` wie folgt vor:

   * Wählen Sie in den Kalendern den Datumsbereich.

     Bei diesem Beispiel ist die Urlaubszeit von `November 1` bis `December 31`.

   * Wählen Sie unter `Select Time Interval` die Option `Day` aus.

     ![Fester Datumsbereich](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-fixed-date-range.png)

   * Klicken Sie abschließend auf **[!UICONTROL Apply]**.

   Der Bericht ist jetzt auf die Urlaubszeit beschränkt, mit einem Datenpunkt für jeden Tag.

   ![Fester Datumsbereich](../../assets/magento-bi-report-builder-revenue-by-products-formula-report-fixed-date-range-report.png)

## Schritt 4: Bericht speichern

In diesem Schritt speichern Sie den Bericht als Diagramm und auch als Tabelle.

1. Klicken Sie oben auf der Seite auf `Untitled Report` und geben Sie einen beschreibenden Titel ein. Für dieses Beispiel ist der Berichtstitel `2017 Holiday Sales`.

   Gehen Sie dann wie folgt vor:

   * Klicken Sie oben rechts auf **[!UICONTROL Save]**.

   * Akzeptieren Sie `Type` die Standardeinstellung `Chart` .

   * Wählen Sie die `Dashboard` aus, in der der Bericht verfügbar sein soll.

   * Klicken Sie auf **[!UICONTROL Save to Dashboard]**.

1. Klicken Sie auf den Berichtstitel und ändern Sie den Namen. Für dieses Beispiel wird der Berichtstitel in `2017 Holiday Sales Data` geändert.

   Gehen Sie dann wie folgt vor:

   * Klicken Sie oben rechts auf **[!UICONTROL Save a Copy]**.

   * Legen Sie `Type` auf `Table` fest.

   * Wählen Sie die `Dashboard` aus, in der der Bericht verfügbar sein soll.

   * Klicken Sie auf **[!UICONTROL Save a Copy to Dashboard]**.

1. Führen Sie einen der folgenden Schritte aus, um die Berichte in Ihrem Dashboard anzuzeigen:

   * Klicken Sie oben auf der Seite in der Nachricht auf **[!UICONTROL Go to Dashboard]** .

   * Wählen Sie im Menü **[!UICONTROL Dashboards]** aus. Klicken Sie auf den Namen des aktuellen Dashboards, um die Liste anzuzeigen. Klicken Sie anschließend auf den Namen des Dashboards, in dem der Bericht gespeichert wurde.
