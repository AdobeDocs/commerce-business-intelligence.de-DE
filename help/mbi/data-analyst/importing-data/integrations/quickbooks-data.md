---
title: Erwartete QuickBooks-Daten
description: Erfahren Sie, wie Sie relevante Datenfelder einfach für die Analyse verfolgen können.
exl-id: a60996bd-e3d1-497d-abce-f02ef1444f1a
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Erwartete [!DNL QuickBooks] Daten

Nachdem [Sie Ihr [!DNL QuickBooks] Konto](../../../data-analyst/importing-data/integrations/quickbooks.md) verbunden haben, können Sie den [Data Warehouse-Manager](../../../data-analyst/data-warehouse-mgr/tour-dwm.md) verwenden, um relevante Datenfelder für die Analyse einfach zu verfolgen. Die folgenden Tabellen werden in Ihrer Data Warehouse erstellt:

Um alle für die Verfolgung verfügbaren Felder anzuzeigen, klicken Sie auf die Links in der Tabellennamenspalte.

## Transaktionsentitäten {#transactionentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`bill`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Bill) | Die Tabelle `bills` enthält Informationen zu AP-Transaktionen oder eine Zahlungsaufforderung eines Dritten. Zu den Attributen gehören Währungstyp, Wechselkurs, Gesamtbetrag, Fälligkeitsdatum, Saldo und mehr. |
| [`billpayments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/BillPayment) | `BillPayment` -Entitäten sind die letzte Transaktion der Zahlung von Rechnungen, die von einem Anbieter empfangen wurden. Diese Tabelle enthält Informationen zum Anbieter, Zahlungsart, Gesamtbetrag, Transaktionsdatum und mehr. |
| [`creditmemos`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/CreditMemo) | In der Tabelle `creditmemos` sind Transaktionen aufgeführt, bei denen es sich um Erstattungen oder Gutschriften sowohl für vollständige als auch für Teilzahlungen handelt. Einige Attribute umfassen den Namen des Kunden, die Abrechnungs- und Versandinformationen des Kunden, den Betrag und das Datum. |
| [`deposits`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Deposit) | `Deposits` umfasst direkte Einlagen und Kundenzahlungen, die in das Asset-Konto verschoben werden, nachdem sie im `Undeposited Funds`-Konto gehalten wurden. Zu den Attributen gehören der Betrag, die Einzahlungs-ID und das Datum. |
| [`estimates`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Estimate) | `Estimates` sind Transaktionen, die Kunden gewährt werden, die die vorgeschlagene Preisgestaltung für ein Gut oder eine Dienstleistung beinhalten. In dieser Tabelle werden der Betrag, alle Rabattinformationen, Kundeninformationen und das Datum erfasst. |
| [`invoices`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Invoice) | `Invoices` sind Verkaufsformulare, die ein Kunde später zahlt. In der Rechnungen-Tabelle werden alle Einlageninformationen, Datum, Zeileneinträge, Steuerinformationen und Kundeninformationen erfasst. |
| [`journalentries`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/JournalEntry) | In der Tabelle &quot;`journalentries`&quot; werden AR- und AP-Kontoinformationen aufgezeichnet, einschließlich der Journaleintragskennung, des Transaktionsdatums und der Informationen zum Zeileneintrag. |
| [`payments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Payment) | Ein `payment` -Datensatz enthält Attribute wie die Zahlungs-ID, angewendete und nicht angewendete Beträge, das Transaktionsdatum, den Transaktionstyp und den Verarbeitungsstatus. |
| [`purchases`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Purchase) | Die Tabelle &quot;`purchases`&quot; stellt Ihre Ausgaben dar und enthält die Kauf-ID, die Zahlungsart, den Betrag und alle Informationen zu Zeileneinträgen. |
| [`purchaseorders`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/PurchaseOrder) | Die Tabelle `purchaseorders` enthält Anforderungen für Waren, die an Anbieter gesendet werden. Diese Tabelle enthält die Informationen zum Anbieter, die Bestellkennung, das Transaktionsdatum, die Informationen zum Zeileneintrag, den Gesamtbetrag und die AP-Kontoinformationen. |
| [`refundreceipts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/RefundReceipt) | Die Tabelle `refundreceipts` zeichnet die Erstattungen auf, die an Kunden gezahlt wurden. Zu den Attributen gehören die Rückerstattungsquitt-ID, Zeileneintragsinformationen, Gesamtbetrag, Kundeninformationen und Saldo. |
| [`salesreceipts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/SalesReceipt) | In der Tabelle &quot;`salesreceipts`&quot; werden Informationen zu den Kundeneinnahmen erfasst, einschließlich der Verkaufs-Quittungen-ID, Zeileneintragsinformationen, Gesamtbetrag, Kundeninformationen, Transaktionsdatum und aller Einlagen. |
| [`timeactivities`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TimeActivity) | Die Tabelle &quot;`timeactivities`&quot; enthält Zeitdatensätze für Anbieter und/oder Mitarbeiter und enthält die Zeit, die Aktivitäts-ID, Mitarbeiter/Anbieter-Informationen, die protokollierte Zeit, die Beschreibung der Aktivität und das aufgezeichnete Datum. |
| [`transfers`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Transfer) | Die Tabelle `transfers` enthält Informationen zu den zwischen Konten umgeschlagenen Fonds. Zu den Attributen gehören die Transfer-ID, der Betrag, die Kontoinformationen und das Datum. |
| [`vendorcredits`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/VendorCredit) | Gutschriften von Anbietern sind AP-Transaktionen, bei denen es sich um Erstattungen oder Gutschriften an Anbieter handelt. Die Tabelle &quot;`vendorcredits`&quot; enthält die Kreditkennung des Anbieters, Informationen zu Zeileneinträgen, Informationen zum Anbieter, AP-Konto, Gesamtbetrag und Datum. |

