---
title: Analyse des Rückkaufverhaltens von Kunden
description: Erfahren Sie, wie Sie das Rückkaufverhalten von Kunden analysieren können.
exl-id: 62666d08-5240-4f19-bf8e-e5b2d79a25c4
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# Rückkaufverhalten des Kunden

Wenn Sie mehr als ein Produkt anbieten, fragen Sie sich wahrscheinlich, wie sich Kunden, die ein bestimmtes Produkt erwerben, im Laufe der Zeit anders verhalten als andere Kunden. In diesem Thema werden Analysen untersucht, die Ihnen bei der Beantwortung der folgenden Fragen helfen können.

Unter Kunden, die einen *bestimmten Artikel* kaufen,

* Wie hoch ist die Wahrscheinlichkeit, dass sie einen weiteren Kauf tätigen?
* Wie lange dauert es, bis sie einen weiteren Kauf tätigen?
* Wie viele Bestellungen können Kunden im Durchschnitt kurz- oder langfristig aufgeben?
* Wie hoch ist der durchschnittliche Umsatz, den Kunden kurz-/langfristig erzielen?

## Empfohlene Kennzahlen

Beim Erstellen von Analysen zur Rückkaufaktivität von Kunden empfiehlt Adobe die Verwendung der folgenden Metriken:

### Wiederholungsreihenwahrscheinlichkeit

Diese Kennzahl ist definiert als die Gesamtzahl der Wiederholungsaufträge, als Prozentsatz der Gesamtaufträge. Mit anderen Worten, dies ist die Wahrscheinlichkeit, dass auf eine Bestellung eine andere Bestellung folgt. Diese Kennzahl identifiziert Artikel, die Kunden wahrscheinlich dazu verleiten werden, zu Ihrem Geschäft zurückzukehren.

### Durchschnittliche Anzahl der aufgegebenen Bestellungen

Dadurch wird das Kaufverhalten Ihrer Kunden deutlich, insbesondere wie viele Bestellungen Ihre Kunden in einem bestimmten Zeitraum aufgegeben haben. Sie können diese Kennzahl einschränken, um das Verhalten der Kunden kurz-, mittel- oder langfristig zu ermitteln. Einige Produkte können Kunden ermutigen, kurzfristig häufige Käufe zu tätigen, während andere die langfristige Kundentreue beeinflussen können. Wenn diese Zahl für einen Artikel höher ist als für andere Artikel, würde dies darauf hindeuten, dass Personen, die diesen Artikel kaufen, diejenigen sind, die zu Ihrem Geschäft zurückkehren.

### Durchschnittlicher Umsatz über die Kundenlebensdauer

Mit dieser Metrik können Sie nachvollziehen, ob Kunden, die bestimmte Artikel erwerben, im Laufe ihres Lebenszyklus wertvoller sind. Wenn diese Zahl für einen Artikel höher ist als für andere Artikel zu ähnlichen Preisen, würde dies darauf hindeuten, dass Ihre höherwertigen Kunden dazu neigen, diesen Artikel zu kaufen.

### Zeit bis zur nächsten Bestellung

Diese Kennzahl zeigt die Bestellhäufigkeit des Kunden an oder die Zeit, die der Kunde zum erneuten Bestellen benötigt. Wenn die Zeit bis zur nächsten Bestellung für einen Artikel kürzer ist als für andere Artikel, würde dies darauf hindeuten, dass Personen, die diesen Artikel kaufen, eher zurückkommen.

## Beispiel von heute: Kaffeeprodukte

Beachten Sie dabei die oben genannten Metriken. Sehen Sie sich ein Beispiel an, das Kaffeeprodukte betrifft.

| **Produktname** | **Wahrscheinlichkeit der Wiederholungsreihenfolge** | **Durchschn. Lebensdauer der Bestellungen** | **Durchschn. Lebensdauerumsatz** | **Mediane Zeit bis zur nächsten Bestellung** |
|-----|-----|-----|-----|-----|
| Kaffeebrüher mit einer Tasse | 94,98 % | 7,92 | 549,82 $ | 57,01 Tage |
| Kaffeekapseln | 93,82 % | 8,68 | 479,98 $ | 63,48 Tage |
| Kaffeebohnen | 41,92 % | 6,07 | 99,82 $ | 27,31 Tage |

