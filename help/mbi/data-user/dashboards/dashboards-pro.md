---
title: Vordefinierte Dashboards
description: Erfahren Sie mehr über vordefinierte Dashboards, um Einblicke in Ihr Unternehmen zu erhalten.
exl-id: fe61c92e-de87-4317-96d7-01d2a9846bf9
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '2245'
ht-degree: 0%

---

# Vordefinierte Dashboards

[!DNL MBI] enthält vordefinierte Dashboards, um Einblicke in Ihr Unternehmen zu erhalten. Mit Dashboards können Sie die Konsistenz wichtiger Metriken überprüfen, z. B. den Umsatz während der Lebensdauer der Benutzer, die Anzahl wiederholter Käufe, die wichtigsten über einen bestimmten Zeitraum gekauften Produkte und mehr. Diese vorkonfigurierten Dashboards wurden erstellt, um Sie bei fundierten Geschäftsentscheidungen zu unterstützen.

>[!NOTE]
>
>Der Zugriff auf diese Dashboards hängt von Ihrem Kontotyp und Ihrer Zugriffsebene ab. Wenn diese Dashboards nicht angezeigt werden, wenden Sie sich an [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).

## Berichtverfügbarkeit

Für `Customers` und `Executive Summary` -Dashboards können Sie einige Berichte nur in Abhängigkeit von der Checkout-Konfiguration Ihres Stores herunterladen. Insbesondere, wenn Ihr Store das Auschecken von Gast zulässt oder das Auschecken von Gast nicht zulässt.

## Kunden (Gastkasse erlaubt)

Das Dashboard Kunden (Gastkasse erlaubt) enthält Informationen zu Ihrer Kundenbasis, z. B. zu ihrem Kaufverhalten. Dieses Dashboard kann Ihnen dabei helfen, die Kundenbindung zu verbessern und festzustellen, welche Kunden den höchsten Umsatz erzielen.

### Berichte

| Name | Beschreibung |
|---|---|
| `Orders by New Customers (Past 30 Days)` | Bestellungen von Kunden, die noch nie eine Bestellung aufgegeben haben, in den letzten 30 Tagen. |
| `Orders by Existing Customers (Past 30 Days)` | Bestellungen von Kunden, die in den letzten 30 Tagen mindestens eine Bestellung aufgegeben haben. |
| `Total Unique Customers (Past 30 Days)` | Anzahl der Unique Customers, die in den letzten 30 Tagen Bestellungen aufgegeben haben. |
| `Orders by New vs Existing Customers` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen im Vergleich zu Kunden mit mindestens einer vorherigen Bestellung. |
| `Subsequent Order Probability (All Time)` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere aufgeben. |
| `% of Customers with Multiple Orders (All Time)` | Prozent aller Kunden, die mehr als eine Bestellung aufgegeben haben. |
| `Median Time Between Orders (All Time)` | Mediane Zeit, die jeder Kunde zwischen der Bestellung und der nächsten benötigt. |
| `Subsequent Order Probability` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine weitere aufgeben, aufgeschlüsselt nach Bestellnummer (d. h. Prozentsatz der Kunden mit einer Bestellung, die eine zweite aufgeben, Prozent mit zwei, die eine dritte aufgeben usw.). |
| `Time Between Orders` | Die durchschnittliche und mittlere Zeit, die Kunden zwischen Bestellungen nehmen, aufgegliedert nach Bestellnummer (d. h. die Zeit zwischen Bestellungen 1 und 2, 2 und 3 usw.). |
| `Number of Customers - Lifetime Orders` | Für eine bestimmte Anzahl von Bestellungen, die während der Lebensdauer eines Kunden aufgegeben werden, stellt die Anzahl der Kunden, die so viele Bestellungen aufgegeben haben, und der Prozentsatz des gesamten Kundenstamms dar, den diese Zahl darstellt. |
| `One-Time Customers who Bought 3-6 Months Ago` | Kunden, die vor drei bis sechs Monaten ihren ersten Kauf getätigt haben. |
| `Avg LTV by First Order` | Vergleicht den kumulativen durchschnittlichen Umsatz der Kundenlebensdauer über Kohorten hinweg. Kohorten werden durch den Monat definiert, in dem ein Kunde zum ersten Mal einen Kauf tätigte. Beispiel: eine `Jan 2020` Die Kohorte zeigt die kumulative durchschnittliche LTV-Rate für Kunden, die zum ersten Mal im Januar 2020 gekauft wurden. |
| `Customer's First 30 Day vs Lifetime Revenue` | Vergleich des durchschnittlichen Umsatzes von Kunden in den 30 Tagen nach ihrem ersten Kauf im Vergleich zur gesamten Lebensdauer. Jede Blase entspricht einer Versandregion, und die Größe jeder Blase entspricht der Anzahl der Kunden, die aus dieser Region erworben wurden. |

