---
title: Formatieren und Importieren von E-Commerce-Daten
description: Lernen Sie die idealen Datenformate kennen, die zum Hochladen von E-Commerce-Daten verwendet werden können.
exl-id: 7b910f78-9a5a-4d5d-a8b7-1b0b76304afe
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Formatieren und Importieren von Daten

Wenn Sie eine Integration verwenden, die derzeit nicht von [!DNL Adobe Commerce Intelligence] unterstützt wird, können Sie dennoch die Funktion [Datei-Upload](using-file-uploader.md) verwenden, um Ihre Daten in Ihre Data Warehouse zu übertragen. In diesem Thema werden die idealen Datenformate für das Hochladen von E-Commerce-Daten behandelt.

## `Orders`

Die `orders` sollte für jede Transaktion, die das Unternehmen durchgeführt hat, eine Zeile enthalten. Zu den potenziellen Spalten gehören:

| Spaltenname | Beschreibung |
|----|----|
| `Order ID` | Die Bestell-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der Primärschlüssel für die Tabelle. |
| `Customer` | Der Kunde, der die Bestellung aufgegeben hat. |
| `Order total` | Die Gesamtzahl der Bestellungen. Dies kann eine berechnungsbasierte Spalte sein, bei der Werte in anderen Spalten - wie Zwischensumme und Versand - die Summe für diese Spalte bilden. |
| `Currency` | Die Währung, in der die Bestellung bezahlt wurde. Einschließen, falls relevant. |
| ` Order status` | Der Status der Bestellung, wie `In Progress`, `Refunded` oder `Complete`. Der Wert dieser Spalte ändert sich (falls nicht vollständig). Neue und aktualisierte Daten können mit der Funktion [Daten anhängen](../../../data-analyst/importing-data/connecting-data/using-file-uploader.md) auf der `File Uploads` Seite importiert werden. |
| `Acquisition/marketing channel` | Der Akquise- oder Marketing-Kanal, über den der Kunde, der die Bestellung aufgegeben hat, weitergeleitet wurde. |
| `Order datetime` | Datum und Uhrzeit der Erstellung der Bestellung. |
| `Order updated at` | Datum und Uhrzeit der letzten Änderung des Bestelldatensatzes. |

{style="table-layout:auto"}

## `Order detail/items` {#itemstable}

Die `order_detail / items` sollte für jedes einzelne Element in jeder Reihenfolge eine Zeile enthalten. Zu den potenziellen Spalten gehören:

| Spaltenname | Beschreibung |
|----|----|
| `Order item ID` | Die Bestellartikel-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der `primary key` für die Tabelle. |
| `Order ID` | Die ID der Bestellung. |
| `Product ID` | Die Produkt-ID. |
| `Product name` | Der Name des Produkts. |
| `Product's unit price` | Der Preis für eine einzelne Einheit des Produkts. |
| `Quantity` | Die Menge des Produkts in der Bestellung. |

## `Customers` {#customerstable}

Die `customers` sollte für jedes Kundenkonto eine Zeile enthalten. Zu den potenziellen Spalten gehören:

| Spaltenname | Beschreibung |
|----|----|
| `Customer ID` | Die Kunden-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der Primärschlüssel für die Tabelle. |
| `Customer created at` | Datum und Uhrzeit der Erstellung des Kundenkontos. |
| `Customer modified at` | Datum und Uhrzeit der letzten Änderung des Kontos des Kunden. |
| `Acquisition/marketing channel source` | Der Akquise- oder Marketing-Kanal, von dem der Kunde weitergeleitet wurde. |
| `Demographic info` | Demografische Informationen wie Altersbereich und Geschlecht können zur Segmentierung Ihrer Berichte verwendet werden. |
| `Acquisition/marketing channel` | Der Akquise- oder Marketing-Kanal, über den der Kunde, der die Bestellung aufgegeben hat, weitergeleitet wurde. |

## `Subscription payments`

Die `subscriptions` sollte für jede Abonnementzahlung eine Zeile enthalten. Zu den potenziellen Spalten gehören:

| Spaltenname | Beschreibung |
|----|----|
| `Subscription ID` | Die Abonnement-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der Primärschlüssel für die Tabelle. |
| `Customer ID` | Die ID des Kunden, der die Zahlung geleistet hat. |
| `Payment amount` | Der Betrag der Abonnementzahlung. |
| `Start date` | Der Anfangsdatum-/-zeitpunkt des Zeitraums, den die Zahlung abdeckt. |
| `End date` | Das Enddatum/die Endzeit des Zeitraums, den die Zahlung abdeckt. |
