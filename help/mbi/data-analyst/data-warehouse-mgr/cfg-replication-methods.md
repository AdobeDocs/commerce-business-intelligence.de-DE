---
title: Konfigurieren von Replikationsmethoden
description: Erfahren Sie, wie Tabellen organisiert sind und wie sich die Tabellendaten verhalten. So können Sie die beste Replikationsmethode für Ihre Tabellen auswählen.
exl-id: 83895c48-a6ec-4b01-9890-164e0b21dcbc
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '1455'
ht-degree: 0%

---

# Konfigurieren von Replikationsmethoden

`Replication` Methoden und [rechecks](../data-warehouse-mgr/cfg-data-rechecks.md) werden verwendet, um neue oder aktualisierte Daten in Ihren Datenbanktabellen zu identifizieren. Eine korrekte Einstellung ist für die Gewährleistung der Datengenauigkeit und optimierter Aktualisierungszeiten von entscheidender Bedeutung. In diesem Artikel werden wir uns nur auf Replikationsmethoden konzentrieren.

Wenn neue Tabellen im Data Warehousen-Manager synchronisiert werden, wird automatisch eine Replikationsmethode für die Tabelle ausgewählt. Anhand der verschiedenen Replikationsmethoden, der Organisation von Tabellen und des Verhaltens der Tabellendaten können Sie die beste Replikationsmethode für Ihre Tabellen auswählen.

## Was sind die Replikationsmethoden?

`Replication` -Methoden werden in drei Gruppen unterteilt - `Incremental`, `Full Table`und `Paused`.

