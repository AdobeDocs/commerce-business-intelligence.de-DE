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

Haben Sie sich jemals gefragt, wie SQL-Abfragen in die [berechneten Spalten](../data-warehouse-mgr/creating-calculated-columns.md), [Metriken](../../data-user/reports/ess-manage-data-metrics.md) und [Berichte](../../tutorials/using-visual-report-builder.md) übersetzt werden, die Sie in [!DNL Commerce Intelligence] verwenden? Wenn Sie ein erfahrener SQL-Benutzer sind, können Sie im [!DNL Commerce Intelligence]Data Warehouse Manager[ intelligenter arbeiten, wenn Sie verstehen, wie SQL in übersetzt ](../data-warehouse-mgr/tour-dwm.md), und die [!DNL Commerce Intelligence] optimal nutzen.

Am Ende dieses Themas finden Sie eine **Übersetzungsmatrix** für SQL-Abfrageklauseln und [!DNL Commerce Intelligence].

Beginnen Sie mit einer allgemeinen Abfrage:

| | |
|--- |--- |
| `SELECT` |  |
| `a,` | Report `group by` |
| `SUM(b)` | `Aggregate function` (Spalte) |
| `FROM c` | `Source` |
| `WHERE` |  |
| `d IS NOT NULL` | `Filter` |
| `AND time < X`<br><br> `AND time >= Y` | Report `time frame` |
| `GROUP BY a` | Report `group by` |

Dieses Beispiel behandelt die meisten Übersetzungsfälle, es gibt jedoch einige Ausnahmen. Tauchen Sie ein, beginnend mit der Übersetzung der `aggregate`.

## Aggregatfunktionen

Aggregatfunktionen (z. B. `count`, `sum`, `average`, `max`, `min`) in Abfragen haben entweder die Form **Metrikaggregationen** oder **Spaltenaggregationen** in [!DNL Commerce Intelligence]. Der Unterscheidungsfaktor ist, ob ein Join erforderlich ist, um die Aggregation durchzuführen.

Sehen Sie sich ein Beispiel für jeden der oben genannten Punkte an.

## Metrikaggregationen {#aggregate}

Beim Aggregieren von `within a single table` ist eine Metrik erforderlich. Beispielsweise würde die `SUM(b)` Aggregatfunktion aus der obigen Abfrage höchstwahrscheinlich durch eine Metrik dargestellt, die die `B` addiert. 

Sehen Sie sich ein konkretes Beispiel an, wie eine `Total Revenue` Metrik in [!DNL Commerce Intelligence] definiert werden könnte. Sehen Sie sich die Abfrage an, die Sie übersetzen möchten:

| | |
|--- |--- |
| `SELECT` |  |
| `SUM(order_total) as "Total Revenue"` | `Metric operation` (Spalte) |
| `FROM orders` | `Metric source` |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | `filter` |
| `AND created_at < X`<br><br>`AND created_at >= Y` | `timestamp` (und Reporting-`time range`) |

