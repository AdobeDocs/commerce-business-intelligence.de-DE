---
title: SQL-berechnete Spalte erstellen und verwenden
description: Erfahren Sie, wie erweiterte Spalten in Form von SQL-Berechnungsspalten in der neuen Adobe Commerce Intelligence-Architektur erstellt werden können.
exl-id: f16e4ee4-ed73-4ddb-b701-1fe3db14346a
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, SQL Report Builder, Commerce Tables
source-git-commit: 8090c2e0f17f0e8d3bdec668ce546206bf024691
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---

# SQL-berechnete Spalte erstellen

In diesem Thema werden Zweck und Verwendung des Spaltentyps `Calculation` beschrieben, der mithilfe des Data Warehouse-Managers [2} zu Tabellen hinzugefügt werden kann. ](../data-warehouse-mgr/tour-dwm.md) Im Folgenden werden die Funktionsweise von SQL-Berechnungen, ihre Verwendung, der Prozess zur Erstellung einer SQL-Berechnung und zwei Beispiele erläutert.

**Erklärung**

In der Vergangenheit konnten Spalten, die als `advanced` galten, nur von einem Analytiker im Customer Success Team hier bei [!DNL Adobe Commerce Intelligence] erstellt werden. Jetzt ist der gesamte Strom in den Händen des Endbenutzers, und erweiterte Spalten können in Form von `SQL Calculation` Spalten in der neuen [!DNL Commerce Intelligence]-Architektur erstellt werden.

