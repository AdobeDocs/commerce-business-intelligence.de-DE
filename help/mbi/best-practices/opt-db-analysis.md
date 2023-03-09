---
title: Datenbank für Analysen optimieren
description: Erfahren Sie, wie Sie Ihre Datenbank für die Analyse optimieren können.
exl-id: e73e1a1e-c933-476d-97bc-bd8f52bb2fa1
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# Datenbank optimieren

Der Hauptvorteil der Nutzung einer operativen Datenbank für Business Intelligence besteht darin, dass nichts erstellt oder geändert werden muss, um Daten zu erfassen. Es gibt bereits wertvolle Informationen. Du musst nichts weiter tun, als es zu entsperren.

Dieses Thema enthält einige Empfehlungen, mit denen Sie Ihre Datenbank für die Analyse optimieren und aus Rohdaten umsetzbare Einblicke gewinnen können.

## Daten nicht löschen

>[!TIP]
>
>Die lokalen und internationalen Gesetze, die Ihr Geschäft (und Ihre eigenen Servicebestimmungen) beeinflussen können, welche Datentypen Sie beibehalten können und wie lange Sie sie behalten können. Die Einhaltung dieser Gesetze sollte oberste Priorität haben.

Wenn eine Bestellung storniert, ein Benutzer sein Konto deaktiviert oder ein Produkt eingestellt wird, ist es versucht, die zugehörigen Informationen in der Datenbank zu löschen. Tabellen wachsen und beseitigen Unübersichtlichkeit scheint eine umsichtige Idee zu sein. Das Löschen von Zeilen bedeutet jedoch, dass diese Informationen für immer verloren gehen oder dass Sie alte Sicherungen durchsuchen müssen, um sie zu finden.

Stattdessen können Sie der Tabelle eine Statusspalte hinzufügen, die angibt, wann die Zeile nicht mehr aktiv oder relevant ist. Es wird außerdem empfohlen, eine Spalte hinzuzufügen, in der das Datum der Änderung gespeichert wird, oder ein Protokoll für historische Änderungen zu erstellen. Wenn Tabellen so groß sind, dass die Leistung langsam zunimmt, sollten Sie die alten Daten in einer für Analysen verwendeten Tabelle archivieren.

## Daten selten überschreiben

Das Überschreiben von Daten sollte sparsam und mit Vorsicht erfolgen.

Unter Verwendung von Anmeldedaten als Beispiel speichern viele Unternehmen das letzte Anmeldedatum und nicht eine Tabelle historischer Anmeldungen. Auch wenn Sie für funktionale Zwecke möglicherweise nur das letzte Anmeldedatum benötigen, stellen überschriebene Daten aus der Sicht der Analyse einen enormen Verlust dar. Wenn Sie kein vollständiges Protokoll dieser Aktionen speichern, können Sie nicht mehr sehen, wie viele Benutzer lange Zeit weg blieben und dann reaktiviert wurden. Außerdem ist es unmöglich, auf der Grundlage von Anmeldungen Kohortenanalysen für die Benutzerinteraktion zu erstellen.

Wenn Sie einen Datensatz aufgrund einer Benutzeraktion aktualisieren, überschreiben Sie im Allgemeinen keine Informationen über eine vorherige oder separate Benutzeraktion.

## Einschließen `Updated_at` Spalten für Daten, die im Zeitverlauf aktualisiert wurden

Wenn die Zeilen einer Tabelle Werte im Laufe der Zeit ändern, z. B.: **order\_status** Änderungen von`processing` nach `complete`, fügen Sie eine **updated\_at** -Spalte, um aufzuzeichnen, wann die letzte Änderung erfolgt. Stellen Sie sicher, dass **updated\_at** beim ersten Einfügen der neuen Datenzeile verfügbar ist, wenn die **updated\_at** date entspricht dem **created\_at** Datum.

Neben der Optimierung für die Analyse **updated\_at** -Spalten ermöglichen Ihnen auch die Verwendung von [Inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md), was dazu beitragen kann, die Länge Ihrer Aktualisierungszyklen zu verkürzen.

