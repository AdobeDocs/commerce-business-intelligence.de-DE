---
title: Erwartete QuickBooks-Daten
description: Erfahren Sie, wie Sie relevante Datenfelder einfach für die Analyse verfolgen können.
exl-id: a60996bd-e3d1-497d-abce-f02ef1444f1a
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 0%

---

# Erwartet [!DNL QuickBooks] data

Nachher [Sie haben Ihre [!DNL QuickBooks] account](../../../data-analyst/importing-data/integrations/quickbooks.md), können Sie die [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse. Die folgenden Tabellen werden in Ihrer Data Warehouse erstellt:

Um alle für die Verfolgung verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Tabellennamenspalte.

## Transaktionsentitäten {#transactionentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`bill`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Bill) | Die `bills` -Tabelle enthält Informationen zu AP-Transaktionen oder eine Zahlungsaufforderung eines Dritten. Zu den Attributen gehören Währungstyp, Wechselkurs, Gesamtbetrag, Fälligkeitsdatum, Saldo und mehr. |
| [`billpayments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/BillPayment) | `BillPayment` -Entitäten sind die letzte Transaktion der Zahlung von Rechnungen, die von einem Verkäufer empfangen wurden. Diese Tabelle enthält Informationen zum Anbieter, Zahlungsart, Gesamtbetrag, Transaktionsdatum und mehr. |
| [`creditmemos`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/CreditMemo) | Die `creditmemos` in der Tabelle werden die Umsätze erfasst, bei denen es sich um Erstattungen oder Gutschriften sowohl für vollständige als auch für Teilzahlungen handelt. Einige Attribute umfassen den Namen des Kunden, die Abrechnungs- und Versandinformationen des Kunden, den Betrag und das Datum. |
| [`deposits`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Deposit) | `Deposits` umfassen direkte Einlagen und Kundenzahlungen, die auf das Asset-Konto übertragen werden, nachdem sie im `Undeposited Funds` -Konto. Zu den Attributen gehören der Betrag, die Einzahlungs-ID und das Datum. |
| [`estimates`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Estimate) | `Estimates` sind Transaktionen, die Kunden gewährt werden und die die vorgeschlagene Preisgestaltung für ein Gut oder eine Dienstleistung beinhalten. In dieser Tabelle werden der Betrag, alle Rabattinformationen, Kundeninformationen und das Datum erfasst. |
| [`invoices`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Invoice) | `Invoices` sind Verkaufsformulare, die ein Kunde später zahlt. In der Rechnungen-Tabelle werden alle Einlageninformationen, Datum, Zeileneinträge, Steuerinformationen und Kundeninformationen erfasst. |
| [`journalentries`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/JournalEntry) | Die `journalentries` -Tabelle enthält AR- und AP-Kontoinformationen, einschließlich der Journaleintrag-ID, des Transaktionsdatums und der Informationen zu Zeileneinträgen. |
| [`payments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Payment) | A `payment` record enthält Attribute wie die Zahlungs-ID, angewendete und nicht angewendete Beträge, das Transaktionsdatum, den Transaktionstyp und den Verarbeitungsstatus. |
| [`purchases`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Purchase) | Die `purchases` -Tabelle enthält Ihre Ausgaben sowie die Kauf-ID, den Zahlungsart, den Betrag und alle Informationen zu den Zeileneinträgen. |
| [`purchaseorders`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/PurchaseOrder) | Die `purchaseorders` -Tabelle enthält Anforderungen für Waren, die an Anbieter gesendet werden. Diese Tabelle enthält die Informationen zum Anbieter, die Bestellkennung, das Transaktionsdatum, die Informationen zum Zeileneintrag, den Gesamtbetrag und die AP-Kontoinformationen. |
| [`refundreceipts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/RefundReceipt) | Die `refundreceipts` -Tabelle erfasst die Erstattungen, die den Kunden gewährt wurden. Zu den Attributen gehören die Rückerstattungsquitt-ID, Zeileneintragsinformationen, Gesamtbetrag, Kundeninformationen und Saldo. |
| [`salesreceipts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/SalesReceipt) | Die `salesreceipts` -Tabelle enthält Informationen zu den Kundeneinnahmen, einschließlich der Verkaufsbeleg-ID, Zeileneintragsinformationen, Gesamtbetrag, Kundeninformationen, Transaktionsdatum und aller Einlagen. |
| [`timeactivities`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TimeActivity) | Die `timeactivities` -Tabelle enthält Zeitdatensätze für Anbieter und/oder Mitarbeiter und enthält die Zeit-Aktivitäts-ID, Mitarbeiter/Anbieter-Informationen, die protokollierte Zeit, die Beschreibung der Aktivität und das aufgezeichnete Datum. |
| [`transfers`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Transfer) | Die `transfers` -Tabelle enthält Informationen zu den zwischen Konten umgeschlagenen Mitteln. Zu den Attributen gehören die Transfer-ID, der Betrag, die Kontoinformationen und das Datum. |
| [`vendorcredits`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/VendorCredit) | Gutschriften von Anbietern sind AP-Transaktionen, bei denen es sich um Erstattungen oder Gutschriften an Anbieter handelt. Die `vendorcredits` -Tabelle enthält die Kreditkennung des Anbieters, Informationen zu Zeileneinträgen, Informationen zum Anbieter, AP-Konto, Gesamtbetrag und Datum. |

{style="table-layout:auto"}

## Entitäten in der Namensliste {#namelistentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`accounts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Account) | Diese Tabelle enthält die Konto-ID, den Namen, den Status, den Typ, den Saldo, die Währung und die Erstellungszeit. |
| [`budgets`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Budget) | In dieser Tabelle werden alle Informationen zu Unternehmenshaushalten aufgeführt, einschließlich Budget-ID, Name, Start- und Enddatum, Typ, Status und Details. |
| [`classes`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Class) | Klassen, die auf Detailzeilen von Transaktionen angewendet werden, ermöglichen es Ihnen, Segmente zu verfolgen, die nicht an einen Kunden oder ein Projekt gebunden sind. Diese Tabelle zeichnet die Klassen-ID, den Namen, die Unterklasse und den Status auf. |
| [`customers`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Customer) | Die `customers` -Tabelle enthält alle Informationen zu Ihren Kunden, einschließlich ID, Name, Abrechnungs- und Versandadresse, Telefonnummer und E-Mail-Adresse des Kunden. |
| [`departments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Department) | Die `departments` enthält die Abteilungs-ID, den Namen und den Typ (Unterabteilung vs. übergeordnete Abteilung). |
| [`employees`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Employee) | Die `employees` -Tabelle enthält Informationen zu den Personen, die für Ihr Unternehmen arbeiten. Zu den Attributen gehören die Mitarbeiter-ID, der Name, die Adresse, die Telefonnummer und die abrechnungsfähigen Informationen, wenn das Unternehmen für die Gehaltsabrechnung aktiviert ist. |
| [`items`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Item) | Die `items` -Tabelle enthält Details zu Produkten oder Dienstleistungen, die Ihr Unternehmen verkauft. Diese Tabelle enthält die Informationen zu Element-ID, Name, Beschreibung, Stückpreis, Typ, Kaufinformationen, manueller Menge sowie Informationen zu Erträgen und Vermögenswerten. |
| [`paymentmethods`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/PaymentMethod) | Die `paymentmethods` Tabelle enthält die Zahlungsmethode für Waren und Dienstleistungen. Sie enthält die Zahlungs-ID, den Typ und den Namen. |
| [`taxagencies`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxAgency) | Diese Tabelle enthält Informationen über Steueragenturen, einschließlich der Kennung der Steuerbehörde, sowie Nachverfolgungsinformationen zu Käufen und Verkäufen. |
| [`taxcodes`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxCode) | Steuercodes werden verwendet, um den Steuerstatus (steuerpflichtig gegenüber nicht steuerpflichtig) von Produkten, Dienstleistungen und Kunden zu verfolgen. Die `taxcodes` enthält die Tabelle die Kennung des Steuercodes, den Namen, die Beschreibung, den Status, den Steuerstatus, den Steuersatz und die Steuergruppe. |
| [`taxrates`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxRate) | Steuersätze werden zur Berechnung der Steuerschulden verwendet. Diese Tabelle enthält die Steuersatz-ID, den Namen, die Beschreibung, den Steuersatz, die Steueragentur und mehr. |
| [`terms`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Term) | Diese Einheit stellt die Bedingungen dar, unter denen Verkäufe getätigt werden. Die Tabelle der Begriffe enthält die Begriffe ID, Name, Typ, Rabattprozentsatz und Fälligkeitstage. |
| [`vendors`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Vendor) | Die Tabelle &quot;Anbieter&quot;enthält Informationen zu den Anbietern, von denen Sie kaufen. Zu den Tabellenattributen gehören die Anbieter-ID, der Firmenname, die Kundennummer, der Kontostand, der Status 1099, die Rechnungsadresse, die Telefonnummer, die E-Mail-Adresse und die Webadresse. |

{style="table-layout:auto"}

## Verwandte:

* [Verbinden [!DNL QuickBooks]](../integrations/quickbooks.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
