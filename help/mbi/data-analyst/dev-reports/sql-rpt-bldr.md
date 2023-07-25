---
title: Verwenden von SQL Report Builder
description: Lernen Sie die In- und Outs der Verwendung von SQL Report Builder kennen.
exl-id: 3a485b00-c59d-4bc5-b78b-57e9e92dd9d6
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, SQL Report Builder, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 0%

---

# Verwenden [!DNL SQL Report Builder]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md) , um SQL-Diagramme zu erstellen und zu bearbeiten. `Standard` Benutzer können diese Diagramme in Dashboards neu anordnen und `Read-only` -Benutzer haben dasselbe Erlebnis wie herkömmliche Diagramme. Darüber hinaus `Read-only` -Benutzer haben keinen Zugriff auf den Text der Abfrage.

Siehe [Schulungsvideo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-sql-report-builder.html) , um mehr zu erfahren.

[!DNL SQL], oder Structured Query Language, ist eine Programmiersprache, die zur Kommunikation mit Datenbanken verwendet wird. In [!DNL Commerce Intelligence], [!DNL SQL] wird verwendet, um Daten aus Ihrer Data Warehouse abzufragen oder abzurufen. Sehen Sie sich die Berichte in Ihrem Dashboard an - hinter den Kulissen wird jeder von einem [!DNL SQL] Abfrage.

Sie können die [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) um Ihre Data Warehouse direkt abzufragen, die Ergebnisse anzuzeigen und in ein Diagramm umzuwandeln. Sie können mit der Erstellung eines Berichts beginnen, indem Sie [!DNL SQL Report Builder] durch Klicken auf **[!UICONTROL Report Builder** > **[!DNL SQL Report Builder]]**.

Siehe [Schulungsvideo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-sql-report-builder.html) , um mehr zu erfahren.

Die [!DNL SQL Report Builder] ermöglicht Ihnen, Ihre Data Warehouse direkt abzufragen, die Ergebnisse anzuzeigen und sie schnell in ein Diagramm umzuwandeln. Der beste Teil zur Verwendung von [!DNL SQL] zum Erstellen von Berichten müssen Sie nicht auf Aktualisierungszyklen warten, um die von Ihnen erstellten Spalten zu iterieren. Wenn die Ergebnisse nicht richtig aussehen, können Sie die Abfrage schnell bearbeiten und erneut ausführen, bis die Ergebnisse Ihren Erwartungen entsprechen.

Dieses Thema führt Sie durch die Verwendung der [!DNL SQL Report Builder]. Wenn Sie wissen, wie Sie sich umgehen, sehen Sie sich die [!DNL SQL] für Visualisierungen oder versuchen Sie, einige der von Ihnen geschriebenen Abfragen zu optimieren.

In diesem Artikel behandelt:

