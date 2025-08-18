---
title: 'Grundlegendes zu Ihrer  [!DNL Commerce Intelligence] '
description: Erfahren Sie mehr über das Arbeiten mit und die Verbesserung Ihrer  [!DNL Commerce Intelligence] .
exl-id: 601b5fba-da02-4cc8-96ed-147c24f326f9
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 0%

---

# Ihre [!DNL Adobe Commerce Intelligence]

Beachten Sie bei der Analyse Ihrer Commerce-Daten diese Faktoren und häufigen Missverständnisse. Wenn Sie Hilfe benötigen, um sicherzustellen, dass Sie Ihr Commerce-Schema ordnungsgemäß verwenden, zögern Sie nicht, sich an den [ zu wenden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

## [!DNL entity\_id]

Viele Ihrer Tabellen enthalten eine Spalte mit dem Namen `entity\_id`. In jeder Tabelle, die eine `entity\_id` enthält, wird diese Spalte zur Identifizierung eindeutiger Zeilen verwendet.

Beispielsweise ist jede Zeile in der `sales\_order`-Tabelle eine eindeutige Reihenfolge. Der Primärschlüssel in dieser Tabelle wird als `entity\_id` bezeichnet. Diese Spalte kann als `order\_id` betrachtet werden. In einer separaten Tabelle `customer\_entity` stellt jede Zeile einen Unique Customer dar. Der Primärschlüssel in dieser Tabelle wird auch als `entity\_id` bezeichnet, was als `customer\_id` betrachtet werden kann.

In diesen Tabellen ist `sales\_order.entity\_id` nicht gleich `customer\_entity.entity\_id`. Dies gilt für alle Gruppen von Tabellen, die `entity\_id` enthalten: `table\_A.entity\_id` ist nicht gleich `table\_B.entity\_id`.

## [!DNL Guest orders]

Wenn Sie Kunden erlauben, ohne Konto über Ihre Website zu bestellen (Gastbestellungen), werden diese Kunden nicht als Zeile in Ihrer `customer\_entity` Tabelle aufgeführt. Außerdem hat jede von einem Gast aufgegebene Bestellung einen Null-`customer\_id`-Wert in der `sales\_order`.

Wenn Sie also das Verhalten Ihrer Gäste im Laufe der Zeit verfolgen möchten, müssen alle Spalten auf Kundenebene auf der `sales\_order`-Tabelle mithilfe einer Kundenkennung wie `customer\_email` berechnet werden.

Wenn Sie die `sales\_order` als Kundentabelle verwenden, müssen Sie beim Erstellen von Metriken auf Kundenebene vorsichtig sein. Betrachten Sie beispielsweise eine Metrik für den durchschnittlichen Lebensdauerumsatz. Diese Metrik wird verwendet, um den durchschnittlichen lebenslangen Umsatz in Ihrem gesamten Kundenstamm zu identifizieren. Dies erfordert zunächst eine neue Spalte, die für jeden Kunden den Lebensdauerumsatz zurückgibt. Dann müssen Sie diese Spalte im Durchschnitt auffüllen, um den durchschnittlichen Lebensdauerumsatz Ihrer Kunden zu erhalten.

Wenn Sie die Tabelle `customer\_entity` verwenden können, ist jede Zeile ein einzelner Kunde, und jeder Kunde ist nur einmal in dieser Tabelle vorhanden. Wenn Sie also über die Spalte Lebensdauerumsatz verfügen, müssen Sie nur eine durchschnittliche Metrik erstellen. Wenn Sie jedoch die Tabelle `sales\_order` als Kundentabelle verwenden, kann ein Kunde möglicherweise in zahlreichen Zeilen vorhanden sein. Nach der Einrichtung der Spalte Lebensdauerumsatz zeigt jede Bestellung (Zeile) eines bestimmten Kunden den Lebensdauerumsatz dieses Kunden an. Sie möchten diesen Kunden jedoch nur einmal in Ihre allgemeine Durchschnittsmetrik aufnehmen.

Der Trick besteht darin, dass Sie Ihrer Metrik einen Filter hinzufügen müssen, der sicherstellt, dass Sie jeden Kunden nur einmal einbeziehen. Adobe empfiehlt die Erstellung und Verwendung eines Filtersatzes mit dem Namen **Kunden zählen** der nach (**Kundenauftragsnummer = 1) filtert** neben anderen Filtern müssen Sie möglicherweise unerwünschte Kunden ausschließen). Durch Hinzufügen dieses Filters wird sichergestellt, dass Sie jeden Kunden nur einmal in eine Metrik auf Kundenebene einbeziehen.

## Produkte und Kategorien

Produkte können mehrere Kategorien haben, und Kategorien können für mehr als ein Produkt verwendet werden. Daher müssen Sie beim Einrichten von Analysen auf Kategorieebene darauf achten, die richtigen Definitionen zu verwenden. Möchten Sie die Kategorie der obersten Ebene? Zweite Kategorie? Was passiert, wenn das Produkt in mehrere Kategorien der obersten Ebene fallen kann?

Stellen Sie sich eine Jeans vor, die in drei verschiedene Kategoriestufen fällt, wie sie von einer Commerce-Implementierung definiert werden: „Clothing“ (oberste Ebene), „Outerwear“ (zweite Ebene) und „Pants“ (dritte Ebene). Sie können Ihre Leistungskategorien nach der Anzahl der verkauften Einheiten analysieren. Die für diese Analyse benötigte Metrik lautet _Artikel verkauft_, die auf der `sales\_order\_item`-Tabelle basiert. Daher müssen Sie Informationen auf Kategorieebene in die Elementtabelle verschieben. Jede Zeile in der `sales\_order\_item`-Tabelle ist mit einem `product\_id` verknüpft. Wenn Sie also die mit einem Produkt verknüpften Kategorien kennen, können Sie diese Informationen in die gewünschte Tabelle übertragen.

Bevor Sie Daten verschieben, müssen Sie zunächst die richtigen Joins und Filter kennen, um sicherzustellen, dass Sie die richtige Kategorie erfassen. Für einige Analysen benötigen Sie möglicherweise „Hosen“, in anderen Analysen ist „Kleidung“ jedoch möglicherweise besser geeignet. Hierbei handelt es sich um verschiedene Kategorien, die separat identifiziert werden. Wenn Sie wissen, wie jede Kategorieebene definiert ist, können Sie den Verkauf von Einheiten der entsprechenden Kategorie für Ihre spezifische Analyse zuordnen.

Stellen Sie sich nun vor, auf der Startseite Ihrer Website befindet sich auch eine `Our Favorites` Kategorie der obersten Ebene. Vielleicht haben Sie Ihren Commerce Store implementiert, um diese Jeans sowohl in der Kategorie `Clothing` als auch in der Kategorie `Our Favorites` einzuschließen. Wenn ja, hat diese Jeans mehr als eine Kategorie der obersten Ebene. In diesem Fall ist es nicht ganz sinnvoll, eine einzelne Kategorie der obersten Ebene in die `sales\_order\_item` Tabelle zu verschieben, da mehrere Optionen vorhanden sind. Aus diesem Grund empfiehlt Adobe die Erstellung von Spalten mit Ja/Nein, die auf bestimmte Kategorien prüfen. Beispielsweise können Sie mit den Spalten `Is product in Clothing category?` und `Is product in Our Favorites category?` überprüfen, ob ein Produkt in diese spezifischen Kategorien fällt.
