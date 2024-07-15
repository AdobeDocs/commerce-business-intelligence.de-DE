---
title: Berechnete Spaltentypen
description: Erfahren Sie, wie Sie Spalten erstellen, um Ihre Daten für die Analyse zu erweitern und zu optimieren.
exl-id: 1af79b9e-77ff-4fc6-917a-4e6743b95035
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Berechnete Spaltentypen

* [Gleiche Tabellenberechnungen](#sametable)
* [Eins bis viele Berechnungen](#onetomany)
* [Viele bis eine Berechnungen](#manytoone)
* [Praktische Referenzzuordnung](#map)
* [Erweiterte berechnete Spalten](#advanced)

Im [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md) können Sie Spalten erstellen, um Ihre Daten für die Analyse zu erweitern und zu optimieren. [Auf diese Funktion](../data-warehouse-mgr/creating-calculated-columns.md) kann zugegriffen werden, indem Sie eine beliebige Tabelle im Data Warehouse-Manager auswählen und auf **[!UICONTROL Create New Column]** klicken.

Hier werden die Spaltentypen beschrieben, die Sie mit dem Data Warehouse Manager erstellen können. Sie umfasst auch die Beschreibung, einen visuellen Durchgang dieser Spalte und eine [Referenz-Zuordnung](#map) aller Eingaben, die zum Erstellen einer Spalte erforderlich sind. Es gibt drei Möglichkeiten, berechnete Spalten zu erstellen:

1. [Dieselbe Tabelle berechnete Spalten](#sametable)
1. [Eins-zu-viele berechnete Spalten](#onetomany)
1. [Zahlreiche berechnete Spalten](#manytoone)

## Dieselbe Tabelle berechnete Spalten {#sametable}

Diese Spalten werden mithilfe von Eingabespalten aus derselben Tabelle erstellt.

### Alter {#age}

Eine Spalte mit dem berechneten Alter gibt die Anzahl der Sekunden zwischen der aktuellen Zeit und einer bestimmten Eingabezeit zurück.

Im folgenden Beispiel wird `Seconds since customer's most recent order` in der Tabelle `customers` erstellt. Dies kann verwendet werden, um Benutzerlisten von Kunden zu erstellen, die innerhalb von `X days` keine Käufe getätigt haben (manchmal auch als &quot;Kurven&quot;bezeichnet).

![](../../assets/age.gif)

### Währungsumrechner

Eine Spalte mit Währungsumrechnern konvertiert die native Währung einer Spalte in eine gewünschte neue Währung.

Im folgenden Beispiel wird `base\_grand\_total In AED` erstellt, wobei die `base\_grand\_total` aus der nativen Währung in die AED-Tabelle in `sales\_flat\_order` konvertiert wird. Diese Spalte eignet sich gut für Geschäfte mit mehreren Währungen, die in ihrer Landeswährung gemeldet werden möchten.

Bei Commerce-Clients speichert das Feld `base\_currency\_code` normalerweise native Währungen. Das Feld `Spot Time` sollte mit dem Datum übereinstimmen, das in Ihren Metriken verwendet wird.

![](../../assets/currency_converter.png)

## Eins-zu-viele berechnete Spalten {#onetomany}

`One-to-Many` Spalten [verwenden einen Pfad zwischen zwei Tabellen](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md). Dieser Pfad impliziert immer eine einzige Tabelle, in der ein Attribut lebt, und eine viele Tabelle, in der dieses Attribut &quot;nach unten verschoben&quot;wird. Der Pfad kann als `foreign key--primary key` -Beziehung beschrieben werden.

### Verbundene Spalte {#joined}

Eine verknüpfte Spalte verschiebt ein Attribut auf der einen Tabelle *in* auf die nViele-Tabelle. Das klassische Beispiel von eins/n sind Kunden (eins) und Bestellungen (viele).

Im folgenden Beispiel wird die Dimension `Customer's group\_id` in die Tabelle `orders` zusammengefügt.

![](../../assets/joined_column.gif)

## Zahlreiche berechnete Spalten {#manytoone}

Diese Spalten verwenden dieselben Pfade wie Eins-zu-viele-Spalten, weisen aber Daten in die entgegengesetzte Richtung. Die Spalte wird auf der einen Seite des Pfads erstellt, im Gegensatz zu den vielen Seiten. Aufgrund dieser Beziehung muss der Wert in der Spalte eine Aggregation sein, d. h. eine mathematische Operation, die an den Datenpunkten auf der vielen Seite durchgeführt wird. Es gibt viele Anwendungsfälle dafür und einige sind unten aufgeführt.

### Count {#count}

Dieser Typ der berechneten Spalte gibt die Anzahl der Werte für die viele Tabelle *auf* in der einen Tabelle zurück.

Im folgenden Beispiel wird die Dimension `Customer's lifetime number of canceled orders` in der Tabelle `customers` erstellt (mit einem Filter für `orders.status`).

![](../../assets/many_to_one.gif){: width=&quot;699&quot; height=&quot;351&quot;}

### Summe {#sum}

Eine berechnete Spalte ist die Summe der Werte der Tabelle `many` auf der einen Tabelle.

Damit können Sie Dimensionen auf Kundenebene wie `Customer's lifetime revenue` erstellen.

### Min. oder Max {#minmax}

Eine berechnete Min.- oder Max.-Spalte gibt den kleinsten oder größten Datensatz zurück, der auf vielen Seiten vorhanden ist.

Damit können Sie Dimensionen auf Kundenebene wie `Customer's first order date` erstellen.

### Exists {#exists}

Eine berechnete Spalte ist ein Binärtest, der bestimmt, ob ein Datensatz auf einer Vielzahl von Seiten vorhanden ist. Anders ausgedrückt: Die neue Spalte gibt einen `1` zurück, wenn der Pfad mindestens eine Zeile in jeder Tabelle verbindet, und `0`, wenn keine Verbindung hergestellt werden kann.

Diese Art von Dimension kann beispielsweise bestimmen, ob ein Kunde ein bestimmtes Produkt erworben hat. Mithilfe eines Joins zwischen einer `customers` -Tabelle und einer `orders` -Tabelle, eines Filters für ein bestimmtes Produkt, kann eine Dimension `Customer has purchased Product X?` erstellt werden.

## Praktische Referenzzuordnung {#map}

Wenn Sie beim Erstellen einer berechneten Spalte Schwierigkeiten haben, sich vorzumerken, was alle Eingaben enthalten, halten Sie diese Referenzkarte beim Erstellen bereit:

![](../../assets/merged_reference_map.png)

## Erweiterte berechnete Spalten {#advanced}

Bei Ihrer Suche nach einer Analyse und Beantwortung von Fragen zu Ihrem Unternehmen kann es vorkommen, dass Sie nicht in der Lage sind, die exakte Spalte zu erstellen, die Sie benötigen.

Um eine schnelle Umgehung sicherzustellen, empfiehlt Adobe, sich im Handbuch [Erweiterte berechnete Spaltentypen](../../data-analyst/data-warehouse-mgr/adv-calc-columns.md) zu informieren, welche Spalten das Adobe-Supportteam erstellen kann. Dieses Thema behandelt auch die Informationen, die Sie zur Erstellung der Spalte benötigen - schließen Sie sie in Ihre Anfrage ein.

## Verwandte Dokumentation

* [Berechnete Spalten erstellen](../../data-analyst/data-warehouse-mgr/creating-calculated-columns.md)
* [Pfade für berechnete Spalten erstellen/löschen](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md)
* [Grundlegendes zu und Auswerten von Tabellenbeziehungen](../../data-analyst/data-warehouse-mgr/table-relationships.md)
