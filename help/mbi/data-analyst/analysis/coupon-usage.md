---
title: Nutzung von Gutscheinen analysieren
description: Erfahren Sie, wie Sie die Nutzung von Gutscheinen beim Akquise und Kundenbindung analysieren.
exl-id: d4d1393f-1695-43f2-980a-84525f84031e
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 0%

---

# Nutzung des Gutscheins

Sie fragen sich je, wie das Anbieten von Coupons Ihr Geschäft beeinflusst? Möchten Sie wissen, welche Coupons die Performance unterstützen oder beeinträchtigen? In diesem Thema werden Analysen untersucht, die Ihnen einen guten Überblick über die Nutzung von Coupons Ihrer Kunden verschaffen, indem Sie diese Fragen beantworten:

* Wie viele Kunden verwenden Coupons?
* Wie viele Coupons werden verwendet?
* Wie hoch ist Ihr Umsatz vor und nach der Anwendung von Coupons?
* Wie hoch ist der durchschnittliche Bestellwert vor und nach der Anwendung von Coupons?
* Was für Kunden ziehen Sie mit Coupons an?

## Empfehlungen für Metriken {#metrics}

Bei der Analyse der Couponnutzung sollten Sie die folgenden Metriken verwenden ([oder ](../../data-user/reports/ess-manage-data-metrics.md) erstellen):

### Anzahl Bestellungen

Diese Metrik zeigt die Anzahl der Bestellungen mit und ohne Gutscheine im Zeitverlauf an. Dies zeigt, ob und wie oft Kunden Ihre Gutscheine verwenden und wie sich dies im Laufe der Zeit ändert.

### Bruttoeinnahmen

Diese Metrik zeigt den Bruttoumsatz an, den Sie aus Bestellungen mit einem bestimmten Coupon erzielen. Der Bruttoumsatz ist eine Berechnung des vollen Preises der verkauften Artikel, bevor Abschläge angewendet werden. Auf diese Weise können Sie feststellen, welche Gutscheine dem höchsten und dem niedrigsten Bruttoeinkommen zugeordnet sind.

### Rabatte aus Gutscheinen

Diese Metrik kann Ihnen den gesamten Rabattbetrag anzeigen, der aus den Gutscheinen angewendet wurde. Es ist wichtig zu beachten, dass diese Aufträge möglicherweise nicht ohne die Gutscheine erfolgt sind.

### Nettoeinnahmen

Diese Metrik zeigt den Nettoumsatz an, den Sie aus Bestellungen erzielen, die einen bestimmten Coupon enthalten. Der Nettoumsatz ist eine Berechnung des Preises der verkauften Artikel nach Anwendung aller Rabatte. Auf diese Weise können Sie feststellen, welche Gutscheine dem höchsten und dem niedrigsten Nettoumsatz zugeordnet sind.

### Prozent diskontiert

Dies zeigt den Anteil des Bruttoumsatzes, der durch Rabatte ausgeglichen wird. Für Gutscheine, die einen prozentualen Rabatt bieten, ist dieser Wert bereits bekannt (z. B. 10 % Rabatt). Trotzdem bietet diese Maßnahme Einblicke und eine Vergleichsmethode für Gutscheine, die einen festen Dollarrabatt darstellen.

### Durchschnittlicher Netto-Bestellwert

Diese Kennzahl zeigt den durchschnittlichen Bestellwert bei Anwendung eines Gutscheins an. Sie können analysieren, ob Bestellungen mit Coupons durchgängig einen geringeren Bestellwert haben als Bestellungen ohne Coupons.

### Durchschnittlicher BestellRabatt

Dies zeigt den durchschnittlichen Dollarwert, abgezinst von jeder Bestellung, in der Coupons angewendet werden. Dies zeigt die Differenz zwischen dem durchschnittlichen Netto-Bestellwert und dem durchschnittlichen Bruttoauftragswert.

### Unique Buyer

Diese Metrik zeigt die Anzahl unterschiedlicher Käufer an, die einen bestimmten Gutschein verwenden.

