---
title: SQL-Abfragen in Commerce Intelligence-Berichte übersetzen
description: Erfahren Sie, wie SQL-Abfragen in die berechneten Spalten und Metriken übersetzt werden, die Sie in Commerce Intelligence verwenden.
exl-id: b3e3905f-6952-4f15-a582-bf892a971fae
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, SQL Report Builder, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# SQL-Abfragen in Commerce Intelligence übersetzen

Haben Sie sich schon einmal gefragt, wie SQL-Abfragen in die [berechneten Spalten](../data-warehouse-mgr/creating-calculated-columns.md), [Metriken](../../data-user/reports/ess-manage-data-metrics.md) und [Berichte](../../tutorials/using-visual-report-builder.md) übersetzt werden, die Sie in [!DNL Commerce Intelligence] verwenden? Wenn Sie ein starker SQL-Benutzer sind, können Sie mit dem Verständnis, wie SQL in [!DNL Commerce Intelligence] übersetzt wird, im [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md) schlauer arbeiten und die [!DNL Commerce Intelligence]-Plattform optimal nutzen.

Am Ende dieses Themas finden Sie eine **Übersetzungsmatrix** für SQL-Abfragen und [!DNL Commerce Intelligence] -Elemente.

Sehen Sie sich zunächst eine allgemeine Abfrage an:

| | |
|--- |--- |
| `SELECT` |  |
| `a,` | Bericht `group by` |
| `SUM(b)` | `Aggregate function` (Spalte) |
| `FROM c` | `Source` table |
| `WHERE` |  |
| `d IS NOT NULL` | `Filter` |
| `AND time < X`<br><br> `AND time >= Y` | Bericht `time frame` |
| `GROUP BY a` | Bericht `group by` |

In diesem Beispiel werden die meisten Übersetzungsfälle behandelt, es gibt jedoch einige Ausnahmen. Tauchen Sie ein, beginnend mit der Übersetzung der Funktion `aggregate` .

## Aggregat-Funktionen

Aggregatfunktionen (z. B. `count`, `sum`, `average`, `max`, `min`) in Abfragen haben entweder die Form von **Metrikaggregationen** oder **Spaltenaggregationen** in [!DNL Commerce Intelligence]. Der Differenzierungsfaktor ist, ob ein Join erforderlich ist, um die Aggregation durchzuführen.

Sehen Sie sich für jeden der oben genannten Beispiele an.

## Metrikaggregationen {#aggregate}

Beim Aggregieren von `within a single table` ist eine Metrik erforderlich. Die Aggregatfunktion `SUM(b)` aus der obigen Abfrage würde daher höchstwahrscheinlich durch eine Metrik dargestellt, die die Spalte `B` summiert. 

Sehen Sie sich ein bestimmtes Beispiel an, wie eine `Total Revenue` -Metrik in [!DNL Commerce Intelligence] definiert werden kann. Sehen Sie sich die unten stehende Abfrage an, mit der Sie versuchen, zu übersetzen:

| | |
|--- |--- |
| `SELECT` |  |
| `SUM(order_total) as "Total Revenue"` | `Metric operation` (Spalte) |
| `FROM orders` | `Metric source` table |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | Metrik `filter` |
| `AND created_at < X`<br><br>`AND created_at >= Y` | Metrik `timestamp` (und Berichterstellung `time range`) |

Navigieren Sie zum Metrikaufbau, indem Sie auf **[!UICONTROL Manage Data** > ** Metriken **> **Neue Metrik erstellen]** klicken. Wählen Sie zunächst die entsprechende Tabelle `source` aus, die in diesem Fall die Tabelle `orders` ist. Anschließend würde die Metrik wie folgt eingerichtet:

![Metrikaggregation](../../assets/Metric_aggregation.png)

## Spaltenaggregationen

Eine berechnete Spalte ist erforderlich, wenn eine Spalte aggregiert wird, die aus einer anderen Tabelle verbunden ist. So kann beispielsweise in Ihrer `customer` -Tabelle eine Spalte mit dem Namen `Customer LTV` erstellt werden, in der der Gesamtwert aller mit diesem Kunden verbundenen Bestellungen in der `orders` -Tabelle zusammengefasst wird.

