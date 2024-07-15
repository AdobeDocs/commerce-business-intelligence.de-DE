---
title: Einbezogene Dashboards
description: Erfahren Sie, wie Sie die Gesundheit wichtiger Metriken wie den Umsatz während der Nutzungsdauer, die Anzahl wiederholter Käufe und mehr überprüfen und so eine solide Grundlage für die zukünftige Exploration schaffen können.
exl-id: f50fc417-e5d4-401c-9baa-cda1468196a2
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 0%

---

# Einbezogene Dashboards

[!DNL Adobe] bietet `eCommerce` - und `SaaS` Starter-Pakete an. Diese von Adobe-Analysten erstellten Packages enthalten einen benutzerdefinierten Satz von Dashboards und Berichten für Ihren Datensatz. Die in diesen Packages enthaltenen Analysen ermöglichen es Ihnen, die Gesundheit wichtiger Metriken wie der Umsatz der Nutzer über die Lebensdauer, die Anzahl wiederholter Käufe und mehr zu überprüfen und so eine solide Grundlage für die zukünftige Erforschung zu schaffen.

>[!NOTE]
>
>Die Verfügbarkeit einiger Dashboards hängt von Ihrem Datensatz ab.

Wenn Sie Fragen haben oder ein Paket zu Ihrem Konto hinzufügen möchten, senden Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) zur Hilfe.

## Übersicht über das Unternehmen

Das Dashboard `executive overview` wird aus Diagrammen erstellt, die in anderen Dashboards vorhanden sind. Dieses Dashboard bietet einen allgemeinen Überblick über Ihre Daten und enthält Diagramme, die täglich überprüft werden, während andere Dashboards detailliertere Informationen enthalten. Zunächst wird es in jedem Konto als Standard-Dashboard festgelegt.

Ein allgemeiner Grafiksatz ist für Sie enthalten. Adobe empfiehlt, dieses Dashboard Ihren Bedürfnissen anzupassen, indem Sie weitere Diagramme hinzufügen, die Sie am häufigsten verwenden.

## Kohortenanalyse

Das Dashboard `cohort analysis` enthält eine Reihe von Diagrammen, die das durchschnittliche Umsatzwachstum und den inkrementellen Umsatzzuwachs für die gesamte Lebensdauer anzeigen, gruppiert nach Registrierungskohorten. Dies zeigt, ob der Lebenszeitwert (LTV) eines Kunden, der Wert eines Kunden für ein Unternehmen, im Laufe der Zeit zunimmt, und identifiziert auch Trends rund um das LTV-Wachstum. Standardmäßig werden *alle registrierten Benutzer (Käufer und Nicht-Käufer) für* in der durchschnittlichen LTV-Berechnung berücksichtigt - siehe das Thema [Kohortenanalyse](../../data-analyst/dev-reports/cohort-rpt-bldr.md).

Dieses Dashboard kann auch Kohortendiagramme enthalten, die den Lebenszeitumsatz von Benutzern aus einer bestimmten Akquisequelle, einem bestimmten Kanal oder einer bestimmten demografischen Gruppe analysieren (z. B. New York oder Kalifornien). Damit wird veranschaulicht, wie Sie LTV für bestimmte Segmente Ihrer Benutzerbasis analysieren und feststellen können, ob eine Gruppe im Laufe der Zeit höhere LTV-Werte liefert.

Weitere Informationen zu Kohorten finden Sie unter [Durchführen einer Kohortenanalyse](../../data-analyst/dev-reports/cohort-rpt-bldr.md).

Wenn Sie derzeit keine Benutzerakquise-Quelle verfolgen, lesen Sie den Abschnitt [Tracking User Acquisition Source Data Overview](../../data-analyst/analysis/google-track-user-acq.md) .

## Email summary

Das Dashboard `Email Summary` enthält einen Beispielsatz von Diagrammen, die in einer automatisierten täglichen E-Mail-Zusammenfassung verwendet werden können. Weitere Informationen zum Konfigurieren von E-Mail-Zusammenfassungen finden Sie unter [Erstellen automatisierter E-Mail-Zusammenfassungen](../../data-user/export-data/email-summaries.md) .  

## Treuestufe

Das Dashboard `Retention health` zeigt das wiederholte Kaufverhalten Ihrer Benutzerbasis an.

