---
title: Optimieren Ihrer SQL-Abfragen
description: Erfahren Sie, wie Sie Ihre SQL-Abfragen optimieren können.
exl-id: 2782c707-6a02-4e5d-bfbb-eff20659fbb2
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# SQL-Abfragen optimieren

Der SQL-Report Builder ermöglicht es Ihnen, diese Abfragen jederzeit abzufragen und zu wiederholen. Dies ist nützlich, wenn Sie eine Abfrage ändern müssen, ohne warten zu müssen, bis ein Aktualisierungszyklus abgeschlossen ist, bevor Sie eine von Ihnen erstellte Spalte oder einen erstellten Bericht realisieren können, die aktualisiert werden muss.

Vor der Ausführung einer Abfrage [[!DNL MBI] Kostenschätzungen](https://support.magento.com/hc/en-us/articles/360016730391). Die Kosten berücksichtigen die Zeitdauer und die Anzahl der Ressourcen, die zur Ausführung einer Abfrage erforderlich sind. Wenn diese Kosten als zu hoch gelten oder die Anzahl der zurückgegebenen Zeilen unsere Grenzwerte überschreitet, wird die Abfrage nicht ausgeführt. Wir haben eine Liste mit Empfehlungen für die Abfrage Ihres Data Warehouse zusammengestellt, um sicherzustellen, dass Sie die bestmöglichen rationalisierten Abfragen schreiben.

## Verwenden von SELECT oder Auswählen aller Spalten

Die Auswahl aller Spalten ermöglicht keine zeitnahe, einfach auszuführende Abfrage. Abfragen, die `SELECT *` Die Ausführung kann etwas Zeit in Anspruch nehmen, insbesondere wenn Ihre Tabelle eine große Anzahl von Spalten aufweist.

Aus diesem Grund wird empfohlen, die Verwendung von `SELECT *` soweit möglich und nur die benötigten Spalten einschließen:

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Select_all_1.png) | ![](../../mbi/assets/Select_all_2.png) |

{style=&quot;table-layout:auto&quot;}

## Verwenden vollständiger Außenverbindungen

Externe Joins wählen die Gesamtheit der beiden Tabellen aus, die verbunden werden sollen, wodurch sich die Rechenkosten der Abfrage erhöhen. Das bedeutet, dass die Ausführung der Abfrage länger dauert und wahrscheinlich eher fehlschlägt, da es länger dauern kann, bis die Ergebnisse zurückgegeben werden.

Anstatt diesen Join-Typ zu verwenden, sollten Sie einen inneren oder linken Join verwenden. Inner-Joins geben nur Ergebnisse zurück, bei denen es eine Spaltenübereinstimmung zwischen Tabellen gibt (z. B. `order_id` ist in beiden Fällen vorhanden: `customers` und `orders` Tabelle); Die linken Joins geben alle Ergebnisse der linken (ersten) Tabelle zusammen mit den entsprechenden Ergebnissen in der rechten (zweiten) Tabelle zurück.

Sehen Sie sich an, wie wir eine FULL OUTER JOIN-Abfrage umschreiben können:

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Full_Outer_Join_1.png) | ![](../../mbi/assets/Full_Outer_Join_2.png) |

{style=&quot;table-layout:auto&quot;}

Wie Sie sehen können, sind diese Abfragen in jeder Hinsicht identisch, mit Ausnahme des von ihnen verwendeten JOIN-Typs.

## Verwenden mehrerer Joins

Sie können zwar mehrere Joins in Ihre Abfrage einschließen, aber beachten Sie, dass dies die Kosten der Abfrage erhöhen kann. Um die Kostenschwelle nicht zu erreichen, empfehlen wir, nach Möglichkeit mehrere Joins zu vermeiden.

## Verwenden von Filtern

Verwenden Sie nach Möglichkeit Filter. `WHERE` und `HAVING` -Klauseln filtern Ihre Ergebnisse und geben Ihnen nur die Daten, die Sie wirklich benötigen.

