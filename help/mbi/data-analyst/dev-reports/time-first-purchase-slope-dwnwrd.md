---
title: Bericht zur durchschnittlichen Zeit bis zum ersten Kauf
description: Erfahren Sie, wie Sie den Bericht Durchschnittliche Zeit bis Erstkauf verwenden.
exl-id: c18734ce-0ae0-4e84-b9d0-eb2c21a5c3a5
source-git-commit: 8de036e2717aedef95a8bb908898fd9b9bc9c3fa
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Bericht zur durchschnittlichen Zeit bis zum ersten Kauf

Viele Adobe-Kunden haben eine Metrik und ein Diagramm mit dem Namen `Average time to first purchase`, die die durchschnittliche Zeit zwischen dem Registrierungsdatum einer Benutzergruppe und dem ersten Kaufdatum anzeigt. Die Daten fallen fast unweigerlich nach unten, wenn die Zeit näher an die Gegenwart rückt.

![durchschnittliche Zeit bis zur ersten Bestellung](../../assets/average-time-to-first-order.png)

Dies liegt daran, dass diese neueren Kunden noch nicht die Möglichkeit hatten, Käufe zu generieren, die mehr als einen Monat nach ihrem Beitritt getätigt wurden. Da Benutzer, die noch nie etwas gekauft haben, überhaupt nicht eingeschlossen sind (bis sie einen Kauf tätigen), führt dies zu einem Rückgang des Durchschnitts für neuere Kundengruppen.

Es gibt einige andere Möglichkeiten, diese Metrik zu betrachten, die weniger Verzerrungen verursachen. Sehen Sie sich ein Beispiel an.

## Beispiel: Führen Sie eine `cohort` Analyse der Erstbestellungen

Möglicherweise haben Sie ein Diagramm auf Ihrem `Users` Dashboard namens `Time to first order cohort`. Dieser Bericht verwendet die `Distinct buyers` Metrik, gruppiert Benutzer nach `cohort` Wochen oder Monate der Registrierung und zeigt das Verhältnis (zwischen `0` und `1`) von Benutzern, die in den folgenden Wochen oder Monaten nach der Registrierung zum ersten Mal einen Kauf getätigt haben.

Die Grafik kann zeigen, dass für die im Dezember 2014 registrierten Benutzer `0.56` (oder `56%`) eine erste Bestellung nach Monat 2 (z. B. Januar 2015).

Diese Kohortenanalyse ist ein guter Indikator für die Benutzeraktivierungsrate im Zeitverlauf. Wenn dieses Diagramm zu einer Abflachung oder Plateau führt und Sie immer noch nicht in der Nähe einer 100%igen Konversion zu Käufern sind, kann es an der Zeit sein, die verbleibenden Benutzer über E-Mail-Kampagnen zu aktivieren.
