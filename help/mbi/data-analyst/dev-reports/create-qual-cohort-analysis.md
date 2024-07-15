---
title: Erstellen einer qualitativen Kohortenanalyse
description: Erfahren Sie, was eine qualitative Kohorte ist, warum Sie an der Erstellung dieser Analyse interessiert sein könnten und wie Sie sie in Commerce Intelligence erstellen können.
exl-id: 113244e4-409b-4129-b3d4-7a3433539ade
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---

# Erstellen einer `Qualitative Cohort Analysis`

Wissen Sie, wie Ihre [!DNL Google Adwords] erworbenen Kundensegmente ihr LTV-Angebot im Vergleich zu den Kunden, die über die kostenlose Suche erworben wurden, erweitern? Haben Sie schon einmal daran gedacht, im selben Bericht nebeneinander verschiedene Kundensegmente mit 0 zu analysieren? `cohort` Wenn ja, hilft Ihnen ein `qualitative cohort analysis` bei der Beantwortung dieser Fragen.

In diesem Thema erfahren Sie, was eine qualitative Kohorte ist, warum Sie an der Erstellung dieser Analyse interessiert sein könnten und wie Sie sie in [!DNL Commerce Intelligence] erstellen können.

## Was ist sowieso `qualitative cohorts`? {#whatare}

`Cohort` Analyse im Allgemeinen kann als Analyse von Benutzergruppen mit ähnlichen Merkmalen über ihre Lebenszyklen hinweg definiert werden. Damit können Sie Verhaltenstrends über verschiedene Benutzergruppen hinweg identifizieren.

Siehe [Kohortenanalyse](https://www.cohortanalysis.com/).

Die meisten `cohort` analysieren in [!DNL Commerce Intelligence] Benutzer nach einem gemeinsamen Datum (z. B. die Gruppe aller Kunden, die in einem bestimmten Monat ihren ersten Kauf tätigten). Ein `qualitative cohort` ist etwas anders: Es handelt sich um eine Benutzergruppe, die durch ein Merkmal definiert wird, das nicht zeitbasiert ist. Beispiele sind:

* Die Gruppe aller Benutzer, die über eine Werbekampagne erworben wurden
* Die Gruppe aller Benutzer, deren erster Kauf einen Coupon enthielt (oder nicht)
* Die Gruppe aller Benutzer eines bestimmten Alters

## Wie unterscheidet sich dies vom normalen `cohort`-Builder? {#different}

Der [`Cohort Analysis Builder`](../dev-reports/cohort-rpt-bldr.md) ist für die Gruppierung von Kohorten mithilfe eines zeitbasierten Merkmals optimiert. Dies eignet sich hervorragend für Analysen, die sich auf ein bestimmtes Benutzersegment konzentrieren (z. B. alle Benutzer, die über eine gebührenpflichtige Suchkampagne erworben wurden). In der `Cohort Analysis Builder` können Sie sich (1) auf diese spezifische Benutzergruppe konzentrieren und (2) `cohort` auf ein Datum (z. B. ihr erstes Bestelldatum).

Wenn Sie jedoch das Kohortenverhalten mehrerer Benutzersegmente im selben Kohortenbericht analysieren möchten (`paid` Suche versus `organic` Suche vs. direkter Traffic, vielleicht?), kann diese erweiterte Analyse in der `Report Builder` erstellt werden.

## Welche Informationen sollte ich an den Support senden, um meine Analyse einzurichten? {#support}

Das Erstellen eines `qualitative cohort` -Berichts im `Report Builder` umfasst das Erstellen einiger [erweiterter berechneter Spalten](../data-warehouse-mgr/creating-calculated-columns.md) durch das Adobe-Analyseteam für die erforderlichen Tabellen.

Senden Sie dazu ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) (und verweisen Sie auf diesen Artikel!). Folgendes müssen Sie wissen:

* Die `metric`, mit der Sie Ihre Kohortenanalyse durchführen möchten, und die Tabelle, in der sie verwendet wird (Beispiel: `Revenue`, basierend auf der `orders`-Tabelle).

* Die `user segments`, die Sie definieren möchten, und wo sich diese Informationen in Ihrer Datenbank befinden (Beispiel: unterschiedliche Werte von `User's referral source`, die in der `users` -Tabelle nativ sind und nach unten auf die `orders` verschoben werden).

