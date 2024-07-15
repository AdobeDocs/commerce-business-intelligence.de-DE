---
title: Verringern der Aktualisierungszyklusdauer
description: Erfahren Sie, wie Sie die Aktualisierungszyklusdauer verkürzen.
exl-id: 0b211e2d-770f-480d-a7fb-8d10e3e7272e
role: Admin, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Verringern der Verarbeitungszeit für den Aktualisierungszyklus

[!DNL Adobe Commerce Intelligence] wird den ganzen Tag mit Ihrer Datenbank synchronisiert, um neue Daten zu replizieren, sodass in Ihren Dashboards immer die neuesten Informationen angezeigt werden.

Viele Faktoren können zu einer bereits langen Aktualisierungszeit beitragen. Bestimmte Replikationsmethoden, höhere Wiederaufnahmefrequenzen und die Anzahl der Dashboards und Diagramme sind nur ein paar Mitwirkende. In diesen Themen werden einige Best Practices zur Verkürzung der Aktualisierungszeiten besprochen.

## Verringern der Wiederholungshäufigkeit

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. In einer Tabelle mit **Bestellungen** kann es beispielsweise eine Spalte mit dem Namen **Status** geben. Wenn eine Bestellung zum ersten Mal in die Datenbank geschrieben wird, kann die Statusspalte den Wert `pending` enthalten. Die Reihenfolge wird in Ihrem [Data Warehouse](../data-analyst/data-warehouse-mgr/tour-dwm.md) mit diesem `pending` -Wert repliziert.

Die veränderlichen Spalten müssen [erneut auf aktualisierte Werte überprüft werden](../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md). Standardmäßig überprüft [!DNL Commerce Intelligence] diese Spalten bei jeder Aktualisierung erneut. Wenn jedoch eine große Datenmenge erneut geprüft und repliziert werden muss, kann dies die Aktualisierungszeit negativ beeinflussen. Anstatt bei jeder Aktualisierung eine erneute Überprüfung durchzuführen, empfiehlt Adobe, die Wiederholungshäufigkeit auf täglich, wöchentlich oder monatlich festzulegen.

## Inkrementelle Replikationsmethoden verwenden

Wie bereits erwähnt, stehen lange Aktualisierungszeiten in direktem Zusammenhang mit der Menge der Daten, die neu überprüft und repliziert werden müssen. [Inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md) können die Menge der während des Aktualisierungszyklus verarbeiteten Daten erheblich reduzieren. Adobe empfiehlt nach Möglichkeit die Verwendung dieser Methoden oder die Änderung Ihrer Datenbank, um eine inkrementelle Methode zu unterstützen.

## Nicht verwendete Diagramme aus Dashboards entfernen

Am Ende des Aktualisierungszyklus führt [!DNL Commerce Intelligence] einen Cache-Vorgang für alle Diagramme aus. Ein Cache speichert Daten, damit zukünftige Informationsanfragen schneller abgeschlossen werden können. In [!DNL Commerce Intelligence] bedeutet dies, dass Dashboards schnell geladen werden, da Diagramme nicht jedes Mal Daten abfragen müssen, wenn sie geladen werden.

Da [!DNL Commerce Intelligence] nur Cache-Vorgänge für Diagramme in einem Dashboard ausführt, verkürzt das Entfernen nicht verwendeter Diagramme aus Ihren Dashboards die Aktualisierungszeit. Beachten Sie, dass sich dasselbe Diagramm möglicherweise in mehreren Dashboards befindet. Wenden Sie sich an Ihr Team, um sicherzustellen, dass auch nicht verwendete Diagramme entfernt wurden.

>[!NOTE]
>
>Wenn Sie Diagramme aus Ihrem Dashboard entfernen, wird das Diagramm nicht gelöscht. Sie können [ihn jederzeit wieder hinzufügen](../data-user/dashboards/add-charts-dashboard.md).

## Datenbank für Analysen optimieren

Zusätzlich zur Neubewertung der Wiederholungsfrequenzen, der Replikationsmethoden und der Nützlichkeit der Grafik können Sie auch [Ihre Datenbank für die Analyse optimieren](../best-practices/opt-db-analysis.md).

## Aufwischen

Wenn die Aktualisierungszeit auch nach der Implementierung dieser Empfehlungen immer noch langsam scheint, kontaktieren Sie [das Supportteam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
