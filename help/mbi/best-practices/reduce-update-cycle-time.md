---
title: Verringern der Aktualisierungszyklusdauer
description: Erfahren Sie, wie Sie die Aktualisierungszyklusdauer verkürzen.
exl-id: 0b211e2d-770f-480d-a7fb-8d10e3e7272e
role: Admin, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Verringern der Verarbeitungszeit für den Aktualisierungszyklus

[!DNL Adobe Commerce Intelligence] synchronisiert täglich mit Ihrer Datenbank, um neue Daten zu replizieren, sodass Ihre Dashboards stets die neuesten Informationen anzeigen.

Viele Faktoren können zu einer bereits langen Aktualisierungszeit beitragen. Bestimmte Replikationsmethoden, höhere Wiederaufnahmefrequenzen und die Anzahl der Dashboards und Diagramme sind nur ein paar Mitwirkende. In diesen Themen werden einige Best Practices zur Verkürzung der Aktualisierungszeiten besprochen.

## Verringern der Wiederholungshäufigkeit

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. Beispiel: in einer **Bestellungen** Tabelle gibt es möglicherweise eine Spalte namens **status**. Wenn eine Bestellung ursprünglich in die Datenbank geschrieben wurde, kann die Statusspalte den Wert enthalten `pending`. Die Bestellung wird in Ihrer [Data Warehouse](../data-analyst/data-warehouse-mgr/tour-dwm.md) mit diesem `pending` -Wert.

Die veränderlichen Spalten müssen [auf aktualisierte Werte erneut geprüft werden](../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) über einen bestimmten Zeitraum. Standardmäßig ist [!DNL Commerce Intelligence] Diese Spalten werden bei jeder Aktualisierung erneut überprüft. Wenn jedoch eine große Datenmenge erneut geprüft und repliziert werden muss, kann dies die Aktualisierungszeit beeinträchtigen. Anstatt bei jeder Aktualisierung eine erneute Überprüfung durchzuführen, empfiehlt Adobe, die Wiederholungshäufigkeit auf täglich, wöchentlich oder monatlich festzulegen.

## Inkrementelle Replikationsmethoden verwenden

Wie bereits erwähnt, stehen lange Aktualisierungszeiten in direktem Zusammenhang mit der Menge der Daten, die neu überprüft und repliziert werden müssen. [Inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md) kann die Menge der während des Aktualisierungszyklus verarbeiteten Daten erheblich verringern. Adobe empfiehlt nach Möglichkeit die Verwendung dieser Methoden oder die Änderung Ihrer Datenbank, um eine inkrementelle Methode zu unterstützen.

## Nicht verwendete Diagramme aus Dashboards entfernen

Am Ende des Aktualisierungszyklus [!DNL Commerce Intelligence] führt einen Cache-Vorgang für alle Diagramme aus. Ein Cache speichert Daten, damit zukünftige Informationsanfragen schneller abgeschlossen werden können. In [!DNL Commerce Intelligence]bedeutet dies, dass Dashboards schnell geladen werden, da Diagramme nicht jedes Mal, wenn sie geladen werden, Daten abfragen müssen.

Seit [!DNL Commerce Intelligence] Führt nur Cache-Vorgänge für Diagramme in einem Dashboard aus. Durch das Entfernen nicht verwendeter Diagramme aus Ihren Dashboards wird die Aktualisierungszeit verkürzt. Beachten Sie, dass sich dasselbe Diagramm möglicherweise in mehreren Dashboards befindet. Wenden Sie sich an Ihr Team, um sicherzustellen, dass auch nicht verwendete Diagramme entfernt wurden.

>[!NOTE]
>
>Wenn Sie Diagramme aus Ihrem Dashboard entfernen, wird das Diagramm nicht gelöscht. Sie können [jederzeit wieder hinzufügen](../data-user/dashboards/add-charts-dashboard.md).

## Datenbank für Analysen optimieren

Zusätzlich zur Neubewertung von Wiederholungsfrequenzen, Replikationsmethoden und der Nützlichkeit von Diagrammen können Sie auch [Datenbank für Analyse optimieren](../best-practices/opt-db-analysis.md).

## Aufwischen

Wenn Ihre Aktualisierungszeit auch nach der Implementierung dieser Empfehlungen immer noch langsam scheint, [das Supportteam kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
