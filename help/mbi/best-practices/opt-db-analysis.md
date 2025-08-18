---
title: Datenbank für Analysen optimieren
description: Erfahren Sie, wie Sie Ihre Datenbank für Analysen optimieren können.
exl-id: e73e1a1e-c933-476d-97bc-bd8f52bb2fa1
role: Admin, Data Architect, Data Engineer, User
feature: Business Performance, Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Datenbank optimieren

Der Hauptvorteil der Verwendung einer operativen Datenbank für [!DNL Adobe Commerce Intelligence] besteht darin, dass zum Erfassen von Daten nichts erstellt oder geändert werden muss. Wertvolle Informationen sind bereits vorhanden - Sie müssen sie nur entsperren.

Dieses Thema enthält einige Empfehlungen, wie Sie Ihre Datenbank für Analysen optimieren und aus Rohdaten verwertbare Einblicke gewinnen können.

## Daten nicht löschen

>[!TIP]
>
>Die lokalen und internationalen Gesetze, die sich auf Ihr Unternehmen (und Ihre eigenen Nutzungsbedingungen) auswirken, können beeinflussen, welche Arten von Daten Sie speichern können und wie lange Sie sie aufbewahren können. Die Einhaltung dieser Gesetze sollte Ihre oberste Priorität sein.

Wenn eine Bestellung storniert wird, ein Benutzer sein Konto deaktiviert oder ein Produkt eingestellt wird, ist es verlockend, die zugehörigen Informationen in der Datenbank zu löschen. Die Tabellen wachsen und die Beseitigung von Unordnung scheint eine vernünftige Idee zu sein. Das Löschen von Zeilen bedeutet jedoch, dass diese Informationen für immer verloren gehen oder Sie alte Backups durchsuchen müssen, um sie zu finden.

Stattdessen können Sie der Tabelle eine Statusspalte hinzufügen, die anzeigt, wann die Zeile nicht mehr aktiv oder relevant ist. Es wird außerdem empfohlen, eine Spalte hinzuzufügen, in der das Datum gespeichert wird, an dem die Änderung vorgenommen wurde, oder ein Protokoll für historische Änderungen zu erstellen. Wenn Tabellen so groß werden, dass die Leistung beeinträchtigt wird, sollten Sie die alten Daten in einer für die Analyse verwendeten Tabelle archivieren.

## Daten nur selten überschreiben

Das Überschreiben von Daten sollte sparsam und mit Vorsicht erfolgen.

Anhand von Anmeldedaten speichern viele Unternehmen das letzte Anmeldedatum anstelle einer Tabelle mit historischen Anmeldungen. Möglicherweise benötigen Sie nur das letzte Anmeldedatum für funktionale Zwecke. Diese überschriebenen Daten stellen jedoch aus Analytics-Sicht einen enormen Verlust dar. Wenn Sie kein vollständiges Protokoll dieser Aktionen führen, können Sie nicht mehr sehen, wie viele Benutzer über einen langen Zeitraum hinweg ferngeblieben und dann wieder aktiviert sind. Es macht es auch unmöglich, Dinge wie Kohortenanalysen zur Benutzerinteraktion auf der Grundlage von Anmeldungen zu erstellen.

Wenn Sie einen Datensatz aufgrund einer Benutzeraktion aktualisieren, überschreiben Sie im Allgemeinen nicht die Informationen zu einer vorherigen oder separaten Benutzeraktion.

## `Updated_at` Spalten für Daten einschließen, die im Laufe der Zeit aktualisiert werden

Wenn sich die Werte in den Zeilen einer Tabelle im Laufe der Zeit ändern, z. B. **order\_status** von`processing` zu `complete`, schließen Sie eine **updated\_at**-Spalte ein, um aufzuzeichnen, wann die letzte Änderung erfolgt. Stellen Sie sicher **dass beim ersten Einfügen der neuen Datenzeile ein** updated\_at) verfügbar ist, wenn das **updated\_at**-Datum dem **created\_at**-Datum entspricht.

Zusätzlich zur Optimierung für die Analyse können Sie mit **updated\_at**-Spalten auch [inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md) verwenden, was dazu beitragen kann, die Länge Ihrer Aktualisierungszyklen zu verkürzen.

