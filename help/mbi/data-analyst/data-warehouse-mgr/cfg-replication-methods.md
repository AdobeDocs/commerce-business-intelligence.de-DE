---
title: Konfigurieren von Replikationsmethoden
description: Erfahren Sie, wie Tabellen organisiert sind und wie sich die Tabellendaten verhalten, damit Sie die beste Replikationsmethode für Ihre Tabellen auswählen können.
exl-id: 83895c48-a6ec-4b01-9890-164e0b21dcbc
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '1442'
ht-degree: 0%

---

# Konfigurieren von Replikationsmethoden

`Replication` Methoden und [erneute Prüfungen](../data-warehouse-mgr/cfg-data-rechecks.md) werden verwendet, um neue oder aktualisierte Daten in Ihren Datenbanktabellen zu identifizieren. Sie richtig einzustellen, ist entscheidend, um sowohl die Datengenauigkeit als auch optimierte Aktualisierungszeiten sicherzustellen. In diesem Abschnitt werden Replikationsmethoden behandelt.

Wenn neue Tabellen im [Data Warehouse Manager](../data-warehouse-mgr/tour-dwm.md) synchronisiert werden, wird automatisch eine Replikationsmethode für die Tabelle ausgewählt. Wenn Sie die verschiedenen Replikationsmethoden verstehen, wissen, wie Tabellen organisiert sind und wie sich die Tabellendaten verhalten, können Sie die beste Replikationsmethode für Ihre Tabellen auswählen.

## Welche Replikationsmethoden gibt es?

`Replication` Methoden lassen sich in drei Gruppen einteilen - `Incremental`, `Full Table` und `Paused`.

