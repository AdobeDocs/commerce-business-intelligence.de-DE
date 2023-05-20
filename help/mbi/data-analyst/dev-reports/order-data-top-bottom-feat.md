---
title: Sortieren von Daten mithilfe der Funktion "Oben/Unten anzeigen"
description: Erfahren Sie, wie Sie Ihre Daten mithilfe der Funktion "Oben/Unten anzeigen"sortieren können.
exl-id: d47119f4-cdc5-4fa7-a606-d4b8555a8843
source-git-commit: 3bf4829543579d939d959753eb3017364c6465bd
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Sortieren von Daten mithilfe von `Show Top/Bottom` Funktion

Weitere Informationen finden Sie im Abschnitt `Visual Report Builder` analysieren, die diesen Trend im Laufe der Zeit analysieren. Sie können beispielsweise einen Bericht erstellen, der anzeigt, wie wertvoll Ihre Akquise- und Marketingkanäle sind, aber Sie können auch einen Bericht erstellen, der nur die fünf leistungsstärksten Kanäle anzeigt. Auf ähnliche Weise können Sie Ihre Marketing-Bemühungen neu ausrichten, indem Sie einen Bericht erstellen, der anzeigt, aus welchen Bundesstaaten der größte Umsatz erzielt wird.

Diese Art der Sortierung und Sortierung von Daten kann in Berichten vorgenommen werden, die sowohl eine `Group By` und `Time Interval of None`. Wenn beide Elemente in einem Bericht enthalten sind, wird die `Show Top/Bottom` oberhalb der Diagrammvorschau angezeigt. Mit dieser Funktion können Sie anhand der von Ihnen festgelegten Parameter die oberen (höchsten bis niedrigsten) und unteren (niedrigsten bis höchsten) Datenpunkte anzeigen.

![Die Funktion &quot;Oben/Unten&quot;im Visual Report Builder anzeigen.](../../assets/Show_Top_Bottom.png)

## Wie verwende ich das? {#how}

Klicken Sie auf **[!UICONTROL Show Top/Bottom link]** , um die Anzeige- und Sortierparameter festzulegen. Die Zahl im Textfeld kann entweder eine ganze Zahl sein (z. B. `5`) oder `ALL`. Als Nächstes können Sie den Bericht entweder nach Metrik ODER nach Gruppierung sortieren.

Wenn Sie z. B. die fünf Verweisquellen anzeigen möchten, die den meisten Umsatz gebracht haben, gehen Sie folgendermaßen vor:

1. Fügen Sie die `Revenue` zum Bericht hinzu.

1. Hinzufügen einer `Group By` , um die Metrik nach Verweisquelle zu segmentieren.

1. Satz `Time Interval` nach `None`.

1. Im `Show Top/Bottom` -Einstellungen festlegen, setzen Sie die Anzeige auf `5` sodass nur die Verweisquellen mit den fünf höchsten Gesamtumsatzbeträgen in den Bericht aufgenommen werden.

>[!NOTE]
>
>Da der Bericht keine `Time Interval`, können sich die Werte - in diesem Fall die fünf wichtigsten Verweisquellen - im Laufe der Zeit ändern. Wenn eine Verweisquelle eine andere in Bezug auf den Umsatz übersteigt, ändert sich die Reihenfolge, in der die Quellen angezeigt werden.

## Wie sieht es mit der Verwendung mehrerer Metriken aus? {#multiplemetrics}

Die Verwendung dieser Funktion wird kompliziert, wenn es sich bei hier um mehr als eine Metrik in einem Bericht handelt, da jede Metrik nur nach sich selbst oder nach einer der Gruppierungen sortiert werden kann.

Angenommen, Sie haben einen Bericht mit den beiden Variablen `Revenue` und `Number of orders` Metriken, gruppiert nach Verweisquelle. `Revenue` kann nur sortiert werden nach `Revenue` oder Verweisquelle und `Number of orders` kann nur sortiert werden nach `Number of orders` oder Verweisquelle.

Das bedeutet, dass während der `Revenue` von nur oben `5` Verweisquellen, die Umsatz generieren, können die Anzahl der Bestellungen nicht auch nach oben anzeigen `5` Verweisquellen, die Umsatz generieren. Einfach ausgedrückt: Wenn mehrere Metriken vorhanden sind, sollten Sie am besten jede Metrik nach der Gruppierung sortieren.

Nachfolgend finden Sie ein Beispiel für ein Diagramm, das die `Revenue` -Metrik selbst anstatt durch die Gruppierung. Wie Sie sehen können, wurde durch das Nichtsortieren der Metrik nach der Gruppierung ein seltsamer (und letztlich nicht hilfreicher) Bericht erstellt:

![Seltsame und nicht hilfreiche Berichtsergebnisse.](../../assets/strange-report-results.png)

Wenn Sie beide Metriken nach der Gruppierung sortiert hätten, sähe das Diagramm wie folgt aus:

![Sortieren der beiden Metriken nach Gruppierung.](../../assets/sort-metrics-by-grouping.png)

## Wie werden Werte standardmäßig sortiert? {#defaultsorting}

Wenn nur eine Metrik in einen Bericht mit einer `Group by` und `Time Interval` von `None`, die Standardreihenfolge im `Visual Report Builder` zeigt die höchsten Werte basierend auf der Metrik an. In dieser Instanz wird die `Show Top/Bottom` -Funktion möglicherweise nicht erforderlich, wenn dies Ihren Anforderungen entspricht.

In diesem Beispiel wird untersucht, wie viele Möglichkeiten Ihre Vertriebsmitarbeiter geschlossen haben. Diese Tabelle wird basierend auf der Metrik automatisch von oben nach unten sortiert. In diesem Fall `Won Opportunities`.

![Reihenfolge nach Metrik.](../../assets/Ordered_by_metric.png)

Wenn jedoch eine zweite Metrik hinzugefügt wird, besteht die Standardeinstellung darin, die obere anhand der Gruppierung anzuordnen. Wenn Metriken und Gruppierungen hinzugefügt werden, basiert die Standardsortierung auf der ersten Gruppierung, der zweiten Gruppierung usw.

![Sortieren nach Gruppierung.](../../assets/Ordered_by_grouping.png)

## Aufbrechen {#wrapup}

Während einige grundlegende Funktionen hier behandelt werden, hat diese Funktion viele interessante Verwendungen.

Denken Sie an den vorherigen Umsatzrep und ein Opportunity-Beispiel. Entfernen der `Time Interval`, Anwendung einer `Group By`und die Sortierung der Daten anhand der Gruppierung ermöglichte es uns, ein detailliertes Bild über die Anzahl der von jedem Kontakt gewann Gelegenheiten zu erhalten. Verwenden Sie außerdem die `Show Top/Bottom` lassen Sie uns herausfinden, wer die besten Auftritte hat.
