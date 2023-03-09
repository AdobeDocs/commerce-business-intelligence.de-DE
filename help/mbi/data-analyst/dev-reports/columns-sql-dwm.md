---
title: Unterschiede zwischen SQL und Data Warehouse Manager
description: Lernen Sie die Unterschiede zwischen SQL und Data Warehouse Manager kennen.
exl-id: 31dd7a04-5c03-4399-b67e-f51703eb9fea
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Unterschiede zwischen SQL und Data Warehouse Manager

Es gibt zwei wesentliche Unterschiede zwischen Spalten, die in der [SQL-Report Builder](../dev-reports/sql-rpt-bldr.md) und denen, die mithilfe der [Data Warehouse Manager](../data-warehouse-mgr/creating-calculated-columns.md). Das eine ist die Abhängigkeit von Aktualisierungszyklen, das andere ist, wie Spalten in Ihrem Konto gespeichert werden.

## Spalten im `SQL Report Builder`

Spalten hängen nicht von Aktualisierungszyklen ab. Sie müssen also nicht mehr warten, bis ein Zyklus abgeschlossen ist, bevor Sie eine Spalte iterieren können. Wenn man einen Fehler macht, braucht man nur ein paar Tastenanschläge, um ihn zu korrigieren - es wartet nicht mehr darauf, dass zwei Updates abgeschlossen werden, bevor man wieder an die Arbeit kommt.

>[!IMPORTANT]
>
>Die mit dem SQL-Editor erstellten Spalten werden nicht in Ihrer Data Warehouse gespeichert. Sie haben immer Zugriff auf die Abfrage, die die Spalte enthält. Wenn Sie die Spalte jedoch in mehr als einem Bericht verwenden möchten, müssen Sie sie in der Abfrage für jeden Bericht neu erstellen. Dies bedeutet, dass Spalten, die mit dem SQL-Editor erstellt wurden, nicht im herkömmlichen `Report Builder`.

## Spalten im Data Warehousen-Manager

Die Spalten hängen von den Aktualisierungszyklen ab. Daher muss ein vollständiger Zyklus abgeschlossen sein, bevor sie bearbeitet werden können. Diese Spalten werden im Data Warehouse Manager gespeichert und können im herkömmlichen Modus verwendet werden `Report Builder` oder `SQL Report Builder`.
