---
title: Sequenzieller Vergleich - berechnete Spalte
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte Sequenzieller Vergleich .
exl-id: 625062b4-f05d-42aa-94c3-729b39c7d728
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# Sequenzieller Vergleich - berechnete Spalte

In diesem Thema werden Zweck und Verwendung der `Sequential Comparison` in der Spalte **[!DNL Manage Data > Data Warehouse]** Seite. Nachstehend finden Sie eine Erläuterung der Funktionsweise, gefolgt von einem Beispiel und der Methode zur Erstellung.

**Erklärung**

Die `Sequential Comparison` Spaltentyp: ermittelt den Unterschied zwischen aufeinander folgenden Ereignissen. Der am häufigsten verwendete Typ `Sequential Comparison` Spalte ist `Seconds since previous order` Spalte. Für diese Spalte sind drei Eingaben erforderlich:

1. `Event Owner`: Diese Eingabe bestimmt die Entität, für die Zeilen gruppiert werden. Beispiel: in der `Seconds since previous order` -Spalte ist der Ereigniseigentümer der Kunde, da Sie die Anzahl der Sekunden seit der vorherigen Bestellung desselben Kunden ermitteln möchten.
1. `Event Date`: Diese Eingabe erzwingt die Reihenfolge der Ereignisse. In den Fällen von `Seconds since previous order`, sollte die Spalte, die den Zeitstempel der Bestellung enthält, die `Event Date`. Diese Eingabe ist immer ein Zeitstempel.
1. `Value to Compare`: Diese Eingabe ist der tatsächliche zu vergleichende Wert. Dadurch wird der Wert der vorherigen Zeile vom Wert der aktuellen Zeile abgezogen. Daher wird eine Spalte aufgerufen, die die zeitliche Differenz zwischen aufeinander folgenden Bestellungen eines Kunden ermittelt `Seconds since previous order`. Diese Eingabe muss kein Zeitstempel sein. Ein Beispiel ohne Zeitstempel besteht darin, den Unterschied zwischen aufeinander folgenden Bestellungen eines Kunden im Bestellwert zu ermitteln.

**Beispiel**

| **`event_id`** | **`owner_id`** | **`timestamp`** | **`Seconds since owner's previous event`** |
|--- |--- |--- |--- |
| **`1`** | A | 2015-01-01 00:00:00 | NULL |
| **`2`** | B | 2015-01-01 00:30:00 | NULL |
| **`3`** | A | 2015-01-01 02:00:00 | 7200 |
| **`4`** | A | 2015-01-02 13:00:00 | 126000 |
| **`5`** | B | 2015-01-03 13:00:00 | 217800 |

Im obigen Beispiel `Seconds since owner's previous event` ist die `Sequential Comparison` berechnete Spalte. Für `owner_id = A`, wird zunächst eine Sequenz anhand der `timestamp` und subtrahiert dann die `timestamp` aus dem Zeitstempel des aktuellen Ereignisses. In der dritten Zeile der Tabelle - die zweite Zeile für `owner_id A` - der Wert von `Seconds since owner's previous event` die Anzahl der Sekunden zwischen &quot;2015-01-01 02:00&quot;und &quot;2015-01-01 00&quot;:00:00&#39;. Dieser Unterschied entspricht zwei Stunden = 7200 Sekunden.

Für diesen berechneten Spaltentyp weist die Zeile, die dem ersten Ereignis des Eigentümers entspricht, eine `NULL` -Wert.

**Mechanik**

So erstellen Sie eine **Ereignisnummer** column:

1. Navigieren Sie zum **[!DNL Manage Data > Data Warehouse]** Seite.

1. Navigieren Sie zu der Tabelle, für die Sie diese Spalte erstellen möchten.

1. Klicken **[!UICONTROL Create New Column]** in der oberen rechten Ecke.

1. Auswählen `Same Table` als `Definition Type` (Wenn sich die zu vergleichenden Spalten nicht in derselben Tabelle befinden, müssen Sie sie möglicherweise umstellen.)

1. Auswählen `SEQUENTIAL_COMPARISON` als `Column Definition Equation`.

1. Wählen Sie die Eingaben wie oben beschrieben aus:
   - `Event Owner`
   - `Event Date`
   - `Value to Compare`

1. Es können auch Filter hinzugefügt werden, um Zeilen von der Berücksichtigung auszuschließen. Die ausgeschlossenen Zeilen haben eine `NULL` -Wert für diese Spalte.

1. Geben Sie oben auf der Seite einen Namen für die Spalte ein und klicken Sie auf **[!UICONTROL Save]**.

1. Die Spalte kann verwendet werden *sofort*.

![SEK](../../assets/SEC_new.png)
