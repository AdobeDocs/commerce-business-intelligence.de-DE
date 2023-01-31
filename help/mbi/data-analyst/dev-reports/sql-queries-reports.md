---
title: SQL-Abfragen in übersetzen [!DNL MBI] Berichte
description: Erfahren Sie, wie SQL-Abfragen in berechnete Spalten und Metriken übersetzt werden, die Sie in [!DNL MBI].
exl-id: b3e3905f-6952-4f15-a582-bf892a971fae
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---

# SQL-Abfragen in MBI übersetzen

Haben Sie sich schon immer gefragt, wie SQL-Abfragen in die [berechnete Spalten](../data-warehouse-mgr/creating-calculated-columns.md), [Metriken](../../data-user/reports/ess-manage-data-metrics.md)und [Berichte](../../tutorials/using-visual-report-builder.md) Sie verwenden [!DNL MBI]? Wenn Sie ein starker SQL-Benutzer sind, sollten Sie wissen, wie SQL übersetzt wird in [!DNL MBI] ermöglicht Ihnen eine intelligentere Arbeit im [Data Warehouse Manager](../data-warehouse-mgr/tour-dwm.md) und das Beste aus dem [!DNL MBI] Plattform.

Am Ende dieses Artikels haben wir eine **Übersetzungsmatrix** für SQL-Abfrageklauseln und [!DNL MBI] -Elemente.

Zunächst wird eine allgemeine Abfrage untersucht:

|  |  |
|--- |--- |
| `SELECT` |  |
| `a,` | Bericht `group by` |
| `SUM(b)` | `Aggregate function` (Spalte) |
| `FROM c` | `Source` table |
| `WHERE` |  |
| `d IS NOT NULL` | `Filter` |
| `AND time < X`<br><br> `AND time >= Y` | Bericht `time frame` |
| `GROUP BY a` | Bericht `group by` |

In diesem Beispiel werden die meisten Übersetzungsfälle behandelt, es gibt jedoch einige Ausnahmen. Lassen Sie uns eintauchen, beginnend mit dem `aggregate` -Funktion übersetzt wird.

## Aggregat-Funktionen

Aggregatfunktionen (z. B. `count`, `sum`, `average`, `max`, `min`) in Abfragen entweder in folgender Form: **Metrikaggregationen** oder **Spaltenaggregationen** in [!DNL MBI]. Der Differenzierungsfaktor besteht darin, ob für die Aggregation ein Join erforderlich ist.

Sehen wir uns ein Beispiel für die oben genannten Punkte an.

## Metrikaggregationen {#aggregate}

Bei der Aggregation von `within a single table`. Beispielsweise wird die `SUM(b)` Aggregatfunktion aus der obigen Abfrage würde höchstwahrscheinlich durch eine Metrik dargestellt, die die Spalte summiert `B`. 

Sehen wir uns ein konkretes Beispiel an, wie ein `Total Revenue` Metriken können in [!DNL MBI]. Sehen Sie sich die unten stehende Abfrage an, um zu versuchen, zu übersetzen:

|  |  |
|--- |--- |
| `SELECT` |  |
| `SUM(order_total) as "Total Revenue"` | `Metric operation` (Spalte) |
| `FROM orders` | `Metric source` table |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | Metrik `filter` |
| `AND created_at < X`<br><br>`AND created_at >= Y` | Metrik `timestamp` (und Berichterstattung) `time range`) |

Navigieren zum Metrikaufbau durch Klicken auf **[!UICONTROL Manage Data** > ** Metriken **> **Neue Metrik erstellen]**, müssen wir zunächst die entsprechenden `source` -Tabelle, die in diesem Fall der `orders` Tabelle. Anschließend würde die Metrik wie folgt eingerichtet:

![Metrikaggregation](../../assets/Metric_aggregation.png)

## Spaltenaggregationen

Eine berechnete Spalte ist erforderlich, wenn eine Spalte aggregiert wird, die aus einer anderen Tabelle verbunden ist. So kann beispielsweise eine Spalte in der `customer` Tabelle mit `Customer LTV`, die den Gesamtwert aller mit diesem Kunden verbundenen Bestellungen im `orders` Tabelle.

