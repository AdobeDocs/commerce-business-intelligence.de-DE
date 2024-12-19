---
title: Visualisierungsoptionen in Visual Report Builder
description: Erfahren Sie, wie Sie die Visualisierungsoptionen in Visual Report Builder verwenden.
exl-id: e42a004e-28e3-4484-bb5a-b58c810b23e0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---

# Visualisierungsoptionen

Die Auswahl der richtigen Visualisierung für einen bestimmten Datensatz ist ein wichtiger Teil des Analyseprozesses. Jeder Datensatz hat eine Geschichte zu erzählen, aber die Wirkung dieser Geschichte wird durch ihre visuelle Wirkung und Lesbarkeit betont.

Das [!DNL Commerce Intelligence] [!DNL Visual Report Builder] bietet 12 verschiedene Visualisierungsoptionen mit ihren jeweiligen Vorteilen und Anwendungsfällen. In diesem Abschnitt werden die verschiedenen Visualisierungsoptionen in [!DNL Commerce Intelligence] erläutert, einschließlich erforderlicher Berichtskonfigurationen (falls zutreffend) und eines Beispiels für einen Anwendungsfall. Die folgenden Visualisierungen sind in [!DNL Commerce Intelligence] verfügbar:

* `Scalar`
* `Table`
* `Line`
* `Bar`
* `Stacked Bar`
* `Column`
* `Stacked Column`
* `Pie`
* `Area`
* `Funnel`
* `Scatter plot`
* `Bubble`
* `Heatmap`

## `Scalar`

`Scalar` Berichte werden als einzelner numerischer Wert angezeigt. Meistens wird dies verwendet, um den Wert „all time“ einer Schlüsselmetrik wie Umsatz oder Bestellungen anzuzeigen oder den Umsatz mit dem aktuellen Datum und dem Budget mit zwei separaten Skalarberichten zu vergleichen. Im folgenden Beispiel wird lediglich die Gesamtzahl der Bestellungen für das jeweilige Reporting-Intervall angezeigt:

![](../../assets/blobid0.png)

Um einen Bericht als Skalar zu speichern, konfigurieren Sie Ihre Filter und Zeiteinstellungen und klicken Sie dann oben rechts im Bericht auf **[!UICONTROL Save]** oder **[!UICONTROL Update]** . Wählen Sie in der Dropdown-Liste `Type` den Namen Zahl: Metrik aus, um den Bericht als den in der linken Seitenleiste angezeigten Wert zu speichern.

![](../../assets/blobid1.png)

**Voraussetzungen**:

* `Time interval`: `None`
* `Group by`: `None`
* Nur eine Metrik

## `Table`

Wie der Name schon sagt, eignen sich `table` Berichte hervorragend für die Anzeige von Tabellendetails. Wenn in einem einzelnen Bericht viele Gruppen nach Werten oder Metriken angezeigt werden müssen, ist eine Tabelle oft die beste Lösung. Nachfolgend finden Sie eine Tabelle mit „Kundendetails“, in der Bestellungen und Umsatz nach Kunden-E-Mail gruppiert angezeigt werden:

![](../../assets/blobid2.png)

Ähnlich wie bei Skalarberichten können Sie einen Bericht als Tabelle speichern, indem Sie im Report Builder auf **[!UICONTROL Save]** oder **[!UICONTROL Update]** klicken und dann die Option Tabelle in der Dropdown-Liste `Type` auswählen.

![](../../assets/blobid3.png)

**Voraussetzungen:**

* Obwohl es keine Berichtskonfigurationsanforderungen gibt, ist es wichtig zu beachten, dass Tabellen auf 3.500 Zeilen beschränkt sind. Wenn Ihr Datensatz mehr als 3.500 Zeilen enthält, müssen Sie entweder die Ergebnisse filtern, um den Umfang einzugrenzen, oder die Ergebnisse nach `.csv` oder `Excel` exportieren, um den vollständigen Datensatz anzuzeigen.

## `Line`

`Line` Diagramme sind die perfekte Wahl, um die Leistung ähnlicher Metrikkohorten zu vergleichen. Beispielsweise können Sie, wie unten dargestellt, die Umsätze zweier Regionen über denselben Zeitraum analysieren oder das jährliche Wachstum der Auftragserfüllung vergleichen:

