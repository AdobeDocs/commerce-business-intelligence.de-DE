---
title: Ändern der Datenbank zur Unterstützung der inkrementellen Replikation
description: Erfahren Sie, wie Sie Ihre Datenbank ändern, um die inkrementelle Replikation zu unterstützen.
exl-id: c9a38892-6096-4eb5-8a53-35b8b7b083dc
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Unterstützung für inkrementelle Replikation

Wenn Ihre Tabellen derzeit keine inkrementelle Replikation zulassen, finden Sie in den folgenden Empfehlungen Lösungsmöglichkeiten.

## Änderungen für geändert am

Die `Modified At` -Methode, die am besten geeignete Replikationsmethode ist, verwendet eine `datetime` -Spalte, um neue und/oder aktualisierte Daten zu erkennen. Beachten Sie, dass die Spalte &quot;`datetime`&quot; in Tabellen, die diese Methode verwenden, indiziert sein muss und keine Nullwerte enthalten darf.

Wenn Ihre Tabelle keine `datetime` -Spalte enthält, können Sie eine Index `modified at` -Spalte hinzufügen. Null-Werte sind in einer `modified at` -Spalte nicht zulässig. Überprüfen Sie, ob die Spalte für jede Zeile gefüllt ist.

Um sicherzustellen, dass die `Modified At` -Methode wie gewünscht funktioniert, können Sie keine Zeilen aus der Tabelle löschen. Stattdessen sollten Sie die Zeile als ungültig markieren, indem Sie der Tabelle eine `deleted` -Spalte hinzufügen. Diese Spalte gibt einen `1` zurück, wenn die Zeile ungültig ist, andernfalls `0`. Anschließend können Sie diese Spalte verwenden, um ungültige Zeilen beim Erstellen von Metriken und Berichten herauszufiltern.

## Änderungen für die automatische Erhöhung des Primären Schlüssels

Wenn die `Modified At` -Methode nicht aktiviert werden kann, ist die Option Primärer Einzelner, automatisch inkrementierender Schlüssel die nächste beste Option. Neue Daten werden in Tabellen mit dieser Methode erkannt, indem nach Primärschlüsselwerten gesucht wird, die höher sind als der aktuelle höchste Wert in der Data Warehouse.

Beachten Sie, dass Tabellen, die diese Methode verwenden, eine einzelne Spalte sind, wobei die Ganzzahl automatisch die Primärschlüssel inkrementiert. Um diese Methode in Ihrer Datenbank zu verwenden, nehmen Sie die folgenden Änderungen vor:

* Wenn der Primärschlüssel entweder ein zusammengesetzter Schlüssel oder eine Nicht-Ganzzahl ist, ändern Sie den Primärschlüssel in eine automatisch inkrementierende Ganzzahl
* Wenn der Primärschlüssel eine einzelne Ganzzahlspalte ist, Schlüssel jedoch nicht sequenziell zugewiesen werden können, ändern Sie den Primärschlüssel in automatische Inkrementierung

## Aufwischen

Durch geringfügige Änderungen an Ihren Tabellen können Sie die schnelleren und effizienteren Methoden für die inkrementelle Replikation nutzen. Ist dies jedoch nicht möglich, können Sie weitere Schritte durchführen, um [Ihre Aktualisierungszeit zu reduzieren](../best-practices/reduce-update-cycle-time.md) und [Ihre Datenbank zu optimieren](../best-practices/opt-db-analysis.md).
