---
title: Spezielle Filteroperatoren
description: Erfahren Sie mehr über einige spezielle Operatoren, die bei der Erstellung eines Berichts oder einer Metrik in Filtern verwendet werden.
exl-id: 12837490-b9ca-4040-bb71-8988b5dde485
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Filteroptionen

Dieses Thema behandelt einige spezielle `operators` verwendet in `filters` when [Berichterstellung](../../tutorials/using-visual-report-builder.md){: target=&quot;_blank&quot;} oder [Erstellen einer Metrik](../../data-user/reports/ess-manage-data-metrics.md){: target=&quot;_blank&quot;}.

## `Filter Operators`

* `LIKE` für Musterzuordnung. Dies muss mit den Platzhalterzeichen % (für einen Platzhalter mit einer variablen Anzahl von Buchstaben) oder _ (für einen einzelnen Platzhalterbuchstaben) verwendet werden.  Beispielsweise die Beschränkung `LIKE \_ake%` würde true zurückgeben für `Jake Stein`, `Jake Smith`oder `Fake Smith`.  Sie gibt &quot;false&quot;zurück für `Drake Smith`.

* `NOT LIKE` ähnelt dem oben aufgeführten Musterabgleich, überprüft jedoch, auf welche Muster nicht übereinstimmen.

* `IS` überprüft, ob die Spalte `NULL`oder leer.

* `IS NOT` ähnelt dem `IS` -Operator weiter oben, sucht jedoch nach Nicht-NULL-Spalten.

* `IN` prüft, ob ein Wert in einer kommagetrennten Liste vorhanden ist. (z. B. &quot;Farbe&quot; `IN` red,orange&quot;entspricht Farbe `equal to` rote OR-Farbe `equal to` orange).

* `NOT IN` ähnelt `IN` höher, prüft jedoch, ob ein Wert nicht vorhanden ist.
