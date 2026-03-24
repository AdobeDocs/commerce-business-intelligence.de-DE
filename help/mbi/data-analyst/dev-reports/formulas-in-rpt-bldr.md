---
title: Formeln in der Report Builder
description: Erfahren Sie, wie Formeln in der Report Builder verwendet werden können.
exl-id: 7a0ad07a-5bcc-474f-95bc-ccc2b74073b2
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: https://experienceleague.adobe.com/XxqMoKRPIKcRgh8HKa6z2IMp6WkiCVp2jhIbXFqcraU
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 544
ht-degree: 0%

---

# Formeln in der `Report Builder`

In der [`Report Builder`](../../tutorials/using-visual-report-builder.md) können Sie mit den [definierten Metriken“ in &#x200B;](../../data-user/reports/ess-manage-data-metrics.md) Konto leistungsstarke Visualisierungen erstellen. Durch die Kombination dieser Metriken in einer Formel können Sie zusätzliche Einblicke aus Ihren Daten gewinnen. Dieses Thema taucht ein in die Verwendung von Formeln im `Report Builder` - lasst uns einsteigen!

## Was ist ein `formula`? {#what}

In der `Report Builder` ist eine `formula` nur eine Kombination aus einer oder mehreren Metriken, die auf einer mathematischen Logik basieren. Ein typisches Beispiel sieht wie folgt aus:

![Formelbeispiel mit einer Berechnung in Report Builder](../../assets/formula-example.png)

In diesem Beispiel verwenden Sie eine `Number of orders metric (A)` und eine `Distinct buyers metric (B)`, um folgende Frage zu beantworten: Wie viele Bestellungen tätigen meine Käufer im Durchschnitt jeden Monat? Die Parameter der Formel sind:

* `Definition`: Hier wenden Sie Mathematik auf die Eingabemetriken an. In diesem Beispiel gibt die Division der Anzahl der Bestellungen durch die Anzahl der einzelnen Käufer Aufschluss über die durchschnittliche Anzahl der Bestellungen. Daher lautet die Definition (A/B).

* `Format`: Gibt Ihre Formel eine Zahl, einen Zeitraum oder einen Währungsbetrag zurück? Neben der Definition der Formel befindet sich ein Dropdown-Menü, mit dem Sie das Format der Rückgabe angeben können. In diesem Fall ist es eine Zahl.

* `Miscellaneous`: Zeitstempel, Gruppierungen, Perspektiven und Filter der Formel werden alle von den Eingabemetriken übernommen. Hier gibt es nichts zu tun!

## Wie kann ich `formulas` in meinen Berichten verwenden? {#how}

Nachdem Sie nun die Grundlagen behandelt haben, sehen Sie sich einige Beispiele an.

### Beispiel: Ich möchte herausfinden, wie viel Prozent meines Umsatzes auf Erstbestellungen entfallen.

![Verwendung von Formeln zur Ermittlung des Prozentsatzes des Umsatzes, der Erstbestellungen zugeordnet wird](../../assets/first_time_orders.gif)

In diesem Beispiel haben Sie die Metriken `Revenue` und `Revenue (first time orders)` verwendet. Indem Sie die `Revenue (first time orders)(B)` durch die `Revenue metric (A)` teilen und das Rückgabeformat auf `Percent` setzen, können Sie den Prozentsatz des Umsatzes ermitteln, der Erstbestellungen zugeordnet werden kann.

### Beispiel: Ich möchte wissen, wie der durchschnittliche Umsatz pro Bestellung ist, wenn ich eine `promo code` anbiete und nicht.

![Verwendung von Formeln zur Ermittlung des durchschnittlichen Umsatzes pro Bestellung mit und ohne Promo-Codes](../../assets/promo_code.gif)

In diesem Beispiel haben Sie die Metriken `Revenue` und `Number of orders` verwendet. Die Antwort auf diese Frage umfasst zwei Schritte: `Revenue (A)` durch die `Number of orders (B)` teilen und das Rückgabeformat auf `Currency` festlegen. Als Nächstes haben Sie nur zugelassen, dass das Formelergebnis (`Avg. Revenue per order`) angezeigt und die Ergebnisse nach `Promo code` gruppiert werden.

### Beispiel: Ich möchte den Vertrieb der UTM-Quellen meiner neuen Kunden wissen.

![Verwendung von Formeln zur Ermittlung der Verteilung der UTM-Quellen neuer Kunden](../../assets/distro.gif)

Um die Antwort auf diese Frage zu finden, sind einige Schritte erforderlich:

1. Zuerst haben Sie die `New Customers` Metrik hinzugefügt und dann nach `utm_source - all` gruppiert. Dies ist die Metrik `A` oder `New Customers (grouped)`.

1. Als Nächstes haben Sie die `New Customers (grouped)` dupliziert und sie auf die Verwendung einer unabhängigen Dimension festgelegt. Metrik `B` - `New customers (ungrouped)` - zeigt die Gesamtzahl der neuen Kunden an.

1. Nachdem Sie beide Metriken ausgeblendet haben, legen Sie für die Formeldefinition `A/B` fest. Das teilt die `New customers (grouped)` durch die `New Customers (ungrouped)`.

1. Als Nächstes legen Sie das Ergebnisformat auf `Percent` fest.

In diesem Beispiel haben Sie die `Stacked Columns` Perspektive verwendet, um die Ergebnisse nach Monat anzuzeigen. Auf diese Weise können wir die Verteilung neuer Kunden von Monat zu Monat vergleichen.

## Verpackung {#wrapup}

Ist Ihnen in den obigen Beispielen aufgefallen, dass die `timestamp`, `groupings`, `perspectives` und `filters` der Formel von den Eingabemetriken übernommen werden? Denken Sie daran, dass Formeln für die Verwendung von `perspectives` und [unabhängigen Zeitoptionen](../../tutorials/time-options-visual-rpt-bldr.md){: target="_blank"} verwendet werden können, genau wie Metriken.

Wenn Sie weitere Fragen zur Verwendung von Formeln in der `Report Builder` haben, wenden Sie [&#x200B; an den &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
