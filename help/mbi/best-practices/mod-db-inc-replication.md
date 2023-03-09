---
title: Ändern der Datenbank zur Unterstützung der inkrementellen Replikation
description: Erfahren Sie, wie Sie Ihre Datenbank ändern, um die inkrementelle Replikation zu unterstützen.
exl-id: c9a38892-6096-4eb5-8a53-35b8b7b083dc
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Unterstützung für inkrementelle Replikation

Wenn Ihre Tabellen derzeit keine inkrementelle Replikation zulassen, finden Sie in den folgenden Empfehlungen Lösungsmöglichkeiten.

## Änderungen für geändert am

Die `Modified At` -Methode, die die am besten geeignete Replikationsmethode ist, verwendet eine `datetime` um neue und/oder aktualisierte Daten zu erkennen. Beachten Sie, dass die `datetime` -Spalte in Tabellen, die diese Methode verwenden, muss indiziert sein und darf keine Nullwerte enthalten.

Wenn Ihre Tabelle keine `datetime` -Spalte können Sie einen Index hinzufügen `modified at` Spalte. Nullwerte sind in einer `modified at` Spalte. Überprüfen Sie, ob die Spalte für jede Zeile gefüllt ist.

Um sicherzustellen, dass `Modified At` -Methode wie gewünscht funktioniert, können Sie keine Zeilen aus der Tabelle löschen. Stattdessen sollten Sie die Zeile als ungültig markieren, indem Sie eine `deleted` in die Tabelle ein. Diese Spalte gibt eine `1` wenn die Zeile ungültig ist und `0` andernfalls. Anschließend können Sie diese Spalte verwenden, um ungültige Zeilen beim Erstellen von Metriken und Berichten herauszufiltern.

## Änderungen für die automatische Erhöhung des Primären Schlüssels

Wenn die Variable `Modified At` -Methode nicht aktiviert werden, ist der Einzelne automatische Inkrementierungs-Primäre Schlüssel die nächste beste Option. Neue Daten werden in Tabellen mit dieser Methode erkannt, indem nach Primärschlüsselwerten gesucht wird, die höher sind als der aktuelle höchste Wert in der Data Warehouse.

Beachten Sie, dass Tabellen, die diese Methode verwenden, eine einzelne Spalte sind, wobei die Ganzzahl automatisch die Primärschlüssel inkrementiert. Um diese Methode in Ihrer Datenbank zu verwenden, nehmen Sie die folgenden Änderungen vor:

* Wenn der Primärschlüssel entweder ein zusammengesetzter Schlüssel oder eine Nicht-Ganzzahl ist, ändern Sie den Primärschlüssel in eine automatisch inkrementierende Ganzzahl
* Wenn der Primärschlüssel eine einzelne Ganzzahlspalte ist, Schlüssel jedoch nicht sequenziell zugewiesen werden können, ändern Sie den Primärschlüssel in automatische Inkrementierung

## Aufbrechen

Durch geringfügige Änderungen an Ihren Tabellen können Sie die schnelleren und effizienteren Methoden für die inkrementelle Replikation nutzen. Ist dies jedoch nicht möglich, können Sie weitere Schritte ausführen, um [Verkürzen der Aktualisierungszeit](../best-practices/reduce-update-cycle-time.md) und [Datenbank optimieren](../best-practices/opt-db-analysis.md).
