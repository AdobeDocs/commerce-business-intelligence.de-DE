---
title: Analysieren der Couponnutzung
description: Erfahren Sie, wie Sie die Couponnutzung bei der Kundenakquise und -bindung analysieren können.
exl-id: d4d1393f-1695-43f2-980a-84525f84031e
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 0%

---

# Couponnutzung

Haben Sie sich jemals gefragt, wie sich das Anbieten von Gutscheinen auf Ihr Unternehmen auswirkt? Möchten Sie wissen, welche Coupons die Leistung unterstützen oder beeinträchtigen? In diesem Thema werden Analysen untersucht, die Ihnen ein gutes Bild der Couponnutzung Ihrer Kunden vermitteln, indem sie die folgenden Fragen beantworten:

* Wie viele Kunden verwenden Coupons?
* Wie viele Gutscheine werden verwendet?
* Wie hoch ist Ihr Umsatz vor und nach der Anwendung der Gutscheine?
* Wie hoch ist der durchschnittliche Bestellwert vor und nach der Couponanwendung?
* Welche Kunden ziehen Sie mit Coupons an?

## Empfohlene Kennzahlen {#metrics}

Erwägen Sie bei der Analyse der Couponnutzung die Verwendung ([oder Erstellung](../../data-user/reports/ess-manage-data-metrics.md) dieser Metriken:

### Anzahl der Bestellungen

Diese Metrik zeigt die Anzahl der Bestellungen mit und ohne Coupons im Zeitverlauf an. Dies zeigt, ob und wie oft Kundinnen und Kunden Ihre Gutscheine verwenden und wie sich dies im Laufe der Zeit ändert.

### Bruttoumsatz

Diese Metrik zeigt den Bruttoumsatz an, den Sie mit Bestellungen erzielen, die einen bestimmten Coupon enthalten. Die Bruttoeinnahmen sind eine Berechnung des vollen Preises der verkauften Artikel, bevor Rabatte angewendet werden. Auf diese Weise lässt sich feststellen, welche Coupons mit den höchsten und niedrigsten Bruttoeinnahmen verbunden sind.

### Rabatte auf Gutscheine

Mit dieser Metrik kann der gesamte Rabattbetrag angezeigt werden, der von den Coupons angewendet wurde. Es ist wichtig zu beachten, dass diese Bestellungen möglicherweise nicht ohne die Coupons erfolgt sind.

### Nettoumsatz

Diese Metrik zeigt den Nettoumsatz an, den Sie mit Bestellungen erzielen, die einen bestimmten Coupon enthalten. Der Nettoumsatz ist eine Berechnung des Preises der verkauften Artikel nach Anwendung aller Rabatte. Auf diese Weise lässt sich feststellen, welche Coupons mit dem höchsten und niedrigsten Nettoumsatz verbunden sind.

### Prozent abgezinst

Dies zeigt den Anteil der Bruttoeinnahmen, der durch Rabatte ausgeglichen wird. Bei Gutscheinen, die einen prozentualen Rabatt bieten, ist dieser Wert bereits bekannt (z. B. 10 % Rabatt). Dennoch bietet diese Maßnahme insight und eine Vergleichsmethode für Coupons, die einen festen Dollarrabatt darstellen.

### Durchschnittlicher Nettoauftragswert

Diese Kennzahl zeigt den durchschnittlichen Bestellwert an, wenn ein Coupon angewendet wird. Sie können analysieren, ob Bestellungen mit Coupons durchgängig einen geringeren Bestellwert haben als Bestellungen ohne Coupons.

### Durchschnittlicher Bestellrabatt

Dies zeigt den durchschnittlichen Dollarwert, der von jeder Bestellung abgezinst wird, bei der Coupons angewendet werden. Dies zeigt die Differenz zwischen dem durchschnittlichen Nettoauftragswert und dem durchschnittlichen Bruttoauftragswert an.

### Unterschiedliche Käufer

Diese Metrik zeigt die Anzahl der einzelnen Käufer an, die einen bestimmten Coupon verwenden.

### Durchschnittlicher Lebensdauerumsatz

Diese Metrik hilft bei der Bewertung der Treue und des durchschnittlichen Umsatzes, die von Kunden generiert werden, die einen bestimmten Coupon verwenden. Wenn Sie beurteilen, ob Kunden, die Coupons verwenden, einen höheren Wert als andere haben, sollten Sie die Anzahl der unterschiedlichen Käufer in jeder Kategorie berücksichtigen, um sicherzustellen, dass Sie über eine signifikante Stichprobengröße verfügen.

## Beispiel {#example}

Nachdem Sie nun wissen, welche Metriken Sie betrachten sollten, sehen Sie sich ein Beispiel an, das drei verschiedene Gutscheine umfasst: 10 % Rabatt, 20 $ Rabatt auf 100 $ oder mehr und 10 $ Rabatt.

| **Coupon** | **Anzahl der Bestellungen** | **Bruttoumsatz** | **Bruttorabatte auf Coupons** | **Nettoumsatz** | **Rabatt in Prozent** |
|-----|-----|-----|-----|-----|-----|
| **10 % Rabatt** | 79 | 19 757,02 $ | 1 975,70 $ | 17 781,32 $ | 10,00 % |
| **$20 Rabatt auf $100+** | 101 | 13 928,91 $ | 2 020,00 $ | 11 908,91 $ | 14,50 % |
| **$ 10 Rabatt** | 201 | 14 542,35 $ | 2 010,00 $ | 12 532,35 $ | 13,82 % |

{style="table-layout:auto"}


| **Coupon** | **Durchschnitt Nettoauftragswert** | **Durchschnitt Bestellrabatt** | **Unterschiedliche Käufer** | **Durchschnitt Lebensdauerumsatz** |
|-----|-----|-----|-----|-----|
| **10 % Rabatt** | 225,08 $ | 25,01 $ | 79 | 361,50 $ |
| **$20 Rabatt auf $100+** | 117,91 $ | 20,00 $ | 95 | 218,76 $ |
| **$ 10 Rabatt** | 62,35 $ | 10,00 $ | 199 | 84,27 $ |

{style="table-layout:auto"}

## Was kann man daraus mitnehmen?

Etwa 80 Bestellungen wurden mit dem „10%-Rabatt“-Coupon aufgegeben, 100 Bestellungen mit dem „20$-Rabatt von 100$ oder mehr“-Coupon und 200 Bestellungen mit dem „10$-Rabatt“-Coupon. Die **Anzahl der Bestellungen** die mit jedem Coupon verbunden sind, kann aufgrund mehrerer Faktoren variieren, darunter:

* Die Zeitdauer, für die die Coupons angeboten wurden.
* Die Zeit von Tag/Woche/Monat/Jahr, zu der die Gutscheine angeboten wurden.
* Die Saison, in der die Gutscheine angeboten wurden, je nach Geschäft. Beispiel:
* Der „10% Rabatt“-Gutschein wurde während der Sommermonate angeboten, aber das Unternehmen verkauft Winterkleidung.

* Die Einschränkungen für die Coupons. Beispiel:
* Der „10$-Rabatt“ wird nur neuen Kunden angeboten.
* Der „10% Rabatt“-Gutschein wird nur Kunden angeboten, die einen Wintermantel in derselben Bestellung erwerben.

* Das typische Kaufverhalten des Kunden.

Während die **Bruttorabatte** für alle drei Coupons ähnlich sind (rund 2.000 US-Dollar), ist die Anzahl der Bestellungen für jeden Coupon unterschiedlich. Durch die Analyse der Rabatte pro Bestellung lassen sich die Gründe für die unterschiedlichen Zahlen erklären. Der „10%-Rabatt“-Coupon hat die geringste Anzahl an Bestellungen, aber einen **durchschnittlichen Bestellrabatt** von etwa 25 US-Dollar. Obwohl dieser Coupon nur eine geringe Anzahl von Bestellungen aufweist, führt sein hoher durchschnittlicher Diskontwert dazu, dass sich sein Bruttodiskontbetrag auf fast 2.000 US-Dollar beläuft.

**Brutto- und Nettoumsatz** liefern eine Gesamtübersicht über den vollen Wert der mit jedem Coupon verbundenen Bestellungen. Dieses Gesamtbild vermittelt jedoch kein Verständnis für die verschiedenen Verhaltensweisen der einzelnen Coupons. Wenn Sie sich die Auftragsbasis ansehen, können Sie sehen, dass der Coupon mit einem Rabatt von 10 % einen hohen **durchschnittlichen Nettoauftragswert** aufweist, was wiederum zu seinem hohen **Nettoumsatz** führt.

Auf der anderen Seite hat der „10% Rabatt“-Coupon einen hohen durchschnittlichen Diskontwert ($25.01), aber den niedrigsten **Prozent**. Dies ist sinnvoll, wenn Sie den durchschnittlichen Nettoauftragswert von 225,08 US-Dollar berücksichtigen. Der „10% Rabatt“-Coupon hat einen kleinen prozentualen Rabatt auf einen großen durchschnittlichen Nettobestellwert, sodass der durchschnittliche Bestellrabatt ein großer Betrag ist.

Sehen Sie sich für **Coupons die** Einzelkäufer **und den durchschnittlichen** an. Der „10% Rabatt“-Coupon hat dieselbe Anzahl von Bestellungen wie einzelne Käufer. Dies kann darauf zurückzuführen sein, dass jeder Kunde auf einen Coupon beschränkt ist. Auf der anderen Seite haben die Gutscheine für &quot;$20 Rabatt von $100 oder mehr“ und &quot;$10 Rabatt“ weniger verschiedene Käufer als die Anzahl der Bestellungen, was bedeutet, dass einige Kunden diese Gutscheine mehrmals verwendet haben.

Der durchschnittliche Umsatz während der gesamten Lebensdauer eines Coupons ist höher als der entsprechende Wert **durchschnittlicher Nettobestellwert**. Dies bedeutet, dass entweder Kunden wiederholt Einkäufe getätigt haben und/oder ihr Bestellwert viel höher war als der durchschnittliche Nettobestellwert.

## Was kann ich noch analysieren? {#otheranalyses}

Insight Die in diesem Thema erwähnten Analysen können Ihnen wertvolle Informationen darüber liefern, wie Ihre Kunden Ihre Gutscheine verwenden. Es gibt jedoch eine Vielzahl anderer Analysen, mit denen Sie etwas tiefer gehen können.

**Sie können die Kundenakquise aus Coupons analysieren.**

Welche Gutscheine regen Kunden dazu an, Bestellungen aufzugeben? Ziehen diese Gutscheine einmalige Käufer an oder fördern sie die Kundentreue (d. h. Kunden, die wiederholt kaufen)?

**Sie können die Zeit analysieren, die Ihre Kunden benötigen, um Ihre Gutscheine zu verwenden.**

Werden Ihre Gutscheine am Tag ihrer Veröffentlichung verwendet oder verstreichen ein bis zwei Wochen, bevor die meisten Ihrer Kunden sie verwenden?

**Sie könnten den optimalen Rabattbetrag entdecken, der die Kundenloyalität und den Gesamtwert erhöht.**

Welcher Rabattbetrag begünstigt Bestandskäufer, einen höheren durchschnittlichen Bestellwert und einen höheren Lebensdauerumsatz?

Die Beantwortung dieser Fragen gibt Ihnen Einblicke in Ihre Kunden, ihr Verhalten und die Coupons, die Ihrem Unternehmen den größten Nutzen bieten.
