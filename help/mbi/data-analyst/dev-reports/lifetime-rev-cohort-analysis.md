---
title: Kohortenanalyse zum Lebensdauerumsatz
description: Erkunden Sie die Leistungsfähigkeit der Commerce Intelligence-Kohortenanalyse.
exl-id: f2b55745-d364-4ba6-9857-ce9cee05c3ae
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# [!DNL Lifetime Revenue Cohort] Analyse

Es gibt zahlreiche Möglichkeiten, Ihre Daten in [!DNL Adobe Commerce Intelligence] zu betrachten. Sie wissen, dass Interpretation und Verständnis ebenso wichtig sind wie Berechnung und Visualisierung. Dieses Thema untersucht die Leistung der Analyse von [!DNL Commerce Intelligence] `cohort`.

## Was bedeutet die Analyse von `lifetime revenue cohort`?

Die folgende Tabelle zeigt die kumulativen Ausgaben pro Benutzer für einen Zeitraum nach dem Erwerb. `Cohorts` der Benutzer werden nach ihrem Akquisemonat aufgeteilt.

Die obige orangefarbene Zeile zeigt beispielsweise den Durchschnitt der Benutzer an, die im November 2011 erworben wurden. Der erste Datenpunkt bedeutet, dass Benutzer, die im November erfasst wurden, im ersten Monat durchschnittlich etwa `$200` ausgegeben haben. Der zweite Datenpunkt bedeutet, dass diese Benutzer am Ende ihres zweiten Monats durchschnittlich etwa `$240` ausgegeben haben. Ihre durchschnittlichen Ausgaben im zweiten Monat betrugen etwa `$40 (240 - 200)`. Die verschiedenen Zeilen stellen unterschiedliche Benutzerkohorten dar. Die grüne Linie stellt die Benutzer dar, die im Dezember erworben wurden, und die blaue Linie zeigt die Benutzer, die im Oktober erworben wurden.

## Warum ist das wichtig?

Diese Art von `cohort` -Analyse kann für verschiedene Zwecke nützlich sein, aber der unmittelbarste Vorteil sind häufig bessere Entscheidungen zur Kundenakquise. Viele Unternehmen beschränken ihre Marketing-Ausgaben auf Kanäle, die beim ersten Kauf eines Kunden eine Rentabilität erzielen. Diese Unternehmen zahlen dafür, dass sie Kunden über einen bestimmten Kanal erwerben, solange ihr durchschnittlicher Erstkauf mehr `gross margin` bringt, als es für die Übernahme kostet.

Das Problem bei diesem Ansatz besteht darin, dass er häufig zu einer unzureichenden Investition in Wachstum führt. Wenn Ihre Konkurrenten auf der Grundlage eines tieferen Verständnisses für das Kaufverhalten Marketing betreiben, sind sie größer als Sie. Die `lifetime revenue cohort` -Analyse hilft Ihnen, die Folgen einer Ausweitung Ihrer Kundenakquise-Ausgaben zu verstehen, und bietet eine einfache Möglichkeit, dies dem Rest Ihres Teams zu vermitteln. Wenn sich zukünftige Kunden wie Bestandskunden verhalten, führt der Erwerb von Kunden für eine höhere CPA zu einer vorhersehbaren Amortisierungszeit. Abhängig von der Kassenposition des Unternehmens können Sie festlegen, mit welcher Zahlungsfrist Sie sich wohlfühlen, den entsprechenden Ort im Diagramm finden und entsprechend ausgeben.

Sie können diese Analyse auch verwenden, um zu sehen, ob Sie beim Onboarding, Interagieren und Generieren von Umsatz durch die von Ihnen erworbenen Benutzer besser werden. Diese `cohort` -Analyse ist beispielsweise eine großartige Möglichkeit zu sehen, ob eine kostenlose Versandaktion für neue Benutzer zu Wiederholungskäufern oder einmaligen Käufern führte, die nie zurückkehrten.

## Wie wird dies für verschiedene Geschäftsmodelle variieren?

