---
title: Spezielle Filteroperatoren
description: Erfahren Sie mehr über einige spezielle Operatoren, die in Filtern beim Erstellen eines Berichts oder beim Erstellen einer Metrik verwendet werden.
exl-id: 12837490-b9ca-4040-bb71-8988b5dde485
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: 'https://experienceleague.adobe.com/xUfPCWqheQFIG9faVsA5PEWiyn6hLO-Rrm8jPzmaWiw'
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
    internal-label: Commerce Intelligence
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
    internal-label: Data Warehouse Manager
  - id: 5d2a63cb-5675-5572-9de5-bc904157ef45
    internal-label: Commerce Tables
  - id: f842eedf-96a8-52c7-891d-4e56f7441a7e
    internal-label: Reports
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: fdbaf74705fb224414ac8cb69f6a1b34277e3f79
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%
---
# Filteroptionen

In diesem Thema werden einige spezielle `operators` untersucht, die in `filters` beim [Erstellen eines Berichts](../../tutorials/using-visual-report-builder.md){: target="_blank"} oder [Erstellen einer Metrik) &#x200B;](../../data-user/reports/ess-manage-data-metrics.md){: target="_blank"}.

## `Filter Operators`

* `LIKE` für Mustervergleich. Dies muss mit den Platzhalterzeichen % (für einen Platzhalter mit einer variablen Anzahl von Buchstaben) oder _ (für einen einzelnen Platzhalterbuchstaben) verwendet werden.  Die `LIKE \_ake%` würde beispielsweise für `Jake Stein`, `Jake Smith` oder `Fake Smith` „true“ zurückgeben.  Sie würde für `Drake Smith` „false“ zurückgeben.

* `NOT LIKE` ähnelt der Musterübereinstimmung oben, prüft jedoch, welche Muster nicht übereinstimmen.

* `IS` prüft, ob die Spalte `NULL` oder leer ist.

* `IS NOT` ähnelt dem `IS` Operator oben, sucht jedoch nach Spalten, die nicht NULL sind.

* `IN` prüft, ob ein Wert in einer kommagetrennten Liste vorhanden ist. (Beispiel: „Farbe `IN` rot,orange“ entspricht der Farbe `equal to` rot ODER der Farbe `equal to` orange).

* `NOT IN` ähnelt `IN` oben, prüft aber, ob ein Wert fehlt.