### Durchschnittlicher Umsatz während der Lebensdauer

Diese Metrik hilft bei der Bewertung der Treue und des durchschnittlichen Umsatzes, die von Kunden generiert werden, die einen bestimmten Gutschein verwenden. Achten Sie bei der Bewertung, ob Kunden, die Gutscheine verwenden, einen höheren Wert haben als andere, darauf, die Anzahl unterschiedlicher Käufer in jeder Kategorie zu berücksichtigen, um sicherzustellen, dass Sie über eine erhebliche Stichprobengröße verfügen.

## Beispiel {#example}

Nun, da Sie wissen, welche Metriken Sie sich ansehen sollten, sehen Sie sich ein Beispiel mit drei verschiedenen Gutscheinen an - 10 % Rabatt, 20 USD Rabatt von 100 USD oder mehr und 10 USD Rabatt.

| **Coupon** | **Anzahl der Bestellungen** | **Bruttoumsatz** | **Bruttorabatte aus Coupons** | **Nettoumsatz** | **Prozent discount** |
|-----|-----|-----|-----|-----|-----|
| **10% Rabatt** | 79 | 19.757,02 $ | $ 1&#39;975.70 | 17.781,32 $ | 10,00 % |
| **$20 von $100+** | 101 | 13.928,91 $ | 2.020,00$ | 11.908,91 $ | 14,50 % |
| **$10 off** | 201 | 14.542,35 $ | 2.010,00$ | 12.532,35 $ | 13,82% |

{style="table-layout:auto"}


| **Coupon** | **Durchschnittl. Netto-Bestellwert** | **Durchschnittl. Bestellrabatt** | **Unique Buyer** | **Durchschnittl. Lebensdauerumsatz** |
|-----|-----|-----|-----|-----|
| **10% Rabatt** | 225,08 $ | 25,01 $ | 79 | 361,50 $ |
| **$20 von $100+** | 117,91 $ | 20,00$ | 95 | 218,76 $ |
| **$10 off** | 62,35 $ | 10,00$ | 199 | 84,27 $ |

{style="table-layout:auto"}

## Was kannst du davon nehmen?

Ungefähr 80 Bestellungen wurden mit dem Gutschein &quot;10 % Rabatt&quot;, 100 Bestellungen mit dem Coupon &quot;20 € Rabatt von 100 € oder mehr&quot;und 200 Bestellungen mit dem Coupon &quot;10 € Rabatt&quot;aufgegeben. Die mit jedem Gutschein verknüpfte **Anzahl der Bestellungen** kann von verschiedenen Faktoren abhängen, darunter:

* die Zeitdauer, für die die Gutscheine angeboten wurden.
* die Tageszeit/Woche/Monat/Jahr, zu der die Gutscheine angeboten wurden.
* die Saison, in der die Gutscheine je nach Unternehmen angeboten wurden. Beispiel:
* Der &quot;10% Rabatt&quot;-Gutschein wurde in den Sommermonaten angeboten, aber das Unternehmen verkauft Winterkleidung.

* die Einschränkungen für die Gutscheine. Beispiel:
* Der &quot;10-Rabatt&quot;-Gutschein wird nur neuen Kunden angeboten.
* Der Gutschein &quot;10 % Rabatt&quot;wird nur Kunden angeboten, die einen Wintermantel in derselben Bestellung erwerben.

* das typische Kaufverhalten des Kunden.

Während die **Brutto-Rabatte** für alle drei Gutscheine ähnlich sind (rund 2.000 $), unterscheidet sich die Anzahl der Bestellungen für jeden Gutschein. Die Analyse von Rabatten auf der Basis einzelner Bestellungen hilft, die Gründe für diese widersprüchlichen Zahlen zu erläutern. Der Gutschein &quot;10 % Rabatt&quot;hat die geringste Anzahl von Bestellungen, aber einen durchschnittlichen Bestellrabatt **von etwa 25 USD.** Obwohl dieser Gutschein eine geringe Anzahl von Bestellungen aufweist, führt sein hoher durchschnittlicher Rabattwert dazu, dass sein Bruttoabsatzbetrag bei etwa 2.000 Dollar liegt.