## Verwenden von Filtern in JOIN-Klauseln

Wenn Sie beim Ausführen eines Joins einen Filter verwenden, achten Sie darauf, diesen auf beide Tabellen des Joins anzuwenden. Selbst wenn sie redundant ist, werden dadurch die Rechenkosten der Abfrage reduziert und die Ausführungszeit verkürzt.

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Join_filters_1.png) | ![](../../mbi/assets/Join_filters_2.png) |

{style=&quot;table-layout:auto&quot;}

## Verwenden von Operatoren

Erwägen Sie beim Schreiben von Abfragen die Verwendung der &quot;kostengünstigsten&quot; Operatoren. Jede Abfrage hat einen Rechenaufwand, der durch die Funktionen, Operatoren und Filter bestimmt wird, aus denen die Abfrage besteht. Manche Betreiber erfordern weniger Rechenaufwand, was sie billiger macht als andere.

Vergleichsoperatoren (>, &lt;, = usw.) sind die kostengünstigsten, gefolgt von [GEFÄLLT. ÄHNLICHE UND POSIX-Operatoren](https://www.postgresql.org/docs/9.5/functions-matching.html) die teuersten Betreiber sind.

## Verwenden von EXISTEN und IN

Verwenden `EXISTS` versus `IN` hängt vom Typ der Ergebnisse ab, die Sie zurückgeben möchten. Wenn Sie nur an einem einzelnen Wert interessiert sind, verwenden Sie die `EXISTS` -Klausel anstelle von `IN`. `IN` wird zusammen mit Listen mit kommagetrennten Werten verwendet, was die Rechenkosten der Abfrage erhöht.

Wann `IN` Abfragen ausgeführt werden, muss das System zuerst die Unterabfrage verarbeiten (die `IN` -Anweisung), dann die gesamte Abfrage basierend auf der in der `IN` -Anweisung. `EXISTS` ist viel effizienter, da die Abfrage nicht mehrmals ausgeführt werden muss - ein true/false -Wert wird zurückgegeben, während die in der Abfrage angegebene Beziehung überprüft wird.

Einfach ausgedrückt: Das System muss bei Verwendung von `EXISTS`.

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Exists_1.png) | ![](../../mbi/assets/Exists_2.png) |

{style=&quot;table-layout:auto&quot;}

## REIHENFOLGE VERWENDEN VON

`ORDER BY` ist eine teure Funktion in SQL und kann die Kosten einer Abfrage erheblich erhöhen. Wenn Sie eine Fehlermeldung erhalten, dass die EXPLAIN-Kosten Ihrer Abfrage zu hoch sind, versuchen Sie, alle `ORDER BY`aus Ihrer Abfrage zurückgegeben werden, es sei denn, dies ist absolut erforderlich.

Das heißt nicht, dass `ORDER BY` kann nicht verwendet werden - nur dass es nur bei Bedarf verwendet werden sollte.

## GRUPPE NACH UND REIHENFOLGE

Es kann zwar einige Situationen geben, in denen dieser Ansatz nicht mit dem übereinstimmt, was Sie versuchen zu tun, die allgemeine Regel ist jedoch, dass bei Verwendung einer `GROUP BY` und `ORDER BY`sollten Sie die Spalten in beiden Klauseln in derselben Reihenfolge ablegen. Beispiel:

| **Stattdessen ...** | **Probier das!** |
|-----|-----|
| ![](../../mbi/assets/Group_by_2.png) | ![](../../mbi/assets/Group_by_1.png) |

{style=&quot;table-layout:auto&quot;}

## Aufbrechen

Die beste Möglichkeit, SQL zu schreiben - und dies effizient zu tun - ist durch Testen und Fehler. Um herauszufinden, was für Sie am besten geeignet ist, erstellen Sie einige Berichte nur mit dem SQL-Editor.
