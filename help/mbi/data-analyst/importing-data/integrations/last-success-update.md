---
title: Grundlegendes zu Ergebnissen zwischen Datenbank und SQL-Editor
description: Erfahren Sie mehr über die Ergebnisse zwischen Datenbank und SQL-Editor.
exl-id: f31f3eef-791a-4984-901e-bc10554031bd
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Datenbankergebnisse vs. [!DNL SQL Editor] Ergebnisse

Sie können neugierig sein, was die `Last successful update began` -Feld in Ihrer `Integrations` Seite:

![Last_success_update.png](../../../assets/Last_successful_update.png)

## Die `timestamp` field

Er zeigt den Start an `timestamp` (in der in Ihrem Konto festgelegten Zeitzone) der _Letzter erfolgreicher Aktualisierungszyklus_ auf Ihrem Konto.

- Wenn bei einer der synchronisierten Tabellen während des letzten Aktualisierungszyklus ein Problem aufgetreten ist, wird dieser Zeitstempel *nicht aktualisiert*.
- Es kann daher vorkommen, dass Berichte mit neuen Daten aktualisiert wurden, aber die *Letzte erfolgreiche Aktualisierung gestartet* hinkt noch hinterher.

## Identifizieren des letzten &quot;echten&quot;Datenpunkts

Der neueste Datenpunkt für eine bestimmte Integration wird durch die Variable `Last Data Point Received` Zeitstempel rechts neben jeder Integration. Dieser Zeitstempel bezieht sich auf den letzten Punkt, an dem Ihre Data Warehouse erfolgreich Datenpunkte von dieser Quelle erhalten hat, unabhängig davon, ob es sich um eine Datenbank-, API- oder Drittanbieterintegration handelt.

So überprüfen Sie die Aktualisierung von Daten aus *Spezifische Tabellen* empfiehlt Adobe, eine schnelle [[!DNL SQL] Bericht](../../dev-reports/sql-rpt-bldr.md) , die eine `MAX(timestamp)` auf der wichtigsten Tabelle Ihres Kontos. Vergleich dieses Zeitstempels mit dem `Last Data Point` gibt an, ob das Problem das gesamte Konto oder eine Untergruppe der Tabellen beeinflusst hat. Adobe empfiehlt dies für drei bis vier wichtige, häufig verwendete Tabellen.

- Wenn die Variable `MAX(timestamp)` Werte, die aktueller sind als `Last Data Point Received`bedeutet dies, dass eine Teilmenge der Tabellen betroffen war, der Aktualisierungszyklus des Gesamtkontos jedoch stabil ist.
- Wenn die Variable `MAX(timestamp)` Werte sind gleich oder bevor `Last Data Point Received`bedeutet dies, dass der Aktualisierungszyklus des Kontos betroffen war. In diesem Fall [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