{style="table-layout:auto"}

Nun, da Sie Ihre Daten haben, was bedeutet dies für jede Ihrer Metriken?

### Wiederholungsreihenwahrscheinlichkeit

In diesem Beispiel ist die Wiederholungsreihenwahrscheinlichkeit - oder die Wahrscheinlichkeit, dass einer Bestellung eine andere folgt - für die Kaffeebrüher und Kaffeekapseln mit einer Tasse viel höher als für die Kaffeebohnen.

Da Kunden, die den Brauer kaufen, sich in Zukunft „verpflichtet“ fühlen, die dazugehörigen Kapseln zu kaufen, ist dies sinnvoll. Ebenso haben die Kunden, die Kapseln gekauft haben, einen Brauer, der mit den Kapseln kompatibel ist. Kaffeebohnen sind jedoch nicht spezifisch für eine bestimmte Brauerei.

### Durchschnittliche Anzahl der Bestellungen während der gesamten Lebensdauer

Auf der Grundlage der oben genannten Daten können Sie sehen, dass Personen, die den Brauer oder die Kapseln kaufen, im Durchschnitt mehr Käufe in ihrem Leben getätigt haben als Kunden, die Kaffeebohnen gekauft haben.

### Durchschnittlicher Umsatz über die Kundenlebensdauer

Kunden, die die Brauerei erwerben, erzielen den höchsten durchschnittlichen Umsatz während der gesamten Lebensdauer, was sinnvoll ist, da die Kosten der Brauerei in dieser Maßnahme enthalten sind. Kunden, die Kaffeebohnen kaufen, kaufen dagegen in der Regel nur preiswerte Artikel.

### Zeit bis zur nächsten Bestellung

Von den Kunden, die Kaffeekapseln gekauft haben, bestellt die Hälfte in etwa zwei Monaten eine Nachbestellung. Unter den Kunden, die Kaffeebohnen gekauft haben, bestellt jedoch die Hälfte innerhalb eines Monats eine Wiederholungsbestellung. Dies könnte daran liegen, dass Personen, die Kapseln bestellen, entweder (1) nicht so viel Kaffee trinken oder (2) Massenbestellungen aufgeben (z. B. Kaffee für zwei Monate in einer Bestellung).

## Welche anderen Analysen kann ich erstellen?

Mithilfe der in diesem Thema beschriebenen Metriken können Sie auch andere nützliche Rückkaufanalysen erstellen. Sie können beispielsweise auch sehen, wie Kunden **denselben Artikel)**, z. B. wenn sie regelmäßig Nachfüllungen kaufen. Kapseln und Kaffeebohnen können regelmäßig zurückgekauft werden, aber es wäre unerwartet, wenn Kunden die Kaffeebrüher immer wieder kaufen würden. Wenn sich Ihr Unternehmen auf Nachfüllungen oder die Wiederauffüllung der Lagerbestände konzentriert, wäre diese Analyse hilfreich.

Neben der Analyse des Rückkaufverhaltens Ihrer Kunden können Sie auch Analysen erstellen, die sich mit der Kundenloyalität befassen. Analyse der Muster bei der Kundenabwanderung: Wo verlassen Ihre Kunden Ihre Website und kommen nicht zurück? Wie schnell passiert das?

Nachdem Sie erkannt haben, warum eine Abwanderung stattfindet, können Sie Ihre Analyse verwenden, um eine `reactivation` Kampagne zu erstellen. Mithilfe dieser Daten können Sie Benutzer identifizieren, die inaktiv geworden sind, wie lange es seit ihrem letzten Besuch gewesen ist, was ihr letzter Kauf war usw. Auf diese Weise können Sie umsetzbare Entscheidungen treffen, die Ihre Kundinnen und Kunden dazu anregen, zurückzukehren.

Um Hilfe bei der Analyse zu erhalten, [den Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).
