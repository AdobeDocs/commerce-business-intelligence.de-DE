---
title: Visualisierungsoptionen im Visual Report Builder
description: Erfahren Sie, wie Sie die Visualisierungsoptionen im Visual Report Builder verwenden.
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

Die [!DNL Commerce Intelligence] [!DNL Visual Report Builder] bietet 12 verschiedene Visualisierungsoptionen mit jeweils eigenen Vorteilen und Anwendungsfällen. In diesem Thema werden die verschiedenen Visualisierungsoptionen in [!DNL Commerce Intelligence] erläutert, einschließlich der erforderlichen Berichtskonfigurationen (falls zutreffend) und eines Beispiels für einen Anwendungsfall. Die folgenden Visualisierungen sind in [!DNL Commerce Intelligence] verfügbar:

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

`Scalar` -Berichte werden als einzelner, numerischer Wert angezeigt. In den meisten Fällen wird dies verwendet, um den &quot;Allzeit&quot;-Wert einer Schlüsselmetrik wie Umsatz oder Bestellungen anzuzeigen oder den Umsatz mit dem Datum und dem Budget mit zwei separaten skalaren Berichten zu vergleichen. Im folgenden Beispiel zeigt dies einfach die Gesamtzahl der Bestellungen für das jeweilige Berichtsintervall:

![](../../assets/blobid0.png)

Um einen Bericht als Skalar zu speichern, konfigurieren Sie Ihre Filter und Zeiteinstellungen und klicken Sie dann oben rechts im Bericht auf **[!UICONTROL Save]** oder **[!UICONTROL Update]** . Wählen Sie im Dropdown-Menü `Type` den Namen Zahl: Metrik aus, um den Bericht als Wert zu speichern, der auf der linken Seitenleiste angezeigt wird.

![](../../assets/blobid1.png)

**Anforderungen**:

* `Time interval`: `None`
* `Group by`: `None`
* Nur eine Metrik

## `Table`

Wie der Name schon sagt, eignen sich `table` -Berichte hervorragend für die Anzeige von Tabellendetails. Wenn viele Gruppen nach Werten oder Metriken in einem Bericht angezeigt werden müssen, ist eine Tabelle häufig der beste Weg. Unten finden Sie eine Tabelle mit &quot;Kundendetails&quot;, in der Bestellungen und Umsatz nach E-Mail-Adresse des Kunden gruppiert sind:

![](../../assets/blobid2.png)

Ähnlich wie bei skalaren Berichten können Sie einen Bericht als Tabelle speichern, indem Sie im ReportBuilder auf **[!UICONTROL Save]** oder **[!UICONTROL Update]** klicken und dann die Option Tabelle im Dropdown-Menü `Type` auswählen.

![](../../assets/blobid3.png)

**Anforderungen:**

* Es gibt zwar keine Anforderungen an die Berichtskonfiguration, es ist jedoch wichtig zu beachten, dass Tabellen auf 3500 Zeilen beschränkt sind. Wenn Ihr Datensatz mehr als 3500 Zeilen enthält, müssen Sie entweder die Ergebnisse filtern, um den Umfang einzugrenzen, oder die Ergebnisse in `.csv` oder `Excel` exportieren, um den vollständigen Datensatz anzuzeigen.

## `Line`

`Line` -Diagramme sind die perfekte Wahl für den Vergleich der Leistung ähnlicher Metrikkohorten. So können Sie beispielsweise die Einnahmen zweier Regionen im selben Zeitraum analysieren oder das Jahreswachstum bei Auftragseingängen im Jahresvergleich vergleichen, wie unten dargestellt:

![](../../assets/blobid0.png)

Jede zum Bericht hinzugefügte Metrik und Formel wird durch eine eigene Zeile dargestellt. Vergessen Sie beim Vergleich von Metriken mit ähnlichen Einheiten und Skalierungen nicht, das Kontrollkästchen für `Multiple Y-Axes` zu deaktivieren, damit alle Metriken auf derselben Skala angezeigt werden.

