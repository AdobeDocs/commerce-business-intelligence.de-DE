---
title: Onboarding von Adobe Commerce Intelligence
description: Weitere Informationen zum Onboarding von Adobe Commerce Intelligence.
exl-id: e0cce957-af2c-4514-9afd-c9aaa651a4f0
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
TQID: https://experienceleague.adobe.com/36wmj-7QyDdemBWFwHTf1NJkd4H06tED9FZPqhFz8eg
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: f42e0a1a-0d79-488d-a83f-f2c30672b137
subfeature_v2: id: bcbf87e7-9b75-4596-bffe-0f376b4c73a7
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 194
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
