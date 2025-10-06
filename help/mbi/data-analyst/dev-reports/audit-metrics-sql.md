---
title: Arbeiten mit SQL Report Builder
description: Erfahren Sie, wie Sie Daten und Metriken mithilfe von SQL Report Builder überprüfen können, damit Sie die Ergebnisse mit den Daten aus Ihrer lokalen Datenbank vergleichen können.
exl-id: d1d9e099-4138-43e6-aaec-6f15ebc5c4d4
role: Admin, Data Architect, Data Engineer, User
feature: Reports, Data Warehouse Manager, SQL Report Builder
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# [!DNL SQL Report Builder]

Die [!DNL SQL Report Builder] wird hauptsächlich zum Erstellen neuer Berichte und zur Iteration von Analysen verwendet, kann aber auch zur effektiven Prüfung von Daten und Metriken verwendet werden. In den folgenden Informationen wird erläutert, wie Sie Daten und Metriken mithilfe der [!DNL SQL Report Builder] überprüfen können, damit Sie die Ergebnisse mit den Daten aus Ihrer lokalen Datenbank vergleichen können.

## Metrik abfragen

Öffnen Sie zunächst die [!DNL SQL Report Builder], indem Sie zu **[!UICONTROL Report Builder > SQL Report Builder > Create Report]** navigieren. Sie können die Seitenleiste im [!DNL SQL] verwenden, um eine Metrik direkt in Ihre Abfrage einzufügen, indem Sie den Mauszeiger über die Metrik bewegen und auf **[!UICONTROL Insert]** klicken. Dadurch wird dem Editor die Abfragedefinition dieser Metrik hinzugefügt. Die Definition umfasst die folgenden Komponenten:

- Der **metrische Vorgang** der ausgeführt wird, wie im folgenden Beispiel durch `SUM()` angegeben.
- Die **Tabelle** auf der die Metrik basiert, angegeben durch die `FROM`.
- Alle **Filter (und Filtersätze)** die der Metrik hinzugefügt wurden, angegeben durch die `WHERE` im folgenden Beispiel.
- Die Komponente des **Zeitstempels** (Jahr, Monat), für die die Daten bestellt werden sollen, angegeben durch die `ORDER BY` im folgenden Beispiel.

Um eine klarere Ansicht der Abfrage zu erhalten, können Sie die Darstellung der Abfrage im Abfragefeld neu formatieren. Wenn Sie bereit sind, wählen Sie `Run Query` aus. Die Ergebnisse werden als Tabelle im Bedienfeld Bericht unter der Abfrage angezeigt.

![Animierte Demonstration der Ausführung einer SQL-Abfrage und der Anzeige von Ergebnissen](../../assets/run-query-results.gif)

## Abfrage einschränken

Wenn Sie versuchen, eine bestimmte Diskrepanz oder einen bestimmten Datensatz zu identifizieren, sollten Sie die Abfrage auf eine bestimmte Stichprobe beschränken, um sie mit Ihrer lokalen Datenbank zu vergleichen. Sie können dies tun, indem Sie die Abfrage entsprechend Ihren gewünschten Einschränkungen bearbeiten. Im folgenden Beispiel beschränken Sie die Abfrage darauf, nur Umsätze ab dem 1. Januar 2013 einzubeziehen. Nachdem Sie die Abfrage aktualisiert haben, wählen Sie erneut **[!UICONTROL Run Query]** aus, um die Ergebnisse zu aktualisieren.

![Animierte Demonstration der Einschränkung von Abfragen mit Filtern](../../assets/restricting-query.gif)

## Speichern und Exportieren

Wenn der Bericht Ihren Anforderungen entspricht, geben Sie dem Bericht einen eindeutigen Namen, klicken Sie auf **[!UICONTROL Save]** und wählen Sie den Berichtstyp aus, den Sie speichern möchten, sowie das Dashboard. Beim Auditing von Metriken empfiehlt Adobe, den Bericht als `Table` zu speichern und in einem Test-Dashboard zu speichern.

Nachdem der Bericht gespeichert wurde, navigieren Sie zu diesem Dashboard, indem Sie `Go to Dashboard` auswählen. Von dort aus können Sie die Daten exportieren, indem Sie den Bericht suchen und **[!UICONTROL Options gear > Full `.csv`Export]** oder **[!UICONTROL Full Excel Export]** auswählen.

![Animierte Demonstration zum Exportieren von Dashboard-Daten](../../assets/export-dboard-data.gif)

## Benutzerdefinierte Abfragen

Sie können auch benutzerdefinierte Abfragen schreiben und die Ergebnisse exportieren, um sie mit Ihrer lokalen Datenbank zu vergleichen. Schreiben Sie gemäß [Richtlinien für die ](../../best-practices/optimizing-your-sql-queries.md)) eine Abfrage im SQL-Editor. Mit den Schaltflächen oben in der Seitenleiste können Sie zwischen Listen von Tabellen und Metriken wechseln, die für die Verwendung in der [!DNL SQL Report Builder] verfügbar sind, und sie zu Ihrer Abfrage hinzufügen. Wenn Ihre benutzerdefinierte Abfrage Ihren Anforderungen entspricht, können Sie den Bericht speichern und diese Daten aus dem Dashboard exportieren.

>[!NOTE]
>
>Wenn Sie nach dem Überprüfen Ihrer Daten eine Diskrepanz feststellen, finden Sie im Support-Thema [Kontaktaufnahme mit dem Support: ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-data-discrepancies.html) Diskrepanzen) weitere Informationen zu weiteren Schritten.
