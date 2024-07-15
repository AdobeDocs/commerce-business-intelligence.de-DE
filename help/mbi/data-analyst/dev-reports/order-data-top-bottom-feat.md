---
title: Sortieren von Daten mithilfe der Funktion "Oben/Unten anzeigen"
description: Erfahren Sie, wie Sie Ihre Daten mithilfe der Funktion "Oben/Unten anzeigen"sortieren können.
exl-id: d47119f4-cdc5-4fa7-a606-d4b8555a8843
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Sortieren von Daten mit der Funktion `Show Top/Bottom`

Sie können mehr in der `Visual Report Builder` tun, als Analysen mit diesem Trend im Zeitverlauf erstellen. Sie können beispielsweise einen Bericht erstellen, der anzeigt, wie wertvoll Ihre Akquise- und Marketingkanäle sind, aber Sie können auch einen Bericht erstellen, der nur die fünf leistungsstärksten Kanäle anzeigt. Auf ähnliche Weise können Sie Ihre Marketing-Bemühungen neu ausrichten, indem Sie einen Bericht erstellen, der anzeigt, aus welchen Bundesstaaten der größte Umsatz erzielt wird.

Diese Art der Sortierung und Sortierung von Daten kann in Berichten erfolgen, die sowohl ein `Group By` als auch ein `Time Interval of None` verwenden. Wenn beide Elemente in einem Bericht enthalten sind, wird oberhalb der Diagrammvorschau die Funktion `Show Top/Bottom` angezeigt. Mit dieser Funktion können Sie anhand der von Ihnen festgelegten Parameter die oberen (höchsten bis niedrigsten) und unteren (niedrigsten bis höchsten) Datenpunkte anzeigen.

![Funktion &quot;Oben/Unten anzeigen&quot;im Visual Report Builder.](../../assets/Show_Top_Bottom.png)

## Wie verwende ich das? {#how}

Klicken Sie auf &quot;**[!UICONTROL Show Top/Bottom link]**&quot;, um die Anzeige- und Sortierparameter festzulegen. Die Zahl im Textfeld kann entweder eine ganze Zahl (z. B. `5`) oder `ALL` sein. Als Nächstes können Sie den Bericht entweder nach Metrik ODER nach Gruppierung sortieren.

Wenn Sie z. B. die fünf Verweisquellen anzeigen möchten, die den meisten Umsatz gebracht haben, gehen Sie folgendermaßen vor:

1. Fügen Sie die Metrik `Revenue` zum Bericht hinzu.

1. Fügen Sie einen `Group By` hinzu, um die Metrik nach Verweisquelle zu segmentieren.

1. Setzen Sie `Time Interval` auf `None`.

1. Setzen Sie in den Einstellungen für `Show Top/Bottom` die Anzeige auf `5` , sodass nur die verweisenden Quellen mit den fünf höchsten Gesamtumsatzbeträgen in den Bericht aufgenommen werden.

>[!NOTE]
>
>Da der Bericht keinen &quot;`Time Interval`&quot;-Wert aufweist, können sich die Werte - in diesem Fall die fünf wichtigsten Verweisquellen - im Laufe der Zeit ändern. Wenn eine Verweisquelle eine andere in Bezug auf den Umsatz übersteigt, ändert sich die Reihenfolge, in der die Quellen angezeigt werden.

## Wie sieht es mit der Verwendung mehrerer Metriken aus? {#multiplemetrics}

Die Verwendung dieser Funktion wird kompliziert, wenn es sich bei hier um mehr als eine Metrik in einem Bericht handelt, da jede Metrik nur nach sich selbst oder nach einer der Gruppierungen sortiert werden kann.

Angenommen, Sie haben einen Bericht mit den Metriken `Revenue` und `Number of orders` erstellt, der nach Verweisquelle gruppiert ist. `Revenue` kann nur nach `Revenue` oder der Verweisquelle sortiert werden und `Number of orders` kann nur nach `Number of orders` oder der Verweisquelle sortiert werden.

Das bedeutet, dass Sie zwar die `Revenue` nur aus den wichtigsten `5` umsatzgenerierenden Verweisquellen anzeigen können, die Anzahl der Bestellungen jedoch nicht auch nach den wichtigsten `5` umsatzgenerierenden Verweisquellen anzeigen können. Einfach ausgedrückt: Wenn mehrere Metriken vorhanden sind, ist es am besten, jede Metrik nach Gruppierung zu sortieren.

Unten finden Sie ein Beispiel für ein Diagramm, das die Metrik `Revenue` nach sich selbst sortiert hat und nicht nach der Gruppierung. Wie Sie sehen können, wurde durch das Nichtsortieren der Metrik nach der Gruppierung ein seltsamer (und letztlich nicht hilfreicher) Bericht erstellt:

![Seltsame und nicht hilfreiche Berichtsergebnisse.](../../assets/strange-report-results.png)

Wenn Sie beide Metriken nach der Gruppierung sortiert hätten, sähe das Diagramm wie folgt aus:

![Sortieren Sie beide Metriken nach der Gruppierung.](../../assets/sort-metrics-by-grouping.png)

## Wie werden Werte standardmäßig sortiert? {#defaultsorting}

Wenn nur eine Metrik in einen Bericht mit dem Wert `Group by` und dem Wert `Time Interval` von `None` einbezogen wird, besteht die Standardreihenfolge in den `Visual Report Builder` darin, die höchsten Werte basierend auf der Metrik anzuzeigen. In diesem Fall ist die Funktion `Show Top/Bottom` möglicherweise nicht erforderlich, wenn dies Ihren Anforderungen entspricht.

In diesem Beispiel wird untersucht, wie viele Möglichkeiten Ihre Vertriebsmitarbeiter geschlossen haben. Diese Tabelle wird basierend auf der Metrik automatisch von oben nach unten sortiert, in diesem Fall `Won Opportunities`.

![ Sortieren nach der Metrik.](../../assets/Ordered_by_metric.png)

Wenn jedoch eine zweite Metrik hinzugefügt wird, besteht die Standardeinstellung darin, die oberste Metrik basierend auf der Gruppierung anzuordnen. Wenn Metriken und Gruppierungen hinzugefügt werden, basiert die Standardsortierung auf der ersten Gruppierung, der zweiten Gruppierung usw.

![Sortieren nach der Gruppierung.](../../assets/Ordered_by_grouping.png)

## Aufwischen {#wrapup}

Während einige grundlegende Funktionen hier behandelt werden, hat diese Funktion viele interessante Verwendungen.

Denken Sie an den vorherigen Umsatzrep und ein Opportunity-Beispiel. Wenn Sie die `Time Interval` entfernen, eine `Group By` anwenden und die Daten basierend auf der Gruppierung sortieren, konnten wir ein detailliertes Bild der Anzahl der Gewinner jedes Rep erhalten. Mithilfe der Funktion &quot;`Show Top/Bottom`&quot; können wir außerdem feststellen, wer die besten Darsteller sind.
