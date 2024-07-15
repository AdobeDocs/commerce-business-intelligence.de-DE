---
title: Daten und Updates - Informationen
description: Erfahren Sie, wie Sie den Status Ihres Aktualisierungszyklus überprüfen können.
exl-id: a4a2e487-b826-4888-baf0-9d246a8ff153
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Daten und Updates - Informationen

* [Warum haben sich meine Daten geändert?](#datachange)
* [Was ist der Unterschied zwischen einer regelmäßigen und erzwungenen Aktualisierung?](#regularforcedupdates)
* [Warum dauert der Aktualisierungszyklus lange?](#updatecycletime)
* [Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist?](#notifyupdate)
* [Warum unterscheiden sich [!DNL Google ECommerce] Daten von meiner Datenbank?](#ecommdatabase)
* [Wie kann ich eine Datendiskrepanz beheben?](#datadiscrepancy)

## Warum haben sich meine Daten geändert? {#datachange}

Diagrammwerte können sich im Laufe des Tages ändern, da neue Daten mit Ihrer Data Warehouse synchronisiert werden. Außerdem können sich die Werte für vorhandene Datenspalten aufgrund von [rechecks](../data-warehouse-mgr/cfg-data-rechecks.md) ändern. Eine erneute Überprüfung ist ein Prozess, der nach geänderten Werten in Datenspalten sucht, z. B. einem Bestellstatus, der von `open` zu `shipped` wechselt.

Je nach den Berechtigungseinstellungen des Benutzers gibt es verschiedene Möglichkeiten, den Status Ihres Aktualisierungszyklus zu überprüfen.](../../best-practices/check-update-cycle.md)[

## Was ist der Unterschied zwischen einer regelmäßigen und erzwungenen Aktualisierung? {#regularforcedupdates}

Regelmäßige Aktualisierungen sind **geplante** Prozesse, während erzwungene Aktualisierungen **manuelle Prozesse sind, die von Ihnen initiiert wurden**. Wenn Sie Blackout-Stunden haben (oder einen Zeitraum, in dem [!DNL Commerce Intelligence] Ihre Daten nicht aktualisieren soll), wird beim Erzwingen einer Aktualisierung ein Zyklus gestartet, der die Einschränkungen der Blackout-Zeit nicht einhält.

## Warum dauert der Aktualisierungszyklus lange? {#updatecycletime}

Eine bereits lange Aktualisierungszeit kann durch zahlreiche Faktoren verlängert werden. Bestimmte [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md), [ höhere Wiederholungsfrequenzen](../data-warehouse-mgr/cfg-data-rechecks.md) und die Anzahl der Dashboards und Diagramme sind nur einige wenige Mitwirkende. Adobe empfiehlt [die Neukonfiguration einiger Ihrer Einstellungen](../../best-practices/reduce-update-cycle-time.md) und [die Optimierung Ihrer Datenbank für Analysen](../../best-practices/opt-db-analysis.md), um die Aktualisierungszeiten zu verkürzen.

## Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist? {#notifyupdate}

Wenn eine Aktualisierung ausgeführt wird, gibt es auf der Seite &quot;`Connections`&quot;einen Link, über den Sie eine E-Mail-Benachrichtigung anfordern können, sobald der Zyklus abgeschlossen ist.

## Warum unterscheiden sich[!DNL Google ECommerce]Daten von meiner Datenbank? {#ecommdatabase}

Diskrepanzen zwischen [!DNL Google Analytics] und Ihrer Datenbank können aus verschiedenen Gründen auftreten. Das Tracking, das nicht ordnungsgemäß aktiviert wurde, Benutzer, die eine Inkognito besuchen, und Klick-Ereignisse, die nicht ordnungsgemäß funktionieren, sind nur einige Beispiele. Wenn Ihr Umsatz und Ihre Bestellungen nicht richtig aussehen, finden Sie in diesem Thema ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-google-ecommerce-revenue-discrepancies.html) Informationen zur Diagnose eines Problems.[

## Wie kann ich eine Datendiskrepanz beheben? {#datadiscrepancy}

Adobe weiß, dass das Erkennen inkonsistenter Daten ein frustrierendes Erlebnis sein kann. Versuchen Sie, das Problem mithilfe der Checkliste für Datendiskrepanzen ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.html) oder des Tutorials [Datenexporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html) zu diagnostizieren. [ Wenn Sie noch nicht angehalten sind, kontaktieren Sie [den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
