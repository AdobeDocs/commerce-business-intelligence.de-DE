---
title: Daten und Updates - Informationen
description: Erfahren Sie, wie Sie den Status Ihres Aktualisierungszyklus überprüfen können.
exl-id: a4a2e487-b826-4888-baf0-9d246a8ff153
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Daten und Updates - Informationen

* [Warum haben sich meine Daten geändert?](#datachange)
* [Was ist der Unterschied zwischen einer regelmäßigen und erzwungenen Aktualisierung?](#regularforcedupdates)
* [Warum dauert der Aktualisierungszyklus lange?](#updatecycletime)
* [Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist?](#notifyupdate)
* [Warum ist [!DNL Google ECommerce] andere Daten als meine Datenbank?](#ecommdatabase)
* [Wie kann ich eine Datendiskrepanz beheben?](#datadiscrepancy)

## Warum haben sich meine Daten geändert? {#datachange}

Diagrammwerte können sich im Laufe des Tages ändern, da neue Daten mit Ihrer Data Warehouse synchronisiert werden. Außerdem können sich die Werte für vorhandene Datenspalten aufgrund von [rechecks](../data-warehouse-mgr/cfg-data-rechecks.md). Eine erneute Überprüfung ist ein Prozess, der nach geänderten Werten in Datenspalten sucht, z. B. einem Bestellstatus, der von `open` nach `shipped`.

Es gibt einige verschiedene Möglichkeiten [um den Status Ihres Aktualisierungszyklus zu überprüfen](../../best-practices/check-update-cycle.md), abhängig von den Berechtigungseinstellungen des Benutzers.

## Was ist der Unterschied zwischen einer regelmäßigen und erzwungenen Aktualisierung? {#regularforcedupdates}

Regelmäßige Aktualisierungen sind **terminiert** Prozesse während erzwungener Aktualisierungen **von Ihnen initiierte manuelle Prozesse**. Wenn Sie Stunden mit der Abmeldung (oder einen Zeitraum, in dem [!DNL Commerce Intelligence] Ihre Daten sollten nicht aktualisiert werden), erzwingen Sie eine Aktualisierung einen Zyklus, der die Einschränkungen der Blackout-Zeit nicht einhält.

## Warum dauert der Aktualisierungszyklus lange? {#updatecycletime}

Eine bereits lange Aktualisierungszeit kann durch zahlreiche Faktoren verlängert werden. Bestimmt [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md), [höhere Wiederaufnahmefrequenzen](../data-warehouse-mgr/cfg-data-rechecks.md)und die Anzahl der Dashboards und Diagramme sind nur wenige Mitwirkende. Adobe empfiehlt [einige Ihrer Einstellungen neu konfigurieren](../../best-practices/reduce-update-cycle-time.md) und [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md) um die Aktualisierungszeiten zu verkürzen.

## Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist? {#notifyupdate}

Wenn eine Aktualisierung ausgeführt wird, befindet sich ein Link auf der `Connections` -Seite, mit der Sie eine E-Mail-Benachrichtigung anfordern können, sobald der Zyklus abgeschlossen ist.

## Warum ist[!DNL Google ECommerce]andere Daten als meine Datenbank? {#ecommdatabase}

Unterschiede zwischen [!DNL Google Analytics] und Ihre Datenbank kann aus verschiedenen Gründen auftreten. Das Tracking, das nicht ordnungsgemäß aktiviert wurde, Benutzer, die eine Inkognito besuchen, und Klick-Ereignisse, die nicht ordnungsgemäß funktionieren, sind nur einige Beispiele. Wenn Ihr Umsatz und Ihre Bestellungen nicht richtig aussehen, [siehe dieses Thema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-google-ecommerce-revenue-discrepancies.html) um ein Problem zu diagnostizieren.

## Wie kann ich eine Datendiskrepanz beheben? {#datadiscrepancy}

Adobe weiß, dass das Erkennen inkonsistenter Daten ein frustrierendes Erlebnis sein kann. Verwenden Sie die [Checkliste für Datendiskrepanzen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.html) oder [Tutorial zu Datenexporten](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html) um das Problem zu diagnostizieren. Wenn Sie noch nicht angehalten sind, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