Die Abfrage für diese Aggregation kann etwa wie folgt aussehen:

|  |  |
|--- |--- |
| `Select` |  |
| `c.customer_id` | Aggregat-Eigentümer |
| `SUM(o.order_total) as "Customer LTV"` | Aggregat-Vorgang (Spalte) |
| `FROM customers c` | Aggregat-Eigentümertabelle |
| `JOIN orders o` | Aggregations-Quelltabelle |
| `ON c.customer_id = o.customer_id` | Pfad |
| `WHERE o.status = 'success'` | Aggregat-Filter |

Einrichten des [!DNL MBI] erfordert die Verwendung Ihres Data Warehouse-Managers, in dem Sie einen Pfad zwischen Ihrem `orders` und `customers` und erstellen Sie dann eine neue Spalte mit dem Namen `Customer LTV` in der Tabelle Ihres Kunden.

Lassen Sie uns zunächst untersuchen, wie ein neuer Weg zwischen den `customers` und `orders`. Unser Ziel ist es, eine neue aggregierte Spalte im `customers` -Tabelle, also navigieren Sie zuerst zur `customers` in der Data Warehouse angezeigt werden, klicken Sie auf **[!UICONTROL Create a Column** > ** Definition auswählen **> **SUM]**.

Wählen Sie anschließend die Quelltabelle aus. Wenn bereits ein Pfad zu Ihrer `orders` -Tabelle aus, wählen Sie sie einfach aus der Dropdown-Liste aus. Wenn Sie jedoch einen neuen Pfad erstellen, klicken Sie auf **[!UICONTROL Create new path]** und Sie erhalten den folgenden Bildschirm:

![Neuen Pfad erstellen](../../assets/Create_new_path.png)

Hier müssen Sie die Beziehung zwischen den beiden Tabellen, die Sie verbinden wollen, sorgfältig überdenken. In diesem Fall gibt es `Many` Bestellungen, die mit `One` -Kunde, also `orders` ist auf der `Many` Seite, während die `customers` auf der `One` Seite.

>[!NOTE]
>
>In [!DNL MBI], *path* entspricht einem `Join` in SQL.

Nachdem der Pfad gespeichert wurde, können Sie alle neue `Customer LTV` column! Sehen Sie sich das folgende Beispiel an:

![](../../assets/Customer_LTV.gif)