![](../../assets/blobid0.png)

Jede Metrik und Formel, die dem Bericht hinzugefügt wird, wird durch eine eigene Zeile dargestellt. Vergessen Sie beim Vergleich von Metriken mit ähnlichen Einheiten und Maßstäben nicht, das Kontrollkästchen zu deaktivieren, damit `Multiple Y-Axes` alle Metriken auf derselben Skala anzeigen können.

Um einen Bericht als Liniendiagramm zu speichern, passen Sie den `Type` an `Chart` an und wählen Sie die entsprechende Visualisierung in Report Builder aus, wie unten dargestellt:

![](../../assets/blobid1.png)

**Voraussetzungen:**

* Keine

## `Bar`

`Bar` Diagramme zeigen Ihre Daten als eine Reihe horizontaler Balken an und eignen sich am besten zur Anzeige der Gesamtleistung einer begrenzten Anzahl von Metriken oder „Gruppieren nach“-Werten. Beispielsweise könnte ein Balkendiagramm verwendet werden, um den Umsatz nach Filiale zu vergleichen:

![](../../assets/blobid2.png)

Jede einzelne Kombination aus Metrik, Gruppierung nach und Zeitintervall wird als eigener Balken angezeigt. Wenn Sie zwei Metriken mit einer `group by` haben, die drei verschiedene `group by` enthalten, zeigt Ihr Bericht sechs separate Balken an.

Um einen Bericht als Balkendiagramm zu speichern, passen Sie den `Type` an `Chart` an und wählen Sie die Option `Bar` wie unten dargestellt aus:

![](../../assets/blobid3.png)

**Voraussetzungen:**

* Keine

## `Stacked Bar`

`Stacked bar` Diagramme ähneln ihren Balkendiagrammen, mit der zusätzlichen Möglichkeit, die proportionale Aufschlüsselung jedes Balkens anzuzeigen. In den meisten Fällen werden gestapelte Balkendiagramme mit zwei oder mehr Metriken und einem einzigen Gruppierungsfeld eingerichtet, sodass jeder Balken eine eindeutige Wertegruppe darstellt, die auf die einzelnen Metrikkomponenten aufgeteilt ist.

Der folgende Bericht enthält beispielsweise zwei identische Umsatzmetriken, von denen eine für Erstbestellungen und die andere für Wiederholungsaufträge gefiltert wurde. Nach der Gruppierung nach Store können Sie sowohl den Gesamtumsatzbeitrag für jeden Store (dargestellt durch die Gesamtbreite des Balkens) als auch die erste vs. wiederholte Aufschlüsselung des Umsatzes für jeden Store sehen.

![](../../assets/blobid4.png)

Stellen Sie sicher, dass das `Multiple Y-Axes` beim Einrichten eines Berichts wie des oben genannten deaktiviert ist.

Um einen Bericht als gestapeltes Balkendiagramm zu speichern, passen Sie den `Type` an `Chart` an und wählen Sie die Option Gestapelter Balken im Report Builder aus:

![](../../assets/blobid5.png)

**Voraussetzungen:**

* Keine

## `Column`

`Column` Diagramme stellen jeden Datenpunkt als vertikale Spalte dar und eignen sich besser zur Anzeige von Daten mit Zeittrends als die horizontale Balkendiagrammvisualisierung. Jede einzelne Metrik und Gruppe nach Kombination wird in einer eigenen Reihe von Balken dargestellt. Ein Spaltenbericht eignet sich am besten für Berichte mit drei oder weniger Metriken oder einer Metrik mit einer einzigen Gruppe, indem er 1-3 Werte für „Gruppieren nach“ enthält.

Im folgenden Beispiel sehen Sie zwei Umsatzmetriken: eine nach erstmaligem Umsatz und die andere nach wiederholtem Umsatz, mit einem Trend im Zeitverlauf nach Monat:

![](../../assets/blobid6.png)

Spaltenberichte können gespeichert werden, indem die `Type` in `Chart` geändert und die Option für die Spaltenvisualisierung ausgewählt wird:

![](../../assets/blobid7.png)

**Voraussetzungen:**

