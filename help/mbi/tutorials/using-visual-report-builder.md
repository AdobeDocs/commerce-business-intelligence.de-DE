---
title: Visual Report Builder verwenden
description: Hier erfahren Sie, wie Sie die Daten in Ihrem Bericht für einen bestimmten Zeitraum analysieren.
exl-id: da97b63d-63f0-4fd6-87e3-4cac49a42acc
source-git-commit: df81d2b036d00cd53274ec1ae22031dbf06cc948
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 0%

---

# Verwenden Sie die [!DNL Visual Report Builder]

Die [[!DNL Visual Report Builder]](../data-user/reports/ess-rpt-build-visual.md) ermöglicht es Ihnen, Ihre Daten visuell zu untersuchen, um Erkenntnisse zu gewinnen und geschäftliche Entscheidungen zu fördern. Dieses Tutorial führt Sie durch den Prozess der Erstellung eines Basisberichts.

>[!NOTE]
>
>Um einem Dashboard einen Bericht hinzuzufügen, benötigen Sie `Standard` [Benutzerberechtigungen](../administrator/user-management/user-management.md) und `Edit` Zugriff auf das Dashboard.

## Schritt 1: Erstellen eines Berichts

Um mit der Erstellung eines Berichts zu beginnen, klicken Sie auf **[!UICONTROL Report Builder]** auf der Seitenleiste oder **[!UICONTROL Add Report]** oben in jedem Dashboard. Wenn die `Report Builder` angezeigt wird, klicken Sie auf die **[!UICONTROL Visual Report Builder]** -Option.

So bearbeiten Sie einen Bericht, der im [!DNL Visual Report Builder], klicken Sie auf das Zahnradsymbol (Optionen) in der oberen rechten Ecke eines beliebigen Diagramms und klicken Sie dann auf **[!UICONTROL Edit]**.

## Schritt 2: Hinzufügen von Metriken

Der erste Schritt bei der Erstellung einer Analyse besteht darin, [die Metrik](../data-user/reports/ess-manage-data-metrics.md) zu analysieren. Während die Metriken standardmäßig alphabetisch aufgelistet sind, können Sie sie auch nach der Tabelle gruppieren, auf der die Metrik basiert.

Sie können nach Auswahl der ursprünglichen Metrik zusätzliche Metriken hinzufügen und alle Metriken in einem einzelnen Bericht überlagern oder mehrere Metriken berechnen, indem Sie Formeln hinzufügen.

## Schritt 3: Hinzufügen `Formulas`

`Formulas` zu Berichten hinzugefügt werden, indem Sie auf **[!UICONTROL Add Formula]**, direkt über der Liste der Metriken im Bericht. Im [Formeleditor](../data-analyst/dev-reports/formulas-in-rpt-bldr.md)können alle im Bericht enthaltenen Metriken als Eingaben verwendet werden. Grundlegende mathematische Operatoren werden verwendet, um die verschiedenen Metriken zu bearbeiten.

Angenommen, Sie möchten einen Bericht erstellen, der uns den durchschnittlichen Umsatz pro Bestellung zeigt. In diesem Fall würden Sie die `Revenue` Metrik nach `Number of orders` Metrik.

![](../assets/ave-rev-per-order.png)

## Schritt 4: Festlegen der `Time Period` und `Interval of Analysis` {#time}

Wenn Sie einen bestimmten Zeitraum nicht einbeziehen möchten, können Sie den Zeitraum für die Analyse festlegen. Sie können auch Zeitintervalle auswählen, um die Daten zu segmentieren (z. B. nach Jahr, Quartal oder Monat). Verwenden Sie die Menüs in der oberen rechten Ecke des Diagramms, um den Zeitraum und das Intervall festzulegen.

![](../assets/Time_Options_Report_Builder.png)

Stellen Sie beim Festlegen eines bestimmten Datumsbereichs für den Zeitraum sicher, dass sich das Startdatum am Anfang des Intervalls befindet und das Enddatum am Ende Ihres Intervalls liegt.

Beispielsweise können Sie einen Zeitraum von `January 1st` nach `March 1st` und wählen Sie eine `monthly` interval zeigt `March` als Datenpunkt verwenden, jedoch jeden Tag in `March` Ausnahme `March 1`. In diesem Fall sollten Sie Ihre `Time Period` von `January 1 to March 31`.

