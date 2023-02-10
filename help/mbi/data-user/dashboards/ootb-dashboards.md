---
title: Einbezogene Dashboards
description: Erfahren Sie, wie Sie die Gesundheit wichtiger Metriken wie den Umsatz während der Nutzungsdauer, die Anzahl wiederholter Käufe und mehr überprüfen und so eine solide Grundlage für die zukünftige Exploration schaffen können.
exl-id: f50fc417-e5d4-401c-9baa-cda1468196a2
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 0%

---

# Einbezogene Dashboards

Im Rahmen unserer Dienstleistungen bieten wir eCommerce und `SaaS` Starter-Pakete. Diese von unseren Analytikern erstellten Pakete enthalten einen benutzerdefinierten Satz von Dashboards und Berichten für Ihren Datensatz. Die in diesen Packages enthaltenen Analysen ermöglichen es Ihnen, die Gesundheit wichtiger Metriken wie der Umsatz der Nutzer über die Lebensdauer, die Anzahl wiederholter Käufe und mehr zu überprüfen und so eine solide Grundlage für die zukünftige Erforschung zu schaffen.

>[!NOTE]
>
>Die Verfügbarkeit einiger Dashboards hängt von Ihrem Datensatz ab.

Wenn Sie Fragen haben oder ein Package zu Ihrem Konto hinzufügen möchten, senden Sie eine [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en) für Hilfe.

## Übersicht über das Unternehmen

Die `executive overview` Das Dashboard basiert auf Diagrammen, die in anderen Dashboards vorhanden sind. Dieses Dashboard bietet einen allgemeinen Überblick über Ihre Daten und enthält Diagramme, die täglich überprüft werden, während andere Dashboards detailliertere Informationen enthalten. Zunächst wird es in jedem Konto als Standard-Dashboard festgelegt.

Wir haben zwar einen allgemeinen Satz von Diagrammen für Sie eingefügt, empfehlen jedoch, dieses Dashboard Ihren Bedürfnissen anzupassen, indem Sie weitere Diagramme hinzufügen, die Sie am häufigsten verwenden.

## Kohortenanalyse

Die `cohort analysis` Das Dashboard enthält eine Reihe von Diagrammen, die das durchschnittliche Umsatzwachstum und den inkrementellen Umsatzzuwachs der Nutzer nach Registrierungs-Kohorten gruppieren. Dies zeigt, ob der Lebenszeitwert (LTV) eines Kunden, der Wert eines Kunden für ein Unternehmen, im Laufe der Zeit zunimmt, und identifiziert auch Trends rund um das LTV-Wachstum. Beachten Sie, dass standardmäßig *Wir übernehmen alle registrierten Benutzer (Käufer und Nicht-Käufer).* in der durchschnittlichen LTV-Berechnung - siehe [Kohortenanalysethema](../../data-analyst/dev-reports/cohort-rpt-bldr.md).

Dieses Dashboard kann auch Kohortendiagramme enthalten, die den Lebenszeitumsatz von Benutzern aus einer bestimmten Akquisequelle, einem bestimmten Kanal oder einer bestimmten demografischen Gruppe analysieren (z. B. New York oder Kalifornien). Damit wird gezeigt, wie Sie LTV für sehr spezifische Segmente Ihrer Benutzerbasis analysieren können und ob eine Gruppe im Laufe der Zeit höhere LTV-Werte liefert.

Weitere Informationen zu Kohorten finden Sie unter [Durchführen einer Kohortenanalyse](../../data-analyst/dev-reports/cohort-rpt-bldr.md).

Wenn Sie die Benutzerakquise-Quelle derzeit nicht verfolgen, lesen Sie den Abschnitt [Tracking der Benutzerakquise-Quelldaten - Überblick](../../data-analyst/analysis/google-track-user-acq.md).

## Email summary

Die `Email Summary` Das Dashboard enthält einen Beispielsatz von Diagrammen, die in einer automatisierten täglichen E-Mail-Zusammenfassung verwendet werden können. Siehe [Erstellen automatisierter E-Mail-Zusammenfassungen](../../data-user/export-data/email-summaries.md) für weitere Informationen zum Konfigurieren von E-Mail-Zusammenfassungen.  

## Treuestufe

Die `Retention health` Dashboard zeigt das wiederholte Kaufverhalten Ihrer Benutzerbasis an.

