---
title: Konfigurieren von Replikationsmethoden
description: Erfahren Sie, wie Tabellen organisiert sind und wie sich die Tabellendaten verhalten. So können Sie die beste Replikationsmethode für Ihre Tabellen auswählen.
exl-id: 83895c48-a6ec-4b01-9890-164e0b21dcbc
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Data Import/Export
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1433'
ht-degree: 0%

---

# Konfigurieren von Replikationsmethoden

`Replication` -Methoden und [rechecks](../data-warehouse-mgr/cfg-data-rechecks.md) werden verwendet, um neue oder aktualisierte Daten in Ihren Datenbanktabellen zu identifizieren. Eine korrekte Einstellung ist für die Gewährleistung der Datengenauigkeit und optimierter Aktualisierungszeiten von entscheidender Bedeutung. Dieses Thema konzentriert sich auf Replikationsmethoden.

Wenn neue Tabellen im [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md) synchronisiert werden, wird automatisch eine Replikationsmethode für die Tabelle ausgewählt. Anhand der verschiedenen Replikationsmethoden, der Organisation von Tabellen und des Verhaltens der Tabellendaten können Sie die beste Replikationsmethode für Ihre Tabellen auswählen.

## Was sind die Replikationsmethoden?

`Replication` Methoden fallen in drei Gruppen - `Incremental`, `Full Table` und `Paused`.

