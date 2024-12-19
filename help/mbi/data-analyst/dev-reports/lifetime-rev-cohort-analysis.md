---
title: Kohortenanalyse zum Lebenszeitumsatz
description: Erkunden Sie die Leistungsfähigkeit der Commerce Intelligence-Kohortenanalyse.
exl-id: f2b55745-d364-4ba6-9857-ce9cee05c3ae
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# [!DNL Lifetime Revenue Cohort]

Es gibt zahlreiche Möglichkeiten, Ihre Daten in [!DNL Adobe Commerce Intelligence] zu betrachten, und Sie wissen, dass Interpretation und Verständnis genauso wichtig sind wie Berechnung und Visualisierung. In diesem Thema wird die Leistungsfähigkeit [!DNL Commerce Intelligence] `cohort` untersucht.

## Was bedeutet `lifetime revenue cohort` Analyse?

Die nachstehende Grafik zeigt die kumulierten Ausgaben pro Benutzerin bzw. Benutzer für einen bestimmten Zeitraum nach dem Erwerb. `Cohorts` Benutzer werden nach dem Monat ihrer Akquise aufgeteilt.

Die obige orangefarbene Linie zeigt beispielsweise den Durchschnitt für Benutzende, die im November 2011 akquiriert wurden. Der erste Datenpunkt bedeutet, dass Benutzende, die im November akquiriert wurden, im ersten Monat im Durchschnitt etwa `$200` verbrachten. Der zweite Datenpunkt bedeutet, dass diese Nutzer am Ende ihres zweiten Monats durchschnittlich etwa `$240` ausgegeben hatten. Ihre durchschnittlichen Ausgaben im zweiten Monat lagen bei ungefähr `$40 (240 - 200)`. Die verschiedenen Linien stellen verschiedene Benutzergruppen dar. Die grüne Linie stellt die Benutzenden dar, die im Dezember akquiriert wurden, und die blaue ist die Benutzenden, die im Oktober akquiriert wurden.

## Warum ist das wichtig?

Diese Art der `cohort` kann für verschiedene Zwecke nützlich sein, aber der unmittelbarste Vorteil besteht oft in besseren Entscheidungen bei der Kundenakquise. Viele Unternehmen beschränken ihre Marketingausgaben auf Kanäle, die beim ersten Kauf eine Profitabilität erzielen. Diese Unternehmen bezahlen für die Kundenakquise über einen bestimmten Kanal, solange ihr durchschnittlicher Erstkauf mehr `gross margin` einbringt, als es für die Kundenakquise kostet.

Das Problem bei diesem Ansatz besteht darin, dass er häufig zu einem Investitionsmangel in das Wachstum führt. Wenn Ihre Konkurrenten Marketing betreiben, das auf einem tieferen Verständnis des Kaufverhaltens basiert, wachsen sie über Sie hinaus. Die `lifetime revenue cohort` Analyse hilft Ihnen, die Folgen einer Ausweitung Ihrer Ausgaben für die Kundenakquise zu verstehen, und bietet eine einfache Möglichkeit, dies dem Rest Ihres Teams zu vermitteln. Wenn sich zukünftige Kunden wie Bestandskunden verhalten, führt die Akquise von Kunden für eine höhere CPA zu einer vorhersehbaren Amortisationszeit. Je nach Kassenposition des Unternehmens können Sie festlegen, mit welcher Amortisationsdauer Sie sich wohl fühlen, den entsprechenden Platz im Diagramm finden und entsprechend ausgeben.

Außerdem können Sie diese Analyse verwenden, um zu sehen, ob Sie beim Onboarding besser werden, sich einbringen und Umsatz mit den von Ihnen erworbenen Benutzern generieren. Beispielsweise ist diese `cohort` eine gute Möglichkeit, um festzustellen, ob eine kostenlose Versandaktion für neue Benutzer zu Wiederholungskäufern oder einmaligen Käufern führte, die nie zurückkommen.

## Wie wird dies je nach Geschäftsmodell variieren?

