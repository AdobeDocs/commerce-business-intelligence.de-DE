---
title: Erwartet[!DNL Google ECommerce]data
description: Erfahren Sie, welche Datentypen für Google ECommerce freigegeben werden.
exl-id: 8e5d8863-f003-4c38-95c5-660bcbff48da
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 3f16484f189f6b4a8b072d2e3514d2f170993d60
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Erwartet [!DNL Google ECommerce] data

Nach [!DNL Google ECommerce] -Konto erfolgreich mit [!DNL Commerce Intelligence], beginnt das System mit dem Import von Daten in eine Tabelle mit dem Titel `ecommerce`. Diese Tabelle zeichnet eine Datenzeile für jede Transaktion auf. Dazu gehören die folgenden Datenspalten auf Bestellebene:

| Spaltenname | Beschreibung |
|-----|-----|
| `\_id` | Diese Spalte ist der Primärschlüssel. |
| `accountId` | Diese Spalte enthält die Konto-ID, die Ihrer [!DNL Google Analytics] eCommerce-Konto. |
| `profileName` | Diese Spalte enthält Ihre [!DNL Google Analytics] Profilname. |
| `profileId` | Diese Spalte enthält Ihre [!DNL Google Analytics] Profil-ID. |
| `socialNetwork` | Diese Spalte enthält den Namen des sozialen Netzwerks (beispielsweise [!DNL Facebook]oder [!DNL YouTube]) |
| `campaign` | Diese Spalte enthält den Kampagnennamen (z. B. [`utm\_campaign`](https://support.google.com/analytics/answer/1033867?hl=en)). |
| `medium` | Diese Spalte enthält den mittleren Namen (z. B. [`utm\_medium`](https://support.google.com/analytics/answer/1033867?hl=en)) |
| `source` | Diese Spalte enthält den Quellnamen. (zum Beispiel: [`utm\_source`](https://support.google.com/analytics/answer/1033867?hl=en)) |
| `keyword` | Diese Spalte enthält die Suchbegriffbeschreibung (z. B. [`utm\_term`](https://support.google.com/analytics/answer/1033867?hl=en)) |
| `transactionId` | Diese Spalte enthält die Bestell-ID. Dadurch werden die Verweisdaten wieder in Ihre Bestellungsdaten eingefügt. |
| `updated\_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. |

{style="table-layout:auto"}
