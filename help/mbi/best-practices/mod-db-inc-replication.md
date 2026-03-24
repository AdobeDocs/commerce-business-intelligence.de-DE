---
title: Ändern der Datenbank zur Unterstützung der inkrementellen Replikation
description: Erfahren Sie, wie Sie Ihre Datenbank ändern, um die inkrementelle Replikation zu unterstützen.
exl-id: c9a38892-6096-4eb5-8a53-35b8b7b083dc
role: Admin, Developer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
TQID: https://experienceleague.adobe.com/VH5mhfRJteAxiQAmh14TzhnAqym65X6SFRMGuSuEvwM
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 334
ht-degree: 0%

---

# Unterstützung für inkrementelle Replikation

Wenn Ihre Tabellen derzeit keine inkrementelle Replikation zulassen, finden Sie in den folgenden Empfehlungen mögliche Lösungen.

## Änderungen für Geändert um

Die `Modified At` Methode, die sich am besten für die Replikation eignet, verwendet eine `datetime` Spalte, um neue und/oder aktualisierte Daten zu erkennen. Denken Sie daran, dass die Spalte `datetime` in Tabellen, die diese Methode verwenden, indiziert sein muss und zu keinem Zeitpunkt Nullwerte enthalten darf.

Wenn Ihre Tabelle keine `datetime` Spalte hat, können Sie eine `modified at` hinzufügen. Nullwerte sind in einer `modified at` Spalte nicht zulässig. Vergewissern Sie sich, dass die Spalte für jede Zeile ausgefüllt ist.

Um sicherzustellen, dass die `Modified At` Methode wie vorgesehen funktioniert, können Sie keine Zeilen aus der Tabelle löschen. Stattdessen sollten Sie die Zeile als ungültig markieren, indem Sie der Tabelle eine `deleted` Spalte hinzufügen. Diese Spalte gibt eine `1` zurück, wenn die Zeile ungültig ist, andernfalls `0`. Sie können diese Spalte dann verwenden, um ungültige Zeilen herauszufiltern, wenn Sie Metriken und Berichte erstellen.

## Änderungen für Primären Einzelschlüssel mit automatischer Erhöhung

Wenn die `Modified At` nicht aktiviert werden kann, ist die Option Einzel Primärer Schlüssel automatisch inkrementieren die nächstbeste Option. Neue Daten werden bei Verwendung dieser Methode in Tabellen erkannt, indem nach Primärschlüsselwerten gesucht wird, die höher sind als der aktuell höchste Wert in der Data Warehouse.

Denken Sie daran, dass Tabellen, die diese Methode verwenden, Einzelspalten sind, wobei die Primärschlüssel automatisch ganzzahlig inkrementiert werden. Um diese Methode in Ihrer Datenbank zu verwenden, nehmen Sie die folgenden Änderungen vor:

* Wenn der Primärschlüssel entweder ein zusammengesetzter Schlüssel oder eine Nicht-Ganzzahl ist, ändern Sie den Primärschlüssel in eine automatisch inkrementierende Ganzzahl
* Wenn der Primärschlüssel eine einzelne ganzzahlige Spalte ist, Schlüssel jedoch nicht sequenziell zugewiesen werden können, ändern Sie den Primärschlüssel in eine automatische Inkrementierung

## Verpackung

Durch kleinere Änderungen an Ihren Tabellen können Sie die schnelleren, effizienteren inkrementellen Replikationsmethoden nutzen. Wenn dies jedoch nicht möglich ist, können Sie weitere Schritte ausführen, um [die Aktualisierungszeit zu reduzieren](../best-practices/reduce-update-cycle-time.md) und [Ihre Datenbank zu optimieren](../best-practices/opt-db-analysis.md).
