---
title: Sequenzieller Vergleich - berechnete Spalte
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte Sequenzieller Vergleich .
exl-id: 625062b4-f05d-42aa-94c3-729b39c7d728
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: 2433a614e9858684842804a0ae29fb67f0d41ead
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Sequenzieller Vergleich - berechnete Spalte

In diesem Thema werden der Zweck und die Verwendung der auf der Seite **[!DNL Manage Data > Data Warehouse]** verfügbaren Spalte mit der berechneten `Sequential Comparison` -Zahl erläutert. Nachstehend finden Sie eine Erläuterung der Funktionsweise, gefolgt von einem Beispiel und der Methode zur Erstellung.

**Erklärung**

Der Spaltentyp `Sequential Comparison`: findet den Unterschied zwischen aufeinander folgenden Ereignissen. Der häufigste Typ der Spalte `Sequential Comparison` ist die Spalte `Seconds since previous order` . Für diese Spalte sind drei Eingaben erforderlich:

1. `Event Owner`: Diese Eingabe bestimmt die Entität, für die Zeilen gruppiert werden. In der Spalte `Seconds since previous order` ist der Ereigniseigentümer beispielsweise der Kunde, da Sie die Anzahl der Sekunden seit der vorherigen Bestellung desselben Kunden ermitteln möchten.
1. `Event Date`: Diese Eingabe erzwingt die Sequenz von Ereignissen. Bei `Seconds since previous order` sollte die Spalte, die den Zeitstempel der Reihenfolge enthält, die `Event Date` sein. Diese Eingabe ist immer ein Zeitstempel.
1. `Value to Compare`: Diese Eingabe ist der tatsächliche zu vergleichende Wert. Dadurch wird der Wert der vorherigen Zeile vom Wert der aktuellen Zeile abgezogen. Daher wird eine Spalte, die die zeitliche Differenz zwischen aufeinander folgenden Bestellungen eines Kunden ermittelt, als `Seconds since previous order` bezeichnet. Diese Eingabe muss kein Zeitstempel sein. Ein Beispiel ohne Zeitstempel besteht darin, den Unterschied zwischen aufeinander folgenden Bestellungen eines Kunden im Bestellwert zu ermitteln.

**Beispiel**

| **`event_id`** | **`owner_id`** | **`timestamp`** | **`Seconds since owner's previous event`** |
|--- |--- |--- |--- |
| **`1`** | A | 01.01.2015 00:00:00 | NULL |
| **`2`** | B | 01.01.2015 00:30:00 | NULL |
| **`3`** | A | 01.01.2015:00:00 | 7200 |
| **`4`** | A | 2015-01-02 13:00:00 | 126000 |
| **`5`** | B | 03.01.2015 13:00:00 | 217800 |

Im obigen Beispiel ist `Seconds since owner's previous event` die berechnete Spalte `Sequential Comparison`. Für den `owner_id = A` wird zunächst eine Sequenz anhand der Spalte `timestamp` identifiziert und dann der Wert `timestamp` des vorherigen Ereignisses vom Zeitstempel des aktuellen Ereignisses abgezogen. In der dritten Zeile in der Tabelle - der zweiten Zeile für `owner_id A` - ist der Wert `Seconds since owner's previous event` die Anzahl der Sekunden zwischen &quot;2015-01-01 02:00&quot;und &quot;2015-01-00:00:00&quot;. Dieser Unterschied entspricht zwei Stunden = 7200 Sekunden.

Für diesen berechneten Spaltentyp hat die Zeile, die dem ersten Ereignis des Eigentümers entspricht, den Wert `NULL`.

**Mechanics**

So erstellen Sie die Spalte **Ereignisnummer** :

1. Navigieren Sie zur Seite &quot;**[!DNL Manage Data > Data Warehouse]**&quot;.

1. Navigieren Sie zu der Tabelle, für die Sie diese Spalte erstellen möchten.

1. Klicken Sie oben rechts auf **[!UICONTROL Create New Column]** .

1. Wählen Sie `Same Table` als `Definition Type` aus (wenn sich die zu vergleichenden Spalten nicht in derselben Tabelle befinden, müssen Sie sie möglicherweise umstellen).

1. Wählen Sie `SEQUENTIAL_COMPARISON` als `Column Definition Equation` aus.

1. Wählen Sie die Eingaben wie oben beschrieben aus:
   - `Event Owner`
   - `Event Date`
   - `Value to Compare`

1. Es können auch Filter hinzugefügt werden, um Zeilen von der Berücksichtigung auszuschließen. Die ausgeschlossenen Zeilen haben einen `NULL` -Wert für diese Spalte.

1. Geben Sie oben auf der Seite einen Namen für die Spalte ein und klicken Sie auf **[!UICONTROL Save]**.

1. Die Spalte ist verfügbar, um *unmittelbar* zu verwenden.

![SEC](../../assets/SEC_new.png)
