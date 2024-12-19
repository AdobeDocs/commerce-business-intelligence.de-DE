---
title: Berechnete Spalte der Ereignisnummer
description: Erfahren Sie mehr über den Zweck und die Verwendung der berechneten Spalte „Ereignisnummer“.
exl-id: c234621e-2e68-4e63-8b0d-7034d1b5fe1f
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# Berechnete Spalte der Ereignisnummer

In diesem Thema werden der Zweck und die Verwendung der `Event Number` berechneten Spalte auf der **[!DNL Manage Data > Data Warehouse]** Seite beschrieben. Nachfolgend finden Sie eine Erläuterung der Funktionen, gefolgt von einem Beispiel und den Methoden zu seiner Erstellung.

**Erläuterung**

Der `Event Number` Spaltentyp identifiziert die Sequenz, in der Ereignisse für einen bestimmten **Ereignisbesitzer“ aufgetreten sind** z. B. eine `customer` oder `user`. Wenn Sie mit SQL vertraut sind, ist dieser Spaltentyp identisch mit der `RANK`. Sie kann verwendet werden, um Verhaltensunterschiede zwischen erstmaligen Ereignissen, Wiederholungsereignissen oder n-ten Ereignissen in Ihren Daten zu beobachten.

Im Fall einer Gleichheit enthält diese Spalte denselben **Rang** für die gleichgestellten Ereignisse und überspringt die nachfolgenden Zahlen. Wenn er beispielsweise die Zahlen 5,8,10,10,12 nach Rang ordnen würde, wären die Ränge 1,2,3,3,5.

Der häufigste Anwendungsfall dieser Spalte ist die Analyse von Erstkäufern und Wiederholungskäufern. Erstkäufer werden durch Hinzufügen eines Filters (zu einer Metrik oder einem Bericht) auf `Customer's order number` = 1 identifiziert. `Customer's order number` ist eine Spalte vom Typ `Event Number`.

**Beispiel**

| **`event_id`** | **`owner_id`** | **`timestamp`** | **`Owner's event number`** |
|--- |--- |--- |--- |
| **1 | A | 01.01.2015 00:00:00 | 1 |
| **2 | B | 01.01.2015 00:30:00 | 1 |
| **3 | A | 01.01.2015 02:00:00 | 2 |
| **4 | A | 2015-01-02 13:00:00 | 3 |
| **5 | B | 03.01.2015 13:00:00 | 2 |

Im obigen Beispiel ist die Spalte `Owner's event number` eine `Event Number` Spalte. Die Ereignisse des Eigentümers werden in der Reihenfolge ihres Auftretens sortiert (basierend auf der Spalte `timestamp` ).

Betrachten Sie beispielsweise alle Zeilen mit `owner_id = A`. Die erste Zeile in der Tabelle ist der früheste Zeitstempel für diesen Eigentümer, gefolgt von der dritten Zeile in der Tabelle, gefolgt von der vierten Zeile in der Tabelle.

**Mechanik**

Im Folgenden finden Sie einige Anweisungen zum Erstellen einer `Event Number` Spalte:

1. Navigieren Sie zur **[!UICONTROL Manage Data > Data Warehouse]**.

1. Navigieren Sie zu der Tabelle, in der Sie diese Spalte erstellen möchten.

1. Klicken Sie auf **[!UICONTROL Create a Column]** und wählen Sie den `EVENT_NUMBER (…)` Spaltentyp aus: unter dem Abschnitt `Same Table` .

1. Die erste Dropdown-`Event Owner` gibt die Entität an, für die der Rang bestimmt werden soll. In dem Fall, in dem ein `Customer's order number`, wäre eine Kundenkennung wie `customer_id` oder `customer_email` der `Event Owner`.

1. Die zweite Dropdown-`Event Rank` gibt die Spalte an, die die Sequenz durchsetzt, die den Rang der Zeile bestimmt. In einem `Customer's order number` wäre der `created_at` Zeitstempel der `Event Rank`.

1. In der Dropdown-Liste `Options` können Sie Filter hinzufügen, um Zeilen von der Berücksichtigung auszuschließen. Die ausgeschlossenen Zeilen haben einen `NULL` Wert für diese Spalte.

1. Geben Sie der Spalte einen Namen und klicken Sie auf **[!UICONTROL Save]**.

1. Die Spalte kann verwendet werden _sofort._