Der Spaltentyp `Calculation` , der jetzt als Option im Data Warehouse Manager verfügbar ist, ist derselbe Tabellenvorgang, mit dem Sie die Spalten einer Tabelle mithilfe der PostgreSQL-Logik umwandeln können. Die Dokumentation zu den Funktionen und Operatoren, die im Spaltentyp `Calculation` verwendet werden können, finden Sie auf der PostgreSQL-Website [hier](https://www.postgresql.org/docs/9.6/functions.html).

Die verschiedenen Spalten, die mit der Spalte `Calculation` erstellt werden können, sind fast unbegrenzt. Die meisten Spalten können jedoch mit IF-THEN-Anweisungen und Basisarithmetik erstellt werden, die in den Beispielen unten verwendet wird.

**Beispiel 1: Ist die letzte Bestellung des Kunden?**

Die meisten Konten verfügen über eine Spalte mit dem Namen `Is customer's last order?` in ihrer `orders` -Tabelle, um Analysen zu Wiederholungskäufen und Kunden durchzuführen. Wenn Ihr Konto auf der neuen Architektur basiert, wird diese Spalte mithilfe einer `Calculation` -Spalte erstellt und ist im folgenden Screenshot zu sehen:

![](../../assets/Is_customer_s_last_order.png)

Die Spalte `Is customer's last order?` verwendet die Eingaben `Customer's lifetime number of orders` und `Customer's order number` als `A` bzw. als `B` Alias.

Die Bedeutung von PostgreSQL lautet Zeile für Zeile:

* case: Startet eine Reihe von If - Then -Anweisungen
* Wenn `A` null oder `B` null ist, dann null: Wenn eine der Eingaben leer ist, sollte die Ausgabe ebenfalls leer sein. Dies verhindert SQL-Fehler
* wenn `A=B` dann `Yes`: Wenn `Customer's lifetime number of orders` gleich `Customer's order number` für diese Zeile ist, geben Sie `Yes` zurück. Wenn ein Kunde also vier Bestellungen aufgegeben hat, würde die Zeile für die vierte Bestellung `Yes` für `Is customer's last order?` zurückgeben
* else `No`: Wenn keiner der anderen Anweisungen erfüllt ist, geben Sie `No` zurück.
* end: Hierdurch wird die If - Then -Anweisung beendet.

Die möglichen Werte, die von dieser Spalte zurückgegeben werden können (`NULL`, `Yes`, `No`), enthalten Zeichen, die nicht aus der Zahl stammen, daher ist der Datentyp hier &quot;String&quot;.

**Beispiel 2: Gesamtwert des Bestellartikels (Menge * Preis)**

Viele Kunden analysieren gerne den Umsatz auf Artikelebene und teilen ihn nach Feldern wie `product name` oder `category`. Die meisten Datenbanken geben Ihnen nicht den Umsatz aus einem Produkt in einer Bestellung, sondern die Menge, die in der Bestellung verkauft wird, und den Preis des Artikels.

Um Produktumsatzanalysen zu aktivieren, verfügen die meisten Konten in ihrer `Orders Items` -Tabelle über eine Spalte mit dem Namen `Order item total value (quantity * price)` . Wenn Ihr Konto auf der neuen Architektur basiert, wird diese Spalte auch mit einer `Calculation` -Spalte erstellt und ist im folgenden Screenshot zu sehen:

![](../../assets/Order_item_total_value.png)

Im Commerce-Schema verwendet die Spalte `Order item total value (quantity * price)` die Eingaben `qty ordered` und `base price`, die als `A` bzw. `B` Alias erhalten.

Die Werte, die von dieser neuen Spalte zurückgegeben werden, sind in Dollar und Cent angegeben, daher ist der richtige Datentyp `Decimal(10,2)`.

**Mechanics**

Eine neue `Calculation` -Spalte kann einer Tabelle hinzugefügt werden, indem Sie zu **[!DNL Manage Data > Data Warehouse]** navigieren, wie unten dargestellt:

![](../../assets/blobid2.png)

Von hier aus können Sie eine `Calculation` -Spalte erstellen, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie die Tabelle aus, der Sie die Spalte `Calculation` hinzufügen möchten.
1. Klicken Sie auf der richtigen Tabelle oben rechts im Bildschirm auf **[!UICONTROL Create New Column]** .
1. Wählen Sie im Dropdownmenü `Select a definition` die Option `Same Table` aus.
1. Wählen Sie `Calculation` als `column definition equation` aus.
1. Geben Sie den Spaltennamen ein.
1. Wählen Sie die `input` -Spalten aus der Tabelle aus, die in der Logik Ihrer neuen Spalte verwendet werden. Jede Spalte, die Sie hinzufügen, erhält einen Briefalias, sodass die erste Spalte `A`, die zweite `B` usw. ist.
1. Geben Sie im Fenster die PostgreSQL-Logik für Ihre neue Spalte mit den Briefaliasen Ihrer Eingaben ein. Die SQL-Berechnung sollte auf eine einzige Spaltendefinition beschränkt sein, einschließlich der gesamten Logik zwischen den SELECT- und FROM-Anweisungen einer SQL-Abfrage. SQL-Schlüsselwörter, die einen der eingegebenen Buchstaben verwenden, sollten in Kleinbuchstaben eingegeben werden. Wenn Sie beispielsweise die Anweisung `CASE` verwenden, sollte sie in Kleinbuchstaben geschrieben werden - `case`. Das System geht davon aus, dass ein großgeschriebener `A` auf einen der Eingaben verweist.
1. Wählen Sie den entsprechenden Datentyp aus.
   * `Integer` - Ganzzahl
   * `Decimal(10,2)` - eine Dezimalzahl mit 10 Ziffern insgesamt, von denen 2 rechts neben dem Dezimalpunkt liegen
   * `String` - Beliebiger Text- oder Zeichensatztyp, der keine Zahlen verwendet
   * Format `Datetime` - `yyyy-MM-dd hh:mm:ss`

1. Klicken Sie auf **[!UICONTROL test column]**. Dadurch wird eine Liste mit fünf Testwerten für jede Ihrer Eingaben generiert und das Ergebnis der Logik aus Schritt 6 für jeden Satz von Testwerten angezeigt. Wenn ein Teil der SQL einen Fehler erzeugt, wird die entsprechende Fehlermeldung zurückgegeben. Beispielergebnisse können nur generiert werden, wenn alle Eingabespalten native Felder sind. Wenn eine der Eingabespalten berechnete Spalten ist, müssen Sie die Ergebnisse validieren, indem Sie die Spalte zu einer Metrik hinzufügen und im Visual Report Builder anzeigen

1. Wenn Sie mit den Ergebnissen zufrieden sind, klicken Sie auf **[!UICONTROL Save]**. Die Spalte ermöglicht die Verwendung.
