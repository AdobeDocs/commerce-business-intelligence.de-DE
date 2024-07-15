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

Dieses Thema behandelt einige spezielle `operators`, die in `filters` verwendet werden, wenn [ein Bericht erstellt](../../tutorials/using-visual-report-builder.md){: target=&quot;_blank&quot;} oder [eine Metrik erstellt](../../data-user/reports/ess-manage-data-metrics.md){: target=&quot;_blank&quot;}.

## `Filter Operators`

* `LIKE` für Musterabgleich. Dies muss mit den Platzhalterzeichen % (für einen Platzhalter mit einer variablen Anzahl von Buchstaben) oder _ (für einen einzelnen Platzhalterbuchstaben) verwendet werden.  Beispielsweise würde die Beschränkung `LIKE \_ake%` für `Jake Stein`, `Jake Smith` oder `Fake Smith` &quot;true&quot;zurückgeben.  Für `Drake Smith` wird &quot;false&quot;zurückgegeben.

* `NOT LIKE` ähnelt dem Muster, das oben übereinstimmt, überprüft jedoch, auf welche Muster nicht übereinstimmen.

* `IS` prüft, ob die Spalte `NULL` oder leer ist.

* `IS NOT` ähnelt dem Operator `IS` oben, sucht jedoch nach Spalten, die nicht NULL sind.

* `IN` prüft, ob ein Wert in einer kommagetrennten Liste vorhanden ist. (z. B. &quot;Farbe `IN` rot,orange&quot;entspricht der Farbe `equal to` rot ODER Farbe `equal to` orange).

* `NOT IN` ähnelt `IN` oben, prüft jedoch, ob ein Wert nicht vorhanden ist.
