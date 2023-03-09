---
title: Analysieren von Wiederholwahrscheinlichkeitsabfall und Abwanderung
description: Erfahren Sie, wie die Zeit zwischen Bestellungen verfällt und wann mit einer Abwanderung der Kunden zu rechnen ist.
exl-id: ea26052d-ac74-43b7-a4a6-977800d4c719
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Wiederholungswahrscheinlichkeitsverfall und Abwanderung

Wenn ein Teil Ihres Umsatzes aus wiederholten Käufen stammt, ist Ihnen der enorme Wert einer treuen Kundenbasis wahrscheinlich bekannt. Zu diesem Zweck ist es wichtig zu verstehen, wie viel Zeit zwischen Bestellungen vergeht und wann mit einer Abwanderung der Kunden zu rechnen ist.

In diesem Thema werden die Analysen untersucht, die Ihnen bei der Beantwortung der folgenden Fragen helfen können:

* Wie hoch ist die Wahrscheinlichkeit, dass ein Kunde einen weiteren Kauf tätigt?
* Wie variiert die Wahrscheinlichkeit einer Wiederholung der Bestellung je nach der Zeit seit dem letzten Kauf des Kunden?
* Wann sollte ein Kunde berücksichtigt werden? Wann sollte also eine Reaktivierungskampagne starten?

## Empfohlene Metriken

Bei der Analyse des Rückgangs und der Abwanderung von Wiederholungswahrscheinlichkeiten sollten Sie erwägen, ([oder Gebäude](../../data-user/reports/ess-manage-data-metrics.md)) diese Metriken:

### anfängliche Wiederholungsreihenwahrscheinlichkeit

Diese Kennzahl ist definiert als die Gesamtzahl der wiederkehrenden Bestellungen in Prozent der Gesamtbestellungen. Anders ausgedrückt: Dies ist die Wahrscheinlichkeit, dass eine Bestellung von einer anderen Bestellung gefolgt wird. Wenn diese Wahrscheinlichkeit über 50 Prozent liegt, bedeutet dies, dass mehr als die Hälfte aller Bestellungen von einer nachfolgenden Bestellung gefolgt wird.

### Wiederholungsbestellwahrscheinlichkeit seit Bestellung in Monaten

Diese Kennzahl zeigt die Wahrscheinlichkeit, dass ein Benutzer eine erneute Bestellung tätigt, da seit seiner letzten Bestellung Monate vergangen sind. Die Formel, mit der diese Metrik generiert wird, vereinfacht Folgendes:

![Formel für Wiederholungswahrscheinlichkeit](../../assets/Repeat_probability_formula.png)

Je nach Ihrem Geschäftsmodell kann die Wiederholungsbestellwahrscheinlichkeit entweder sofort nach der Bestellung eines Kunden abnehmen und in den darauffolgenden Monaten weiter sinken oder saisonale Schwankungen und Spitzen zeigen.

Wenn Sie den Prozentsatz der Kunden verstehen, von denen erwartet wird, dass sie Wiederholungskäufe tätigen (und wie dieser Trend im Laufe der Zeit abläuft), können Sie Ihre Kunden in Intervallen ansprechen, um die Wahrscheinlichkeit eines Wiederholungskäufs zu maximieren. Wenn also die Wahrscheinlichkeit eines wiederholten Kaufs abnimmt, können Sie einen Zeitpunkt auswählen, um einen Kunden als abgesichert zu identifizieren, und Ihre Bemühungen von der Bindung zur erneuten Aktivierung umstellen.

## Das heutige Beispiel

Sehen Sie sich den Rückgang der Wiederholungswahrscheinlichkeit für ein typisches E-Commerce-Geschäft an.

![Anfängliche Wiederholungsauftragswahrscheinlichkeit Wiederholungsauftragswahrscheinlichkeit in den Monaten seit der Bestellung.](../../assets/Order_probability_reports.png)

### anfängliche Wiederholungsreihenwahrscheinlichkeit

In diesem Beispiel beträgt die anfängliche Wiederholungsbestellwahrscheinlichkeit - oder die Wahrscheinlichkeit, dass ein Kunde einen Wiederholungskauf tätigt - 60 %. Das bedeutet, dass 60% aller bei diesem Geschäft aufgegebenen Bestellungen von einer nachfolgenden Bestellung gefolgt werden.

### Wiederholungsbestellwahrscheinlichkeit seit Bestellung in Monaten

Dieser Bericht zeigt die Wahrscheinlichkeit, dass ein Kunde erneut bestellt wird, da seit seiner letzten Bestellung Monate vergangen sind. Obwohl es für den Abwanderungsschwellenwert in diesem Bericht keine Einzeldefinition gibt, empfiehlt Adobe, die Abwanderung als den Punkt zu definieren, an dem der Wahrscheinlichkeitsverfall den Wert überschreitet, der der Hälfte der anfänglichen Wiederholwahrscheinlichkeitsrate entspricht.

