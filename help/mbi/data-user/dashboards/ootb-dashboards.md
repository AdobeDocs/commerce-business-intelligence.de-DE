---
title: Enthaltene Dashboards
description: Erfahren Sie, wie Sie den Zustand wichtiger Metriken wie Benutzerlebensdauerumsatz, Anzahl der Wiederholungskäufe und mehr überprüfen können, um so eine solide Grundlage für die zukünftige Untersuchung zu schaffen.
exl-id: f50fc417-e5d4-401c-9baa-cda1468196a2
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 3a7423c9dd0f957b77baa27b3447a715caad017b
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 0%

---

# Enthaltene Dashboards

[!DNL Adobe] bietet `eCommerce` und `SaaS` Starter-Pakete an. Diese von Adobe-Analysten erstellten Pakete enthalten eine benutzerdefinierte Reihe von Dashboards und Berichten für Ihren Datensatz. Die in diesen Paketen enthaltenen Analysen ermöglichen es Ihnen, den Zustand wesentlicher Metriken wie den Lebensdauerumsatz der Benutzenden, die Anzahl der Wiederholungskäufe und mehr zu überprüfen und so eine solide Grundlage für die zukünftige Exploration zu schaffen.

>[!NOTE]
>
>Die Verfügbarkeit einiger Dashboards hängt von Ihrem Datensatz ab.

Wenn Sie Fragen haben oder daran interessiert sind, ein Paket zu Ihrem Konto hinzuzufügen, senden Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de), um Hilfe zu erhalten.

## Überblick für Führungskräfte

Das `executive overview` Dashboard wird aus Diagrammen erstellt, die in anderen Dashboards vorhanden sind. Dieses Dashboard bietet einen allgemeinen Überblick über Ihre Daten und enthält Diagramme, die täglich überprüft werden, während andere Dashboards detailliertere Informationen enthalten. Zunächst wird es in jedem Konto als Standard-Dashboard festgelegt.

Ein allgemeiner Satz von Diagrammen ist für Sie enthalten. Adobe empfiehlt, dieses Dashboard an Ihre Anforderungen anzupassen, indem Sie andere Diagramme hinzufügen, die Sie am häufigsten verwenden.

## Kohortenanalyse

Das `cohort analysis`-Dashboard enthält eine Reihe von Diagrammen, die das durchschnittliche Wachstum des Benutzerumsatzes während der Lebensdauer und das inkrementelle Umsatzwachstum gruppiert nach Registrierungskohorten zeigen. So lässt sich feststellen, ob der Kundenlebenszeitwert (LTV), der Wert eines Kunden für ein Unternehmen, im Laufe der Zeit steigt, und es lassen sich Trends rund um das LTV-Wachstum erkennen. Standardmäßig werden *alle registrierten Benutzer (Käufer und Nicht-Käufer) bei der Berechnung* durchschnittlichen LTV berücksichtigt - siehe [Thema Kohortenanalyse](../../data-analyst/dev-reports/cohort-rpt-bldr.md).

Dieses Dashboard kann auch Kohortendiagramme enthalten, die den Lebenszeitumsatz von Benutzenden aus einer bestimmten Akquisequelle, einem bestimmten Kanal oder einer bestimmten demografischen Gruppe (z. B. New York oder Kalifornien) analysieren. Auf diese Weise können Sie LTV für bestimmte Segmente Ihrer Benutzerbasis analysieren und sehen, ob die eine oder andere Gruppe im Laufe der Zeit höhere LTV-Werte erzielt.

Weitere Informationen zu Kohorten finden Sie unter [Durchführen einer Kohortenanalyse](../../data-analyst/dev-reports/cohort-rpt-bldr.md).

