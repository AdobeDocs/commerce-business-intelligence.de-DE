---
title: Erwartete QuickBooks-Daten
description: Erfahren Sie, wie Sie relevante Datenfelder für die Analyse einfach verfolgen können.
exl-id: a60996bd-e3d1-497d-abce-f02ef1444f1a
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Erwartete [!DNL QuickBooks]

Nachdem [Sie Ihr [!DNL QuickBooks] Konto verbunden haben](../../../data-analyst/importing-data/integrations/quickbooks.md) können Sie den [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen. Die folgenden Tabellen werden in Ihrer Data Warehouse erstellt:

Um alle für das Tracking verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Spalte „Tabellenname“.

## Transaktionsentitäten {#transactionentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`bill`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Bill) | Die `bills` Tabelle enthält Informationen zu AP-Transaktionen oder eine Zahlungsaufforderung eines Dritten. Zu den Attributen gehören Währungstyp, Wechselkurs, Gesamtbetrag, Fälligkeitsdatum, Saldo und mehr. |
| [`billpayments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/BillPayment) | `BillPayment` Entitäten sind die endgültige Zahlung von Rechnungen, die von einem Anbieter empfangen wurden. Diese Tabelle enthält die Kreditoreninformationen, die Zahlungsart, den Gesamtbetrag, das Transaktionsdatum und mehr. |
| [`creditmemos`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/CreditMemo) | In der `creditmemos` Tabelle werden Transaktionen erfasst, bei denen es sich um Rückerstattungen oder Gutschriften von Voll- und Teilzahlungen handelt. Einige Attribute umfassen den Namen des Kunden, die Rechnungs- und Versandinformationen des Kunden, den Betrag und das Datum. |
| [`deposits`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Deposit) | `Deposits` umfassen Direkteinlagen und Kundenzahlungen, die auf das Aktivkonto übertragen werden, nachdem sie auf dem `Undeposited Funds` gehalten wurden. Zu den Attributen gehören Betrag, Einzahlungs-ID und Datum. |
| [`estimates`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Estimate) | `Estimates` sind Transaktionen an Kunden, die Preisvorschläge für eine Ware oder Dienstleistung enthalten. In dieser Tabelle werden der Betrag, alle Rabattinformationen, Kundeninformationen und das Datum erfasst. |
| [`invoices`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Invoice) | `Invoices` sind Verkaufsformulare, die ein Kunde später bezahlt. Die Tabelle „Rechnungen“ erfasst alle Anzahlungsinformationen, Datumsangaben, Zeilenpositionen, Steuerinformationen und Kundeninformationen. |
| [`journalentries`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/JournalEntry) | In der `journalentries` Tabelle werden AR- und AP-Kontoinformationen erfasst, einschließlich der Buchungs-ID, des Transaktionsdatums und der Positionsdaten. |
| [`payments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Payment) | Ein `payment` enthält Attribute wie die Zahlungs-ID, zugeordnete und nicht zugeordnete Beträge, das Transaktionsdatum, die Transaktionsart und den Verarbeitungsstatus. |
| [`purchases`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Purchase) | Die `purchases` Tabelle stellt Ihre Ausgaben dar und enthält die Kauf-ID, die Zahlungsart, den Betrag und alle Positionsdaten. |
| [`purchaseorders`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/PurchaseOrder) | Die `purchaseorders` enthält Anfragen für Waren, die an Kreditoren gesendet werden. Diese Tabelle enthält die Kreditoreninformationen, die Bestellkennung, das Transaktionsdatum, die Positionsdaten, den Gesamtbetrag und die Kontoinformationen des Kreditors. |
| [`refundreceipts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/RefundReceipt) | In der `refundreceipts` Tabelle werden die an Kunden gezahlten Erstattungen aufgezeichnet. Zu den Attributen gehören die Rückerstattungsquittungs-ID, die Positionsdaten, der Gesamtbetrag, die Kundendaten und der Saldo. |
| [`salesreceipts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/SalesReceipt) | In der `salesreceipts` Tabelle werden die Kundeneingänge erfasst, einschließlich der Kundeneingangskennung, der Positionsdaten, des Gesamtbetrags, der Kundendaten, des Transaktionsdatums und aller Einlagen. |
| [`timeactivities`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TimeActivity) | Die `timeactivities` Tabelle enthält Zeitdatensätze für Kreditoren und/oder Mitarbeiter und enthält die Aktivitäts-ID für Zeit, Mitarbeiter-/Lieferanteninformationen, die protokollierte Zeit, die Aktivitätsbeschreibung und das aufgezeichnete Datum. |
| [`transfers`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Transfer) | In der `transfers` Tabelle werden Informationen zu zwischen Konten übertragenen Mitteln aufgezeichnet. Zu den Attributen gehören die Transfer-ID, der Betrag, die Kontoinformationen und das Datum. |
| [`vendorcredits`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/VendorCredit) | Kreditorenguthaben sind AP-Transaktionen, bei denen es sich um Rückerstattungen oder Gutschriften an Kreditoren handelt. Die `vendorcredits` enthält die Kreditorenkredit-ID, Positionsdaten, Kreditoreninformationen, das Kreditorenkonto, den Gesamtbetrag und das Datum. |

{style="table-layout:auto"}

## Benennen von Listenentitäten {#namelistentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`accounts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Account) | Diese Tabelle enthält die Konto-ID, den Namen, den Status, den Typ, den Saldo, die Währung und die Erstellungszeit. |
| [`budgets`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Budget) | In dieser Tabelle werden alle Informationen zu Unternehmensbudgets aufgezeichnet, einschließlich der Budget-ID, des Namens, des Start- und Enddatums, des Typs, des Status und der Details. |
| [`classes`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Class) | Klassen, die auf Detailzeilen von Transaktionen angewendet werden, ermöglichen es Ihnen, Segmente zu verfolgen, die nicht mit einem Client oder Projekt verknüpft sind. Diese Tabelle zeichnet die Klassen-ID, den Namen, die Unterklasse und den Status auf. |
| [`customers`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Customer) | Die `customers` Tabelle enthält alle Informationen zu Ihren Kunden, einschließlich Kunden-ID, Name, Rechnungs- und Lieferadressen, Telefonnummer und E-Mail-Adresse. |
| [`departments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Department) | Die `departments` Tabelle enthält die Abteilungs-ID, den Namen und den Typ (Unterabteilung vs. Abteilung der obersten Ebene). |
| [`employees`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Employee) | Die `employees` Tabelle zeichnet Informationen über die Personen auf, die für Ihr Unternehmen arbeiten. Zu den Attributen gehören die Mitarbeiter-ID, der Name, die Adresse, die Telefonnummer und fakturierbare Informationen, wenn für das Unternehmen die Lohn- und Gehaltsabrechnung aktiviert ist. |
| [`items`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Item) | Die `items` enthält Details zu Produkten oder Dienstleistungen, die Ihr Unternehmen verkauft. Diese Tabelle enthält die Artikel-ID, den Namen, die Beschreibung, den Stückpreis, die Art, die Kaufinformationen, die Lagerbestandsmenge sowie die Informationen zu Einkommen und Anlagenkonten. |
| [`paymentmethods`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/PaymentMethod) | In der `paymentmethods` Tabelle wird die Zahlungsmethode erfasst, die für Waren und Dienstleistungen empfangen wurde. Sie enthält die Zahlungs-ID, den Typ und den Namen. |
| [`taxagencies`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxAgency) | In dieser Tabelle werden Informationen zu Steuerbehörden, einschließlich der Steuerbehörden-ID, und Tracking-Informationen zu Steuern für Käufe und Verkäufe aufgezeichnet. |
| [`taxcodes`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxCode) | Steuercodes werden verwendet, um den Steuerstatus (steuerpflichtig vs. nicht steuerpflichtig) von Produkten, Dienstleistungen und Kunden zu verfolgen. Die `taxcodes` enthält die Steuerschlüssel-ID, den Namen, die Beschreibung, den Status, den Steuerstatus, den Steuersatz und die Steuergruppe. |
| [`taxrates`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxRate) | Steuersätze werden zur Berechnung von Steuerschulden verwendet. Diese Tabelle enthält die Steuersatz-ID, den Namen, die Beschreibung, den Satz, die Steuerbehörde und mehr. |
| [`terms`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Term) | Dieses Unternehmen stellt die Bedingungen dar, unter denen die Verkäufe getätigt werden. Die Tabelle „Bedingungen“ enthält die Begriffe-ID, Name, Typ, Rabatt in Prozent und Fälligkeitstage. |
| [`vendors`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Vendor) | Die Tabelle Kreditoren enthält Informationen zu den Kreditoren, bei denen Sie Einkäufe tätigen. Zu den Tabellenattributen gehören die Anbieter-ID, der Firmenname, die Kontonummer, der Kontostand, der 1099-Status, die Rechnungsadresse, die Telefonnummer, die E-Mail-Adresse und die Web-Adresse. |

{style="table-layout:auto"}

## Verwandt:

* [Verbinden [!DNL QuickBooks]](../integrations/quickbooks.md)
* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