Die `Time between orders` -Diagramm zeigt die durchschnittliche und/oder mittlere verstrichene Zeit zwischen der ersten und zweiten Bestellung eines Benutzers, der zweiten und dritten Reihenfolge usw. Sie können [die Verwendung dieser Daten zur Konfiguration Ihrer E-Mail-Marketing-Kampagnen in Erwägung ziehen](http://blog.rjmetrics.com/acting-on-marketing-data-in-your-rjmetrics-online-dashboard/).

Die `Users by lifetime number of orders` -Diagramm listet die Gesamtanzahl der Benutzer für jede Lebensdauer von Bestellungen auf, um einen allgemeinen Überblick über das Verhalten bei wiederholten Bestellungen zu erhalten.  

Die `Repeat order probability` zeigt die Wahrscheinlichkeit an, dass ein Benutzer mit einer bestimmten Bestellnummer einen Kauf tätigt. So sehen Sie die Wahrscheinlichkeit von Kunden, die `x` Bestellungen `(x+1)` Bestellungen, teilen Sie einfach die Anzahl der Personen, die mindestens `(x+1)` Käufe nach der Anzahl der Personen, die mindestens `x` Einkäufe.

### Beispiel

Anzahl der Kunden, die in ihrer Lebensdauer einen Kauf getätigt haben: `90`

Anzahl der Kunden, die während ihrer Lebensdauer zwei Käufe getätigt haben: `30`

Anzahl der Kunden, die während ihrer Lebensdauer drei Käufe getätigt haben: `10`

In diesem Beispiel lautet die Wahrscheinlichkeit, dass Kunden, die während ihrer Lebensdauer einen Kauf getätigt haben, einen zweiten Kauf tätigen, wie folgt: `(30 + 10) / (30+10+90) = 30.77%`.

## Wachstum von Kunden-LTV

Die `Customer LTV growth` Das Dashboard enthält eine Reihe von Diagrammen, die den durchschnittlichen Umsatz pro Benutzer ermitteln. Die Diagramme werden basierend auf dem durchschnittlichen Umsatz segmentiert, der innerhalb der ersten 30, 60, 90 oder 365 Tage nach der Registrierung generiert wird.  

Die untere Diagrammzeile zeigt diese Durchschnittswerte, segmentiert nach Akquise-Quellen oder demografischen Daten, um zu zeigen, welche Benutzergruppen im Zeitverlauf den meisten Umsatz generieren.

## Produktleistung

Die `Product Performance` Das Dashboard enthält Diagramme, die die allgemeine Produktleistung anzeigen, indem die Anzahl der verkauften Artikel und der Umsatz nach Artikeln angezeigt werden und die leistungsstärksten Produkte ermittelt werden.

## Letzte Aktivität

Die `Recent Activity` Dashboard zeigt die Leistungsdaten der letzten 30 Tage an.

## Transaktionsstatus

Die `Transaction Health` Das Dashboard enthält Übersichtsdiagramme zu Umsatz, Bestellungen und durchschnittlichem Bestellwert. Diese Diagramme können nach Marketing-Kanälen, demografischen Daten oder speziellen Couponcodes segmentiert werden.

## Benutzer zum Targeting

Die `Users to target` Das Dashboard enthält Tabellen-Diagramme, in denen Benutzer aufgelistet werden, die über ein bestimmtes gemeinsames Kaufverhalten verfügen. Zu den Beispielen gehören:

* Liste der einmaligen Käufer, die kaufen `X` vor Monaten (die Sie möglicherweise erneut aktivieren möchten)

* Liste der wichtigsten Geldgeber (die Sie möglicherweise glücklich halten möchten)

* Liste der in der Vergangenheit aktiven Spender `X` Tage (die Sie belohnen möchten)

Mit unseren Datenexport-Tools ist es einfach, [Erstellen von E-Mail-Listen von Benutzern mit ähnlichem Kaufverhalten für Zielmarketing](http://blog.rjmetrics.com/creating-contact-lists-for-top-customers/).

## Benutzeraktivität

Die `User activity` Das Dashboard enthält Diagramme, die Benutzer nach einer Vielzahl von Daten segmentieren, darunter Akquisequelle, demografische Daten und die durchschnittliche Erstbestellung. Er enthält auch die Analyse der Benutzerkohorte, einschließlich des durchschnittlichen Gesamtumsatzes während der Lebensdauer nach dem Registrierungsmonat des Benutzers.

Die `% of cohort members who have purchased` -Diagramm ist besonders nützlich, da es das Konversionsverhältnis (zwischen 0 und 1) der Benutzer basierend darauf anzeigt, wann sie sich registrieren (jede Zeile stellt eine Kohorte von Benutzern dar) und wann sie ihren ersten Kauf tätigen (z. B. in Monat 1, 2, 3.. nach der Registrierung). Dies kann zeigen, dass 10 % der Benutzer im Monat 1 aktiviert haben, während diese Zahl im Monat 2, 3, 4... zunimmt und sich später versteigern kann.

In der Regel werden die Zeilen in dieser Grafik nach einem bestimmten Zeitraum horizontal. Dies bedeutet, dass nach diesem Zeitpunkt nur wenige zusätzliche Kohortenmitglieder organisch konvertiert werden - d. h. die meisten Benutzer, die einen Kauf tätigen werden, haben dies bereits getan. An dieser Stelle ist es höchst unwahrscheinlich, dass diese Mitglieder ohne Eingreifen in Käufer konvertieren. [Die Kontaktaufnahme mit benutzerdefinierten Promotions oder speziell zielgerichteten E-Mails ist eine äußerst risikoarme Möglichkeit, die Konversion dieser Population zu beschleunigen.](http://blog.rjmetrics.com/acting-on-marketing-data-in-your-rjmetrics-online-dashboard/)
