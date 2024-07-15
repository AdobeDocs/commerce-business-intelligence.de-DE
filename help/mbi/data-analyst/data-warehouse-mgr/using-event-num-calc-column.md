---
title: Spalte mit Ereignisnummer
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte Ereignisnummer berechnet .
exl-id: c234621e-2e68-4e63-8b0d-7034d1b5fe1f
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# Spalte mit Ereignisnummer

In diesem Thema werden der Zweck und die Verwendung der auf der Seite **[!DNL Manage Data > Data Warehouse]** verfügbaren Spalte mit der berechneten `Event Number` -Zahl erläutert. Nachstehend finden Sie eine Erläuterung dessen, was es tut, gefolgt von einem Beispiel und der Methode, sie zu erstellen.

**Erklärung**

Der Spaltentyp `Event Number` gibt die Sequenz an, in der Ereignisse für einen bestimmten **Ereigniseigentümer** aufgetreten sind, z. B. `customer` oder `user`. Wenn Sie mit SQL vertraut sind, ist dieser Spaltentyp mit der Funktion `RANK` identisch. Sie kann verwendet werden, um Unterschiede im Verhalten zwischen Erstereignissen, Wiederholungsereignissen oder n-ten Ereignissen in Ihren Daten zu beobachten.

Im Falle einer Verknüpfung enthält diese Spalte denselben **Rang** für die verbundenen Ereignisse und überspringt die nachfolgenden Zahlen. Wenn sie beispielsweise die Zahlen 5,8,10,10,12 einstuft, wären die Ränge 1,2,3,3,5.

Der häufigste Anwendungsfall dieser Spalte ist die Analyse von Erstkäufern und Wiederholungskäufern. Erstmalige Käufer werden durch Hinzufügen eines Filters (zu einer Metrik oder einem Bericht) für `Customer's order number` = 1 identifiziert. `Customer's order number` ist eine Spalte vom Typ `Event Number`.

**Beispiel**

| **`event_id`** | **`owner_id`** | **`timestamp`** | **`Owner's event number`** |
|--- |--- |--- |--- |
| **1 | A | 01.01.2015 00:00:00 | 1 |
| **2 | B | 01.01.2015 00:30:00 | 1 |
| **3 | A | 01.01.2015:00:00 | 2 |
| **4 | A | 2015-01-02 13:00:00 | 3 |
| **5 | B | 03.01.2015 13:00:00 | 2 |

Im obigen Beispiel ist die Spalte `Owner's event number` eine Spalte `Event Number` . Er ordnet die Ereignisse des Eigentümers in der Reihenfolge an, in der sie aufgetreten sind (basierend auf der Spalte `timestamp` ).

Betrachten Sie beispielsweise alle Zeilen mit `owner_id = A`. Die erste Zeile in der Tabelle ist der früheste Zeitstempel für diesen Inhaber, gefolgt von der dritten Zeile in der Tabelle, gefolgt von der vierten Zeile in der Tabelle.

**Mechanics**

Im Folgenden finden Sie einige Anweisungen zum Erstellen einer `Event Number` -Spalte:

1. Navigieren Sie zur Seite &quot;**[!UICONTROL Manage Data > Data Warehouse]**&quot;.

1. Navigieren Sie zu der Tabelle, für die Sie diese Spalte erstellen möchten.

1. Klicken Sie auf **[!UICONTROL Create a Column]** und wählen Sie den Spaltentyp `EVENT_NUMBER (…)` aus: unter dem Abschnitt `Same Table` .

1. Das erste Dropdown-Menü &quot;`Event Owner`&quot; gibt die Entität an, für die der Rang bestimmt werden soll. In dem Fall, in dem eine `Customer's order number`, wäre eine Kunden-ID wie `customer_id` oder `customer_email` die `Event Owner`.

1. Das zweite Dropdown-Feld &quot;`Event Rank`&quot; gibt die Spalte an, die die Sequenz erzwingt, die den Rang der Zeile bestimmt. In dem Fall, in dem ein `Customer's order number` ist, wäre der `created_at`-Zeitstempel der `Event Rank`.

1. Im Dropdown-Menü `Options` können Sie Filter hinzufügen, um Zeilen von der Berücksichtigung auszuschließen. Die ausgeschlossenen Zeilen haben einen `NULL` -Wert für diese Spalte.

1. Geben Sie einen Namen für die Spalte ein und klicken Sie auf **[!UICONTROL Save]**.

1. Die Spalte ist verfügbar, um _sofort zu verwenden._