* Keine

## `Stacked Column`

`Stacked column` Berichte sind fast identisch mit Spaltendiagrammen, mit der Ausnahme, dass ähnliche Spalten so übereinander gestapelt sind, dass die Gesamthöhe die Summe der Werte darstellt. Gestapelte Spalten werden wieder am besten mit einer begrenzten Anzahl von Metriken oder Gruppenbys visualisiert.

Wenn Sie dieselbe Berichtskonfiguration wie im obigen Abschnitt `Column` verwenden, würde ein Bericht mit zwei Umsatzmetriken (erstmalig gefiltert und wiederholt) wie folgt aussehen mit einer gestapelten Spaltenvisualisierung:

![](../../assets/blobid8.png)

Auch hier ist es wichtig, dass das Kontrollkästchen `Multiple Y-Axes` deaktiviert wird, wenn mit der gestapelten Spaltenvisualisierung mehrere Metriken angezeigt werden.

Um einen Bericht als gestapelte Spalte zu speichern, setzen Sie den `Type` auf `Chart` und wählen Sie die Option `stacked column` aus:

![](../../assets/blobid9.png)

**Voraussetzungen:**

* Keine

## `Pie`

`Pie` Diagramme eignen sich am besten für die Anzeige einer einzelnen Metrik mit einem oder mehreren Gruppenbys oder mehrerer Metriken ohne Gruppenbys. In beiden Fällen muss das Zeitintervall auf „Ohne“ festgelegt sein, damit Daten in einem Tortendiagramm angezeigt werden. Im folgenden Beispiel wird eine einzelne Bestellmetrik nach Shop-Namen gruppiert, um die Aufschlüsselung der Bestellungen nach Shop anzuzeigen:

![](../../assets/blobid10.png)

Um einen Bericht als Tortendiagramm zu speichern, setzen Sie den `Type` auf `Chart` und wählen Sie die Option `pie` wie unten dargestellt aus:

![](../../assets/blobid11.png)

**Voraussetzungen:**

* `Time interval`: `None`
* Eine der folgenden Möglichkeiten:
   * `Single metric with one or more group bys`
   * `Multiple metrics with no group bys`

## `Area`

`Area` Diagramme sind fast identisch mit gestapelten Säulendiagrammen, mit der Ausnahme, dass die Spalten kontinuierlich angezeigt werden. Ähnlich wie gestapelte Spalten werden Bereichsdiagramme am besten mit einer begrenzten Anzahl von Gruppensymbolen oder Metriken visualisiert.

Unter Verwendung des gleichen Beispiels aus dem Abschnitt `stacked column` zeigt der nachstehende Bericht den ersten Umsatz im Vergleich zu den wiederholten Einnahmen mit der Visualisierung des Flächendiagramms:

![](../../assets/blobid12.png)

Um einen Bericht als Flächendiagramm zu speichern, passen Sie die `Type` an `Chart` an und wählen Sie die Option Bereich aus:

![](../../assets/blobid13.png)

**Voraussetzungen:**

* Keine

## `Funnel`

`Funnel` Diagramme eignen sich perfekt zur Visualisierung von Konversionen in einer erwarteten Ereignissequenz. Einige Beispiele sind die Analyse des potenziellen Umsatzes in Ihrem Verkaufstrichter vom Lead zum geschlossenen Abschluss oder die Messung des Rückgangs bei den Kunden zwischen ihrer ersten und zweiten Bestellung, der zweiten und dritten Bestellung usw. Ein Beispiel für Letzteres wird unten angezeigt:

![](../../assets/blobid4.png)

In einem Trichterbericht wird der relative Wert einer bestimmten Stufe des Trichters durch die Höhe der Stufe widergespiegelt. Die Berichtskonfiguration bestimmt die Reihenfolge, in der die Schritte angezeigt werden. Es gibt zwei Möglichkeiten, einen Trichterbericht zu konfigurieren:

* `Single metric with one group by`: - Reihenfolge der Schritte, bestimmt durch die Einstellung „Oben/Unten anzeigen“ in der Gruppe von. Standardmäßig werden die Trichterschritte in der Reihenfolge vom größten zum kleinsten Wert angezeigt, Sie können sie jedoch auch alphabetisch nach der Gruppe „Nach Name“ sortieren.

