---
title: Erwartete QuickBooks-Daten
description: Erfahren Sie, wie Sie relevante Datenfelder für die Analyse einfach nachverfolgen können.
exl-id: a60996bd-e3d1-497d-abce-f02ef1444f1a
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---

# Erwartet [!DNL QuickBooks] data

![](../../../assets/Quickbooks.png)

Nachher [Sie haben Ihre [!DNL QuickBooks] account](../../../data-analyst/importing-data/integrations/quickbooks.md), können Sie die [Data Warehouse Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) zur einfachen Nachverfolgung relevanter Datenfelder für die Analyse. Die folgenden Tabellen werden in Ihrem Data Warehouse erstellt:

Um alle für die Verfolgung verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Tabellennamenspalte.

## Transaktionsentitäten {#transactionentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`bill`](https://developer.intuit.com/docs/api/accounting/Bill) | Die Tabelle &quot;Rechnungen&quot;enthält Informationen zu AP-Transaktionen oder eine Zahlungsaufforderung eines Dritten. Zu den Attributen gehören Währungstyp, Wechselkurs, Gesamtbetrag, Fälligkeitsdatum, Saldo und mehr. |
| [`billpayments`](https://developer.intuit.com/docs/api/accounting/BillPayment) | BillPayment-Entitäten sind die letzte Transaktion der Zahlung von Rechnungen, die von einem Verkäufer empfangen wurden. Diese Tabelle enthält Informationen zum Anbieter, Zahlungsart, Gesamtbetrag, Transaktionsdatum und mehr. |
| [`creditmemos`](https://developer.intuit.com/docs/api/accounting/CreditMemo) | In der Tabelle der kreditmemos werden Transaktionen erfasst, bei denen es sich um Erstattungen oder Gutschriften sowohl für vollständige als auch für Teilzahlungen handelt. Einige Attribute umfassen den Namen des Kunden, die Abrechnungs- und Versandinformationen des Kunden, den Betrag und das Datum. |
| [`deposits`](https://developer.intuit.com/docs/api/accounting/Deposit) | Einlagen umfassen direkte Einlagen und Kundenzahlungen, die nach ihrer Verwahrung in das Asset-Konto eingezahlt werden `Undeposited Funds` -Konto. Zu den Attributen gehören der Betrag, die Einzahlungs-ID und das Datum. |
| [`estimates`](https://developer.intuit.com/docs/api/accounting/Estimate) | Schätzungen sind Transaktionen, die Kunden gewährt werden und die die vorgeschlagene Preisgestaltung für eine Ware oder eine Dienstleistung beinhalten. In dieser Tabelle werden der Betrag, alle Rabattinformationen, Kundeninformationen und das Datum erfasst. |
| [`invoices`](https://developer.intuit.com/docs/api/accounting/Invoice) | Rechnungen sind Verkaufsformulare, die ein Kunde später zahlt. In der Rechnungen-Tabelle werden alle Einlageninformationen, Datum, Zeileneinträge, Steuerinformationen und Kundeninformationen erfasst. |
| [`journalentries`](https://developer.intuit.com/docs/api/accounting/JournalEntry) | Die Tabelle &quot;journalentry&quot;zeichnet AR- und AP-Kontoinformationen auf, einschließlich der Journaleintragskennung, des Transaktionsdatums und der Informationen zu Zeileneinträgen. |
| [`payments`](https://developer.intuit.com/docs/api/accounting/Payment) | Ein Zahlungsdatensatz enthält Attribute wie die Zahlungs-ID, angewendete und nicht angewendete Beträge, das Transaktionsdatum, den Transaktionstyp und den Verarbeitungsstatus. |
| [`purchases`](https://developer.intuit.com/docs/api/accounting/Purchase) | Die Käufungstabelle enthält Ihre Ausgaben sowie die Kauf-ID, den Zahlungsart, den Betrag und alle Informationen zu den Zeileneinträgen. |
| [`purchaseorders`](https://developer.intuit.com/docs/api/accounting/PurchaseOrder) | Kaufaufträge sind Warenanfragen an Anbieter. Diese Tabelle enthält die Informationen zum Anbieter, die Bestellkennung, das Transaktionsdatum, die Informationen zum Zeileneintrag, den Gesamtbetrag und die AP-Kontoinformationen. |
| [`refundreceipts`](https://developer.intuit.com/docs/api/accounting/RefundReceipt) | In dieser Tabelle sind die Erstattungen aufgeführt, die den Kunden gewährt wurden. Zu den Attributen gehören die Rückerstattungsquitt-ID, Zeileneintragsinformationen, Gesamtbetrag, Kundeninformationen und Saldo. |
| [`salesreceipts`](https://developer.intuit.com/docs/api/accounting/SalesReceipt) | Die Tabelle der Verkaufseinnahmen enthält Informationen zu den Kundeneinnahmen, einschließlich der Verkaufs-Quittungen-ID, Zeileneintragsinformationen, Gesamtbetrag, Kundeninformationen, Transaktionsdatum und aller Einlagen. |
| [`timeactivities`](https://developer.intuit.com/docs/api/accounting/TimeActivity) | Zeitaktivitäten sind Zeiteinträge für Anbieter und/oder Mitarbeiter. Die Tabelle der Zeitaktivitäten enthält die Zeit der Aktivitäts-ID, Mitarbeiter-/Anbieterinformationen, die protokollierte Zeit, die Beschreibung der Aktivität und das aufgezeichnete Datum. |
| [`transfers`](https://developer.intuit.com/docs/api/accounting/Transfer) | In der Übertragungstabelle werden Informationen über die zwischen Konten umgeschlagenen Mittel aufgeführt. Zu den Attributen gehören die Transfer-ID, der Betrag, die Kontoinformationen und das Datum. |
| [`vendorcredits`](https://developer.intuit.com/docs/api/accounting/VendorCredit) | Gutschriften von Anbietern sind AP-Transaktionen, bei denen es sich um Erstattungen oder Gutschriften an Anbieter handelt. Die `vendorcredits` -Tabelle enthält die Kreditkennung des Anbieters, Informationen zu Zeileneinträgen, Informationen zum Anbieter, AP-Konto, Gesamtbetrag und Datum. |

{style=&quot;table-layout:auto&quot;}

## Entitäten in der Namensliste {#namelistentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`accounts`](https://developer.intuit.com/docs/api/accounting/Account) | Diese Tabelle enthält die Konto-ID, den Namen, den Status, den Typ, den Saldo, die Währung und die Erstellungszeit. |
| [`budgets`](https://developer.intuit.com/docs/api/accounting/Budget) | In dieser Tabelle werden alle Informationen zu Unternehmenshaushalten aufgeführt, einschließlich Budget-ID, Name, Start- und Enddatum, Typ, Status und Details. |
| [`classes`](https://developer.intuit.com/docs/api/accounting/Class) | Klassen, die auf Detailzeilen von Transaktionen angewendet werden, ermöglichen es Ihnen, Segmente zu verfolgen, die nicht an einen Kunden oder ein Projekt gebunden sind. Diese Tabelle zeichnet die Klassen-ID, den Namen, die Unterklasse und den Status auf. |
| [`customers`](https://developer.intuit.com/docs/api/accounting/Customer) | Die Tabelle &quot;Kunden&quot;enthält alle Informationen zu Ihren Kunden, einschließlich ID, Name, Abrechnungs- und Versandadressen, Telefonnummer und E-Mail-Adresse des Kunden. |
| [`departments`](https://developer.intuit.com/docs/api/accounting/Department) | Die Abteilungstabelle enthält die Abteilungs-ID, den Namen und den Typ (Unterabteilung vs. übergeordnete Abteilung). |
| [`employees`](https://developer.intuit.com/docs/api/accounting/Employee) | In der Mitarbeitertabelle werden Informationen zu den Personen aufgezeichnet, die für Ihr Unternehmen arbeiten. Zu den Attributen gehören die Mitarbeiter-ID, der Name, die Adresse, die Telefonnummer und die abrechnungsfähigen Informationen, wenn das Unternehmen für die Gehaltsabrechnung aktiviert ist. |
| [`items`](https://developer.intuit.com/docs/api/accounting/Item) | Die Tabelle items enthält Details zu Produkten oder Dienstleistungen, die Ihr Unternehmen verkauft. Diese Tabelle enthält die Informationen zu Element-ID, Name, Beschreibung, Stückpreis, Typ, Kaufinformationen, manueller Menge sowie Informationen zu Erträgen und Vermögenswerten. |
| [`paymentmethods`](https://developer.intuit.com/docs/api/accounting/PaymentMethod) | In der Tabelle der Zahlungsmethoden wird die Zahlungsmethode für Waren und Dienstleistungen erfasst. Sie enthält die Zahlungs-ID, den Typ und den Namen. |
| [`taxagencies`](https://developer.intuit.com/docs/api/accounting/TaxAgency) | Diese Tabelle enthält Informationen über Steueragenturen, einschließlich der Kennung der Steuerbehörde, sowie Nachverfolgungsinformationen zu Käufen und Verkäufen. |
| [`taxcodes`](https://developer.intuit.com/docs/api/accounting/TaxCode) | Steuercodes werden verwendet, um den Steuerstatus (steuerpflichtig gegenüber nicht steuerpflichtig) von Produkten, Dienstleistungen und Kunden zu verfolgen. Die Tabelle mit den Steuercodes enthält die Kennung des Steuercodes, den Namen, die Beschreibung, den Status, den Steuerstatus, den Steuersatz und die Steuergruppe. |
| [`taxrates`](https://developer.intuit.com/docs/api/accounting/TaxRate) | Steuersätze werden zur Berechnung der Steuerschulden verwendet. Diese Tabelle enthält die Steuersatz-ID, den Namen, die Beschreibung, den Steuersatz, die Steueragentur und mehr. |
| [`terms`](https://developer.intuit.com/docs/api/accounting/Term) | Diese Einheit stellt die Bedingungen dar, unter denen Verkäufe getätigt werden. Die Tabelle der Begriffe enthält die Begriffe ID, Name, Typ, Rabattprozentsatz und Fälligkeitstage. |
| [`vendors`](https://developer.intuit.com/docs/api/accounting/Vendor) | Die Tabelle &quot;Anbieter&quot;enthält Informationen zu den Anbietern, von denen Sie kaufen. Zu den Tabellenattributen gehören die Anbieter-ID, der Firmenname, die Kundennummer, der Kontostand, der Status 1099, die Rechnungsadresse, die Telefonnummer, die E-Mail-Adresse und die Webadresse. |

{style=&quot;table-layout:auto&quot;}

## Verwandte:

* [Verbinden [!DNL QuickBooks]](../integrations/quickbooks.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
