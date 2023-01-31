---
title: Bericht zur Bestellwahrscheinlichkeit wiederholen
description: Erfahren Sie mehr über den Bericht zur Wahrscheinlichkeit wiederholter Bestellungen.
exl-id: 2c88b85a-7320-44ca-87a5-5b91250348ea
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Bericht zur Bestellwahrscheinlichkeit wiederholen

## Wann ist der `Incremental Event Probability` Perspektive verfügbar?

Die `incremental event probability` ist nur verfügbar, wenn Filter Dimensionen verwenden, die für alle Bestellungen gleich sind (z. B. die `gender`, der `age` oder des Benutzers `source`)

Dies liegt daran, dass diese Perspektive auf einer Dimension mit dem Namen `User's order number` für die Segmentierung, die die Käufe eines Benutzers zählt (z. B. die 1., 2. und 3. Bestellungen von John).

Wenn wir einen Filter hinzufügen würden, der eine Dimension verwendet, die nicht für alle Bestellungen gleich ist (z. B. `Order's Region`), die `User's order number` -Dimension nicht mehr genau sein, da sie bei der Nummerierung der Bestellungen eines Benutzers bestimmte Regionen nicht berücksichtigt (z. B. sind die ersten, zweiten und dritten Bestellungen von John immer noch die gleichen, unabhängig von ihrer Region).

## Eine auftragsspezifische Dimension in eine benutzerspezifische Dimension umwandeln

In bestimmten Fällen können wir die `order-specific` Dimension in eine `user-specific` Dimension, die als Filter in der `Repeat Order Probability` Diagramm. In diesen Fällen geben wir das Bestellattribut der ersten Bestellung oder der neuesten Bestellung eines Benutzers zurück (z. B. den Regionennamen des Benutzers für die erste Bestellung).

Wenn Sie eine solche neue Dimension erstellen möchten, [Support kontaktieren](../../guide-overview.md).

## Vergleich der Wiederholungswahrscheinlichkeit von Bestellungen mit unterschiedlichen Attributen

Um die Anzahl wiederholter Käufe für verschiedene Bestellattribute zu vergleichen (z. B. die `region`), empfehlen wir, ein Diagramm ähnlich dem zu erstellen. `Users by lifetime number of orders` zeigt die Anzahl der Benutzer an, die 1, 2, 3 usw. Bestellungen getätigt haben, und fügt den Filter auf Bestellebene hinzu. (Mit anderen Worten: Dies zeigt Ihnen, ob Benutzer in einer Region oder einer anderen mehr oder weniger Käufe tätigen.)

Die Zahlen, aus denen ein solches Diagramm besteht, können dann in Excel exportiert werden, um das Wahrscheinlichkeitsverhältnis der Wiederholung der Bestellung zu berechnen. So sehen Sie die Wahrscheinlichkeit von Kunden, die `(x)` Bestellungen `(x+1)` Bestellungen, einfach` divide the number of people who've made at least (x+1) purchases by the number of people who have made at least (x)` Einkäufe.

### Beispiel:

|  |  |
|---|---|
| Anzahl der Kunden, die in ihrer Lebensdauer einen Kauf getätigt haben | `90` |
| Anzahl der Kunden, die während ihrer Lebensdauer zwei Käufe getätigt haben | `30` |
| Anzahl der Kunden, die während ihrer Lebensdauer drei Käufe getätigt haben | `10` |
| Die Wiederholungsauftragswahrscheinlichkeit von Kunden, die während ihrer Lebensdauer einen Kauf getätigt haben, um einen zweiten Kauf zu tätigen | `(30 + 10) / (30+10+90) = 30.77%` |
