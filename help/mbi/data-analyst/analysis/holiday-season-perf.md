---
title: Analysieren der Leistung der Weihnachtszeit
description: Erfahren Sie, wie sich das diesjährige Wachstum im Vergleich zu den Vorjahren entwickelt.
exl-id: 328f30b8-0db6-48fd-8d97-95f0bc7e4803
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Holiday Shopping Analysis

Für Ihr Unternehmen ist der Urlaub vielleicht eine der geschäftigsten Zeiten des Jahres. Für Einzelhändler mit einem großen amerikanischen Kundenstamm erstreckt sich die Weihnachtszeit in der Regel über die Monate zwischen dem Erntedankfest und dem Neujahr.

Rushes können jederzeit während des Jahres auftreten. Wenn Ihr Unternehmen z. B. Shorts oder Poolvorräte verkauft, kann es im Sommer zu einer Eile kommen. Dieses Thema untersucht Analysen, die Ihnen helfen, Ihre hohen Jahreszeiten über verschiedene Jahre hinweg zu vergleichen.

## Empfohlene Metriken

Bei der Analyse der Leistung in der Weihnachtszeit sollten Sie die Analyse in Erwägung ziehen ([oder Gebäude](../../data-user/reports/ess-manage-data-metrics.md)) diese Metriken:

### Anzahl neuer Kunden, Anzahl Bestellungen, Umsatz

Um zu verstehen, wie sich das diesjährige Wachstum im Vergleich zu den Vorjahren entwickelt, sollten Sie diese Maßnahmen analysieren. Die Anzahl neuer Kunden, die Anzahl neuer Bestellungen und der Umsatzbetrag zeigen Ihnen die tägliche Leistung Ihres Unternehmens für den von Ihnen festgelegten Zeitraum (Weihnachtszeit). Sie können diese Kennzahlen auch mithilfe einer kumulativen Perspektive analysieren, um zu sehen, wie sich die Metrik im Laufe der Zeit ändert.

### Durchschnittlicher Bestellwert

Diese Kennzahl zeigt den durchschnittlichen Gesamtbestellwert während Ihrer Urlaubszeit an.

## Beispiel: Täglicher Umsatz in der Weihnachtszeit

Nachdem Sie nun wissen, welche Metriken analysiert werden sollen, sehen Sie sich einige Beispielumsatzdaten während der Weihnachtsmonate November und Dezember für 2014 und 2015 an.

![Tägliche Weihnachtseinnahmen für 2014 und 2015](../../assets/Analyzing_holiday_season.png)

In diesem Beispiel gibt es zwei große Umsatzspitzen für 2014 und 2015: Diese Erhöhungen entsprechen Black Friday und Cyber Monday. Beachten Sie, dass die Spitzen 2014 und 2015 nicht am selben Tag stattfinden. Dies liegt daran, dass Black Friday für 2014 auf den 27. November und für 28. November 2015 auf den 27. November fiel. Ebenso war Cyber Montag der 30. November für 2014 und der 1. Dezember für 2015.

Darüber hinaus gibt es einen Anstieg der Einnahmen für 2015 am 19. Dezember, der 2014 nicht auftritt. Es ist möglich, dass ein Verkauf an diesem Samstag angeboten wurde, der im Vorjahr nicht verfügbar war.

Abgesehen von den wenigen oben genannten Daten verzeichnen sich die Umsätze für diese beiden Jahre zusammen.

## Welche Fragen sollte ich beachten?

Um Ihnen zu helfen, die saisonalen Trends für Ihr Unternehmen zu verstehen, sollten Sie bei der Erforschung Ihrer eigenen Daten einige Fragen beachten:

* Sind die Trends von Jahr zu Jahr zu erwarten?
* Entsprechen die Trends Ihren Erwartungen an saisonbedingte Schwankungen?
* Gibt es Unterschiede von Jahr zu Jahr? Können diese Unterschiede erklärt werden?
* Wurden in einem bestimmten Jahr Promotions angeboten?
* Wurden die Preise in einem bestimmten Jahr gestiegen?
* Wurden die Werbeausgaben für ein bestimmtes Jahr erhöht?

## Was soll ich sonst noch analysieren?

Eine Möglichkeit besteht darin, das Kaufverhalten Ihrer Kunden während der Urlaubszeit zu analysieren. Verbringen Kunden, die während der Weihnachtszeit erworben wurden, häufiger oder kaufen häufiger als Kunden außerhalb der Weihnachtszeit?

Eine weitere Möglichkeit besteht darin, den ROI nach Kampagnen während der Urlaubszeiten zu analysieren. Ist Ihr ROI bei bestimmten Kampagnen höher, die während der Weihnachtszeit ausgeführt werden? Sollten Sie während dieser Saison die Ausgaben für Kampagnen mit hohem ROI erhöhen?

Darüber hinaus können Sie die Anzahl der diskontierten Bestellungen im Vergleich zu vollständigen Preisaufträgen analysieren. [Warten die meisten Kunden auf einen Kauf von Bestellungen](../analysis/coupon-usage.md) während Ihrer Urlaubszeit oder kaufen sie ganze Preisartikel?

### Verwandte

* [Analyse der Auswirkungen von Gutscheinen auf die Akquise und Bindung von Kunden](../analysis/coupon-impact.md)
* [Analysieren des Kaufverhaltens von Kunden](../analysis/repurchase-behavior.md)
