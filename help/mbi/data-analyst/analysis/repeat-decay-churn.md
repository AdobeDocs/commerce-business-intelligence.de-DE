---
title: Analyse der Wiederholungswahrscheinlichkeit von Abfall und Abwanderung
description: Erfahren Sie, wie viel Zeit zwischen Bestellungen vergeht und wann Kunden voraussichtlich abwandern werden.
exl-id: ea26052d-ac74-43b7-a4a6-977800d4c719
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---

# Wiederholungswahrscheinlichkeit, Abwanderung und Abwanderung

Wenn ein Teil Ihres Umsatzes aus wiederholten Käufen stammt, sind Sie sich wahrscheinlich des enormen Werts eines treuen Kundenstamms bewusst. Zu diesem Zweck ist es wichtig zu verstehen, wie viel Zeit zwischen den Bestellungen vergeht und wann die Kunden voraussichtlich abwandern werden.

In diesem Thema werden die Analysen untersucht, die Ihnen bei der Beantwortung der folgenden Fragen helfen können:

* Wie hoch ist die Wahrscheinlichkeit, dass ein Kunde einen weiteren Kauf tätigt?
* Wie schwankt die Wahrscheinlichkeit für die Wiederholungsbestellung im Laufe der Zeit seit dem letzten Kauf des Kunden?
* Wann sollte ein Kunde als abgewandert betrachtet werden? Und wann sollte eine Reaktivierungskampagne gestartet werden?

## Empfohlene Kennzahlen

