---
title: Zeitoptionen in Visual Report Builder verwenden
description: Hier erfahren Sie, wie Sie die Daten in Ihrem Bericht für einen bestimmten Zeitraum analysieren.
exl-id: a1bb4838-f882-44b1-a29f-84b985032ceb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 0%

---

# [!DNL Time] Optionen in [!DNL Visual Report Builder] verwenden

Eine der Funktionen von [!DNL Visual Report Builder] sind die globalen Einstellungen `Time Range` und `Interval`. Mit diesen Einstellungen können Sie die Daten in Ihrem Bericht für einen bestimmten Zeitraum analysieren.

Bei einigen Analysen müssen Sie jedoch möglicherweise verschiedene Zeitbereiche oder Zeitintervalle im selben Bericht berücksichtigen. Hier kommen `Time` -Optionen hinzu. Um Ihnen eine bessere Vorstellung von der Verwendung der `Time` -Optionen in Ihren Berichten zu vermitteln, werden in diesem Tutorial die folgenden Anwendungsfälle behandelt:

* [Analysieren von Metriken ohne Zeitstempel](#notimestamp)
* [Geben einer Metrik ein unabhängiges Zeitintervall](#independenttimeinterval)
* [Vergleichen derselben Metrik über verschiedene Zeiträume hinweg](#difftimerange)

Wenn Sie einigen der in diesem Thema behandelten Beispielberichte folgen möchten, öffnen Sie den [[!DNL Visual Report Builder]](../data-user/reports/ess-rpt-build-visual.md) , bevor Sie fortfahren.

## Analysieren von Metriken ohne Zeitstempel {#notimestamp}

Einige Metriken können einfach keine Trendbildung im Zeitverlauf vornehmen, da die Daten nicht mit einem zugehörigen Zeitstempel erfasst oder gespeichert werden. Beispielsweise enthält eine Bestandstabelle oft nur eine Zeile für jede SKU. In diesem Fall sollten Sie [die Metrik](../data-user/reports/ess-manage-data-metrics.md) erstellen, ohne einen Zeitstempel anzugeben.

Wenn Sie eine solche Metrik in Ihren Berichten verwenden, stellen Sie fest, dass durch das Hinzufügen dieser Metrik zu einem Bericht automatisch ein unabhängiger `Time Interval` von `None` und `Time Range` von `Global` festgelegt wird:

![](../assets/Metrics_without_timestamps.gif)

## Geben einer Metrik ein unabhängiges Zeitintervall {#independenttimeinterval}

`Time` Mit Optionen können Sie zeitbasierte 100 %-Diagramme erstellen, um zu ermitteln, welcher Tag, welche Woche, welcher Monat oder welches Jahr während eines bestimmten Zeitraums am meisten beigetragen hat. In diesem Abschnitt erstellen Sie ein Diagramm, das Ihnen den Prozentsatz des Umsatzes anzeigt, der in jedem Kalendermonat eines Jahres generiert wurde.

Dieser Berichtstyp kann nützlich sein, wenn Sie den Umsatz vergleichen möchten, der im Jahresvergleich generiert wurde. Sie haben beispielsweise eine Grafik für 2015, die gezeigt hat, dass der Januar 18 Prozent des Umsatzes für das Jahr beigetragen hat, und eine Grafik für 2016 zeigte nur 8 Prozent. Du könntest anfangen zu recherchieren, was geschehen sein könnte.

1. Fügen Sie Ihre `Revenue` -Metrik zum Bericht hinzu.
1. Klicken Sie auf **[!UICONTROL Duplicate]** , um eine Kopie der Metrik zu erstellen.
1. Klicken Sie auf die globale **[!UICONTROL Time Range]** -Option und dann auf **[!UICONTROL Moving Time Range]**. Setzen Sie dies auf `Last Year`.
1. Klicken Sie auf die globale Option **[!UICONTROL Time Interval]** und legen Sie sie auf `Monthly` fest.
1. Report Builder fügt für eine zweite Metrik automatisch eine zweite Y-Achse hinzu. Heben Sie die Auswahl des Felds `Multiple Y-Axes` auf.
1. Als Nächstes wenden Sie eine unabhängige `Time Interval` auf die erste Metrik an. Klicken Sie rechts neben dem `first Revenue metric` auf **[!UICONTROL Time Options]** (Uhrensymbol).
1. Klicken Sie im erweiterten Fenster, das über dem Bericht angezeigt wird, auf &quot;**[!UICONTROL Time Options]**&quot;.
1. Legen Sie im Dropdown-Menü Folgendes fest:

   * `Time Interval`: Setzen Sie dies auf `None`.

   * `Time Range`: Setzen Sie dies auf `Last Year`, indem Sie zuerst auf **[!UICONTROL Custom]** und dann auf **[!UICONTROL Moving Range]** klicken und schließlich die Option `Last Year` auswählen.

   * Klicken Sie auf **[!UICONTROL Apply]** , um die Intervall- und Bereichseinstellungen zu speichern. Dadurch wird eine Metrik erstellt, die den Gesamtumsatz des Vorjahres berechnet. Als Nächstes verwenden Sie diese Metrik als Nenner in einer Formel.

   * Um den Prozentsatz des Umsatzes für jeden Monat anzuzeigen, müssen Sie dem Bericht eine Formel hinzufügen. Klicken Sie auf **[!UICONTROL Add Formula]**.

   * Geben Sie `B/A` in das Formelfeld ein und wählen Sie `% Percent` aus der Dropdown-Liste neben dem Textfeld aus. Mit dieser Formel wird der Umsatzbetrag von einem bestimmten Monat im letzten Jahr durch den Gesamtumsatz im letzten Jahr dividiert.

   * Klicken Sie auf **[!UICONTROL Apply Changes]**.

   * Blenden Sie beide Eingabemetriken aus und benennen Sie die Formel um.

Nun können Sie sehen, wie effektiv jeder Monat im letzten Jahr war:

![](../assets/Independent_Time_Int.png)

## Vergleichen derselben Metrik über verschiedene Zeiträume hinweg {#difftimerange}

In diesem Beispiel wird eine benutzerdefinierte Dimension namens `Day number of the month` verwendet. Wenn Sie diesen Bericht erstellen möchten und diese Dimension noch nicht in Ihrer Data Warehouse haben, wenden Sie sich für Unterstützung an den [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) .

Die beiden häufigsten Beispiele in dieser Kategorie sind (1) der Vergleich von Wachstumsmetriken (Umsatz im Jahr oder Monat im Monat) und (2) ein besseres Verständnis aktueller Inventar- oder Artikelverkaufstrends.

Um diesen Anwendungsfall zu demonstrieren, sehen Sie sich den täglichen Umsatz des Vormonats im Vergleich zum Vorjahresmonat an. Nehmen wir an, Sie möchten den Umsatz für jeden Tag im Januar 2016 betrachten und ihn dann mit Januar 2015, Januar 2014 usw. vergleichen - dieser Bericht würde uns das zeigen.

1. Fügen Sie Ihre `Revenue` -Metrik zum Bericht hinzu.
1. Klicken Sie auf **[!UICONTROL Duplicate]** , um eine Kopie der Metrik zu erstellen.
1. Benennen Sie die erste Metrik in `Items sold last 7 days` und die zweite in `Items sold last 28 days` um.
1. Klicken Sie auf **[!UICONTROL Time Range]** und dann auf **[!UICONTROL Moving Time Range]**. Setzen Sie dies auf `Last Month`.
1. Klicken Sie auf **[!UICONTROL Time Interval]** und legen Sie dafür den Wert `None` fest.
1. Klicken Sie neben der zweiten `Revenue` -Metrik auf **[!UICONTROL Time Options]** (Uhrensymbol).
1. Klicken Sie im erweiterten Fenster, das über dem Bericht angezeigt wird, auf &quot;**[!UICONTROL Time Options]**&quot;.
1. Legen Sie im Dropdown-Menü Folgendes fest:

   * `Time Interval`: Setzen Sie dies auf `None`.

   * `Time Range`: Setzen Sie dies auf `From 14 Months Ago To 13 Months Ago`, indem Sie zuerst auf **[!UICONTROL Custom]** und dann auf **[!UICONTROL Moving Range]** klicken. Verwenden Sie die Felder und Dropdown-Listen oben im Menü, um den Bereich festzulegen. Diese Einstellung ermöglicht es uns, den Umsatz des Vormonats, aber des Vorjahres zu sehen.

   Machen Sie sich keine Gedanken, wenn die Metrik aus dem Bericht verschwindet. Wenn Sie eine unabhängige Zeitoption festlegen, wird die Metrik automatisch aus dem Bericht ausgeblendet. Um sie erneut anzuzeigen, klicken Sie neben der Metrik auf **[!UICONTROL Show]** .

   ![](../assets/Different_Time_Ranges.gif)

   * Klicken Sie auf **[!UICONTROL Apply]** , um die Intervall- und Bereichseinstellungen zu speichern.

   * Als Nächstes fügen Sie Ihre benutzerdefinierte Dimension `Day number of the month` hinzu, indem Sie auf **[!UICONTROL Group By]** klicken und die Dimension auswählen. Dadurch wird die Tagesnummer des Monats einer Bestellung zurückgegeben, z. B. wird bei einer am 2. März aufgegebenen Bestellung `2` zurückgegeben.

   * Wählen Sie im Dropdown-Menü `Group By` die Option `Show All` aus und klicken Sie auf **[!UICONTROL Apply]**. Dadurch werden die X-Achsen-Werte für den Bericht erstellt:

   ![](../assets/TO4.png)

   * Benennen Sie die Metriken um. In diesem Beispiel ist die erste Metrik `Revenue - 2015` und die zweite `Revenue - 2014`.

Eine weitere gängige Verwendung von benutzerdefiniertem `Time Options` ist die Bestimmung der Lieferwochen. Insbesondere während der Weihnachtszeit oder eines speziellen Werbezeitraums können Sie Artikel berücksichtigen, die in der letzten Woche, im letzten Monat und im vorherigen Werbezeitraum verkauft wurden, um fundierte Kaufentscheidungen treffen zu können.

Denken Sie daran, die Zeiträume auf das zu setzen, was Sie beim Erstellen dieses Berichts selbst benötigen.

1. Fügen Sie Ihre `Items Sold` -Metrik zum Bericht hinzu.
1. Klicken Sie auf **[!UICONTROL Duplicate]** , um eine Kopie der Metrik zu erstellen.
1. Benennen Sie die Metriken um. Sie können dieselben Namen verwenden oder etwas Ähnliches verwenden:
   1. Benennen Sie die erste Metrik in `Items sold last 7 days` um.
   1. Benennen Sie die zweite Metrik in `Items sold last 28 days` um.
1. Klicken Sie auf der Metrik `Items sold last 7 days` auf die globale Option **[!UICONTROL Time Range]** und dann auf **[!UICONTROL Moving Time Range]**. Für dieses Beispiel setzen Sie es auf `Last 7 Days`.
1. Klicken Sie auf **[!UICONTROL Time Interval]** und legen Sie dafür den Wert `None` fest.
1. Als Nächstes definieren Sie den `Time Options` für die Metrik `Items sold last 28 days` . Klicken Sie rechts neben der Metrik `second Items sold` auf **[!UICONTROL Time Options]** (Uhrensymbol).
1. Klicken Sie im erweiterten Fenster, das über dem Bericht angezeigt wird, auf &quot;**[!UICONTROL Time Options]**&quot;.
1. Legen Sie im Dropdown-Menü Folgendes fest:

   * `Time Interval`: Setzen Sie dies auf `None`.
   * `Time Range`: Setzen Sie dies auf `From 29 days to 1 day ago`, indem Sie zuerst auf **[!UICONTROL Custom]** und dann auf **[!UICONTROL Moving Range]** klicken. Verwenden Sie die Felder und Dropdown-Listen oben im Menü, um den Bereich festzulegen.
   * Klicken Sie auf **[!UICONTROL Apply]** , um die Intervall- und Bereichseinstellungen zu speichern.
   * Duplizieren Sie die Metrik `Items sold last 28 days` und öffnen Sie die Metrik `Time Options` der neuen Metrik. Legen Sie die Optionen auf Folgendes fest:

      * `Time Interval`: Belassen Sie diesen Wert auf `None`.
      * `Time Range`: Ändern Sie diesen in den Datumsbereich, der mit der Promotion, an der Sie interessiert sind, übereinstimmt, indem Sie auf **[!UICONTROL Specific Date Range]** klicken und dann die entsprechenden Daten eingeben.
      * Benennen Sie die Metrik &quot;`Items sold during last promotion`&quot;oder eine ähnliche Metrik um.
      * Fügen Sie Ihre `Units on hand` -Metrik hinzu.
      * Als Nächstes müssen Sie die Berechnungen hinzufügen, die uns unter Berücksichtigung der Verkaufstrends für die Zeiträume (`last 7 days`, `last 28 days` und `last promo` Zeitraum) zeigen, die Sie in den Bericht einbeziehen. Sie müssen dies einmal für jeden Zeitraum tun.

Um die Formeln zu erstellen, klicken Sie auf **[!UICONTROL Add Formula]**. Geben Sie die folgenden Formeln ein und klicken Sie danach auf **[!UICONTROL Apply Changes]** . Wiederholen Sie diesen Vorgang für jeden der drei Zeiträume:

* Geben Sie für den Wert `last 7 days time period` `D / A` in das Feld `Formula` ein.
* Geben Sie für den Wert `last 28 days time period` `D / (B/4)` in das Feld `Formula` ein.

  >[!NOTE]
  >
  >Es ist wichtig, die ausgewählten Zeiträume hier zu normalisieren. Teilen Sie in diesem Beispiel 28 Tage in vier Wochen auf. Möglicherweise müssen Sie eine andere Logik auf die Formel anwenden.

* Geben Sie für den Wert `last promo period` `D / C` in das Feld `Formula` ein.

  ![](../assets/Different_Time_Ranges_2.png)

* Passen Sie schließlich den Bericht an, indem Sie die Metriken ausblenden und eine `SKU` oder eine ähnliche Dimension zum Bericht als `Group By` hinzufügen.

Dieses Beispiel zeigt, dass die aktuellen Lagerbestände für einen produktweiten 14-tägigen Verkauf gut aufgestellt waren. Wenn jedoch ein vergleichbarer Werbezeitraum hinzugefügt wird, muss das Unternehmen einige Änderungen vornehmen - entweder indem es mehr Inventar bestellt und nur Artikel mit genügend Lagereinheiten bewirbt.

Da sich Ihre Kunden im Laufe der Zeit anders verhalten, können Sie bei der Durchführung von Analysen mit Abweichungen in den Daten rechnen. Durch das Festlegen benutzerdefinierter Zeitoptionen können Sie schnell komplexe Analysen erstellen und datengesteuerte Entscheidungen ermöglichen, die historische Trends berücksichtigen.

