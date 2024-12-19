---
title: Onboarding von Adobe Commerce Intelligence
description: Weitere Informationen zum Onboarding von Adobe Commerce Intelligence.
exl-id: e0cce957-af2c-4514-9afd-c9aaa651a4f0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Onboarding [!DNL Adobe Commerce Intelligence]

Die Onboarding-Fragen im Zusammenhang mit `store`- und `database` stellen sicher, dass Sie Ihre Berichte korrekt einrichten. Mit diesen Antworten liefert Adobe Ihre Berichte, die genau auf die Einrichtung Ihres Shops zugeschnitten sind.

## Store-Einstellungen

- *Akzeptiert Ihr Geschäft einen Gast-Checkout?* - Wählen Sie **Ja**, wenn Sie Kunden erlauben, einen Kauf in Ihrem Geschäft zu tätigen, ohne sich für ein Konto zu registrieren.

- `Timezone` : Wählen Sie die `timezone` aus, in der Ihre Berichte angezeigt werden sollen.

- `Currency` : Wählen Sie die `currency` aus, in der Ihr Store betrieben wird.

- `Your week starts on...` : Wählen Sie den Wochentag aus, an dem die Woche in Ihren Berichten beginnen soll.

- *Welche Version von Commerce verwenden Sie?* : Wählen Sie die `currency` aus, in der Ihr Store betrieben wird.

- *Ist Ihr Geschäft in der Europäischen Union ansässig?* - Wenn Sie diese Frage `Yes` beantworten, hosten Sie Ihre Data Warehouse und alle Ihre Daten in der Europäischen Union in Adobe in Übereinstimmung mit der DSGVO.

## Datenbankeinstellungen

- `Database name` - Wie lautet *Name der [!DNL MySQL]-Datenbank* in der sich Ihre Commerce-Transaktionsdaten befinden?

- `Table prefix (optional)` - Werden den in Ihrer Commerce-Datenbank enthaltenen Tabellen Elemente vorangestellt (z. B. `store_`)? Dies ist normalerweise nicht der Fall, aber es ist eine Anpassung, die vorgenommen werden kann.