Navigieren Sie zum Metrik-Builder, indem Sie **[!UICONTROL Manage Data** > **&#x200B; Metriken &#x200B;**> **Neue Metrik erstellen]** klicken. Sie müssen zunächst die entsprechende `source` auswählen, bei der es sich in diesem Fall um die `orders` handelt. Anschließend würde die Metrik wie unten dargestellt eingerichtet:

![Metrikaggregation](../../assets/Metric_aggregation.png)

## Spaltenaggregationen

Eine berechnete Spalte ist erforderlich, wenn eine Spalte aggregiert wird, die aus einer anderen Tabelle verbunden ist. Beispielsweise könnte in Ihrer `customer` eine Spalte namens `Customer LTV` erstellt sein, die den Gesamtwert aller Bestellungen summiert, die mit diesem Kunden in der `orders`-Tabelle verknüpft sind.

Die Abfrage für diese Aggregation kann in etwa wie folgt aussehen:

|  |  |
|--- |--- |
| `Select` | |
| `c.customer_id` | Aggregierter Besitzer |
| `SUM(o.order_total) as "Customer LTV"` | Aggregatvorgang (Spalte) |
| `FROM customers c` | Tabelle des Aggregateigentümers |
| `JOIN orders o` | Quelltabelle der Aggregation |
| `ON c.customer_id = o.customer_id` | Pfad |
| `WHERE o.status = 'success'` | Aggregatfilter |

Für die Einrichtung in [!DNL Commerce Intelligence] ist die Verwendung Ihres Data Warehouse-Managers erforderlich, mit dem Sie einen Pfad zwischen Ihrer `orders` und `customers` Tabelle erstellen und dann in der Tabelle Ihres Kunden eine Spalte mit dem Namen `Customer LTV` erstellen.

Erfahren Sie, wie Sie einen neuen Pfad zwischen dem `customers` und dem `orders` einrichten. Das Endziel besteht darin, eine neue aggregierte Spalte in der `customers` zu erstellen. Gehen Sie daher in Ihrer Data Warehouse zur `customers` Tabelle und klicken Sie auf **[!UICONTROL Create a Column** > **&#x200B; Definition auswählen &#x200B;**> **SUM]**.

Als Nächstes müssen Sie die Quelltabelle auswählen. Wenn ein Pfad zu Ihrer `orders` vorhanden ist, wählen Sie ihn einfach aus der Dropdown-Liste aus. Wenn Sie jedoch einen neuen Pfad erstellen, klicken Sie auf **[!UICONTROL Create new path]** . Daraufhin wird der folgende Bildschirm angezeigt:

![Neuen Pfad erstellen](../../assets/Create_new_path.png)

Hier müssen Sie die Beziehung zwischen den beiden Tabellen, die Sie verbinden möchten, sorgfältig prüfen. In diesem Fall sind potenziell `Many` Bestellungen mit `One` Kunden verknüpft. Daher wird die `orders` Tabelle auf der `Many` Seite aufgelistet, während die `customers` Tabelle auf der `One` Seite ausgewählt wird.

>[!NOTE]
>
>In [!DNL Commerce Intelligence] entspricht ein `path` einem `Join` in SQL.

Nachdem der Pfad gespeichert wurde, können Sie die Spalte `Customer LTV` erstellen! Siehe unten:

![](../../assets/Customer_LTV.gif)

Nachdem Sie nun die neue Spalte `Customer LTV` in Ihrer `customers` erstellt haben, können Sie mithilfe dieser Spalte eine [Metrikaggregation](#aggregate) erstellen (um beispielsweise den durchschnittlichen LTV pro Kunde zu ermitteln). Sie können auch die berechnete Spalte in einem Bericht `group by` oder `filter`, indem Sie vorhandene Metriken verwenden, die auf der `customers`-Tabelle basieren.

>[!NOTE]
>
>Für letzteres müssen Sie jedes Mal, wenn Sie eine neue berechnete Spalte erstellen, [die Dimension zu vorhandenen Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor sie als `filter` oder `group by` verfügbar ist.

Siehe [Erstellen berechneter Spalten](../data-warehouse-mgr/creating-calculated-columns.md) mit Ihrem Data Warehouse Manager.

## `Group By`

`Group By` Funktionen in Abfragen werden häufig in [!DNL Commerce Intelligence] als Spalte dargestellt, die zum Segmentieren oder Filtern eines visuellen Berichts verwendet wird. Sehen wir uns als Beispiel die `Total Revenue` Abfrage an, die Sie zuvor untersucht haben. Dieses Mal segmentieren Sie den Umsatz jedoch nach `coupon\_code`, um besser zu verstehen, welche Coupons den meisten Umsatz generieren.

Beginnen Sie mit der folgenden Abfrage:

| | |
|--- |--- |
| `SELECT coupon_code,` | Report `group by` |
| `SUM(order_total) as "Total Revenue"` | `Metric operation`(Spalte) |
| `FROM orders` | `Metric source` |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | `filter` |
| `AND created_at < '2016-12-01'` <br><br>`AND created_at >= '2016-09-01'` | `timestamp` (und Reporting-`time range`) |
| `GROUP BY coupon_code` | Report `group by` |

>[!NOTE]
>
>Der einzige Unterschied zu der Abfrage, mit der Sie vorher begonnen haben, ist das Hinzufügen des „coupon\_code“ als Gruppierung nach._

Mit derselben `Total Revenue`, die Sie zuvor erstellt haben, können Sie jetzt einen Umsatzbericht erstellen, der nach Couponcode segmentiert ist! Sehen Sie sich das folgende GIF an, das zeigt, wie Sie diesen visuellen Bericht einrichten, indem Sie Daten von September bis November betrachten:

![Umsatz nach Couponcode](../../assets/Revenue_by_coupon_code.gif)

## Formeln

Manchmal kann eine Abfrage mehrere Aggregationen umfassen, um die Beziehung zwischen verschiedenen Spalten zu berechnen. Sie können beispielsweise den durchschnittlichen Bestellwert in einer Abfrage auf zwei Arten berechnen:

* `AVG('order\_total')` ODER
* `SUM('order\_total')/COUNT('order\_id')`

Die frühere Methode beinhaltet die Erstellung einer neuen Metrik, die einen Durchschnitt in der `order\_total` Spalte durchführt. Die letztgenannte Methode kann jedoch direkt im Report Builder erstellt werden, vorausgesetzt, Sie haben bereits Metriken zur Berechnung der `Total Revenue` und `Number of orders` eingerichtet.

Gehen Sie einen Schritt zurück und sehen Sie sich die Gesamtabfrage für `Average order value` an:

| | |
|--- |--- |
| `SELECT` |  |
| `SUM(order_total) as "Total Revenue"` | `operation` (Spalte) |
| `COUNT(order_id) as "Number of orders"` | `operation` (Spalte) |
| `SUM(order_total)/COUNT(order_id) as "Average order value"` | `operation` (Spalte)/Metrikvorgang (Spalte) |
| `FROM orders` | `source` |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | `filter` |
| `AND created_at < '2016-12-01'`<br><br>`AND created_at >= '2016-09-01'` | Metrik-Zeitstempel (und Reporting-Zeitbereich) |

Nehmen wir nun an, Sie haben bereits Metriken eingerichtet, um die `Total Revenue` und `Number of orders` zu berechnen. Da diese Metriken vorhanden sind, können Sie einfach den `Report Builder` öffnen und eine Berechnung auf Anfrage mit der `Formula`-Funktion erstellen:

![AOV-Formel](../../assets/AOV_forumula.gif)

## Verpackung

Wenn Sie ein starker SQL-Benutzer sind und darüber nachdenken, wie Abfragen in [!DNL Commerce Intelligence] übersetzt werden, können Sie berechnete Spalten, Metriken und Berichte erstellen.

Zur schnellen Übersicht sehen Sie sich die unten stehende Matrix an. Dies zeigt das entsprechende [!DNL Commerce Intelligence] einer SQL-Klausel und wie sie mehreren Elementen zugeordnet werden kann, je nachdem, wie sie in der Abfrage verwendet wird.

## Commerce Intelligence-Elemente

| **`SQL Clause`** | **`Metric`** | **`Filter`** | **`Report group by`** | **`Report time frame`** | **`Path`** | **`Calculated column inputs`** | **`Source table`** |
|---|---|---|---|---|---|---|---|
| `SELECT` | X | - | X | - | - | X | - |
| `FROM` | - | - | - | - | - | - | X |
| `WHERE` | - | X | - | - | - | - | - |
| `WHERE` (mit Zeitelementen) | - | - | - | X | - | - | - |
| `JOIN...ON` | - | X | - | - | X | X | - |
| `GROUP BY` | - | - | X | - | - | - | - |