[**[!UICONTROL Incremental Replication]**](#incremental) bedeutet, dass [!DNL Commerce Intelligence] bei jedem Replikationsversuch nur neue oder aktualisierte Daten repliziert. Da diese Methoden die Latenz stark reduzieren, empfiehlt Adobe, sie nach Möglichkeit zu verwenden.

[**[!UICONTROL Full Table Replication]**](#fulltable) bedeutet, dass [!DNL Commerce Intelligence] bei jedem Replikationsversuch den gesamten Inhalt einer Tabelle repliziert. Aufgrund der potenziell großen Menge an zu replizierenden Daten können diese Methoden die Latenz und Aktualisierungszeiten erhöhen. Wenn eine Tabelle Zeitstempel- oder Datumszeitspalten enthält, empfiehlt Adobe stattdessen die Verwendung einer Inkrementellen Methode.

**[!UICONTROL Paused]** gibt an, dass die Replikation für die Tabelle angehalten oder angehalten wurde. [!DNL Commerce Intelligence] sucht während eines Aktualisierungszyklus nicht nach neuen oder aktualisierten Daten. Dies bedeutet, dass keine Daten aus einer Tabelle repliziert werden, die dies als Replikationsmethode hat.

## Inkrementelle Replikationsmethoden {#incremental}

### Geändert am (am besten geeignet)

Die Replikationsmethode `Modified At` verwendet eine Datums-/Uhrzeitspalte, die bei der Erstellung einer Zeile und deren anschließender Aktualisierung bei Datenänderungen aufgefüllt wird, um zu replizierende Daten zu finden. Diese Methode wurde für die Verwendung mit Tabellen entwickelt, die die folgenden Kriterien erfüllen:

* enthält eine Spalte &quot;`datetime`&quot;, die beim Erstellen einer Zeile anfänglich gefüllt wird und bei jeder Änderung der Zeile aktualisiert wird;
* die Spalte `datetime` ist nie null;
* Zeilen werden nicht aus der Tabelle gelöscht

Zusätzlich zu diesen Kriterien empfiehlt Adobe die **Indizierung** für die `datetime` -Spalte, die für die `Modified At`-Replikation verwendet wird, da dies die Replikationsgeschwindigkeit optimiert.

Beim Ausführen der Aktualisierung werden neue oder geänderte Daten identifiziert, indem nach Zeilen gesucht wird, die einen Wert in der Spalte `datetime` aufweisen, der nach der letzten Aktualisierung aufgetreten ist. Wenn neue Zeilen gefunden werden, werden sie auf Ihrer Data Warehouse repliziert. Wenn Zeilen im [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md) vorhanden sind, werden sie mit den aktuellen Datenbankwerten überschrieben.

Eine Tabelle kann beispielsweise eine Spalte mit dem Namen `modified\_at` enthalten, die angibt, wann die Daten zuletzt geändert wurden. Wenn die letzte Aktualisierung Dienstag um Mittag ausgeführt wurde, sucht die Aktualisierung nach allen Zeilen, deren `modified\_at` -Wert größer ist als Dienstag Mittag. Entdeckte Zeilen, die seit Dienstag Mittag erstellt oder geändert wurden, werden auf der Data Warehouse repliziert.

**Wusstest du das?**
Selbst wenn Ihre Datenbank derzeit keine `Incremental` Replikationsmethode unterstützt, können Sie [Änderungen an Ihrer Datenbank vornehmen](../../best-practices/mod-db-inc-replication.md), die die Verwendung von `Modified At` oder `Single Auto Incrementing PK` ermöglichen würden.

`Modified At` ist nicht nur die ideale Replikationsmethode, sondern auch die schnellste. Diese Methode führt nicht nur zu deutlichen Geschwindigkeitssteigerungen bei großen Datensätzen, sondern erfordert auch nicht die Konfiguration einer Wiederholungsoption. Andere Methoden müssen durch eine ganze Tabelle navigieren, um Änderungen zu identifizieren, selbst wenn sich eine kleine Datenuntergruppe geändert hat. `Modified At` durchläuft nur diese kleine Teilmenge.

### Einzelne automatische Erhöhung des Primären Schlüssels

`Auto Incrementing` ist ein Verhalten, das nacheinander Primärschlüssel Zeilen zuweist. Wenn eine Tabelle den Wert &quot;`Auto Incrementing`&quot;hat und der höchste Primärschlüssel in der Tabelle den Wert &quot;1.000&quot;hat, beträgt der nächste Primärwert 1.001 oder höher. Eine Tabelle, die kein &quot;`Auto Incrementing`&quot;-Verhalten verwendet, kann einen Primärschlüsselwert von weniger als 1.000 zuweisen oder zu einer viel größeren Zahl springen, dies wird jedoch nicht häufig verwendet.

Diese Methode dient der Replikation neuer Daten aus Tabellen, die die folgenden Kriterien erfüllen:

* `single-column primary key` und
* `primary key` datatype ist `integer` und
* `auto incrementing` Primärschlüsselwerte.

Wenn eine Tabelle die `Single Auto Incrementing Primary Key`-Replikation verwendet, werden neue Daten erkannt, indem nach Primärschlüsselwerten gesucht wird, die höher sind als der aktuelle höchste Wert in Ihrer Data Warehouse. Wenn der höchste Primärschlüsselwert in Ihrer Data Warehouse beispielsweise 500 beträgt, wird bei der nächsten Aktualisierung nach Zeilen mit Primärschlüsselwerten von 501 oder höher gesucht.

### Datum hinzufügen

Die `Add Date` -Methode funktioniert ähnlich wie die `Single Auto Incrementing Primary Key` -Methode. Anstatt eine Ganzzahl für den Primärschlüssel der Tabelle zu verwenden, verwendet diese Methode eine `timestamped` -Spalte, um nach neuen Zeilen zu suchen.

Wenn eine Tabelle die `Add Date`-Replikation verwendet, werden neue Daten erkannt, indem nach Zeitstempelwerten gesucht wird, die größer sind als das neueste mit Ihrer Data Warehouse synchronisierte Datum. Beispiel: Wenn eine Aktualisierung zuletzt am 12.20.2015 ausgeführt wurde, 09.0}00, werden alle Zeilen mit einem Zeitstempel, der größer als dieser ist, als neue Daten markiert und repliziert.:00:

>[!NOTE]
>
>Im Gegensatz zur `Modified At` -Methode überprüft `Add Date` vorhandene Zeilen nicht auf aktualisierte Informationen - es werden nur neue Zeilen erwartet.

## Vollständige Tabellenreplikationsmethoden {#fulltable}

### Vollständige Tabelle

Die `Full table`-Replikation aktualisiert die gesamte Tabelle, sobald neue Zeilen erkannt werden. Dies ist bei weitem die bei weitem am wenigsten effiziente Replikationsmethode, da alle Daten bei jeder Aktualisierung erneut verarbeitet werden müssen, vorausgesetzt, es gibt neue Zeilen.

Neue Zeilen werden erkannt, indem Sie Ihre Datenbank zu Beginn des Synchronisierungsprozesses abfragen und die Anzahl der Zeilen zählen. Wenn Ihre lokale Datenbank mehr Zeilen als [!DNL Commerce Intelligence] enthält, wird die Tabelle aktualisiert. Wenn die Zeilenanzahl identisch ist oder [!DNL Commerce Intelligence] *mehr* Zeilen enthält als Ihre lokale Datenbank, wird die Tabelle übersprungen.

Dies wirft den wichtigen Punkt auf, dass die **`Full Table`-Replikation nicht kompatibel ist, wenn:**

* zwischen den nachfolgenden Aktualisierungszyklen mehr Zeilen gelöscht als in Ihrer lokalen Datenbanktabelle erstellt wurden, oder
* Spaltenwerte werden geändert, es werden jedoch keine zusätzlichen Zeilen erstellt.

In einem der obigen Szenarien erkennt die `Full Table`-Replikation keine Änderungen und Ihre Daten sind veraltet. Aufgrund der Ineffizienz dieser Replikationsmethode und der oben erwähnten Anforderungen wird die `Full Table`-Replikation nur als letztes Mittel empfohlen.

### Batch mit Primärem Schlüssel

Wenn eine Tabelle `Primary Key Batch` (PK-Batch) verwendet, werden neue Daten erkannt, indem Zeilen innerhalb von Bereichen oder Stapeln von Primärschlüsselwerten gezählt werden. Während Sie sich normalerweise vorstellen, dass dies mit Ganzzahlen verwendet wird, können auch Textwerte so angeordnet werden, dass das System konstante Bereiche definieren kann.

Angenommen, eine Aktualisierung wird ausgeführt und eine Zeilenanzahl für den Bereich von Schlüsseln zwischen 1 und 100 durchgeführt. In diesem Update sucht und protokolliert das System 37 Zeilen. In der nächsten Aktualisierung wird eine Zeilenanzahl für den Bereich 1-100 erneut durchgeführt und findet 41 Zeilen. Da die Anzahl der Zeilen im Vergleich zur letzten Aktualisierung unterschiedlich ist, prüft das System diesen Bereich (oder Batch) detaillierter.

Diese Methode dient zur Replikation von Daten aus Tabellen, die die folgenden Kriterien erfüllen:

* einspaltige Nicht-Ganzzahl oder
* zusammengesetzte Schlüssel (mehrere Spalten, die den Primärschlüssel enthalten) - beachten Sie, dass in einem zusammengesetzten Primärschlüssel verwendete Spalten niemals Nullwerte haben können; oder
* einspaltige, Ganzzahl, nicht automatisch inkrementierende Primärschlüsselwerte.

Diese Methode ist nicht optimal, da sie aufgrund der Menge an Verarbeitung, die erforderlich ist, um Batches zu untersuchen und Änderungen zu finden, unglaublich langsam ist. Adobe empfiehlt, diese Methode nicht zu verwenden, es sei denn, es ist unmöglich, die erforderlichen Änderungen zur Unterstützung der anderen Replikationsmethoden vorzunehmen. Wenn diese Methode verwendet werden soll, ist mit einer Erhöhung der Aktualisierungszeiten zu rechnen.

## Festlegen von Replikationsmethoden

Replikationsmethoden werden pro Tabelle festgelegt. Um eine Replikationsmethode für eine Tabelle festzulegen, benötigen Sie [`Admin`](../../administrator/user-management/user-management.md) -Berechtigungen, damit Sie auf den Data Warehouse-Manager zugreifen können.

1. Wählen Sie im Data Warehouse-Manager die Tabelle aus der Liste `Synced Tables` aus, um das Tabellenschema anzuzeigen.
1. Die aktuelle Replikationsmethode ist unter dem Tabellennamen aufgeführt. Um sie zu ändern, klicken Sie auf den Link.
1. Klicken Sie im angezeigten Popup-Fenster auf das Optionsfeld neben der Replikation `Incremental` oder `Full Table` , um einen Replikationstyp auszuwählen.
1. Klicken Sie anschließend auf das Dropdown-Menü **[!UICONTROL Replication Method]** , um eine Methode auszuwählen. Beispiel: `Paused` oder `Modified At`.

   >[!NOTE]
   >
   >**Bei einigen inkrementellen Methoden müssen Sie einen`Replication Key`** festlegen. [!DNL Commerce Intelligence] verwendet diesen Schlüssel, um zu bestimmen, wo der nächste Aktualisierungszyklus beginnen soll.
   >
   >Wenn Sie beispielsweise die `modified at` -Methode für Ihre `orders`-Tabelle verwenden möchten, müssen Sie einen `date column` als Replikationsschlüssel festlegen. Es können mehrere Optionen für Replikationsschlüssel vorhanden sein, Sie wählen jedoch `created at` oder den Zeitpunkt, zu dem die Bestellung erstellt wurde. Wenn der letzte Aktualisierungszyklus am 12.1.2015 00:10:00 angehalten wurde, beginnt der nächste Zyklus mit der Replikation von Daten mit einem `created at` Datum größer als dieser.

1. Klicken Sie abschließend auf **[!UICONTROL Save]**.

Betrachten Sie den gesamten Prozess:

![](../../assets/replication_method.gif)<!--{: width="801" height="341"}-->

## Aufwischen

Abschließend haben Sie diese Tabelle erstellt, in der die verschiedenen Replikationsmethoden verglichen werden. Es ist unglaublich praktisch bei der Auswahl einer Methode für die Tabellen in Ihrem Data Warehouse.

| **`Method`** | **`Syncing New Data`** | **`Processing Rechecks on Large Data Sets`** | **`Handle Composite Keys?`** | **`Handle Non-Integer PKs?`** | **`Handle Non-Sequential PK Population?`** | **`Handle Row Deletion?`** |
|-----|-----|-----|-----|-----|-----|-----|
| `Auto-Incrementing Primary Key` | Schneller | Langsam | Nein | Nein | Nein | Ja |
| `Primary Key Batch Monitoring` | Langsam | Langsam | Ja | Ja | Ja | Ja |
| `Modified At` | Schneller | Schneller | Ja | Ja | Ja | Nein |

{style="table-layout:auto"}

## Verwandte Dokumentation

* [Grundlegendes zu Datenaufladungen](../data-warehouse-mgr/cfg-data-rechecks.md)
* [Ändern der Datenbank zur Unterstützung ](../../best-practices/mod-db-inc-replication.md)
* [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md)
* [Verkürzen der Aktualisierungszeiten](../../best-practices/reduce-update-cycle-time.md)
