---
title: Analysieren des Kundenrückkaufverhaltens
description: Erfahren Sie, wie Sie das Verhalten von Kunden bei der Rücknahme analysieren.
exl-id: 62666d08-5240-4f19-bf8e-e5b2d79a25c4
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# Kundenrückkaufverhalten

Wenn Sie mehr als ein Produkt anbieten, fragen Sie sich wahrscheinlich, wie sich Kunden, die ein bestimmtes Produkt kaufen, im Laufe der Zeit anders verhalten als andere Kunden. In diesem Artikel untersuchen wir Analysen, die Ihnen bei der Beantwortung der folgenden Fragen helfen können:

Von Kunden, die eine *spezifisches Element*,

* Wie wahrscheinlich ist es, dass sie einen weiteren Kauf tätigen?
* Wie lange dauert es, bis sie einen weiteren Kauf tätigen?
* Wie viele Bestellungen haben Kunden im Schnitt kurz-/langfristig aufgegeben?
* Welchen durchschnittlichen Umsatz erzielen Kunden kurz-/langfristig?

## Empfohlene Metriken

Bei der Erstellung von Kundenanalysen zur Neukauf-Aktivität empfehlen wir die Verwendung der folgenden Metriken:

### Wiederholungsreihenwahrscheinlichkeit

Diese Kennzahl ist definiert als die Gesamtzahl der wiederkehrenden Bestellungen in Prozent der Gesamtbestellungen. Mit anderen Worten, dies ist die Wahrscheinlichkeit, dass eine Bestellung von einer anderen Bestellung gefolgt wird. Diese Kennzahl identifiziert Elemente, die Kunden wahrscheinlich dazu verleiten, zu Ihrem Geschäft zurückzukehren.

### Durchschnittliche Anzahl der aufgegebenen Bestellungen

Dies zeigt das Kaufverhalten Ihrer Kunden, insbesondere die Anzahl der Bestellungen, die Ihre Kunden über einen bestimmten Zeitraum aufgegeben haben. Sie können diese Maßnahme beschränken, um das Verhalten der Kunden kurz-, mittel- oder langfristig zu sehen. Einige Produkte können Kunden dazu ermutigen, kurzfristig häufige Käufe zu tätigen, während andere die langfristige Loyalität eines Kunden beeinflussen können. Wenn diese Zahl für einen Artikel höher ist als für andere Artikel, würde dies darauf hindeuten, dass Personen, die diesen Artikel kaufen, diejenigen sind, die zu Ihrem Geschäft zurückkehren.

### Durchschnittlicher Umsatz während der Kundenlebensdauer

Mit dieser Metrik können Sie erkennen, ob Kunden, die bestimmte Artikel kaufen, im Laufe ihrer Lebensdauer wertvoller sind. Wenn diese Zahl für einen Artikel höher ist als für andere Artikel mit ähnlichen Preisen, würde dies darauf hindeuten, dass Ihre Kunden mit höherem Wert dazu neigen, diesen Artikel zu kaufen.

### Zeit bis zur nächsten Bestellung

Diese Kennzahl zeigt die Bestellfrequenz des Kunden oder die Zeit an, die es dauert, bis der Kunde erneut bestellt wird. Wenn die Zeit bis zur nächsten Bestellung für einen Artikel kürzer ist als für andere Artikel, würde dies darauf hindeuten, dass Personen, die diesen Artikel kaufen, dazu neigen, früher zurückzukommen.

## Das heutige Beispiel: Kaffeeprodukte

Beachten Sie die oben genannten Metriken. Sehen wir uns ein Beispiel für Kaffeeprodukte an.

| **Produktname** | **Wiederholungsreihenwahrscheinlichkeit** | **Durchschnittliche Anzahl der Bestellungen über die Lebensdauer** | **Durchschnittlicher Umsatz während der Lebensdauer** | **Mittlere Zeit bis nächste Bestellung** |
|-----|-----|-----|-----|-----|
| Kaffeebierwanne für eine Tasse | 94,98% | 7,92 | 549,82 $ | 57.01 Tage |
| Kaffeekapseln | 93,82% | 8,68 | $ 479.98 | 63.48 Tage |
| Kaffeebohnen | 41,92% | 6,07 | 99,82 $ | 27.31 Tage |

