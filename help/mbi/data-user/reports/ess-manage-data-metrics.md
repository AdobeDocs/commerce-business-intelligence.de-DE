---
title: Metriken erstellen
description: Erfahren Sie, wie Sie Metriken zum Erstellen von Diagrammen verwenden.
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

Eine Metrik ist eine Messung. In SQL- und Datenbankstrukturen ist eine Metrik wie eine gespeicherte Abfrage über einen Variablenzeitraum.

In [!DNL Commerce Intelligence] können Sie Metriken verwenden, um [Diagramme zu erstellen](../../data-user/reports/ess-rpt-build-visual.md). Die Metrik `revenue` ist beispielsweise die Gesamtzahl der Bestellungen. Die Metrik `average customer revenue per order` ist, was der durchschnittliche Kunde pro Bestellung ausgibt.

Wenn Metriken in Berichten verwendet werden, können sie über einen bestimmten Zeitraum analysiert und [gefiltert oder segmentiert](../../best-practices/segment-filter.md) nach verschiedenen Kategorien gruppiert werden. Ziehen Sie die Analyse des durchschnittlichen Kundenumsatzes in Betracht, gruppiert nach Geschlecht - in diesem Fall ist `average customer revenue per order` die Metrik und das Geschlecht die Gruppierung.

## Definieren der Metrik {#define}

1. Um eine Metrik zu erstellen, klicken Sie auf **[!UICONTROL Data** > **Metrics]**.

1. Klicken Sie auf **[!UICONTROL Create New Metric]**.

1. Klicken Sie im Dropdown-Menü auf die Tabelle, die die native oder berechnete Spalte enthält, die Sie für Ihre Metrik verwenden möchten.

1. Benennen Sie Ihre Metrik.

   Adobe empfiehlt einen Namen, der Ihnen auf einen Blick zeigt, was die Metrik ist. Beispiel: `Average Order Revenue`.

1. Der nächste Schritt besteht darin zu definieren, was Ihre Metrik tut. Definieren Sie mithilfe der Dropdown-Menüs den Vorgang der Metrik, die Spalte `operation` und eine `date` Dimension:

   * Vorgang auswählen:
      * `Count` - Dieser Vorgang zählt die Anzahl der Zeilen in einer Datentabelle
      * `Max` - Max. Gibt den Höchstwert einer bestimmten Datenspalte zurück.
      * `Min` - Min. gibt den Mindestwert einer bestimmten Datenspalte zurück
      * `Sum` - Dieser Vorgang addiert die Werte einer bestimmten Datenspalte
      * `Average` - Dieser Vorgang berechnet den Durchschnitt der Datenspaltenwerte
      * `Count Distinct Value` - Dies zählt die eindeutige Anzahl der Werte in einer bestimmten Datenspalte
      * `Median` - Dieser Vorgang berechnet den Median der Datenspaltenwerte
      * `First and Third Quartiles` - Mit diesen Vorgängen wird das 25. bzw. 75. Perzentil der Datenspaltenwerte berechnet
      * `Tenth and Ninetieth Percentiles` - Diese Vorgänge berechnen das 10. bzw. 90. Perzentil der Datenspaltenwerte

   * Spalte auswählen, für die der Vorgang ausgeführt werden soll. Wenn Sie beispielsweise den Gesamtumsatz ermitteln möchten, führen Sie einen Summenvorgang für die Spalte `order total` aus.

     Wenn Sie eine vorhandene Metrik bearbeiten, können Sie auch [die Operationstabelle der Metrik ändern](../../data-analyst/data-warehouse-mgr/change-metric-op-table.md) in diesem Abschnitt.

   * Wählen Sie eine Datumsdimension aus, die zur Entwicklung der Metrik verwendet werden kann. Beispiel: `order date`.

## Filter hinzufügen {#filters}

Im Abschnitt `Filter` können Sie einen Filter erstellen oder einen [gespeicherten Filtersatz](../../data-user/reports/ess-manage-data-filters.md) auf Ihre Metrik anwenden.

Für die `average order revenue`-Metrik sollten Sie keine Testaufträge einbeziehen, die bei der Einrichtung Ihres Stores ausgeführt wurden - dies würde uns ein ungenaues Ergebnis liefern. Sie können einen Filtersatz anwenden, um diese Bestellungen aus dem Datensatz zu entfernen. Nachdem der Filter erstellt wurde, gilt er für alle Diagramme, die mit dieser Metrik erstellt wurden.

Im `Filter Logic` Abschnitt können Sie genauer definieren, wie sich eine Metrik verhalten soll.

* &quot;\[`A`\] oder \[`B`\]&quot; lässt alle Daten zu, die den Filtern \[`A`\] ODER \[`B`\] entsprechen
* &quot;\[`A`\] und \[`B`\]&quot; erlaubt nur Daten, die beide Filter \[`A`\] und \[`B`\] erfüllen
* „(\[`A`\] und \[`B`\]) ODER \[`C`\]&quot; lässt nur Daten zu, die entweder beide Filter \[`A`\] und \[`B`\] erfüllen oder den Filter \[`C`\] allein erfüllen

## Hinzufügen von Dimensionen {#dimensions}

Im Abschnitt [`Dimensions`](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) werden alle verfügbaren Datendimensionen zum Filtern oder Gruppieren angezeigt. Standardmäßig werden alle verfügbaren Datenspalten als Dimensionen aufgeführt. Wenn Sie Ihren Umsatz nach Empfehlungsquelle segmentieren möchten, können Sie dies hier tun.

Zusätzlich zur Auflistung aller verfügbaren Datenspalten als Dimensionen schätzt [!DNL Commerce Intelligence], an welchen Spalten gruppiert werden kann. *Um Daten in Berichten zu segmentieren oder zu gruppieren* müssen Spalten als gruppierbar markiert werden.

## Fertigstellen {#finish}

Sie können nicht nur festlegen, wie sich Ihre Metrik verhält, sondern auch im Abschnitt `User Rights` Berechtigungsebenen festlegen. Obwohl `Admin` Benutzer Zugriff auf alle Metriken haben, müssen Sie die Benutzer angeben, die diese Metrik verwenden können, indem Sie das Kontrollkästchen neben der entsprechenden Gruppe aktivieren.

Wenn Sie eine vorhandene Metrik bearbeiten, können Sie eine Liste der Diagramme (und deren Eigentümer), die diese Metrik verwenden, im Abschnitt `Dependent Charts` anzeigen.

Änderungen werden automatisch gespeichert und die Metrik ist jetzt einsatzbereit.
