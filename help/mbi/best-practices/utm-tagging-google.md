---
title: UTM-Tracking in Google Analytics
description: Erfahren Sie mehr über Best Practices für UTM-Tracking (Tagging) in Google Analytics.
exl-id: 70bfd855-3b3f-469b-99bc-deb8251904b7
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# UTM-Tracking

`UTM`-Tracking ist eine Tagging-Konvention für URLs, mit der Sie analysieren können, woher Ihre Benutzer kommen. Wenn Sie sich die URLs ansehen, auf die Sie in den meisten Marketing-E-Mail- oder Banneranzeigen klicken, sehen Sie UTM-Tagging. Es sind diese langen Verbindungen, die mit Dingen wie `utm\_source` und `utm\_medium` enden.

[!DNL Google Analytics] verwendet `UTM`-Tagging, um herauszufinden, wo Ihr Traffic herkommt. Einige dieser Informationen stammen vom [HTTP Referrer](https://en.wikipedia.org/wiki/HTTP_referer) aber der Rest muss mit `UTM` Parametern angegeben werden. Wenn Sie `google adwords` oder `email marketing` sehen, bedeutet dies, dass diese `UTM` Parameter vom ursprünglichen Link-Klick aufgezeichnet und dann in den Cookies der Benutzer gespeichert werden. Von dort aus verwendet [!DNL Google Analytics] diese Daten, um [interessante Verhaltensweisen“ ](../data-analyst/analysis/google-track-user-acq.md) Ihrer Site zuzuordnen. Wenn Sie verstehen, wofür diese Parameter bestimmt sind, können Sie verstehen, wie UTM-Tagging am besten eingerichtet und verwendet werden.

## Best Practices für UTM-Tagging

Im Folgenden sind die fünf wichtigsten Aspekte aufgeführt, die Sie beim Einrichten Ihrer URLs mit `UTM`-Tagging beachten müssen.

### 1. Ziel ist es, jede URL zu taggen, die Sie steuern können, wenn sie auf Ihre Site kommt

Jedes Mal, wenn Sie Personen bitten, auf einen Link zu klicken, sollten Sie `UTM` Tagging einrichten. Dazu gehören all Ihre E-Mail-Links (Ihr E-Mail-Dienstleister hat wahrscheinlich eine Möglichkeit, Ihre URLs automatisch zu taggen), Anzeigen-Links, Presseartikel, Blog-Posts.

### 2. Verwenden eines Tools zum Erstellen der URL

`UTM`-getaggte URLs können umständlich sein. Anstatt zu versuchen, sie mit langer Hand zu tippen, verwenden Sie ein Tool [wie dieses](https://support.google.com/analytics/answer/1033867?hl=en), um Ihnen zu helfen. Dadurch wird sichergestellt, dass Sie alle sinnvollen Parameter zur URL hinzufügen und die URL kopieren und einfügen können. Um Social-Media-Links zu verwalten, bieten Tools wie [!DNL Hootsuite] die Option, allen Ihren Links benutzerdefinierte URL-Parameter hinzuzufügen.

### 3. Achten Sie in den Parameterwerten auf Groß- und Kleinschreibung

Beachten Sie, dass sich das Tag `utm\_source=adwords` von `utm\_source=Adwords` unterscheidet. Erwäge, alles kleingeschrieben zu machen.

### 4. UTM-Parameterwerte in der Datenbank speichern

Jedes Mal, wenn eine Transaktion oder ein Ereignis stattfindet, möchten Sie die Leistung Ihrer Marketing-Aktivitäten bewerten. Lesen Sie dazu die Werte der UTM-Parameterwerte aus dem [[!DNL Google Analytics] Cookie in Ihre Datenbank](../data-analyst/analysis/google-track-user-acq.md).

### 5. Überlegen Sie, wie Sie Kampagnen benennen

Um verfolgen zu können, wie sich Ihre Marketing-Maßnahmen im Laufe der Zeit verbessern, müssen Sie Ihre Namenskonventionen intelligent einhalten. Halten Sie es einfach und minimieren Sie so viel wie möglich. Komplizierte Benennungssysteme sind schwieriger zu verwalten.

Sobald Sie diese Daten in Ihrer Datenbank erfassen, können Sie die Leistung Ihres Marketings und Ihrer Werbung durch eine komplexere Analyse bewerten, einschließlich [Kundenlebenszeitwert](../data-analyst/analysis/ess-expected-ltv.md), [Wiederholungskaufraten](../data-analyst/analysis/repurchase-behavior.md) und [Durchschnittlicher Bestellwert](../data-analyst/analysis/basic-analytics.md).
