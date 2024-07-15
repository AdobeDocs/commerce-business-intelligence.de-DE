---
title: UTM-Tracking in Google Analytics
description: Erfahren Sie mehr über Best Practices für das UTM-Tracking (Tagging) in Google Analytics.
exl-id: 70bfd855-3b3f-469b-99bc-deb8251904b7
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# UTM-Tracking

`UTM`-Tracking ist eine Tagging-Konvention für URLs, mit der Sie analysieren können, woher Ihre Benutzer kommen. Wenn Sie sich die URLs ansehen, auf die Sie in den meisten Marketing-E-Mail- oder Banneranzeigen klicken, sehen Sie das UTM-Tagging. Es sind die langen Verknüpfungen, die mit Dingen wie `utm\_source` und `utm\_medium` enden.

[!DNL Google Analytics] verwendet `UTM`-Tagging, um zu erfahren, woher Ihr Traffic stammt. Einige dieser Informationen stammen aus dem [HTTP-Referrer](https://en.wikipedia.org/wiki/HTTP_referer), der Rest muss jedoch mit `UTM` -Parametern angegeben werden. Wenn Sie `google adwords` oder `email marketing` sehen, bedeutet dies, dass diese `UTM` Parameter vom ursprünglichen Link-Klick aufgezeichnet und dann in den Cookies der Benutzer gespeichert werden. Von dort verwendet [!DNL Google Analytics] diese Daten, um [interessante Verhaltensweisen](../data-analyst/analysis/google-track-user-acq.md) auf Ihrer Site zuzuordnen. Wenn Sie wissen, wofür diese Parameter sind, können Sie nachvollziehen, wie Sie das UTM-Tagging am besten einrichten und verwenden.

## Best Practices für UTM-Tagging

Im Folgenden werden die fünf wichtigsten Elemente aufgelistet, die beim Einrichten Ihrer URLs mit `UTM` -Tagging beachtet werden müssen.

### 1. Ziel ist es, jede URL zu taggen, die Sie steuern können, wenn Sie zu Ihrer Site gelangen.

Jedes Mal, wenn Sie Personen auffordern, auf einen Link zu klicken, sollten Sie `UTM`-Tagging einrichten. Dazu gehören alle Ihre E-Mail-Links (Ihr E-Mail-Dienstanbieter hat wahrscheinlich eine Möglichkeit, Ihre URLs automatisch mit Tags zu versehen), Werbe-Links, Presseartikel, Blog-Beiträge.

### 2. Verwenden Sie ein Tool, um die URL zu erstellen

Mit `UTM` getaggte URLs können schwerfällig sein. Statt zu versuchen, sie einseitig einzugeben, verwenden Sie ein Werkzeug [wie dieses](https://support.google.com/analytics/answer/1033867?hl=en), um Ihnen zu helfen. Dadurch wird sichergestellt, dass Sie alle sinnvollen Parameter zur URL hinzufügen und die URL direkt kopieren und einfügen können. Zum Verwalten von Social-Links enthalten Tools wie [!DNL Hootsuite] die Option, benutzerdefinierte URL-Parameter zu allen Links hinzuzufügen.

### 3. Achten Sie bei den Parameterwerten auf die Groß-/Kleinschreibung.

Beachten Sie dabei, dass das Tag `utm\_source=adwords` ein anderes Tag als `utm\_source=Adwords` ist. Erwägen Sie, alles in Kleinbuchstaben zu schreiben.

### 4. Speichern Sie die UTM-Parameterwerte in Ihrer Datenbank.

Jedes Mal, wenn eine Transaktion oder ein Ereignis eintritt, möchten Sie die Leistung Ihrer Marketing-Aktivitäten bewerten. Sie können dies tun, indem Sie die Werte der UTM-Parameterwerte aus dem [[!DNL Google Analytics] Cookie in Ihre Datenbank lesen](../data-analyst/analysis/google-track-user-acq.md).

### 5. Denken Sie darüber nach, wie Sie Kampagnen benennen

Damit Sie verfolgen können, wie sich Ihre Marketing-Bemühungen im Laufe der Zeit verbessern, müssen Sie Ihre Benennungskonventionen mit Vorsicht beachten. Halten Sie es einfach und minimieren Sie so viel wie möglich. Die Verwaltung komplizierter Benennungssysteme ist schwieriger.

Nachdem Sie diese Daten in Ihrer Datenbank erfasst haben, können Sie die Leistung Ihres Marketing- und Werbegeschäfts durch eine komplexere Analyse bewerten, einschließlich [Kundenlebenszeitwert](../data-analyst/analysis/ess-expected-ltv.md), [Wiederholungskäufe](../data-analyst/analysis/repurchase-behavior.md) und [durchschnittlicher Bestellwert](../data-analyst/analysis/basic-analytics.md).