Für die meisten Unternehmen zeigt das Diagramm `lifetime revenue cohort` Analyse einen großen Ausgabenbetrag in der Anfangsphase an und steigt dann im Laufe der Zeit langsamer an. Diese anfängliche Spitze liegt darin begründet, dass Kunden ihren ersten Kauf eher kurz nach dem Kauf tätigen als zu jedem anderen Zeitpunkt. Wenn es sich bei dem Akquiseereignis selbst um einen Kauf handelt, tätigen 100 % der Kunden einen Kauf in ihrem ersten Zeitraum. In Fällen, in denen die Registrierung vor dem Kauf erfolgen kann, ist dieser Effekt weniger drastisch.

Beispielsweise hätte [!DNL Groupon] wahrscheinlich einen viel niedrigeren anfänglichen Sprung als [!DNL Amazon], da viele der Personen, die sich für [!DNL Groupon] anmelden, nicht sofort einen Kauf tätigen. Wenn es keine hohe Anzahl von Rückerstattungen gibt, wird diese Grafik nach dem ersten Sprung nach oben und nach rechts geneigt. Die Wachstumsrate nimmt tendenziell im Laufe der Zeit ab, da Kunden am aktivsten sind, wenn sie sich zum ersten Mal anmelden. Dies führt zu einem Rückgang des Durchschnitts, da die Anzahl der Personen in der Kohorte konstant bleibt, unabhängig davon, wie viele zurückkommen, um mehr zu kaufen. In Abonnementunternehmen wird der Abhang weniger aggressiv verfallen als in Unternehmen, in denen einmalige Käufe getätigt werden.

Gelegentlich hat ein Abonnementgeschäft tatsächlich eine Steigung, die mit der Zeit zunimmt. Es ist selten, dies zu sehen, aber es ist ein großartiges Signal für das Unternehmen, wenn es geschieht. Dies bedeutet nicht, dass es keine wechselnden Kunden gibt, sondern eher, dass Upgrades für Kunden, die mehr bleiben, als die Kunden, die das Programm verlassen, zu kompensieren.

## Wie wird das berechnet?

Bei dieser Berechnung gibt es zwei einfache Eingaben: wie viele Mitglieder sich im `cohort` befinden (was sich nie ändert) und wie viel Umsatz diese Mitglieder in der jeweiligen Periode generiert haben. Um die Mitglieder in der `cohort` zu ermitteln, zählen Sie die Anzahl der Benutzenden, die in dem betreffenden Zeitraum erworben wurden. Eine Akquise kann ein erster Kauf, eine Kontoerstellung, eine Newsletter-Anmeldung oder ein anderes Ereignis sein. Die `revenue` ist etwas komplizierter. Sie möchten den Umsatz für Bestellungen summieren, die von Mitgliedern dieses `cohort` innerhalb eines festen Zeitraums ab dem Kaufdatum (z. B. die ersten drei Monate) aufgegeben wurden. Schließlich teilen Sie den Umsatz durch die Anzahl der Mitglieder im `cohort` für jeden Zeitraum im Diagramm und addieren diesen Wert kumulativ im Zeitverlauf.

## Was sind die Varianten dieser Grafik?

Es gibt viele verschiedene Arten nützlicher `cohort`. Die häufigste Variante ist [Filtern nach Benutzerakquise-Quelle](../analysis/most-value-source-channel.md). Beispiel: Sie möchten dieses Diagramm für Kunden verwenden, die aus `organic` Suche, `paid` oder einem Affiliate-Programm stammen. Dies hilft zu verstehen, ob die Kunden aus einer Akquise loyaler oder wertvoller sind als andere. Sie können auch nach Demografie oder anderen Benutzerattributen filtern.

Eine andere Möglichkeit, die Daten zu betrachten, ist mit einer inkrementellen statt kumulativen Datenperspektive. Dies zeigt den inkrementellen Betrag an, den ein durchschnittlicher Benutzer in jedem Monat nach dem Erwerb ausgibt. Dies ist nützlich für die Prognose der Anzahl wiederholter Käufe, die Sie von vorhandenen Benutzern erhalten. Man kann das neben dem Umsatz auch mit anderen Dingen sehen. Einige Beispiele sind Margen- und nichtfinanzielle Metriken wie Einladungen, Abstimmungen oder Nachrichten.
