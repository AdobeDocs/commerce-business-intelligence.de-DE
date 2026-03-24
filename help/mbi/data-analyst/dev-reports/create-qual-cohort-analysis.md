---
title: Erstellen einer qualitativen Kohortenanalyse
description: Erfahren Sie, was eine qualitative Kohorte ist, warum Sie am Aufbau dieser Analyse interessiert sein könnten und wie Sie sie in Commerce Intelligence erstellen können.
exl-id: 113244e4-409b-4129-b3d4-7a3433539ade
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: https://experienceleague.adobe.com/XOdXVSRzCzVPNWv9N58Ddheo-h5kO-3UZFiAwGDzXzQ
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
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 846
ht-degree: 0%

---

# Erstellen eines `Qualitative Cohort Analysis`

Wissen Sie, wie Ihre [!DNL Google Adwords] Kundensegmente ihren LTV im Vergleich zu den Kunden aus der organischen Suche erweitern? Haben Sie schon einmal daran gedacht, im selben Bericht eine `cohort` Analyse für verschiedene Kundensegmente nebeneinander durchzuführen? Wenn ja, hilft Ihnen ein `qualitative cohort analysis`, diese Fragen zu beantworten.

Dieses Thema geht näher darauf ein, was eine qualitative Kohorte ist, warum Sie möglicherweise am Aufbau dieser Analyse interessiert sind und wie Sie sie in [!DNL Commerce Intelligence] erstellen können.

## Was sind überhaupt `qualitative cohorts`? {#whatare}

`Cohort` Analyse im Allgemeinen kann grob definiert werden als die Analyse von Benutzergruppen, die ähnliche Eigenschaften über ihren Lebenszyklus hinweg aufweisen. So können Sie Verhaltenstrends in verschiedenen Benutzergruppen identifizieren.

Die meisten `cohort` in [!DNL Commerce Intelligence] gruppieren Benutzer nach einem gemeinsamen Datum (z. B. die Gruppe aller Kunden, die ihren ersten Kauf in einem bestimmten Monat getätigt haben). Ein `qualitative cohort` ist etwas Anderes: Es handelt sich um eine Benutzergruppe, die durch ein Merkmal definiert wird, das nicht zeitbasiert ist. Beispiele:

* Die Gruppe aller Benutzer, die von einer Anzeigenkampagne erfasst wurden
* Der Satz aller Benutzer, deren erster Kauf einen Coupon enthielt (oder nicht enthielt)
* Die Gruppe aller Benutzer mit einem bestimmten Alter

## Wie unterscheidet sich das vom normalen `cohort` Builder? {#different}

Die [`Cohort Analysis Builder`](../dev-reports/cohort-rpt-bldr.md) ist für die Gruppierung von Kohorten anhand eines zeitbasierten Merkmals optimiert. Dies eignet sich hervorragend für Analysen, die sich auf ein bestimmtes Segment von Benutzenden konzentrieren (z. B. alle Benutzenden, die über eine Paid-Search-Kampagne erworben wurden). Im `Cohort Analysis Builder` können Sie (1) auf diese bestimmte Benutzergruppe fokussieren und (2) auf ein Datum (wie das Datum der ersten Bestellung) `cohort`.

Wenn Sie jedoch das Kohortenverhalten mehrerer Benutzersegmente im selben Kohortenbericht analysieren möchten (`paid` Suche versus `organic` Suche vs. direkter Traffic, vielleicht?), kann diese erweiterte Analyse im `Report Builder` erstellt werden.

## Welche Informationen sollte ich an den Support senden, um meine Analyse einzurichten? {#support}

Das Erstellen eines `qualitative cohort` in der `Report Builder` beinhaltet, dass das Adobe-Analystenteam einige [erweiterte berechnete Spalten](../data-warehouse-mgr/creating-calculated-columns.md) auf den erforderlichen Tabellen erstellt.

Um diese zu erstellen, reichen Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de) ein (und lesen Sie diesen Artikel!). Hier finden Sie, was Sie wissen müssen:

* Die `metric`, mit der Sie Ihre Kohortenanalyse durchführen möchten, und welche Tabelle verwendet wird (Beispiel: `Revenue`, basierend auf der `orders`).

* Die `user segments`, die Sie definieren möchten, und wo diese Informationen in Ihrer Datenbank vorhanden sind (Beispiel: verschiedene Werte von `User's referral source`, die in der `users`-Tabelle enthalten sind und nach unten in die `orders` verschoben wurden).

