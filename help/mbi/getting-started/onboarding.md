---
title: Onboarding von Adobe Commerce Intelligence
description: Weitere Informationen zum Onboarding von Adobe Commerce Intelligence.
exl-id: e0cce957-af2c-4514-9afd-c9aaa651a4f0
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 5e80ff8f8ec76996b88a22b115be696b110581be
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Onboarding [!DNL Adobe Commerce Intelligence]

Die Onboarding-Fragen im Zusammenhang mit `store`- und `database` stellen sicher, dass Sie Ihre Berichte korrekt einrichten. Mit diesen Antworten stellt Adobe Ihre Berichte bereit, die genau auf die Einrichtung Ihres Shops zugeschnitten sind.

## Store-Einstellungen

- *Akzeptiert Ihr Geschäft einen Gast-Checkout?* - Wählen Sie **Ja**, wenn Sie Kunden erlauben, einen Kauf in Ihrem Geschäft zu tätigen, ohne sich für ein Konto zu registrieren.

- `Timezone` : Wählen Sie die `timezone` aus, in der Ihre Berichte angezeigt werden sollen.

- `Currency` : Wählen Sie die `currency` aus, in der Ihr Store betrieben wird.

- `Your week starts on...` : Wählen Sie den Wochentag aus, an dem die Woche in Ihren Berichten beginnen soll.

- *Welche Version von Commerce verwenden Sie?* : Wählen Sie die `currency` aus, in der Ihr Store betrieben wird.

- *Ist Ihr Geschäft in der Europäischen Union ansässig?* - Wenn Sie `Yes` auf diese Frage beantworten, hostet Adobe Ihre Data Warehouse und alle Ihre Daten in der Europäischen Union in Übereinstimmung mit der DSGVO.

## Datenbankeinstellungen

- `Database name` - Wie lautet *Name der [!DNL MySQL]-Datenbank* in der sich Ihre Commerce-Transaktionsdaten befinden?

- `Table prefix (optional)` - Werden den in Ihrer Commerce-Datenbank enthaltenen Tabellen Elemente vorangestellt (z. B. `store_`)? Dies ist normalerweise nicht der Fall, aber es ist eine Anpassung, die vorgenommen werden kann.
