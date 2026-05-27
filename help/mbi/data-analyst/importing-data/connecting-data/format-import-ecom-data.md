---
title: Formatieren und Importieren von E-Commerce-Daten
description: Lernen Sie die idealen Datenformate kennen, die zum Hochladen von E-Commerce-Daten verwendet werden können.
exl-id: 7b910f78-9a5a-4d5d-a8b7-1b0b76304afe
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/3Aa9DgQL0H9cNeJOJ7-qHkROOkphjzpQkDvJ0KwOIwY
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 460
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
