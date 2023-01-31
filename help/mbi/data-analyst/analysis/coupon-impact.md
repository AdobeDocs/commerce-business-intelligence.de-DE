---
title: Auswirkungen des Gutscheins analysieren
description: Erfahren Sie, wie Sie die Auswirkungen von Gutscheinen auf die Akquise und Kundenbindung analysieren können.
exl-id: b0619365-fa75-49b5-a393-87f3364a390f
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 0%

---

# Couponeffekt

Die Analyse, wie Kunden Ihre Gutscheine verwenden, bietet wichtige Einblicke in Ihr Geschäft. Insbesondere wird analysiert, wie Sie Kunden über Coupons gewinnen und binden. In diesem Artikel untersuchen wir Analysen, die Ihnen bei der Beantwortung der folgenden Fragen helfen können:

* Wie viele Kunden erwerben Sie über Coupons?
* Sind Kunden, die Gutscheine erworben haben, eher geneigt, Wiederholungskäufe zu tätigen als Kunden, die nicht über Gutscheine erworben wurden?
* Inwiefern unterscheidet sich der durchschnittliche Umsatz während der Lebensdauer zwischen den durch Gutscheine erworbenen Kunden und den nicht durch Gutscheine erworbenen Kunden?
* Machen Kunden, die über Gutscheine erworben wurden, Wiederholungskäufe mit Gutscheinen?

