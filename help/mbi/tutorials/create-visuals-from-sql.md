---
title: Erstellen von Visualisierungen aus SQL-Abfragen
description: Lernen Sie die im SQL Report Builder verwendete Terminologie kennen und erhalten Sie eine solide Grundlage für die Erstellung von SQL-Visualisierungen.
exl-id: 9b9bc205-5b64-4e64-8d23-057072e5dd72
role: Admin, Data Architect, Data Engineer, Leader, User
feature: SQL Report Builder, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Erstellen von Visualisierungen aus SQL-Abfragen

Ziel dieses Tutorials ist es, Sie mit der in der [!DNL SQL Report Builder] verwendeten Terminologie vertraut zu machen und Ihnen eine solide Grundlage für die Erstellung von `SQL visualizations` zu geben.

Der [[!DNL SQL Report Builder]](../data-analyst/dev-reports/sql-rpt-bldr.md) ist ein Report Builder mit Optionen: Sie können eine Abfrage ausführen, um nur eine Datentabelle abzurufen, oder Sie können diese Ergebnisse in einen Bericht umwandeln. In diesem Tutorial wird beschrieben, wie Sie eine Visualisierung aus einer SQL-Abfrage erstellen.

## Terminologie

Bevor Sie mit diesem Tutorial beginnen, lesen Sie die folgende in der `SQL Report Builder` verwendete Terminologie.

- `Series`: Die Spalte, die Sie messen möchten, wird im SQL-Report Builder als Reihe bezeichnet. Häufige Beispiele sind `revenue`, `items sold` und `marketing spend`. Mindestens eine Spalte muss als `Series` festgelegt sein, um eine Visualisierung zu erstellen.

- `Category`: Die Spalte, die Sie zur Segmentierung Ihrer Daten verwenden möchten, wird als `Category` bezeichnet. Dies entspricht der Funktion `Group By` in den [`Visual Report Builder`](../data-user/reports/ess-rpt-build-visual.md). Wenn Sie beispielsweise den Umsatz Ihrer Kunden über die gesamte Lebensdauer nach ihrer Akquise-Quelle segmentieren möchten, wird die Spalte, die die Akquise-Quelle enthält, als `Category` angegeben. Mehr als eine Spalte kann als `Category` festgelegt werden.

>[!NOTE]
>
>Daten und Zeitstempel können auch als `Categories` verwendet werden. Es handelt sich lediglich um eine weitere Datenspalte in Ihrer Abfrage, die in der Abfrage selbst nach Bedarf formatiert und sortiert werden muss.

- `Labels`: Diese werden als X-Achsen-Beschriftungen angewendet. Bei der Analyse von Datentrends im Zeitverlauf werden die Spalten für Jahr und Monat als Titel angegeben. Es kann mehr als eine Spalte als Titel festgelegt werden.

## Schritt 1: Abfrage schreiben

Beachten Sie Folgendes:

- Der [!DNL SQL Report Builder] verwendet [`Redshift SQL`](https://docs.aws.amazon.com/redshift/latest/dg/c_redshift-and-postgres-sql.html).

- Wenn Sie einen Bericht mit einer Zeitreihe erstellen, stellen Sie sicher, dass Sie die Zeitstempelspalte auf `ORDER BY` setzen. Dadurch wird sichergestellt, dass die Zeitstempel im Bericht in der richtigen Reihenfolge dargestellt werden.

- Die Funktion `EXTRACT` eignet sich hervorragend zum Analysieren von Tag, Woche, Monat oder Jahr des Zeitstempels. Dies ist nützlich, wenn der `time interval`, den Sie im Bericht verwenden möchten, `daily`, `weekly`, `monthly` oder `yearly` lautet.

Um zu beginnen, öffnen Sie die [!DNL SQL Report Builder], indem Sie auf **[!UICONTROL Report Builder** > **SQL Report Builder]** klicken.

Betrachten Sie als Beispiel diese Abfrage, die die monatliche Gesamtzahl der verkauften Artikel für jedes Produkt zurückgibt:

```sql
    SELECT SUM("qty") AS "Items Sold", "products's name" AS "product name",
    EXTRACT(year from "Order date") AS "year",
    EXTRACT(month from "Order date") AS "month"
    FROM "items"
    WHERE "products's name" LIKE '%Jeans'
    GROUP BY  "products's name", "year","month"
    ORDER BY "year" ASC,"month" ASC
    LIMIT 3500
```

Diese Abfrage gibt die folgende Ergebnistabelle zurück:

![](../assets/SQL_results_table.png)

## Schritt 2: Erstellen der Visualisierung

Mit diesen Ergebnissen, *wie erstellen Sie die Visualisierung?* Um zu beginnen, klicken Sie auf die Registerkarte **[!UICONTROL Chart]** im Bereich `Results` . Dadurch wird die Registerkarte `Chart settings` angezeigt.

Wenn eine Abfrage zum ersten Mal ausgeführt wird, kann der Bericht undurchsichtig aussehen, da alle Spalten in der Abfrage als Reihe dargestellt werden:

![](../assets/SQL_initial_report_results.png)

In diesem Beispiel soll es sich um ein Liniendiagramm handeln, das sich im Zeitverlauf entwickelt. Verwenden Sie zum Erstellen die folgenden Einstellungen:

- `Series`: Wählen Sie die Spalte `Items sold` als `Series` aus, da Sie sie messen möchten. Nachdem Sie eine `Series` -Spalte definiert haben, wird eine einzelne Zeile im Bericht gezeichnet.

- `Category`: In diesem Beispiel möchten Sie jedes Produkt als eine andere Zeile im Bericht anzeigen. Dazu legen Sie `Product name` als `Category` fest.

- `Labels`: Verwenden Sie die Spalten `year` und `month` als Beschriftungen auf der X-Achse, um `Items Sold` als Trend im Zeitverlauf anzeigen zu können.

>[!NOTE]
>
>Die Abfrage muss eine &quot;`ORDER BY`&quot;-Klausel für die Beschriftungen enthalten, wenn es sich um `date`/`time` -Spalten handelt.

Im Folgenden sehen Sie, wie Sie diese Visualisierung erstellt haben, von der Ausführung der Abfrage bis zur Einrichtung des Berichts:

![](../assets/SQL_report_settings.gif)

## Schritt 3: Auswählen eines `Chart Type`

In diesem Beispiel wird der Diagrammtyp `Line` verwendet. Um einen anderen `chart type` zu verwenden, klicken Sie auf die Symbole über dem Abschnitt &quot;Grafikoptionen&quot;, um ihn zu ändern:

![](../assets/Chart_types.png)

## Schritt 4: Speichern der Visualisierung

Wenn Sie diesen Bericht erneut verwenden möchten, geben Sie dem Bericht einen Namen und klicken Sie oben rechts auf **[!UICONTROL Save]** .

Wählen Sie im Dropdown-Menü `Chart` als `Type` und dann ein Dashboard, in dem der Bericht gespeichert werden soll.

## Aufwischen

Willst du noch einen Schritt weiter gehen? Sehen Sie sich die Best Practices für die [Abfrageoptimierung](../best-practices/optimizing-your-sql-queries.md) an.
