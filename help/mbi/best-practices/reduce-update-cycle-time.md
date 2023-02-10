---
title: Verringern der Aktualisierungszyklusdauer
description: Erfahren Sie, wie Sie die Aktualisierungszyklusdauer verkürzen.
exl-id: 0b211e2d-770f-480d-a7fb-8d10e3e7272e
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Verringern der Verarbeitungszeit für den Aktualisierungszyklus

[!DNL MBI] synchronisiert täglich mit Ihrer Datenbank, um neue Daten zu replizieren, sodass in Ihren Dashboards immer die neuesten Informationen angezeigt werden.

Eine Vielzahl von Faktoren kann zu einer bereits langen Aktualisierungszeit beitragen. Bestimmte Replikationsmethoden, höhere Wiederaufnahmefrequenzen und die Anzahl der Dashboards und Diagramme sind nur ein paar Mitwirkende. In diesen Themen werden einige Best Practices zur Verkürzung der Aktualisierungszeiten besprochen.

## Verringern der Wiederholungshäufigkeit

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. Beispiel: in einer **Bestellungen** Tabelle gibt es möglicherweise eine Spalte namens **status**. Wenn eine Bestellung ursprünglich in die Datenbank geschrieben wurde, kann die Statusspalte den Wert enthalten `pending`. Die Bestellung wird dann in Ihrer [Data Warehouse](../data-analyst/data-warehouse-mgr/tour-dwm.md) mit diesem `pending` -Wert.

Die veränderlichen Spalten müssen [auf aktualisierte Werte erneut geprüft werden](../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) über einen bestimmten Zeitraum. Standardmäßig [!DNL MBI] Diese Spalten werden bei jeder Aktualisierung erneut überprüft. Wenn jedoch eine große Datenmenge erneut geprüft und repliziert werden muss, kann dies die Aktualisierungszeit beeinträchtigen. Anstatt bei jeder Aktualisierung eine erneute Überprüfung durchzuführen, empfehlen wir, die Häufigkeit der Überprüfung auf täglich, wöchentlich oder monatlich festzulegen.

## Inkrementelle Replikationsmethoden verwenden

Wie bereits erwähnt, stehen lange Aktualisierungszeiten in direktem Zusammenhang mit der Menge der Daten, die neu überprüft und repliziert werden müssen. [Inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md) kann die Menge der während des Aktualisierungszyklus verarbeiteten Daten erheblich verringern. Wenn möglich, empfehlen wir die Verwendung dieser Methoden oder die Durchführung von Änderungen an Ihrer Datenbank, um eine inkrementelle Methode zu unterstützen.

## Nicht verwendete Diagramme aus Dashboards entfernen

Am Ende des Aktualisierungszyklus [!DNL MBI] führt einen Cache-Vorgang für alle Diagramme aus. Ein Cache speichert Daten, damit zukünftige Informationsanfragen schneller abgeschlossen werden können. In [!DNL MBI]bedeutet dies, dass Dashboards schnell geladen werden, da Diagramme nicht jedes Mal, wenn sie geladen werden, Daten abfragen müssen.

Seit [!DNL MBI] Führt nur Cache-Vorgänge für Diagramme in einem Dashboard aus. Wenn Sie nicht verwendete Diagramme aus Ihren Dashboards entfernen, wird die Aktualisierungszeit verkürzt. Beachten Sie, dass sich dasselbe Diagramm möglicherweise in mehreren Dashboards befindet. Wenden Sie sich an Ihr Team, um sicherzustellen, dass auch nicht verwendete Diagramme entfernt wurden.

>[!NOTE]
>
>Wenn Sie Diagramme aus Ihrem Dashboard entfernen, wird das Diagramm nicht gelöscht. Sie können [jederzeit wieder hinzufügen](../data-user/dashboards/add-charts-dashboard.md).

## Datenbank für Analysen optimieren

Zusätzlich zur Neubewertung von Wiederholungsfrequenzen, Replikationsmethoden und der Nützlichkeit von Diagrammen können Sie auch [Datenbank für Analyse optimieren](../best-practices/opt-db-analysis.md).

## Aufbrechen

Wenn Ihre Aktualisierungszeit auch nach der Implementierung dieser Empfehlungen immer noch langsam scheint [Kontakt zu unserem Support-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).