{style="table-layout:auto"}

## Entitäten in der Namensliste {#namelistentities}

| **Tabellenname** | **Beschreibung** |
|-----|-----|
| [`accounts`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Account) | Diese Tabelle enthält die Konto-ID, den Namen, den Status, den Typ, den Saldo, die Währung und die Erstellungszeit. |
| [`budgets`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Budget) | In dieser Tabelle werden alle Informationen zu Unternehmenshaushalten aufgeführt, einschließlich Budget-ID, Name, Start- und Enddatum, Typ, Status und Details. |
| [`classes`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Class) | Klassen, die auf Detailzeilen von Transaktionen angewendet werden, ermöglichen es Ihnen, Segmente zu verfolgen, die nicht an einen Kunden oder ein Projekt gebunden sind. Diese Tabelle zeichnet die Klassen-ID, den Namen, die Unterklasse und den Status auf. |
| [`customers`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Customer) | Die Tabelle &quot;`customers`&quot; enthält alle Informationen zu Ihren Kunden, einschließlich ID, Name, Abrechnungs- und Lieferadresse, Telefonnummer und E-Mail-Adresse des Kunden. |
| [`departments`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Department) | Die Tabelle &quot;`departments`&quot; enthält die ID, den Namen und den Typ der Abteilung (Unterabteilung im Vergleich zur obersten Abteilung). |
| [`employees`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Employee) | Die Tabelle `employees` enthält Informationen zu den Personen, die für Ihr Unternehmen arbeiten. Zu den Attributen gehören die Mitarbeiter-ID, der Name, die Adresse, die Telefonnummer und die abrechnungsfähigen Informationen, wenn das Unternehmen für die Gehaltsabrechnung aktiviert ist. |
| [`items`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Item) | Die Tabelle `items` enthält Details zu Produkten oder Dienstleistungen, die Ihr Unternehmen verkauft. Diese Tabelle enthält die Informationen zu Element-ID, Name, Beschreibung, Stückpreis, Typ, Kaufinformationen, manueller Menge sowie Informationen zu Erträgen und Vermögenswerten. |
| [`paymentmethods`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/PaymentMethod) | Die Tabelle `paymentmethods` enthält die Zahlungsmethode für Waren und Dienstleistungen. Sie enthält die Zahlungs-ID, den Typ und den Namen. |
| [`taxagencies`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxAgency) | Diese Tabelle enthält Informationen über Steueragenturen, einschließlich der Kennung der Steuerbehörde, sowie Nachverfolgungsinformationen zu Käufen und Verkäufen. |
| [`taxcodes`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxCode) | Steuercodes werden verwendet, um den Steuerstatus (steuerpflichtig gegenüber nicht steuerpflichtig) von Produkten, Dienstleistungen und Kunden zu verfolgen. Die Tabelle `taxcodes` enthält die Kennung des Steuercodes, den Namen, die Beschreibung, den Status, den Steuerstatus, den Steuersatz und die Steuergruppe. |
| [`taxrates`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/TaxRate) | Steuersätze werden zur Berechnung der Steuerschulden verwendet. Diese Tabelle enthält die Steuersatz-ID, den Namen, die Beschreibung, den Steuersatz, die Steueragentur und mehr. |
| [`terms`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Term) | Diese Einheit stellt die Bedingungen dar, unter denen Verkäufe getätigt werden. Die Tabelle der Begriffe enthält die Begriffe ID, Name, Typ, Rabattprozentsatz und Fälligkeitstage. |
| [`vendors`](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/Vendor) | Die Tabelle &quot;Anbieter&quot;enthält Informationen zu den Anbietern, von denen Sie kaufen. Zu den Tabellenattributen gehören die Anbieter-ID, der Firmenname, die Kundennummer, der Kontostand, der Status 1099, die Rechnungsadresse, die Telefonnummer, die E-Mail-Adresse und die Webadresse. |

{style="table-layout:auto"}

## Verwandte:

* [Verbinden [!DNL QuickBooks]](../integrations/quickbooks.md)
* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
