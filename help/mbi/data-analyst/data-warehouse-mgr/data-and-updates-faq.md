---
title: Daten und Updates - Informationen
description: Erfahren Sie, wie Sie den Status Ihres Aktualisierungszyklus überprüfen können.
exl-id: a4a2e487-b826-4888-baf0-9d246a8ff153
source-git-commit: 09b6983c3e06a1f18035542dfa3b9de9ac3ceb38
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Daten und Updates - Informationen

* [Warum haben sich meine Daten geändert?](#datachange)
* [Was ist der Unterschied zwischen einer regelmäßigen und erzwungenen Aktualisierung?](#regularforcedupdates)
* [Warum dauert der Aktualisierungszyklus lange?](#updatecycletime)
* [Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist?](#notifyupdate)
* [Warum [!DNL Google ECommerce] Daten, die sich von meiner Datenbank unterscheiden?](#ecommdatabase)
* [Wie kann ich eine Datendiskrepanz beheben?](#datadiscrepancy)

## Warum haben sich meine Daten geändert? {#datachange}

Diagrammwerte können sich im Laufe des Tages ändern, da neue Daten mit Ihrem Data Warehouse synchronisiert werden. Darüber hinaus können sich die Werte für vorhandene Datenspalten aufgrund von [rechecks](../data-warehouse-mgr/cfg-data-rechecks.md). Eine erneute Überprüfung ist ein Prozess, der nach geänderten Werten in Datenspalten sucht, z. B. einem Bestellstatus, der von `open` nach `shipped`.

Es gibt einige verschiedene Möglichkeiten [um den Status Ihres Aktualisierungszyklus zu überprüfen](../../best-practices/check-update-cycle.md), abhängig vom Typ der Benutzerberechtigungen, die Sie haben.

## Was ist der Unterschied zwischen einer regelmäßigen und erzwungenen Aktualisierung? {#regularforcedupdates}

Regelmäßige Aktualisierungen sind **terminiert** Prozesse während erzwungener Aktualisierungen **von Ihnen initiierte manuelle Prozesse**. Wenn Sie Stunden der Abmeldung benötigen - oder einen Zeitraum, in dem [!DNL MBI] Ihre Daten sollten nicht aktualisiert werden. Durch das Erzwingen einer Aktualisierung wird ein Zyklus gestartet, der die Einschränkungen der Blackout-Zeit nicht einhält.

## Warum dauert der Aktualisierungszyklus lange? {#updatecycletime}

Eine Vielzahl von Faktoren kann zu einer bereits langen Aktualisierungszeit beitragen. Bestimmt [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md), [höhere Wiederaufnahmefrequenzen](../data-warehouse-mgr/cfg-data-rechecks.md)und die Anzahl der Dashboards und Diagramme sind nur wenige Mitwirkende. Wir empfehlen [einige Ihrer Einstellungen neu konfigurieren](../../best-practices/reduce-update-cycle-time.md) und [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md) um die Aktualisierungszeiten zu verkürzen.

## Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist? {#notifyupdate}

Absolut! Wenn derzeit eine Aktualisierung ausgeführt wird, finden Sie einen Link auf der `Connections` -Seite, mit der Sie eine E-Mail-Benachrichtigung anfordern können, sobald der Zyklus abgeschlossen ist.

## Warum[!DNL Google ECommerce]Daten, die sich von meiner Datenbank unterscheiden? {#ecommdatabase}

Diskrepanzen zwischen [!DNL Google Analytics] und Ihre Datenbank kann aus verschiedenen Gründen auftreten. Das Tracking, das nicht ordnungsgemäß aktiviert wurde, Benutzer, die eine Inkognito besuchen, und Klick-Ereignisse, die nicht ordnungsgemäß funktionieren, sind nur einige Beispiele. Wenn Ihr Umsatz und Ihre Bestellungen nicht richtig aussehen, [diesen Artikel verwenden](https://support.magento.com/hc/en-us/articles/360016505232) um das Problem zu diagnostizieren.

## Wie kann ich eine Datendiskrepanz beheben? {#datadiscrepancy}

Wir wissen, dass das Erkennen inkonsistenter Daten ein frustrierendes Erlebnis sein kann. Verwenden Sie unsere [Checkliste für Datendiskrepanzen](https://support.magento.com/hc/en-us/articles/360016731271) oder [Tutorial zu Datenexporten](https://support.magento.com/hc/en-us/articles/360016730631) um das Problem zu diagnostizieren. Wenn Sie noch nicht angehalten sind, [Support kontaktieren](../../guide-overview.md).