{style=&quot;table-layout:auto&quot;}

Nachdem wir nun über unsere Daten verfügen, sollten wir uns ansehen, was dies für jede unserer Metriken bedeuten könnte.

### Wiederholungsreihenwahrscheinlichkeit

In diesem Beispiel ist die Wiederholungsbestellwahrscheinlichkeit - oder die Wahrscheinlichkeit, dass eine Bestellung von einer anderen Bestellung gefolgt wird - für die Kaffeehausen und Kaffeekapseln viel höher als für die Kaffeebohnen.

Da sich Kunden, die die Brauerei kaufen, verpflichtet fühlen, in Zukunft die entsprechenden Kapseln zu erwerben, ist dies sinnvoll. Ebenso haben die Kunden, die Kapseln gekauft haben, einen Brauer, der mit den Kapseln kompatibel ist. Kaffeebohnen sind jedoch für bestimmte Brauereien nicht spezifisch.

### Durchschnittliche Anzahl der Bestellungen über die Lebensdauer

Auf der Grundlage der oben genannten Daten können wir feststellen, dass Personen, die die Brauerei oder Kapseln kaufen, im Durchschnitt mehr Käufe getätigt haben als Kunden, die Kaffeebohnen gekauft haben.

### Durchschnittlicher Umsatz während der Kundenlebensdauer

Kunden, die die Brauerei erwerben, haben den höchsten durchschnittlichen Umsatz während der Lebensdauer; Dies ist sinnvoll, da die Kosten der Brauerei in diese Maßnahme einbezogen werden. Im Gegensatz dazu kaufen Kunden, die Kaffeebohnen kaufen, normalerweise nur kostengünstige Artikel.

### Zeit bis zur nächsten Bestellung

Bei Kunden, die Kaffeekapseln gekauft haben, kann die Hälfte innerhalb von 2 Monaten eine Wiederholungsbestellung tätigen. Bei Kunden, die Kaffeebohnen gekauft haben, kann die Hälfte jedoch innerhalb von etwa 1 Monat eine erneute Bestellung tätigen. Dies kann daran liegen, dass Menschen, die Kapseln bestellen, entweder (1) nicht so viel Kaffee trinken oder (2) Bestellungen in loser Schüttung aufgeben (z. B. indem sie zwei Monate Kaffee in einer Bestellung kaufen).

## Welche anderen Analysen kann ich erstellen?

Mithilfe der in diesem Artikel beschriebenen Metriken können Sie auch weitere nützliche Repkaufanalyse erstellen. Beispielsweise können wir auch sehen, wie Kunden zurückkaufen **dasselbe Element** - wenn sie beispielsweise regelmäßig Nachfüllungen kaufen. Kapseln und Kaffeebohnen können regelmäßig neu gekauft werden, es wäre jedoch unerwartet, wenn Kunden den Kaffee-Brauer erneut kaufen würden. Wenn sich Ihr Unternehmen auf Nachbearbeitung oder Wiederaufstockung konzentriert, wäre diese Analyse äußerst nützlich.

Zusätzlich zur Analyse des Kaufverhaltens Ihrer Kunden können Sie auch Analysen erstellen, die sich auf die Kundenloyalität beziehen. Erwägen Sie die Analyse von Mustern in der Kundenabwanderung - wo verlassen Ihre Kunden Ihre Site und kommen nicht zurück? Wie schnell ist das passiert?

Nachdem Sie ermittelt haben, warum die Abwanderung stattfindet, können Sie Ihre Analyse verwenden, um eine `reactivation` Kampagne. Mithilfe dieser Daten können Sie Benutzer identifizieren, die inaktiv geworden sind, wie lange es seit ihrem letzten Besuch ist, was ihr letzter Kauf war usw. Auf diese Weise können Sie umsetzbare Entscheidungen treffen, die Ihre Kunden zur Rückkehr bewegen.

Hilfe zur Analyse: [Support kontaktieren](../../guide-overview.md).
