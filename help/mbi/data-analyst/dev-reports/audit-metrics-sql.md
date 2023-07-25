---
title: Arbeiten mit SQL Report Builder
description: Erfahren Sie, wie Sie Daten und Metriken mithilfe von SQL Report Builder überprüfen können, damit Sie die Ergebnisse mit den Daten aus Ihrer lokalen Datenbank vergleichen können.
exl-id: d1d9e099-4138-43e6-aaec-6f15ebc5c4d4
role: Admin, Data Architect, Data Engineer, User
feature: Reports, Data Warehouse Manager, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# [!DNL SQL Report Builder]

Die [!DNL SQL Report Builder] wird hauptsächlich zur Erstellung neuer Berichte und Iteration von Analysen verwendet, kann aber auch zur effektiven Prüfung von Daten und Metriken verwendet werden. In den folgenden Informationen wird erläutert, wie Daten und Metriken mithilfe der [!DNL SQL Report Builder] damit Sie die Ergebnisse mit den Daten aus Ihrer lokalen Datenbank vergleichen können.

## Abfrage zu einer Metrik

Öffnen Sie zunächst das [!DNL SQL Report Builder] durch Navigation zu **[!UICONTROL Report Builder > SQL Report Builder > Create Report]**. Sie können die Seitenleiste im [!DNL SQL] Editor verwenden, um eine Metrik direkt in Ihre Abfrage einzufügen, indem Sie den Mauszeiger über die Metrik bewegen und auf **[!UICONTROL Insert]**. Dadurch wird die Abfragedefinition dieser Metrik zum Editor hinzugefügt. Die Definition umfasst die folgenden Komponenten:

- Die **Metrikvorgang** durchgeführt werden, angegeben durch `SUM()` im Beispiel unten.
- Die **Tabelle auf** , aus der die Metrik erstellt wurde, angezeigt durch die `FROM` -Klausel.
- Alle **Filter (und Filtersätze)** die zur Metrik hinzugefügt wurden, angegeben durch die `WHERE` -Klausel im Beispiel unten.
- Die Komponente der **timestamp** (Jahr, Monat), an dem die Daten bestellt werden sollen, angegeben durch `ORDER BY` -Klausel im Beispiel unten.

Um eine bessere Übersicht über die Abfrage zu erhalten, können Sie die Anzeige im Abfragefeld neu formatieren. Wenn Sie bereit sind, wählen Sie `Run Query`. Die Ergebnisse werden als Tabelle im Berichtbereich unter der Abfrage ausgefüllt.

![](../../assets/run-query-results.gif)

## Einschränkung der Abfrage

Wenn Sie versuchen, eine bestimmte Diskrepanz oder einen bestimmten Datensatz zu ermitteln, sollten Sie die Abfrage auf ein bestimmtes Beispiel beschränken, um es mit Ihrer lokalen Datenbank abgleichen zu können. Bearbeiten Sie dazu die Abfrage entsprechend Ihren gewünschten Einschränkungen. Im folgenden Beispiel beschränken Sie die Abfrage so, dass nur der Umsatz ab dem 1. Januar 2013 oder höher erfasst wird. Nachdem Sie die Abfrage aktualisiert haben, wählen Sie **[!UICONTROL Run Query]** erneut, um die Ergebnisse zu aktualisieren.

![](../../assets/restricting-query.gif)

## Speichern und exportieren

Wenn der Bericht Ihren Anforderungen entspricht, geben Sie dem Bericht einen eindeutigen Namen und klicken Sie auf **[!UICONTROL Save]** und wählen Sie den Berichtstyp aus, den Sie speichern möchten, sowie das Dashboard. Bei der Prüfung von Metriken empfiehlt Adobe, den Bericht als `Table` und speichern Sie sie in einem Test-Dashboard.

Navigieren Sie nach dem Speichern des Berichts zu diesem Dashboard, indem Sie `Go to Dashboard`. Dort können Sie die Daten exportieren, indem Sie den Bericht suchen und **[!UICONTROL Options gear > Full `.csv`Export]** oder **[!UICONTROL Full Excel Export]**.

![](../../assets/export-dboard-data.gif)

## Benutzerdefinierte Abfragen

Sie können auch benutzerdefinierte Abfragen schreiben und die Ergebnisse exportieren, um sie mit Ihrer lokalen Datenbank zu vergleichen. Im Folgenden [Richtlinien zur Abfrageoptimierung](../../best-practices/optimizing-your-sql-queries.md), schreiben Sie eine Abfrage in den SQL-Editor. Sie können die Schaltflächen oben in der Seitenleiste verwenden, um zwischen den Listen der Tabellen und Metriken umzuschalten, die für die Verwendung in der [!DNL SQL Report Builder] und fügen Sie sie Ihrer Abfrage hinzu. Wenn Ihre benutzerdefinierte Abfrage Ihren Anforderungen entspricht, können Sie den Bericht speichern und diese Daten aus dem Dashboard exportieren.

>[!NOTE]
>
>Wenn Sie nach der Prüfung Ihrer Daten eine Diskrepanz feststellen, überprüfen Sie die [Support kontaktieren: Datendiskrepanzen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-data-discrepancies.html) Support-Thema für weitere Informationen zu den nächsten Schritten.