## Source zur Benutzerakquise speichern

Einer der häufigsten Fehler ist, dass [User Acquisition Source](../data-analyst/analysis/google-track-user-acq.md) (UAS) nicht in der Betriebsdatenbank gespeichert wird. In den meisten Situationen, in denen dies ein Problem darstellt, wird UAS nur über [!DNL Google Analytics] oder ein anderes Web-Analyse-Tool verfolgt. Obwohl diese Tools nützlich sein können, hat die ausschließliche Speicherung von UAS in ihnen einige Nachteile, z. B. dass Sie keine Daten auf Benutzerebene aus diesen Tools extrahieren können. Wenn es möglich ist, ist es in der Regel ein schwieriger Prozess. Es sollte einfach sein, diese Informationen abzurufen und sie mit Daten aus anderen Quellen zu verbinden, z. B. den Verhaltens- und Transaktionsinformationen, die ebenfalls in Ihrer Datenbank gespeichert sind.

Das Speichern von UAS in Ihrer eigenen Datenbank ist oft die größte Verbesserung, die ein Online-Unternehmen an seinen Analysefunktionen vornehmen kann. Dies ermöglicht die Analyse von Verkäufen, Benutzerinteraktion, Amortisationszeiten, Kundenlebenszeitwert, Abwanderung und anderen kritischen Metriken durch UAS. [Diese Daten sind bei der Entscheidung, wo Marketing-Ressourcen investiert werden sollen, von entscheidender Bedeutung](../data-analyst/analysis/most-value-source-channel.md).

Zu viele Unternehmen konzentrieren sich ausschließlich auf die Suche nach Kanälen, die neue Benutzer zu den niedrigsten Kosten anbieten. Wenn Sie die Qualität der von den einzelnen Kanälen erworbenen Benutzer nicht verfolgen, laufen Sie Gefahr, Benutzer anzulocken, die keinen Geschäftswert generieren.

## Einrichtung der Datentabelle

### Primären Schlüssel festlegen

Ein [Primärschlüssel](https://en.wikipedia.org/wiki/Unique_key) ist eine unveränderliche Spalte (oder Gruppe von Spalten), die eindeutige Werte innerhalb einer Tabelle erzeugt. Primäre Schlüssel sind unglaublich wichtig, da sie sicherstellen, dass Ihre Tabellen ordnungsgemäß in [!DNL Commerce Intelligence] repliziert werden.

Verwenden Sie beim Erstellen von Primärschlüsseln einen ganzzahligen Datentyp für die Spalte, die automatisch erhöht wird. Adobe empfiehlt, nach Möglichkeit die Verwendung mehrspaltiger Primärschlüssel zu vermeiden.

Wenn es sich bei Ihrer Tabelle um eine SQL-Ansicht handelt, fügen Sie eine Spalte hinzu, die als Primärschlüssel dienen kann. [!DNL Commerce Intelligence] kann diese Spalte automatisch als Primärschlüssel identifizieren.

### Zuweisen eines Datentyps zu Ihrer Datenspalte

Wenn einer Datenspalte kein [Datentyp“ zugewiesen ist](https://en.wikipedia.org/wiki/Data_type) schätzt [!DNL Commerce Intelligence], welcher Datentyp verwendet werden soll. Wenn das System falsch schätzt, können Sie die entsprechenden Analysen möglicherweise erst durchführen, wenn das Adobe-Supportteam die Spalte an den richtigen Datentyp angepasst hat. Wenn beispielsweise eine Datumsspalte als numerischer Datentyp geschätzt wird, können Sie mithilfe dieser Datumsdimension einen Trend im Zeitverlauf durchführen.

### Fügen Sie Ihren Datentabellen Präfixe hinzu, wenn Sie mehrere Datenbanken haben

Wenn mehr als eine Datenbank mit [!DNL Commerce Intelligence] verbunden ist, empfiehlt Adobe, den Tabellen Präfixe hinzuzufügen, um Verwirrung zu vermeiden. Präfixe helfen Ihnen dabei, sich zu merken, woher Metriken oder Datendimensionen stammen.
