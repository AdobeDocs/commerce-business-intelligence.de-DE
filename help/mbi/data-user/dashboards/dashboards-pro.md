---
title: Vordefinierte Dashboards
description: Erfahren Sie mehr über vordefinierte Dashboards, um Einblicke in Ihr Unternehmen zu erhalten.
exl-id: fe61c92e-de87-4317-96d7-01d2a9846bf9
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1950'
ht-degree: 0%

---

# Vordefinierte Dashboards

[!DNL Adobe Commerce Intelligence] enthält vordefinierte Dashboards, um Einblicke in Ihr Geschäft zu bieten. Mit Dashboards können Sie die Konsistenz wichtiger Metriken überprüfen, z. B. den Umsatz während der Lebensdauer der Benutzer, die Anzahl wiederholter Käufe, die wichtigsten über einen bestimmten Zeitraum gekauften Produkte und mehr. Diese vorkonfigurierten Dashboards wurden erstellt, um Sie bei fundierten Geschäftsentscheidungen zu unterstützen.

>[!NOTE]
>
>Der Zugriff auf diese Dashboards hängt von Ihrem Kontotyp und Ihrer Zugriffsebene ab. Wenn diese Dashboards nicht angezeigt werden, wenden Sie sich an [support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

## Berichtverfügbarkeit

Für die Dashboards `Customers` und `Executive Summary` sind einige Berichte nur in Abhängigkeit von der Checkout-Konfiguration Ihres Stores verfügbar. Insbesondere, wenn Ihr Store das Auschecken von Gast erlaubt oder das Auschecken von Gast nicht zulässt.

## Kunden (Gastkasse erlaubt)

Das Dashboard Kunden (Gastkasse erlaubt) enthält Informationen zu Ihrer Kundenbasis, z. B. zu ihrem Kaufverhalten. Dieses Dashboard kann Ihnen dabei helfen, die Kundenbindung zu verbessern und festzustellen, welche Kunden den höchsten Umsatz erzielen.

### Berichte

| Name | Beschreibung |
|---|---|
| `Orders by New Customers (Past 30 Days)` | Bestellungen von Kunden, die noch nie eine Bestellung aufgegeben haben, in den letzten 30 Tagen. |
| `Orders by Existing Customers (Past 30 Days)` | Bestellungen von Kunden, die in den letzten 30 Tagen mindestens eine Bestellung aufgegeben haben. |
| `Total Unique Customers (Past 30 Days)` | Anzahl der Unique Customers, die in den letzten 30 Tagen Bestellungen aufgegeben haben. |
| `Orders by New vs Existing Customers` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen im Vergleich zu Kunden mit mindestens einer vorherigen Bestellung. |
| `Subsequent Order Probability (All Time)` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere platzieren. |
| `% of Customers with Multiple Orders (All Time)` | Prozent aller Kunden, die mehr als eine Bestellung aufgegeben haben. |
| `Median Time Between Orders (All Time)` | Mittlere Zeit, die jeder Kunde zwischen der Bestellung und der nächsten benötigt. |
| `Subsequent Order Probability` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere Bestellung aufgeben, aufgeschlüsselt nach Bestellnummer. Das heißt, der Prozentsatz der Kunden mit einer Bestellung, die eine Sekunde aufgeben, der Prozentsatz mit zwei, die eine dritte platzieren usw. |
| `Time Between Orders` | Die durchschnittliche und mittlere Zeit, die Kunden zwischen Bestellungen nehmen, aufgegliedert nach Bestellnummer (d. h. die Zeit zwischen Bestellungen 1 und 2, 2 und 3 usw.). |
| `Number of Customers - Lifetime Orders` | Für eine bestimmte Anzahl von Bestellungen, die während der Lebensdauer eines Kunden aufgegeben werden, stellt die Anzahl der Kunden, die so viele Bestellungen aufgegeben haben, und der Prozentsatz des gesamten Kundenstamms dar, den diese Zahl darstellt. |
| `One-Time Customers who Bought 3-6 Months Ago` | Kunden, die vor drei bis sechs Monaten ihren ersten Kauf getätigt haben. |
| `Avg LTV by First Order` | Vergleicht den kumulativen durchschnittlichen Umsatz der Kundenlebensdauer über Kohorten hinweg. Kohorten werden durch den Monat definiert, in dem ein Kunde zum ersten Mal einen Kauf tätigte. Beispielsweise zeigt eine Kohorte mit dem Wert &quot;`Jan 2020`&quot;die kumulative durchschnittliche LTV-Wiedergabe für Kunden, deren erster Kauf im Januar 2020 erfolgte. |
| `Customer's First 30 Day vs Lifetime Revenue` | Vergleich des durchschnittlichen Umsatzes von Kunden in den 30 Tagen nach ihrem ersten Kauf im Vergleich zur gesamten Lebensdauer. Jede Blase entspricht einer Versandregion, und die Größe jeder Blase entspricht der Anzahl der Kunden, die aus dieser Region erworben wurden. |

## Kunden (kein Gast-Checkout erlaubt)

Das Dashboard Kunden (kein Gastkauf erlaubt) enthält Informationen zu Ihrer Kundenbasis, z. B. zu ihrem Kaufverhalten und Konversionen von Kontoregistrierungen zu Bestellplatzierungen. Dieses Dashboard kann Ihnen dabei helfen, die Kundenbindung zu verbessern und festzustellen, welche Kunden den höchsten Umsatz erzielen.

### Berichte

| Name | Beschreibung |
|---|---|
| `Account Registration (Past 30 Days)` | Die Anzahl der Personen, die sich in den letzten 30 Tagen für ein Konto bei Ihrem Geschäft angemeldet haben. |
| `Accounts Registered (Past 30 Days) with 1 or More Orders` | Die Anzahl der Personen, die sich in den letzten 30 Tagen bei Ihrem Geschäft für ein Konto angemeldet und auch mindestens eine Bestellung aufgegeben haben. |
| `% Conversion from Registration to First Order (Past 30 Days)` | Prozentsatz der Konten, die in den letzten 30 Tagen registriert wurden und eine Bestellung aufgegeben haben. |
| `% Conversion from Registration to First Order` | Prozentsatz der registrierten Konten, die eine Bestellung getätigt haben, nach Monat der Registrierung. |
| `Orders by New vs Existing Customers` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen im Vergleich zu Kunden mit mindestens einer vorherigen Bestellung. |
| `Subsequent Order Probability (All Time)` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere platzieren. |
| `% of Customers with Multiple Orders (All Time)` | Prozent aller Kunden, die mehr als eine Bestellung aufgegeben haben. |
| `Median Time Between Orders (All Time)` | Mittlere Zeit, die jeder Kunde zwischen der Bestellung und der nächsten benötigt. |
| `Subsequent Order Probability` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere platzieren, aufgeschlüsselt nach Auftragsnummer. Das heißt, Prozent der Kunden mit einer Bestellung, die eine Sekunde aufgeben, Prozent mit zwei, die eine dritte platzieren usw. |
| `Time Between Orders` | Die durchschnittliche und mittlere Zeit, die Kunden zwischen Bestellungen nehmen, aufgegliedert nach Bestellnummer (d. h. die Zeit zwischen Bestellungen 1 und 2, 2 und 3 usw.). |
| `Number of Customers - Lifetime Orders` | Für eine bestimmte Anzahl von Bestellungen, die während der Lebensdauer eines Kunden aufgegeben werden, stellt die Anzahl der Kunden, die so viele Bestellungen aufgegeben haben, und der Prozentsatz des gesamten Kundenstamms dar, den diese Zahl darstellt. |
| `One-Time Customers who Bought 3-6 Months Ago` | Kunden, die vor drei bis sechs Monaten ihren ersten Kauf getätigt haben. |
| `Avg LTV by First Order` | Vergleicht den kumulativen durchschnittlichen Umsatz der Kundenlebensdauer über Kohorten hinweg. Kohorten werden durch den Monat definiert, in dem ein Kunde zum ersten Mal einen Kauf tätigte. Beispielsweise zeigt eine Kohorte vom Januar 2020 die kumulative durchschnittliche LTV-Rate für Kunden, deren erster Kauf im Januar 2020 erfolgte. |
| `Customer's First 30 Day vs Lifetime Revenue` | Vergleich des durchschnittlichen Umsatzes von Kunden in den 30 Tagen nach ihrem ersten Kauf im Vergleich zur gesamten Lebensdauer. Jede Blase entspricht einer Versandregion, und die Größe jeder Blase entspricht der Anzahl der Kunden, die aus dieser Region erworben wurden. |

## Zusammenfassung (Gastkasse erlaubt)

Das Dashboard &quot;Executive Summary&quot;(Gastkasse erlaubt) gibt Ihnen einen Überblick darüber, wie das Unternehmen im Hinblick auf Bestellungen und Umsatz vorgeht. Dieses Dashboard wurde für Führungskräfte entwickelt, um ein allgemeines Verständnis der Geschäftsleistung zu erhalten, kann aber auch für andere Benutzer aufschlussreich sein.

### Berichte

| Name | Beschreibung |
|---|---|
| `Revenue (Current Month)` | Der Umsatz, der von Ihrem Store für den aktuellen Monat generiert wurde. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| `Revenue (Past 6 Months by Day)` | Gesamttäglicher Umsatz, überlagert mit dem durchschnittlichen Tagesumsatz der letzten sieben Tage. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| `% Change in Revenue (MoM MTD)` | Vergleich des Umsatzes im aktuellen Monat (bisher) mit dem gleichen Anteil im Vormonat. |
| `Revenue from New vs Existing Customers (Current Month)` | Umsatz für den aktuellen Monat (bisher), der neuen (erstmaligen) Kunden zugeordnet wurde, gegenüber bestehenden Kunden (Platzierung einer zweiten oder späteren Bestellung). |
| `Average Order Value (Current Month)` | Durchschnittlicher Tageswert der im aktuellen Monat aufgegebenen Bestellungen (bisher). Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| `Orders (Current Month)` | Die Anzahl der Bestellungen, die in Ihrem Store für den aktuellen Monat aufgegeben wurden (bisher). |
| `% Change in Orders (MoM MTD)` | Vergleich der Anzahl der Bestellungen für den aktuellen Monat (bisher) mit dem gleichen Anteil des Vormonats. |
| `Orders by New Customers (Current Month)` | Bestellungen für den aktuellen Monat von Kunden, die noch nie eine Bestellung aufgegeben haben. |
| `Orders by Existing Customers (Current Month)` | Bestellungen für den aktuellen Monat von Kunden, die zuvor mindestens eine Bestellung aufgegeben haben. |
| `Orders by New vs Existing Customers (Current Year by Week)` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen im Vergleich zu Kunden mit mindestens einer vorherigen Bestellung für jede Woche des laufenden Jahres (bisher). |

## Zusammenfassung (kein Gast-Checkout erlaubt)

Das Dashboard &quot;Executive Summary&quot;(kein Gast-Checkout erlaubt) gibt Ihnen einen kurzen Überblick darüber, wie das Unternehmen in Bezug auf Bestellungen, Umsatz und Kontoregistrierungen vorgeht. Dieses Dashboard wurde für Führungskräfte entwickelt, um ein allgemeines Verständnis der Geschäftsleistung zu erhalten, kann aber auch für andere Benutzer aufschlussreich sein.

### Berichte

| Name | Beschreibung |
|---|---|
| `Revenue (Current Month)` | Der Umsatz, der in diesem Monat von Ihrem Store generiert wurde. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| `Revenue (Past 6 Months by Day)` | Gesamttäglicher Umsatz, überlagert mit dem durchschnittlichen Tagesumsatz der letzten sieben Tage. In diesem Fall ist der Umsatz definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| `% Change in Revenue (MoM MTD)` | Vergleich des Umsatzes in diesem Monat mit dem gleichen Anteil im Vormonat. |
| `Revenue from New vs Existing Customers (Current Month)` | Umsatz für den aktuellen Monat (bisher), der neuen (erstmaligen) Kunden zugeordnet wurde, gegenüber bestehenden Kunden (Platzierung einer zweiten oder späteren Bestellung). |
| `Average Order Value (Current Month)` | Durchschnittlicher Tageswert der im aktuellen Monat aufgegebenen Bestellungen (bisher). Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| `Orders (Current Month)` | Die Anzahl der Bestellungen, die in Ihrem Store für den aktuellen Monat aufgegeben wurden (bisher). |
| `% Change in Orders (MoM MTD)` | Vergleich der Anzahl der Bestellungen für den aktuellen Monat (bisher) mit dem gleichen Anteil des Vormonats. |
| `Account Registrations (Current Month)` | Die Anzahl der neu registrierten Konten in diesem Monat. |
| `% Conversion from Registration to First Order (Current Month)` | Der Prozentsatz der Konten, die in diesem Monat bisher registriert wurden und eine Bestellung aufgegeben haben. |
| `% Conversion from Registration to First Order (Current Year by Week)` | Der Prozentsatz der Konten, die bis jetzt in diesem Jahr jede Woche registriert wurden und eine Bestellung aufgegeben haben. |

## Bestellungen

Das Dashboard &quot;Bestellungen&quot;bietet Einblicke in das Transaktionsvolumen von Bestellungen, ihren Status, die verwendeten Couponcodes, den erzielten Umsatz und die verwendeten Zahlungsmethoden. Sie können beispielsweise den Ausführungsprozess verfolgen und sicherstellen, dass es keine Probleme oder Engpässe gibt.

>[!NOTE]
>
>Die Berichte in diesem Dashboard stehen für Konten zur Verfügung, die mit Stores verbunden sind, die beide Konfigurationstypen aufweisen (Gastkasse, kein Gast-Checkout).

### Berichte

| Name | Beschreibung |
|---|---|
| `Orders (Past 30 Days)` | Die Anzahl der Bestellungen, die in den letzten 30 Tagen bei Ihrem Geschäft aufgegeben wurden. |
| `Revenue (Past 30 Days)` | Der Umsatz, der von Ihrem Store in den letzten 30 Tagen generiert wurde. Umsatz ist definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| `Average Order Value (Past 30 Days)` | Durchschnittlicher Wert der Bestellungen der letzten 30 Tage. Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| `Orders` | Die Anzahl der Bestellungen, die jeden Monat in Ihrem Geschäft aufgegeben werden. |
| `Revenue by Payment Method` | Der Umsatz, der von Ihrem Store generiert wurde, aufgeteilt nach Zahlungsmethode. Umsatz ist definiert als der Endpreis, der von einem Kunden für eine Bestellung gezahlt wird. |
| `AOV by New vs Existing Customers` | Durchschnittlicher Monatswert der in Ihrem Geschäft getätigten Bestellungen, aufgeteilt nach Bestellungen von Kunden ohne vorherige Bestellungen, gegenüber Kunden mit mindestens einer vorherigen Bestellung. Der Bestellwert ist definiert als der Endpreis, den ein Kunde bei einer Bestellung zahlt. |
| `% Orders by Status (Past 30 Days)` | Prozent der Bestellungen von jedem Tag in den letzten 30 Tagen, die sich derzeit in jedem Bestellstatus befinden. |
| `Incomplete Orders (Created more than 1 Day Ago)` | Liste aller vor mehr als einem Tag aufgegebenen Bestellungen, die noch immer unvollständig sind (weder storniert noch abgeschlossen). |
| `Orders Per Hour (Past 7 Days)` | Bestellvolumen nach Tag und Stunde. |
| `Revenue Details (Past 30 Days)` | Tägliche Aufschlüsselung des Umsatzes für die letzten 30 Tage in alle Komponenten des Gesamtumsatzwerts. |
| `Order Details by Coupon Code (Past 30 Days)` | Für jeden Gutscheincode, den Ihr Store anbietet, geben Sie an, wie dieser Couponcode verwendet wurde und welche Gutscheincodes in den letzten 30 Tagen zurückgegeben wurden. |
| `% Orders with Coupon (Past 30 Days)` | Der Prozentsatz der Bestellungen, die in den letzten 30 Tagen mit einem Coupon bestellt wurden, im Vergleich zu den Bestellungen, die nicht getätigt wurden. |

## Produkte

Das Produkt-Dashboard zeigt die allgemeine Produktleistung in Bezug auf bestellte Produkte, ihren Brutto-Merchandise-Wert (GMV) sowie die wichtigsten gekauften und erstatteten Produkte an. Es kann Ihnen dabei helfen, Käufe und Renditen auszugleichen und den Erfolg und die Beliebtheit des Produkts zu bestimmen. Ihr Store muss [so konfiguriert sein, dass Erstattungen verfolgt werden](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/store-credit/credit-configure.html), damit diese Diagramme ausgefüllt werden.

>[!NOTE]
>
>Die Berichte in diesem Dashboard stehen für Konten zur Verfügung, die mit Stores verbunden sind, die beide Konfigurationstypen aufweisen (Gastkasse, kein Gast-Checkout).

### Berichte

| Name | Beschreibung |
|---|---|
| `GMV (Past 30 Days)` | Der Bruttowarenwert aller in den letzten 30 Tagen verkauften Produkte. GMV ist definiert als die bestellte Menge multipliziert mit dem Basispreis für jedes Produkt. |
| `% GMV (Past 30 Days) Refunded` | Prozent der GMV für Produkte, die in den letzten 30 Tagen gekauft wurden und zu einer Rückerstattung führten. |
| `Product Quantity Ordered (Past 30 Days)` | Gesamtbetrag der in den letzten 30 Tagen bestellten Artikel. |
| `% Purchased Products (Past 30 Days) Refunded` | Prozentsatz der Artikel, die in den letzten 30 Tagen gekauft wurden und zu einer Rückerstattung führten. |
| `Gross Merchandise Value` | Der Bruttowertwert aller verkauften Produkte nach Monat. GMV ist definiert als die bestellte Menge multipliziert mit dem Basispreis für jedes Produkt. |
| `Purchases vs Refund Rate per Product (Past 30 Days)` | Für jedes Produkt wird die Gesamtzahl der bestellten Artikel in den letzten 30 Tagen mit der Erstattungsquote verglichen. Die Größe jeder Blase entspricht der Erstattungsrate. |
| `Product Performance Details (Past 30 Days)` | Detaillierte Angaben zu den Verkäufen und den anschließenden Erstattungen in den letzten 30 Tagen, aufgeschlüsselt nach Produkt-SKU und Produktname. |
| `Top Purchased Products by GMV (Past 30 Days)` | In den letzten 30 Tagen verkaufte Produkte, die den meisten Umsatz brachten (Top 10). |
| `Top Refunded Products by GMV (Past 30 Days)` | Produkte, die in den letzten 30 Tagen gekauft wurden und die am meisten GMV aufgrund von Erstattungen verloren haben (Top 10). |
| `Top Purchased Products by Quantity (Past 30 Days)` | Produkte, die in den letzten 30 Tagen in der größten Zahl (Top 10) verkauft wurden. |
| `Top Refunded Products by Quantity (Past 30 Days)` | Produkte, die in den letzten 30 Tagen gekauft wurden, was zu der größten erstatteten Menge führte (Top 10). |