* `Multiple metrics with no group by`: - Reihenfolge der Schritte, die durch die Reihenfolge bestimmt wird, in der die Metriken dem Bericht hinzugefügt werden.

Um einen Bericht als Trichterdiagramm zu speichern, passen Sie den `Type` `Chart` an und wählen Sie die entsprechende Visualisierung in Report Builder aus.

![](../../assets/blobid5.png)

**Voraussetzungen:**

* `Time interval`: `None`
* Eine der folgenden Möglichkeiten:
   * `Single metric with one group by`
   * `Multiple metrics with no group by`

## `Scatter plot`

Eine `scatter plot` wird verwendet, um die Beziehung einer Metrik mit zwei verschiedenen Variablen zu untersuchen, damit Sie Korrelationen und Ausreißer einfach identifizieren können. Diese Art der Visualisierung eignet sich am besten nur für numerische Dimensionen. Versuchen Sie es mit der Bestellmetrik und den `Customer's lifetime number of coupons`- und `Customer's lifetime revenue` Dimensionen, um zu sehen, wie die Couponnutzung mit dem Umsatz zusammenhängt. Sie können zwischen einem Streudiagramm mit und ohne Trendlinie wählen:

![](../../assets/scatter-plot-1.png)

![ohne Trendlinie](../../assets/scatter-plot-2.png)

![](../../assets/scatter-plot-3.png)

![mit Trendlinie](../../assets/scatter-plot-4.png)

**Voraussetzungen:**

Option 1:

* Zwei `metrics`
* Ein `group by`
* `Time interval`: `None`

Option 2:

* Zwei `metrics`
* Keine `group by`
* `time interval` festlegen

## `Bubble`

In einem `bubble` können bis zu vier Datendimensionen angezeigt werden, wobei die `X`- und `Y` die Position der Blasen angeben. Die `Z` Achse ist die Größe der Blasen, und durch Einbeziehung von zwei Gruppen by können Sie Farbe zu den Blasen hinzufügen. Diese Art der Visualisierung empfiehlt sich, wenn Sie mehrere Datendimensionen in einem Diagramm darstellen möchten.

Das folgende Diagramm zeigt beispielsweise die Anzahl der Kunden (Blasengröße), gruppiert nach einer bestimmten Akquisequelle (Blasenfarbe) und dem Status (verschiedene Blasen in einer bestimmten Farbe), dargestellt als Gesamtumsatz und durchschnittliche Lebensdauerbestellungen.

![](../../assets/bubble-1.png)

Das folgende Diagramm zeigt die Anzahl der Kunden (Blasengröße), gruppiert nach Akquise-Quelle (Blasenfarbe) und Status (verschiedene Blasen in einer bestimmten Farbe), dargestellt als durchschnittlicher Lebenszeitwert und Gesamtumsatz.

![](../../assets/bubble-2.png)

**Anforderungen für ein Blasendiagramm mit einer Serie:**

Option 1

* Drei `metrics`
* Ein `group by`
* `Time interval`: `None`

Option 2

* Drei `metrics`
* Keine `group by`
* `time interval` festlegen

**Anforderungen an ein Mehrreihen-Blasendiagramm:**

* Drei `metrics`
* Zwei `group by`
* `Time interval`: `None`

## `Heatmap`

Verwenden Sie `heatmaps`, um Hotspots in Ihren Daten zu visualisieren. Beispielsweise kann eine Heatmap anzeigen, wo Sie routinemäßig eine höhere Lautstärke erhalten. Durch die Visualisierung dieser Daten können Sie Ihre Inventarebenen anpassen, um sicherzustellen, dass Sie den Bedarf während dieser Spitzenzeiten decken.

Die folgende Heatmap zeigt Bestellungen nach Wochentag und Stunde des Tages insgesamt über mehrere Wochen hinweg.

![](../../assets/heat-map.png)<!--{: width="650"}-->

**Voraussetzungen:**

Option 1

* Ein `metric`
* Zwei `group by`
* `Time interval`: `None`

Option 2

* Ein `metric`
* Ein `group by`
* `time interval` festlegen
