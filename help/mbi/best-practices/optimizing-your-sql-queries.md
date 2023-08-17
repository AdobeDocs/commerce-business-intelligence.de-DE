---
title: Optimieren Ihrer SQL-Abfragen
description: Erfahren Sie, wie Sie Ihre SQL-Abfragen optimieren können.
exl-id: 2782c707-6a02-4e5d-bfbb-eff20659fbb2
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# SQL-Abfragen optimieren

Die [!DNL SQL Report Builder] ermöglicht es Ihnen, diese Abfragen jederzeit abzufragen und zu wiederholen. Dies ist nützlich, wenn Sie eine Abfrage ändern müssen, ohne auf die Fertigstellung eines Aktualisierungszyklus warten zu müssen, bevor Sie eine von Ihnen erstellte Spalte oder einen erstellten Bericht realisieren können.

Vor der Ausführung einer Abfrage [[!DNL Commerce Intelligence] Kostenschätzungen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/sql-queries-explain-cost-errors.html). Kosten berücksichtigt die Dauer und die Anzahl der Ressourcen, die zur Ausführung einer Abfrage erforderlich sind. Wenn diese Kosten als zu hoch betrachtet werden oder wenn die Anzahl der zurückgegebenen Zeilen [!DNL Commerce Intelligence] -Beschränkungen, schlägt die Abfrage fehl. Zur Abfrage Ihrer [Data Warehouse](../data-analyst/data-warehouse-mgr/tour-dwm.md), wodurch Sie die bestmöglichen Abfragen erstellen können, empfiehlt Adobe Folgendes.

## Verwenden von SELECT oder Auswählen aller Spalten

Die Auswahl aller Spalten ermöglicht keine zeitnahe, einfach auszuführende Abfrage. Abfragen, die `SELECT *` Die Ausführung kann etwas Zeit in Anspruch nehmen, insbesondere wenn Ihre Tabelle viele Spalten enthält.

Daher empfiehlt Adobe, die Verwendung von `SELECT *` soweit möglich und nur die benötigten Spalten einschließen:

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Select_all_1.png) | ![](../../mbi/assets/Select_all_2.png) |

{style="table-layout:auto"}

## Verwenden vollständiger Außenverbindungen

Externe Joins wählen die Gesamtheit der beiden Tabellen aus, die verbunden werden sollen, wodurch sich die Rechenkosten der Abfrage erhöhen. Das bedeutet, dass die Ausführung Ihrer Abfrage länger dauert und eher fehlschlägt, da es länger dauern kann, bis die Ergebnisse zurückgegeben werden.

Anstatt diesen Join-Typ zu verwenden, sollten Sie einen inneren oder linken Join verwenden. Inner-Joins geben Ergebnisse nur dann zurück, wenn eine Spaltenübereinstimmung zwischen Tabellen vorliegt (z. B. `order_id` ist in beiden Fällen vorhanden `customers` und `orders` Tabelle). Linke Joins geben alle Ergebnisse aus der linken (ersten) Tabelle zusammen mit den entsprechenden Ergebnissen in der rechten (zweiten) Tabelle zurück.

Sehen Sie sich an, wie Sie eine FULL OUTER JOIN-Abfrage umschreiben können:

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Full_Outer_Join_1.png) | ![](../../mbi/assets/Full_Outer_Join_2.png) |

{style="table-layout:auto"}

Diese Abfragen sind in jeder Hinsicht identisch, mit Ausnahme des von ihnen verwendeten JOIN-Typs.

## Verwenden mehrerer Joins

Sie können zwar mehrere Joins in Ihre Abfrage einschließen, aber beachten Sie, dass dies die Kosten der Abfrage erhöhen kann. Um die Kostenschwelle nicht zu erreichen, empfiehlt Adobe, nach Möglichkeit mehrere Joins zu vermeiden.

## Filter verwenden

Verwenden Sie nach Möglichkeit Filter. `WHERE` und `HAVING` -Klauseln filtern Ihre Ergebnisse und geben Ihnen nur die Daten, die Sie wirklich benötigen.

## Verwenden von Filtern in JOIN-Klauseln

Wenn Sie beim Ausführen eines Joins einen Filter verwenden, achten Sie darauf, diesen auf beide Tabellen des Joins anzuwenden. Selbst wenn sie redundant ist, reduziert dies die Rechenkosten der Abfrage und verkürzt die Ausführungszeit.

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Join_filters_1.png) | ![](../../mbi/assets/Join_filters_2.png) |

{style="table-layout:auto"}

## Benutzer verwenden

Erwägen Sie beim Schreiben von Abfragen die Verwendung der &quot;kostengünstigsten&quot; Operatoren. Jede Abfrage hat einen Rechenaufwand, der durch die Funktionen, Operatoren und Filter bestimmt wird, aus denen die Abfrage besteht. Manche Betreiber erfordern weniger Rechenaufwand, was sie billiger macht als andere.

Vergleichsoperatoren (>, &lt;, = usw.) sind die kostengünstigsten, gefolgt von [GEFÄLLT. ÄHNLICHE UND POSIX-Operatoren](https://www.postgresql.org/docs/9.5/functions-matching.html) die teuersten Betreiber sind.

## Verwenden von EXISTEN und IN

Verwenden `EXISTS` versus `IN` hängt von der Art der Ergebnisse ab, die Sie zurückgeben möchten. Wenn Sie nur an einem einzelnen Wert interessiert sind, verwenden Sie die `EXISTS` -Klausel anstelle von `IN`. `IN` wird mit Listen mit kommagetrennten Werten verwendet, was die berechneten Kosten der Abfrage erhöht.

Wann `IN` Abfragen ausgeführt werden, muss das System zuerst die Unterabfrage verarbeiten (die `IN` -Anweisung), dann die gesamte Abfrage basierend auf der in der `IN` -Anweisung. `EXISTS` ist viel effizienter, da die Abfrage nicht mehrmals ausgeführt werden muss - ein true/false -Wert wird zurückgegeben, während die in der Abfrage angegebene Beziehung überprüft wird.

Einfach ausgedrückt: Das System muss bei Verwendung von `EXISTS`.

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Exists_1.png) | ![](../../mbi/assets/Exists_2.png) |

{style="table-layout:auto"}

## REIHENFOLGE VERWENDEN VON

`ORDER BY` ist eine teure Funktion in SQL und kann die Kosten einer Abfrage erheblich erhöhen. Wenn Sie eine Fehlermeldung erhalten, dass die EXPLAIN-Kosten Ihrer Abfrage zu hoch sind, versuchen Sie, alle `ORDER BY`ist, falls erforderlich, aus Ihrer Abfrage entfernt.

Das heißt nicht, dass `ORDER BY` kann nicht verwendet werden - nur, dass es nur bei Bedarf verwendet werden sollte.

## GRUPPE NACH UND REIHENFOLGE

Es kann einige Situationen geben, in denen dieser Ansatz nicht mit dem übereinstimmt, was Sie versuchen zu tun. Die allgemeine Regel lautet: Wenn Sie eine `GROUP BY` und `ORDER BY`sollten Sie die Spalten in beiden Klauseln in derselben Reihenfolge ablegen. Beispiel:

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Group_by_2.png) | ![](../../mbi/assets/Group_by_1.png) |

{style="table-layout:auto"}

## Aufwischen

Die beste Möglichkeit, SQL zu schreiben - und dies effizient zu tun - ist durch Testen und Fehler. Um herauszufinden, was für Sie am besten geeignet ist, erstellen Sie einige Berichte nur mit dem SQL-Editor.