## Kunden (kein Gast-Checkout erlaubt)

Das Dashboard Kunden (kein Gastkauf erlaubt) enthält Informationen zu Ihrer Kundenbasis, z. B. zu ihrem Kaufverhalten und Konversionen von Kontoregistrierungen zu Bestellplatzierungen. Dieses Dashboard kann Ihnen dabei helfen, die Kundenbindung zu verbessern und festzustellen, welche Kunden den höchsten Umsatz erzielen.

### Berichte

| Name | Beschreibung |
|---|---|
| Kontoregistrierung (seit 30 Tagen) | Die Anzahl der Personen, die sich in den letzten 30 Tagen für ein Konto bei Ihrem Geschäft angemeldet haben. |
| Registrierte Konten (letzte 30 Tage) mit 1 oder mehr Bestellungen | Die Anzahl der Personen, die sich in den letzten 30 Tagen bei Ihrem Geschäft für ein Konto angemeldet und auch mindestens eine Bestellung aufgegeben haben. |
| Konversion von der Registrierung in die erste Bestellung (vergangene 30 Tage) | Prozentsatz der Konten, die in den letzten 30 Tagen registriert wurden und eine Bestellung aufgegeben haben. |
| % Konversion von der Registrierung in die erste Bestellung | Prozentsatz der registrierten Konten, die eine Bestellung getätigt haben, nach Monat der Registrierung. |
| Bestellungen neuer und bestehender Kunden | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen im Vergleich zu Kunden mit mindestens einer vorherigen Bestellung. |
| Nachfolgende Bestellwahrscheinlichkeit (alles Zeit) | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere aufgeben. |
| % der Kunden mit mehreren Bestellungen (Gesamtdauer) | Prozent aller Kunden, die mehr als eine Bestellung aufgegeben haben. |
| Mediane Zeit zwischen Bestellungen (gesamte Zeit) | Mediane Zeit, die jeder Kunde zwischen der Bestellung und der nächsten benötigt. |
| Nachfolgende Bestellwahrscheinlichkeit | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine weitere aufgeben, aufgeschlüsselt nach Bestellnummer (d. h. Prozentsatz der Kunden mit einer Bestellung, die eine zweite aufgeben, Prozent mit zwei, die eine dritte aufgeben usw.). |
| Zeit zwischen Bestellungen | Die durchschnittliche und mittlere Zeit, die Kunden zwischen Bestellungen nehmen, aufgegliedert nach Bestellnummer (d. h. die Zeit zwischen Bestellungen 1 und 2, 2 und 3 usw.). |
| Anzahl der Kunden - Bestellungen während der Lebensdauer | Für eine bestimmte Anzahl von Bestellungen, die während der Lebensdauer eines Kunden aufgegeben werden, stellt die Anzahl der Kunden, die so viele Bestellungen aufgegeben haben, und der Prozentsatz des gesamten Kundenstamms dar, den diese Zahl darstellt. |
| Einmalige Kunden, die vor 3-6 Monaten gekauft haben | Kunden, die vor drei bis sechs Monaten ihren ersten Kauf getätigt haben. |
| Avg LTV by First Order | Vergleicht den kumulativen durchschnittlichen Umsatz der Kundenlebensdauer über Kohorten hinweg. Kohorten werden durch den Monat definiert, in dem ein Kunde zum ersten Mal einen Kauf tätigte. Beispielsweise zeigt eine Kohorte vom Januar 2020 die kumulative durchschnittliche LTV-Rate für Kunden, deren erster Kauf im Januar 2020 erfolgte. |
| Umsatz der ersten 30 Tage des Kunden im Vergleich zum Lebenszeitumsatz | Vergleich des durchschnittlichen Umsatzes von Kunden in den 30 Tagen nach ihrem ersten Kauf im Vergleich zur gesamten Lebensdauer. Jede Blase entspricht einer Versandregion, und die Größe jeder Blase entspricht der Anzahl der Kunden, die aus dieser Region erworben wurden. |