1. [Schreiben von Abfragen](#writing)

1. [Ausführen der Abfrage und Anzeigen der Ergebnisse](#runquery)

1. [Erstellen einer Visualisierung](#createviz)

1. [Bericht speichern](#save)

## [!DNL SQL Report Builder] Integrationen

[[!DNL Google Analytics]](../importing-data/integrations/google-analytics.md) ist die einzige Integration, die nicht für die Verwendung mit der [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md). Diese Funktion befindet sich in der Entwicklung.

Erste Schritte mit der Erstellung eines [!DNL SQL] Bericht, klicken Sie auf **[!UICONTROL Report Builder]** oder **[!UICONTROL Add Report]** oben in jedem Dashboard. Im [!DNL Report Picker] Bildschirm, klicken Sie auf **[!UICONTROL SQL Report Builder]** , um [!DNL SQL] Editor.

## Erste Schritte

Um einen Bericht zu bearbeiten, klicken Sie auf das Zahnrad (![](../../assets/gear-icon.png)) in der oberen rechten Ecke eines [!DNL SQL]-basiertes Diagramm und klicken Sie auf **[!UICONTROL Edit]**.

## Schreiben von Abfragen {#writing}

>[!NOTE]
>
>[!DNL SQL Report Builder] bei Abfragen wird zwischen Groß- und Kleinschreibung unterschieden. Stellen Sie sicher, dass Sie beim Schreiben von Abfragen die richtige Groß-/Kleinschreibung verwenden, oder Sie können unerwartete Ergebnisse oder Fehler erzeugen.

Im Folgenden [Richtlinien zur Abfrageoptimierung](../../best-practices/optimizing-your-sql-queries.md), schreiben Sie eine Abfrage in [!DNL SQL] Editor.

>[!IMPORTANT]
>
>**Metriken in [!DNL SQL] Berichte** - Wenn Sie eine Metrik in einen SQL-Bericht einfügen, wird die `current definition` verwendet wird.

Wenn die Metrik in der Zukunft aktualisiert wird, wird der SQL-Bericht *nicht* die Änderungen widerspiegeln. Sie müssen den Bericht manuell bearbeiten, damit die Änderungen wirksam werden.

Mit den Schaltflächen am oberen Rand der Seitenleiste können Sie zwischen Tabellen- und Metriklisten umschalten, die in der Variablen [!DNL SQL Report Builder]. Wenn Sie nicht sehen, wonach Sie in der Liste suchen, versuchen Sie, mithilfe der Suchleiste oben in der Seitenleiste danach zu suchen.

Sie können auch die Seitenleiste im [!DNL SQL] Editor verwenden, um Metriken, Tabellen und Spalten direkt in Ihre Abfragen einzufügen, indem Sie den Mauszeiger über sie halten und auf **[!UICONTROL Insert]**:

![Tabellen in die [!DNL SQL] Editor.](../../assets/SQL_RB_Insert_Table.png)

>[!NOTE]
>
>Alle [SELECT-Funktion](https://www.postgresql.org/docs/9.5/sql-select.html#SQL-SELECT-LIST)oder einer Funktion, die keine Daten mutiert, die von PostgreSQL unterstützt wird, wird im SQL-Report Builder unterstützt. Dazu gehören AVG, COUNT, COUNT, COUNT DISTINCT, MIN/MAX und SUM.

Außerdem können `JOIN` -Typ wird unterstützt, aber Adobe empfiehlt nur die Verwendung von INNER JOIN, da dies der kostengünstigste der `JOIN` Typen.

## Ausführen der Abfrage und Anzeigen der Ergebnisse {#runquery}

Wenn Sie Ihre Abfrage geschrieben haben, klicken Sie auf **[!UICONTROL Run Query]**. Die Ergebnisse werden in einer Tabelle unter dem SQL-Editor angezeigt:

![Ausführen der Abfrage und Anzeigen der Ergebnisse.](../../assets/SQL_Run_Query.gif)

Wenn in den Ergebnissen ein falsches Ergebnis auftritt, können Sie die Abfrage bearbeiten und erneut ausführen, bis Sie zufrieden sind.

Manchmal wird [Meldungen unterhalb des Editors mit EXPLAIN](../../best-practices/optimizing-your-sql-queries.md). Wenn eine davon angezeigt wird, bedeutet dies, dass Ihre Abfrage nicht ausgeführt wurde und eine kleine Feinabstimmung erforderlich ist.

Nachdem Sie die Bearbeitung Ihrer Abfrage abgeschlossen haben, können Sie entweder eine Visualisierung erstellen oder Ihre Arbeit in einem Dashboard speichern.

## Erstellen einer Visualisierung {#createviz}

Um eine Visualisierung mit Ihren Abfrageergebnissen zu erstellen, klicken Sie auf die Schaltfläche **[!UICONTROL Chart]** im `Results` -Bereich. Wählen Sie auf dieser Registerkarte Folgendes aus:

* Die `Series`oder der Spalte, die Sie messen möchten, z. B. **Verkaufte Artikel**.
* Die `Category`oder der Spalte, die Sie zur Segmentierung Ihrer Daten verwenden möchten, z. B. **Akquisequelle**.
* Die `Labels`oder X-Achsenwerte.

Hier sehen Sie, wie der Visualisierungsprozess aussieht:

![](../../assets/SQL_RB_viz_overview.gif)

Eine ausführliche Anleitung zum Erstellen einer Visualisierung finden Sie im Abschnitt [Tutorial zum Erstellen von Visualisierungen aus SQL-Abfragen](../../tutorials/create-visuals-from-sql.md){: target=&quot;_blank&quot;}.

## Bericht speichern {#save}

Bevor Sie Ihre Arbeit speichern können, müssen Sie dem Bericht einen Namen geben. Denken Sie daran, dem [Best Practice-Richtlinien für die Benennung](../../best-practices/naming-elements.md){: target=&quot;_blank&quot;} und wählen Sie etwas aus, das deutlich vermittelt, was der Bericht ist!

Klicken **[!UICONTROL Save]** oben rechts im [!DNL SQL] und wählen Sie den Bericht aus `Type` (`Chart` oder `Table`). Um die Elemente einzuschließen, wählen Sie das Dashboard aus, in dem der Bericht gespeichert werden soll, und klicken Sie auf **[!UICONTROL Save to Dashboard]**.

![](../../assets/SQL_Save_Report.gif)

### Daten analysieren

#### [!DNL SQL Report Builder]

[[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) bietet Ihnen die Möglichkeit, Ihre Data Warehouse direkt abzufragen, die Ergebnisse anzuzeigen und sie schnell in einen Bericht umzuwandeln. Verwenden [!DNL SQL] erlaubt auch [zur Verwendung [!DNL SQL] nicht verfügbare Funktionen](https://docs.aws.amazon.com/redshift/latest/dg/c_SQL_functions.html) im `Visual` oder `Cohort` Report Builder, sodass Sie mehr Kontrolle über Ihre Daten haben.

Berechnete Spalten, die mit [!DNL SQL] sind nicht von Aktualisierungszyklen abhängig, d. h., Sie können sie wie gewünscht durchlaufen und sofort Ergebnisse sehen.

>[!NOTE]
>
>Dies gilt nur für die Struktur der Spalte, nicht für die Aktualisierung der Daten. Neue Daten hängen weiterhin von erfolgreich abgeschlossenen Aktualisierungszyklen ab.

| **Das ist perfekt für ...** | **Das ist nicht so toll für ...** |
|---|---|
| Vermittelnde/erweiterte Analysten | Anfänger - Sie müssen es wissen [!DNL SQL]. |
| Die [!DNL SQL] savvy | Einfache Analysen: Das Schreiben einer Abfrage kann mehr Arbeit als einfach die Verwendung der [!UICONTROL Visual Report Builder]. |
| Erstellen von einmaligen berechneten Spalten | Freigabe für andere - denken Sie an Ihre Zielgruppe: was sie verstehen [!DNL SQL]? Andernfalls könnten sie durch die Erstellung des Berichts verwirrt werden. |
| Daten mit `one-to-many` Beziehungen |  |
| Testen einer neuen Spalte oder Analyse |  |

#### Datenbank vs. SQL Editor-Ergebnisse

Meistens können Unterschiede in den Ergebnissen auf Aktualisierungszyklen zurückgeführt werden. Wenn [!DNL Commerce Intelligence] im Prozess der Replikation von Daten aus Ihrer Datenbank auf Ihre Data Warehouse ausgeführt wird, kann es sogar bei Verwendung derselben Abfrage zu unterschiedlichen Ergebnissen kommen.

Verbindungsprobleme können auch zu Diskrepanzen führen. Navigieren Sie zum `Connections` Seite durch Klicken auf **[!DNL Manage Data** > **Connections]** zur Überprüfung - Gibt es einen Fehler bei der betreffenden Datenbankintegration? Wenn ja, müssen Sie möglicherweise [die Integration erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html) um die Dinge wieder in Gang zu bringen.

Wenn all Ihre Integrationen erfolgreich verbunden sind und Sie sich nicht mitten in einem Aktualisierungszyklus befinden, kann etwas Anderes fehlschlagen.

#### Wird gelöscht [!DNL SQL] auch die zugrunde liegenden Spalten aus meiner Data Warehouse löschen?

Nein, Sie verlieren keine Spalten aus Ihrer Data Warehouse, unabhängig davon, wie Sie sie erstellt haben.

Spalten, die mit der `Data Warehouse Manager` sind nicht betroffen, wenn Sie einen Bericht oder eine Abfrage löschen, die/die sie verwendet.

Spalten, die mit der [!DNL SQL Report Builder] nicht in Ihrer Data Warehouse gespeichert werden.


#### `Report Builder` versus `SQL Report Builder`

Die [!DNL SQL Report Builder] bietet Ihnen mehr Flexibilität bei der Erstellung und Strukturierung Ihrer Diagramme - Sie können beispielsweise auswählen, welche Werte auf der `X` und `Y` Achsen. Weitere Informationen zum Erstellen von Diagrammen finden Sie unter [!DNL SQL Report Builder], sehen Sie sich die [Erstellen von Visualisierungen aus [!DNL SQL] Abfragen](../../tutorials/create-visuals-from-sql.md) Tutorial.

#### `Cohort Report Builder` {#cohortrb}

Im Gegensatz zu [!DNL Visual Report Builder], die [[!DNL Cohort Report Builder]](../dev-reports/cohort-rpt-bldr.md) ist für einen einzigen Zweck gedacht - die Analyse und Identifizierung von Verhaltenstrends ähnlicher Benutzergruppen im Zeitverlauf. Verwenden der [!DNL Cohort Report Builder] erfordert keine [!DNL SQL] Ich kann Ihnen helfen, sich ohne Zögern einzutauchen, wenn Sie gerade erst anfangen.

| **Das ist perfekt für ...** | **Das ist nicht so toll für ...** |
|---|---|
| Vermittelnde/erweiterte Analysten | Anfänger - Sie benötigen praxisdefinierte Kohorten. |
| Identifizieren von Verhaltenstrends im Zeitverlauf | Qualitative Analyse - sie kann [done](../dev-reports/create-qual-cohort-analysis.md), erfordert jedoch Hilfe von Adoben. |

## Neuerstellen von Abfragen nach dem Aktualisierungszyklus

Sie müssen Ihre Abfragen nicht neu erstellen. Mit der Variablen [[!DNL SQL Report Builder]](../dev-reports/sql-rpt-bldr.md) werden so gespeichert, wie sie im traditionellen `Report Builder`. Der Aktualisierungsprozess für [!DNL SQL] sind die gleichen Diagramme - nach der Aktualisierung Ihrer Daten werden die Werte in Ihren Diagrammen neu berechnet und angezeigt.

>[!NOTE]
>
>Beim Löschen einer [!DNL SQL] -Bericht/Abfrage verwenden, werden die zugrunde liegenden Spalten nicht aus Ihrer Data Warehouse gelöscht. Sie verlieren keine Spalten, unabhängig davon, wie Sie sie erstellt haben.

* Spalten, die mit dem Data Warehousen-Manager erstellt wurden, sind nicht betroffen, wenn Sie einen Bericht oder eine Abfrage löschen, die/die diese verwendet.

* Spalten, die mit SQL Report Builder erstellt wurden, werden nicht in Ihrer Data Warehouse gespeichert.

## Aufbrechen {#wrapup}

Wenn Sie etwas herausforderndes ausprobieren möchten, warum versuchen Sie nicht, eine für die Visualisierung optimierte Abfrage zu schreiben? Sehen Sie sich die [Erstellen von Visualisierungen aus [!DNL SQL] Tutorial zu Abfragen](../../tutorials/create-visuals-from-sql.md){: target=&quot;_blank&quot;}, um zu beginnen.
