---
title: Formeln im Report Builder
description: Erfahren Sie, wie Formeln im Report Builder verwendet werden können.
exl-id: 7a0ad07a-5bcc-474f-95bc-ccc2b74073b2
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Formeln im `Report Builder`

In der [`Report Builder`](../../tutorials/using-visual-report-builder.md) können Sie leistungsstarke Visualisierungen mithilfe der [definierten Metriken](../../data-user/reports/ess-manage-data-metrics.md) in Ihrem Konto erstellen. Durch die Kombination dieser Metriken mit einer Formel können Sie zusätzliche Einblicke aus Ihren Daten gewinnen. In diesem Thema erfahren Sie, wie Formeln in der `Report Builder` verwendet werden können - springen Sie ein!

## Was ist ein `formula`? {#what}

Im `Report Builder` ist ein `formula` nur eine Kombination aus einer oder mehreren Metriken, die auf einer mathematischen Logik basieren. Ein typisches Beispiel sieht wie folgt aus:

![](../../assets/formula-example.png)

In diesem Beispiel verwenden Sie einen `Number of orders metric (A)` und einen `Distinct buyers metric (B)`, und das Ziel besteht darin, die Frage zu beantworten: Wie hoch ist die durchschnittliche Anzahl von Bestellungen, die meine Käufer jeden Monat tätigen? Die Formel enthält folgende Parameter:

* `Definition`: Hier wenden Sie die Mathematik auf die Eingabemetriken an. In diesem Beispiel teilt uns die Division der Anzahl der Bestellungen durch die Anzahl unterschiedlicher Käufer die durchschnittliche Anzahl der Bestellungen mit. Daher lautet die Definition (A/B).

* `Format`: Gibt Ihre Formel eine Zahl, einen Zeitraum oder einen Währungsbetrag zurück? Neben der Definition der Formel befindet sich ein Dropdown-Menü, in dem Sie das Format der Rückgabe angeben können. In diesem Fall ist es eine Zahl.

* `Miscellaneous`: Der Zeitstempel, die Gruppierungen, Perspektiven und Filter der Formel werden alle von den Eingabemetriken übernommen. Hier gibt es nichts zu tun!

## Wie kann ich `formulas` in meinen Berichten verwenden? {#how}

Nachdem Sie nun die Grundlagen behandelt haben, sehen Sie sich einige Beispiele an.

### Beispiel: Ich möchte herausfinden, welcher Prozentsatz meines Umsatzes Erstbestellungen zugeordnet werden kann.

![Verwenden von Formeln zur Ermittlung des Prozentsatzes des Umsatzes, der Erstbestellungen zugeordnet wird](../../assets/first_time_orders.gif)

In diesem Beispiel haben Sie die Metriken `Revenue` und `Revenue (first time orders)` verwendet. Indem Sie die Metrik `Revenue (first time orders)(B)` durch die Metrik `Revenue metric (A)` dividieren und das Rückgabeformat auf `Percent` setzen, können Sie den Prozentsatz des Umsatzes ermitteln, der Erstbestellungen zugeordnet werden kann.

### Beispiel: Ich möchte wissen, was der durchschnittliche Umsatz pro Bestellung ist, wenn ich das tue, und keine `promo code` anbieten.

![Formeln zum Auffinden des durchschnittlichen Umsatzes pro Bestellung mit und ohne Angebotscodes verwenden](../../assets/promo_code.gif)

In diesem Beispiel haben Sie die Metriken `Revenue` und `Number of orders` verwendet. Die Antwort auf diese Frage umfasst zwei Schritte: die Division von `Revenue (A)` durch den `Number of orders (B)` und die Festlegung des Rückgabeformats auf `Currency`. Als Nächstes haben Sie nur zugelassen, dass das Formelergebnis (`Avg. Revenue per order`) die Ergebnisse mit `Promo code` anzeigt und gruppiert.

### Beispiel: Ich möchte die Verteilung der UTM-Quellen meiner neuen Kunden erfahren.

![Verwenden von Formeln zur Suche nach der Verteilung der UTM-Quellen neuer Kunden](../../assets/distro.gif)

Die Beantwortung dieser Frage umfasst einige Schritte:

1. Zuerst haben Sie die Metrik `New Customers` hinzugefügt und dann nach `utm_source - all` gruppiert. Dies sind die Metriken `A` oder `New Customers (grouped)`.

1. Als Nächstes haben Sie die Metrik &quot;`New Customers (grouped)`&quot;dupliziert und so eingestellt, dass sie eine unabhängige Dimension verwendet. Metrik `B` - `New customers (ungrouped)` - zeigt die Gesamtanzahl neuer Kunden an.

1. Nachdem Sie beide Metriken ausgeblendet haben, setzen Sie die Formeldefinition auf `A/B`. Dadurch wird die `New customers (grouped)` durch die `New Customers (ungrouped)` geteilt.

1. Als Nächstes legen Sie das Ergebnisformat auf `Percent` fest.

In diesem Beispiel haben Sie die Perspektive `Stacked Columns` verwendet, um die Ergebnisse pro Monat anzuzeigen. Dadurch können wir den Vertrieb neuer Kunden von Monat zu Monat vergleichen.

## Aufwischen {#wrapup}

Haben Sie in den obigen Beispielen bemerkt, dass die Formeln `timestamp`, `groupings`, `perspectives` und `filters` von den Eingabemetriken übernommen werden? Denken Sie daran, dass Formeln zur Verwendung von `perspectives` und [unabhängigen Zeitoptionen](../../tutorials/time-options-visual-rpt-bldr.md){: target=&quot;_blank&quot;} verwendet werden können, genau wie dies Metriken können.

Wenn Sie weitere Fragen zur Verwendung von Formeln in `Report Builder` haben, kontaktieren Sie [den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
