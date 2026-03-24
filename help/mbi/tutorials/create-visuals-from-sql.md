---
title: Erstellen von Visualisierungen aus SQL-Abfragen
description: Lernen Sie die in SQL Report Builder verwendete Terminologie kennen und erhalten Sie eine solide Grundlage für die Erstellung von SQL-Visualisierungen.
exl-id: 9b9bc205-5b64-4e64-8d23-057072e5dd72
role: Admin, Developer, Leader, User
feature: SQL Report Builder, Data Warehouse Manager, Reports, Data Integration
TQID: https://experienceleague.adobe.com/xWv7O8UJ6gXxysl6oG1t24ygF-PE4LTanwyrrvoJzQ4
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 665
ht-degree: 0%

---

# Erstellen von Visualisierungen aus SQL-Abfragen

Ziel dieses Tutorials ist es, Sie mit der in der [!DNL SQL Report Builder] verwendeten Terminologie vertraut zu machen und Ihnen eine solide Grundlage für die Erstellung von `SQL visualizations` zu bieten.

Der [[!DNL SQL Report Builder]](../data-analyst/dev-reports/sql-rpt-bldr.md) ist ein Report Builder mit Optionen: Sie können eine Abfrage zum einzigen Zweck des Abrufs einer Datentabelle ausführen oder diese Ergebnisse in einen Bericht umwandeln. In diesem Tutorial wird erläutert, wie Sie eine Visualisierung aus einer SQL-Abfrage erstellen.

## Terminologie

Bevor Sie mit diesem Tutorial beginnen, lesen Sie die folgende Terminologie, die in der `SQL Report Builder` verwendet wird.

- `Series`: Die Spalte, die Sie messen möchten, wird in der SQL-Report Builder als Serie bezeichnet. Häufige Beispiele sind `revenue`, `items sold` und `marketing spend`. Zum Erstellen einer Visualisierung muss mindestens eine Spalte als `Series` festgelegt werden.

- `Category`: Die Spalte, die Sie zum Segmentieren Ihrer Daten verwenden möchten, wird als `Category` bezeichnet. Dies entspricht der `Group By` Funktion in der [`Visual Report Builder`](../data-user/reports/ess-rpt-build-visual.md). Wenn Sie beispielsweise den Umsatz Ihrer Kundinnen und Kunden während ihrer Lebensdauer nach ihrer Akquisequelle segmentieren möchten, wird die Spalte, die die Akquisequelle enthält, als `Category` angegeben. Es können mehrere Spalten als `Category` festgelegt werden.

>[!NOTE]
>
>Datumsangaben und Zeitstempel können auch `Categories` verwendet werden. Sie sind nur eine weitere Datenspalte in Ihrer Abfrage und müssen in der Abfrage selbst nach Wunsch formatiert und sortiert sein.

- `Labels`: Diese werden als X-Achsen-Beschriftungen angewendet. Bei der Analyse von Daten-Trends im Zeitverlauf werden die Spalten für Jahr und Monat als Bezeichnungen angegeben. Es kann mehr als eine Spalte als Beschriftung festgelegt werden.

## Schritt 1: Abfrage schreiben

Beachten Sie Folgendes:

- Die [!DNL SQL Report Builder] verwendet [`Redshift SQL`](https://docs.aws.amazon.com/redshift/latest/dg/c_redshift-and-postgres-sql.html).

- Wenn Sie einen Bericht mit einer Zeitreihe erstellen, stellen Sie sicher, dass Sie die Zeitstempelspalten `ORDER BY`. Dadurch wird sichergestellt, dass die Zeitstempel im Bericht in der richtigen Reihenfolge dargestellt werden.

- Die `EXTRACT`-Funktion eignet sich hervorragend zum Analysieren des Tages, der Woche, des Monats oder des Jahres des Zeitstempels. Dies ist nützlich, wenn die `time interval`, die Sie für den Bericht verwenden möchten, `daily`, `weekly`, `monthly` oder `yearly` ist.

Öffnen Sie zunächst die [!DNL SQL Report Builder], indem Sie auf **[!UICONTROL Report Builder** > **SQL Report Builder]** klicken.

Betrachten Sie als Beispiel diese Abfrage, die die monatliche Gesamtzahl der für jedes Produkt verkauften Artikel zurückgibt:

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

![Tabelle mit SQL-Abfrageergebnissen mit Artikeln, die nach Produkt, Jahr und Monat verkauft wurden](../assets/SQL_results_table.png)

## Schritt 2: Visualisierung erstellen

Mit diesen Ergebnissen *Sie, wie Sie die Visualisierung erstellen.* Klicken Sie zunächst auf die Registerkarte **[!UICONTROL Chart]** im `Results`. Dadurch wird die Registerkarte `Chart settings` angezeigt.

Wenn eine Abfrage zum ersten Mal ausgeführt wird, kann der Bericht undurchsichtig aussehen, da alle Spalten in der Abfrage als Serie dargestellt werden:

![Anfänglicher SQL-Bericht mit allen als Serie dargestellten Spalten](../assets/SQL_initial_report_results.png)

In diesem Beispiel soll dies ein Liniendiagramm sein, das die Entwicklung im Zeitverlauf anzeigt. Verwenden Sie zum Erstellen die folgenden Einstellungen:

- `Series`: Wählen Sie die `Items sold` als `Series` aus, da Sie sie messen möchten. Nachdem Sie eine `Series` definiert haben, wird im Bericht eine einzelne Zeile angezeigt.

- `Category`: In diesem Beispiel möchten Sie jedes Produkt als eine andere Zeile im Bericht anzeigen. Legen Sie dazu `Product name` als `Category` fest.

- `Labels`: Verwenden Sie die Spalten `year` und `month` als Beschriftungen auf der X-Achse, um `Items Sold` als Trend im Zeitverlauf anzeigen zu können.

>[!NOTE]
>
>Die Abfrage muss eine `ORDER BY`-Klausel für die Beschriftungen enthalten, wenn es sich um `date`/`time` Spalten handelt.

Nachstehend finden Sie einen kurzen Überblick über die Erstellung dieser Visualisierung, von der Ausführung der Abfrage bis zur Einrichtung des Berichts:

![Animierte Demonstration der Konfiguration der Visualisierungseinstellungen von SQL-Berichten](../assets/SQL_report_settings.gif)

## Schritt 3: `Chart Type` auswählen

In diesem Beispiel wird der Diagrammtyp `Line` verwendet. Um einen anderen `chart type` zu verwenden, klicken Sie auf die Symbole über dem Abschnitt Diagrammoptionen , um ihn zu ändern:

![Verfügbare Diagrammtypsymbole einschließlich Linien-, Balken-, Flächen- und anderer Visualisierungsoptionen](../assets/Chart_types.png)

## Schritt 4: Speichern Sie die Visualisierung

Wenn Sie diesen Bericht erneut verwenden möchten, geben Sie dem Bericht einen Namen und klicken Sie oben rechts auf **[!UICONTROL Save]** .

Wählen Sie in der Dropdown-Liste `Chart` als `Type` und dann ein Dashboard aus, in dem der Bericht gespeichert werden soll.

## Verpackung

Möchten Sie einen Schritt weiter gehen? Sehen Sie sich die [Best Practices zur Abfrageoptimierung](../best-practices/optimizing-your-sql-queries.md) an.
