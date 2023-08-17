---
title: UTM-Tracking in Google Analytics
description: Erfahren Sie mehr über Best Practices für das UTM-Tracking (Tagging) in Google Analytics.
exl-id: 70bfd855-3b3f-469b-99bc-deb8251904b7
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# UTM-Tracking

`UTM` Tracking ist eine Tagging-Konvention für URLs, mit der Sie analysieren können, woher Ihre Benutzer kommen. Wenn Sie sich die URLs ansehen, auf die Sie in den meisten Marketing-E-Mail- oder Banneranzeigen klicken, sehen Sie das UTM-Tagging. Es sind die langen Verknüpfungen, die mit Dingen wie `utm\_source` und `utm\_medium`.

[!DNL Google Analytics] uses `UTM` Tagging, um zu erfahren, woher Ihr Traffic stammt. Einige dieser Informationen stammen aus dem [HTTP-Verweis](https://en.wikipedia.org/wiki/HTTP_referer) aber der Rest muss man sich selbst versorgen `UTM` Parameter. Wenn `google adwords` oder `email marketing`, bedeutet dies `UTM` -Parameter, die vom ursprünglichen Link-Klick aufgezeichnet und dann in den Cookies der Benutzer gespeichert werden. Von dort aus: [!DNL Google Analytics] verwendet diese Daten für [Attribut interessanter Verhaltensweisen](../data-analyst/analysis/google-track-user-acq.md) auf Ihrer Site. Wenn Sie wissen, wofür diese Parameter sind, können Sie nachvollziehen, wie Sie das UTM-Tagging am besten einrichten und verwenden.

## Best Practices für UTM-Tagging

Im Folgenden werden die fünf wichtigsten Elemente aufgelistet, die Sie beim Einrichten Ihrer URLs mit `UTM` Tagging.

### 1. Ziel ist es, jede URL zu taggen, die Sie steuern können, wenn Sie zu Ihrer Site gelangen.

Jedes Mal, wenn Sie Personen auffordern, auf einen Link zu klicken, sollten Sie `UTM` Tagging. Dazu gehören alle Ihre E-Mail-Links (Ihr E-Mail-Dienstanbieter hat wahrscheinlich eine Möglichkeit, Ihre URLs automatisch mit Tags zu versehen), Werbe-Links, Presseartikel, Blog-Beiträge.

### 2. Verwenden Sie ein Tool, um die URL zu erstellen

`UTM`-getaggte URLs können schwerfällig sein. Verwenden Sie ein Tool, anstatt zu versuchen, sie einseitig einzugeben. [wie folgt](https://support.google.com/analytics/answer/1033867?hl=en) um Ihnen zu helfen. Dadurch wird sichergestellt, dass Sie alle sinnvollen Parameter zur URL hinzufügen und die URL direkt kopieren und einfügen können. Zum Verwalten von Social-Links, Tools wie [!DNL Hootsuite] enthalten die Option zum Hinzufügen benutzerdefinierter URL-Parameter zu allen Links.

### 3. Achten Sie bei den Parameterwerten auf die Groß-/Kleinschreibung.

Es ist wichtig, sich zu merken, dass das Tag `utm\_source=adwords` ist ein anderes Tag als `utm\_source=Adwords`. Erwägen Sie, alles in Kleinbuchstaben zu schreiben.

### 4. Speichern Sie die UTM-Parameterwerte in Ihrer Datenbank.

Jedes Mal, wenn eine Transaktion oder ein Ereignis eintritt, möchten Sie die Leistung Ihrer Marketing-Aktivitäten bewerten. Sie können dies tun, indem Sie die Werte der UTM-Parameterwerte aus der [[!DNL Google Analytics] Cookie in Ihrer Datenbank](../data-analyst/analysis/google-track-user-acq.md).

### 5. Denken Sie darüber nach, wie Sie Kampagnen benennen

Damit Sie verfolgen können, wie sich Ihre Marketing-Bemühungen im Laufe der Zeit verbessern, müssen Sie Ihre Benennungskonventionen mit Vorsicht beachten. Halten Sie es einfach und minimieren Sie so viel wie möglich. Die Verwaltung komplizierter Benennungssysteme ist schwieriger.

Sobald Sie diese Daten in Ihrer Datenbank erfassen, können Sie die Leistung Ihrer Marketing- und Werbemaßnahmen durch eine ausgefeiltere Analyse bewerten, einschließlich [Kundenlebenszeitwert](../data-analyst/analysis/ess-expected-ltv.md), [Wiederholungskäufe](../data-analyst/analysis/repurchase-behavior.md), und [Durchschnittlicher Bestellwert](../data-analyst/analysis/basic-analytics.md).
