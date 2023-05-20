---
title: eCommerce-Daten formatieren und importieren
description: Erfahren Sie mehr über die idealen Datenformate zum Hochladen von eCommerce-Daten.
exl-id: 7b910f78-9a5a-4d5d-a8b7-1b0b76304afe
source-git-commit: 3bf4829543579d939d959753eb3017364c6465bd
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Formatieren und Importieren von Daten

Wenn Sie eine Integration verwenden, die derzeit nicht von [!DNL Adobe Commerce Intelligence], können Sie weiterhin die [Funktion &quot;Datei-Upload&quot;](using-file-uploader.md) , um Ihre Daten in Ihre Data Warehouse zu übertragen. In diesem Thema werden die idealen Datenformate zum Hochladen von E-Commerce-Daten behandelt.

## `Orders` table

Die `orders` -Tabelle sollte für jede Transaktion, die das Unternehmen getätigt hat, eine Zeile enthalten. Mögliche Spalten:

| Spaltenname | Beschreibung |
|----|----|
| `Order ID` | Die Bestell-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der Primärschlüssel für die Tabelle. |
| `Customer` | Der Kunde, der die Bestellung aufgegeben hat. |
| `Order total` | Die Gesamtbestellung. Dies kann eine berechenbasierte Spalte sein, in der Werte in anderen Spalten - wie z. B. Zwischensumme und Versand - die Summe für diese Spalte ausmachen. |
| `Currency` | Die Währung, in der die Bestellung bestellt wurde. Gegebenenfalls einschließen. |
| ` Order status` | Der Status der Bestellung, z. B. `In Progress`, `Refunded`oder `Complete`. Der Wert dieser Spalte ändert sich (falls nicht vollständig). Neue und aktualisierte Daten können mit der [Funktion &quot;Daten anhängen&quot;](../../../data-analyst/importing-data/connecting-data/using-file-uploader.md) auf `File Uploads` Seite. |
| `Acquisition/marketing channel` | Der Akquise- oder Marketingkanal, von dem der Kunde, der die Bestellung aufgegeben hat, verwiesen wurde. |
| `Order datetime` | Datum und Uhrzeit der Erstellung der Bestellung. |
| `Order updated at` | Datum und Uhrzeit der letzten Änderung am Bestelldatensatz. |

{style="table-layout:auto"}

## `Order detail/items` table {#itemstable}

Die `order_detail / items` -Tabelle sollte für jedes einzelne Element in jeder Reihenfolge eine Zeile enthalten. Mögliche Spalten:

| Spaltenname | Beschreibung |
|----|----|
| `Order item ID` | Die Bestellelement-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der `primary key` für die Tabelle. |
| `Order ID` | Die ID der Bestellung. |
| `Product ID` | Die Kennung des Produkts. |
| `Product name` | Der Name des Produkts. |
| `Product's unit price` | Der Preis für eine Einheit des Produkts. |
| `Quantity` | Die Menge des Produkts in der Bestellung. |

## `Customers` table {#customerstable}

Die `customers` sollte für jedes Kundenkonto eine Zeile enthalten. Mögliche Spalten:

| Spaltenname | Beschreibung |
|----|----|
| `Customer ID` | Die Kunden-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der Primärschlüssel für die Tabelle. |
| `Customer created at` | Datum und Uhrzeit der Erstellung des Kundenkontos. |
| `Customer modified at` | Datum und Uhrzeit der letzten Änderung des Kundenkontos. |
| `Acquisition/marketing channel source` | Der Akquise- oder Marketingkanal, von dem der Kunde verwiesen wurde. |
| `Demographic info` | demografische Informationen wie Altersgruppe und Geschlecht können zur Segmentierung Ihrer Berichte verwendet werden. |
| `Acquisition/marketing channel` | Der Akquise- oder Marketingkanal, von dem der Kunde, der die Bestellung aufgegeben hat, verwiesen wurde. |

## `Subscription payments` table

Die `subscriptions` sollte für jede Abonnement-Zahlung eine Zeile enthalten. Mögliche Spalten:

| Spaltenname | Beschreibung |
|----|----|
| `Subscription ID` | Die Anmelde-ID sollte für jede Zeile in der Tabelle eindeutig sein. Außerdem ist dies normalerweise der Primärschlüssel für die Tabelle. |
| `Customer ID` | Die ID des Kunden, der die Zahlung getätigt hat. |
| `Payment amount` | Die Höhe der Abonnement-Zahlung. |
| `Start date` | Der Startzeitpunkt des Zeitraums, für den die Zahlung gilt. |
| `End date` | Der Endzeitpunkt des Zeitraums, für den die Zahlung gilt. |
