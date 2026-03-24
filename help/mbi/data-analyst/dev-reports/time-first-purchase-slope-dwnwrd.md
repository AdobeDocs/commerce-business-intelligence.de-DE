---
title: Bericht zur durchschnittlichen Zeit bis zum ersten Kauf
description: Erfahren Sie, wie Sie den Bericht „Durchschnittliche Zeit bis zum ersten Kauf“ verwenden.
exl-id: c18734ce-0ae0-4e84-b9d0-eb2c21a5c3a5
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: https://experienceleague.adobe.com/LWbb4E4IMPQd-hUpsylSGt4lgrrvYI1VUhmovjvcfu4
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 258
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