* Die `cohort date`, die Ihre Analyse verwenden soll (Beispiel: `User's first order date` Zeitstempel). Dieses Beispiel würde es uns ermöglichen, jedes Segment zu betrachten und `How does a user's revenue grow in the months following their first order date?` zu stellen.

* Die `time interval`, über die die Analyse angezeigt werden soll (Beispiel: `weeks`, `months` oder `quarters` nach der `User's first order date`).

Sobald das Adobe-Analyst-Team auf die oben genannten Fragen antwortet, haben Sie einige neue erweiterte berechnete Spalten, um Ihren Bericht zu erstellen! Folgen Sie dazu den unten stehenden Anweisungen.

## Erstellen der qualitativen Kohortenanalyse {#create}

Zunächst möchten Sie die Metrik, die Sie für die Kohorte interessieren, einmal für jedes `cohort` hinzufügen, das Sie analysieren. In diesem Beispiel möchten Sie kumulative `Revenue` sehen, die in den Monaten nach der ersten Bestellung eines Kunden getätigt wurden, und die nach `User's referral source` segmentiert sind. Das bedeutet, dass Sie für jedes Segment eine `Revenue` Metrik hinzufügen und nach dem spezifischen Segment filtern:

![Animierte Demonstration zur Erstellung einer qualitativen Kohortenanalyse](../../assets/qualcohort1.gif)

Zweitens sollten Sie zwei Änderungen an den Zeitoptionen des Berichts vornehmen:

1. Legen Sie die `time interval` auf `None` fest. Dies liegt daran, dass Sie nach dem Zeitintervall letztendlich als Dimension gruppieren, anstatt die üblichen Zeitoptionen zu verwenden.

1. Legen Sie die `time range` auf das Zeitfenster fest, das der Bericht abdecken soll.

In diesem Beispiel sehen Sie eine `all time` Ansicht von `Revenue`. Danach sollten Sie eine Reihe von Punkten bekommen:

![Animierte Demonstration der Optionen für Kohortengruppierung und Analyse](../../assets/qualcohort2.gif)

Drittens nehmen Sie die Anpassung vor, um die `cohorts` einzurichten. Basierend auf den `cohort date` und `time interval`, die Sie dem Adobe-Analystenteam angegeben haben, haben Sie eine Dimension in Ihrem Konto, die die `cohort` Datierung durchführt. In diesem Beispiel wird diese benutzerdefinierte Dimension `Months between this order and customer's first order date` genannt. Mit dieser Dimension sollten Sie:

* `Group by` der Dimension mit der Option &quot;`group by`&quot;

* Wählen Sie alle Werte der `dimension` aus, an denen Sie interessiert sind

* Wählen Sie mit dem `Show top/bottom option` die X wichtigsten Monate aus, die Sie interessieren, und sortieren Sie nach der `Months between this order and customer's first order date` Dimension

Jetzt können Sie für jede angegebene `cohort` eine Zeile sehen. Sehen Sie sich jetzt das Beispiel an - Sie sehen die von den Benutzern jeder Empfehlungsquelle beigesteuerten `Revenue`, `grouped by` die Anzahl der Monate zwischen ihrer ersten Bestellung und jeder nachfolgenden Bestellung. Im Beispiel wurde auch ein `Cumulative perspective` hinzugefügt, um das `cohorts'` Gesamtwachstum anzuzeigen. Weitere Details finden Sie in der Ergebnistabelle.

Was sagt uns das? Hier ist die spezifische `Paid search` für Empfehlungen im ersten Monat des Kauflebens eines Kunden wertvoll, kann jedoch seinen Kundenstamm nicht mit wiederholten Umsätzen halten. Während `Direct Traffic` mit einem niedrigeren Betrag beginnt, akkumulieren sich die Einnahmen in den folgenden Monaten tatsächlich mit einer ähnlichen Geschwindigkeit.

Egal, wie Sie es drehen: `cohort` Analyse ist ein leistungsstarkes Tool in Ihrer Analyse-Toolbox. Diese Art der Analyse kann zu einigen interessanten Einblicken in Ihr Unternehmen führen, die in herkömmlichen `time-based cohorts` möglicherweise nicht vorhanden sind, sodass Sie bessere datengestützte Entscheidungen treffen können.
