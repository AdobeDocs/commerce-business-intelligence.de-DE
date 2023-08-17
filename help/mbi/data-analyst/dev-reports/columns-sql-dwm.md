---
title: Unterschiede zwischen SQL und Data Warehouse Manager
description: Lernen Sie die Unterschiede zwischen SQL und Data Warehouse Manager kennen.
exl-id: 31dd7a04-5c03-4399-b67e-f51703eb9fea
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, SQL Report Builder, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Unterschiede zwischen [!DNL SQL] und [!DNL Data Warehouse Manager]

Es gibt zwei wesentliche Unterschiede zwischen Spalten, die in der [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) und denen, die mithilfe der [[!DNL Data Warehouse Manager]](../data-warehouse-mgr/creating-calculated-columns.md). Das eine ist die Abhängigkeit von Aktualisierungszyklen, das andere ist, wie Spalten in Ihrem Konto gespeichert werden.

## Spalten im [!DNL SQL Report Builder]

Spalten hängen nicht von Aktualisierungszyklen ab. Sie müssen also nicht mehr warten, bis ein Zyklus abgeschlossen ist, bevor Sie eine Spalte iterieren können. Wenn man einen Fehler macht, braucht man nur ein paar Tastenanschläge, um ihn zu korrigieren - es wartet nicht mehr darauf, dass zwei Updates abgeschlossen werden, bevor man wieder an die Arbeit kommt.

>[!IMPORTANT]
>
>Die Spalten, die Sie mithilfe der [!DNL SQL] -Editor nicht auf Ihrer Data Warehouse gespeichert. Sie haben immer Zugriff auf die Abfrage, die die Spalte enthält. Wenn Sie die Spalte jedoch in mehr als einem Bericht verwenden möchten, müssen Sie sie in der Abfrage für jeden Bericht neu erstellen. Dies bedeutet, dass Spalten, die mit der Variablen [!DNL SQL] Der Editor kann nicht im herkömmlichen [!DNL Report Builder].

## Spalten im Data Warehouse-Manager

Die Spalten hängen von den Aktualisierungszyklen ab. Daher muss ein vollständiger Zyklus abgeschlossen sein, bevor sie bearbeitet werden können. Diese Spalten werden im Data Warehouse-Manager gespeichert und können im herkömmlichen [!DNL Report Builder] oder [!DNL SQL Report Builder].
