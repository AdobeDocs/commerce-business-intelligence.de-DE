---
title: Onboarding von Adobe Commerce Intelligence
description: Erfahren Sie mehr über das Onboarding von Adobe Commerce Intelligence.
exl-id: e0cce957-af2c-4514-9afd-c9aaa651a4f0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Onboarding [!DNL Adobe Commerce Intelligence]

Die Onboarding-Fragen im Zusammenhang mit `store` und `database` -Einstellungen sicherstellen, dass Sie die Berichterstellung korrekt einrichten. Mit diesen Antworten stellt Adobe Ihre Berichte bereit, die genau auf das Setup Ihres Stores zugeschnitten sind.

## Speichereinstellungen

- *Akzeptiert Ihr Geschäft einen Gast-Checkout?* - Auswählen **yes** wenn Sie Kunden erlauben, in Ihrem Geschäft einen Kauf zu tätigen, ohne sich für ein Konto zu registrieren.

- `Timezone` - Wählen Sie die `timezone` in dem Sie Ihre Berichterstellung sehen möchten.

- `Currency` - Wählen Sie die `currency` , in dem Ihr Geschäft tätig ist.

- `Your week starts on...` - Wählen Sie den Wochentag aus, der in Ihren Berichten als Wochentag beginnen soll.

- *Welche Commerce-Version verwenden Sie?* - Wählen Sie die `currency` , in dem Ihr Geschäft tätig ist.

- *Ist Ihr Geschäft in der Europäischen Union ansässig?* - Wenn Sie antworten `Yes` zu dieser Frage hosten Adobe Ihre Data Warehouse und alle Ihre Daten in der Europäischen Union gemäß der DSGVO.

## Datenbankeinstellungen

- `Database name` - Was ist der *Name des [!DNL MySQL] Datenbank* Wo befinden sich Ihre Commerce-Transaktionsdaten?

- `Table prefix (optional)` - Sind die in Ihrer Commerce-Datenbank enthaltenen Tabellen durch irgendetwas (z. B. `store_`)? Dies ist normalerweise nicht der Fall, aber es ist eine Anpassung, die vorgenommen werden kann.
