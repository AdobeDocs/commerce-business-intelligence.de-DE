---
title: SQL-berechnete Spalte erstellen und verwenden
description: Erfahren Sie, wie erweiterte Spalten in Form von SQL-Berechnungsspalten in der neuen Adobe Commerce Intelligence-Architektur erstellt werden können.
exl-id: f16e4ee4-ed73-4ddb-b701-1fe3db14346a
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, SQL Report Builder, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# SQL-berechnete Spalte erstellen

In diesem Thema werden Zweck und Verwendung der Variablen `Calculation` Spaltentyp, der Tabellen mithilfe der [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md). Im Folgenden werden die Funktionsweise von SQL-Berechnungen, ihre Verwendung, der Prozess zur Erstellung einer SQL-Berechnung und zwei Beispiele erläutert.

**Erklärung**

In der Vergangenheit wurden Spalten `advanced` kann nur von einem Analytiker des Customer Success-Teams hier unter [!DNL Adobe Commerce Intelligence]. Jetzt liegt die gesamte Leistung in den Händen des Endbenutzers, und erweiterte Spalten können in Form von `SQL Calculation` Spalten in der neuen [!DNL Commerce Intelligence] Architektur.

Die `Calculation` Der nun als Option im Data Warehouse-Manager verfügbare Spaltentyp ist derselbe Tabellenvorgang, mit dem Sie die Tabellenspalten mithilfe der PostgreSQL-Logik umwandeln können. Dokumentation zu den Funktionen und Operatoren, die in der `Calculation` Spaltentyp finden Sie auf der PostgreSQL-Website. [here](https://www.postgresql.org/docs/9.6/functions.html).

Die verschiedenen Spalten, die mit der `Calculation` -Spalte ist fast unbegrenzt, aber die meisten Spalten können mit IF-THEN -Anweisungen und Arithmetik erstellt werden, die in den Beispielen unten verwendet wird.

**Beispiel 1: Ist die letzte Bestellung des Kunden?**

Die meisten Konten haben eine Spalte namens `Is customer's last order?` auf `orders` -Tabelle, um Analysen zu wiederholten Kaufraten und geschlagenen Kunden durchzuführen. Wenn Ihr Konto auf der neuen Architektur basiert, wird diese Spalte mithilfe einer `Calculation` und im folgenden Screenshot angezeigt werden:

![](../../assets/Is_customer_s_last_order.png)

Die `Is customer's last order?` -Spalte verwendet Eingaben `Customer's lifetime number of orders` und `Customer's order number` Alias `A` und `B` bzw.

Die Bedeutung von PostgreSQL lautet Zeile für Zeile:

* case: Startet eine Reihe von If - Then -Anweisungen
* when `A` ist null oder `B` null ist, dann null: Wenn eine der Eingaben leer ist, sollte die Ausgabe ebenfalls leer sein. Dies verhindert SQL-Fehler
* when `A=B` then `Yes`: Wenn `Customer's lifetime number of orders` gleich `Customer's order number` für diese Zeile und dann `Yes`. Wenn ein Kunde also vier Bestellungen aufgegeben hat, würde die Zeile für die vierte Bestellung zurückgegeben `Yes` für `Is customer's last order?`
* else `No`: Wenn keine der anderen Anweisungen erfüllt ist, geben Sie `No`
* end: Hierdurch wird die If - Then -Anweisung beendet.

Die möglichen Werte, die von dieser Spalte (`NULL`, `Yes`, `No`) Zeichen enthalten, die keine Zahl sind, daher ist der Datentyp hier &quot;String&quot;.

**Beispiel 2: Gesamtwert des Bestellartikels (Menge * Preis)**

Viele Kunden analysieren gerne den Umsatz auf Artikelebene und teilen ihn nach Feldern wie `product name` oder `category`. Die meisten Datenbanken geben Ihnen nicht den Umsatz aus einem Produkt in einer Bestellung, sondern die Menge, die in der Bestellung verkauft wird, und den Preis des Artikels.

Um Produktumsatzanalysen zu ermöglichen, verfügen die meisten Konten über eine Spalte mit dem Namen `Order item total value (quantity * price)` auf `Orders Items` Tabelle. Wenn Ihr Konto auf der neuen Architektur basiert, wird diese Spalte auch mithilfe einer `Calculation` und im folgenden Screenshot angezeigt werden:

![](../../assets/Order_item_total_value.png)

Im Commerce-Schema wird die `Order item total value (quantity * price)` -Spalte verwendet Eingaben `qty ordered` und `base price` Alias `A` und `B` bzw.

Die Werte, die von dieser neuen Spalte zurückgegeben werden, sind in Dollar und Cent angegeben. Daher ist der richtige Datentyp `Decimal(10,2)`.

**Mechanik**

Eine neue `Calculation` kann einer Tabelle durch Navigieren zu **[!DNL Manage Data > Data Warehouse]** wie unten gezeigt:

![](../../assets/blobid2.png)

Hier können Sie eine `Calculation` durch die folgenden Schritte aus:

1. Wählen Sie die Tabelle aus, der Sie die `Calculation` Spalte.
1. Klicken Sie auf der richtigen Tabelle auf **[!UICONTROL Create New Column]** oben rechts auf dem Bildschirm.
1. Aus dem `Select a definition` Dropdown-Liste auswählen `Same Table`.
1. Auswählen `Calculation` als `column definition equation`.
1. Geben Sie den Spaltennamen ein.
1. Wählen Sie die `input` Spalten aus der Tabelle, die in der Logik für die neue Spalte verwendet werden. Jede hinzugefügte Spalte erhält einen Briefalias, sodass die erste Spalte `A`, ist der zweite `B` und so weiter.
1. Geben Sie im Fenster die PostgreSQL-Logik für Ihre neue Spalte mit den Briefaliasen Ihrer Eingaben ein. Die SQL-Berechnung sollte auf eine einzige Spaltendefinition beschränkt sein, einschließlich der gesamten Logik zwischen den SELECT- und FROM-Anweisungen einer SQL-Abfrage. SQL-Schlüsselwörter, die einen der eingegebenen Buchstaben verwenden, sollten in Kleinbuchstaben eingegeben werden. Wenn Sie beispielsweise die `CASE` -Anweisung, sollte es in Kleinbuchstaben geschrieben werden - `case`. Das System geht davon aus, dass ein Großbuchstabe `A` bezieht sich auf eine der Eingaben.
1. Wählen Sie den entsprechenden Datentyp aus.
   * `Integer` - Ganzzahl
   * `Decimal(10,2)` - eine Dezimalzahl mit 10 Gesamtzahlen, von denen 2 rechts neben dem Dezimalpunkt liegen
   * `String` - Beliebiger Text- oder Zeichensatztyp, der keine Zahlen verwendet
   * `Datetime` - yyyy-MM-dd hh:mm:ss format

1. Klicken **[!UICONTROL test column]**. Dadurch wird eine Liste mit fünf Testwerten für jede Ihrer Eingaben generiert und das Ergebnis der Logik aus Schritt 6 für jeden Satz von Testwerten angezeigt. Wenn ein Teil der SQL einen Fehler erzeugt, wird die entsprechende Fehlermeldung zurückgegeben. Beispielergebnisse können nur generiert werden, wenn alle Eingabespalten native Felder sind. Wenn eine der Eingabespalten berechnete Spalten ist, müssen Sie die Ergebnisse validieren, indem Sie die Spalte zu einer Metrik hinzufügen und im Visual Report Builder anzeigen

1. Wenn Sie mit den Ergebnissen zufrieden sind, klicken Sie auf **[!UICONTROL Save]**. Die Spalte ermöglicht die Verwendung.
