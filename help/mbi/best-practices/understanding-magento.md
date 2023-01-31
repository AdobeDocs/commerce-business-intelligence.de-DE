---
title: Verstehen Sie Ihre [!DNL MBI] Umgebung
description: Erfahren Sie mehr über die Arbeit mit und die Verbesserung Ihrer [!DNL MBI] Umgebung.
exl-id: 601b5fba-da02-4cc8-96ed-147c24f326f9
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Ihre [!DNL MBI] Umgebung

Achten Sie bei der Analyse Ihrer Commerce-Daten auf diese Faktoren und häufige falsche Vorstellungen. Wenn Sie Unterstützung benötigen, um sicherzustellen, dass Sie Ihr Commerce-Schema richtig verwenden, zögern Sie nicht, [Support kontaktieren](../guide-overview.md).

## [!DNL entity\_id]

Viele Ihrer Tabellen enthalten eine Spalte mit dem Namen `entity\_id`. In jeder Tabelle mit `entity\_id`, wird diese Spalte verwendet, um eindeutige Zeilen zu identifizieren.

Beispiel: Jede Zeile im `sales\_order` -Tabelle ist eine eindeutige Reihenfolge. Der Primärschlüssel in dieser Tabelle heißt `entity\_id`. Diese Spalte kann als `order\_id`. In einer separaten Tabelle `customer\_entity`, stellt jede Zeile einen Unique Customer dar. Der Primärschlüssel in dieser Tabelle wird auch als `entity\_id`, der als `customer\_id`.

In diesen Tabellen wird `sales\_order.entity\_id` ist nicht gleich `customer\_entity.entity\_id`. Dies gilt für alle Tabellensätze mit `entity\_id`: `table\_A.entity\_id` ist nicht gleich `table\_B.entity\_id`.

## [!DNL Guest orders]

Wenn Sie Kunden erlauben, von Ihrer Site aus zu bestellen, ohne ein Konto zu haben (Gastaufträge), werden diese Kunden nicht als Zeile in Ihrer `customer\_entity` Tabelle. Darüber hinaus hat jede von einem Gast aufgegebene Bestellung eine Null `customer\_id` Wert auf `sales\_order` Tabelle.

Wenn Sie das Verhalten Ihrer Gäste im Laufe der Zeit verfolgen möchten, müssen daher alle Spalten auf Kundenebene auf der Grundlage der Variablen `sales\_order` mit einer Kunden-ID wie `customer\_email`.

Wenn Sie die `sales\_order` als Kundentabelle verwenden, müssen Sie bei der Erstellung von Metriken auf Kundenebene vorsichtig sein. Betrachten Sie beispielsweise eine durchschnittliche Umsatzmetrik für die Lebensdauer. Diese Metrik wird verwendet, um den durchschnittlichen Umsatz während der gesamten Lebensdauer in Ihrer Kundenbasis zu ermitteln. Dies erfordert zunächst eine neue Spalte, die für jeden Kunden seinen Lebensdauerumsatz zurückgibt. Anschließend müssen Sie den Durchschnitt dieser Spalte berechnen, um den durchschnittlichen Umsatz Ihrer Kunden über die gesamte Lebensdauer zu erhalten.

Wenn Sie die `customer\_entity` -Tabelle, ist jede Zeile ein einzelner Kunde und jeder Kunde ist nur einmal in dieser Tabelle vorhanden. Wenn Sie daher über die Spalte mit dem Lebenszeitumsatz verfügen, müssen Sie lediglich eine durchschnittliche Metrik erstellen. Wenn Sie jedoch die `sales\_order` als Kundentabelle bezeichnet, kann ein Kunde möglicherweise in mehreren Zeilen vorhanden sein. Nach der Einrichtung der Spalte mit dem Lebensdauerumsatz zeigt jede von einem bestimmten Kunden aufgegebene Bestellung (Zeile) den Umsatz dieses Kunden in der Lebensdauer an. Sie möchten diesen Kunden jedoch nur einmal in Ihre Gesamtdurchschnittsmetrik aufnehmen.

Der Trick dabei ist, dass Sie Ihrer Metrik einen Filter hinzufügen müssen, der sicherstellt, dass Sie nur jeden Kunden einmal einbeziehen. Wir empfehlen Ihnen, einen Filtersatz mit dem Namen **Kunden, die wir zählen** wird nach **Bestellnummer des Kunden = 1** (neben anderen Filtern müssen Sie möglicherweise unerwünschte Kunden ausschließen). Durch Hinzufügen dieses Filters wird sichergestellt, dass Sie jeden Kunden nur einmal in eine Metrik auf Kundenebene aufnehmen.

## Produkte und Kategorien

Produkte können mehrere Kategorien aufweisen und Kategorien können für mehrere Produkte verwendet werden. Daher müssen Sie bei der Einrichtung von Analysen auf Kategorieebene darauf achten, die richtigen Definitionen zu verwenden. Möchten Sie die Kategorie der obersten Ebene? Zweite Kategorie? Was passiert, wenn das Produkt in mehrere Kategorien der obersten Ebene fällt?

Stellen Sie sich ein Paar Jeans vor, die in drei verschiedene Kategoriestufen fallen, wie in einer Commerce-Implementierung definiert: &quot;Bekleidung&quot;(oberste Ebene), &quot;Schuhe&quot;(zweite Stufe) und &quot;Pflanzen&quot;(dritte Stufe). Sie können die Performance Ihrer Kategorien nach der Anzahl der verkauften Einheiten analysieren. Die Metrik, die Sie für diese Analyse benötigen, lautet _Verkaufte Artikel_, der auf der `sales\_order\_item` Tabelle. Daher müssen Sie Informationen auf Kategorienebene in die Elementtabelle verschieben. Jede Zeile auf der `sales\_order\_item` -Tabelle ist zugeordnet. `product\_id`Wenn Sie also die Kategorien kennen, die mit einem Produkt verknüpft sind, können Sie diese Informationen in die gewünschte Tabelle übertragen.

Bevor Sie Daten verschieben, müssen Sie zunächst die richtigen Joins und Filter kennen, um sicherzustellen, dass Sie die richtige Kategorie abrufen. Für einige Analysen müssen Sie möglicherweise &quot;Pflanzen&quot;kennen, aber in anderen Analysen ist &quot;Kleidung&quot;möglicherweise besser geeignet. Hierbei handelt es sich um separate Kategorien, die separat identifiziert werden. Wenn Sie wissen, wie die einzelnen Kategorieebenen definiert sind, können Sie den Einzelverkauf der entsprechenden Kategorie für Ihre spezifische Analyse zuordnen.

Stellen Sie sich vor, Sie haben auch eine Kategorie &quot;Unsere Favoriten&quot;auf der Startseite Ihrer Website. Vielleicht haben Sie Ihren Commerce Store so implementiert, dass diese Jeans sowohl in der Kategorie &quot;Bekleidung&quot;als auch in der Kategorie &quot;Unsere Favoriten&quot;enthalten sind. Ist dies der Fall, wird dieses Jeans-Paar mehr als eine Kategorie der obersten Ebene haben. Verschieben Sie in diesem Fall eine Kategorie der obersten Ebene in die `sales\_order\_item` -Tabelle ist nicht ganz sinnvoll, da es mehrere Optionen gibt. Um dies zu berücksichtigen, schlagen wir vor, Ja/Nein-Spalten zu erstellen, die nach bestimmten Kategorien suchen. Beispiel: `Is product in Clothing category?` und `Is product in Our Favorites category?` -Spalten können Sie überprüfen, ob ein Produkt in diese spezifischen Kategorien fällt.
