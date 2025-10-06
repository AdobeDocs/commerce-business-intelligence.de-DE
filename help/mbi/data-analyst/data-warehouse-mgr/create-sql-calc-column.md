---
title: Erstellen und Verwenden einer berechneten SQL-Spalte
description: Erfahren Sie, wie erweiterte Spalten in Form von SQL-Berechnungsspalten in der neuen Adobe Commerce Intelligence-Architektur erstellt werden können.
exl-id: f16e4ee4-ed73-4ddb-b701-1fe3db14346a
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, SQL Report Builder, Commerce Tables
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---

# Erstellen einer berechneten SQL-Spalte

In diesem Abschnitt werden Zweck und Verwendungszwecke des `Calculation` Spaltentyps beschrieben, der mithilfe des [Data Warehouse Managers} zu Tabellen hinzugefügt ](../data-warehouse-mgr/tour-dwm.md) kann. Im Folgenden wird erläutert, was SQL-Berechnungen bewirken, warum sie verwendet werden und wie eine SQL-Berechnung erstellt wird. Nachfolgend werden zwei Beispiele beschrieben.

**Erläuterung**

Früher konnten Spalten, die als `advanced` eingestuft wurden, nur von einem Analyst im Customer Success-Team hier bei [!DNL Adobe Commerce Intelligence] erstellt werden. Jetzt liegt die gesamte Macht in den Händen des Endbenutzers, und erweiterte Spalten können in Form von `SQL Calculation` Spalten in der neuen [!DNL Commerce Intelligence]-Architektur erstellt werden.