Für die meisten Unternehmen wird das Diagramm `lifetime revenue cohort` zur Analyse einen hohen Ausgabenbetrag im Anfangszeitraum anzeigen und dann im Laufe der Zeit langsamer ansteigen. Dieser anfängliche Anstieg liegt daran, dass Kunden ihren ersten Kauf eher kurz nach dem Kauf tätigen als zu einem anderen Zeitpunkt. In Fällen, in denen das Akquise-Ereignis selbst ein Kauf ist, tätigen 100 % der Kunden in ihrem ersten Zeitraum einen Kauf. In Fällen, in denen eine Registrierung vor einem Kauf erfolgen kann, ist dieser Effekt weniger drastisch.

Beispiel: [!DNL Groupon] hätte wahrscheinlich einen wesentlich geringeren ersten Sprung als [!DNL Amazon], da viele der Personen, die sich für [!DNL Groupon] anmelden, nicht sofort einen Kauf tätigen. Wenn es keine große Anzahl von Erstattungen gibt, wird diese Grafik nach dem ersten Sprung nach oben und nach rechts nach oben nach oben nach oben und nach rechts abwärts gleiten. Die Wachstumsrate sinkt im Laufe der Zeit tendenziell, da Kunden bei ihrer ersten Anmeldung am aktivsten sind. Dies führt dazu, dass der Durchschnitt sinkt, da die Anzahl der Personen in der Kohorte konstant bleibt, unabhängig davon, wie viele zurückkehren, um mehr zu kaufen. In Abonnementgeschäften wird der Abhang weniger aggressiv verfallen als in Unternehmen, in denen Menschen einmalige Käufe tätigen.

Gelegentlich wird ein Abonnement-Geschäft tatsächlich einen Hang haben, der sich im Laufe der Zeit erhöht. Es ist selten, dies zu sehen, aber es ist ein großartiges Signal für das Unternehmen, wenn es passiert. Dies bedeutet nicht, dass es keine Kunden gibt, die sich berühren, sondern dass Upgrades für Kunden durchgeführt werden, die mehr bleiben, als für Kunden, die weggehen, aufzukommen.

## Wie wird das berechnet?

Diese Berechnung enthält zwei einfache Eingaben: die Anzahl der Mitglieder im `cohort` (die sich nie ändern) und die Anzahl der Umsätze, die diese Mitglieder in dem angegebenen Zeitraum generiert haben. Um die Mitglieder im `cohort` zu bestimmen, zählen Sie die Anzahl der Benutzer, die im betreffenden Zeitraum erworben wurden. Bei einer Akquise kann es sich um einen Erstkauf, eine Kontoerstellung, eine Newsletter-Anmeldung oder ein anderes Ereignis handeln. Die `revenue`-Berechnung ist etwas komplizierter. Sie möchten den Umsatz für Bestellungen summieren, die von Mitgliedern dieses `cohort` aufgegeben wurden und innerhalb eines bestimmten Zeitraums ab ihrem Akquisedatum stattgefunden haben (z. B. die ersten drei Monate). Schließlich teilen Sie den Umsatz durch die Anzahl der Mitglieder in den `cohort` für jeden Zeitraum im Diagramm und fügen diesen Wert kumulierend über einen Zeitraum hinzu.

## Was sind die Varianten dieser Grafik?

Es gibt viele verschiedene Arten nützlicher `cohort`-Analysen. Die häufigste Variante ist das Filtern nach der Benutzerakquise-Quelle ](../analysis/most-value-source-channel.md). [ Sie können dieses Diagramm beispielsweise für Kunden betrachten, die aus der `organic`-Suche, der `paid`-Suche oder einem Partnerprogramm kamen. Auf diese Weise können Sie erkennen, ob die Kunden aus einer Akquise-Quelle loyaler oder wertvoller sind als andere. Sie können auch nach demografischen oder anderen Benutzerattributen filtern.

Eine weitere Möglichkeit, die Daten anzuzeigen, besteht in einer inkrementellen anstatt einer kumulativen Datenperspektive. Dies zeigt den inkrementellen Betrag an, den ein durchschnittlicher Benutzer in jedem Monat nach dem Erwerb ausgibt. Dies ist nützlich, um die Anzahl der wiederholten Käufe vorherzusagen, die Sie von vorhandenen Benutzern erhalten. Sie können dies neben dem Umsatz auch mit anderen Dingen betrachten. Einige Beispiele sind Marge- und nicht finanzielle Metriken wie Einladungen, Abstimmungen oder Nachrichten.