Das Diagramm `Time between orders` zeigt die durchschnittliche und/oder mittlere verstrichene Zeit zwischen der ersten und zweiten Bestellung eines Benutzers, der zweiten und dritten Reihenfolge usw. Sie können [erwägen, diese Daten zur Konfiguration Ihrer E-Mail-Marketing-Kampagnen zu verwenden](http://blog.rjmetrics.com/acting-on-marketing-data-in-your-rjmetrics-online-dashboard/).

In der `Users by lifetime number of orders` -Grafik wird die Gesamtanzahl der Benutzer für jede Lebensdauer von Bestellungen aufgeführt, um einen allgemeinen Überblick über das Verhalten bei wiederholten Bestellungen zu erhalten.  

Das Diagramm `Repeat order probability` zeigt die Wahrscheinlichkeit an, dass ein Benutzer mit einer bestimmten Bestellnummer einen wiederholten Kauf tätigt. Um die Wahrscheinlichkeit zu sehen, mit der Kunden, die `x` Bestellungen getätigt haben, um `(x+1)` Bestellungen zu tätigen, einfach die Anzahl der Personen, die mindestens `(x+1)` Bestellungen getätigt haben, durch die Anzahl der Personen zu teilen, die mindestens `x` Bestellungen getätigt haben.

### Beispiel

Anzahl der Kunden, die während ihrer Lebensdauer einen Kauf getätigt haben: `90`

Anzahl der Kunden, die während ihrer Lebensdauer zwei Käufe getätigt haben: `30`

Anzahl der Kunden, die während ihrer Lebensdauer drei Käufe getätigt haben: `10`

In diesem Beispiel beträgt die Wiederholungsbestellwahrscheinlichkeit von Kunden, die während ihrer Lebensdauer einen Kauf getätigt haben, um einen zweiten Kauf zu tätigen: `(30 + 10) / (30+10+90) = 30.77%`.

## Wachstum von Kunden-LTV

Das Dashboard `Customer LTV growth` enthält eine Reihe von Diagrammen, die den durchschnittlichen Umsatz pro Benutzer ermitteln. Die Diagramme werden basierend auf dem durchschnittlichen Umsatz segmentiert, der innerhalb der ersten 30, 60, 90 oder 365 Tage nach der Registrierung generiert wird.  

Die untere Tabellenzeile zeigt, dass diese Durchschnittswerte segmentiert nach Akquise-Quellen oder demografischen Daten zeigen, welche Benutzergruppen im Laufe der Zeit den meisten Umsatz generieren.

## Produktleistung

Das Dashboard `Product Performance` enthält Diagramme, in denen die allgemeine Produktleistung dargestellt wird, indem die Anzahl der verkauften Artikel und der Umsatz nach Artikeln angezeigt und die leistungsstärksten Produkte ermittelt werden.

## Letzte Aktivität

Das Dashboard `Recent Activity` zeigt Leistungsdaten aus den letzten 30 Tagen an.

## Transaktionsstatus

Das Dashboard `Transaction Health` enthält Übersichtsdiagramme zu Umsatz, Bestellungen und durchschnittlichem Bestellwert. Diese Diagramme können nach Marketing-Kanälen, demografischen Daten oder speziellen Couponcodes segmentiert werden.

## Benutzer zum Targeting

Das Dashboard `Users to target` enthält Tabellen-Grafiken, die Benutzer mit gemeinsamen Kaufverhaltensweisen auflisten. Zu den Beispielen gehören:

* Liste der einmaligen Käufer, die vor `X` Monaten gekauft haben (die Sie möglicherweise reaktivieren möchten)

* Liste der wichtigsten Geldgeber (die Sie möglicherweise glücklich halten möchten)

* Liste der wichtigsten Geldgeber, die in den letzten `X` Tagen aktiv waren (die Sie möglicherweise belohnen möchten)

Mit Ihren Datenexport-Tools können Sie [E-Mail-Listen von Benutzern erstellen, die ähnliche Kaufverhaltensweisen für das Zielmarketing haben](http://blog.rjmetrics.com/creating-contact-lists-for-top-customers/).

## Benutzeraktivität

Das Dashboard `User activity` enthält Diagramme, die Benutzer nach verschiedenen Daten segmentieren, einschließlich Akquise-Quelle, demografischen Daten und durchschnittlicher Erstbestellung. Er enthält auch die Analyse der Benutzerkohorte, einschließlich des durchschnittlichen Gesamtumsatzes während der Lebensdauer nach dem Registrierungsmonat des Benutzers.

Das Diagramm `% of cohort members who have purchased` ist nützlich, da es das Konversionsverhältnis (von 0 bis 1) der Benutzer basierend auf dem Zeitpunkt der Registrierung anzeigt (jede Zeile stellt eine Kohorte von Benutzern dar). Er zeigt auch an, wann er seinen ersten Kauf tätigt (z. B. in Monat 1, 2, 3... nach der Registrierung). Dies kann zeigen, dass 10 % der Benutzer im Monat 1 aktiviert haben, während diese Zahl im Monat 2, 3, 4... zunimmt und sich später versteigern kann.

In der Regel werden die Zeilen in dieser Grafik nach einigen Zeiträumen horizontal. Dies weist darauf hin, dass nach diesem Zeitpunkt nur wenige weitere Kohortenmitglieder organisch konvertieren - die meisten Benutzer, die einen Kauf tätigen werden, haben dies bereits getan. An dieser Stelle ist es höchst unwahrscheinlich, dass diese Mitglieder ohne Eingreifen in Käufer konvertieren. [Mit benutzerdefinierten Promotions oder zielgerichteten E-Mails auf sie zuzugreifen ist eine Methode, mit der die Konversion dieser Population mit geringem Risiko beschleunigt werden kann.](http://blog.rjmetrics.com/acting-on-marketing-data-in-your-rjmetrics-online-dashboard/)
