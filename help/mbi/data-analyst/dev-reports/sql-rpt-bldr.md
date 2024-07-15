---
title: Verwenden von SQL Report Builder
description: Lernen Sie die In- und Outs der Verwendung von SQL Report Builder kennen.
exl-id: 3a485b00-c59d-4bc5-b78b-57e9e92dd9d6
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, SQL Report Builder, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 0%

---

# Verwenden von [!DNL SQL Report Builder]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md) zum Erstellen und Bearbeiten von SQL-Diagrammen. `Standard` -Benutzer können diese Diagramme in Dashboards neu anordnen, und `Read-only` -Benutzer haben dasselbe Erlebnis wie herkömmliche Diagramme. Außerdem haben `Read-only` -Benutzer keinen Zugriff auf den Text der Abfrage.

Weitere Informationen finden Sie im [Schulungsvideo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-sql-report-builder.html) .

[!DNL SQL] oder &quot;Structured Query Language&quot;ist eine Programmiersprache, die zur Kommunikation mit Datenbanken verwendet wird. In [!DNL Commerce Intelligence] wird [!DNL SQL] zum Abfragen oder Abrufen von Daten von Ihrer Data Warehouse verwendet. Sehen Sie sich die Berichte in Ihrem Dashboard an - hinter den Kulissen wird jeder von einer [!DNL SQL] -Abfrage unterstützt.

Mit dem [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) können Sie Ihre Data Warehouse direkt abfragen, die Ergebnisse anzeigen und in eine Grafik umwandeln. Sie können einen Bericht mit dem Wert [!DNL SQL Report Builder] erstellen, indem Sie auf **[!UICONTROL Report Builder** > **[!DNL SQL Report Builder]]** klicken.

Weitere Informationen finden Sie im [Schulungsvideo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-sql-report-builder.html) .

Mit dem [!DNL SQL Report Builder] können Sie Ihre Data Warehouse direkt abfragen, die Ergebnisse anzeigen und sie schnell in eine Grafik umwandeln. Die beste Möglichkeit, mit [!DNL SQL] Berichte zu erstellen, besteht darin, dass Sie nicht auf Aktualisierungszyklen warten müssen, um von Ihnen erstellte Spalten zu iterieren. Wenn die Ergebnisse nicht richtig aussehen, können Sie die Abfrage schnell bearbeiten und erneut ausführen, bis die Ergebnisse Ihren Erwartungen entsprechen.

Dieses Thema führt Sie durch die Verwendung von [!DNL SQL Report Builder]. Nachdem Sie Ihren Umweg kennen, sehen Sie sich das Tutorial [!DNL SQL] für Visualisierungen an oder versuchen Sie, einige der von Ihnen geschriebenen Abfragen zu optimieren.

In diesem Artikel behandelt:

1. [Schreiben von Abfragen](#writing)

1. [Ausführen der Abfrage und Anzeigen der Ergebnisse](#runquery)

1. [Erstellen einer Visualisierung](#createviz)

1. [Bericht speichern](#save)

## [!DNL SQL Report Builder] Integrationen

[[!DNL Google Analytics]](../importing-data/integrations/google-analytics.md) ist die einzige Integration, die nicht für die Verwendung mit dem [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) verfügbar ist. Diese Funktion befindet sich in der Entwicklung.

Um mit der Erstellung eines [!DNL SQL] -Berichts zu beginnen, klicken Sie oben in jedem Dashboard auf **[!UICONTROL Report Builder]** oder **[!UICONTROL Add Report]** . Klicken Sie im Bildschirm [!DNL Report Picker] auf **[!UICONTROL SQL Report Builder]** , um den Editor [!DNL SQL] zu öffnen.

## Erste Schritte

Um einen Bericht zu bearbeiten, klicken Sie auf das Zahnradsymbol (![](../../assets/gear-icon.png)) in der oberen rechten Ecke eines [!DNL SQL]-basierten Diagramms und klicken Sie auf **[!UICONTROL Edit]**.

## Schreiben von Abfragen {#writing}

>[!NOTE]
>
>Bei [!DNL SQL Report Builder] -Abfragen wird zwischen Groß- und Kleinschreibung unterschieden. Stellen Sie sicher, dass Sie beim Schreiben von Abfragen die richtige Groß-/Kleinschreibung verwenden, oder Sie können unerwartete Ergebnisse oder Fehler erzeugen.

Schreiben Sie entsprechend den [ Richtlinien für die Abfrageoptimierung](../../best-practices/optimizing-your-sql-queries.md) eine Abfrage in den [!DNL SQL]-Editor.

>[!IMPORTANT]
>
>**Metriken in [!DNL SQL] Berichten** - Wenn Sie eine Metrik in einen SQL-Bericht einfügen, wird die `current definition` der Metrik verwendet.

Wenn die Metrik in der Zukunft aktualisiert wird, spiegelt der SQL-Bericht *nicht* die Änderungen wider. Sie müssen den Bericht manuell bearbeiten, damit die Änderungen wirksam werden.

Mit den Schaltflächen am oberen Rand der Seitenleiste können Sie zwischen Listen mit Tabellen und Metriken umschalten, die für die Verwendung in [!DNL SQL Report Builder] verfügbar sind. Wenn Sie nicht sehen, wonach Sie in der Liste suchen, versuchen Sie, mithilfe der Suchleiste oben in der Seitenleiste danach zu suchen.

Sie können auch die Seitenleiste im Editor [!DNL SQL] verwenden, um Metriken, Tabellen und Spalten direkt in Ihre Abfragen einzufügen, indem Sie den Mauszeiger über sie halten und auf **[!UICONTROL Insert]** klicken:

![Einfügen einer Tabelle in den [!DNL SQL]-Editor.](../../assets/SQL_RB_Insert_Table.png)

>[!NOTE]
>
>Jede [SELECT-Funktion](https://www.postgresql.org/docs/9.5/sql-select.html#SQL-SELECT-LIST) oder jede Funktion, die keine Daten mutiert, die von PostgreSQL unterstützt wird, wird im SQL-Report Builder unterstützt. Dazu gehören AVG, COUNT, COUNT, COUNT DISTINCT, MIN/MAX und SUM.

Außerdem wird jeder `JOIN` -Typ unterstützt, Adobe empfiehlt jedoch nur die Verwendung von INNER JOIN, da dies der kostengünstigste der `JOIN` -Typen ist.

## Ausführen der Abfrage und Anzeigen der Ergebnisse {#runquery}

Wenn Sie Ihre Abfrage geschrieben haben, klicken Sie auf **[!UICONTROL Run Query]**. Die Ergebnisse werden in einer Tabelle unter dem SQL-Editor angezeigt:

![ Ausführen der Abfrage und Anzeigen der Ergebnisse.](../../assets/SQL_Run_Query.gif)

Wenn in den Ergebnissen ein falsches Ergebnis auftritt, können Sie die Abfrage bearbeiten und erneut ausführen, bis Sie zufrieden sind.

Manchmal werden unter dem Editor [ Meldungen mit EXPLAIN angezeigt. ](../../best-practices/optimizing-your-sql-queries.md) Wenn eine davon angezeigt wird, bedeutet dies, dass Ihre Abfrage nicht ausgeführt wurde und eine kleine Feinabstimmung erforderlich ist.

Nachdem Sie die Bearbeitung Ihrer Abfrage abgeschlossen haben, können Sie entweder eine Visualisierung erstellen oder Ihre Arbeit in einem Dashboard speichern.

## Erstellen einer Visualisierung {#createviz}

Um eine Visualisierung mit Ihren Abfrageergebnissen zu erstellen, klicken Sie im Bereich `Results` auf die Registerkarte **[!UICONTROL Chart]** . Wählen Sie auf dieser Registerkarte Folgendes aus:

* Die `Series` oder die Spalte, die Sie messen möchten, z. B. **Verkauf**.
* Die `Category` oder die Spalte, die Sie zur Segmentierung Ihrer Daten verwenden möchten, z. B. **Akquise-Quelle**.
* Die Werte `Labels` oder X-Achse.

Hier sehen Sie, wie der Visualisierungsprozess aussieht:

![](../../assets/SQL_RB_viz_overview.gif)

Eine ausführliche Anleitung zum Erstellen einer Visualisierung finden Sie im Tutorial [Erstellen von Visualisierungen aus SQL-Abfragen](../../tutorials/create-visuals-from-sql.md){: target=&quot;_blank&quot;}.

## Bericht speichern {#save}

Bevor Sie Ihre Arbeit speichern können, müssen Sie dem Bericht einen Namen geben. Denken Sie daran, die [Best Practice-Richtlinien für die Benennung](../../best-practices/naming-elements.md){: target=&quot;_blank&quot;} zu befolgen und wählen Sie etwas aus, das deutlich vermittelt, was der Bericht ist!

Klicken Sie oben rechts im Editor [!DNL SQL] auf **[!UICONTROL Save]** und wählen Sie den Bericht `Type` (`Chart` oder `Table`) aus. Um die Elemente einzuschließen, wählen Sie das Dashboard aus, in dem der Bericht gespeichert werden soll, und klicken Sie auf &quot;**[!UICONTROL Save to Dashboard]**&quot;.

![](../../assets/SQL_Save_Report.gif)

### Daten analysieren

#### [!DNL SQL Report Builder]

Mit [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) können Sie Ihre Data Warehouse direkt abfragen, die Ergebnisse anzeigen und sie schnell in einen Bericht umwandeln. Durch Verwendung von [!DNL SQL] können Sie [auch nicht verfügbare](https://docs.aws.amazon.com/redshift/latest/dg/c_SQL_functions.html) Funktionen in den Report Buildern `Visual` oder `Cohort` verwenden, wodurch Sie eine bessere Kontrolle über Ihre Daten erhalten. [!DNL SQL] 

Mit [!DNL SQL] erstellte berechnete Spalten hängen nicht von Aktualisierungszyklen ab, d. h., Sie können sie wie gewünscht durchlaufen und sofort Ergebnisse anzeigen.

>[!NOTE]
>
>Dies gilt nur für die Struktur der Spalte, nicht für die Aktualisierung der Daten. Neue Daten hängen weiterhin von erfolgreich abgeschlossenen Aktualisierungszyklen ab.

| **Dies ist perfekt für ...**. | **Das ist nicht so toll für ...**. |
|---|---|
| Vermittelnde/erweiterte Analysten | Anfänger - Sie müssen [!DNL SQL] wissen. |
| Die [!DNL SQL]-Savy | Einfache Analysen: Das Schreiben einer Abfrage kann mehr Arbeit als einfach die Verwendung des [!UICONTROL Visual Report Builder] sein. |
| Erstellen von einmaligen berechneten Spalten | Teilen mit anderen - denken Sie an Ihre Zielgruppe: Verstehen sie [!DNL SQL]? Andernfalls könnten sie durch die Erstellung des Berichts verwirrt werden. |
| Daten mit `one-to-many` -Beziehungen |  |
| Testen einer neuen Spalte oder Analyse |  |

#### Datenbank vs. SQL Editor-Ergebnisse

Meistens können Unterschiede in den Ergebnissen auf Aktualisierungszyklen zurückgeführt werden. Wenn [!DNL Commerce Intelligence] gerade Daten aus Ihrer Datenbank auf Ihre Data Warehouse repliziert, werden möglicherweise auch bei Verwendung derselben Abfrage unterschiedliche Ergebnisse angezeigt.

Verbindungsprobleme können auch zu Diskrepanzen führen. Navigieren Sie zur Seite &quot;`Connections`&quot;, indem Sie auf &quot;**[!DNL Manage Data** > **Connections]**&quot;klicken, um sie auszuchecken. Gibt es einen Fehler für die betreffende Datenbankintegration? In diesem Fall müssen Sie möglicherweise [die Integration erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html), damit die Dinge wieder ausgeführt werden.

Wenn all Ihre Integrationen erfolgreich verbunden sind und Sie sich nicht mitten in einem Aktualisierungszyklus befinden, kann etwas Anderes fehlschlagen.

#### Löscht das Löschen eines [!DNL SQL] -Berichts auch die zugrunde liegenden Spalten aus meiner Data Warehouse?

Nein, Sie verlieren keine Spalten von Ihrer Data Warehouse, unabhängig davon, wie Sie sie erstellt haben.

Spalten, die mit dem `Data Warehouse Manager` erstellt wurden, sind nicht betroffen, wenn Sie einen Bericht oder eine Abfrage löschen, die/die diese verwendet.

Spalten, die mit dem [!DNL SQL Report Builder] erstellt wurden, werden nicht auf Ihrer Data Warehouse gespeichert.


#### `Report Builder` versus `SQL Report Builder`

Der [!DNL SQL Report Builder] gibt Ihnen mehr Flexibilität bei der Erstellung und Strukturierung Ihrer Diagramme - Sie können beispielsweise auswählen, welche Werte auf den Achsen `X` und `Y` angezeigt werden sollen. Weitere Informationen zum Erstellen von Diagrammen in [!DNL SQL Report Builder] finden Sie im Tutorial zum Erstellen von Visualisierungen aus  [!DNL SQL] Abfragen](../../tutorials/create-visuals-from-sql.md) .[

#### `Cohort Report Builder` {#cohortrb}

Im Gegensatz zum [!DNL Visual Report Builder] ist der [[!DNL Cohort Report Builder]](../dev-reports/cohort-rpt-bldr.md) für einen einzigen Zweck gedacht - die Analyse und Identifizierung von Verhaltenstrends ähnlicher Benutzergruppen im Zeitverlauf. Die Verwendung der [!DNL Cohort Report Builder] erfordert keine [!DNL SQL] Speicherkapazität, sodass Sie ohne Zögern sofort eintauchen können, wenn Sie gerade erst anfangen.

| **Dies ist perfekt für ...**. | **Das ist nicht so toll für ...**. |
|---|---|
| Vermittelnde/erweiterte Analysten | Anfänger - Sie benötigen praxisdefinierte Kohorten. |
| Identifizieren von Verhaltenstrends im Zeitverlauf | Qualitative Analyse: Sie kann [done](../dev-reports/create-qual-cohort-analysis.md) sein, erfordert jedoch Adobe-Hilfe. |

## Neuerstellen von Abfragen nach dem Aktualisierungszyklus

Sie müssen Ihre Abfragen nicht neu erstellen. Berichte, die mit dem [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) erstellt wurden, werden wie im herkömmlichen `Report Builder` gespeichert. Der Aktualisierungsprozess für [!DNL SQL] -Diagramme ist derselbe: Nach der Aktualisierung Ihrer Daten werden die Werte in Ihren Diagrammen neu berechnet und angezeigt.

>[!NOTE]
>
>Beim Löschen eines [!DNL SQL] -Berichts/einer -Abfrage werden die zugrunde liegenden Spalten nicht aus Ihrer Data Warehouse gelöscht. Sie verlieren keine Spalten, unabhängig davon, wie Sie sie erstellt haben.

* Spalten, die mit dem Data Warehouse Manager erstellt wurden, sind nicht betroffen, wenn Sie einen Bericht oder eine Abfrage löschen, die bzw. die sie verwendet.

* Spalten, die mit dem SQL-Report Builder erstellt wurden, werden nicht auf Ihrer Data Warehouse gespeichert.

## Aufwischen {#wrapup}

Wenn Sie etwas herausforderndes ausprobieren möchten, warum versuchen Sie nicht, eine für die Visualisierung optimierte Abfrage zu schreiben? Sehen Sie sich das Tutorial [Erstellen von Visualisierungen aus  [!DNL SQL] Abfragen}](../../tutorials/create-visuals-from-sql.md){: target=&quot;_blank&quot;} an, um zu beginnen.
