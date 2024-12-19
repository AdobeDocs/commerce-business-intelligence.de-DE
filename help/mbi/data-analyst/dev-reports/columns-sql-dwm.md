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

Es gibt zwei wesentliche Unterschiede zwischen den Spalten, die in der [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) erstellt wurden, und den Spalten, die mithilfe der [[!DNL Data Warehouse Manager]](../data-warehouse-mgr/creating-calculated-columns.md) erstellt wurden. Einer ist die Abhängigkeit von Aktualisierungszyklen und der andere ist, wie Spalten in Ihrem Konto gespeichert werden.

## Spalten in der [!DNL SQL Report Builder]

Spalten sind nicht von Aktualisierungszyklen abhängig, sodass Sie nicht mehr auf den Abschluss einer Spalte warten müssen, bevor Sie eine Spalte iterieren können. Wenn Sie einen Fehler machen, dauert es nur ein paar Tastenanschläge, um ihn zu korrigieren - Sie müssen nicht mehr auf zwei Updates warten, bevor Sie wieder an die Arbeit gehen können.

>[!IMPORTANT]
>
>Die Spalten, die Sie mit dem [!DNL SQL]-Editor erstellen, werden nicht auf Ihrem Data Warehouse gespeichert. Sie haben immer Zugriff auf die Abfrage, die die Spalte enthält. Wenn Sie die Spalte jedoch in mehr als einem Bericht verwenden möchten, müssen Sie sie in der Abfrage für jeden Bericht neu erstellen. Das bedeutet, dass Spalten, die mit dem [!DNL SQL]-Editor erstellt wurden, im herkömmlichen [!DNL Report Builder] nicht verwendet werden können.

## Spalten im Data Warehouse-Manager

Spalten hängen von Aktualisierungszyklen ab, sodass ein vollständiger Zyklus abgeschlossen sein muss, bevor sie bearbeitet werden können. Diese Spalten werden im Data Warehouse-Manager gespeichert und können im herkömmlichen [!DNL Report Builder] oder [!DNL SQL Report Builder] verwendet werden.
