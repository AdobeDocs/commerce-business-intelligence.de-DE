---
title: UTM-Tracking in Google Analytics
description: Erfahren Sie mehr über Best Practices für UTM-Tracking (Tagging) in Google Analytics.
exl-id: 70bfd855-3b3f-469b-99bc-deb8251904b7
role: Admin, Developer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
TQID: https://experienceleague.adobe.com/IX5oaIr8tbUUeA3ZrIQNUMnG8ApXMBS1hcpecqFW8kg
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: beb7a3c1-66ab-4786-b879-7621375b3c40
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 450
ht-degree: 0%

---

# UTM-Tracking

`UTM`-Tracking ist eine Tagging-Konvention für URLs, mit der Sie analysieren können, woher Ihre Benutzer kommen. Wenn Sie sich die URLs ansehen, auf die Sie in den meisten Marketing-E-Mail- oder Banneranzeigen klicken, sehen Sie UTM-Tagging. Es sind diese langen Verbindungen, die mit Dingen wie `utm\_source` und `utm\_medium` enden.

[!DNL Google Analytics] verwendet `UTM`-Tagging, um herauszufinden, wo Ihr Traffic herkommt. Einige dieser Informationen stammen vom [HTTP Referrer](https://en.wikipedia.org/wiki/HTTP_referer) aber der Rest muss mit `UTM` Parametern angegeben werden. Wenn Sie `google adwords` oder `email marketing` sehen, bedeutet dies, dass diese `UTM` Parameter vom ursprünglichen Link-Klick aufgezeichnet und dann in den Cookies der Benutzer gespeichert werden. Von dort aus verwendet [!DNL Google Analytics] diese Daten, um [interessante Verhaltensweisen“ &#x200B;](../data-analyst/analysis/google-track-user-acq.md) Ihrer Site zuzuordnen. Wenn Sie verstehen, wofür diese Parameter bestimmt sind, können Sie verstehen, wie UTM-Tagging am besten eingerichtet und verwendet werden.

## Best Practices für UTM-Tagging

Im Folgenden sind die fünf wichtigsten Aspekte aufgeführt, die Sie beim Einrichten Ihrer URLs mit `UTM`-Tagging beachten müssen.

### &#x200B;1. Ziel ist es, jede URL zu taggen, die Sie steuern können, wenn sie auf Ihre Site kommt

Jedes Mal, wenn Sie Personen bitten, auf einen Link zu klicken, sollten Sie `UTM` Tagging einrichten. Dazu gehören all Ihre E-Mail-Links (Ihr E-Mail-Dienstleister hat wahrscheinlich eine Möglichkeit, Ihre URLs automatisch zu taggen), Anzeigen-Links, Presseartikel, Blog-Posts.

### &#x200B;2. Verwenden eines Tools zum Erstellen der URL

`UTM`-getaggte URLs können umständlich sein. Anstatt zu versuchen, sie mit langer Hand zu tippen, verwenden Sie ein Tool [wie dieses](https://support.google.com/analytics/answer/1033867?hl=en), um Ihnen zu helfen. Dadurch wird sichergestellt, dass Sie alle sinnvollen Parameter zur URL hinzufügen und die URL kopieren und einfügen können. Um Social-Media-Links zu verwalten, bieten Tools wie [!DNL Hootsuite] die Option, allen Ihren Links benutzerdefinierte URL-Parameter hinzuzufügen.

### &#x200B;3. Achten Sie in den Parameterwerten auf Groß- und Kleinschreibung

Beachten Sie, dass sich das Tag `utm\_source=adwords` von `utm\_source=Adwords` unterscheidet. Erwäge, alles kleingeschrieben zu machen.

### &#x200B;4. UTM-Parameterwerte in der Datenbank speichern

Jedes Mal, wenn eine Transaktion oder ein Ereignis stattfindet, möchten Sie die Leistung Ihrer Marketing-Aktivitäten bewerten. Lesen Sie dazu die Werte der UTM-Parameterwerte aus dem [[!DNL Google Analytics] Cookie in Ihre Datenbank](../data-analyst/analysis/google-track-user-acq.md).

### &#x200B;5. Überlegen Sie, wie Sie Kampagnen benennen

Um verfolgen zu können, wie sich Ihre Marketing-Maßnahmen im Laufe der Zeit verbessern, müssen Sie Ihre Namenskonventionen intelligent einhalten. Halten Sie es einfach und minimieren Sie so viel wie möglich. Komplizierte Benennungssysteme sind schwieriger zu verwalten.

Sobald Sie diese Daten in Ihrer Datenbank erfassen, können Sie die Leistung Ihres Marketings und Ihrer Werbung durch eine komplexere Analyse bewerten, einschließlich [Kundenlebenszeitwert](../data-analyst/analysis/ess-expected-ltv.md), [Wiederholungskaufraten](../data-analyst/analysis/repurchase-behavior.md) und [Durchschnittlicher Bestellwert](../data-analyst/analysis/basic-analytics.md).
