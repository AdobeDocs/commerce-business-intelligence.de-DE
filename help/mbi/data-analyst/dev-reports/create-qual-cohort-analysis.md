---
title: Erstellen einer qualitativen Kohortenanalyse
description: Erfahren Sie, was eine qualitative Kohorte ist, warum Sie an der Erstellung dieser Analyse interessiert sein könnten und wie Sie sie erstellen können in [!DNL MBI].
exl-id: 113244e4-409b-4129-b3d4-7a3433539ade
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Erstellen Sie eine `Qualitative Cohort Analysis`

Weißt du, wie deine [!DNL Adwords]-erworbene Kundensegmente bauen ihr LTV-Angebot im Vergleich zu den Kunden aus der kostenlosen Suche aus. Haben Sie schon einmal daran gedacht, eine `cohort` Analyse verschiedener Kundensegmente nebeneinander im selben Bericht? Wenn ja, wird eine `qualitative cohort analysis` hilft Ihnen bei der Beantwortung dieser Fragen.

In diesem Artikel erfahren Sie, was eine qualitative Kohorte ist, warum Sie an der Erstellung dieser Analyse interessiert sein könnten und wie Sie sie erstellen können in [!DNL MBI].

## Was ist `qualitative cohorts`Wie auch immer? {#whatare}

`Cohort` Analyse im Allgemeinen kann als Analyse von Benutzergruppen mit ähnlichen Merkmalen über ihre Lebenszyklen hinweg definiert werden. Damit können Sie Verhaltenstrends über verschiedene Benutzergruppen hinweg identifizieren.