## Schritt 5: `Group by` / `Segmenting the Analysis` {#groupby}

[So segmentieren Sie Ihre Metriken nach Datendimensionen](../best-practices/segment-filter.md), klicken Sie auf die **[!UICONTROL Group by]** oben links im Diagramm. Dadurch wird eine Dropdown-Liste mit allen verfügbaren Dimensionen der ersten in der Liste enthaltenen Metrik angezeigt.

Sie können `None` , um zu verhindern, dass eine Metrik segmentiert wird. So könnten Sie beispielsweise eine Metrik wünschen, die den Gesamtumsatz ohne Segmentierung zurückgibt, während eine andere Umsatzmetrik nach Region segmentiert ist.

Kehren Sie zu Ihrem Beispiel für den durchschnittlichen Umsatz pro Bestellung zurück und legen Sie die Gruppe auf den Angebotscode fest. Dies zeigt Ihnen den durchschnittlichen Umsatz pro Bestellung für Bestellungen mit und ohne Sonderangebotscode.

![](../assets/Group_By_Report_Builder.png)

Wenn die in der Analyse enthaltenen Metriken auf unterschiedlichen Datentabellen basieren, können Sie in einem Popup-Fenster die passende Datendimension in jeder Tabelle auswählen. Das Ziel besteht hier darin, Dimensionen zu finden, die den Typ von Werten für die Segmentierung teilen:

![](../assets/Dimension_Editor.png)

## Schritt 6: Einstellung `Metric Filters`, `Perspective`und `Time Interval` {#metric-specific}

Für jede zur Analyse hinzugefügte Metrik können Sie Filter hinzufügen, die relevante Datenperspektive auswählen und `time interval` Optionen. Um auf diese Funktionen zuzugreifen, klicken Sie auf den Trichter (`Filter`), Auge (`Perspective`) und der Uhr (`Time`) neben den im Bericht enthaltenen Metriken.

![](../assets/Filters_Perspective_Interval_Report_builder.png)

### `Filters`

`Filters` den in der Analyse enthaltenen Datensatz zu begrenzen. Filter sind beispielsweise beim Auswerten einzelner Akquisekanäle und beim Entfernen von Ausreißern nützlich.

Zusätzlich zu den Dropdown-Menüs und dem Textfeld können Sie auch spezielle Filteroperatoren wie `LIKE` oder `IN` , um Filter zu erstellen.

Die Verwendung von Platzhaltern (`%` oder `_`) mit `LIKE` -Anweisungen unterstützt. Die `%` Platzhalter entspricht mehreren Zeichen, während `_` entspricht nur einem einzelnen Zeichen. Beispiel:

- `affiliate's name Like B%` erlaubt nur Daten von Kunden, deren Name mit `B`.

- `affiliate's name Like _ake` erlaubt nur Daten von Kunden, deren Namen ungefähr `Jake`, `Rake`oder `Bake` aber nicht `Drake` oder `Blake`.

Durch das Hinzufügen mehrerer Filter können die Daten der Grafik genau gesteuert werden. Standardmäßig müssen alle Filterbedingungen wahr sein, damit ein Datenelement eingeschlossen wird. Sie können jedoch ODER-Beziehungen erstellen, indem Sie das Textfeld Filterregeln bearbeiten.

![](../assets/edit-filter-rules.png)

### `Perspectives`

`Perspectives` Ermöglicht Ihnen den einfachen Umschalter zwischen verschiedenen Ansichten Ihrer Daten. Sehen Sie sich an, was verfügbar ist:

- `Standard perspective`: Die Standardperspektive zeigt Ihnen das Ergebnis für das entsprechende Datum auf der X-Achse (z. B. Umsatz im Januar). Dies ist die Perspektive, die Sie in Ihrem Beispiel Durchschnittlicher Umsatz pro Bestellung verwenden.

![](../assets/Standard.png)

- `Amount` ODER `Percent Change` versus `Previous Period` Perspektive: Diese Perspektive zeigt die Menge oder prozentuale Veränderung von einem Intervall zum nächsten und ist nützlich zur Messung der Änderungsrate bei schnell wechselnden Metriken. Es gibt auch eine Perspektive, um das Intervall mit dem gleichen Zeitraum im letzten Jahr zu vergleichen und das Wachstum im Jahresvergleich anzuzeigen.

