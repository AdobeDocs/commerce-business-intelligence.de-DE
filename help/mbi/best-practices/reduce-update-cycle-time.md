---
title: Verkürzen des Aktualisierungszyklus
description: Erfahren Sie, wie Sie die Zykluszeit für Aktualisierungen reduzieren können.
exl-id: 0b211e2d-770f-480d-a7fb-8d10e3e7272e
role: Admin, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Verkürzen der Verarbeitungszeit für den Aktualisierungszyklus

[!DNL Adobe Commerce Intelligence] synchronisiert den ganzen Tag lang mit Ihrer Datenbank, um neue Daten zu replizieren, sodass Ihre Dashboards immer die neuesten Informationen anzeigen.

Zu einer bereits langen Aktualisierungszeit können viele Faktoren hinzukommen. Bestimmte Replikationsmethoden, höhere Häufigkeit der erneuten Prüfungen und die Anzahl der Dashboards und Diagramme sind nur einige wenige Faktoren. In diesem Abschnitt werden einige Best Practices erläutert, mit denen Sie die Aktualisierungszeit verkürzen können.

## Häufigkeit der erneuten Prüfung verringern

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. Beispiel: In einer Tabelle **Bestellungen** kann es eine Spalte namens **Status** geben. Wenn eine Bestellung erstmals in die Datenbank geschrieben wird, kann die Statusspalte den Wert `pending` enthalten. Die Bestellung wird in Ihrer [Data Warehouse](../data-analyst/data-warehouse-mgr/tour-dwm.md) mit diesem `pending` Wert repliziert.

Änderbare Spalten müssen im [ auf aktualisierte Werte ](../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) werden. Standardmäßig überprüft [!DNL Commerce Intelligence] diese Spalten bei jeder Aktualisierung neu. Wenn jedoch eine große Datenmenge erneut überprüft und repliziert werden muss, kann dies negative Auswirkungen auf die Aktualisierungszeit haben. Anstatt während jeder Aktualisierung erneute Prüfungen durchzuführen, empfiehlt Adobe, die Häufigkeit der erneuten Prüfungen auf täglich, wöchentlich oder monatlich festzulegen.

## Verwenden von inkrementellen Replikationsmethoden

Wie bereits erwähnt, hängen lange Aktualisierungszeiten direkt damit zusammen, wie viele Daten erneut überprüft und repliziert werden müssen. [Inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md) können die Menge der während des Aktualisierungszyklus verarbeiteten Daten erheblich reduzieren. Wenn möglich, empfiehlt Adobe die Verwendung dieser Methoden oder die Änderung Ihrer Datenbank, um eine inkrementelle Methode zu unterstützen.

## Entfernen nicht verwendeter Diagramme aus Dashboards

Am Ende des Aktualisierungszyklus führt [!DNL Commerce Intelligence] einen Cache-Vorgang für alle Diagramme durch. Ein Cache speichert Daten, damit zukünftige Informationsanfragen schneller erledigt werden können. [!DNL Commerce Intelligence] bedeutet dies, dass Dashboards schnell geladen werden, da Diagramme nicht bei jedem Laden Daten abfragen müssen.

Da [!DNL Commerce Intelligence] nur Cache-Vorgänge für Diagramme ausführt, die in einem Dashboard gefunden wurden, reduziert das Entfernen nicht verwendeter Diagramme aus Ihren Dashboards die Aktualisierungszeit. Denken Sie daran, dass dasselbe Diagramm in mehreren Dashboards angezeigt werden kann. Wenden Sie sich an Ihr Team, um sicherzustellen, dass auch nicht verwendete Diagramme entfernt wurden.

>[!NOTE]
>
>Beim Entfernen von Diagrammen aus dem Dashboard wird das Diagramm nicht gelöscht. Sie können [jederzeit wieder hinzufügen](../data-user/dashboards/add-charts-dashboard.md).

## Datenbank für Analysen optimieren

Neben der Neubewertung der Häufigkeit der erneuten Prüfungen, der Replikationsmethoden und der Nützlichkeit des Diagramms können Sie auch [Ihre Datenbank für Analysen optimieren](../best-practices/opt-db-analysis.md).

## Verpackung

Wenn Ihre Aktualisierungszeit auch nach der Implementierung dieser Empfehlungen immer noch langsam zu sein scheint, [wenden Sie sich an das Support-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).
