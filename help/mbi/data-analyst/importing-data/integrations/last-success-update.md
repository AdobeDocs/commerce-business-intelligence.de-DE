---
title: Ergebnisse zwischen Datenbank und SQL-Editor
description: Erfahren Sie mehr über die Ergebnisse zwischen Datenbank und SQL-Editor.
exl-id: f31f3eef-791a-4984-901e-bc10554031bd
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Datenbankergebnisse vs. [!DNL SQL Editor] Ergebnisse

Vielleicht möchten Sie wissen, was sich das Feld `Last successful update began` in Ihrer `Integrations`-Seite befindet:

![Last_success_update.png](../../../assets/Last_successful_update.png)

## Grundlegendes zum Feld `timestamp`

Er zeigt den Start `timestamp` (in der in Ihrem Konto festgelegten Zeitzone) des _letzten erfolgreichen Aktualisierungszyklus_ für Ihr Konto an.

- Wenn bei einer der synchronisierten Tabellen während des letzten Aktualisierungszyklus ein Problem aufgetreten ist, ist dieser Zeitstempel *nicht aktualisiert*.
- Daher kann es vorkommen, dass Berichte mit neuen Daten aktualisiert wurden, aber die *letzte erfolgreiche Aktualisierung begonnen hat* immer noch hinkt.

## Identifizieren des letzten &quot;echten&quot;Datenpunkts

Der neueste Datenpunkt für eine bestimmte Integration wird durch den Zeitstempel `Last Data Point Received` rechts neben jeder Integration bestimmt. Dieser Zeitstempel bezieht sich auf den letzten Punkt, an dem Ihr Data Warehouse erfolgreich Datenpunkte von dieser Quelle erhalten hat, unabhängig davon, ob es sich um eine Datenbank-, API- oder Drittanbieterintegration handelt.

Um die Aktualisierung von Daten aus *bestimmten Tabellen* zu überprüfen, empfiehlt Adobe, einen schnellen [[!DNL SQL] Bericht](../../dev-reports/sql-rpt-bldr.md) zu erstellen, der eine `MAX(timestamp)` für die wichtigste Tabelle in Ihrem Konto ausführt. Wenn Sie diesen Zeitstempel mit dem Wert `Last Data Point` vergleichen, wird angegeben, ob das Problem das gesamte Konto oder eine Untergruppe der Tabellen betraf. Adobe empfiehlt dies für drei bis vier wichtige, häufig verwendete Tabellen.

- Wenn die `MAX(timestamp)` -Werte aktueller sind als `Last Data Point Received`, bedeutet dies, dass eine Untergruppe der Tabellen betroffen war, der Aktualisierungszyklus des Gesamtkontos jedoch stabil ist.
- Wenn die `MAX(timestamp)` -Werte gleich oder vor `Last Data Point Received` sind, bedeutet dies, dass der Aktualisierungszyklus des Kontos betroffen war. In diesem Fall senden [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
