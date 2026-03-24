---
title: Unterschiede zwischen SQL und Data Warehouse Manager
description: Lernen Sie die Unterschiede zwischen SQL und Data Warehouse Manager kennen.
exl-id: 31dd7a04-5c03-4399-b67e-f51703eb9fea
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, SQL Report Builder, Reports
TQID: https://experienceleague.adobe.com/aWLLAi9e-A6Di7AGujRNd79W7GqSRo5yIgmQRZAHOEQ
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 210
ht-degree: 0%

---

# Unterschiede zwischen [!DNL SQL] und [!DNL Data Warehouse Manager]

Es gibt zwei wesentliche Unterschiede zwischen den Spalten, die in der [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) erstellt wurden, und den Spalten, die mithilfe der [[!DNL Data Warehouse Manager]](../data-warehouse-mgr/creating-calculated-columns.md) erstellt wurden. Einer ist die Abhängigkeit von Aktualisierungszyklen und der andere ist, wie Spalten in Ihrem Konto gespeichert werden.

## Spalten in der [!DNL SQL Report Builder]

Spalten sind nicht von Aktualisierungszyklen abhängig, sodass Sie nicht mehr auf den Abschluss einer Spalte warten müssen, bevor Sie eine Spalte iterieren können. Wenn Sie einen Fehler machen, dauert es nur ein paar Tastenanschläge, um ihn zu korrigieren - Sie müssen nicht mehr auf zwei Updates warten, bevor Sie wieder an die Arbeit gehen können.

>[!IMPORTANT]
>
>Die Spalten, die Sie mit dem [!DNL SQL]-Editor erstellen, werden nicht in Ihrer Data Warehouse gespeichert. Sie haben immer Zugriff auf die Abfrage, die die Spalte enthält. Wenn Sie die Spalte jedoch in mehr als einem Bericht verwenden möchten, müssen Sie sie in der Abfrage für jeden Bericht neu erstellen. Das bedeutet, dass Spalten, die mit dem [!DNL SQL]-Editor erstellt wurden, im herkömmlichen [!DNL Report Builder] nicht verwendet werden können.

## Spalten im Data Warehouse Manager

Spalten hängen von Aktualisierungszyklen ab, sodass ein vollständiger Zyklus abgeschlossen sein muss, bevor sie bearbeitet werden können. Diese Spalten werden im Data Warehouse Manager gespeichert und können im herkömmlichen [!DNL Report Builder] oder [!DNL SQL Report Builder] verwendet werden.
