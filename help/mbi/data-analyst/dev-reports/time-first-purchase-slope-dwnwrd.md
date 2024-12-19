---
title: Bericht zur durchschnittlichen Zeit bis zum ersten Kauf
description: Erfahren Sie, wie Sie den Bericht „Durchschnittliche Zeit bis zum ersten Kauf“ verwenden.
exl-id: c18734ce-0ae0-4e84-b9d0-eb2c21a5c3a5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 330832e2668024b00edb2b7c49b92bb042bd004a
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Bericht zur durchschnittlichen Zeit bis zum ersten Kauf

Viele Adobe-Kunden verfügen über eine Metrik und ein Diagramm mit dem Namen `Average time to first purchase`, das die durchschnittliche Zeit zwischen dem Registrierungsdatum einer Gruppe von Benutzern und dem ersten Kaufdatum anzeigt. Die Daten neigen sich fast immer nach unten, je näher die Zeit an die Gegenwart heranrückt.

![Durchschnittliche Zeit bis zur ersten Bestellung](../../assets/average-time-to-first-order.png)

Dies liegt daran, dass diese neueren Kundinnen und Kunden noch nicht die Möglichkeit hatten, Käufe zu generieren, die mehr als einen Monat nach ihrem Beitrittsdatum getätigt wurden. Da Benutzende, die noch nie einen Kauf getätigt haben, überhaupt nicht eingeschlossen sind (bis sie einen Kauf tätigen), tendiert dies den Durchschnitt für neuere Kundengruppen nach unten.

Es gibt einige andere potenzielle Möglichkeiten, diese Metrik zu betrachten, die weniger Voreingenommenheit verursachen. Ein Beispiel:

## Beispiel: Durchführen einer `cohort` Analyse der ersten Bestellungen

Möglicherweise haben Sie auf Ihrem `Users`-Dashboard ein Diagramm mit dem Namen `Time to first order cohort`. Dieser Bericht verwendet die `Distinct buyers`, gruppiert Benutzer nach `cohort` Wochen oder Monaten der Registrierung und zeigt das Verhältnis (zwischen `0` und `1`) der Benutzer an, die in den folgenden Wochen oder Monaten nach der Registrierung einen ersten Kauf getätigt haben.

Das Diagramm kann zeigen, dass für Benutzer, die sich im Dezember 2014 registriert haben, `0.56` (oder `56%`) bis Monat 2 eine erste Bestellung aufgegeben haben (z. B. Januar 2015).

Diese Kohortenanalyse ist ein guter Indikator für die Benutzeraktivierungsrate im Zeitverlauf. Wenn dieses Diagramm zu reduzieren oder ein Plateau zu erreichen beginnt und Sie immer noch nicht in der Nähe von 100 % Konversion zu Käufern sind, kann es Zeit sein, die verbleibenden Benutzer über E-Mail-Kampagnen zu aktivieren.
