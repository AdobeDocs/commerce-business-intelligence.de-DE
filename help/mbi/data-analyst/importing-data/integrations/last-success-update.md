---
title: Ergebnisse zwischen Datenbank und SQL-Editor
description: Erfahren Sie, wie Sie die Ergebnisse zwischen Datenbank und SQL-Editor verstehen.
exl-id: f31f3eef-791a-4984-901e-bc10554031bd
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/pScH-yKW8hbSNZzsJ537CN7rxhcuygaLmCu3fdVaYgk
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
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
source-wordcount: 257
ht-degree: 0%

---

# Datenbankergebnisse im Vergleich zu [!DNL SQL Editor] Ergebnissen

Sie könnten neugierig sein, was das `Last successful update began` auf Ihrer `Integrations`-Seite ist:

![Last_successful_update.png](../../../assets/Last_successful_update.png)

## Grundlegendes zum `timestamp`

Er zeigt die `timestamp` (in der für Ihr Konto festgelegten Zeitzone) des _letzten erfolgreichen Aktualisierungszyklus_ für Ihr Konto an.

- Wenn bei einer der synchronisierten Tabellen während des letzten Aktualisierungszyklus ein Problem aufgetreten ist, wird dieser Zeitstempel *nicht aktualisiert*.
- Daher kann es Fälle geben, in denen Berichte mit neuen Daten aktualisiert wurden, aber die *Letzte erfolgreiche Aktualisierung begann* immer noch nicht abgeschlossen ist.

## Identifizieren des letzten „echten“ Datenpunkts

Der aktuelle Datenpunkt für eine bestimmte Integration wird durch den `Last Data Point Received` Zeitstempel rechts von jeder Integration bestimmt. Dieser Zeitstempel bezieht sich auf den letzten Zeitpunkt, an dem Ihr Data Warehouse erfolgreich Datenpunkte aus dieser Quelle empfangen hat, unabhängig davon, ob es sich um eine Datenbank, eine API oder eine Integration von Drittanbietern handelt.

Um die Aktualität von Daten aus *spezifischen Tabellen* zu überprüfen, empfiehlt Adobe die Erstellung eines [[!DNL SQL] Berichts](../../dev-reports/sql-rpt-bldr.md), der eine `MAX(timestamp)` der wichtigsten Tabelle in Ihrem Konto durchführt. Wenn Sie diesen Zeitstempel mit dem `Last Data Point` vergleichen, wird angezeigt, ob das Problem das gesamte Konto oder eine Teilmenge der Tabellen betraf. Adobe empfiehlt dies für drei bis vier wichtige, häufig verwendete Tabellen.

- Wenn die `MAX(timestamp)` Werte aktueller als `Last Data Point Received` sind, bedeutet dies, dass eine Teilmenge der Tabellen betroffen war, der Aktualisierungszyklus des Kontos insgesamt jedoch stabil ist.
- Wenn die `MAX(timestamp)` Werte gleich oder vor `Last Data Point Received` sind, bedeutet dies, dass der Aktualisierungszyklus des Kontos betroffen war. Senden Sie in [&#x200B; Fall ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).