Um einen Bericht als Liniendiagramm zu speichern, passen Sie den Bericht `Type` auf `Chart` an und wählen Sie die entsprechende Visualisierung aus dem ReportBuilder aus, wie unten dargestellt:

![](../../assets/blobid1.png)

**Anforderungen:**

* Keines

## `Bar`

`Bar` -Diagramme zeigen Ihre Daten als Reihe von horizontalen Balken an und eignen sich am besten zur Anzeige der Gesamtleistung einer begrenzten Anzahl von Metriken oder der Gruppe nach Werten. Beispielsweise kann ein Balkendiagramm verwendet werden, um den Umsatz nach Geschäft zu vergleichen:

![](../../assets/blobid2.png)

Jede einzelne Kombination aus Metrik, Gruppe nach und Zeitintervall wird als eigener Balken angezeigt. Wenn Sie zwei Metriken mit einem `group by` haben, die drei verschiedene `group by` -Werte enthalten, zeigt Ihr Bericht sechs separate Balken an.

Um einen Bericht als Balkendiagramm zu speichern, passen Sie den Bericht `Type` auf `Chart` an und wählen Sie die Option `Bar` wie unten gezeigt aus:

![](../../assets/blobid3.png)

**Anforderungen:**

* Keines

## `Stacked Bar`

`Stacked bar` -Diagramme ähneln ihren Balkendiagrammbrüchen, mit der zusätzlichen Möglichkeit, die proportionale Aufschlüsselung der einzelnen Balken anzuzeigen. In den meisten Fällen werden gestapelte Balkendiagramme mit zwei oder mehr Metriken und einer einzigen Gruppe nach eingerichtet, sodass jede Leiste eine eindeutige Gruppe nach Wert darstellt, die auf die Metrikkomponenten aufgeteilt ist.

Beispielsweise weist der unten stehende Bericht zwei identische Umsatzmetriken auf, von denen eine für Erstbestellungen gefiltert und die andere für Wiederholungsbestellungen gefiltert ist. Nach der Gruppierung nach Geschäft können Sie sowohl den Gesamtumsatzbeitrag für jeden Store (dargestellt durch die Gesamtbreite des Balkens) als auch die erstmalige Aufschlüsselung des Umsatzes für jeden Store im Vergleich sehen.

![](../../assets/blobid4.png)

Stellen Sie sicher, dass das Kontrollkästchen `Multiple Y-Axes` deaktiviert ist, wenn Sie einen Bericht wie den oben genannten einrichten.

Um einen Bericht als gestapeltes Balkendiagramm zu speichern, passen Sie den Bericht `Type` auf `Chart` an und wählen Sie die Option für gestapelte Balken aus ReportBuilder aus:

![](../../assets/blobid5.png)

**Anforderungen:**

* Keines

## `Column`

`Column` -Diagramme stellen jeden Datenpunkt als vertikale Spalte dar und eignen sich besser für die Anzeige von Trend-Zeitdaten als für die horizontale Balkendiagrammvisualisierung. Jede einzelne Metrik und Gruppe nach Kombination wird in einer eigenen Serie von Balken dargestellt. Ein Spaltenbericht eignet sich am besten für Berichte mit drei oder weniger Metriken oder einer Metrik mit einer einzelnen Gruppe, indem er 1-3 Gruppen nach Werten enthält.

Im folgenden Beispiel sehen Sie zwei Umsatzmetriken: eine für den Erstumsatz und die andere für den wiederholten Umsatz, wobei die Trends im Zeitverlauf nach Monaten gefiltert werden:

![](../../assets/blobid6.png)

Spaltenberichte können gespeichert werden, indem der Bericht `Type` in `Chart` geändert und die Spaltenvisualisierungsoption ausgewählt wird:

![](../../assets/blobid7.png)

**Anforderungen:**

* Keines

## `Stacked Column`

`Stacked column` -Berichte sind fast identisch mit Spaltendiagrammen, allerdings werden ähnliche Spalten übereinander gestapelt, sodass die Gesamthöhe die Summe der Werte darstellt. Gestapelte Spalten lassen sich am besten mit einer begrenzten Anzahl von Metriken oder Gruppenbeiständen visualisieren.