Siehe [Kohortenanalyse](https://www.cohortanalysis.com/).

Am meisten `cohort` Analysen in [!DNL MBI] Benutzer nach einem gemeinsamen Datum gruppieren (z. B. die Gruppe aller Kunden, die in einem bestimmten Monat ihren ersten Kauf getätigt haben). A `qualitative cohort` unterscheidet sich etwas: Es handelt sich um eine Benutzergruppe, die durch ein nicht zeitbasiertes Merkmal definiert wird. Zu den Beispielen gehören:

* Die Gruppe aller Benutzer, die über eine Werbekampagne erworben wurden
* Die Gruppe aller Benutzer, deren erster Kauf einen Coupon enthielt (oder nicht)
* Die Gruppe aller Benutzer eines bestimmten Alters

## Worin unterscheidet sich das vom normalen `cohort` Builder? {#different}

Die [`Cohort Analysis Builder`](../dev-reports/cohort-rpt-bldr.md) ist für die Gruppierung von Kohorten mit einem zeitbasierten Merkmal optimiert. Dies eignet sich hervorragend für Analysen, die sich auf ein bestimmtes Benutzersegment konzentrieren (z. B. alle Benutzer, die über eine gebührenpflichtige Suchkampagne erworben wurden). Im `Cohort Analysis Builder`, können Sie (1) sich auf diese spezifische Benutzergruppe konzentrieren und (2) `cohort` an einem Datum (z. B. dem Datum der ersten Bestellung).

Wenn Sie jedoch das Kohortenverhalten mehrerer Benutzersegmente im selben Kohortenbericht analysieren möchten (`paid` Suche versus `organic` Suche vs. direkter Traffic, vielleicht?), kann diese erweiterte Analyse in der `Report Builder`.

## Welche Informationen sollte ich an den Support senden, um meine Analyse einzurichten? {#support}

Erstellen einer `qualitative cohort` im Bericht `Report Builder` umfasst das Erstellen eines Adobe Analyst-Teams [Erweiterte berechnete Spalten](../data-warehouse-mgr/creating-calculated-columns.md) auf den erforderlichen Tabellen.

Um diese zu erstellen, senden Sie eine [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en) (und referenzieren Sie diesen Artikel!). Folgendes müssen Sie wissen:

* Die `metric` Sie möchten Ihre Kohortenanalyse mit der verwendeten Tabelle durchführen (Beispiel: `Revenue`, basierend auf der `orders` Tabelle).

* Die `user segments` Sie möchten definieren und wo sich diese Informationen in Ihrer Datenbank befinden (Beispiel: unterschiedliche Werte `User's referral source`, nativ für die `users` und nach unten zu `orders`).

* Die `cohort date` Sie möchten, dass Ihre Analyse verwendet wird (Beispiel: die `User's first order date` Zeitstempel). Dieses Beispiel würde es uns ermöglichen, jedes Segment zu betrachten und `How does a user's revenue grow in the months following their first order date?`.

* Die `time interval` dass die Analyse angezeigt werden soll (Beispiel: `weeks`, `months`oder `quarters` nach `User's first order date`).

Sobald das Analyseteam der Adobe auf die oben genannten Punkte reagiert, verfügen Sie über einige neue erweiterte berechnete Spalten, um Ihren Bericht zu erstellen! Dann können Sie die folgenden Anweisungen befolgen, um dies zu tun.

## Erstellung der qualitativen Kohortenanalyse {#create}

Zunächst möchten Sie die Metrik, die Sie für die Kohortierung interessieren, einmal für jede `cohort` analysieren. In diesem Beispiel möchten Sie die kumulative `Revenue` in den Monaten nach der ersten Bestellung eines Kunden, segmentiert durch die `User's referral source`. Das bedeutet, dass Sie für jedes Segment einen `Revenue` Metrik und Filter für das spezifische Segment:

![](../../assets/qualcohort1.gif)

Zweitens sollten Sie zwei Zeitoptionen des Berichts ändern:

1. Legen Sie die `time interval` nach `None`. Dies liegt daran, dass Sie eine Gruppierung nach Zeitintervall als Dimension vornehmen, anstatt die üblichen Zeitoptionen zu verwenden.

1. Legen Sie die `time range` in das Zeitfenster, das der Bericht abdecken soll.

In diesem Beispiel sehen Sie sich eine `all time` Ansicht von `Revenue`. Danach sollte eine Reihe von Punkten angezeigt werden:

![](../../assets/qualcohort2.gif)

Drittens passen Sie die Einstellung an, um die `cohorts`. Basierend auf `cohort date` und `time interval` Sie dem Adobe Analyst-Team eine Dimension in Ihrem Konto zugewiesen haben, die die `cohort` Dating. In diesem Beispiel wird diese benutzerdefinierte Dimension `Months between this order and customer's first order date`. Mithilfe dieser Dimension sollten Sie:

* `Group by` die Dimension mit der `group by` option

* Wählen Sie alle Werte der `dimension` an dem Sie interessiert sind

* Mit dem `Show top/bottom option`, wählen Sie die wichtigsten X Monate aus, an denen Sie interessiert sind, und sortieren Sie nach `Months between this order and customer's first order date` Dimension

Jetzt können Sie für jede Zeile eine Zeile sehen `cohort` die Sie angegeben haben. Sehen Sie sich jetzt das Beispiel an - Sie sehen die `Revenue` von den Nutzern jeder Verweisquelle beigetragen werden, `grouped by` die Anzahl der Monate zwischen ihrer ersten Bestellung und einer nachfolgenden Bestellung. Im Beispiel wurde auch eine `Cumulative perspective` um die `cohorts'` aggregiertes Wachstum - Sehen Sie sich die Ergebnistabelle für mehr Granularität an.

Was sagt uns das? Hier die spezifische Verweisquelle `Paid search` ist im ersten Monat der Kauflebensdauer eines Kunden nützlich, kann aber seinen Kundenstamm nicht mit wiederholtem Umsatz halten. while `Direct Traffic` beginnt mit einem niedrigeren Betrag, werden die Einnahmen in den Folgemonaten tatsächlich in einem ähnlichen Tempo angesammelt.

Egal, wie du es würdest, `cohort` Die Analyse ist ein leistungsstarkes Tool in Ihrer Analyse-Toolbox. Diese Art von Analyse kann einige interessante Einblicke in Ihr Geschäft liefern, dass traditionelle `time-based cohorts` Dies kann nicht der Fall sein, da Sie damit bessere datenbasierte Entscheidungen treffen können.
