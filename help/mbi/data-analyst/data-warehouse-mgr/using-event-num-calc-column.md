---
title: Spalte "Ereignisnummer berechnet"
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte Ereignisnummer berechnet .
exl-id: c234621e-2e68-4e63-8b0d-7034d1b5fe1f
source-git-commit: 2db58f4b612fda9bdb2570e582fcde89ddc18154
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 3%

---

# Spalte &quot;Ereignisnummer berechnet&quot;

In diesem Thema werden Zweck und Verwendung der `Event Number` in der Spalte **[!DNL Manage Data > Data Warehouse]** Seite. Nachstehend finden Sie eine Erläuterung dessen, was es tut, gefolgt von einem Beispiel und der Methode, sie zu erstellen.

**Erklärung**

Die `Event Number` Spaltentyp gibt die Sequenz an, in der Ereignisse für eine bestimmte **Ereignisinhaber**, wie z. B. `customer` oder `user`. Wenn Sie mit SQL vertraut sind, ist dieser Spaltentyp mit dem Szenario `RANK` -Funktion. Sie kann verwendet werden, um Unterschiede im Verhalten zwischen Erstereignissen, Wiederholungsereignissen oder n-ten Ereignissen in Ihren Daten zu beobachten.

Im Falle einer Krawatte enthält diese Spalte die gleiche **rank** für die verknüpften Ereignisse und überspringt die nachfolgenden Zahlen. Wenn sie beispielsweise die Zahlen 5,8,10,10,12 einstuft, wären die Ränge 1,2,3,3,5.

Der häufigste Anwendungsfall dieser Spalte ist die Analyse von Erstkäufern und Wiederholungskäufern. Erstmalige Käufer werden durch Hinzufügen eines Filters (zu einer Metrik oder einem Bericht) zu `Customer's order number` = 1. `Customer's order number` ist eine Spalte des Typs `Event Number`.

**Beispiel**

| **`event_id`** | **`owner_id`** | **`timestamp`** | **`Owner's event number`** |
|--- |--- |--- |--- |
| **1 | A | 2015-01-01 00:00:00 | 1 |
| **2 | B | 2015-01-01 00:30:00 | 1 |
| **3 | A | 2015-01-01 02:00:00 | 2 |
| **4 | A | 2015-01-02 13:00:00 | 3 |
| **5 | B | 2015-01-03 13:00:00 | 2 |

Im obigen Beispiel wird die Spalte `Owner's event number` ist `Event Number` Spalte. Er ordnet die Ereignisse des Eigentümers in der Reihenfolge an, in der sie aufgetreten sind (basierend auf der `timestamp` Spalte).

Betrachten Sie beispielsweise alle Zeilen, bei denen `owner_id = A`. Die erste Zeile in der Tabelle ist der früheste Zeitstempel für diesen Inhaber, gefolgt von der dritten Zeile in der Tabelle, gefolgt von der vierten Zeile in der Tabelle.

**Mechanik**

Im Folgenden finden Sie einige Anweisungen zum Erstellen eines `Event Number` column:

1. Navigieren Sie zum **[!UICONTROL Manage Data > Data Warehouse]** Seite.

1. Navigieren Sie zu der Tabelle, für die Sie diese Spalte erstellen möchten.

1. Klicken **[!UICONTROL Create a Column]** und wählen Sie die `EVENT_NUMBER (…)` Spaltentyp: unter `Same Table` Abschnitt.

1. Das erste Dropdown-Menü `Event Owner` gibt die Entität an, für die der Rang bestimmt werden soll. In dem Fall, in dem `Customer's order number`, eine Kunden-ID wie `customer_id` oder `customer_email` wäre `Event Owner`.

1. Das zweite Dropdown-Menü `Event Rank` gibt die Spalte an, die die Sequenz erzwingt, die den Rang der Zeile bestimmt. In dem Fall, in dem `Customer's order number`, die `created_at` timestamp `Event Rank`.

1. Unter dem `Options` Dropdown-Liste können Sie Filter hinzufügen, um Zeilen von der Berücksichtigung auszuschließen. Die ausgeschlossenen Zeilen haben eine `NULL` -Wert für diese Spalte.

1. Geben Sie der Spalte einen Namen und klicken Sie auf **[!UICONTROL Save]**.

1. Die Spalte kann verwendet werden _sofort._