Bei Verwendung derselben Berichtskonfiguration wie im obigen Abschnitt `Column` beschrieben würde ein Bericht mit zwei Umsatzmetriken (gefiltert zum ersten Mal und wiederholt) mit einer gestapelten Spaltenvisualisierung wie folgt aussehen:

![](../../assets/blobid8.png)

Auch hier ist es wichtig, dass das Kontrollkästchen `Multiple Y-Axes` deaktiviert wird, wenn mehrere Metriken mit der gestapelten Spaltenvisualisierung angezeigt werden.

Um einen Bericht als gestapelte Spalte zu speichern, setzen Sie den Bericht `Type` auf `Chart` und wählen Sie die Option `stacked column` aus:

![](../../assets/blobid9.png)

**Anforderungen:**

* Keines

## `Pie`

`Pie` -Diagramme eignen sich am besten für die Anzeige einer einzelnen Metrik mit einem oder mehreren Gruppenblöcken oder mehrerer Metriken ohne Gruppenbys. In beiden Fällen muss das Zeitintervall auf &quot;Keine&quot;gesetzt werden, damit Daten in einem Kreisdiagramm angezeigt werden. Im folgenden Beispiel ist eine Metrik für einzelne Bestellungen eine Gruppe nach Store-Namen, um die Aufschlüsselung der Bestellungen nach Store anzuzeigen:

![](../../assets/blobid10.png)

Um einen Bericht als Tortendiagramm zu speichern, setzen Sie den Bericht `Type` auf `Chart` und wählen Sie die Option `pie` wie unten gezeigt aus:

![](../../assets/blobid11.png)

**Anforderungen:**

* `Time interval`: `None`
* Sie haben eine der folgenden Möglichkeiten:
   * `Single metric with one or more group bys`
   * `Multiple metrics with no group bys`

## `Area`

`Area` -Diagramme sind fast mit gestapelten Spaltendiagrammen identisch, allerdings werden die Spalten kontinuierlich angezeigt. Ähnlich wie gestapelte Spalten werden Flächendiagramme am besten mit einer begrenzten Anzahl von Gruppenbys oder Metriken visualisiert.

Ausgehend vom gleichen Beispiel aus dem Abschnitt `stacked column` zeigt der unten stehende Bericht den ersten Umsatz mit der Visualisierung des Flächendiagramms im Vergleich zu Wiederholungsumsätzen:

![](../../assets/blobid12.png)

Um einen Bericht als Flächendiagramm zu speichern, passen Sie die `Type` -Einstellung auf `Chart` an und wählen Sie die Bereichsoption aus:

![](../../assets/blobid13.png)

**Anforderungen:**

* Keines

## `Funnel`

`Funnel` -Diagramme eignen sich ideal für die Visualisierung der Konversion über eine erwartete Ereignissequenz hinweg. Einige Beispiele sind die Analyse des potenziellen Umsatzes in Ihrem Verkaufstrichter vom Lead bis zum geschlossenen Geschäft oder die Messung des Rückgangs der Kunden zwischen ihren ersten und zweiten Bestellungen, zweiten und dritten Bestellungen usw. Nachstehend finden Sie ein Beispiel für Letztere:

![](../../assets/blobid4.png)

In einem Trichterbericht spiegelt sich der relative Wert eines bestimmten Schritts des Trichters in der Höhe des Schritts wider. Die Berichtskonfiguration bestimmt die Reihenfolge, in der die Schritte angezeigt werden. Es gibt zwei Möglichkeiten, einen Trichterbericht zu konfigurieren:

* `Single metric with one group by`: Die Reihenfolge der Schritte wird durch die Einstellung &quot;Oben/Unten anzeigen&quot;der Gruppe von bestimmt. Standardmäßig werden Trichterschritte in der Reihenfolge vom größten zum kleinsten Wert angezeigt. Sie können sie aber auch alphabetisch nach Name sortieren.

* `Multiple metrics with no group by`: Die Reihenfolge der Schritte wird durch die Reihenfolge bestimmt, in der die Metriken zum Bericht hinzugefügt werden.

