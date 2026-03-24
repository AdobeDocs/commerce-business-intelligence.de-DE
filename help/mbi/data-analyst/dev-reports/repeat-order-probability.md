---
title: Bericht zur Wahrscheinlichkeit der Wiederholungsreihenfolge
description: Lernen Sie den Bericht zur Wahrscheinlichkeit der Wiederholungsreihenfolge kennen und verstehen Sie ihn.
exl-id: 2c88b85a-7320-44ca-87a5-5b91250348ea
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: https://experienceleague.adobe.com/MW9jxiwitZyjc6-woelN-FOAmvEFPCWDt01wyTOX16k
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 343
ht-degree: 0%

---

# Bericht zur Wahrscheinlichkeit der Wiederholungsreihenfolge

## Wann ist die `Incremental Event Probability` verfügbar?

Die `incremental event probability` ist nur verfügbar, wenn Filter Dimensionen verwenden, die für alle Bestellungen gleich sind (z. B. `gender`, `age` oder `source` der Benutzenden).

Dies liegt daran, dass diese Perspektive auf einer Dimension namens `User's order number` für die Segmentierung basiert, die die Käufe eines Benutzers nummeriert (z. B. die erste, zweite und dritte Bestellung von John).

Wenn Sie einen Filter hinzugefügt haben, der eine Dimension verwendet, die nicht für alle Bestellungen gleich ist (z. B. `Order's Region`), ist die `User's order number` Dimension nicht mehr korrekt. Dies liegt daran, dass bei der Nummerierung der Bestellungen eines Benutzers bestimmte Regionen nicht berücksichtigt werden (z. B. sind die 1., 2., 3. Bestellung von John unabhängig von ihrer Region immer noch gleich).

## Umwandeln einer auftragsspezifischen Dimension in eine benutzerspezifische Dimension

In bestimmten Fällen können Sie eine `order-specific` Dimension in eine `user-specific` Dimension umwandeln, die dem `Repeat Order Probability` als Filter hinzugefügt werden soll. In diesen Fällen geben Sie das Sortierattribut der ersten oder letzten Bestellung eines Benutzers zurück (z. B. den Regionsnamen der ersten Bestellung eines Benutzers).

Wenn Sie eine solche neue Dimension erstellen möchten, wenden [ sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

## Vergleich der Wiederholungswahrscheinlichkeit von Aufträgen mit verschiedenen Attributen

Um die Anzahl der wiederholten Käufe für verschiedene Bestellattribute (z. B. die `region` der Bestellung) zu vergleichen, empfiehlt Adobe die Erstellung eines Diagramms, das `Users by lifetime number of orders` ähnelt. Hier wird die Anzahl der Benutzer angezeigt, die 1, 2, 3,… Lebensdauernummer der Bestellungen getätigt haben, und der Filter auf Bestellebene hinzugefügt. (Mit anderen Worten: Dies kann anzeigen, ob Benutzende in der einen oder anderen Region mehr oder weniger wiederholte Käufe tätigen.)

Die Zahlen, aus denen ein solches Diagramm besteht, können dann nach Excel exportiert werden, um das Wahrscheinlichkeitsverhältnis der Wiederholungsreihenfolge zu berechnen. Um die Wahrscheinlichkeit von Kunden zu sehen, die `(x)` Bestellungen für `(x+1)` Bestellungen getätigt haben, ` divide the number of people who've made at least (x+1) purchases by the number of people who have made at least (x)` Sie einfach Käufe.

### Beispiel:

| Kategorie | Wert |
|---|---|
| Anzahl der Kundinnen und Kunden, die im Laufe ihres Lebens einen Kauf getätigt haben | `90` |
| Anzahl der Kunden, die im Laufe ihres Lebens zwei Käufe getätigt haben | `30` |
| Anzahl der Kunden, die im Laufe ihres Lebens drei Käufe getätigt haben | `10` |
| Die Wahrscheinlichkeit der Wiederholungsbestellung von Kunden, die einen Kauf im Laufe ihres Lebens getätigt haben, um einen zweiten Kauf zu tätigen | `(30 + 10) / (30+10+90) = 30.77%` |
