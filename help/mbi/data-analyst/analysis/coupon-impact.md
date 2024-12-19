---
title: Analyse der Couponwirkung
description: Erfahren Sie, wie Sie die Auswirkungen von Coupons auf die Kundenakquise und -bindung analysieren können.
exl-id: b0619365-fa75-49b5-a393-87f3364a390f
role: Admin, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 1%

---

# Coupon-Auswirkung

Durch die Analyse der Verwendung Ihrer Gutscheine durch Kunden erhalten Sie einen wichtigen Einblick in Ihr Unternehmen. Insbesondere die Analyse der Kundenakquise und -bindung über Gutscheine. In diesem Thema werden Analysen vorgestellt, die Ihnen bei der Beantwortung folgender Fragen helfen können:

* Wie viele Kunden gewinnen Sie mit Gutscheinen?
* Tätigen Kundinnen und Kunden, die Coupons erwerben, mit höherer Wahrscheinlichkeit wiederholte Käufe als Kunden, die nicht über Coupons erworben werden?
* Wie unterscheidet sich der durchschnittliche Umsatz während der Lebensdauer zwischen Kunden, die Coupons erwerben, und Kunden, die nicht über Coupons erworben werden?
* Tätigen Kunden, die über Coupons erworben wurden, wiederholte Käufe mit Coupons?

