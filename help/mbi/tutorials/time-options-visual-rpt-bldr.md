---
title: Verwenden von Zeitoptionen in Visual Report Builder
description: Erfahren Sie, wie Sie die Daten in Ihrem Bericht für einen bestimmten Zeitraum analysieren können.
exl-id: a1bb4838-f882-44b1-a29f-84b985032ceb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 0%

---

# Verwenden von [!DNL Time] in [!DNL Visual Report Builder]

Zu den Funktionen der [!DNL Visual Report Builder] gehören die globalen `Time Range`- und `Interval`. Mit diesen Einstellungen können Sie die Daten in Ihrem Bericht über einen bestimmten Zeitraum analysieren.

Bei einigen Analysen müssen Sie jedoch möglicherweise unterschiedliche Zeitbereiche oder Zeitintervalle in demselben Bericht berücksichtigen. An dieser Stelle kommen `Time` Optionen ins Spiel. Um Ihnen eine bessere Vorstellung davon zu geben, wie Sie `Time` Optionen in Ihren Berichten verwenden, werden in diesem Tutorial die folgenden Anwendungsfälle behandelt:

* [Analysieren von Metriken ohne Zeitstempel](#notimestamp)
* [Einer Metrik ein unabhängiges Zeitintervall zuweisen](#independenttimeinterval)
* [Vergleichen derselben Metrik über verschiedene Zeitbereiche hinweg](#difftimerange)

Wenn Sie einigen der in diesem Thema besprochenen Beispielberichte folgen möchten, öffnen Sie die [[!DNL Visual Report Builder]](../data-user/reports/ess-rpt-build-visual.md), bevor Sie fortfahren.

## Analysieren von Metriken ohne Zeitstempel {#notimestamp}

Einige Metriken können im Laufe der Zeit einfach keinen Trend aufweisen, da die Daten nicht erfasst oder mit einem zugehörigen Zeitstempel gespeichert werden. Beispielsweise enthält eine Inventartabelle oft nur eine Zeile für jede SKU. In diesem Fall sollten Sie [Metrik erstellen](../data-user/reports/ess-manage-data-metrics.md) ohne einen Zeitstempel anzugeben.

Wenn Sie eine solche Metrik in Ihrem Reporting verwenden, beachten Sie, dass beim Hinzufügen dieser Metrik zu einem Bericht automatisch eine unabhängige `Time Interval` der `None` und `Time Range` der `Global` festgelegt wird:

![](../assets/Metrics_without_timestamps.gif)

## Einer Metrik ein unabhängiges Zeitintervall zuweisen {#independenttimeinterval}

Mit `Time` Optionen können Sie zeitbasierte 100-%-Diagramme erstellen, um zu ermitteln, welcher Tag, welche Woche, welcher Monat oder welches Jahr in einem bestimmten Zeitraum am meisten zur Wertschöpfung beigetragen hat. In diesem Abschnitt erstellen Sie ein Diagramm, das den Prozentsatz des Umsatzes anzeigt, der in jedem Kalendermonat eines Jahres generiert wurde.

Dieser Berichtstyp kann nützlich sein, wenn Sie den im Jahresvergleich generierten Umsatz vergleichen möchten. Sie haben zum Beispiel eine Grafik für 2015, die zeigt, dass Januar 18 Prozent des Umsatzes für das Jahr beitrug und eine Grafik für 2016 zeigte nur 8 Prozent. Man hätte recherchieren können, was passiert sein könnte.

1. Fügen Sie Ihre `Revenue` Metrik zum Bericht hinzu.
1. Klicken Sie auf **[!UICONTROL Duplicate]** , um eine Kopie der Metrik zu erstellen.
1. Klicken Sie auf die Option Globale **[!UICONTROL Time Range]** und dann auf **[!UICONTROL Moving Time Range]**. Legen Sie dies auf `Last Year` fest.
1. Klicken Sie auf die Option Globale **[!UICONTROL Time Interval]** und legen Sie sie auf `Monthly` fest.
1. Report Builder fügt automatisch eine zweite Y-Achse für eine zweite Metrik hinzu. Deaktivieren Sie das `Multiple Y-Axes`.
1. Als Nächstes wenden Sie eine unabhängige `Time Interval` auf die erste Metrik an. Klicken Sie auf **[!UICONTROL Time Options]** (Uhrensymbol) rechts neben der `first Revenue metric`.
1. Klicken Sie in dem erweiterten Fenster, das über dem Bericht angezeigt wird, auf **[!UICONTROL Time Options]** .
1. Legen Sie in der Dropdown-Liste Folgendes fest:

   * `Time Interval`: Setzen Sie dies auf `None`.

   * `Time Range`: Legen Sie dies auf `Last Year` fest, indem Sie zuerst auf **[!UICONTROL Custom]** klicken, dann **[!UICONTROL Moving Range]** und schließlich die Option `Last Year` auswählen.

   * Klicken Sie auf **[!UICONTROL Apply]** , um die Intervall- und Bereichseinstellungen zu speichern. Dadurch wird eine Metrik erstellt, die den Gesamtumsatz des Vorjahres berechnet. Als Nächstes verwenden Sie diese Metrik als Nenner in einer Formel.

   * Um den Prozentsatz des Umsatzes für jeden Monat anzuzeigen, müssen Sie dem Bericht eine Formel hinzufügen. Klicken Sie auf **[!UICONTROL Add Formula]**.

   * Geben Sie `B/A` in das Feld Formel ein und wählen Sie `% Percent` aus der Dropdown-Liste neben dem Textfeld aus. Diese Formel teilt die Einnahmen aus einem bestimmten Monat des letzten Jahres durch die Gesamteinnahmen des letzten Jahres.

   * Klicken Sie auf **[!UICONTROL Apply Changes]**.

   * Blenden Sie Ihre beiden Eingabemetriken aus und benennen Sie die Formel um.

Jetzt können Sie sehen, wie wirksam jeder Monat im letzten Jahr war:

![](../assets/Independent_Time_Int.png)

## Vergleichen derselben Metrik über verschiedene Zeitbereiche hinweg {#difftimerange}

In diesem Beispiel wird eine benutzerdefinierte Dimension namens `Day number of the month` verwendet. Wenn Sie diesen Bericht erstellen möchten, diese Dimension aber noch nicht auf Ihrem Data Warehouse vorhanden ist, [ Sie sich an den ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

Die beiden häufigsten Beispiele in dieser Kategorie sind (1) der Vergleich von Wachstumsmetriken (Umsatz im Jahresvergleich oder Monat im Monatsvergleich) und (2) ein besseres Verständnis der jüngsten Trends bei Lagerbeständen oder Artikelverkäufen.

Um diesen Anwendungsfall zu demonstrieren, sehen Sie sich den täglichen Umsatz des Vormonats im Vergleich zum gleichen Monat des Vorjahres an. Angenommen, Sie möchten sich die Einnahmen für jeden Tag im Januar 2016 ansehen und dann mit Januar 2015, Januar 2014 usw. vergleichen - dieser Bericht würde uns das zeigen.

1. Fügen Sie Ihre `Revenue` Metrik zum Bericht hinzu.
1. Klicken Sie auf **[!UICONTROL Duplicate]** , um eine Kopie der Metrik zu erstellen.
1. Benennen Sie die erste Metrik in `Items sold last 7 days` und die zweite in `Items sold last 28 days` um.
1. Klicken Sie auf **[!UICONTROL Time Range]** und dann auf **[!UICONTROL Moving Time Range]**. Legen Sie dies auf `Last Month` fest.
1. Klicken Sie auf **[!UICONTROL Time Interval]** und legen Sie `None` fest.
1. Klicken Sie auf **[!UICONTROL Time Options]** (Uhrensymbol) neben der zweiten `Revenue`.
1. Klicken Sie in dem erweiterten Fenster, das über dem Bericht angezeigt wird, auf **[!UICONTROL Time Options]** .
1. Legen Sie in der Dropdown-Liste Folgendes fest:

   * `Time Interval`: Setzen Sie dies auf `None`.

   * `Time Range`: Legen Sie dies auf `From 14 Months Ago To 13 Months Ago` fest, indem Sie zuerst auf **[!UICONTROL Custom]** und dann auf **[!UICONTROL Moving Range]** klicken. Verwenden Sie die Felder und Dropdown-Listen oben im Menü, um den Bereich festzulegen. Mit dieser Einstellung können wir den Umsatz für den Vormonat, aber für das Vorjahr anzeigen.

   Machen Sie sich keine Gedanken, wenn die Metrik aus dem Bericht verschwindet - durch Festlegen einer unabhängigen Zeitoption wird die Metrik automatisch aus dem Bericht ausgeblendet. Um sie erneut anzuzeigen, klicken Sie **[!UICONTROL Show]** neben der Metrik.

   ![](../assets/Different_Time_Ranges.gif)

   * Klicken Sie auf **[!UICONTROL Apply]** , um die Intervall- und Bereichseinstellungen zu speichern.

   * Als Nächstes fügen Sie Ihre benutzerdefinierte `Day number of the month` hinzu, indem Sie auf **[!UICONTROL Group By]** klicken und die Dimension auswählen. Dadurch wird die Tagesnummer des Monats einer Bestellung zurückgegeben - z. B. gibt eine Bestellung am 2. März `2` zurück.

   * Wählen Sie in der Dropdown-Liste `Group By` die Option `Show All` und klicken Sie auf **[!UICONTROL Apply]**. Dadurch werden die X-Achsenwerte für den Bericht erstellt:

   ![](../assets/TO4.png)

   * Benennen Sie die Metriken um. Im Beispiel ist die erste Metrik `Revenue - 2015` und die zweite `Revenue - 2014`.

Eine weitere gängige Verwendung von `Time Options` ist die Bestimmung der Lieferwochen. Insbesondere während der Weihnachtssaison oder eines speziellen Werbezeitraums sollten Sie Artikel in Betracht ziehen, die in der letzten Woche, im letzten Monat und im vorherigen Werbezeitraum verkauft wurden, um fundierte Kaufentscheidungen zu treffen.

Denken Sie daran, die Zeitbereiche auf das einzustellen, was Sie benötigen, wenn Sie diesen Bericht selbst erstellen.

1. Fügen Sie Ihre `Items Sold` Metrik zum Bericht hinzu.
1. Klicken Sie auf **[!UICONTROL Duplicate]** , um eine Kopie der Metrik zu erstellen.
1. Benennen Sie die Metriken um. Sie können dieselben Namen verwenden oder etwas Ähnliches verwenden:
   1. Benennen Sie die erste Metrik in `Items sold last 7 days` um.
   1. Benennen Sie die zweite Metrik in `Items sold last 28 days` um.
1. Klicken Sie in der Metrik `Items sold last 7 days` auf die Option Globale **[!UICONTROL Time Range]** und dann auf **[!UICONTROL Moving Time Range]**. Für dieses Beispiel legen Sie `Last 7 Days` fest.
1. Klicken Sie auf **[!UICONTROL Time Interval]** und legen Sie `None` fest.
1. Als Nächstes definieren Sie die `Time Options` für die `Items sold last 28 days`. Klicken Sie auf **[!UICONTROL Time Options]** (Uhrensymbol) rechts neben der `second Items sold`.
1. Klicken Sie in dem erweiterten Fenster, das über dem Bericht angezeigt wird, auf **[!UICONTROL Time Options]** .
1. Legen Sie in der Dropdown-Liste Folgendes fest:

   * `Time Interval`: Setzen Sie dies auf `None`.
   * `Time Range`: Legen Sie dies auf `From 29 days to 1 day ago` fest, indem Sie zuerst auf **[!UICONTROL Custom]** und dann auf **[!UICONTROL Moving Range]** klicken. Verwenden Sie die Felder und Dropdown-Listen oben im Menü, um den Bereich festzulegen.
   * Klicken Sie auf **[!UICONTROL Apply]** , um die Intervall- und Bereichseinstellungen zu speichern.
   * Duplizieren Sie die `Items sold last 28 days` und öffnen Sie die `Time Options` der neuen Metrik. Legen Sie die Optionen wie folgt fest:

      * `Time Interval`: Belassen Sie das als `None`.
      * `Time Range`: Ändern Sie dies in den Datumsbereich, der der gewünschten Promotion entspricht, indem Sie auf **[!UICONTROL Specific Date Range]** klicken und dann die entsprechenden Daten eingeben.
      * Benennen Sie die `Items sold during last promotion` um oder etwas Ähnliches.
      * Fügen Sie Ihre `Units on hand` hinzu.
      * Als Nächstes müssen Sie die Berechnungen hinzufügen, die uns die verfügbaren Wochen unter Berücksichtigung der Umsatztrends für die Zeiträume (`last 7 days`, `last 28 days` und `last promo`) zeigen, die Sie in den Bericht aufnehmen. Sie müssen dies für jeden Zeitraum einmal tun.

Um die Formeln zu erstellen, klicken Sie auf **[!UICONTROL Add Formula]**. Geben Sie die unten stehenden Formeln ein und klicken Sie abschließend auf **[!UICONTROL Apply Changes]** . Wiederholen Sie dies für jeden der drei Zeiträume:

* Geben Sie für die `last 7 days time period` `D / A` in das Feld `Formula` ein.
* Geben Sie für die `last 28 days time period` `D / (B/4)` in das Feld `Formula` ein.

  >[!NOTE]
  >
  >Es ist wichtig, Ihre ausgewählten Zeitbereiche hier zu normalisieren. Teilen Sie in diesem Beispiel 28 Tage in vier Wochen auf. Möglicherweise müssen Sie verschiedene Logiken auf die Formel anwenden.

* Geben Sie für die `last promo period` `D / C` in das Feld `Formula` ein.

  ![](../assets/Different_Time_Ranges_2.png)

* Passen Sie abschließend den Bericht an, indem Sie die Metriken ausblenden und dem Bericht eine `SKU` oder eine ähnliche Dimension als `Group By` hinzufügen.

Dieses Beispiel zeigt, dass die aktuellen Lagerbestände für einen produktweiten 14-Tage-Verkauf gut gelegen waren. Das Hinzufügen eines vergleichbaren Werbezeitraums legt jedoch nahe, dass das Unternehmen einige Änderungen vornehmen muss - entweder indem es mehr Inventar bestellt und nur die Artikel mit genügend Einheiten auf Lager bewirbt.

Da sich Ihre Kunden im Laufe der Zeit anders verhalten, können Sie bei der Durchführung von Analysen Datenabweichungen erwarten. Durch das Festlegen benutzerdefinierter Zeitoptionen können Sie schnell komplexe Analysen erstellen und datengesteuerte Entscheidungen ermöglichen, die historische Trends berücksichtigen.