[**[!UICONTROL Incremental Replication]**](#incremental) bedeutet, dass [!DNL MBI] repliziert bei jedem Replikationsversuch nur neue oder aktualisierte Daten. Da diese Methoden Latenzzeiten deutlich reduzieren, empfehlen wir dringend, sie nach Möglichkeit zu verwenden.

[**[!UICONTROL Full Table Replication]**](#fulltable) bedeutet, dass [!DNL MBI] repliziert bei jedem Replikationsversuch den gesamten Inhalt einer Tabelle. Aufgrund der potenziell großen Menge an zu replizierenden Daten können diese Methoden die Latenz und Aktualisierungszeiten erhöhen. Wenn eine Tabelle Zeitstempel- oder Datumszeitspalten enthält, wird stattdessen die Verwendung einer Inkrementellen Methode empfohlen.

**[!UICONTROL Paused]** gibt an, dass die Replikation für die Tabelle angehalten oder angehalten wurde. [!DNL MBI] während eines Aktualisierungszyklus nicht auf neue oder aktualisierte Daten prüfen; Dies bedeutet, dass keine Daten aus einer Tabelle repliziert werden, die dies als Replikationsmethode hat.

## Inkrementelle Replikationsmethoden {#incremental}

### Geändert am (am besten geeignet)

Die `Modified At` Die Replikationsmethode verwendet eine Datums-/Uhrzeitspalte, die bei der Erstellung einer Zeile gefüllt und dann bei Datenänderungen aktualisiert wird, um zu replizierende Daten zu finden. Diese Methode wurde für die Verwendung mit Tabellen entwickelt, die die folgenden Kriterien erfüllen:

* enthält `datetime` -Spalte, die beim Erstellen einer Zeile anfänglich gefüllt wird und bei jeder Änderung der Zeile aktualisiert wird;
* die `datetime` column ist nie null;
* Zeilen werden nicht aus der Tabelle gelöscht

Zusätzlich zu diesen Kriterien empfehlen wir dringend **Indizierung** die `datetime` Spalte, die für `Modified At` Replikation, da dies zur Optimierung der Replikationsgeschwindigkeit beiträgt.

Wenn die Aktualisierung ausgeführt wird, werden neue oder geänderte Daten identifiziert, indem nach Zeilen gesucht wird, die einen Wert im `datetime` -Spalte, die nach der letzten Aktualisierung aufgetreten ist. Wenn neue Zeilen gefunden werden, werden sie in Ihrer Data Warehouse repliziert. Wenn bereits Zeilen in der Data Warehouse vorhanden sind, werden sie mit den aktuellen Datenbankwerten überschrieben.

Eine Tabelle kann beispielsweise eine Spalte namens `modified\_at` , der angibt, wann die Daten zuletzt geändert wurden. Wenn die letzte Aktualisierung am Dienstag um Mittag ausgeführt wurde, sucht das Update nach allen Zeilen mit einer `modified\_at` Wert größer als Dienstag Mittag. Entdeckte Zeilen, die seit Dienstag Mittag erstellt oder geändert wurden, werden in der Data Warehouse repliziert.

**Wusstest du das?**
Auch wenn Ihre Datenbank derzeit keine Unterstützung für `Incremental` Replikationsmethode, können Sie [Änderungen an Ihrer Datenbank vornehmen](../../best-practices/mod-db-inc-replication.md) die Nutzung `Modified At` oder `Single Auto Incrementing PK`.

`Modified At` ist nicht nur die ideale Replikationsmethode, sondern auch die schnellste. Diese Methode führt nicht nur zu deutlichen Geschwindigkeitssteigerungen bei großen Datensätzen, sondern erfordert auch nicht die Konfiguration einer Wiederholungsoption. Andere Methoden müssen durch eine ganze Tabelle navigieren, um Änderungen zu identifizieren, selbst wenn sich eine kleine Datenuntergruppe geändert hat. `Modified At` durchläuft nur diese kleine Teilmenge.

### Einzelne automatische Erhöhung des Primären Schlüssels

`Auto Incrementing` ist ein Verhalten, das nacheinander Primärschlüssel Zeilen zuweist. Wenn eine Tabelle `Auto Incrementing` und der höchste Primärschlüssel in der Tabelle derzeit 1000 ist, wird der nächste Primärwert 1001 oder höher sein. Eine Tabelle, die nicht verwendet `Auto Incrementing` -Verhalten kann einen Primärschlüsselwert von unter 1000 zuweisen oder zu einer viel größeren Zahl springen, dies wird jedoch nicht häufig verwendet.

Diese Methode dient der Replikation neuer Daten aus Tabellen, die die folgenden Kriterien erfüllen:

* `single-column primary key`; und
* `primary key` datatype is `integer`; und
* `auto incrementing` Primärschlüsselwerte.

Wenn eine Tabelle `Single Auto Incrementing Primary Key` Replikation werden neue Daten erkannt, indem nach Primärschlüsselwerten gesucht wird, die über dem aktuellen Höchstwert in Ihrer Data Warehouse liegen. Wenn der höchste Primärschlüsselwert in Ihrer Data Warehouse beispielsweise 500 beträgt, wird bei der nächsten Aktualisierung nach Zeilen mit Primärschlüsselwerten von 501 oder höher gesucht.

### Datum hinzufügen

Die `Add Date` -Methodenfunktionen ähnlich wie `Single Auto Incrementing Primary Key` -Methode. Anstatt eine Ganzzahl für den Primärschlüssel der Tabelle zu verwenden, verwendet diese Methode einen `timestamped` auf neue Zeilen zu überprüfen.

Wenn eine Tabelle `Add Date` Replikation werden neue Daten erkannt, indem nach Zeitstempelwerten gesucht wird, die größer sind als das neueste mit Ihrer Data Warehouse synchronisierte Datum. Beispiel: Wenn eine Aktualisierung zuletzt am 12.20.2015 09 ausgeführt wurde:00:00, werden alle Zeilen mit einem Zeitstempel, der größer als dieser ist, als neue Daten markiert und repliziert.

>[!NOTE]
>
>Im Gegensatz zu `Modified At` -Methode, `Add Date` überprüft keine vorhandenen Zeilen auf aktualisierte Informationen - es werden nur neue Zeilen erwartet.

## Vollständige Tabellenreplikationsmethoden {#fulltable}

### Vollständige Tabelle

`Full table` Die Replikation aktualisiert die gesamte Tabelle, sobald neue Zeilen erkannt werden. Dies ist bei weitem die bei weitem am wenigsten effiziente Replikationsmethode, da alle Daten bei jeder Aktualisierung erneut verarbeitet werden müssen, vorausgesetzt, es gibt neue Zeilen.

Neue Zeilen werden erkannt, indem Sie Ihre Datenbank zu Beginn des Synchronisierungsprozesses abfragen und die Anzahl der Zeilen zählen. Wenn Ihre lokale Datenbank mehr Zeilen enthält als [!DNL MBI], wird die Tabelle aktualisiert. Wenn die Zeilenanzahl identisch ist oder wenn [!DNL MBI] contains *more* Zeilen als Ihre lokale Datenbank verwenden, wird die Tabelle übersprungen.

Daraus ergibt sich der wichtige Punkt, dass **`Full Table`Die Replikation ist inkompatibel, wenn:**

* zwischen den nachfolgenden Aktualisierungszyklen mehr Zeilen gelöscht als in Ihrer lokalen Datenbanktabelle erstellt wurden, oder
* Spaltenwerte werden geändert, es werden jedoch keine zusätzlichen Zeilen erstellt

In einem der oben genannten Szenarien `Full Table` Replikation erkennt keine Änderungen und Ihre Daten sind veraltet. Aufgrund der Ineffizienz dieser Replikationsmethode und der oben genannten Anforderungen, `Full Table` Die Replikation wird nur als letztes Mittel empfohlen.

### Primärer Schlüsselstapel

Wenn eine Tabelle `Primary Key Batch` (PK-Batch) werden neue Daten erkannt, indem Zeilen innerhalb von Bereichen oder Stapeln von Primärschlüsselwerten gezählt werden. Während wir normalerweise davon ausgehen, dass dies mit Ganzzahlen verwendet wird, können auch Textwerte so angeordnet werden, dass das System konstante Bereiche definieren kann.

Nehmen wir beispielsweise an, eine Aktualisierung wird ausgeführt und eine Zeilenanzahl für den Bereich von Schlüsseln zwischen 1 und 100 durchgeführt. In diesem Update sucht und protokolliert das System 37 Zeilen. In der nächsten Aktualisierung wird eine Zeilenanzahl für den Bereich 1-100 erneut durchgeführt und findet 41 Zeilen. Da es einen Unterschied in der Anzahl der Zeilen im Vergleich zur letzten Aktualisierung gibt, überprüft das System diesen Bereich (oder Batch) detaillierter.

Diese Methode dient zur Replikation von Daten aus Tabellen, die die folgenden Kriterien erfüllen:

* einspaltige Nicht-Ganzzahl; oder
* zusammengesetzte Schlüssel (mehrere Spalten, die den Primärschlüssel enthalten) - Beachten Sie, dass Spalten, die in einem zusammengesetzten Primärschlüssel verwendet werden, niemals Nullwerte haben können. oder
* einspaltige, Ganzzahl, nicht automatisch inkrementierende Primärschlüsselwerte.

Diese Methode ist nicht optimal, da sie aufgrund der Menge an Verarbeitung, die erforderlich ist, um Batches zu untersuchen und Änderungen zu finden, unglaublich langsam ist. Wir empfehlen die Verwendung dieser Methode nur, wenn es nicht möglich ist, die zur Unterstützung der anderen Replikationsmethoden erforderlichen Änderungen vorzunehmen. Wenn diese Methode verwendet werden soll, ist mit einer Erhöhung der Aktualisierungszeiten zu rechnen.

## Festlegen von Replikationsmethoden

Replikationsmethoden werden pro Tabelle festgelegt. Um eine Replikationsmethode für eine Tabelle festzulegen, benötigen Sie [`Admin`](../../administrator/user-management/user-management.md) -Berechtigungen, damit Sie auf den Data Warehouse Manager zugreifen können.

1. Wählen Sie im Data Warehousen-Manager die Tabelle aus der `Synced Tables` Liste, um das Schema der Tabelle anzuzeigen.
1. Die aktuelle Replikationsmethode ist unter dem Tabellennamen aufgeführt. Um sie zu ändern, klicken Sie auf den Link.
1. Klicken Sie im angezeigten Popup-Fenster auf das Optionsfeld neben `Incremental` oder `Full Table` Replikation zur Auswahl eines Replikationstyps.
1. Klicken Sie anschließend auf das **[!UICONTROL Replication Method]** Dropdown, um eine Methode auszuwählen, z. B. `Paused` oder `Modified At`.

   >[!NOTE]
   >
   >**Bei einigen inkrementellen Methoden müssen Sie eine`Replication Key`**. [!DNL MBI] verwendet diesen Schlüssel, um zu bestimmen, wo der nächste Aktualisierungszyklus beginnen soll.
   >
   >Wenn Sie beispielsweise die `modified at` -Methode `orders` -Tabelle, müssen wir eine `date column` als Replikationsschlüssel. Es können mehrere Optionen für Replikationsschlüssel vorhanden sein, aber wir wählen `created at`oder der Zeitpunkt, zu dem die Bestellung erstellt wurde. Wenn der letzte Aktualisierungszyklus am 12.1.2015 00 angehalten wurde:10:00 würde der nächste Zyklus mit der Replikation von Daten mit einer `created at` Datum größer als dieser.

1. Klicken Sie abschließend auf **[!UICONTROL Save]**.

Sehen Sie sich den gesamten Prozess an:

![](../../assets/replication_method.gif)<!--{: width="801" height="341"}-->

## Aufbrechen

Abschließend haben wir diese Tabelle zusammengestellt, in der die verschiedenen Replikationsmethoden verglichen werden. Wir finden es unglaublich praktisch bei der Auswahl einer Methode für die Tabellen in unserem Data Warehouse.

| **`Method`** | **`Syncing New Data`** | **`Processing Rechecks on Large Data Sets`** | **`Handle Composite Keys?`** | **`Handle Non-Integer PKs?`** | **`Handle Non-Sequential PK Population?`** | **`Handle Row Deletion?`** |
|-----|-----|-----|-----|-----|-----|-----|
| `Auto-Incrementing Primary Key` | Schneller | Langsam | Nein | Nein | Nein | Ja |
| `Primary Key Batch Monitoring` | Langsam | Langsam | Ja | Ja | Ja | Ja |
| `Modified At` | Schneller | Schneller | Ja | Ja | Ja | Nein |

{style=&quot;table-layout:auto&quot;}

## Verwandte Dokumentation

* [Grundlegendes zu Datenaufladungen](../data-warehouse-mgr/cfg-data-rechecks.md)
* [Ändern der Datenbank zur Unterstützung ](../../best-practices/mod-db-inc-replication.md)
* [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md)
* [Verkürzen der Aktualisierungszeiten](../../best-practices/reduce-update-cycle-time.md)
