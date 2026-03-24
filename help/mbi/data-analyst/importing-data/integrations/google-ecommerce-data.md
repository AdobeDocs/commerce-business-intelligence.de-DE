---
title: '[!DNL Google ECommerce] Daten'
description: Erfahren Sie, welche Datentypen für Google E-Commerce freigegeben werden.
exl-id: 8e5d8863-f003-4c38-95c5-660bcbff48da
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/tGcSyz6DHcusK-RomMkRZoyY7acXb0dmXlHcc5pW7cg
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 158
ht-degree: 0%

---

# Erwartete [!DNL Google ECommerce]

Nachdem Ihr [!DNL Google ECommerce]-Konto erfolgreich mit [!DNL Commerce Intelligence] verbunden wurde, beginnt das System mit dem Import von Daten in eine Tabelle mit dem Titel `ecommerce`. Diese Tabelle zeichnet für jede Transaktion eine Datenzeile auf. Dies umfasst die folgenden Datenspalten auf Auftragsebene:

| Spaltenname | Beschreibung |
|-----|-----|
| `\_id` | Diese Spalte ist der Primärschlüssel. |
| `accountId` | Diese Spalte enthält die Konto-ID, die mit Ihrem [!DNL Google Analytics] eCommerce-Konto verknüpft ist. |
| `profileName` | Diese Spalte enthält den Namen Ihres [!DNL Google Analytics]. |
| `profileId` | Diese Spalte enthält Ihre [!DNL Google Analytics]. |
| `socialNetwork` | Diese Spalte enthält den Namen des sozialen Netzwerks (z. B. [!DNL Facebook] oder [!DNL YouTube]) |
| `campaign` | Diese Spalte enthält den Kampagnennamen (z. B. [`utm\_campaign`](https://support.google.com/analytics/answer/1033867?hl=en)). |
| `medium` | Diese Spalte enthält den Mediennamen (z. B. [`utm\_medium`](https://support.google.com/analytics/answer/1033867?hl=en)) |
| `source` | Diese Spalte enthält den Quellnamen. (z. B. [`utm\_source`](https://support.google.com/analytics/answer/1033867?hl=en)) |
| `keyword` | Diese Spalte enthält die Keyword-Beschreibung (z. B. [`utm\_term`](https://support.google.com/analytics/answer/1033867?hl=en)) |
| `transactionId` | Diese Spalte enthält die Bestell-ID. Dies wird verwendet, um die Verweisdaten wieder mit Ihren Bestelldaten zu verbinden. |
| `updated\_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. |

{style="table-layout:auto"}