Um diese Fragen zu beantworten, konzentrieren wir uns auf [Vergleich von kupon-erworbenen Kunden mit nicht kupon-erworbenen Kunden](#compare), [Analyse von Details zu Erstbestellungen aus Coupon-Akquisen](#firstorder)und [Betrachten Sie die Attribute von Kunden, die Gutscheine in ihrer ersten Bestellung verwenden.](#attributes)

Fangen wir an!

## Vergleich von mit Gutscheinen erworbenen Kunden mit nicht mit Gutscheinen erworbenen Kunden {#compare}

Wenn Sie Analysen erstellen, die Ihre Couponakquise und -bindung untersuchen, sollten Sie die folgenden Metriken verwenden:

### Anzahl neuer Kunden

Diese Metrik zeigt Ihnen die Anzahl der mit Coupon erworbenen Kunden und der nicht mit Coupons erworbenen Kunden über die ganze Zeit. Auf diese Weise können Sie das Verhältnis der Kundenakquise über Gutscheine ermitteln.

### Durchschnittlicher Umsatz während der Lebensdauer

Diese Metrik zeigt Ihnen den durchschnittlichen Umsatz über die gesamte Lebensdauer von Kunden, die Gutscheine und andere Gutscheine erworben haben. Dies kann dabei helfen festzustellen, ob der Lebenszeitwert eines Kunden je nach Akquisetyp variiert.

### Anzahl wiederholter Bestellungen

Diese Metrik zeigt die Anzahl der Wiederholungsaufträge, die von beiden Arten von Kundenakquisen getätigt wurden. Auf diese Weise können Sie feststellen, ob weitere Folgeaufträge von durch Gutscheine erworbenen oder nicht durch Gutscheine erworbenen Kunden aufgegeben werden.

### Anzahl und Prozentsatz der Wiederholungen von Bestellungen mit Coupon

Zeigt die Anzahl der wiederholten Bestellungen mit einem angewendeten Coupon und den Prozentsatz der wiederholten Bestellungen mit einem Coupon an. Auf diese Weise können Sie feststellen, ob kupon-erworbene Kunden dazu neigen, mit einem Coupon mehr wiederkehrende Bestellungen zu tätigen als mit Nicht-Coupon erworbene Kunden, und ob kupon-erworbene Kunden bei ihren Folgebestellungen unverhältnismäßig stark Coupons verwenden.

Sehen wir uns einige Beispieldaten für die Kennzahlen für die Gutscheinakquise im Vergleich zu den Kennzahlen für die Nicht-Gutscheinakquise an:

| **Kundenakquise** | **Anzahl neuer Kunden** | **Durchschnittlicher Umsatz während der Lebensdauer** | **Anzahl wiederholter Bestellungen** | **Anzahl wiederholter Bestellungen mit Coupon** | **% der Wiederholungsaufträge mit Coupon** |
|-----|-----|-----|-----|-----|-----|
| Coupon | 1.206 | 356,91 $ | 2.570 | 1.248 | 48,56% |
| Nicht Coupon | 11.561 | $ 498.30 | 20.145 | 3.251 | 16,14 % |

{style=&quot;table-layout:auto&quot;}

Was können wir daraus nehmen? Sehen wir uns Folgendes an:

### Anzahl neuer Kunden

Im obigen Beispiel gibt es eine wesentlich größere Anzahl von Nicht-Coupon-Akquisitionen als Coupon-Akquise. Es gibt jedoch immer noch 1.206 Kunden, die über einen Gutschein erworben wurden, der andernfalls möglicherweise nicht zum Kunden geworden wäre.

### Durchschnittlicher Umsatz während der Lebensdauer

In diesem Beispiel haben Nicht-Gutscheinakquisitionen einen höheren durchschnittlichen Umsatz während der Lebensdauer als Coupon-Akquise. Dies bedeutet, dass Nicht-Coupon-Akquisitionen mehr wiederholte Käufe tätigen und/oder höhere Wertkäufe tätigen.

### Anzahl wiederholter Bestellungen

Die Anzahl der Wiederholungsaufträge für Nicht-Coupon-Akquise ist viel höher als die Anzahl der Coupon-Akquise. Dies wird erwartet, da es viele weitere Kunden gibt, die keinen Gutschein erworben haben.

### Anzahl wiederholter Bestellungen mit Coupon

Gleichermaßen ist die Anzahl wiederholter Bestellungen, die mit einem Coupon getätigt wurden, bei Nicht-Coupon-Akquisen höher.

## #Percent of repeat orders with coupon

Kunden, die keinen Gutschein erworben haben, haben einen wesentlich geringeren Prozentsatz von Wiederholungsbestellungen mit einem Coupon als Kunden mit Coupon. Somit wird bei kupon-erworbenen Kunden fast jeder zweite Wiederholungsauftrag mit einem Coupon belegt. In diesem Beispiel neigen Kunden, die Gutscheine erworben haben, dazu, Wiederholungskäufe mit Coupons zu tätigen.

## Analysieren von Details zu Erstbestellungen aus Coupon-Akquisen {#firstorder}

In diesem Abschnitt konzentrieren wir uns nur auf **erste Bestellungen aus Couponakquisitionen, segmentiert nach Coupon.** Wir verwenden diese Metriken in unserer Analyse:

### Anzahl der Bestellungen/Kunden

Diese Metrik zeigt die Anzahl der Erstbestellungen für jeden Gutschein oder die Anzahl der Kunden an, die diesen Gutschein in ihrer ersten Bestellung verwendet haben. Auf diese Weise kann festgestellt werden, ob ein bestimmter Gutschein mehr Erstkäufe als andere Gutscheine fördert.

### Bruttoeinnahmen

Diese Metrik zeigt den Umsatz an, den Sie mit einem bestimmten Gutschein erzielen, der in der ersten Bestellung eines Kunden verwendet wurde. Dieser Umsatz ist eine Berechnung der verkauften Artikel, bevor Rabatte gewährt werden.

### Rabatte aus Gutscheinen

Diese Metrik zeigt den Gesamtbetrag des Rabatts an, der aus den Gutscheinen gewährt wurde.

### Nettoeinnahmen

Diese Metrik zeigt den Umsatz an, den Sie mit einem bestimmten Gutschein erzielen, der in der ersten Bestellung eines Kunden verwendet wurde. Dieser Umsatz ist eine Berechnung der verkauften Artikel, nachdem alle Rabatte angewendet wurden. Es ist wichtig festzustellen, dass die Nettoeinnahmen ohne die Gutscheine möglicherweise nicht getätigt wurden.

### Durchschnittlicher Bestellwert

Diese Metrik zeigt den durchschnittlichen Bestellwert für einen bestimmten Gutschein an.

### Durchschnittliche Anzahl der Bestellungen über die Lebensdauer

Diese Metrik hilft bei der Bewertung der Treue und der durchschnittlichen Anzahl der Bestellungen, die von Kunden generiert wurden, die einen bestimmten Gutschein verwenden.

### Durchschnittlicher Umsatz während der Lebensdauer

Diese Metrik hilft bei der Bewertung der Treue und des durchschnittlichen Umsatzes, die von Kunden generiert werden, die einen bestimmten Gutschein verwenden. Achten Sie bei der Bewertung, ob Kunden, die Gutscheine verwenden, einen höheren Wert haben als andere, darauf, die Anzahl der Bestellungen zu berücksichtigen, in denen jeder Gutschein verwendet wurde, um sicherzustellen, dass Sie über eine erhebliche Stichprobengröße verfügen.

Sehen wir uns nun ein Beispiel an, in dem drei verschiedene Gutscheine für die Erstbestellung von Kunden verwendet werden:

| **Coupon** | **Erstbestellungen (FTO)** | **Bruttoeinnahmen aus FTO** | **Ermäßigungen für FTO** | **Nettoeinnahmen aus FTO** | **Durchschnittlicher Bestellwert für FTO** |
|-----|-----|-----|-----|-----|-----|
| **25 % Rabatt auf 100 USD oder mehr** | 56 | 8.531,04 $ | 2.132,76 $ | $ 6&#39;398.28 | 152,34 $ |
| **10 USD Rabatt** | 87 | $ 3&#39;707.07 | 426,10 $ | $ 3&#39;280.97 | 42,61 $ |
| **20 % Rabatt** | 145 | 10.975,05 $ | 2.195,01 $ | 8.780,04 $ | $ 75.69 |

{style=&quot;table-layout:auto&quot;}

Was können wir daraus nehmen? Erstens hatte der Gutschein &quot;20 % Rabatt&quot;die meisten Erstbestellungen. Die Anzahl der mit jedem Gutschein verknüpften Bestellungen kann jedoch von verschiedenen Faktoren abhängen, darunter:

* die Höhe der Werbung für jeden Gutschein.
* die Zeitdauer, für die die Gutscheine angeboten wurden.
* die Tageszeit/Woche/Monat/Jahr, zu der die Gutscheine angeboten wurden.
* die Saison, in der die Gutscheine je nach Geschäft angeboten wurden.

   **Beispiel:** Der Gutschein &quot;20% Rabatt&quot; wurde in den Sommermonaten angeboten, aber das Unternehmen verkauft Winterkleidung.
* die Einschränkungen für die Gutscheine.

   **Beispiel:** Der Gutschein &quot;10 % Rabatt&quot;wird nur Kunden angeboten, die einen Wintermantel in derselben Bestellung erwerben.

Die **Bruttoeinnahmen** für den Coupon &quot;25 % Rabatt von 100 $ oder mehr&quot;ist viel höher als der Bruttoumsatz für den &quot;10 off&quot;-Coupon. Der Gutschein für &quot;$10 off&quot;ist jedoch viel größer **Anzahl der Bestellungen**. Analysieren der **durchschnittlicher Bestellwert** bietet Einblicke in diese Unterschiede: Obwohl der Coupon &quot;25 % Rabatt von 100 Euro oder mehr&quot;weniger Bestellungen aufwies, liegt der durchschnittliche Bestellwert über dem Dreifachen des &quot;10-Rabatt&quot;-Coupons. Somit wird ein größerer Bruttoumsatz dem Coupon &quot;25 % Rabatt von 100 $ oder mehr&quot;zugeordnet.

Die **Rabatte** und **Nettoeinnahmen** für die Gutscheine &quot;25 % Rabatt von 100 USD oder mehr&quot;und &quot;20 % Rabatt&quot;sind wertmäßig. Auch wenn der durchschnittliche Bestellwert für &quot;25 % Rabatt von 100 $ oder mehr&quot;fast dem Doppelten des durchschnittlichen Bestellwerts für &quot;20 % Rabatt&quot;entspricht, hat der letztgenannte Coupon etwas weniger als das Dreifache der Anzahl von Bestellungen.

## Attribute von Kunden, die Gutscheine in ihrer ersten Bestellung verwenden {#attributes}

Nachdem wir uns nun die Bestellungen selbst angesehen haben, sollten wir uns die Kunden ansehen, die bei ihren ersten Bestellungen Coupons verwenden:

| **Erstbestellcoupon des Kunden** | **Anzahl der Kunden** | **Durchschnittliche Anzahl der Bestellungen über die Lebensdauer** | **Durchschnittlicher Umsatz während der Lebensdauer** |
|-----|-----|-----|-----|
| **25 % Rabatt auf 100 USD oder mehr** | 56 | 2,8 | 554,54 $ |
| **10 USD Rabatt** | 87 | 1,9 | 115,50 $ |
| **20 % Rabatt** | 145 | 1,3 | 103,75 $ |

{style=&quot;table-layout:auto&quot;}

Sie werden feststellen, dass die Anzahl der Erstbestellungen mit der Anzahl der Kunden für jeden Gutschein übereinstimmt. Dies ist sinnvoll, da jeder Kunde nur eine erste Bestellung haben kann.

Die größte Anzahl von Kunden wurde durch den &quot;20% Rabatt&quot;-Gutschein erworben. Diese Kunden haben jedoch die niedrigsten **durchschnittliche Lebensdauer der Bestellungen** und **Durchschnittlicher Umsatz während der Lebensdauer**; Im Allgemeinen tätigen die meisten Kunden, die Gutscheine erworben haben, keine Nachbestellungen. Darüber hinaus haben Kunden über das Coupon-Laufwerk &quot;25 % Rabatt von 100 Euro oder mehr&quot;einen höheren Wert erworben **durchschnittliche Lebensdauer der Bestellungen** und wiederum höher **Durchschnittlicher Umsatz während der Lebensdauer**. Im Allgemeinen kehren Benutzer, die über diesen Gutschein erworben wurden, zurück und tätigen weitere Käufe.

## Aufbrechen {#wrapup}

Es gibt eine Vielzahl von Analysen, die Sie erstellen können, um besser zu verstehen, wie Ihre Kunden Gutscheine verwenden. Haben Sie schon einmal darüber nachgedacht zu analysieren, wie Ihre Kunden Ihre Gutscheine verwenden oder wie lange es dauert, bis Gutscheine verwendet werden? Wie sieht es mit der Suche nach dem optimalen Rabattbetrag aus - welcher Betrag ermutigt Wiederholungskäufer, einen höheren durchschnittlichen Bestellwert und höheren Lebenszeitumsatz? Für Hilfe zu diesen Fragen, [Support kontaktieren](../../guide-overview.md).
