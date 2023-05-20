---
title: Formeln im Report Builder
description: Erfahren Sie, wie Formeln im Report Builder verwendet werden können.
exl-id: 7a0ad07a-5bcc-474f-95bc-ccc2b74073b2
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Formeln im `Report Builder`

Im [`Report Builder`](../../tutorials/using-visual-report-builder.md), können Sie leistungsstarke Visualisierungen mithilfe der [definierte Metriken](../../data-user/reports/ess-manage-data-metrics.md) in Ihrem Konto. Durch die Kombination dieser Metriken mit einer Formel können Sie zusätzliche Einblicke aus Ihren Daten gewinnen. In diesem Thema wird erläutert, wie Formeln im `Report Builder` - springen Sie ein!

## Was ist ein `formula`? {#what}

Im `Report Builder`, `formula` ist nur eine Kombination aus einer oder mehreren Metriken basierend auf einer mathematischen Logik. Ein typisches Beispiel sieht wie folgt aus:

![](../../assets/formula-example.png)

In diesem Beispiel verwenden Sie eine `Number of orders metric (A)` und `Distinct buyers metric (B)`und das Ziel besteht darin, die Frage zu beantworten: Wie viele Bestellungen tätigen meine Käufer jeden Monat? Die Formel enthält folgende Parameter:

* `Definition`: Hier wenden Sie die Mathematik auf die Eingabemetriken an. In diesem Beispiel teilt uns die Division der Anzahl der Bestellungen durch die Anzahl unterschiedlicher Käufer die durchschnittliche Anzahl der Bestellungen mit. Daher lautet die Definition (A/B).

* `Format`: Gibt Ihre Formel eine Zahl, einen Zeitraum oder einen Währungsbetrag zurück? Neben der Definition der Formel befindet sich ein Dropdown-Menü, in dem Sie das Format der Rückgabe angeben können. In diesem Fall ist es eine Zahl.

* `Miscellaneous`: Der Zeitstempel, die Gruppierungen, Perspektiven und Filter der Formel werden durch die Eingabemetriken vererbt. Hier gibt es nichts zu tun!

## Wie kann ich `formulas` in meinen Berichten? {#how}

Nachdem Sie nun die Grundlagen behandelt haben, sehen Sie sich einige Beispiele an.

### Beispiel: Ich möchte herausfinden, welcher Prozentsatz meines Umsatzes Erstbestellungen zugeordnet werden kann.

![Verwenden von Formeln zur Ermittlung des Prozentsatzes des Umsatzes, der Erstbestellungen zugeordnet wird](../../assets/first_time_orders.gif)

In diesem Beispiel haben Sie die Variable `Revenue` und `Revenue (first time orders)` Metriken. Durch Division der `Revenue (first time orders)(B)` Metrik nach `Revenue metric (A)` und legen Sie das Rückgabeformat auf `Percent`können Sie den Prozentsatz des Umsatzes ermitteln, der Erstbestellungen zugeordnet werden kann.

### Beispiel: Ich möchte wissen, was der durchschnittliche Umsatz pro Bestellung ist, wenn ich dies tue, und keine Angebote für `promo code`.

![Verwenden von Formeln zur Ermittlung des durchschnittlichen Umsatzes pro Bestellung mit und ohne Angebotscodes](../../assets/promo_code.gif)

In diesem Beispiel haben Sie die Variable `Revenue` und `Number of orders` Metriken. Die Antwort auf diese Frage umfasst zwei Schritte - die Aufteilung `Revenue (A)` durch `Number of orders (B)` und legen Sie das Rückgabeformat auf `Currency`. Als Nächstes wurde nur das Formelergebnis zugelassen (`Avg. Revenue per order`), um die Ergebnisse anzuzeigen und zu gruppieren, indem Sie `Promo code`.

### Beispiel: Ich möchte die Verteilung der UTM-Quellen meiner neuen Kunden erfahren.

![Verwendung von Formeln zur Suche nach UTM-Quellen neuer Kunden](../../assets/distro.gif)

Die Beantwortung dieser Frage umfasst einige Schritte:

1. Zuerst haben Sie die `New Customers` Metrik und anschließend gruppiert nach `utm_source - all`. Dies ist eine Metrik `A`oder `New Customers (grouped)`.

1. Als Nächstes haben Sie die `New Customers (grouped)` und legen Sie fest, dass eine unabhängige Dimension verwendet werden soll. Metrik `B` - `New customers (ungrouped)` - zeigt die Gesamtzahl neuer Kunden an.

1. Nachdem Sie beide Metriken ausgeblendet haben, setzen Sie die Formeldefinition auf `A/B`. Dadurch wird die `New customers (grouped)` durch `New Customers (ungrouped)`.

1. Als Nächstes legen Sie das Ergebnisformat auf `Percent`.

In diesem Beispiel haben Sie die Variable `Stacked Columns` um die Ergebnisse nach Monat anzuzeigen. Dadurch können wir den Vertrieb neuer Kunden von Monat zu Monat vergleichen.

## Aufbrechen {#wrapup}

Haben Sie in den obigen Beispielen bemerkt, dass die Formel `timestamp`, `groupings`, `perspectives`und `filters` von den Eingabemetriken vererbt werden? Beachten Sie, dass Formeln zur Verwendung von `perspectives` und [unabhängige Zeitoptionen](../../tutorials/time-options-visual-rpt-bldr.md){: target=&quot;_blank&quot;}, genau wie Metriken.

Wenn Sie weitere Fragen zur Verwendung von Formeln im `Report Builder`, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