Beantworten Sie diese Fragen, indem Sie sich auf [Vergleich von Coupon-erworbenen Kunden mit Nicht-Coupon-erworbenen Kunden](#compare), [Analyse der Details der ersten Bestellung aus Coupon-](#firstorder)) und [die Attribute von Kunden, die Coupons in ihrer ersten Bestellung verwenden.](#attributes)

Erste Schritte!

## Vergleich von durch Coupons erworbenen Kunden mit nicht durch Coupons erworbenen Kunden {#compare}

Wenn Sie Analysen erstellen, die Ihre Couponakquise und -bindung untersuchen, sollten Sie die folgenden Metriken verwenden:

### Anzahl neuer Kunden

Diese Metrik zeigt die Anzahl der mit und ohne Coupon akquirierten Kunden über den gesamten Zeitraum an. Auf diese Weise lässt sich das Verhältnis der Kundenakquise über Coupons ermitteln.

### Durchschnittlicher Lebensdauerumsatz

Diese Metrik zeigt den durchschnittlichen lebenslangen Umsatz von Kunden mit und ohne Coupon an. Auf diese Weise lässt sich feststellen, ob der Lebenszeitwert eines Kunden je nach Akquise-Typ variiert.

### Anzahl der Wiederholungsaufträge

Diese Metrik zeigt die Anzahl der Wiederholungsaufträge an, die von beiden Arten der Kundenakquise getätigt wurden. Auf diese Weise lässt sich feststellen, ob weitere Nachbestellungen von Kunden, die einen Coupon erworben haben oder nicht, aufgegeben werden.

### Anzahl und Prozentsatz der Wiederholungsaufträge mit Coupon

Dies zeigt die Anzahl der mit einem angewendeten Coupon ausgeführten Wiederholungsaufträge und den Prozentsatz der mit einem Coupon ausgeführten Wiederholungsaufträge. Auf diese Weise lässt sich feststellen, ob Kundinnen und Kunden, die einen Coupon erwerben, tendenziell mehr Wiederholungsaufträge mit einem Coupon ausführen als nicht mit Coupons erworbene Kunden und ob Kundinnen, die einen Coupon erworben haben, in ihren Folgeaufträgen überproportional Coupons verwenden.

Sehen Sie sich einige Beispieldaten für Couponakquise versus Nicht-Couponakquise-Metriken an:

| **Kundenakquise** | **Anzahl neuer Kunden** | **Durchschnittlicher Lebensdauerumsatz** | **Anzahl der Wiederholungsaufträge** | **Anzahl der Wiederholungsaufträge mit Coupon** | **% der Wiederholungsaufträge mit Coupon** |
|-----|-----|-----|-----|-----|-----|
| Coupon | 1.206 | 356,91 $ | 2.570 | 1.248 | 48,56 % |
| Gutscheinfrei | 11.561 | 498,30 $ | 20.145 | 3.251 | 16,14 % |

{style="table-layout:auto"}

Schauen Sie, was Sie daraus mitnehmen können:

### Anzahl neuer Kunden

Im obigen Beispiel gibt es eine viel größere Anzahl von Nicht-Coupon-Akquisitionen als Coupon-Akquisitionen. Es werden jedoch immer noch 1.206 Kunden über einen Coupon akquiriert, der ansonsten möglicherweise nicht zu Kunden geworden wäre.

### Durchschnittlicher Lebensdauerumsatz

In diesem Beispiel haben Nicht-Coupon-Akquisitionen einen höheren durchschnittlichen lebenslangen Umsatz als Coupon-Akquisitionen. Dies bedeutet, dass nichtkupongebundene Zukäufe häufiger wiederholte und/oder höherwertige Zukäufe tätigen.

### Anzahl der Wiederholungsaufträge

Die Anzahl der Wiederholungsaufträge für Nicht-Coupon-Akquisitionen ist viel höher als Coupon-Akquisitionen. Dies ist zu erwarten, da es viel mehr Kunden gibt, die keine Coupons erwerben.

### Anzahl der Wiederholungsaufträge mit Coupon

Ebenso ist die Anzahl der mit einem Coupon getätigten Wiederholungsaufträge bei Nicht-Coupon-Akquisitionen höher.

## Prozentsatz der wiederholten Bestellungen mit Coupon

Kunden, die keine Coupons erwerben, haben einen viel geringeren Prozentsatz an Wiederholungsaufträgen mit angewendetem Coupon als Kunden, die einen Coupon erwerben. Somit wird bei fast der Hälfte der Wiederholungsaufträge für Kundinnen und Kunden, die einen Coupon erwerben, ein Coupon angewendet. In diesem Beispiel neigen Kundinnen und Kunden, die Coupons erworben haben, dazu, wiederholte Käufe mit Coupons zu tätigen.

## Analysieren von Details erster Bestellung aus Couponakquisitionen {#firstorder}

Dieser Abschnitt konzentriert sich nur auf **erste Bestellungen aus Couponakquisitionen, segmentiert nach Coupons.** Verwenden Sie diese Metriken in Ihrer Analyse:

### Anzahl Bestellungen/Kunden

Diese Metrik zeigt die Anzahl der Erstbestellungen für jeden Coupon oder die Anzahl der Kunden, die diesen Coupon in ihrer ersten Bestellung verwendet haben. Auf diese Weise lässt sich feststellen, ob mit einem bestimmten Coupon mehr Erstkäufe gefördert werden als mit anderen Coupons.

### Bruttoumsatz

Diese Metrik zeigt den Umsatz an, den Sie mit einem bestimmten Coupon erzielen, der bei der ersten Bestellung eines Kunden verwendet wurde. Bei diesem Umsatz handelt es sich um eine Berechnung der verkauften Artikel, bevor Rabatte angewendet werden.

### Rabatte auf Gutscheine

Diese Metrik zeigt den gesamten Rabattbetrag an, der von den Gutscheinen angewendet wurde.

### Nettoumsatz

Diese Metrik zeigt den Umsatz an, den Sie mit einem bestimmten Coupon erzielen, der bei der ersten Bestellung eines Kunden verwendet wurde. Dieser Umsatz ist eine Berechnung der verkauften Artikel, nachdem alle Rabatte angewendet wurden. Es ist wichtig zu beachten, dass die Nettoeinnahmen möglicherweise nicht ohne die Coupons erzielt wurden.

### Durchschnittlicher Bestellwert

Diese Metrik zeigt den durchschnittlichen Bestellwert für einen bestimmten Coupon an.

### Durchschnittliche Anzahl der Bestellungen während der gesamten Lebensdauer

Diese Metrik hilft bei der Bewertung der Treue und der durchschnittlichen Anzahl der Bestellungen, die von Kunden generiert wurden, die einen bestimmten Coupon verwenden.

### Durchschnittlicher Lebensdauerumsatz

Diese Metrik hilft bei der Bewertung der Treue und des durchschnittlichen Umsatzes, die von Kunden generiert werden, die einen bestimmten Coupon verwenden. Berücksichtigen Sie bei der Bewertung, ob Kunden, die Coupons verwenden, höhere Werte als andere verwenden, die Anzahl der Bestellungen, in denen jeder Coupon verwendet wurde, um sicherzustellen, dass Sie über eine signifikante Stichprobengröße verfügen.

Sehen Sie sich jetzt ein Beispiel mit drei verschiedenen Coupons an, die für die Erstbestellung von Kunden verwendet werden:

| **Coupon** | **Erstbestellungen (FTO)** | **Bruttoeinnahmen aus FTO** | **Auf FTO angewendete Rabatte** | **Nettoeinnahmen aus FTO** | **Durchschnittlicher Bestellwert für FTO** |
|-----|-----|-----|-----|-----|-----|
| **25 % Rabatt auf 100 $ oder mehr** | 56 | 8 531,04 $ | 2 132,76 $ | 6 398,28 $ | 152,34 $ |
| **$ 10 Rabatt** | 87 | 3 707,07 $ | 426,10 $ | 3 280,97 $ | 42,61 $ |
| **20 % Rabatt** | 145 | 10 975,05 $ | 2 195,01 $ | 8 780,04 $ | 75,69 $ |

{style="table-layout:auto"}

Was kann man daraus lernen? Erstens war die Anzahl der Erstbestellungen mit dem „20% Rabatt“ am höchsten. Die Anzahl der mit jedem Coupon verbundenen Bestellungen kann jedoch aufgrund mehrerer Faktoren variieren, darunter:

* Der Anzeigenbetrag für jeden Coupon.
* Die Zeitdauer, für die die Coupons angeboten wurden.
* Die Zeit von Tag/Woche/Monat/Jahr, zu der die Gutscheine angeboten wurden.
* Die Saison, in der die Gutscheine angeboten wurden, je nach Geschäft.

  **Beispiel** Der „20% Rabatt“-Coupon wurde in den Sommermonaten angeboten, aber das Unternehmen verkauft Winterkleidung.
* Die Einschränkungen für die Coupons.

  **Beispiel** Der „10% Rabatt“-Gutschein wird nur Kunden angeboten, die einen Wintermantel in derselben Bestellung erwerben.

Der **Bruttoertrag** für den „25% Rabatt auf 100 $ oder mehr“-Coupon ist viel höher als der Bruttoertrag für den „10$ Rabatt“-Coupon. Der „10$ Rabatt“-Coupon hat jedoch eine viel größere **Anzahl an Bestellungen**. Die Analyse **durchschnittlichen Bestellwerts** bietet einen Einblick in diese Unterschiede. Obwohl der „25%-Rabatt von 100$ oder mehr“ weniger Bestellungen hatte, ist der durchschnittliche Bestellwert mehr als dreimal so hoch wie der des „10$-Rabatts“. Somit wird dem Coupon „25% Rabatt auf 100 Dollar oder mehr“ ein höherer Bruttoumsatz zugerechnet.

Die **Rabatte** und **Nettoumsatz** für die „25 % Rabatt auf 100 $ oder mehr“ und „20 % Rabatt“ sind wertmäßig nah. Obwohl der durchschnittliche Bestellwert für „25% Rabatt von 100 $ oder mehr“ nahe dem Doppelten des durchschnittlichen Bestellwerts für „20% Rabatt“ liegt, hat der letztgenannte Coupon etwas weniger als das Dreifache der Bestellanzahl.

## Attribute von Kunden, die Gutscheine in ihrer ersten Bestellung verwenden {#attributes}

Nachdem Sie sich nun die Bestellungen selbst angesehen haben, sehen Sie sich die Kunden an, die Coupons für ihre ersten Bestellungen verwenden:

| **Erstbestellgutschein des Kunden** | **Anzahl der Kunden** | **Durchschnittliche Anzahl der Bestellungen während der gesamten Lebensdauer** | **Durchschnittlicher Lebensdauerumsatz** |
|-----|-----|-----|-----|
| **25 % Rabatt auf 100 $ oder mehr** | 56 | 2,8 | 554,54 $ |
| **$ 10 Rabatt** | 87 | 1,9 | 115,50 $ |
| **20 % Rabatt** | 145 | 1,3 | 103,75 $ |

{style="table-layout:auto"}

Sie werden feststellen, dass die Anzahl der Erstbestellungen der Anzahl der Kunden für jeden Coupon entspricht. Dies ist sinnvoll, da jeder Kunde nur eine Erstbestellung haben kann.

Die größte Anzahl von Kunden wurde mit dem „20% Rabatt“-Coupon erworben. Diese Kunden haben jedoch die niedrigste **durchschnittliche Anzahl der Bestellungen** und **durchschnittlicher Umsatz über die gesamte Lebensdauer**; im Allgemeinen tätigen die meisten Coupon-Kunden keine Wiederholungsbestellungen. Darüber hinaus führen Kundinnen und Kunden, die mit dem „25 % Rabatt von 100 USD oder mehr“ erworben haben, zu einer höheren **durchschnittliche Anzahl der Bestellungen** und damit zu einem höheren **durchschnittlichen Umsatz während der**. Im Allgemeinen kommen Benutzer, die über diesen Coupon erworben wurden, in der Regel zurück und tätigen mehr wiederholte Käufe.

## Verpackung {#wrapup}

Es gibt eine Vielzahl von Analysen, die Sie erstellen können, um besser zu verstehen, wie Ihre Kunden Gutscheine verwenden. Haben Sie schon einmal darüber nachgedacht zu analysieren, wie Ihre Kunden Ihre Coupons verwenden oder wie lange es dauert, bis Coupons verwendet werden? Wie sieht es mit der Suche nach dem optimalen Rabattbetrag aus - welcher Betrag ermutigt Wiederholungskäufer, einen höheren durchschnittlichen Bestellwert und einen höheren Lebensdauerumsatz? Wenn Sie Hilfe bei diesen Fragen benötigen, wenden [ sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