Der `Calculation` Spaltentyp, der jetzt als Option im Data Warehouse Manager verfügbar ist, ist ein Tabellenvorgang, mit dem Sie die Spalten einer Tabelle mithilfe der PostgreSQL-Logik umwandeln können. Dokumentationen zu den Funktionen und Operatoren, die im `Calculation` Spaltentyp verwendet werden können, finden Sie auf der PostgreSQL-Website [hier](https://www.postgresql.org/docs/9.6/functions.html).

Die verschiedenen Spalten, die mit der `Calculation` Spalte erstellt werden können, sind nahezu unbegrenzt, aber die meisten Spalten können mit IF-THEN-Anweisungen und einfacher Arithmetik erstellt werden, die in den folgenden Beispielen verwendet wird.

**Beispiel 1: Ist die letzte Bestellung des Kunden?**

Die meisten Konten verfügen über eine Spalte namens `Is customer's last order?` in ihrer `orders`, um Analysen zu Wiederholungskäuferraten und abgewanderten Kunden durchzuführen. Wenn sich Ihr Konto auf der neuen Architektur befindet, wird diese Spalte mithilfe einer `Calculation` Spalte erstellt und ist im folgenden Screenshot zu sehen:

![SQL-Definition der berechneten Spalte zur Identifizierung der letzten Bestellung eines Kunden](../../assets/Is_customer_s_last_order.png)

Die Spalte `Is customer's last order?` verwendet die Eingaben `Customer's lifetime number of orders` und `Customer's order number` Alias `A` bzw. `B`.

Zeile für Zeile hat PostgreSQL folgende Bedeutung:

* case: Dies startet eine Reihe von If - Then-Anweisungen
* Wenn `A` null oder `B` null ist, dann null: Wenn eine der Eingaben leer ist, sollte die Ausgabe ebenfalls leer sein. Dadurch sollen SQL-Fehler verhindert werden
* Wenn `A=B` dann `Yes`: Wenn `Customer's lifetime number of orders` gleich `Customer's order number` für diese Zeile ist, dann `Yes` zurückgeben. Wenn also ein Kunde vier Bestellungen aufgegeben hat, würde die Zeile für die vierte Bestellung `Yes` für `Is customer's last order?` zurückgeben
* else `No`: Wenn keine der anderen Aussagen erfüllt ist, `No` zurückgeben
* end: Damit werden die If - Then-Anweisungen beendet

Die möglichen Werte, die von dieser Spalte zurückgegeben werden können (`NULL`, `Yes`, `No`) enthalten Nicht-Zahlenzeichen, sodass der Datentyp hier „String“ ist.

**Beispiel 2: Gesamtwert des Auftragspostens (Menge * Preis)**

Viele Kunden analysieren den Umsatz gerne auf Artikelebene, indem sie ihn nach Feldern wie `product name` oder `category` aufteilen. Die meisten Datenbanken geben einem nicht den Umsatz eines Produkts in einer Bestellung, sondern sie liefern die Menge, die in der Bestellung verkauft wird, und den Preis des Artikels.

Um Analysen des Produktumsatzes zu ermöglichen, verfügen die meisten Konten in ihrer `Order item total value (quantity * price)` über eine Spalte mit dem Namen `Orders Items`. Wenn sich Ihr Konto auf der neuen Architektur befindet, wird diese Spalte auch mit einer `Calculation` Spalte erstellt und ist im folgenden Screenshot zu sehen:

![SQL-Definition der berechneten Spalte für den Gesamtwert des Bestellartikels](../../assets/Order_item_total_value.png)

Im Commerce-Schema verwendet die `Order item total value (quantity * price)` die `qty ordered` Eingaben und `base price` Alias `A` bzw. `B`.

Die von dieser neuen Spalte zurückgegebenen Werte lauten in Dollar und Cent, sodass der richtige Datentyp `Decimal(10,2)` ist.

**Mechanik**

Eine neue `Calculation` Spalte kann zu einer Tabelle hinzugefügt werden, indem Sie zu **[!DNL Manage Data > Data Warehouse]** navigieren, wie unten dargestellt:

![Tabellenansicht mit berechneten Spaltenergebnissen](../../assets/blobid2.png)

Gehen Sie wie folgt vor, um eine `Calculation` Spalte zu erstellen:

1. Wählen Sie die Tabelle aus, der Sie die `Calculation` hinzufügen möchten.
1. Klicken Sie auf der richtigen Tabelle oben rechts im Bildschirm auf **[!UICONTROL Create New Column]**.
1. Wählen Sie im Dropdown-Menü `Select a definition` die Option `Same Table` aus.
1. Wählen Sie `Calculation` als `column definition equation` aus.
1. Geben Sie den Spaltennamen ein.
1. Wählen Sie die `input` Spalten aus der Tabelle aus, die in der Logik für Ihre neue Spalte verwendet werden. Jede hinzugefügte Spalte erhält einen Alias für den Brief, sodass die erste Spalte `A`, die zweite `B` wird usw.
1. Geben Sie im Fenster die PostgreSQL-Logik für Ihre neue Spalte mithilfe der Buchstabenaliase Ihrer Eingaben ein. Die SQL-Berechnung sollte auf eine einzelne Spaltendefinition beschränkt sein, einschließlich der gesamten Logik zwischen den SELECT- und FROM-Anweisungen einer SQL-Abfrage. SQL-Schlüsselwörter, die einen der Eingabebriefe verwenden, sollten in Kleinbuchstaben geschrieben werden. Wenn Sie beispielsweise die Anweisung `CASE` verwenden, sollte sie in Kleinbuchstaben geschrieben werden - `case`. Das System geht davon aus, dass ein `A` in Großbuchstaben auf eine der Eingaben verweist.
1. Wählen Sie den entsprechenden Datentyp aus.
   * `Integer` - Ganze Zahl
   * `Decimal(10,2)` - Eine Dezimalzahl mit 10 Gesamtziffern, von denen sich 2 rechts neben dem Dezimalpunkt befinden
   * `String` - Jeder Text- oder Zeichenfolgentyp, bei dem andere Zahlen als Zahlen verwendet werden
   * `Datetime` - `yyyy-MM-dd hh:mm:ss`

1. Klicken Sie auf **[!UICONTROL test column]**. Dadurch wird eine Liste von fünf Testwerten für jede Ihrer Eingaben generiert und das Ergebnis der Logik aus Schritt 6 für jeden Satz von Testwerten angezeigt. Wenn ein Teil der SQL einen Fehler erzeugt, wird die entsprechende Fehlermeldung zurückgegeben. Beispielergebnisse können nur generiert werden, wenn alle Eingabespalten native Felder sind. Wenn es sich bei einer der Eingabespalten um berechnete Spalten handelt, müssen Sie die Ergebnisse überprüfen, indem Sie die Spalte zu einer Metrik hinzufügen und in der Visual Report Builder anzeigen

1. Wenn Sie mit den Ergebnissen zufrieden sind, klicken Sie auf **[!UICONTROL Save]**. Die Spalte ermöglicht die Verwendung.