Die Abfrage für diese Aggregation kann etwa wie folgt aussehen:

|  |  |
|--- |--- |
| `Select` | |
| `c.customer_id` | Aggregat-Eigentümer |
| `SUM(o.order_total) as "Customer LTV"` | Aggregat-Vorgang (Spalte) |
| `FROM customers c` | Aggregat-Eigentümertabelle |
| `JOIN orders o` | Aggregations-Quelltabelle |
| `ON c.customer_id = o.customer_id` | Pfad |
| `WHERE o.status = 'success'` | Aggregat-Filter |

Die Einrichtung in [!DNL Commerce Intelligence] erfordert die Verwendung Ihres Data Warehouse-Managers, wo Sie einen Pfad zwischen Ihrer `orders`- und `customers`-Tabelle erstellen und dann in der Kundentabelle eine Spalte mit dem Namen `Customer LTV` erstellen.

Sehen Sie sich an, wie Sie einen neuen Pfad zwischen `customers` und `orders` festlegen. Das Endziel besteht darin, eine neue aggregierte Spalte in der Tabelle `customers` zu erstellen. Navigieren Sie also zunächst zur Tabelle `customers` in Ihrer Data Warehouse und klicken Sie dann auf **[!UICONTROL Create a Column** > ** Definition auswählen **> **SUM]**.

Wählen Sie anschließend die Quelltabelle aus. Wenn ein Pfad zu Ihrer `orders`-Tabelle vorhanden ist, wählen Sie ihn einfach aus der Dropdown-Liste aus. Wenn Sie jedoch einen neuen Pfad erstellen, klicken Sie auf **[!UICONTROL Create new path]** und der folgende Bildschirm wird angezeigt:

![Neuen Pfad erstellen](../../assets/Create_new_path.png)

Hier müssen Sie die Beziehung zwischen den beiden Tabellen, denen Sie beitreten möchten, sorgfältig überdenken. In diesem Fall gibt es potenziell `Many` Bestellungen, die mit dem `One` -Kunden verknüpft sind. Daher wird die `orders` -Tabelle auf der Seite `Many` aufgelistet, während die `customers` -Tabelle auf der Seite `One` ausgewählt ist.

>[!NOTE]
>
>In [!DNL Commerce Intelligence] entspricht ein `path` einem `Join` in SQL.

Nachdem der Pfad gespeichert wurde, können Sie die Spalte `Customer LTV` erstellen! Siehe unten:

![](../../assets/Customer_LTV.gif)

