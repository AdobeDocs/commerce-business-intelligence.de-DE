---
title: Vorkonfigurierte Dashboards
description: Erfahren Sie mehr über vordefinierte Dashboards, die insight in Ihr Unternehmen integrieren.
exl-id: fe61c92e-de87-4317-96d7-01d2a9846bf9
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1950'
ht-degree: 0%

---

# Vorkonfigurierte Dashboards

[!DNL Adobe Commerce Intelligence] enthält vordefinierte Dashboards, um insight in Ihr Unternehmen zu integrieren. Mit Dashboards können Sie den Status wichtiger Metriken überprüfen, z. B. den Lebensdauerumsatz der Benutzenden, die Anzahl der Wiederholungskäufe, die über einen bestimmten Zeitraum gekauften Top-Produkte und mehr. Diese vorkonfigurierten Dashboards wurden erstellt, um Sie bei fundierten Geschäftsentscheidungen zu unterstützen.

>[!NOTE]
>
>Der Zugriff auf diese Dashboards hängt von Ihrem Kontotyp und Ihrer Zugriffsebene ab. Wenn diese Dashboards nicht angezeigt werden, wenden Sie sich an den [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

## Berichtverfügbarkeit

Für die `Customers`- und `Executive Summary`-Dashboards sind einige Berichte nur je nach Checkout-Konfiguration Ihres Geschäfts verfügbar. Insbesondere dann, wenn Ihr Store einen Gast-Checkout zulässt oder keinen Gast-Checkout zulässt.

## Kunden (Gast-Checkout erlaubt)

Das Dashboard „Kunden“ (Gast-Checkout zulässig) enthält Informationen zu Ihrem Kundenstamm, wie z. B. das Kaufverhalten. Dieses Dashboard kann Ihnen dabei helfen, die Kundenbindung zu verbessern und festzustellen, welche Kunden den höchsten Umsatz erzielen.

### Berichte

| -Name | Beschreibung |
|---|---|
| `Orders by New Customers (Past 30 Days)` | Bestellungen in den letzten 30 Tagen von Kunden, die noch nie eine Bestellung aufgegeben haben. |
| `Orders by Existing Customers (Past 30 Days)` | Bestellungen in den letzten 30 Tagen von Kunden, die zuvor mindestens eine Bestellung aufgegeben haben. |
| `Total Unique Customers (Past 30 Days)` | Anzahl der Unique Customers, die in den letzten 30 Tagen Bestellungen aufgegeben haben. |
| `Orders by New vs Existing Customers` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen gegenüber Kunden mit mindestens einer vorherigen Bestellung. |
| `Subsequent Order Probability (All Time)` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere aufgeben. |
| `% of Customers with Multiple Orders (All Time)` | Prozent aller Kunden, die mehr als eine Bestellung aufgegeben haben. |
| `Median Time Between Orders (All Time)` | Durchschnittliche Zeit, die jeder Kunde zwischen einer Bestellung und der nächsten benötigt. |
| `Subsequent Order Probability` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere Bestellung aufgeben, aufgeschlüsselt nach Bestellnummer. Das heißt, der Prozentsatz der Kunden mit einer Bestellung, die eine zweite aufgeben, der Prozentsatz der Kunden mit zwei Aufträgen, die eine dritte aufgeben, usw. |
| `Time Between Orders` | Die durchschnittliche und mediane Zeit, die Kunden zwischen Aufträgen benötigen, aufgeschlüsselt nach Auftragsnummern (d. h. die Zeit zwischen den Aufträgen 1 und 2, 2 und 3 usw.). |
| `Number of Customers - Lifetime Orders` | Bei einer bestimmten Anzahl von Aufträgen, die während der Kundenlebensdauer aufgegeben werden, die Anzahl der Kunden, die so viele Aufträge aufgegeben haben, und der Prozentsatz des gesamten Kundenstamms, den diese Anzahl darstellt. |
| `One-Time Customers who Bought 3-6 Months Ago` | Kunden, die ihren ersten und einzigen Kauf vor drei bis sechs Monaten getätigt haben. |
| `Avg LTV by First Order` | Vergleicht den kumulativen durchschnittlichen Kundenlebensdauerumsatz in allen Kohorten. Kohorten werden durch den Monat definiert, in dem ein Kunde zum ersten Mal einen Kauf getätigt hat. Eine `Jan 2020` Kohorte zeigt beispielsweise den kumulativen durchschnittlichen LTV für Kunden, deren erster Kauf im Januar 2020 erfolgte. |
| `Customer's First 30 Day vs Lifetime Revenue` | Vergleich des durchschnittlichen Umsatzes von Kunden in den 30 Tagen nach ihrem ersten Kauf im Vergleich zu ihrem gesamten Lebenszyklus. Jede Blase entspricht einer Versandregion, und die Größe jeder Blase gibt die Anzahl der von dieser Region erworbenen Kunden an. |

## Kunden (kein Gast-Checkout zulässig)

Das Dashboard Kunden (kein Gast-Checkout zulässig) enthält Informationen zu Ihrem Kundenstamm, wie z. B. das Kaufverhalten und Konversionen von Kontoregistrierungen zu Bestellplatzierungen. Dieses Dashboard kann Ihnen dabei helfen, die Kundenbindung zu verbessern und festzustellen, welche Kunden den höchsten Umsatz erzielen.

### Berichte

| -Name | Beschreibung |
|---|---|
| `Account Registration (Past 30 Days)` | Die Anzahl der Personen, die sich in den letzten 30 Tagen für ein Konto bei Ihrem Store registriert haben. |
| `Accounts Registered (Past 30 Days) with 1 or More Orders` | Die Anzahl der Personen, die sich in den letzten 30 Tagen für ein Konto bei Ihrem Geschäft registriert und auch mindestens eine Bestellung aufgegeben haben. |
| `% Conversion from Registration to First Order (Past 30 Days)` | Prozentsatz der Konten, die in den letzten 30 Tagen registriert wurden und eine Bestellung aufgegeben haben. |
| `% Conversion from Registration to First Order` | Prozentsatz der registrierten Konten, die eine Bestellung aufgegeben haben, nach Monat der Registrierung. |
| `Orders by New vs Existing Customers` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen gegenüber Kunden mit mindestens einer vorherigen Bestellung. |
| `Subsequent Order Probability (All Time)` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere aufgeben. |
| `% of Customers with Multiple Orders (All Time)` | Prozent aller Kunden, die mehr als eine Bestellung aufgegeben haben. |
| `Median Time Between Orders (All Time)` | Durchschnittliche Zeit, die jeder Kunde zwischen einer Bestellung und der nächsten benötigt. |
| `Subsequent Order Probability` | Die Wahrscheinlichkeit, dass Kunden, die eine Bestellung aufgegeben haben, eine andere aufgeben, aufgeschlüsselt nach Bestellnummer. Das heißt, Prozent der Kunden mit einer Bestellung, die eine zweite aufgeben, Prozent mit zwei, die eine dritte aufgeben, und so weiter. |
| `Time Between Orders` | Die durchschnittliche und mediane Zeit, die Kunden zwischen Aufträgen benötigen, aufgeschlüsselt nach Auftragsnummern (d. h. die Zeit zwischen den Aufträgen 1 und 2, 2 und 3 usw.). |
| `Number of Customers - Lifetime Orders` | Bei einer bestimmten Anzahl von Aufträgen, die während der Kundenlebensdauer aufgegeben werden, die Anzahl der Kunden, die so viele Aufträge aufgegeben haben, und der Prozentsatz des gesamten Kundenstamms, den diese Anzahl darstellt. |
| `One-Time Customers who Bought 3-6 Months Ago` | Kunden, die ihren ersten und einzigen Kauf vor drei bis sechs Monaten getätigt haben. |
| `Avg LTV by First Order` | Vergleicht den kumulativen durchschnittlichen Kundenlebensdauerumsatz in allen Kohorten. Kohorten werden durch den Monat definiert, in dem ein Kunde zum ersten Mal einen Kauf getätigt hat. Beispielsweise zeigt eine Kohorte im Januar 2020 den kumulativen durchschnittlichen LTV für Kunden, deren erster Kauf im Januar 2020 erfolgte. |
| `Customer's First 30 Day vs Lifetime Revenue` | Vergleich des durchschnittlichen Umsatzes von Kunden in den 30 Tagen nach ihrem ersten Kauf im Vergleich zu ihrem gesamten Lebenszyklus. Jede Blase entspricht einer Versandregion, und die Größe jeder Blase gibt die Anzahl der von dieser Region erworbenen Kunden an. |

## Executive Summary (Gast-Checkout erlaubt)

Das Dashboard „Executive Summary“ (Gast-Checkout zulässig) bietet einen kurzen Überblick über die Aktivitäten des Unternehmens in Bezug auf Bestellungen und Umsatz. Dieses Dashboard wurde für Führungskräfte entwickelt, um einen Überblick über die Geschäftsleistung zu erhalten, kann aber auch für andere interessant sein.

### Berichte

| -Name | Beschreibung |
|---|---|
| `Revenue (Current Month)` | Der Umsatz, der von Ihrem Geschäft für den aktuellen Monat generiert wurde. In diesem Fall wird der Umsatz definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt. |
| `Revenue (Past 6 Months by Day)` | Gesamter Tagesumsatz, überlagert mit dem durchschnittlichen Tagesumsatz der letzten sieben Tage. In diesem Fall wird der Umsatz definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt. |
| `% Change in Revenue (MoM MTD)` | Vergleich des Umsatzes des aktuellen Monats (bisher) mit dem gleichen Anteil des Vormonats. |
| `Revenue from New vs Existing Customers (Current Month)` | Umsatz für den aktuellen Monat (bisher), der neuen (Erstkundinnen und -kunden) gegenüber Bestandskunden (zweite oder spätere Bestellung) zugeordnet wird. |
| `Average Order Value (Current Month)` | Tagesdurchschnittswert der im aktuellen Monat aufgegebenen Bestellungen (bisher). Der Bestellwert ist definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt hat. |
| `Orders (Current Month)` | Die Anzahl der Bestellungen, die für den aktuellen Monat (bis jetzt) in Ihrem Geschäft aufgegeben wurden. |
| `% Change in Orders (MoM MTD)` | Vergleich der Anzahl der Bestellungen für den aktuellen Monat (bisher) mit dem gleichen Teil des Vormonats. |
| `Orders by New Customers (Current Month)` | Bestellungen für den aktuellen Monat von Kunden, die noch nie eine Bestellung aufgegeben haben. |
| `Orders by Existing Customers (Current Month)` | Bestellungen für den aktuellen Monat von Kunden, die zuvor mindestens eine Bestellung aufgegeben haben. |
| `Orders by New vs Existing Customers (Current Year by Week)` | Anzahl der Bestellungen von Kunden ohne vorherige Bestellungen gegenüber Kunden mit mindestens einer vorherigen Bestellung für jede Woche des aktuellen Jahres (bisher). |

## Zusammenfassung für Führungskräfte (kein Gast-Checkout zulässig)

Das Dashboard „Executive Summary“ (Kein Gast-Checkout zulässig) bietet einen kurzen Überblick über die Geschäftsentwicklung in Bezug auf Bestellungen, Umsatz und Kontoregistrierungen. Dieses Dashboard wurde für Führungskräfte entwickelt, um einen Überblick über die Geschäftsleistung zu erhalten, kann aber auch für andere interessant sein.

### Berichte

| -Name | Beschreibung |
|---|---|
| `Revenue (Current Month)` | Der Umsatz, der von Ihrem Geschäft in diesem Monat generiert wurde. In diesem Fall wird der Umsatz definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt. |
| `Revenue (Past 6 Months by Day)` | Gesamter Tagesumsatz, überlagert mit dem durchschnittlichen Tagesumsatz der letzten sieben Tage. In diesem Fall wird der Umsatz definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt. |
| `% Change in Revenue (MoM MTD)` | Vergleich der bisherigen Einnahmen in diesem Monat mit dem gleichen Anteil des Vormonats. |
| `Revenue from New vs Existing Customers (Current Month)` | Umsatz für den aktuellen Monat (bisher), der neuen (Erstkundinnen und -kunden) gegenüber Bestandskunden (zweite oder spätere Bestellung) zugeordnet wird. |
| `Average Order Value (Current Month)` | Tagesdurchschnittswert der im aktuellen Monat aufgegebenen Bestellungen (bisher). Der Bestellwert ist definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt hat. |
| `Orders (Current Month)` | Die Anzahl der Bestellungen, die für den aktuellen Monat (bis jetzt) in Ihrem Geschäft aufgegeben wurden. |
| `% Change in Orders (MoM MTD)` | Vergleich der Anzahl der Bestellungen für den aktuellen Monat (bisher) mit dem gleichen Teil des Vormonats. |
| `Account Registrations (Current Month)` | Die Anzahl der bisher neu registrierten Konten in diesem Monat. |
| `% Conversion from Registration to First Order (Current Month)` | Der Prozentsatz der in diesem Monat bisher registrierten Konten, die eine Bestellung aufgegeben haben. |
| `% Conversion from Registration to First Order (Current Year by Week)` | Der Prozentsatz der Konten, die in diesem Jahr bisher jede Woche registriert wurden und eine Bestellung aufgegeben haben. |

## Bestellungen

Das Dashboard „Bestellungen“ bietet Einblicke in das Transaktionsvolumen von Bestellungen, ihren Status, die verwendeten Couponcodes, den generierten Umsatz und die verwendeten Zahlungsmethoden. Sie können beispielsweise den Erfüllungsprozess verfolgen und sicherstellen, dass keine Probleme oder Engpässe auftreten.

>[!NOTE]
>
>Die Berichte in diesem Dashboard sind für Konten verfügbar, die mit Stores mit beiden Konfigurationstypen verbunden sind (Gast-Checkout, kein Gast-Checkout).

### Berichte

| -Name | Beschreibung |
|---|---|
| `Orders (Past 30 Days)` | Die Anzahl der Bestellungen, die in den letzten 30 Tagen bei Ihrem Geschäft aufgegeben wurden. |
| `Revenue (Past 30 Days)` | Der Umsatz, der von Ihrem Geschäft in den letzten 30 Tagen generiert wurde. Der Umsatz ist definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt. |
| `Average Order Value (Past 30 Days)` | Durchschnittlicher Wert der Bestellungen der letzten 30 Tage. Der Bestellwert ist definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt hat. |
| `Orders` | Die Anzahl der Bestellungen, die monatlich in Ihrem Geschäft aufgegeben werden. |
| `Revenue by Payment Method` | Der Umsatz, der von Ihrem Geschäft generiert wurde, aufgeteilt nach Zahlungsmethode. Der Umsatz ist definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt. |
| `AOV by New vs Existing Customers` | Monatlicher Durchschnittswert der in Ihrem Geschäft getätigten Bestellungen, aufgeteilt nach Bestellungen von Kunden ohne vorherige Bestellungen gegenüber Kunden mit mindestens einer vorherigen Bestellung. Der Bestellwert ist definiert als der Endpreis, den ein Kunde für eine Bestellung bezahlt hat. |
| `% Orders by Status (Past 30 Days)` | Prozent der Bestellungen von jedem Tag in den letzten 30 Tagen, die derzeit in jedem Bestellstatus sind. |
| `Incomplete Orders (Created more than 1 Day Ago)` | Eine Liste aller Bestellungen, die vor mehr als einem Tag aufgegeben wurden und sich noch im Status „Unvollständig“ (nicht storniert oder abgeschlossen) befinden. |
| `Orders Per Hour (Past 7 Days)` | Bestellmenge nach Tag und Stunde. |
| `Revenue Details (Past 30 Days)` | Tägliche Aufschlüsselung des Umsatzes der letzten 30 Tage in alle Komponenten des Gesamtumsatzwerts. |
| `Order Details by Coupon Code (Past 30 Days)` | Für jeden von Ihrem Shop angebotenen Couponcode Details dazu, wie dieser Couponcode verwendet wurde und welche Rückgaben er in den letzten 30 Tagen eingebracht hat. |
| `% Orders with Coupon (Past 30 Days)` | Der Prozentsatz der in den letzten 30 Tagen aufgegebenen Bestellungen, für die ein Coupon verwendet wurde, im Vergleich zu den Bestellungen, für die kein Coupon verwendet wurde. |

## PRODUCT

Das Dashboard „Produkte“ zeigt die allgemeine Produktleistung in Bezug auf bestellte Produkte, ihren Bruttowarenwert (GMV) und die am häufigsten gekauften und rückerstatteten Produkte an. Dies kann Ihnen helfen, Käufe und Rücksendungen auszugleichen und den Produkterfolg und die Beliebtheit zu bestimmen. Ihr Store muss [konfiguriert sein, um Rückerstattungen zu &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/store-credit/credit-configure.html?lang=de)), damit diese Diagramme ausgefüllt werden.