Um einen Bericht als Trichterdiagramm zu speichern, passen Sie den Bericht `Type` auf `Chart` an und wählen Sie die entsprechende Visualisierung im ReportBuilder aus.

![](../../assets/blobid5.png)

**Anforderungen:**

* `Time interval`: `None`
* Sie haben eine der folgenden Möglichkeiten:
   * `Single metric with one group by`
   * `Multiple metrics with no group by`

## `Scatter plot`

Mit einem `scatter plot` wird die Beziehung einer Metrik mit zwei verschiedenen Variablen untersucht, sodass Sie Korrelationen und Ausreißer leicht identifizieren können. Diese Visualisierung sollte am besten nur bei numerischen Dimensionen verwendet werden. Versuchen Sie es mit der Metrik Bestellungen und den Dimensionen `Customer's lifetime number of coupons` und `Customer's lifetime revenue`, um zu sehen, wie die Nutzung des Coupons mit dem Umsatz verbunden ist. Sie können zwischen einem Streudiagramm mit und ohne Trendlinie wählen:

![](../../assets/scatter-plot-1.png)

![ohne trendline](../../assets/scatter-plot-2.png)

![](../../assets/scatter-plot-3.png)

![Mit trendline](../../assets/scatter-plot-4.png)

**Anforderungen:**

Option 1:

* Zwei `metrics`
* One `group by`
* `Time interval`: `None`

Option 2:

* Zwei `metrics`
* Nein `group by`
* `time interval` festlegen

## `Bubble` Diagramm

Ein `bubble` -Diagramm kann bis zu vier Datendimensionen anzeigen, wobei die `X` - und `Y` -Achsen die Position der Blasen angeben. Die Achse &quot;`Z`&quot; entspricht der Größe der Blasen. Durch Einschluss von zwei Gruppenbys können Sie den Blasen Farbe hinzufügen. Diese Art der Visualisierung eignet sich am besten, wenn Sie mehrere Datendimensionen in einem Diagramm darstellen möchten.

Die folgende Tabelle zeigt beispielsweise die Anzahl der Kunden (Punktgröße), gruppiert nach einer bestimmten Akquise-Quelle (Blasenfarbe) und Status (verschiedene Blasen in einer bestimmten Farbe), gezeichnet anhand des Gesamtumsatzes und der durchschnittlichen Bestellungen während der Lebensdauer.

![](../../assets/bubble-1.png)

Die folgende Tabelle zeigt die Anzahl der Kunden (Blasengröße), gruppiert nach Akquisequelle (Blasenfarbe) und Status (verschiedene Blasen in einer bestimmten Farbe), gezeichnet anhand des durchschnittlichen Lebenszeitwerts und des Gesamtumsatzes.

![](../../assets/bubble-2.png)

**Anforderungen an Punktdiagramme einzelner Serien:**

Option 1

* Drei `metrics`
* One `group by`
* `Time interval`: `None`

Option 2

* Drei `metrics`
* Nein `group by`
* `time interval` festlegen

**Anforderungen für ein mehrreihenweises Punktdiagramm:**

* Drei `metrics`
* Zwei `group by`
* `Time interval`: `None`

## `Heatmap`

Verwenden Sie `heatmaps` , um Hotspots in Ihren Daten zu visualisieren. Beispielsweise kann eine Heatmap angeben, wo Sie routinemäßig ein höheres Volumen erhalten. Die Visualisierung dieser Daten kann Ihnen dabei helfen, Ihre Lagerbestände anzupassen, um sicherzustellen, dass Sie die Nachfrage während dieser Spitzenfenster erfüllen.

Die folgende Heatmap zeigt die Bestellungen über mehrere Wochen nach Wochentag, Stunde für Tag.

![](../../assets/heat-map.png)<!--{: width="650"}-->

**Anforderungen:**

Option 1

* One `metric`
* Zwei `group by`
* `Time interval`: `None`

Option 2

* One `metric`
* One `group by`
* `time interval` festlegen