Bei der Analyse von Wiederholungswahrscheinlichkeitsverfall und Abwanderung sollten Sie die Verwendung ([oder den Aufbau](../../data-user/reports/ess-manage-data-metrics.md) dieser Metriken in Betracht ziehen:

### Wahrscheinlichkeit der anfänglichen Wiederholungsreihenfolge

Diese Kennzahl ist definiert als die Gesamtzahl der Wiederholungsaufträge, als Prozentsatz der Gesamtaufträge. Anders ausgedrückt: Dies ist die Wahrscheinlichkeit, dass einer Bestellung eine andere Bestellung folgt. Wenn diese Wahrscheinlichkeit über 50 Prozent liegt, bedeutet dies, dass mehr als die Hälfte aller Bestellungen von einer nachfolgenden Bestellung gefolgt wird.

### Wiederholungswahrscheinlichkeit der Bestellung seit Monaten

Diese Kennzahl zeigt die Wahrscheinlichkeit, dass eine Benutzerin oder ein Benutzer angesichts der Anzahl der Monate seit ihrer letzten Bestellung erneut bestellt. Die Formel, mit der diese Metrik generiert wird, vereinfacht Folgendes:

![Formel für die Wiederholungswahrscheinlichkeit](../../assets/Repeat_probability_formula.png)

Je nach Geschäftsmodell sinkt die Wahrscheinlichkeit für Wiederholungsaufträge entweder sofort nach der Auftragserteilung durch den Kunden und sinkt in den folgenden Monaten weiter oder es können saisonale Schwankungen und Spitzen auftreten.

Wenn Sie wissen, wie viel Prozent der Kundinnen und Kunden voraussichtlich wiederholte Käufe tätigen werden (und wie sich dieser Trend im Laufe der Zeit entwickelt), können Sie Ihre Kundinnen und Kunden in bestimmten Abständen ansprechen, um die Wahrscheinlichkeit eines wiederholten Kaufs zu maximieren. Wenn also die Wahrscheinlichkeit eines wiederholten Kaufs sinkt, können Sie einen Zeitpunkt auswählen, zu dem Sie einen Kunden als Abgewanderte identifizieren und Ihre Bemühungen von der Bindung auf die Reaktivierung umstellen.

## Beispiel vom heutigen Tag

Betrachten Sie die Wiederholungswahrscheinlichkeit für einen typischen E-Commerce-Betrieb.

![Anfängliche Wiederholungsreihenfolgewahrscheinlichkeit Wiederholungsreihenfolgewahrscheinlichkeit angegeben Monate seit Bestellung.](../../assets/Order_probability_reports.png)

### Wahrscheinlichkeit der anfänglichen Wiederholungsreihenfolge

In diesem Beispiel beträgt die anfängliche Wahrscheinlichkeit für Wiederholungsaufträge - oder die Wahrscheinlichkeit, dass ein Kunde einen Wiederholungskauf tätigt - 60 Prozent. Das bedeutet, dass auf 60 Prozent aller Bestellungen in diesem Geschäft eine Nachbestellung folgt.

### Wiederholungswahrscheinlichkeit der Bestellung seit Monaten

Dieser Bericht zeigt die Wahrscheinlichkeit, dass ein Kunde erneut bestellt, da seit seiner letzten Bestellung einige Monate vergangen sind. Obwohl es für diesen Bericht keine Einzeldefinition für den Abwanderungsschwellenwert gibt, empfiehlt Adobe, Abwanderung als den Punkt zu definieren, an dem der Wahrscheinlichkeitsabfall den Wert überschreitet, der die Hälfte der anfänglichen Wiederholungswahrscheinlichkeitsrate beträgt.

Da die anfängliche Wiederholungswahrscheinlichkeitsrate für dieses Beispiel 60 % beträgt, wäre das Abwanderungsdatum der Zeitpunkt, zu dem die Wiederholungsreihenfolgewahrscheinlichkeit unter 60 %/2 = 30 % fällt, oder bei etwa 6 Monaten. Von den 60 % der Bestellungen, die voraussichtlich mit einer anderen Bestellung nachgeholt werden, wurde die Hälfte innerhalb der ersten 6 Monate aufgegeben.

Anders ausgedrückt: Wenn ein Kunde eine Folgebestellung aufgeben wollte, war die Wahrscheinlichkeit höher, dass er dies innerhalb von sechs Monaten nach seiner letzten Bestellung getan hat, als nach der Sechsmonatsmarke. Wenn ein Kunde nach sechs Monaten keinen Rückkauf getätigt hat, sollte eine Reaktivierungskampagne gestartet werden, um diesen Kunden wieder heranzuziehen.

Je nach Geschäftsmodell sollten Sie stattdessen einen anderen Schwellenwert wählen, z. B. den Punkt, an dem die Wahrscheinlichkeit der Wiederholungsreihenfolge unter 50 % oder 10 % sinkt. Wenn Ihr internes Wissen eine andere Zahl vorschlägt, dann sollten Sie sie auf jeden Fall verwenden!

Das Ziel besteht letztendlich darin, den Schwellenwert auszuwählen, bei dem es sinnvoll ist, von der Beibehaltung zu den Reaktivierungsbemühungen zu wechseln. Aufbewahrungsmaßnahmen können E-Mails beinhalten, um erneut mit Bestandskunden mit vorgeschlagenen Folgekäufen zu interagieren, während Reaktivierungsmaßnahmen E-Mails mit Coupons und Angeboten an verfallene Kunden umfassen können.

## Welche Fragen sollte ich berücksichtigen?

Um Ihnen dabei zu helfen, die Wahrscheinlichkeit von Wiederholungsaufträgen für Ihr Unternehmen zu verstehen, schlägt Adobe vor, diese Fragen zu berücksichtigen, wenn Sie Ihre eigenen Daten untersuchen:

* Wird die anfängliche Wiederholungsreihenfolge erwartet? Wenn nicht, warum sollte sie dann höher oder niedriger sein?
* Gibt es seit der letzten Bestellung erhebliche Rückgänge bei der Wiederholungsreihenwahrscheinlichkeit für bestimmte Monate? Wenn ja, werden diese Änderungen erwartet?
* Wie hoch ist die aktuelle Abwanderungsschwelle?
* Passt Ihr aktueller Abwanderungsschwellenwert zu einem der Werte in Ihrer Wiederholungsauftragswahrscheinlichkeit, die seit der letzten Bestellauswertung Monate zurückliegt?
* Spiegelt der aktuelle Schwellenwert Ihre Werbebemühungen beim Wechsel von der Bindung zur Reaktivierung wider?
* Ist es für Ihr Unternehmen sinnvoll, den Schwellenwert auf den Monat zu ändern, in dem der Wahrscheinlichkeitsverfall den Wert überschreitet, der der Hälfte der ursprünglichen Wiederholungswahrscheinlichkeitsrate entspricht?

## Was sollte ich noch analysieren?

Nachdem Sie die oben genannte Analyse erstellt und eine Abwanderungsschwelle festgelegt haben, können Sie weitere Analysen erstellen, um gängige Trends bei abgewanderten Benutzenden zu identifizieren. Werden beispielsweise Kunden, die im selben Zeitraum abgewandert sind, erworben oder haben sie ähnliche Produkte in ihrer letzten Bestellung gekauft? Sobald ein Abwanderungsschwellenwert festgelegt wurde, können Sie sich näher mit bestimmten Eigenschaften dieser abgewanderten Kundinnen und Kunden befassen.

Wenn Sie mehr als ein Produkt anbieten, fragen Sie sich wahrscheinlich, wie sich Kunden, die ein bestimmtes Produkt erwerben, im Laufe der Zeit anders verhalten als andere Kunden. Möchten Sie mehr erfahren? Sehen Sie sich dieses Tutorial an, um das lebenslange Kaufverhalten von Kundenkohorten basierend auf bestimmten Produkten zu untersuchen, die sie gekauft haben.

Diese Best Practice wird von [!DNL Adobe Commerce Intelligence] Data Analysis Services (DAS) bereitgestellt. [Kontaktieren Sie den ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um weitere Informationen zu erhalten.

### verwandt

* [Analyse der Couponauswirkungen auf Kundenakquise und Kundenbindung](../analysis/coupon-impact.md)
* [Analyse des Rückkaufverhaltens von Kunden](../analysis/repurchase-behavior.md)
