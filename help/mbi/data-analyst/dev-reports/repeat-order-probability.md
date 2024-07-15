---
title: Bericht zur Bestellwahrscheinlichkeit wiederholen
description: Erfahren Sie mehr über den Bericht zur Wahrscheinlichkeit wiederholter Bestellungen.
exl-id: 2c88b85a-7320-44ca-87a5-5b91250348ea
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Bericht zur Bestellwahrscheinlichkeit wiederholen

## Wann ist die Perspektive `Incremental Event Probability` verfügbar?

Die Perspektive `incremental event probability` ist nur verfügbar, wenn Filter Dimensionen verwenden, die für alle Bestellungen gleich sind (z. B. `gender` des Benutzers, `age` des Benutzers oder `source` des Benutzers).

Dies liegt daran, dass diese Perspektive bei der Segmentierung auf einer Dimension mit dem Namen `User's order number` beruht, die die Käufe eines Benutzers zählt (z. B. die erste, zweite und dritte Bestellungen von John).

Wenn Sie einen Filter hinzufügen, der eine Dimension verwendet, die nicht für alle Bestellungen gleich ist (z. B. `Order's Region`), wäre die Dimension `User's order number` nicht mehr genau. Dies liegt daran, dass bei der Nummerierung der Bestellungen eines Benutzers bestimmte Regionen nicht berücksichtigt werden (z. B. sind die Bestellungen von John 1., 2. und 3. unabhängig von seiner Region immer noch gleich).

## Eine auftragsspezifische Dimension in eine benutzerspezifische Dimension umwandeln

In bestimmten Fällen können Sie eine `order-specific` -Dimension in eine `user-specific` -Dimension umwandeln, um sie als Filter in das `Repeat Order Probability` -Diagramm einzufügen. In diesen Fällen geben Sie das Bestellattribut der ersten Bestellung oder der neuesten Bestellung eines Benutzers zurück (z. B. den Regionennamen der ersten Bestellung des Benutzers).

Wenn Sie eine solche neue Dimension erstellen möchten, kontaktieren Sie [den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

## Vergleich der Wiederholungswahrscheinlichkeit von Bestellungen mit unterschiedlichen Attributen

Um die Anzahl der Wiederholungskäufe für verschiedene Bestellattribute zu vergleichen (z. B. `region` der Bestellung), empfiehlt Adobe, eine Grafik ähnlich der `Users by lifetime number of orders` zu erstellen. Zeigt die Anzahl der Benutzer an, die 1, 2, 3 usw. Bestellungen getätigt haben, und fügt den Filter auf Bestellebene hinzu. (Mit anderen Worten: Dies zeigt Ihnen, ob Benutzer in einer Region oder einer anderen mehr oder weniger Käufe tätigen.)

Die Zahlen, aus denen ein solches Diagramm besteht, können dann in Excel exportiert werden, um das Wahrscheinlichkeitsverhältnis der Wiederholung der Bestellung zu berechnen. Um die Wahrscheinlichkeit zu sehen, mit der Kunden, die `(x)` Bestellungen aufgegeben haben, `(x+1)` Bestellungen tätigen, einfach ` divide the number of people who've made at least (x+1) purchases by the number of people who have made at least (x)` Käufe tätigen.

### Beispiel:

| Kategorie | Wert |
|---|---|
| Anzahl der Kunden, die in ihrer Lebensdauer einen Kauf getätigt haben | `90` |
| Anzahl der Kunden, die während ihrer Lebensdauer zwei Käufe getätigt haben | `30` |
| Anzahl der Kunden, die während ihrer Lebensdauer drei Käufe getätigt haben | `10` |
| Die Wiederholungsauftragswahrscheinlichkeit von Kunden, die während ihrer Lebensdauer einen Kauf getätigt haben, um einen zweiten Kauf zu tätigen | `(30 + 10) / (30+10+90) = 30.77%` |