Da die anfängliche Wiederholungswahrscheinlichkeitsrate für dieses Beispiel 60 % beträgt, wäre das Abwanderungsdatum der Zeitpunkt, zu dem die Wiederholungsbestellwahrscheinlichkeit unter 60 %/2 = 30 % oder etwa 6 Monate absinkt. Von den 60 % der Bestellungen, die voraussichtlich mit einer weiteren Bestellung bestellt werden, wurde die Hälfte innerhalb der ersten sechs Monate aufgegeben.

Anders ausgedrückt: Wenn ein Kunde eine Nachbestellung tätigt, ist es wahrscheinlicher, dass er dies innerhalb von sechs Monaten nach seiner letzten Bestellung getan hat als nach der Sechsmonatsfrist. Wenn ein Kunde nach sechs Monaten nicht zurückgekauft hat, sollte eine Reaktivierungskampagne gestartet werden, um diesen Kunden wieder einzuziehen.

Abhängig von Ihrem Geschäftsmodell können Sie stattdessen einen anderen Schwellenwert wählen, z. B. den Punkt, an dem die Wiederholungsbestellwahrscheinlichkeit unter 50 % oder 10 % sinkt. Wenn Ihr internes Wissen auf eine andere Zahl hinweist, dann sollten Sie sie auf jeden Fall verwenden!

Letztlich besteht das Ziel darin, die Schwelle auszuwählen, an der es sinnvoll ist, von der Aufbewahrung zur Reaktivierung zu wechseln. Bei den Bemühungen um Kundenbindung kann es sich um E-Mails handeln, um Bestandskunden mit empfohlenen Folgekäufen erneut anzusprechen, während bei Reaktivierungsmaßnahmen E-Mails an verstorbene Kunden mit Coupons und Angeboten erforderlich sein können.

## Welche Fragen sollte ich beachten?

Um Ihnen dabei zu helfen, die Wahrscheinlichkeit von wiederholten Bestellungen zu verstehen, die für Ihr Unternehmen gilt, schlägt Adobe vor, diese Fragen zu berücksichtigen, wenn Sie Ihre eigenen Daten untersuchen:

* Ist die anfängliche Wiederholungsauftragswahrscheinlichkeit zu erwarten? Wenn nein, warum sollte es Ihrer Meinung nach höher oder niedriger sein?
* Gibt es seit der letzten Bestellung einen großen Rückgang der Wahrscheinlichkeit für wiederholte Bestellungen für bestimmte Monate? Wenn ja, sind diese Änderungen zu erwarten?
* Wie hoch ist Ihre aktuelle Abwanderungsschwelle?
* Stimmt der aktuelle Abwanderungsschwellenwert mit einem der Werte in Ihrer Wiederholungsbestellwahrscheinlichkeit für bestimmte Monate seit dem letzten Bestellbericht überein?
* Spiegelt Ihre aktuelle Schwelle Ihre Werbebemühungen wider, von der Aufbewahrung zur erneuten Aktivierung zu wechseln?
* Ist es sinnvoll, dass Ihr Unternehmen die Schwelle in den Monat ändert, in dem der Wahrscheinlichkeitsverfall den Wert überschreitet, der halb so hoch ist wie die anfängliche Wiederholwahrscheinlichkeitsrate?

## Was soll ich sonst noch analysieren?

Nachdem Sie die obige Analyse erstellt und einen Abwanderungsschwellenwert ermittelt haben, können Sie weitere Analysen erstellen, um allgemeine Trends bei abgeworfenen Benutzern zu identifizieren. Wurden beispielsweise Kunden, die im selben Zeitraum gekauft haben, oder haben sie in ihrer letzten Bestellung ähnliche Produkte gekauft? Sobald ein Abwanderungsschwellenwert festgelegt wurde, können Sie in bestimmte Eigenschaften dieser abgefeuerten Kunden eintauchen.

Wenn Sie mehr als ein Produkt anbieten, fragen Sie sich wahrscheinlich, wie sich Kunden, die ein bestimmtes Produkt kaufen, im Laufe der Zeit anders verhalten als andere Kunden. Möchten Sie mehr erfahren? Sehen Sie sich dieses Tutorial an, um das lebenslange Kaufverhalten von Kundenkohorten basierend auf bestimmten Produkten, die sie gekauft haben, zu untersuchen.

Diese Best Practice wird von [!DNL MBI] Data Analysis Services (DAS). [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en) für weitere Informationen.

### Verwandte

* [Analyse der Auswirkungen von Gutscheinen auf die Akquise und Bindung von Kunden](../analysis/coupon-impact.md)
* [Analysieren des Kaufverhaltens von Kunden](../analysis/repurchase-behavior.md)
