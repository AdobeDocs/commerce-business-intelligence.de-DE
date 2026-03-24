---
title: Sortieren von Daten mit der Funktion „Nach oben/unten anzeigen“
description: Erfahren Sie, wie Sie Ihre Daten mit der Funktion „Nach oben/unten anzeigen“ sortieren können.
exl-id: d47119f4-cdc5-4fa7-a606-d4b8555a8843
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
TQID: https://experienceleague.adobe.com/EbxcX2kLo3aKcj1KkCZLfkRlCbQ5q00m9zf-afGv1Ic
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 665
ht-degree: 0%

---

# Sortieren von Daten mit `Show Top/Bottom` Funktion

Sie können in der `Visual Report Builder` mehr tun als Analysen zu erstellen, die sich im Laufe der Zeit entwickeln. Sie können beispielsweise einen Bericht erstellen, der den Wert Ihrer Akquise- und Marketing-Kanäle aufzeigt, aber auch einen Bericht, der nur die fünf leistungsstärksten Kanäle ausgibt. Ebenso können Sie Ihre Marketing-Maßnahmen neu ausrichten, indem Sie einen Bericht erstellen, der Ihnen zeigt, welche Bundesstaaten den meisten Umsatz generieren.

Diese Art der Sortierung und Sortierung von Daten kann in Berichten vorgenommen werden, die sowohl eine `Group By` als auch eine `Time Interval of None` verwenden. Wenn sich diese beiden Elemente in einem Bericht befinden, wird die `Show Top/Bottom` Funktion über der Diagrammvorschau angezeigt. Mit dieser Funktion können Sie die oberen (höchsten zu niedrigsten) und unteren (niedrigsten zu höchsten) Datenpunkte basierend auf den von Ihnen festgelegten Parametern anzeigen.

![Funktion „Oben/Unten“ in Visual Report Builder anzeigen.](../../assets/Show_Top_Bottom.png)

## Wie verwende ich das? {#how}

Klicken Sie auf die **[!UICONTROL Show Top/Bottom link]**, um die Anzeige- und Sortierparameter festzulegen. Die Zahl im Textfeld kann entweder eine Ganzzahl (wie `5`) oder `ALL` sein. Als Nächstes können Sie den Bericht entweder nach Metrik ODER nach Gruppierung sortieren.

Wenn Sie beispielsweise die fünf Empfehlungsquellen anzeigen möchten, die den höchsten Umsatz gebracht haben, tun Sie dies wie folgt:

1. Fügen Sie die `Revenue` Metrik zum Bericht hinzu.

1. Fügen Sie der Metrik eine `Group By` nach Empfehlungsquelle hinzu.

1. Legen Sie `Time Interval` auf `None` fest.

1. Legen Sie in den `Show Top/Bottom` Einstellungen die Anzeige auf `5` fest, sodass nur die Empfehlungsquellen mit den fünf größten Gesamtumsatzbeträgen im Bericht enthalten sind.

>[!NOTE]
>
>Da der Bericht keine `Time Interval` hat, können sich die Werte - in diesem Fall die fünf häufigsten Empfehlungsquellen - im Laufe der Zeit ändern. Wenn eine Empfehlungsquelle eine andere hinsichtlich des Umsatzes übertrifft, ändert sich die Reihenfolge, in der die Quellen angezeigt werden.

## Wie sieht es mit der Verwendung mehrerer Metriken aus? {#multiplemetrics}

Die Verwendung dieser Funktion wird kompliziert, wenn ein Bericht mehr als eine Metrik enthält, da jede Metrik nur für sich selbst oder nach einer der Gruppierungen sortiert werden kann.

Angenommen, Sie haben einen Bericht mit den Metriken `Revenue` und `Number of orders` erstellt, gruppiert nach Empfehlungsquelle. `Revenue` können nur nach `Revenue` oder Verweisquelle sortiert werden und `Number of orders` nur nach `Number of orders` oder Verweisquelle.

Das bedeutet, dass Sie zwar nur die `Revenue` aus den `5` umsatzgenerierenden Verweisquellen anzeigen können, aber nicht die Anzahl der Bestellungen auch nach den `5` umsatzgenerierenden Verweisquellen anzeigen können. Einfach ausgedrückt: Wenn mehrere Metriken vorhanden sind, ist es am besten, jede Metrik nach Gruppierung zu sortieren.

Nachfolgend finden Sie ein Beispiel für ein Diagramm, in dem die `Revenue`-Metrik nach sich selbst und nicht nach der Gruppierung sortiert wird. Wie zu sehen ist, wird die Metrik nicht nach der Gruppierung sortiert, sondern ein seltsamer (und letztendlich nicht hilfreicher) Bericht erstellt:

![Seltsame und nicht hilfreiche Berichtsergebnisse.](../../assets/strange-report-results.png)

Wenn Sie beide Metriken nach Gruppierung sortiert hätten, würde das Diagramm wie folgt aussehen:

![Beide Metriken nach Gruppierung sortieren.](../../assets/sort-metrics-by-grouping.png)

## Wie werden Werte standardmäßig sortiert? {#defaultsorting}

Wenn in einem Bericht mit einer `Group by` und einer `Time Interval` von `None` nur eine Metrik enthalten ist, besteht die Standardreihenfolge in der `Visual Report Builder` darin, die höchsten Werte basierend auf der Metrik anzuzeigen. In diesem Fall ist die `Show Top/Bottom` möglicherweise nicht erforderlich, wenn dies Ihren Anforderungen entspricht.

In diesem Beispiel wird gezeigt, wie viele Opportunities Ihre Vertriebsmitarbeiter geschlossen haben. Diese Tabelle wird anhand der Metrik automatisch vom höchsten zum niedrigsten Wert sortiert, in diesem Fall `Won Opportunities`.

![Sortieren nach Metrik.](../../assets/Ordered_by_metric.png)

Wenn jedoch eine zweite Metrik hinzugefügt wird, besteht die Standardeinstellung darin, die Spitze basierend auf der Gruppierung zu sortieren. Beim Hinzufügen von Metriken und Gruppierungen basiert die Standardsortierung auf der ersten Gruppierung, der zweiten Gruppierung usw.

![Sortieren nach Gruppierung.](../../assets/Ordered_by_grouping.png)

## Verpackung {#wrapup}

Während einige grundlegende Funktionen hier behandelt werden, hat diese Funktion viele interessante Verwendungen.

Denken Sie an das Beispiel des vorherigen Vertriebsmitarbeiters und an die Verkaufschancen. Durch das Entfernen der `Time Interval`, das Anwenden einer `Group By` und das Sortieren der Daten basierend auf der Gruppierung konnten wir uns ein detailliertes Bild über die Anzahl der gewonnenen Opportunitys jedes Partners verschaffen. Außerdem können wir mithilfe der `Show Top/Bottom`-Funktion herausfinden, wer die besten Ergebnisse erzielt.
