---
title: Filter
description: Erfahren Sie, wie Sie Filter verwenden.
exl-id: eb683dfe-9a90-400a-a0c0-3dc00d1f28b5
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Filter

Es können ein oder mehrere Filter hinzugefügt werden, um die Daten zu beschränken, die zum Produkt eines Berichts verwendet werden. Jeder Filter ist ein Ausdruck, der eine Spalte der zugehörigen Tabelle, einen Operator und einen Wert enthält. Um beispielsweise nur wiederkehrende Kunden einzubeziehen, können Sie einen Filter erstellen, der nur Kunden umfasst, die mehr als eine Bestellung aufgegeben haben. Mehrere Filter können mit logischen `AND/OR` Operatoren verwenden, um dem Bericht Logik hinzuzufügen.

>[!TIP]
>
>Ein Bericht kann maximal 3.500 Datenpunkte enthalten. Um die Anzahl der Datenpunkte zu reduzieren, verwenden Sie einen Filter, um die Datenmenge zu reduzieren, die zum Generieren des Berichts verwendet wird.

MBI enthält eine Auswahl von Filtern, die Sie &quot;vorkonfiguriert&quot;(OOTB) verwenden oder an Ihre Anforderungen anpassen können. Die Anzahl der Filter, die Sie erstellen können, ist unbegrenzt.

## So fügen Sie einen Filter hinzu:

1. Bewegen Sie den Mauszeiger im Diagramm über jeden Datenpunkt.

   In diesem Bericht zeigt jeder Datenpunkt die Gesamtanzahl der Kunden für den Monat an.

1. Klicken Sie im linken Bereich auf Filter (![](../../assets/magento-bi-btn-filter.png)).

   ![Filter hinzufügen](../../assets/magento-bi-report-builder-filter-add.png)

1. Klicken **[!UICONTROL Add Filter]**.

   Filter werden alphabetisch nummeriert und der erste ist `[A]`. Die ersten beiden Teile des Filters sind Dropdown-Optionen und der dritte Teil ist ein Wert.

   ![](../../assets/magento-bi-report-builder-filter-add-a.png)

   * Klicken Sie auf den ersten Teil des Filters und wählen Sie die Spalte aus, die Sie als Betreff des Ausdrucks verwenden möchten.

      ![Auswählen des ersten Teils des Filters](../../assets/magento-bi-report-builder-filter-part1.png)

   * Klicken Sie auf den zweiten Teil des Filters und wählen Sie den Operator aus.

      ![Operator auswählen](../../assets/magento-bi-report-builder-filter-part2.png)

   * Geben Sie im dritten Teil des Filters den Wert ein, der zum Vervollständigen des Ausdrucks erforderlich ist.

      ![Wert eingeben](../../assets/magento-bi-report-builder-filter-part3.png)

   * Wenn der Filter abgeschlossen ist, klicken Sie auf **[!UICONTROL Apply]**.

      Der Bericht enthält jetzt nur noch wiederkehrende Kunden, und die Anzahl der für den Bericht abgerufenen Kundendatensätze wurde von 33.000 auf 12.6.000 verringert.

      ![Gefilterter Bericht](../../assets/magento-bi-report-builder-filter-report.png)<!--{: .zoom}-->

1. Klicken Sie in der Seitenleiste auf die Perspektive ( ![](../../assets/magento-bi-btn-perspective.png)).

   ![Perspektive](../../assets/magento-bi-report-builder-filter-perspective.png)<!--{: .zoom}-->

1. Wählen Sie in der Liste der Einstellungen `Cumulative`. Klicken Sie anschließend auf **[!UICONTROL Apply]**.

   ![Kumulierte Perspektive](../../assets/magento-bi-report-builder-filter-perspective-cumulative.png)

   Die `Cumulative` Die Perspektive verteilt die Änderung im Zeitverlauf, anstatt die &quot;Aufgejagt&quot;und &quot;Abgezackt&quot;für jeden Monat anzuzeigen.

1. Geben Sie einen `Title` und klicken Sie auf **[!UICONTROL Save]** es als `Chart` in Ihr Dashboard.

   ![In Dashboard speichern](../../assets/magento-bi-report-builder-filter-perspective-cumulative-save.png)