## Zusammenfassung (Gastkasse erlaubt)

Das Dashboard &quot;Executive Summary&quot;(Gastkasse erlaubt) gibt Ihnen einen Überblick darüber, wie das Unternehmen im Hinblick auf Bestellungen und Umsatz vorgeht. Dieses Dashboard wurde für Führungskräfte entwickelt, um ein allgemeines Verständnis der Geschäftsleistung zu erhalten, kann aber auch für andere Benutzer aufschlussreich sein.

### Berichte

| Name | Beschreibung |
|---|---|
| Umsatz (aktueller Monat) | Der Umsatz, der von Ihrem Store für den aktuellen Monat generiert wurde. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| Umsatz (in den letzten 6 Monaten nach Tag) | Gesamttäglicher Umsatz, überlagert mit dem durchschnittlichen Tagesumsatz der letzten sieben Tage. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| Umsatzänderung in % (MoM MTD) | Vergleich des Umsatzes im aktuellen Monat (bisher) mit dem gleichen Anteil im Vormonat. |
| Umsatz neuer und bestehender Kunden (aktueller Monat) | Umsatz für den aktuellen Monat (bisher), der neuen (erstmaligen) Kunden zugeordnet wurde, gegenüber bestehenden Kunden (Platzierung einer zweiten oder späteren Bestellung). |
| Durchschnittlicher Bestellwert (aktueller Monat) | Durchschnittlicher Tageswert der im aktuellen Monat aufgegebenen Bestellungen (bisher). Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| Bestellungen (aktueller Monat) | Die Anzahl der Bestellungen, die in Ihrem Store für den aktuellen Monat aufgegeben wurden (bisher). |
| Änderung der Bestellungen in % (MoM MTD) | Vergleich der Anzahl der Bestellungen für den aktuellen Monat (bisher) mit dem gleichen Anteil des Vormonats. |
| Bestellungen neuer Kunden (aktueller Monat) | Bestellungen für den aktuellen Monat von Kunden, die noch nie eine Bestellung aufgegeben haben. |
| Bestellungen bestehender Kunden (aktueller Monat) | Bestellungen für den aktuellen Monat von Kunden, die zuvor mindestens eine Bestellung aufgegeben haben. |
| Bestellungen neuer und bestehender Kunden (aktuelles Jahr nach Woche) | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen im Vergleich zu Kunden mit mindestens einer vorherigen Bestellung für jede Woche des laufenden Jahres (bisher). |

## Zusammenfassung (kein Gast-Checkout erlaubt)

Das Dashboard &quot;Executive Summary&quot;(kein Gast-Checkout erlaubt) gibt Ihnen einen kurzen Überblick darüber, wie das Unternehmen in Bezug auf Bestellungen, Umsatz und Kontoregistrierungen vorgeht. Dieses Dashboard wurde für Führungskräfte entwickelt, um ein allgemeines Verständnis der Geschäftsleistung zu erhalten, kann aber auch für andere Benutzer aufschlussreich sein.

### Berichte

