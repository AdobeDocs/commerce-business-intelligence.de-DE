---
title: Arbeiten mit SQL Report Builder
description: Erfahren Sie, wie Sie Daten und Metriken mithilfe von SQL Report Builder überprüfen können, damit Sie die Ergebnisse mit den Daten aus Ihrer lokalen Datenbank vergleichen können.
exl-id: d1d9e099-4138-43e6-aaec-6f15ebc5c4d4
role: Admin, Data Architect, Data Engineer, User
feature: Reports, Data Warehouse Manager, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# [!DNL SQL Report Builder]

Der [!DNL SQL Report Builder] wird hauptsächlich zum Erstellen neuer Berichte und zum Iterieren von Analysen verwendet, kann aber auch verwendet werden, um Daten und Metriken effektiv zu überprüfen. In den folgenden Informationen wird erläutert, wie Sie Daten und Metriken mithilfe von [!DNL SQL Report Builder] prüfen können, damit Sie die Ergebnisse mit den Daten aus Ihrer lokalen Datenbank vergleichen können.

## Abfrage zu einer Metrik

Öffnen Sie zunächst die [!DNL SQL Report Builder], indem Sie zu **[!UICONTROL Report Builder > SQL Report Builder > Create Report]** navigieren. Sie können die Seitenleiste im Editor [!DNL SQL] verwenden, um eine Metrik direkt in Ihre Abfrage einzufügen, indem Sie den Mauszeiger über die Metrik bewegen und auf **[!UICONTROL Insert]** klicken. Dadurch wird die Abfragedefinition dieser Metrik zum Editor hinzugefügt. Die Definition umfasst die folgenden Komponenten:

- Der ausgeführte **metrische Vorgang**, wie im Beispiel unten durch `SUM()` angegeben.
- Die **Tabelle auf**, die die Metrik erstellt wurde, wie durch die `FROM` -Klausel angegeben.
- Alle **Filter (und Filtersätze)**, die zur Metrik hinzugefügt wurden, wie durch die `WHERE` -Klausel im folgenden Beispiel angegeben.
- Die Komponente des **Zeitstempels** (Jahr, Monat), für die die Daten sortiert werden sollen, wie durch die `ORDER BY` -Klausel im unten stehenden Beispiel angegeben.

Um eine bessere Übersicht über die Abfrage zu erhalten, können Sie die Anzeige im Abfragefeld neu formatieren. Wählen Sie &quot;`Run Query`&quot;, wenn Sie bereit sind. Die Ergebnisse werden als Tabelle im Berichtbereich unter der Abfrage ausgefüllt.

![](../../assets/run-query-results.gif)

## Einschränkung der Abfrage

Wenn Sie versuchen, eine bestimmte Diskrepanz oder einen bestimmten Datensatz zu ermitteln, sollten Sie die Abfrage auf ein bestimmtes Beispiel beschränken, um es mit Ihrer lokalen Datenbank abgleichen zu können. Bearbeiten Sie dazu die Abfrage entsprechend Ihren gewünschten Einschränkungen. Im folgenden Beispiel beschränken Sie die Abfrage so, dass nur der Umsatz ab dem 1. Januar 2013 oder höher erfasst wird. Nachdem Sie die Abfrage aktualisiert haben, wählen Sie erneut **[!UICONTROL Run Query]** aus, um die Ergebnisse zu aktualisieren.

![](../../assets/restricting-query.gif)

## Speichern und exportieren

Wenn der Bericht Ihren Anforderungen entspricht, geben Sie dem Bericht einen eindeutigen Namen, klicken Sie auf &quot;**[!UICONTROL Save]**&quot;, wählen Sie den Berichtstyp aus, den Sie speichern möchten, und klicken Sie auf das Dashboard. Bei der Prüfung von Metriken empfiehlt Adobe, den Bericht als `Table` zu speichern und ihn in einem Test-Dashboard zu speichern.

Nachdem der Bericht gespeichert wurde, navigieren Sie zu diesem Dashboard, indem Sie `Go to Dashboard` auswählen. Von dort aus können Sie die Daten exportieren, indem Sie den Bericht suchen und **[!UICONTROL Options gear > Full `.csv`Export]** oder **[!UICONTROL Full Excel Export]** auswählen.

![](../../assets/export-dboard-data.gif)

## Benutzerdefinierte Abfragen

Sie können auch benutzerdefinierte Abfragen schreiben und die Ergebnisse exportieren, um sie mit Ihrer lokalen Datenbank zu vergleichen. Schreiben Sie entsprechend den [Richtlinien für die Abfrageoptimierung](../../best-practices/optimizing-your-sql-queries.md) eine Abfrage in den SQL-Editor. Sie können die Schaltflächen oben in der Seitenleiste verwenden, um zwischen den Listen der Tabellen und Metriken zu wechseln, die für die Verwendung in [!DNL SQL Report Builder] verfügbar sind, und sie zu Ihrer Abfrage hinzuzufügen. Wenn Ihre benutzerdefinierte Abfrage Ihren Anforderungen entspricht, können Sie den Bericht speichern und diese Daten aus dem Dashboard exportieren.

>[!NOTE]
>
>Wenn Sie nach der Prüfung Ihrer Daten eine Diskrepanz feststellen, finden Sie weitere Informationen zu den nächsten Schritten im Support-Thema [Support kontaktieren: Datendiskrepanzen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-data-discrepancies.html) .