Jetzt, da Sie die neue `Customer LTV` in der Spalte `customers` -Tabelle, können Sie eine [Metrikaggregation](#aggregate) die Verwendung dieser Spalte (z. B. um die durchschnittliche LTV-Rate pro Kunde zu ermitteln) oder einfach `group by` oder `filter` durch die berechnete Spalte in einem Bericht mit vorhandenen Metriken, die auf der `customers` Tabelle.

>[!NOTE]
>
>Für letztere müssen Sie jedes Mal, wenn Sie eine neue berechnete Spalte erstellen, [Dimension zu vorhandenen Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor sie als `filter` oder `group by`.

Siehe [berechnete Spalten erstellen](../data-warehouse-mgr/creating-calculated-columns.md) mit Ihrem Data Warehouse Manager.

## `Group By` Klauseln

`Group By` Funktionen in Abfragen werden häufig in [!DNL MBI] als Spalte zur Segmentierung oder Filterung eines visuellen Berichts. Beispiel: `Total Revenue` Abfrage, die wir zuvor erforscht haben, aber diesmal den Umsatz nach `coupon\_code` um ein besseres Verständnis davon zu gewinnen, welche Gutscheine den meisten Umsatz generieren.

Zuerst beginnen wir mit der folgenden Abfrage:

|  |  |
|--- |--- |
| `SELECT coupon_code,` | Bericht `group by` |
| `SUM(order_total) as "Total Revenue"` | `Metric operation`(Spalte) |
| `FROM orders` | `Metric source` table |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | Metrik `filter` |
| `AND created_at < '2016-12-01'` <br><br>`AND created_at >= '2016-09-01'` | Metrik `timestamp` (und Berichterstattung) `time range`) |
| `GROUP BY coupon_code` | Bericht `group by` |

>[!NOTE]
>
>Der einzige Unterschied zu der Abfrage, mit der wir zuvor begonnen haben, besteht darin, dass &quot;coupon\_code&quot;als Gruppe von hinzugefügt wird._

Verwenden des gleichen `Total Revenue` -Metrik, die wir zuvor erstellt haben, können wir nun unseren Bericht über den Umsatz erstellen, der nach Couponcode segmentiert ist! Sehen Sie sich das unten stehende GIF an, in dem gezeigt wird, wie dieser visuelle Bericht mit Daten von September bis November eingerichtet wird:

![Umsatz nach Couponcode](../../assets/Revenue_by_coupon_code.gif)

## Formeln

In einigen Fällen kann eine Abfrage mehrere Aggregationen umfassen, um die Beziehung zwischen getrennten Spalten zu berechnen. Sie können beispielsweise den durchschnittlichen Bestellwert in einer Abfrage auf zwei Arten berechnen:

* `AVG('order\_total')` ODER
* `SUM('order\_total')/COUNT('order\_id')`

Die frühere Methode würde die Erstellung einer neuen Metrik beinhalten, die einen Durchschnittswert für die `order\_total` Spalte. Die letztgenannte Methode kann jedoch direkt im ReportBuilder erstellt werden, vorausgesetzt, Sie verfügen bereits über Metriken zur Berechnung der `Total Revenue` und `Number of orders`.

Lassen Sie uns einen Schritt zurückgehen und die Gesamtabfrage für `Average order value`:

|  |  |
|--- |--- |
| `SELECT` |  |
| `SUM(order_total) as "Total Revenue"` | Metrik `operation` (Spalte) |
| `COUNT(order_id) as "Number of orders"` | Metrik `operation` (Spalte) |
| `SUM(order_total)/COUNT(order_id) as "Average order value"` | Metrik `operation` (Spalte) / Metrikvorgang(Spalte) |
| `FROM orders` | Metrik `source` table |
| `WHERE` |  |
| `email NOT LIKE '%@magento.com'` | Metrik `filter` |
| `AND created_at < '2016-12-01'`<br><br>`AND created_at >= '2016-09-01'` | Metrikzeitstempel (und Berichtszeitbereich) |

Nehmen wir auch an, dass bereits Metriken zur Berechnung der `Total Revenue` und `Number of orders`. Da diese Metriken bereits vorhanden sind, können wir einfach die `Report Builder` und erstellen Sie eine Ad-hoc-Berechnung mithilfe der `Formula` Funktion:

![AOV-Forumula](../../assets/AOV_forumula.gif)

## Aufbrechen

Wie wir am Anfang dieses Artikels erwähnt haben, wenn Sie ein starker SQL-Benutzer sind und darüber nachdenken, wie Abfragen in übersetzt werden [!DNL MBI] ermöglicht Ihnen die Erstellung berechneter Spalten, Metriken und Berichte.

Sehen Sie sich die folgende Matrix für einen schnellen Überblick an. Dies zeigt die Entsprechung einer SQL-Klausel [!DNL MBI] -Element und wie es mehreren Elementen zugeordnet werden kann, je nachdem, wie es in der Abfrage verwendet wird.

## MBI-Elemente

|**`SQL Clause`**|**`Metric`**|**`Filter`**|**`Report group by`**|**`Report time frame`**|**`Path`**|**`Calculated column inputs`**|**`Source table`**| |—|—|—|—|—|—|—|—|—| |`SELECT`|X|-|X|-|-|X|-|-| |`FROM`|-|-|-|-|-|-|X| |`WHERE`|-|X|-|-|-|-|-|-| |`WHERE` (mit Zeitelementen)|-|-|-|X|-|-|-| |`JOIN...ON`|-|X|-|-|X|X|-| |`GROUP BY`|-|-|X|-|-|-|-|-|