## Store User Acquisition Source

Einer der häufigsten Fehler ist der [Benutzerakquise-Quelle](../data-analyst/analysis/google-track-user-acq.md) (UAS) nicht in der Betriebsdatenbank gespeichert. In den meisten Fällen, in denen dies ein Problem ist, wird die AS nur verfolgt [!DNL Google Analytics] oder einem anderen Webanalysetool. Diese Instrumente können zwar nützlich sein, doch gibt es einige Nachteile, die die ausschließliche Lagerung von UAS in diesen Instrumenten mit sich bringt. Sie können beispielsweise keine Daten auf Benutzerebene aus diesen Tools extrahieren. Wenn es möglich ist, ist es normalerweise ein schwieriger Prozess. Es sollte einfach sein, diese Informationen zu erhalten und sie mit Daten aus anderen Quellen zu verbinden, z. B. mit den Verhaltens- und Transaktionsdaten, die ebenfalls in Ihrer Datenbank gespeichert sind.

Die Speicherung von UAS in Ihrer eigenen Datenbank ist oft die größte Verbesserung, die ein Online-Unternehmen an seinen analytischen Fähigkeiten vornehmen kann. Dies ermöglicht die Analyse von Vertrieb, Benutzerinteraktion, Payback-Zeiträumen, Kundenlebenszeitwert, Abwanderung und anderen kritischen Metriken nach UAS. [Diese Daten sind bei der Entscheidung, wo Marketing-Ressourcen investiert werden, von entscheidender Bedeutung](../data-analyst/analysis/most-value-source-channel.md).

Zu viele Unternehmen konzentrieren sich ausschließlich auf die Suche nach Kanälen, die neue Benutzer zu niedrigsten Kosten anbieten. Wenn Sie die Qualität der von den einzelnen Kanälen erworbenen Benutzer nicht verfolgen, besteht das Risiko, Benutzer anzuziehen, die keinen Geschäftswert generieren.

## Einrichten von Datentabellen

### Festlegen eines Primären Schlüssels

A [Primärschlüssel](https://en.wikipedia.org/wiki/Unique_key) ist eine unveränderliche Spalte (oder ein Satz von Spalten), die eindeutige Werte in einer Tabelle erzeugt. Primäre Schlüssel sind sehr wichtig, da sie sicherstellen, dass Ihre Tabellen ordnungsgemäß repliziert werden in [!DNL MBI].

Verwenden Sie beim Erstellen von Primärschlüsseln einen ganzzahligen Datentyp für die Spalte, die automatisch erhöht wird. Adobe empfiehlt, die Verwendung von mehrspaltigen Primärschlüsseln möglichst zu vermeiden.

Wenn es sich bei Ihrer Tabelle um eine SQL-Ansicht handelt, fügen Sie eine Spalte hinzu, die als Primärschlüssel dienen kann. [!DNL MBI] kann diese Spalte automatisch als Primärschlüssel identifizieren.

### Datentyp zu Ihrer Datenspalte zuweisen

Wenn einer Datenspalte keine [Datentyp](https://en.wikipedia.org/wiki/Data_type), [!DNL MBI] rät, welcher Datentyp verwendet werden soll. Wenn das System falsch einschätzt, können Sie die entsprechenden Analysen erst dann durchführen, wenn das Adobe Support-Team die Spalte an den entsprechenden Datentyp anpasst. Wenn beispielsweise eine Datumsspalte als numerischer Datentyp betrachtet wird, können Sie mithilfe dieser Datumsdimension einen Trend im Zeitverlauf erstellen.

### Hinzufügen von Präfixen zu Ihren Datentabellen, wenn mehrere Datenbanken vorhanden sind

Wenn mehrere Datenbanken mit [!DNL MBI]empfiehlt Adobe, den Tabellen Präfixe hinzuzufügen, um Verwirrung zu vermeiden. Mit Präfixen können Sie sich merken, woher Metriken oder Datendimensionen stammen.