| Name | Beschreibung |
|---|---|
| Umsatz (aktueller Monat) | Der Umsatz, der in diesem Monat von Ihrem Store generiert wurde. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| Umsatz (in den letzten 6 Monaten nach Tag) | Gesamttäglicher Umsatz, überlagert mit dem durchschnittlichen Tagesumsatz der letzten sieben Tage. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| Umsatzänderung in % (MoM MTD) | Vergleich des Umsatzes bis jetzt in diesem Monat mit dem gleichen Anteil im Vormonat. |
| Umsatz neuer und bestehender Kunden (aktueller Monat) | Umsatz für den aktuellen Monat (bisher), der neuen (erstmaligen) Kunden zugeordnet wurde, gegenüber bestehenden Kunden (Platzierung einer zweiten oder späteren Bestellung). |
| Durchschnittlicher Bestellwert (aktueller Monat) | Durchschnittlicher Tageswert der im aktuellen Monat aufgegebenen Bestellungen (bisher). Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| Bestellungen (aktueller Monat) | Die Anzahl der Bestellungen, die in Ihrem Store für den aktuellen Monat aufgegeben wurden (bisher). |
| Änderung der Bestellungen in % (MoM MTD) | Vergleich der Anzahl der Bestellungen für den aktuellen Monat (bisher) mit dem gleichen Anteil des Vormonats. |
| Kontoregistrierungen (aktueller Monat) | Die Anzahl der neu registrierten Konten in diesem Monat. |
| Konversion in % von der Registrierung in die erste Bestellung (aktueller Monat) | Der Prozentsatz der Konten, die in diesem Monat bisher registriert wurden und eine Bestellung aufgegeben haben. |
| Konversion von der Registrierung in die erste Bestellung (aktuelles Jahr nach Woche) | Der Prozentsatz der Konten, die bis jetzt in diesem Jahr jede Woche registriert wurden und eine Bestellung aufgegeben haben. |

## Bestellungen

Das Dashboard &quot;Bestellungen&quot;bietet Einblicke in das Transaktionsvolumen von Bestellungen, ihren Status, die verwendeten Couponcodes, den erzielten Umsatz und die verwendeten Zahlungsmethoden. Sie können beispielsweise den Ausführungsprozess verfolgen und sicherstellen, dass keine Probleme oder Engpässe auftreten.

>[!NOTE]
>
>Die Berichte in diesem Dashboard stehen für Konten zur Verfügung, die mit Stores verbunden sind, die beide Konfigurationstypen aufweisen (Gastkasse, kein Gast-Checkout).

### Berichte

| Name | Beschreibung |
|---|---|
| Bestellungen (letzte 30 Tage) | Die Anzahl der Bestellungen, die in den letzten 30 Tagen bei Ihrem Geschäft aufgegeben wurden. |
| Umsatz (vergangene 30 Tage) | Der Umsatz, der von Ihrem Store in den letzten 30 Tagen generiert wurde. Umsatz ist definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| Durchschnittlicher Bestellwert (vergangene 30 Tage) | Durchschnittlicher Wert der Bestellungen der letzten 30 Tage. Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| Bestellungen | Die Anzahl der Bestellungen, die jeden Monat in Ihrem Geschäft aufgegeben werden. |
| Einnahmen nach Zahlungsmethode | Der Umsatz, der von Ihrem Store generiert wurde, aufgeteilt nach Zahlungsmethode. Umsatz ist definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| AOV von neuen und bestehenden Kunden | Durchschnittlicher Monatswert der in Ihrem Geschäft getätigten Bestellungen, aufgeteilt nach Bestellungen von Kunden ohne vorherige Bestellungen, gegenüber Kunden mit mindestens einer vorherigen Bestellung. Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| % Bestellungen nach Status (vergangene 30 Tage) | Prozent der Bestellungen von jedem Tag in den letzten 30 Tagen, die sich derzeit in jedem Bestellstatus befinden. |
| Unvollständige Bestellungen (vor mehr als 1 Tag erstellt) | Liste aller vor mehr als einem Tag aufgegebenen Bestellungen, die noch immer unvollständig sind (weder storniert noch abgeschlossen). |
| Bestellungen pro Stunde (vergangene 7 Tage) | Bestellvolumen nach Tag und Stunde. |
| Umsatzdetails (vergangene 30 Tage) | Tägliche Aufschlüsselung des Umsatzes für die letzten 30 Tage in alle Komponenten des Gesamtumsatzwerts. |
| Bestelldetails nach Couponcode (vergangene 30 Tage) | Für jeden Gutscheincode, den Ihr Store anbietet, geben Sie an, wie dieser Couponcode verwendet wurde und welche Gutscheincodes in den letzten 30 Tagen zurückgegeben wurden. |
| % Bestellungen mit Coupon (vergangene 30 Tage) | Der Prozentsatz der Bestellungen, die in den letzten 30 Tagen mit einem Coupon bestellt wurden, im Vergleich zu den Bestellungen, die nicht getätigt wurden. |