![](../assets/Amt_or_Percent_Change.png)

- `Cumulative perspective`: Die `cumulative perspective` zeigt den laufenden oder kumulativen Summenbetrag der Metrik über den Zeitraum an. Dies wird häufig zur Analyse der Gesamtkunden und zur Planung künftiger Kapazitäten verwendet.

![](../assets/Cumulative_Perspective.png)

- `Percent of First Value perspective`: Diese Perspektive zeigt die Daten als Prozentsatz des in der Analyse enthaltenen Erstintervalls. Dies ist hilfreich bei der Messung der Effektivität spezifischer Aktionen im Vergleich zur Leistung des ersten Zeitraums.

![](../assets/Percent_of_First_Value.png)

- `Rolling averages window perspective`: Die Perspektive &quot;Rollierende Durchschnittswerte&quot;zeigt den rollierenden Durchschnittswert einer Metrik über den angegebenen Zeitraum. Das Intervall muss mit dem auf Berichtsebene festgelegten Intervall übereinstimmen. Wenn der Bericht beispielsweise das letzte vollständige Quartal des Umsatzes pro Woche anzeigt, können Sie den rollierenden durchschnittlichen Fensterzeitbereich auf vier Wochen festlegen. Dadurch sind die ersten drei Werte null und der vierte Wert stellt den Durchschnitt der ersten vier Umsatzwochen dar. Stellen Sie für mehr Klarheit sicher, dass Sie die `Multiple Y-Axes` aktivieren, wenn Sie dieselbe Metrik mit einem rollierenden Durchschnitt anzeigen, wie im Beispiel unten.

![](../assets/rolling_avg_window.png)

### Metrikspezifische Zeitoptionen

Für in Berichten verwendete Metriken gibt es zwei Optionen: sie können einen Trend im Zeitverlauf entsprechend den globalen Zeitoptionen aufweisen oder nicht, wodurch sie als Skalarzahl angezeigt werden.

Ändern eines Metrikzeitintervalls in `None` gibt eine `scalar` Zahl, was beim Erstellen von Formeln nützlich ist, bei denen eine Metrik mit Trends in der Zeit durch eine `scalar` Zahl. Sie können auch den Zeitbereich der `scalar` auf einen Zeitraum, der unabhängig von dem für den Bericht ist.

Nehmen wir beispielsweise an, Sie wollten sehen, dass der monatliche Umsatz von 2019 in Prozent des Gesamtumsatzes von 2019 ausgedrückt wird. Sie können zwei `Revenue` Metriken zu einem Bericht mit einem globalen Zeitbereich vom 1. Januar 2019 bis zum 31. Dezember 2019, segmentiert nach Monatsintervall.

>[!NOTE]
>
>Wenn Sie `group by` Dimensionen, wählen Sie eine neue Visualisierung aus oder passen Sie das Zeitintervall an und speichern Sie dann nur die Zahl (`scalar`). Diese Anpassungen werden nicht beibehalten, wenn Sie den Bericht das nächste Mal über ein Dashboard öffnen - es wird nur der Zeitraum beibehalten.

Weitere Informationen zur Verwendung von Zeitoptionen in Berichten finden Sie in diesem [Tutorial](../tutorials/time-options-visual-rpt-bldr.md).

## Schritt 7: Speichern des Berichts

Wenn Sie ein Diagramm erstellen, können Sie es speichern, indem Sie auf **[!UICONTROL Save]** oben rechts im `Visual Report Builder`.

Sie können ein Diagramm, eine Tabelle oder eine Zahl (`scalar`) mithilfe der `Type` und das Dashboard, in dem der Bericht gespeichert werden soll, mithilfe der `Location` Dropdown-Liste.

Anschließend können Sie den Bericht speichern, indem Sie auf **[!UICONTROL Save to Dashboard]**.

![](../assets/save-to-dashboard.png)

## Berichtsausgaben

Informationen zur Auswahl der Berichtausgabe finden Sie unter folgenden Themen:

### Diagramm

![](../assets/RB_Chart.png)

### Verzeichnis

![](../assets/RB_Table.png)

### Zahl (`scalar`)

![](../assets/RB_Scalar.png)

Herzlichen Glückwunsch! Du bist fertig.
