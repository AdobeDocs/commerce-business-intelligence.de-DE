---
title: Spezielle Filteroperatoren
description: Erfahren Sie mehr über einige spezielle Operatoren, die in Filtern beim Erstellen eines Berichts oder beim Erstellen einer Metrik verwendet werden.
exl-id: 12837490-b9ca-4040-bb71-8988b5dde485
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Filteroptionen

In diesem Thema werden einige spezielle `operators` untersucht, die in `filters` beim [Erstellen eines Berichts](../../tutorials/using-visual-report-builder.md){: target="_blank"} oder [Erstellen einer Metrik) ](../../data-user/reports/ess-manage-data-metrics.md){: target="_blank"}.

## `Filter Operators`

* `LIKE` für Mustervergleich. Dies muss mit den Platzhalterzeichen % (für einen Platzhalter mit einer variablen Anzahl von Buchstaben) oder _ (für einen einzelnen Platzhalterbuchstaben) verwendet werden.  Die `LIKE \_ake%` würde beispielsweise für `Jake Stein`, `Jake Smith` oder `Fake Smith` „true“ zurückgeben.  Sie würde für `Drake Smith` „false“ zurückgeben.

* `NOT LIKE` ähnelt der Musterübereinstimmung oben, prüft jedoch, welche Muster nicht übereinstimmen.

* `IS` prüft, ob die Spalte `NULL` oder leer ist.

* `IS NOT` ähnelt dem `IS` Operator oben, sucht jedoch nach Spalten, die nicht NULL sind.

* `IN` prüft, ob ein Wert in einer kommagetrennten Liste vorhanden ist. (Beispiel: „Farbe `IN` rot,orange“ entspricht der Farbe `equal to` rot ODER der Farbe `equal to` orange).

* `NOT IN` ähnelt `IN` oben, prüft aber, ob ein Wert fehlt.
