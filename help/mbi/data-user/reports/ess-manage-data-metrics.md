---
title: Metriken erstellen
description: Erfahren Sie, wie Sie mit Metriken Diagramme erstellen können.
exl-id: d4c25546-3c51-4d32-b9d8-c424ec103be5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Metriken erstellen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Eine Metrik ist eine Messung. In SQL- und Datenbankstrukturen entspricht eine Metrik einer gespeicherten Abfrage über einen Variablenzeitraum.

In [!DNL Commerce Intelligence] können Sie Metriken verwenden, um [Diagramme zu erstellen](../../data-user/reports/ess-rpt-build-visual.md). Die Metrik &quot;`revenue`&quot;entspricht beispielsweise der Gesamtanzahl der Bestellungen. Die Metrik &quot;`average customer revenue per order`&quot; ist der durchschnittliche Kundenaufwand pro Bestellung.

Bei Verwendung in Berichten können Metriken über einen bestimmten Zeitraum analysiert und [gefiltert oder segmentiert](../../best-practices/segment-filter.md) nach verschiedenen Kategorien gefiltert werden. Erwägen Sie die Analyse des durchschnittlichen Kundenumsatzes, gruppiert nach Geschlecht - in diesem Fall ist `average customer revenue per order` die Metrik und Geschlecht die Gruppierung.

## Definieren der Metrik {#define}

1. Um eine Metrik zu erstellen, klicken Sie auf **[!UICONTROL Data** > **Metrics]**.

1. Klicken Sie auf **[!UICONTROL Create New Metric]**.

1. Klicken Sie im Dropdown-Menü auf die Tabelle mit der nativen oder berechneten Spalte, die Sie für Ihre Metrik verwenden möchten.

1. Benennen Sie Ihre Metrik.

   Adobe empfiehlt einen Namen, der Ihnen auf einen Blick mitteilt, was die Metrik ist. Beispiel: `Average Order Revenue`.

1. Der nächste Schritt besteht darin, zu definieren, was Ihre Metrik bewirkt. Definieren Sie mithilfe der Dropdown-Menüs den Vorgang der Metrik, die Spalte `operation` und eine Dimension `date`:

   * Wählen Sie einen Vorgang aus:
      * `Count` - Dieser Vorgang zählt die Anzahl der Zeilen in einer Datentabelle
      * `Max` - Max. gibt den Maximalwert einer bestimmten Datenspalte zurück
      * `Min` - Min. gibt den Mindestwert einer bestimmten Datenspalte zurück
      * `Sum` - Dieser Vorgang summiert die Werte einer bestimmten Datenspalte
      * `Average` - Dieser Vorgang berechnet den Durchschnitt der Datenspaltenwerte
      * `Count Distinct Value` - Zählt die eindeutige Anzahl der Werte in einer bestimmten Datenspalte
      * `Median` - Dieser Vorgang berechnet den Median der Datenspaltenwerte
      * `First and Third Quartiles` - Diese Vorgänge berechnen die 25. und 75. Perzentile der Datenspaltenwerte.
      * `Tenth and Ninetieth Percentiles` - Diese Vorgänge berechnen die 10. und 90. Perzentile der Datenspaltenwerte.

   * Wählen Sie eine Spalte aus, für die der Vorgang ausgeführt werden soll. Wenn Sie beispielsweise den Gesamtumsatz ermitteln möchten, führen Sie einen Summenvorgang für die Spalte `order total` durch.

     Wenn Sie eine vorhandene Metrik bearbeiten, können Sie in diesem Abschnitt auch die Arbeitstabelle der Metrik ](../../data-analyst/data-warehouse-mgr/change-metric-op-table.md) ändern.[

   * Wählen Sie eine Datumsdimension aus, die für die Trendverfolgung der Metrik verwendet werden kann. Beispiel: `order date`.

## Filter hinzufügen {#filters}

Im Abschnitt `Filter` können Sie einen Filter erstellen oder einen [gespeicherten Filtersatz](../../data-user/reports/ess-manage-data-filters.md) auf Ihre Metrik anwenden.

Für die Metrik `average order revenue` möchten Sie keine Testaufträge einbeziehen, die möglicherweise beim Einrichten Ihres Stores ausgeführt wurden. Dies würde uns ein ungenaues Ergebnis liefern. Kann einen Filtersatz anwenden, um diese Bestellungen aus dem Datensatz zu entfernen. Nach der Erstellung des Filters wird er auf alle Diagramme angewendet, die mit dieser Metrik erstellt wurden.

Im Abschnitt `Filter Logic` können Sie weiter definieren, wie sich eine Metrik verhalten soll.

* &quot;\[`A`\] oder \[`B`\]&quot;ermöglicht alle Daten, die den Filtern \[`A`\] ODER \[`B`\] entsprechen.
* &quot;\[`A`\] und \[`B`\]&quot;erlauben nur Daten, die beide Filter \[`A`\] und \[`B`\] erfüllen.
* &quot;(\[`A`\] und \[`B`\]) ODER \[`C`\]&quot;erlaubt nur Daten, die entweder beide Filter \[`A`\] und \[`B`\] erfüllen oder Filter \[`C`\] allein erfüllen

## Dimensionen hinzufügen {#dimensions}

Der Abschnitt [`Dimensions`](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) enthält alle verfügbaren Datendimensionen zum Filtern oder Gruppieren. Standardmäßig werden alle verfügbaren Datenspalten als Dimensionen aufgelistet. Wenn Sie im Beispiel Ihren Umsatz nach Verweisquelle segmentieren möchten, können Sie dies hier vornehmen.

Neben der Auflistung aller verfügbaren Datenspalten als Dimensionen wird mit [!DNL Commerce Intelligence] ermittelt, in welchen Spalten gruppierbar sind. *Um Daten in Berichten zu segmentieren oder zu gruppieren*, müssen Spalten als gruppierbar markiert werden.

## Fertigstellung {#finish}

Zusätzlich zur Definition des Verhaltens Ihrer Metrik können Sie auch Berechtigungsebenen im Abschnitt `User Rights` festlegen. Während `Admin` -Benutzer Zugriff auf alle Metriken haben, müssen Sie die Benutzer angeben, die diese Metrik verwenden können, indem Sie das Kontrollkästchen neben der entsprechenden Gruppe aktivieren.

Wenn Sie eine vorhandene Metrik bearbeiten, können Sie eine Liste von Diagrammen (und deren Eigentümer) anzeigen, die diese Metrik im Abschnitt `Dependent Charts` verwenden.

Änderungen werden automatisch gespeichert und Ihre Metrik kann jetzt verwendet werden.