[**[!UICONTROL Incremental Replication]**](#incremental) bedeutet, dass [!DNL Commerce Intelligence] bei jedem Replikationsversuch nur neue oder aktualisierte Daten repliziert. Da diese Methoden die Latenz erheblich reduzieren, empfiehlt Adobe, sie nach Möglichkeit zu verwenden.

[**[!UICONTROL Full Table Replication]**](#fulltable) bedeutet, dass [!DNL Commerce Intelligence] bei jedem Replikationsversuch den gesamten Inhalt einer Tabelle repliziert. Aufgrund der potenziell großen Datenmenge, die repliziert werden soll, können diese Methoden die Latenz erhöhen und die Aktualisierungszeiten verkürzen. Wenn eine Tabelle Spalten mit Zeitstempel oder Datum/Uhrzeit enthält, empfiehlt Adobe stattdessen die Verwendung einer inkrementellen Methode.

**[!UICONTROL Paused]** gibt an, dass die Replikation für die Tabelle angehalten oder angehalten wurde. [!DNL Commerce Intelligence] sucht während eines Aktualisierungszyklus nicht nach neuen oder aktualisierten Daten. Dies bedeutet, dass keine Daten aus einer Tabelle repliziert werden, die diese als Replikationsmethode verwendet.

## Inkrementelle Replikationsmethoden {#incremental}

### Geändert (höchstens ideal)

Die `Modified At` Replikationsmethode verwendet eine Datums-/Uhrzeitspalte, die beim Erstellen einer Zeile gefüllt und bei Datenänderungen aktualisiert wird, um zu replizierende Daten zu finden. Diese Methode ist für die Verwendung mit Tabellen konzipiert, die die folgenden Kriterien erfüllen:

* enthält eine `datetime`, die beim Erstellen einer Zeile anfänglich aufgefüllt und bei jeder Änderung der Zeile aktualisiert wird;
* Die Spalte `datetime` ist nie null.
* Zeilen werden nicht aus der Tabelle gelöscht

Zusätzlich zu diesen Kriterien empfiehlt Adobe **Indizierung** die `datetime`, die für die `Modified At` Replikation verwendet wird, da dies die Replikationsgeschwindigkeit optimiert.

Wenn die Aktualisierung ausgeführt wird, werden neue oder geänderte Daten identifiziert, indem nach Zeilen gesucht wird, die einen Wert in der Spalte `datetime` enthalten, die nach der letzten Aktualisierung aufgetreten ist. Wenn neue Zeilen erkannt werden, werden sie in Ihre Data Warehouse repliziert. Wenn Zeilen im [Data Warehouse Manager](../data-warehouse-mgr/tour-dwm.md) vorhanden sind, werden sie mit den aktuellen Datenbankwerten überschrieben.

Beispielsweise kann eine Tabelle eine Spalte mit dem Namen `modified\_at` enthalten, die angibt, wann die Daten zuletzt geändert wurden. Wenn die letzte Aktualisierung Dienstag Mittag ausgeführt wurde, sucht die Aktualisierung nach allen Zeilen mit einem `modified\_at` Wert größer als Dienstag Mittag. Alle gefundenen Zeilen, die seit Dienstagmittag erstellt oder geändert wurden, werden in die Data Warehouse repliziert.

**Wussten Sie schon?**
Selbst wenn Ihre Datenbank derzeit keine `Incremental` Replikationsmethode unterstützen kann, können Sie möglicherweise [Änderungen an Ihrer Datenbank vornehmen](../../best-practices/mod-db-inc-replication.md) wodurch die Verwendung von `Modified At` oder `Single Auto Incrementing PK` ermöglicht würde.

`Modified At` ist nicht nur die ideale Replikationsmethode, sondern auch die schnellste. Diese Methode erzeugt nicht nur merkliche Geschwindigkeitssteigerungen bei großen Datensätzen, sondern erfordert auch keine Konfiguration einer Option für eine erneute Überprüfung. Andere Methoden müssen durch eine gesamte Tabelle navigieren, um Änderungen zu identifizieren, auch wenn sich eine kleine Teilmenge der Daten geändert hat. `Modified At` durchläuft nur diese kleine Teilmenge.

### Primärer Schlüssel mit automatischer Erhöhung

`Auto Incrementing` ist ein Verhalten, das Zeilen sequenziell Primärschlüssel zuweist. Wenn eine Tabelle `Auto Incrementing` ist und der höchste Primärschlüssel in der Tabelle 1.000 ist, dann ist der nächste Primärwert 1.001 oder höher. Eine Tabelle, die kein `Auto Incrementing` Verhalten verwendet, kann einen Primärschlüsselwert von weniger als 1.000 zuweisen oder zu einer viel größeren Zahl springen, dies wird jedoch nicht häufig verwendet.

Diese Methode dient zur Replikation neuer Daten aus Tabellen, die die folgenden Kriterien erfüllen:

* `single-column primary key` und
* `primary key` Datentyp ist `integer`; und
* `auto incrementing` Primärschlüsselwerte.

Wenn eine Tabelle `Single Auto Incrementing Primary Key` Replikation verwendet, werden neue Daten erkannt, indem nach Primärschlüsselwerten gesucht wird, die höher sind als der aktuell höchste Wert in Ihrer Data Warehouse. Wenn beispielsweise der höchste Primärschlüsselwert in Ihrer Data Warehouse 500 beträgt, sucht sie bei der nächsten Aktualisierung nach Zeilen mit Primärschlüsselwerten von 501 oder höher.

### Datum hinzufügen

Die `Add Date` Methode funktioniert ähnlich wie die `Single Auto Incrementing Primary Key`. Anstatt eine Ganzzahl für den Primärschlüssel der Tabelle zu verwenden, verwendet diese Methode eine `timestamped` Spalte, um auf neue Zeilen zu prüfen.

Wenn eine Tabelle `Add Date` Replikation verwendet, werden neue Daten erkannt, indem nach Werten mit Zeitstempel gesucht wird, die nach dem letzten mit Ihrer Data Warehouse synchronisierten Datum liegen. Wenn beispielsweise eine Aktualisierung zuletzt am 20/12/2015 09.:00: ausgeführt wurde, werden alle Zeilen mit einem Zeitstempel, der größer ist als dieser, als neue Daten markiert und repliziert.

>[!NOTE]
>
>Im Gegensatz zur `Modified At`-Methode prüft `Add Date` vorhandene Zeilen nicht auf aktualisierte Informationen - es freut sich nur auf neue Zeilen.

## Replikationsmethoden für vollständige Tabellen {#fulltable}

### Volle Tabelle

`Full table` Replikation aktualisiert die gesamte Tabelle, sobald neue Zeilen erkannt werden. Dies ist bei weitem die am wenigsten effiziente Replikationsmethode, da alle Daten bei jeder Aktualisierung neu verarbeitet werden müssen, vorausgesetzt, es gibt neue Zeilen.

Neue Zeilen werden erkannt, indem Sie Ihre Datenbank zu Beginn des Synchronisierungsprozesses abfragen und die Anzahl der Zeilen zählen. Wenn die lokale Datenbank mehr Zeilen als [!DNL Commerce Intelligence] enthält, wird die Tabelle aktualisiert. Wenn die Zeilenanzahl identisch ist oder [!DNL Commerce Intelligence] (*)* Zeilen enthält als Ihre lokale Datenbank, wird die Tabelle übersprungen.

Dies wirft den wichtigen Punkt auf, dass **`Full Table`Replikation in folgenden Fällen inkompatibel ist:**

* zwischen nachfolgenden Aktualisierungszyklen mehr Zeilen gelöscht als in der lokalen Datenbanktabelle erstellt werden oder
* Spaltenwerte werden geändert, es werden jedoch keine zusätzlichen Zeilen erstellt

In beiden oben genannten Szenarien erkennt `Full Table` Replikation keine Änderungen und Ihre Daten werden veraltet. Aufgrund der Ineffizienz dieser Replikationsmethode und der oben genannten Anforderungen wird `Full Table` Replikation nur als letztes Mittel empfohlen.

### Primärer Schlüsselstapel

Wenn eine Tabelle `Primary Key Batch` (PK-Batch) verwendet, werden neue Daten erkannt, indem Zeilen innerhalb von Bereichen oder Batches mit Primärschlüsselwerten gezählt werden. Während man davon ausgeht, dass dies normalerweise mit Ganzzahlen verwendet wird, können sogar Textwerte auf eine Weise sortiert werden, die es dem System ermöglicht, konstante Bereiche zu definieren.

Angenommen, eine Aktualisierung wird ausgeführt und führt eine Zeilenanzahl für den Schlüsselbereich von 1 bis 100 durch. In diesem Update findet und protokolliert das System 37 Zeilen. Bei der nächsten Aktualisierung wird erneut eine Zeilenanzahl im Bereich von 1 bis 100 durchgeführt, wobei 41 Zeilen gefunden werden. Da sich die Anzahl der Zeilen im Vergleich zur letzten Aktualisierung unterscheidet, prüft das System diesen Bereich (oder Batch) genauer.

Diese Methode dient zur Replikation von Daten aus Tabellen, die die folgenden Kriterien erfüllen:

* einspaltige Nicht-Ganzzahl oder
* Zusammengesetzte Schlüssel (mehrere Spalten, die den Primärschlüssel umfassen) - Beachten Sie, dass Spalten, die in einem zusammengesetzten Primärschlüssel verwendet werden, nie Nullwerte haben können; oder
* Einzelspaltige, ganzzahlige, nicht automatisch inkrementierende Primärschlüsselwerte.

Diese Methode ist nicht ideal, da sie aufgrund des Verarbeitungsaufwands für die Untersuchung von Stapeln und das Auffinden von Änderungen unglaublich langsam ist. Adobe empfiehlt, diese Methode nur zu verwenden, wenn die erforderlichen Änderungen zur Unterstützung der anderen Replikationsmethoden vorgenommen werden können. Es wird erwartet, dass die Aktualisierungszeiten zunehmen, wenn diese Methode verwendet werden muss.

## Festlegen von Replikationsmethoden

Die Replikationsmethoden werden für jede Tabelle einzeln festgelegt. Zum Festlegen einer Replikationsmethode für eine Tabelle benötigen Sie [`Admin`](../../administrator/user-management/user-management.md) Berechtigungen, damit Sie auf Data Warehouse Manager zugreifen können.

1. Wählen Sie im Data Warehouse Manager die Tabelle aus der `Synced Tables` Liste aus, um das Schema der Tabelle anzuzeigen.
1. Die aktuelle Replikationsmethode wird unter dem Tabellennamen aufgeführt. Um ihn zu ändern, klicken Sie auf den Link.
1. Klicken Sie im angezeigten Popup auf die Optionsschaltfläche neben `Incremental` oder `Full Table` Replikation, um einen Replikationstyp auszuwählen.
1. Klicken Sie anschließend auf das Dropdown-Menü **[!UICONTROL Replication Method]** , um eine Methode auszuwählen. Beispiel: `Paused` oder `Modified At`.

   >[!NOTE]
   >
   >**Bei einigen inkrementellen Methoden müssen Sie einen`Replication Key`** festlegen. [!DNL Commerce Intelligence] verwendet diesen Schlüssel, um zu bestimmen, wo der nächste Aktualisierungszyklus beginnen soll.
   >
   >Wenn Sie beispielsweise die `modified at`-Methode für Ihre `orders`-Tabelle verwenden möchten, müssen Sie einen `date column` als Replikationsschlüssel festlegen. Es können mehrere Optionen für Replikationsschlüssel vorhanden sein, Sie wählen jedoch `created at` oder den Zeitpunkt aus, zu dem die Bestellung erstellt wurde. Wenn der letzte Aktualisierungszyklus am 12/1/2015 um 00::10: anhielt, würde der nächste Zyklus mit der Replikation von Daten beginnen, deren `created at` nach diesem Datum liegt.

1. Klicken Sie abschließend auf **[!UICONTROL Save]**.

Betrachten Sie den gesamten Prozess:

![Animierte Demonstration der Konfiguration von Replikationsmethoden für Datenbanktabellen](../../assets/replication_method.gif)<!--{: width="801" height="341"}-->

## Verpackung

Zum Abschluss haben Sie diese Tabelle zusammengestellt, die die verschiedenen Replikationsmethoden vergleicht. Dies ist äußerst praktisch, wenn Sie eine Methode für die Tabellen in Ihrer Data Warehouse auswählen.

| **`Method`** | **`Syncing New Data`** | **`Processing Rechecks on Large Data Sets`** | **`Handle Composite Keys?`** | **`Handle Non-Integer PKs?`** | **`Handle Non-Sequential PK Population?`** | **`Handle Row Deletion?`** |
|-----|-----|-----|-----|-----|-----|-----|
| `Auto-Incrementing Primary Key` | Schneller | Langsam | Nein | Nein | Nein | Ja |
| `Primary Key Batch Monitoring` | Langsam | Langsam | Ja | Ja | Ja | Ja |
| `Modified At` | Schneller | Schneller | Ja | Ja | Ja | Nein |

{style="table-layout:auto"}

## Verwandte Dokumentation

* [Grundlagen zu Datenprüfungen](../data-warehouse-mgr/cfg-data-rechecks.md)
* [Ändern der Datenbank zur Unterstützung von ](../../best-practices/mod-db-inc-replication.md)
* [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md)
* [Verkürzung der Aktualisierungszeiten](../../best-practices/reduce-update-cycle-time.md)