Wenn Sie derzeit keine Quelle für die Benutzerakquise verfolgen, lesen Sie den Abschnitt [Übersicht über Source-Daten zur Benutzerakquise &#x200B;](../../data-analyst/analysis/google-track-user-acq.md).

## E-Mail-Zusammenfassung

Das `Email Summary`-Dashboard enthält einen Beispielsatz von Diagrammen, die in einer automatisierten täglichen E-Mail-Zusammenfassung verwendet werden können. Weitere Informationen [&#x200B; Konfigurieren von E-Mail](../../data-user/export-data/email-summaries.md)Zusammenfassungen finden Sie unter „Erstellen automatisierter E-Mail-Zusammenfassungen“.  

## Aufbewahrungszustand

Das `Retention health`-Dashboard zeigt das Verhalten beim wiederholten Kauf Ihres Benutzerstamms an.

Das `Time between orders` Diagramm zeigt die durchschnittliche und/oder mediane Zeit zwischen der ersten und zweiten, zweiten und dritten Ordnung usw. eines Benutzers. Sie können diese Daten verwenden, um Ihre E-Mail-Marketing-Kampagnen zu konfigurieren.

Das `Users by lifetime number of orders` Diagramm listet die Gesamtzahl der Benutzer für jede lebenslange Anzahl von Bestellungen auf, um einen allgemeinen Überblick über das Verhalten bei wiederholten Käufen zu geben.  

Das `Repeat order probability` zeigt die Wahrscheinlichkeit, dass ein Benutzer mit einer bestimmten Bestellnummer einen wiederholten Kauf tätigt. Um die Wahrscheinlichkeit von Kunden zu sehen, die `x` Bestellungen getätigt haben, um `(x+1)` Bestellungen zu tätigen, teilen Sie einfach die Anzahl der Personen, die mindestens `(x+1)` Einkäufe getätigt haben, durch die Anzahl der Personen, die mindestens `x` Einkäufe getätigt haben.

### Beispiel

Anzahl der Kunden, die im Laufe ihres Lebens einen Kauf getätigt haben: `90`

Anzahl der Kunden, die im Laufe ihres Lebens zwei Käufe getätigt haben: `30`

Anzahl der Kunden, die im Laufe ihres Lebens drei Käufe getätigt haben: `10`

In diesem Beispiel ist die Wahrscheinlichkeit der Wiederholungsbestellung von Kunden, die einen Kauf im Laufe ihres Lebens getätigt haben, um einen zweiten Kauf zu tätigen, `(30 + 10) / (30+10+90) = 30.77%`.

## Kunden-LTV-Wachstum

Das `Customer LTV growth`-Dashboard enthält eine Reihe von Diagrammen, die den durchschnittlichen Umsatz pro Benutzer ermitteln. Die Diagramme sind auf der Grundlage des durchschnittlichen Umsatzes segmentiert, der entweder innerhalb der ersten 30, 60, 90 oder 365 Tage nach der Registrierung generiert wird.  

Die untere Zeile der Diagramme zeigt, dass diese Durchschnittswerte nach Akquisequellen oder Demographien segmentiert sind, um zu zeigen, welche Benutzergruppen im Laufe der Zeit den meisten Umsatz generieren.

## Produktleistung

Das `Product Performance`-Dashboard enthält Diagramme, die die allgemeine Produktleistung anzeigen, indem sie die Anzahl der verkauften Artikel und den Umsatz nach Artikel anzeigen und die leistungsstärksten Produkte identifizieren.

## Letzte Aktivität

Das `Recent Activity`-Dashboard zeigt Leistungsdaten für die letzten 30 Tage an.

## Transaktionsstatus

Das `Transaction Health`-Dashboard enthält Übersichtsdiagramme mit Umsatz, Bestellungen und durchschnittlichem Bestellwert. Diese Diagramme können nach Marketing-Kanälen, Demografie oder speziellen Couponcodes segmentiert werden.

## Zielgruppe der Benutzer

Das `Users to target`-Dashboard enthält tabellenartige Diagramme, in denen Benutzende mit bestimmten gemeinsamen Kaufverhaltensweisen aufgelistet sind. Einige Beispiele:

* Liste der einmaligen Käufer, die vor `X` Monaten gekauft haben (die Sie möglicherweise reaktivieren möchten)

* Liste der Top-Spender (die Sie vielleicht glücklich halten möchten)

* Liste der Top-Spender, die in den letzten `X` Tagen aktiv waren (wen Sie möglicherweise belohnen möchten)

Sie können Ihre Datenexportwerkzeuge verwenden, um E-Mail-Listen von Benutzern mit ähnlichem Kaufverhalten für Target-Marketing zu erstellen.

## Benutzeraktivität

Das `User activity`-Dashboard enthält Diagramme, die Benutzer nach verschiedenen Daten segmentieren, einschließlich der Akquise, der Demografie und der durchschnittlichen Erstbestellung. Sie enthält auch eine Analyse der Benutzergruppen, einschließlich des durchschnittlichen Gesamtumsatzes während der Lebensdauer nach Registrierungsmonat der Benutzer.

Das `% of cohort members who have purchased` Diagramm ist nützlich, da es das Konversionsverhältnis (von 0 bis 1) von Benutzern basierend auf dem Zeitpunkt ihrer Registrierung anzeigt (jede Zeile stellt eine Kohorte von Benutzern dar). Es zeigt auch an, wann sie ihren ersten Kauf tätigen (z. B. in Monat 1, 2, 3… nach der Registrierung). Dies kann zeigen, dass 10 % der Benutzenden in Monat 1 aktiviert wurden, während diese Zahl in Monat 2, 3, 4… zunimmt und später ein Plateau erreicht werden kann.

In der Regel werden die Linien in diesem Diagramm nach einiger Zeit horizontal. Dies deutet darauf hin, dass nach diesem Zeitpunkt nur wenige zusätzliche Kohortenmitglieder organisch konvertieren - die meisten Benutzer, die einen Kauf tätigen werden, haben dies bereits getan. Zum gegenwärtigen Zeitpunkt ist es höchst unwahrscheinlich, dass diese Mitglieder ohne Eingreifen in Käufer übergehen. Sie mit benutzerdefinierten Promotions oder zielgerichteten E-Mails zu kontaktieren, ist eine risikoarme Methode, um die Konversion dieser Population zu starten.
