---
title: Kohortenanalyse zum Lebensdauerumsatz
description: Erkunden Sie die Leistungsfähigkeit der Commerce Intelligence-Kohortenanalyse.
exl-id: f2b55745-d364-4ba6-9857-ce9cee05c3ae
source-git-commit: 6b1bd96a0f9ae8bda3ae8db8ca78ad655079f2a4
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# [!DNL Lifetime Revenue Cohort] Analyse

Es gibt verschiedene Möglichkeiten, Ihre Daten anzuzeigen in [!DNL Adobe Commerce Intelligence]und Sie wissen, dass Interpretation und Verständnis ebenso wichtig sind wie Berechnung und Visualisierung. Dieses Thema untersucht die Leistungsfähigkeit von [!DNL Commerce Intelligence] `cohort` Analyse.

## Funktion `lifetime revenue cohort` Analyse bedeuten?

Die folgende Tabelle zeigt die kumulativen Ausgaben pro Benutzer für einen Zeitraum nach dem Erwerb. `Cohorts` der Benutzer nach ihrem Akquise-Monat aufgeteilt werden.

Die obige orangefarbene Zeile zeigt beispielsweise den Durchschnitt der Benutzer an, die im November 2011 erworben wurden. Der erste Datenpunkt bedeutet, dass die im November erworbenen Benutzer in ihrem ersten Monat im Durchschnitt etwa `$200`. Der zweite Datenpunkt bedeutet, dass diese Benutzer am Ende ihres zweiten Monats durchschnittlich etwa `$240`. Ihre durchschnittlichen Ausgaben im zweiten Monat waren ungefähr `$40 (240 - 200)`. Die verschiedenen Zeilen stellen unterschiedliche Benutzerkohorten dar. Die grüne Linie stellt die Benutzer dar, die im Dezember erworben wurden, und die blaue Linie zeigt die Benutzer, die im Oktober erworben wurden.

## Warum ist das wichtig?

Diese Art `cohort` Die Analyse kann für verschiedene Zwecke nützlich sein, doch der unmittelbarste Vorteil sind häufig bessere Entscheidungen über die Kundenakquise. Viele Unternehmen beschränken ihre Marketing-Ausgaben auf Kanäle, die beim ersten Kauf eines Kunden eine Rentabilität erzielen. Diese Unternehmen zahlen dafür, Kunden über einen bestimmten Kanal zu erwerben, solange ihr durchschnittlicher Erstkauf mehr bringt `gross margin` als es kostet, sie zu erwerben.

Das Problem bei diesem Ansatz besteht darin, dass er häufig zu einer unzureichenden Investition in Wachstum führt. Wenn Ihre Konkurrenten auf der Grundlage eines tieferen Verständnisses für das Kaufverhalten Marketing betreiben, sind sie größer als Sie. Die `lifetime revenue cohort` Die Analyse hilft Ihnen, die Folgen einer Ausweitung Ihrer Kundenakquise-Ausgaben zu verstehen, und bietet eine einfache Möglichkeit, dies dem Rest Ihres Teams zu vermitteln. Wenn sich zukünftige Kunden wie Bestandskunden verhalten, führt der Erwerb von Kunden für eine höhere CPA zu einer vorhersehbaren Amortisierungszeit. Abhängig von der Kassenposition des Unternehmens können Sie festlegen, mit welcher Zahlungsfrist Sie sich wohlfühlen, den entsprechenden Ort im Diagramm finden und entsprechend ausgeben.

Sie können diese Analyse auch verwenden, um zu sehen, ob Sie beim Onboarding, Interagieren und Generieren von Umsatz durch die von Ihnen erworbenen Benutzer besser werden. Dies `cohort` Die Analyse ist eine großartige Möglichkeit zu sehen, ob eine kostenlose Versandaktion für neue Benutzer zu wiederholten Käufern oder einmaligen Käufern führte, die nie zurückkehren.

## Wie wird dies für verschiedene Geschäftsmodelle variieren?