**Brutto- und Nettoumsatz** geben einen Überblick über den Gesamtwert der mit jedem Gutschein verknüpften Bestellungen. Dieses Gesamtbild vermittelt jedoch kein Verständnis der unterschiedlichen Verhaltensweisen, die mit den einzelnen Gutscheinen verbunden sind. Wenn Sie sich eine Bestellbasis ansehen, können Sie sehen, dass der &quot;10%-ige&quot;Coupon einen hohen **durchschnittlichen Nettoauftragswert** aufweist, was wiederum zu seinem hohen **Nettoumsatz** führt.

Auf der anderen Seite weist der Gutschein &quot;10% Rabatt&quot;einen hohen durchschnittlichen Rabattwert ($25,01) auf, der niedrigste **Prozent Rabatt**. Dies ist sinnvoll, wenn Sie den durchschnittlichen Netto-Bestellwert von 225,08 US-Dollar berücksichtigen. Der &quot;10% Rabatt&quot;-Gutschein weist einen kleinen prozentualen Rabatt auf einen großen durchschnittlichen Nettoauftragswert auf, sodass der durchschnittliche Nachlass für Bestellungen ein großer Betrag ist.

Sehen Sie sich die **einzelnen Käufer** und den **durchschnittlichen Umsatz während der Lebensdauer** für jeden Gutschein an. Der Gutschein &quot;10 % Rabatt&quot;weist dieselbe Anzahl von Bestellungen auf wie unterschiedliche Käufer. Dies könnte darauf zurückzuführen sein, dass jeder Kunde auf einen Gutschein beschränkt ist. Auf der anderen Seite haben die Gutscheine &quot;$20 von $100 oder mehr&quot;und &quot;$10 off&quot;weniger unterschiedliche Käufer als die Anzahl der Bestellungen, was bedeutet, dass einige Kunden diese Gutscheine mehrmals verwendet haben.

Für den durchschnittlichen Umsatz während der Lebensdauer können Sie sehen, dass der durchschnittliche Umsatz für jeden Gutschein über dem entsprechenden Wert für **durchschnittliche Nettoaufträge** liegt. Dies bedeutet, dass entweder Kunden wiederholt Käufe getätigt haben und/oder ihr Bestellwert viel höher war als der durchschnittliche Netto-Bestellwert.

## Was kann ich sonst noch analysieren? {#otheranalyses}

Die in diesem Thema erwähnten Analysen geben Ihnen wertvolle Einblicke in die Verwendung Ihrer Gutscheine durch Ihre Kunden. Es gibt jedoch eine Vielzahl weiterer Analysen, die Ihnen erlauben, ein wenig tiefer zu gehen.

**Sie können Ihre Kundenakquise aus Gutscheinen analysieren.**

Welche Coupons ermutigen Kunden, Bestellungen aufzunehmen? Sind diese Gutscheine für einmalige Käufer attraktiv oder fördern sie die Kundenloyalität (d. h. Kunden, die wiederholte Käufe tätigen)?

**Sie können die Zeit analysieren, die Ihre Kunden benötigen, um Ihre Gutscheine zu verwenden.**

Werden Ihre Gutscheine am Tag ihrer Veröffentlichung verwendet oder verstreichen ein oder zwei Wochen, bevor die meisten Ihrer Kunden sie verwenden?

**Sie können den optimalen Rabattbetrag ermitteln, der die Kundenloyalität und den Gesamtwert erhöht.**

Welchen Rabatt ermuntert wiederkehrende Käufer, einen höheren durchschnittlichen Bestellwert und einen höheren Lebenszeitumsatz?

Durch die Beantwortung dieser Fragen erhalten Sie Einblicke in Ihre Kunden, ihr Verhalten und die Gutscheine, die Ihrem Unternehmen den größten Nutzen bringen.
