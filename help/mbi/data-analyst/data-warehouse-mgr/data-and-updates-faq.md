---
title: Informationen zu Daten und Aktualisierungen
description: Erfahren Sie, wie Sie den Status Ihres Aktualisierungszyklus überprüfen.
exl-id: a4a2e487-b826-4888-baf0-9d246a8ff153
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Informationen zu Daten und Aktualisierungen

* [Warum haben sich meine Daten geändert?](#datachange)
* [Was ist der Unterschied zwischen einer regulären und einer erzwungenen Aktualisierung?](#regularforcedupdates)
* [Warum dauert der Aktualisierungszyklus so lange?](#updatecycletime)
* [Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist?](#notifyupdate)
* [Warum  [!DNL Google ECommerce]  sich die Daten von meiner Datenbank?](#ecommdatabase)
* [Wie kann ich eine Datendiskrepanz beheben?](#datadiscrepancy)

## Warum haben sich meine Daten geändert? {#datachange}

Diagrammwerte können sich den ganzen Tag über ändern, da neue Daten mit Ihrer Data Warehouse synchronisiert werden. Außerdem können sich Werte für vorhandene Datenspalten aufgrund von [ ändern](../data-warehouse-mgr/cfg-data-rechecks.md). Eine erneute Prüfung ist ein Prozess, der nach geänderten Werten in Datenspalten sucht, z. B. nach einem Bestellstatus, der von `open` zu `shipped` wechselt.

Es gibt verschiedene Möglichkeiten, [den Status Ihres Aktualisierungszyklus zu überprüfen](../../best-practices/check-update-cycle.md) je nach den Berechtigungseinstellungen des Benutzers.

## Was ist der Unterschied zwischen einer regulären und einer erzwungenen Aktualisierung? {#regularforcedupdates}

Regelmäßige Updates sind **geplante** Prozesse, erzwungene Updates sind **manuelle Prozesse, die von Ihnen initiiert**. Wenn Sie Ausfallzeiten haben (oder einen Zeitraum, in dem [!DNL Commerce Intelligence] Ihre Daten nicht aktualisieren sollten), wird beim Erzwingen einer Aktualisierung ein Zyklus gestartet, der die Einschränkungen der Ausfallzeit nicht berücksichtigt.

## Warum dauert der Aktualisierungszyklus so lange? {#updatecycletime}

Zu einer bereits langen Aktualisierungszeit können zahlreiche Faktoren hinzukommen. Bestimmte [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md), [höhere Häufigkeit der erneuten Überprüfung](../data-warehouse-mgr/cfg-data-rechecks.md) und die Anzahl der Dashboards und Diagramme sind nur einige wenige Beitragende. Adobe empfiehlt [einige Einstellungen neu konfigurieren](../../best-practices/reduce-update-cycle-time.md) und [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md) um Aktualisierungszeiten zu reduzieren.

## Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist? {#notifyupdate}

Wenn eine Aktualisierung ausgeführt wird, gibt es auf der `Connections` einen Link, über den Sie nach Abschluss des Zyklus eine E-Mail-Benachrichtigung anfordern können.

## Warum [!DNL Google ECommerce] sich die Daten von meiner Datenbank? {#ecommdatabase}

Diskrepanzen zwischen [!DNL Google Analytics] und Ihrer Datenbank können aus verschiedenen Gründen auftreten. Tracking wird nicht ordnungsgemäß aktiviert, Benutzer, die inkognito besuchen, und Klickereignisse funktionieren nicht ordnungsgemäß, sind nur einige Beispiele. Wenn Ihre Umsätze und Bestellungen nicht korrekt aussehen, [ Sie (siehe dieses Thema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-google-ecommerce-revenue-discrepancies.html?lang=de) ein Problem diagnostizieren.

## Wie kann ich eine Datendiskrepanz beheben? {#datadiscrepancy}

Adobe weiß, dass es frustrierend sein kann, inkonsistente Daten zu sehen. Versuchen Sie, das Problem mithilfe [ Tutorials ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.html?lang=de)Datendiskrepanz-Checkliste“ oder [Datenexporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html?lang=de) zu diagnostizieren. Wenn Sie immer noch blockiert sind, [ Sie den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).
