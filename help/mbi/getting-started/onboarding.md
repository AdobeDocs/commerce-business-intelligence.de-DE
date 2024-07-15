---
title: Onboarding von Adobe Commerce Intelligence
description: Informationen zum Onboarding von Adobe Commerce Intelligence.
exl-id: e0cce957-af2c-4514-9afd-c9aaa651a4f0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Onboarding [!DNL Adobe Commerce Intelligence]

Die Onboarding-Fragen im Zusammenhang mit den Einstellungen für `store` und `database` stellen sicher, dass Sie die Berichterstellung korrekt einrichten. Mit diesen Antworten stellt Adobe Ihre Berichte bereit, die genau auf das Setup Ihres Stores zugeschnitten sind.

## Speichereinstellungen

- *Akzeptiert Ihr Store ein Auschecken als Gast?* - Wählen Sie **yes** aus, wenn Sie Kunden erlauben, einen Kauf in Ihrem Geschäft abzuschließen, ohne sich für ein Konto zu registrieren.

- `Timezone` - Wählen Sie den `timezone` aus, in dem Ihre Berichterstellung angezeigt werden soll.

- `Currency` - Wählen Sie die `currency` aus, in der Ihr Store tätig ist.

- `Your week starts on...` - Wählen Sie den Wochentag aus, der in Ihren Berichten als Wochenstart verwendet werden soll.

- *Welche Version von Commerce verwenden Sie?* - Wählen Sie die `currency` aus, in der Ihr Store tätig ist.

- *Ist Ihr Geschäft in der Europäischen Union ansässig?* - Wenn Sie `Yes` auf diese Frage antworten, hostet Adobe Ihre Data Warehouse und all Ihre Daten in der Europäischen Union gemäß der DSGVO.

## Datenbankeinstellungen

- `Database name` - Wie lautet der *Name der [!DNL MySQL] Datenbank*, in der sich Ihre Commerce-Transaktionsdaten befinden?

- `Table prefix (optional)` - Sind die in Ihrer Commerce-Datenbank enthaltenen Tabellen von irgendetwas (z. B. `store_`) vorangestellt? Dies ist normalerweise nicht der Fall, aber es ist eine Anpassung, die vorgenommen werden kann.
