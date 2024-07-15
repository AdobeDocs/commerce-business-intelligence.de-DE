---
title: Bericht zur durchschnittlichen Zeit bis zum ersten Kauf
description: Erfahren Sie, wie Sie den Bericht Durchschnittliche Zeit bis Erstkauf verwenden.
exl-id: c18734ce-0ae0-4e84-b9d0-eb2c21a5c3a5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 330832e2668024b00edb2b7c49b92bb042bd004a
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Bericht zur durchschnittlichen Zeit bis zum ersten Kauf

Viele Adobe-Kunden verfügen über eine Metrik und ein Diagramm mit dem Namen `Average time to first purchase`, die die durchschnittliche Zeit zwischen dem Registrierungsdatum einer Benutzergruppe und dem ersten Kaufdatum anzeigt. Die Daten fallen fast unweigerlich nach unten, wenn die Zeit näher an die Gegenwart rückt.

![durchschnittliche Zeit bis zur ersten Bestellung](../../assets/average-time-to-first-order.png)

Dies liegt daran, dass diese neueren Kunden noch nicht die Möglichkeit hatten, Käufe zu generieren, die mehr als einen Monat nach ihrem Beitritt getätigt wurden. Da Benutzer, die noch nie etwas gekauft haben, überhaupt nicht eingeschlossen sind (bis sie einen Kauf tätigen), führt dies zu einem Rückgang des Durchschnitts für neuere Kundengruppen.

Es gibt einige andere Möglichkeiten, diese Metrik zu betrachten, die weniger Verzerrungen verursachen. Sehen Sie sich ein Beispiel an.

## Beispiel: Durchführen einer `cohort`-Analyse von Erstbestellungen

Sie können ein Diagramm in Ihrem `Users`-Dashboard mit dem Namen `Time to first order cohort` haben. Dieser Bericht verwendet die Metrik &quot;`Distinct buyers`&quot;, gruppiert Benutzer nach `cohort` Wochen oder Monaten der Registrierung und zeigt das Verhältnis (zwischen `0` und `1`) der Benutzer an, die in den folgenden Wochen oder Monaten nach der Registrierung einen ersten Kauf getätigt haben.

Die Grafik kann zeigen, dass für Benutzer, die sich im Dezember 2014 registriert haben, `0.56` (oder `56%`) bis zum 2. Monat (z. B. Januar 2015) eine erste Bestellung tätigte.

Diese Kohortenanalyse ist ein guter Indikator für die Benutzeraktivierungsrate im Zeitverlauf. Wenn dieses Diagramm zu einer Abflachung oder Plateau führt und Sie immer noch nicht in der Nähe einer 100%igen Konversion zu Käufern sind, kann es an der Zeit sein, die verbleibenden Benutzer über E-Mail-Kampagnen zu aktivieren.