Für die meisten Unternehmen ist die `lifetime revenue cohort` Das Analysediagramm zeigt einen großen Ausgabenbetrag im Anfangszeitraum an und steigt dann im Laufe der Zeit langsamer an. Dieser anfängliche Anstieg liegt daran, dass Kunden ihren ersten Kauf eher kurz nach dem Kauf tätigen als zu einem anderen Zeitpunkt. In Fällen, in denen das Akquise-Ereignis selbst ein Kauf ist, tätigen 100 % der Kunden in ihrem ersten Zeitraum einen Kauf. In Fällen, in denen eine Registrierung vor einem Kauf erfolgen kann, ist dieser Effekt weniger drastisch.

Beispiel: [!DNL Groupon] würde wahrscheinlich einen wesentlich geringeren Sprung als [!DNL Amazon], weil viele der Personen, die sich für [!DNL Groupon] tätigen Sie nicht sofort einen Kauf. Wenn es keine große Anzahl von Erstattungen gibt, wird diese Grafik nach dem ersten Sprung nach oben und nach rechts nach oben nach oben nach oben und nach rechts abwärts gleiten. Die Wachstumsrate sinkt im Laufe der Zeit tendenziell, da Kunden bei ihrer ersten Anmeldung am aktivsten sind. Dies führt dazu, dass der Durchschnitt sinkt, da die Anzahl der Personen in der Kohorte konstant bleibt, unabhängig davon, wie viele zurückkehren, um mehr zu kaufen. In Abonnementgeschäften wird der Abhang weniger aggressiv verfallen als in Unternehmen, in denen Menschen einmalige Käufe tätigen.

Gelegentlich wird ein Abonnement-Geschäft tatsächlich einen Hang haben, der sich im Laufe der Zeit erhöht. Es ist selten, dies zu sehen, aber es ist ein großartiges Signal für das Unternehmen, wenn es passiert. Dies bedeutet nicht, dass es keine Kunden gibt, die sich berühren, sondern dass Upgrades für Kunden durchgeführt werden, die mehr bleiben, als für Kunden, die weggehen, aufzukommen.

## Wie wird das berechnet?

Diese Berechnung umfasst zwei einfache Eingaben: wie viele Mitglieder sich im `cohort` (die sich nie ändern) und wie viel Umsatz diese Mitglieder im angegebenen Zeitraum generiert haben. So bestimmen Sie die Mitglieder im `cohort`, zählt die Anzahl der Benutzer, die im betreffenden Zeitraum erworben wurden. Bei einer Akquise kann es sich um einen Erstkauf, eine Kontoerstellung, eine Newsletter-Anmeldung oder ein anderes Ereignis handeln. Die `revenue` Die Berechnung ist etwas komplizierter. Sie möchten den Umsatz für Bestellungen summieren, die von Mitgliedern dieses `cohort` und innerhalb eines bestimmten Zeitraums ab ihrem Erwerbsdatum (z. B. die ersten drei Monate) stattgefunden haben. Schließlich teilen Sie den Umsatz durch die Anzahl der Mitglieder in der `cohort` für jeden Zeitraum im Diagramm und fügen Sie diesen Wert kumulativ im Zeitverlauf hinzu.

## Was sind die Varianten dieser Grafik?

Es gibt viele verschiedene Arten von nützlichen `cohort` analysiert. Die häufigste Variante ist [Filtern nach der Benutzerakquise-Quelle](../analysis/most-value-source-channel.md). Sie können diese Grafik beispielsweise für Kunden anzeigen, die von `organic` Suche, `paid` oder ein Partnerprogramm. Auf diese Weise können Sie erkennen, ob die Kunden aus einer Akquise-Quelle loyaler oder wertvoller sind als andere. Sie können auch nach demografischen oder anderen Benutzerattributen filtern.

Eine weitere Möglichkeit, die Daten anzuzeigen, besteht in einer inkrementellen anstatt einer kumulativen Datenperspektive. Dies zeigt den inkrementellen Betrag an, den ein durchschnittlicher Benutzer in jedem Monat nach dem Erwerb ausgibt. Dies ist nützlich, um die Anzahl der wiederholten Käufe vorherzusagen, die Sie von vorhandenen Benutzern erhalten. Sie können dies neben dem Umsatz auch mit anderen Dingen betrachten. Einige Beispiele sind Marge- und nicht finanzielle Metriken wie Einladungen, Abstimmungen oder Nachrichten.
