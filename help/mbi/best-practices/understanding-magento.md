---
title: Ihre [!DNL Commerce Intelligence] Umgebung
description: Erfahren Sie mehr über die Arbeit mit und die Verbesserung Ihrer [!DNL Commerce Intelligence] Umgebung.
exl-id: 601b5fba-da02-4cc8-96ed-147c24f326f9
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# Ihre [!DNL Adobe Commerce Intelligence] Umgebung

Achten Sie bei der Analyse Ihrer Commerce-Daten auf diese Faktoren und häufige falsche Vorstellungen. Wenn Sie Unterstützung benötigen, um sicherzustellen, dass Sie Ihr Commerce-Schema richtig verwenden, zögern Sie nicht, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

## [!DNL entity\_id]

Viele Ihrer Tabellen enthalten eine Spalte mit dem Namen `entity\_id`. In jeder Tabelle mit `entity\_id`, wird diese Spalte verwendet, um eindeutige Zeilen zu identifizieren.

Beispiel: Jede Zeile im `sales\_order` -Tabelle ist eine eindeutige Reihenfolge. Der Primärschlüssel in dieser Tabelle heißt `entity\_id`. Diese Spalte kann als `order\_id`. In einer separaten Tabelle `customer\_entity`, stellt jede Zeile einen Unique Customer dar. Der Primärschlüssel in dieser Tabelle wird auch als `entity\_id`, der als `customer\_id`.

In diesen Tabellen wird `sales\_order.entity\_id` ist nicht gleich `customer\_entity.entity\_id`. Dies gilt für alle Tabellensätze mit `entity\_id`: `table\_A.entity\_id` ist nicht gleich `table\_B.entity\_id`.

## [!DNL Guest orders]

Wenn Sie Kunden erlauben, von Ihrer Site aus zu bestellen, ohne ein Konto zu haben (Gastaufträge), werden diese Kunden nicht als Zeile in Ihrer `customer\_entity` Tabelle. Außerdem hat jede von einem Gast aufgegebene Bestellung eine Null `customer\_id` -Wert auf `sales\_order` Tabelle.

Wenn Sie das Verhalten Ihrer Gäste im Laufe der Zeit verfolgen möchten, müssen daher alle Spalten auf Kundenebene auf der Grundlage der Variablen `sales\_order` mit einer Kunden-ID, z. B. `customer\_email`.

Wenn Sie die `sales\_order` als Kundentabelle verwenden, müssen Sie bei der Erstellung von Metriken auf Kundenebene vorsichtig sein. Betrachten Sie beispielsweise eine durchschnittliche Umsatzmetrik für die Lebensdauer. Diese Metrik wird verwendet, um den durchschnittlichen Umsatz während der gesamten Lebensdauer in Ihrer Kundenbasis zu ermitteln. Dies erfordert zunächst eine neue Spalte, die für jeden Kunden seinen Lebensdauerumsatz zurückgibt. Anschließend müssen Sie den Durchschnitt dieser Spalte berechnen, um den durchschnittlichen Umsatz Ihrer Kunden über die gesamte Lebensdauer zu erhalten.

Wenn Sie die `customer\_entity` -Tabelle, ist jede Zeile ein einzelner Kunde und jeder Kunde ist nur einmal in dieser Tabelle vorhanden. Wenn Sie daher über die Spalte mit dem Lebenszeitumsatz verfügen, müssen Sie lediglich eine durchschnittliche Metrik erstellen. Wenn Sie jedoch die `sales\_order` als Kundentabelle bezeichnet, kann ein Kunde möglicherweise in mehreren Zeilen vorhanden sein. Nach der Einrichtung der Spalte mit dem Lebensdauerumsatz zeigt jede von einem bestimmten Kunden aufgegebene Bestellung (Zeile) den Lebensdauerumsatz dieses Kunden an. Sie möchten jedoch diesen Kunden nur einmal in Ihre Gesamtdurchschnittsmetrik einbeziehen.

Der Trick dabei ist, dass Sie Ihrer Metrik einen Filter hinzufügen müssen, der sicherstellt, dass Sie nur jeden Kunden einmal einbeziehen. Adobe empfiehlt Ihnen, einen Filtersatz mit dem Namen **Kunden, die wir zählen** , die **Bestellnummer des Kunden = 1** (neben anderen Filtern müssen Sie möglicherweise unerwünschte Kunden ausschließen). Durch Hinzufügen dieses Filters wird sichergestellt, dass Sie jeden Kunden nur einmal in eine Metrik auf Kundenebene aufnehmen.

## Produkte und Kategorien

Produkte können mehrere Kategorien aufweisen und Kategorien können für mehrere Produkte verwendet werden. Daher müssen Sie bei der Einrichtung von Analysen auf Kategorieebene darauf achten, die richtigen Definitionen zu verwenden. Möchten Sie die Kategorie der obersten Ebene? Zweite Kategorie? Was passiert, wenn das Produkt in mehrere Kategorien der obersten Ebene fällt?

Stellen Sie sich ein Paar von Jeans vor, die in drei verschiedene Kategoriestufen fallen, wie in einer Commerce-Implementierung definiert: &quot;Bekleidung&quot;(oberste Ebene), &quot;Schuhe&quot;(zweite Ebene) und &quot;Pants&quot;(dritte Ebene). Sie können die Performance Ihrer Kategorien nach der Anzahl der verkauften Einheiten analysieren. Die für diese Analyse benötigte Metrik ist _Verkaufte Artikel_, der auf der `sales\_order\_item` Tabelle. Daher müssen Sie Informationen auf Kategorienebene in die Elementtabelle verschieben. Jede Zeile auf der `sales\_order\_item` -Tabelle ist zugeordnet. `product\_id`Wenn Sie also die Kategorien kennen, die mit einem Produkt verknüpft sind, können Sie diese Informationen in die gewünschte Tabelle übertragen.

Bevor Sie Daten verschieben, müssen Sie zunächst die richtigen Joins und Filter kennen, um sicherzustellen, dass Sie die richtige Kategorie abrufen. Für einige Analysen müssen Sie möglicherweise &quot;Pflanzen&quot;kennen, aber in anderen Analysen ist &quot;Kleidung&quot;möglicherweise besser geeignet. Hierbei handelt es sich um separate Kategorien, die separat identifiziert werden. Wenn Sie wissen, wie die einzelnen Kategorienebenen definiert sind, können Sie den Stückumsatz der entsprechenden Kategorie für Ihre spezifische Analyse zuordnen.

Stellen Sie sich vor, Sie haben auch eine `Our Favorites` Kategorie der obersten Ebene auf der Startseite Ihrer Website. Vielleicht haben Sie Ihren Commerce Store implementiert, um diese Jeans in beide `Clothing` und `Our Favorites` Kategorie. Wenn ja, hat dieses Jeans-Paar mehr als eine Top-Level-Kategorie. Verschieben Sie in diesem Fall eine einzelne Kategorie der obersten Ebene in die `sales\_order\_item` -Tabelle ist nicht ganz sinnvoll, da es mehrere Optionen gibt. Um dies zu berücksichtigen, schlägt Adobe vor, Ja/Nein-Spalten zu erstellen, die nach bestimmten Kategorien suchen. Beispiel: `Is product in Clothing category?` und `Is product in Our Favorites category?` -Spalten können Sie überprüfen, ob ein Produkt in diese spezifischen Kategorien fällt.
