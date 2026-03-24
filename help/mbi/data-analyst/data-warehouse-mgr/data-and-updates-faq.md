---
title: Informationen zu Daten und Aktualisierungen
description: Erfahren Sie, wie Sie den Status Ihres Aktualisierungszyklus überprüfen.
exl-id: a4a2e487-b826-4888-baf0-9d246a8ff153
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/qT3lojSuve8jHgNVKoJCUW82cN2QK497wFX8NVbptWI
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 481
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

Diagrammwerte können sich den ganzen Tag über ändern, da neue Daten mit Ihrer Data Warehouse synchronisiert werden. Außerdem können sich Werte für vorhandene Datenspalten aufgrund von [&#x200B; ändern](../data-warehouse-mgr/cfg-data-rechecks.md). Eine erneute Prüfung ist ein Prozess, der nach geänderten Werten in Datenspalten sucht, z. B. nach einem Bestellstatus, der von `open` zu `shipped` wechselt.

Es gibt verschiedene Möglichkeiten, [den Status Ihres Aktualisierungszyklus zu überprüfen](../../best-practices/check-update-cycle.md) je nach den Berechtigungseinstellungen des Benutzers:

* **[!UICONTROL Read-Only]und [!UICONTROL Standard] Benutzer** - Kann den Mauszeiger über das Symbol oben rechts auf der Seite bewegen, um zu sehen, wann der letzte Datenpunkt abgerufen wurde.
* **[!UICONTROL Admin]Benutzer** - Kann den letzten Datenpunkt und das Statussymbol für Kontointegrationen anzeigen. Navigieren Sie für weitere Details zu **[!UICONTROL Manage Data]** > **[!UICONTROL Integrations]** , um den aktuellen Aktualisierungsstatus und die Uhrzeit der letzten abgeschlossenen Aktualisierung anzuzeigen.
* **API-Methode** - Kann den zuletzt abgeschlossenen Aktualisierungszyklus mithilfe der Aktualisierungszyklus-Status-API abrufen.

Ausführliche Informationen zur Überprüfung des Status Ihres Aktualisierungszyklus finden Sie unter [Überprüfen des Aktualisierungszyklusstatus](../../best-practices/check-update-cycle.md).

## Was ist der Unterschied zwischen einer regulären und einer erzwungenen Aktualisierung? {#regularforcedupdates}

Regelmäßige Updates sind **geplante** Prozesse, erzwungene Updates sind **manuelle Prozesse, die von Ihnen initiiert**. Wenn Sie Ausfallzeiten haben (oder einen Zeitraum, in dem [!DNL Commerce Intelligence] Ihre Daten nicht aktualisieren sollten), wird beim Erzwingen einer Aktualisierung ein Zyklus gestartet, der die Einschränkungen der Ausfallzeit nicht berücksichtigt.

## Warum dauert der Aktualisierungszyklus so lange? {#updatecycletime}

Zu einer bereits langen Aktualisierungszeit können zahlreiche Faktoren hinzukommen. Bestimmte [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md), [höhere Häufigkeit der erneuten Überprüfung](../data-warehouse-mgr/cfg-data-rechecks.md) und die Anzahl der Dashboards und Diagramme sind nur einige wenige Beitragende. Adobe empfiehlt [einige Einstellungen neu konfigurieren](../../best-practices/reduce-update-cycle-time.md) und [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md) um Aktualisierungszeiten zu reduzieren.

## Kann ich benachrichtigt werden, wenn ein Aktualisierungszyklus abgeschlossen ist? {#notifyupdate}

Wenn eine Aktualisierung ausgeführt wird, gibt es auf der Seite **[!UICONTROL Manage Data]** > **[!UICONTROL Integrations]** einen Link, über den Sie nach Abschluss des Zyklus eine E-Mail-Benachrichtigung anfordern können. Wenn keine Aktualisierung ausgeführt wird, wird stattdessen ein Link angezeigt, um den Start einer Aktualisierung zu erzwingen.

## Warum [!DNL Google ECommerce] sich die Daten von meiner Datenbank? {#ecommdatabase}

Diskrepanzen zwischen [!DNL Google Analytics] und Ihrer Datenbank können aus verschiedenen Gründen auftreten. Tracking wird nicht ordnungsgemäß aktiviert, Benutzer, die inkognito besuchen, und Klickereignisse funktionieren nicht ordnungsgemäß, sind nur einige Beispiele. Wenn Ihre Umsätze und Bestellungen nicht korrekt aussehen, [&#x200B; Sie (siehe dieses Thema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-google-ecommerce-revenue-discrepancies.html) ein Problem diagnostizieren.

## Wie kann ich eine Datendiskrepanz beheben? {#datadiscrepancy}

Adobe weiß, dass es frustrierend sein kann, inkonsistente Daten zu sehen. Versuchen Sie, das Problem mithilfe [&#x200B; Tutorials &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.html)Datendiskrepanz-Checkliste“ oder [Datenexporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html) zu diagnostizieren. Wenn Sie immer noch blockiert sind, [&#x200B; Sie den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
