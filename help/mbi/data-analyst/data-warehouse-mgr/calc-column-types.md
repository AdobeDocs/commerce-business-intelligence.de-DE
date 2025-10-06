---
title: Berechnete Spaltentypen
description: Erfahren Sie, wie Sie Spalten erstellen, um Ihre Daten für die Analyse zu ergänzen und zu optimieren.
exl-id: 1af79b9e-77ff-4fc6-917a-4e6743b95035
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Berechnete Spaltentypen

* [Berechnungen derselben Tabelle](#sametable)
* [Eins zu viele Berechnungen](#onetomany)
* [Viele-zu-eins-Berechnungen](#manytoone)
* [Praktische Referenzkarte](#map)
* [Erweiterte berechnete Spalten](#advanced)

Im [Data Warehouse Manager](../data-warehouse-mgr/tour-dwm.md) können Sie Spalten erstellen, um Ihre Daten für die Analyse zu erweitern und zu optimieren. [Diese Funktion](../data-warehouse-mgr/creating-calculated-columns.md) können Sie aufrufen, indem Sie eine beliebige Tabelle im Data Warehouse Manager auswählen und auf **[!UICONTROL Create New Column]** klicken.

In diesem Thema werden die Spaltentypen beschrieben, die Sie mit dem Data Warehouse Manager erstellen können. Es behandelt auch die Beschreibung, eine visuelle Anleitung für diese Spalte und eine [Referenzzuordnung](#map) aller Eingaben, die zum Erstellen einer Spalte erforderlich sind. Es gibt drei Möglichkeiten, berechnete Spalten zu erstellen:

1. [Berechnete Spalten der gleichen Tabelle](#sametable)
1. [1:n-berechnete Spalten](#onetomany)
1. [n:1-berechnete Spalten](#manytoone)

## Berechnete Spalten der gleichen Tabelle {#sametable}

Diese Spalten werden mit Eingabespalten aus derselben Tabelle erstellt.

### Alter {#age}

Eine berechnete Altersspalte gibt die Anzahl Sekunden zwischen der aktuellen Zeit und einer Eingabezeit zurück.

Im folgenden Beispiel wird `Seconds since customer's most recent order` in der `customers`-Tabelle erstellt. Dies kann verwendet werden, um Benutzerlisten von Kunden zu erstellen, die innerhalb von `X days` keine Käufe getätigt haben (manchmal auch als Abwanderung bezeichnet).

![Animierte Demonstration der Erstellung einer Altersberechnungsspalte](../../assets/age.gif)

### Währungsumrechner

Eine berechnete Spalte vom Währungsumrechner konvertiert die native Währung einer Spalte in die gewünschte neue Währung.

Im folgenden Beispiel wird ein `base\_grand\_total In AED` erstellt, bei dem der `base\_grand\_total` aus der nativen Währung in der `sales\_flat\_order` in AED konvertiert wird. Diese Spalte eignet sich gut für Geschäfte mit mehreren Währungen, die in ihrer lokalen Währung berichten möchten.

Für Commerce-Clients speichert das `base\_currency\_code` normalerweise native Währungen. Das `Spot Time` sollte mit dem in Ihren Metriken verwendeten Datum übereinstimmen.

![Spaltenkonfiguration des Währungsumrechners berechnet](../../assets/currency_converter.png)

## 1:n-berechnete Spalten {#onetomany}

`One-to-Many` Spalten [verwenden einen Pfad zwischen zwei Tabellen](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md). Dieser Pfad impliziert immer eine Tabelle, in der ein Attribut vorhanden ist, und eine Tabelle mit vielen Tabellen, in denen dieses Attribut „neu positioniert“ wird. Der Pfad kann als `foreign key--primary key` Beziehung beschrieben werden.

### Verbundene Spalte {#joined}

Eine verbundene Spalte verschiebt ein Attribut in der einen Tabelle *in* der vielen Tabelle. Das klassische Beispiel für „ein“ oder „viele“ sind „Kunden“ (eine) und „Bestellungen“ (viele).

Im folgenden Beispiel wird die Dimension `Customer's group\_id` mit der `orders` verbunden.

![Animierte Demonstration der Erstellung von verknüpften Spalten-Verknüpfungstabellen](../../assets/joined_column.gif)

## n:1-berechnete Spalten {#manytoone}

Diese Spalten verwenden dieselben Pfade wie die Eins-zu-viele-Spalten, verweisen jedoch auf Daten in die entgegengesetzte Richtung. Die Spalte wird auf der einen Seite des Pfads erstellt, im Gegensatz zu den vielen Seiten. Aufgrund dieser Beziehung muss der Wert in der Spalte eine Aggregation sein, d. h. eine mathematische Operation, die für die Datenpunkte auf der Viele-Seite durchgeführt wird. Es gibt viele Anwendungsfälle dafür, und einige davon sind unten aufgeführt.

### Count {#count}

Dieser Typ der berechneten Spalte gibt die Anzahl der Werte in der vielen Tabelle *auf* der einen Tabelle zurück.

Im folgenden Beispiel wird die Dimension `Customer's lifetime number of canceled orders` für die `customers`-Tabelle erstellt (mit einem Filter für `orders.status`).

![Animierte Demonstration der Viele-zu-eins-Spaltenaggregation](../../assets/many_to_one.gif){: width="699" height="351"}

### Summe {#sum}

Eine berechnete Summenspalte ist die Summe der Werte in der `many` Tabelle auf der einen Tabelle.

Dies kann verwendet werden, um Dimensionen auf Kundenebene wie `Customer's lifetime revenue` zu erstellen.

### Min oder Max {#minmax}

Eine berechnete Min.- oder Max. Spalte gibt den kleinsten oder größten Datensatz zurück, der auf der Viele-Seite vorhanden ist.

Dies kann verwendet werden, um Dimensionen auf Kundenebene wie `Customer's first order date` zu erstellen.

### Vorhanden {#exists}

Eine berechnete Spalte ist ein binärer Test, der das Vorhandensein eines Datensatzes auf der Viele-Seite bestimmt. Mit anderen Worten: Die neue Spalte gibt eine `1` zurück, wenn der Pfad mindestens eine Zeile in jeder Tabelle verbindet, und `0`, wenn keine Verbindung hergestellt werden kann.

Diese Art von Dimension kann beispielsweise bestimmen, ob ein Kunde jemals ein bestimmtes Produkt gekauft hat. Mithilfe einer Verknüpfung zwischen einer `customers` und `orders` Tabelle kann ein Filter für ein bestimmtes Produkt, eine `Customer has purchased Product X?` erstellt werden.

## Praktische Referenzkarte {#map}

Wenn Sie beim Erstellen einer berechneten Spalte nicht genau wissen können, was alle Eingaben sind, sollten Sie diese Referenzzuordnung beim Erstellen von Folgendem zur Hand haben:

![Referenzzuordnung mit zusammengeführter berechneter Spaltenkonfiguration](../../assets/merged_reference_map.png)

## Erweiterte berechnete Spalten {#advanced}

Bei der Analyse und Beantwortung von Fragen zu Ihrem Unternehmen kann es vorkommen, dass Sie nicht in der Lage sind, die gewünschte Spalte zu erstellen.

Um eine schnelle Umstellung zu gewährleisten, empfiehlt Adobe, das Handbuch [Erweiterte berechnete Spaltentypen](../../data-analyst/data-warehouse-mgr/adv-calc-columns.md) zu lesen, um zu sehen, welche Art von Spalten das Adobe-Supportteam erstellen kann. In diesem Thema werden auch die Informationen behandelt, die Sie zum Erstellen der Spalte benötigen - schließen Sie sie in Ihre Anfrage ein.

## Verwandte Dokumentation

* [Berechnete Spalten erstellen](../../data-analyst/data-warehouse-mgr/creating-calculated-columns.md)
* [Erstellen/Löschen von Pfaden für berechnete Spalten](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md)
* [Verstehen und Auswerten von Tabellenbeziehungen](../../data-analyst/data-warehouse-mgr/table-relationships.md)
