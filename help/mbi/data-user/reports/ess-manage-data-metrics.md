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

In [!DNL Commerce Intelligence], können Sie Metriken für [Grafiken erstellen](../../data-user/reports/ess-rpt-build-visual.md). Beispielsweise wird die Metrik `revenue` die Gesamtzahl der Bestellungen. Die Metrik `average customer revenue per order` ist das, was der durchschnittliche Kunde pro Bestellung ausgibt.

Bei Verwendung in Berichten können Metriken über einen bestimmten Zeitraum analysiert werden und [gefiltert oder segmentiert](../../best-practices/segment-filter.md) nach verschiedenen Kategorien. Erwägen Sie die Analyse des durchschnittlichen Kundenumsatzes nach Geschlecht - in diesem Fall: `average customer revenue per order` ist die Metrik und Geschlecht ist die Gruppierung.

## Definieren der Metrik {#define}

1. Klicken Sie zum Erstellen einer Metrik auf **[!UICONTROL Data** > **Metrics]**.

1. Klicken **[!UICONTROL Create New Metric]**.

1. Klicken Sie im Dropdown-Menü auf die Tabelle mit der nativen oder berechneten Spalte, die Sie für Ihre Metrik verwenden möchten.

1. Benennen Sie Ihre Metrik.

   Adobe empfiehlt einen Namen, der Ihnen auf einen Blick mitteilt, was die Metrik ist. Beispiel: `Average Order Revenue`.

1. Der nächste Schritt besteht darin, zu definieren, was Ihre Metrik bewirkt. Definieren Sie mithilfe der Dropdown-Menüs den Vorgang der Metrik, die `operation` und eine `date` Dimension:

   * Wählen Sie einen Vorgang aus:
      * `Count` - Dieser Vorgang zählt die Anzahl der Zeilen in einer Datentabelle
      * `Max` - Max gibt den Maximalwert einer bestimmten Datenspalte zurück
      * `Min` - Min gibt den Mindestwert einer bestimmten Datenspalte zurück
      * `Sum` - Dieser Vorgang summiert die Werte einer bestimmten Datenspalte
      * `Average` - Dieser Vorgang berechnet den Durchschnitt der Datenspaltenwerte
      * `Count Distinct Value` - Hiermit wird die eindeutige Anzahl von Werten in einer bestimmten Datenspalte gezählt.
      * `Median` - Dieser Vorgang berechnet den Median der Datenspaltenwerte
      * `First and Third Quartiles` - Diese Vorgänge berechnen die 25. bzw. 75. Perzentile der Datenspaltenwerte
      * `Tenth and Ninetieth Percentiles` - Diese Vorgänge berechnen die 10. bzw. 90. Perzentile der Datenspaltenwerte

   * Wählen Sie eine Spalte aus, für die der Vorgang ausgeführt werden soll. Wenn Sie beispielsweise den Gesamtumsatz ermitteln möchten, führen Sie einen Summenvorgang für die `order total` Spalte.

     Wenn Sie eine vorhandene Metrik bearbeiten, können Sie auch [die operationelle Tabelle der Metrik ändern](../../data-analyst/data-warehouse-mgr/change-metric-op-table.md) in diesem Abschnitt.

   * Wählen Sie eine Datumsdimension aus, die für die Trendverfolgung der Metrik verwendet werden kann. Beispiel, `order date`.

## Filter hinzufügen {#filters}

Die `Filter` -Bereich können Sie Filter erstellen oder einen [gespeicherter Filtersatz](../../data-user/reports/ess-manage-data-filters.md) zu Ihrer Metrik hinzufügen.

Für `average order revenue` -Metrik, würden Sie keine Testaufträge einbeziehen, die möglicherweise bei der Einrichtung Ihres Stores durchgeführt wurden. Dies würde uns ein ungenaues Ergebnis liefern. Kann einen Filtersatz anwenden, um diese Bestellungen aus dem Datensatz zu entfernen. Nach der Erstellung des Filters wird er auf alle Diagramme angewendet, die mit dieser Metrik erstellt wurden.

Die `Filter Logic` -Abschnitt enthält, können Sie weiter definieren, wie sich eine Metrik verhalten soll.

* &quot;\[`A`\] oder \[`B`&quot;\]&quot;erlaubt alle Daten, die den Filtern \[ entsprechen.`A`\] ODER \[`B`\]
* &quot;\[`A`\] und \[`B`\]&quot;erlaubt nur Daten, die beide Filter erfüllen \[`A`\] und \[`B`\]
* &quot;(\[`A`\] und \[`B`\]) ODER \[`C`\]&quot;erlaubt nur Daten, die beide Filter erfüllen \[`A`\] und \[`B`\] oder erfüllt Filter \[`C`\] allein

## Dimensionen hinzufügen {#dimensions}

Die [`Dimensions`](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) zeigt alle verfügbaren Datendimensionen zum Filtern oder Gruppieren an. Standardmäßig werden alle verfügbaren Datenspalten als Dimensionen aufgelistet. Wenn Sie im Beispiel Ihren Umsatz nach Verweisquelle segmentieren möchten, können Sie dies hier vornehmen.

Zusätzlich zur Auflistung aller verfügbaren Datenspalten als Dimensionen, [!DNL Commerce Intelligence] schätzt, in welchen Spalten gruppierbar sind. *So segmentieren oder gruppieren Sie Daten in Berichten*, müssen Spalten als gruppierbar markiert werden.

## Fertigstellung {#finish}

Zusätzlich zur Definition des Verhaltens Ihrer Metrik können Sie auch Berechtigungsebenen in der Variablen `User Rights` Abschnitt. while `Admin` -Benutzer Zugriff auf alle Metriken haben, müssen Sie die Benutzer angeben, die diese Metrik verwenden können, indem Sie das Kontrollkästchen neben der entsprechenden Gruppe aktivieren.

Wenn Sie eine vorhandene Metrik bearbeiten, können Sie eine Liste von Diagrammen (und deren Eigentümer) anzeigen, die diese Metrik im `Dependent Charts` Abschnitt.

Änderungen werden automatisch gespeichert und Ihre Metrik kann jetzt verwendet werden.