* Die `cohort date`, die Ihre Analyse verwenden soll (Beispiel: der `User's first order date` Zeitstempel). In diesem Beispiel können wir jedes Segment betrachten und `How does a user's revenue grow in the months following their first order date?` fragen.

* Die `time interval`, über die die Analyse angezeigt werden soll (Beispiel: `weeks`, `months` oder `quarters` nach dem `User's first order date`).

Sobald das Adobe-Analyseteam auf die oben genannten Punkte reagiert, haben Sie einige neue erweiterte berechnete Spalten, um Ihren Bericht zu erstellen! Dann können Sie die folgenden Anweisungen befolgen, um dies zu tun.

## Erstellung der qualitativen Kohortenanalyse {#create}

Zunächst möchten Sie die Metrik hinzufügen, die Sie für die Kohortierung interessieren, einmal für jeden `cohort`, den Sie analysieren. In diesem Beispiel möchten Sie die kumulative `Revenue` sehen, die in den Monaten nach der ersten Bestellung eines Kunden erstellt wurde und durch die `User's referral source` segmentiert ist. Das bedeutet, dass Sie für jedes Segment eine `Revenue` -Metrik hinzufügen und für das spezifische Segment filtern:

![](../../assets/qualcohort1.gif)

Zweitens sollten Sie zwei Zeitoptionen des Berichts ändern:

1. Setzen Sie die `time interval` auf `None`. Dies liegt daran, dass Sie eine Gruppierung nach Zeitintervall als Dimension vornehmen, anstatt die üblichen Zeitoptionen zu verwenden.

1. Setzen Sie &quot;`time range`&quot;auf das Zeitfenster, das der Bericht abdecken soll.

In diesem Beispiel sehen Sie sich die Ansicht `all time` von `Revenue` an. Danach sollte eine Reihe von Punkten angezeigt werden:

![](../../assets/qualcohort2.gif)

Drittens passen Sie die Einstellung an, um die `cohorts` einzurichten. Basierend auf den `cohort date` und `time interval`, die Sie dem Adobe-Analyseteam angegeben haben, haben Sie in Ihrem Konto eine Dimension, die die `cohort` Dating-Aktivität ausführt. In diesem Beispiel wird diese benutzerdefinierte Dimension als `Months between this order and customer's first order date` bezeichnet. Mithilfe dieser Dimension sollten Sie:

* `Group by` die Dimension mit der `group by` -Option

* Wählen Sie alle Werte des `dimension` aus, an dem Sie interessiert sind

* Wählen Sie mit dem Wert &quot;`Show top/bottom option`&quot;die obersten X Monate aus, die Sie interessiert, und sortieren Sie nach der Dimension &quot;`Months between this order and customer's first order date`&quot;

Jetzt können Sie für jeden von Ihnen angegebenen `cohort` eine Zeile sehen. Sehen Sie sich das Beispiel jetzt an - Sie sehen, dass die Benutzer der einzelnen Verweisquellen `Revenue` beigetragen haben, `grouped by` die Anzahl der Monate zwischen ihrer ersten Bestellung und jeder nachfolgenden Bestellung. Im Beispiel wurde auch der Wert `Cumulative perspective` hinzugefügt, um das Aggregat-Wachstum `cohorts'` anzuzeigen. In der Ergebnistabelle wird eine größere Granularität angezeigt.

Was sagt uns das? In diesem Fall ist die spezifische Verweisquelle `Paid search` im ersten Monat der Kauflebensdauer eines Kunden nützlich, kann aber seinen Kundenstamm nicht mit wiederholtem Umsatz halten. Während `Direct Traffic` mit einem niedrigeren Betrag beginnt, sammeln sich die Umsätze in den Folgemonaten tatsächlich in einem ähnlichen Tempo.

Unabhängig davon, wie Sie es würfeln, `cohort` Analyse ist ein leistungsstarkes Tool in Ihrer Analyse-Toolbox. Diese Art von Analyse kann einige interessante Einblicke in Ihr Geschäft liefern, die traditionelle `time-based cohorts` nicht bieten. Dies ermöglicht es Ihnen, datenbasierte Entscheidungen zu treffen.