Nachdem Sie die neue Spalte `Customer LTV` in Ihrer Tabelle `customers` erstellt haben, können Sie mit dieser Spalte eine [Metrik-Aggregation](#aggregate) erstellen (z. B. um die durchschnittliche LTV-Rate pro Kunde zu ermitteln). Sie können auch `group by` oder `filter` durch die berechnete Spalte in einem Bericht verwenden, indem Sie vorhandene Metriken verwenden, die auf der Tabelle `customers` erstellt wurden.

>[!NOTE]
>
>Für letztere müssen Sie bei jedem Erstellen einer neuen berechneten Spalte [die Dimension zu den vorhandenen Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md), bevor sie als `filter` oder `group by` verfügbar ist.

Siehe [Erstellen berechneter Spalten](../data-warehouse-mgr/creating-calculated-columns.md) mit Ihrem Data Warehouse-Manager.

## `Group By` Klauseln

`Group By` -Funktionen in Abfragen werden in [!DNL Commerce Intelligence] häufig als Spalte dargestellt, die zum Segmentieren oder Filtern eines visuellen Berichts verwendet wird. Beispiel: Besuchen Sie die zuvor untersuchte `Total Revenue`-Abfrage erneut. Segmentieren Sie diesmal jedoch den Umsatz durch die `coupon\_code`, um ein besseres Verständnis darüber zu erhalten, welche Coupons den meisten Umsatz generieren.

Beginnen Sie mit der folgenden Abfrage:

| | |
|--- |--- |
| `SELECT coupon_code,` | Bericht `group by` |
| `SUM(order_total) as "Total Revenue"` | `Metric operation`(column) |
| `FROM orders` | `Metric source` table |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | Metrik `filter` |
| `AND created_at < '2016-12-01'` <br><br>`AND created_at >= '2016-09-01'` | Metrik `timestamp` (und Berichterstellung `time range`) |
| `GROUP BY coupon_code` | Bericht `group by` |

>[!NOTE]
>
>Der einzige Unterschied zu der Abfrage, mit der Sie zuvor begonnen haben, besteht darin, dass &quot;coupon\_code&quot;als Gruppe von hinzugefügt wird._

Mit derselben `Total Revenue` -Metrik, die Sie zuvor erstellt haben, können Sie jetzt Ihren Bericht mit dem Umsatz erstellen, der nach Couponcode segmentiert ist! Sehen Sie sich das unten stehende GIF an, in dem gezeigt wird, wie dieser visuelle Bericht mit Daten von September bis November eingerichtet wird:

![Umsatz nach Couponcode](../../assets/Revenue_by_coupon_code.gif)

## Formeln

Manchmal kann eine Abfrage mehrere Aggregationen umfassen, um die Beziehung zwischen verschiedenen Spalten zu berechnen. Sie können beispielsweise den durchschnittlichen Bestellwert in einer Abfrage auf zwei Arten berechnen:

* `AVG('order\_total')` ODER
* `SUM('order\_total')/COUNT('order\_id')`

Die frühere Methode würde die Erstellung einer neuen Metrik beinhalten, die einen Durchschnittswert für die Spalte `order\_total` ausführt. Die letztgenannte Methode kann jedoch direkt im ReportBuilder erstellt werden, vorausgesetzt, Sie verfügen bereits über Metriken, mit denen die `Total Revenue` und die `Number of orders` berechnet werden.

Gehen Sie einen Schritt zurück und prüfen Sie die Gesamtabfrage für `Average order value`:

| | |
|--- |--- |
| `SELECT` |  |
| `SUM(order_total) as "Total Revenue"` | Metrik `operation` (Spalte) |
| `COUNT(order_id) as "Number of orders"` | Metrik `operation` (Spalte) |
| `SUM(order_total)/COUNT(order_id) as "Average order value"` | Metrik `operation` (Spalte)/Metrikvorgang(Spalte) |
| `FROM orders` | Metrik `source` Tabelle |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | Metrik `filter` |
| `AND created_at < '2016-12-01'`<br><br>`AND created_at >= '2016-09-01'` | Metrikzeitstempel (und Berichtszeitbereich) |

Angenommen, Sie verfügen bereits über Metriken zur Berechnung von `Total Revenue` und `Number of orders`. Da diese Metriken vorhanden sind, können Sie einfach den `Report Builder` öffnen und eine On-Demand-Berechnung mithilfe der Funktion `Formula` erstellen:

![AOV forumula](../../assets/AOV_forumula.gif)

## Aufwischen

Wenn Sie SQL-Benutzer sind und darüber nachdenken, wie Abfragen in [!DNL Commerce Intelligence] übersetzt werden, können Sie berechnete Spalten, Metriken und Berichte erstellen.

Sehen Sie sich die folgende Matrix für einen schnellen Überblick an. Dies zeigt das äquivalente [!DNL Commerce Intelligence] -Element einer SQL-Klausel und wie sie je nach Verwendung in der Abfrage mehr als einem Element zugeordnet werden kann.

## Commerce Intelligence-Elemente

| **`SQL Clause`** | **`Metric`** | **`Filter`** | **`Report group by`** | **`Report time frame`** | **`Path`** | **`Calculated column inputs`** | **`Source table`** |
|---|---|---|---|---|---|---|---|
| `SELECT` | X | - | X | - | - | X | - |
| `FROM` | - | - | - | - | - | - | X |
| `WHERE` | - | X | - | - | - | - | - |
| `WHERE` (mit Zeitelementen) | - | - | - | X | - | - | - |
| `JOIN...ON` | - | X | - | - | X | X | - |
| `GROUP BY` | - | - | X | - | - | - | - |