>[!NOTE]
>
>Die Berichte in diesem Dashboard sind für Konten verfügbar, die mit Stores mit beiden Konfigurationstypen verbunden sind (Gast-Checkout, kein Gast-Checkout).

### Berichte

| -Name | Beschreibung |
|---|---|
| `GMV (Past 30 Days)` | Der Bruttowarenwert aller in den letzten 30 Tagen verkauften Produkte. GMV ist definiert als die bestellte Menge multipliziert mit dem Grundpreis für jedes Produkt. |
| `% GMV (Past 30 Days) Refunded` | Prozent des GMV für Produkte, die in den letzten 30 Tagen gekauft wurden und zu einer Rückerstattung führten. |
| `Product Quantity Ordered (Past 30 Days)` | Gesamtzahl der in den letzten 30 Tagen bestellten Artikel. |
| `% Purchased Products (Past 30 Days) Refunded` | Prozent der in den letzten 30 Tagen gekauften Artikel, die zu einer Rückerstattung geführt haben. |
| `Gross Merchandise Value` | Der Bruttowarenwert aller verkauften Produkte nach Monat. GMV ist definiert als die bestellte Menge multipliziert mit dem Grundpreis für jedes Produkt. |
| `Purchases vs Refund Rate per Product (Past 30 Days)` | Für jedes Produkt ein Vergleich der Gesamtzahl der bestellten Artikel in den letzten 30 Tagen mit dem Satz, zu dem das Produkt zurückerstattet wurde. Die Größe jeder Blase entspricht dem Erstattungssatz. |
| `Product Performance Details (Past 30 Days)` | Detaillierte Informationen zu Verkäufen und nachfolgenden Erstattungen in den letzten 30 Tagen, nach Produkt-SKU und Produktname. |
| `Top Purchased Products by GMV (Past 30 Days)` | In den letzten 30 Tagen verkaufte Produkte, die den höchsten Umsatz erzielten (Top 10). |
| `Top Refunded Products by GMV (Past 30 Days)` | In den letzten 30 Tagen gekaufte Produkte, die zu den meisten GMV-Verlusten aufgrund von Erstattungen führten (die Top 10). |
| `Top Purchased Products by Quantity (Past 30 Days)` | Produkte, die in den letzten 30 Tagen in den meisten Zahlen verkauft wurden (Top 10). |
| `Top Refunded Products by Quantity (Past 30 Days)` | Produkte, die in den letzten 30 Tagen gekauft wurden und die am meisten erstattet wurden (Top 10). |