## Produkte

Das Produkt-Dashboard zeigt die allgemeine Produktleistung in Bezug auf bestellte Produkte, ihren Brutto-Merchandise-Wert (GMV) sowie die am häufigsten gekauften und erstatteten Produkte an. Es kann Ihnen dabei helfen, Käufe und Renditen auszugleichen und den Erfolg und die Beliebtheit des Produkts zu bestimmen. Ihr Geschäft muss [zur Rückverfolgung der Erstattungen konfiguriert wurde](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/store-credit/credit-configure.html) für diese Diagramme.

>[!NOTE]
>
>Die Berichte in diesem Dashboard stehen für Konten zur Verfügung, die mit Stores verbunden sind, die beide Konfigurationstypen aufweisen (Gastkasse, kein Gast-Checkout).

### Berichte

| Name | Beschreibung |
|---|---|
| GMV (vergangene 30 Tage) | Der Bruttowarenwert aller in den letzten 30 Tagen verkauften Produkte. GMV ist definiert als die bestellte Menge multipliziert mit dem Basispreis für jedes Produkt. |
| % GMV (vergangene 30 Tage) rückerstattet | Prozent der GMV für Produkte, die in den letzten 30 Tagen gekauft wurden und zu einer Rückerstattung führten. |
| Bestellte Produktmenge (vergangene 30 Tage) | Gesamtbetrag der in den letzten 30 Tagen bestellten Artikel. |
| In % gekaufte Produkte (vergangene 30 Tage) rückerstattet | Prozentsatz der Artikel, die in den letzten 30 Tagen gekauft wurden und zu einer Rückerstattung führten. |
| Bruttowert der Waren | Der Bruttowertwert aller verkauften Produkte nach Monat. GMV ist definiert als die bestellte Menge multipliziert mit dem Basispreis für jedes Produkt. |
| Käufe vs. Erstattungssatz pro Produkt (vergangene 30 Tage) | Für jedes Produkt wird die Gesamtzahl der bestellten Artikel in den letzten 30 Tagen mit der Erstattungsquote verglichen. Die Größe jeder Blase entspricht der Erstattungsrate. |
| Details zur Produktleistung (letzte 30 Tage) | Detaillierte Angaben zu den Verkäufen und den anschließenden Erstattungen in den letzten 30 Tagen, nach Produkt-SKU und Produktname. |
| Häufig gekaufte Produkte nach GMV (letzte 30 Tage) | In den letzten 30 Tagen verkaufte Produkte, die den meisten Umsatz brachten (Top 10). |
| Top-erstattete Produkte nach GMV (vergangene 30 Tage) | Produkte, die in den letzten 30 Tagen gekauft wurden und die am meisten GMV aufgrund von Erstattungen verloren haben (Top 10). |
| Häufigste gekaufte Produkte nach Menge (vergangene 30 Tage) | Produkte, die in den letzten 30 Tagen in der größten Zahl (Top 10) verkauft wurden. |
| Top erstattete Produkte nach Menge (vergangene 30 Tage) | Produkte, die in den letzten 30 Tagen gekauft wurden, was zu der größten erstatteten Menge führte (Top 10). |
