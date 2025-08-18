---
title: Google Analytics und UTM Attribution
description: Erfahren Sie mehr über den Google Analytics-Quellattributionsprozess.
exl-id: 48b8a3d3-f1ac-4d3f-8f65-db1245c9ae0a
role: Admin, Data Architect, Data Engineer, User
feature: Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# [!DNL Google Analytics]- und UTM-Attribution

Es ist wichtig, die [Quelle der Benutzerakquise](../../data-analyst/analysis/google-track-user-acq.md) zu verfolgen, um [die Werbekampagnen mit der besten Performance zu ](../../data-analyst/analysis/most-value-source-channel.md). In diesem Thema wird der Prozess der [!DNL Google Analytics]-Quellattribution untersucht. Mit anderen Worten, welche Informationen wann aufgezeichnet werden.

## Was ist Attribution?

`Attribution` geht darum, eine Empfehlungsquelle für eine bestimmte Aktivität anzugeben. Diese Aktivitäten sind in der Regel Makro- oder Mikrokonversionen, Makro ist etwas wie **Käufe**, Mikro ist etwas wie **Registrierung, E-Mail-Anmeldung, Blog-Kommentar** und so weiter.

Idealerweise wird jedes Mal, wenn ein Konversionsereignis auftritt, eine Empfehlungsquelle aufgezeichnet. Aber wie wird die Quelle bestimmt?

Die Realität ist, dass Benutzer oft aus vielen Quellen kommen, bevor sie eine Mikro- oder Makrokonvertierung treffen/übertragen. Sie können zum Beispiel über Bio auf die Website kommen, dann die Website verlassen, dann über Paid Search kommen, dann die Website verlassen und dann direkt zur Website selbst kommen. Diese Tracking-Informationen werden der Website oft über UTM-Parameter bereitgestellt, es gibt jedoch auch komplexere Systeme. Konzentrieren Sie sich für Ihre Zwecke auf [UTM](https://support.google.com/analytics/answer/1033867?hl=en&ref_topic=1032998).

## Wie ordnet [!DNL Google Analytics] Verweisquellen über UTM-Parameter zu?

Wenn die UTM-Parameter für die URL angegeben werden, werden diese ausgewertet und in einem [!DNL Google Analytics] ([) ](https://en.wikipedia.org/wiki/HTTP_cookie). Wenn eine Website nicht über [!DNL Google Analytics] verfügt, macht es keinen Sinn, UTMs zu verwenden. [!DNL Google Analytics] verfügt über Regeln für den Umgang mit Benutzenden, die während ihres Lebenszyklus mehrere URLs mit UTMs aufrufen (mehr dazu später). Angenommen, die Website ist so konfiguriert, dass UTM-Parameter in einer externen Datenbank erfasst werden. Wenn eine Mikro- oder Makrokonvertierung stattfindet, wird alles, was sich zum Zeitpunkt der Konvertierung im [!DNL Google Analytics]-Cookie befindet, in die Datenbank repliziert.

## Erster Klick vs. letzter Klick

### Attribution Letzter Klick

Die Attribution Letztklick ist das häufigste Attributionsmodell, das von [!DNL Google Analytics] verwendet wird. In diesem Fall stellt das [!DNL Google Analytics]-Cookie die UTM-Parameter der letzten Quelle vor dem Konversionsereignis dar und wird [in der Datenbank aufgezeichnet](../../data-analyst/analysis/google-track-user-acq.md). Das [!DNL Google Analytics]-Cookie überschreibt nur die vorherigen UTM-Parameter, wenn der Benutzer auf eine neue URL klickt, die einen neuen Satz UTM-Parameter enthält.

Angenommen, ein Benutzer besucht eine Website zuerst über [!DNL Google Analytics] *Paid Search*, kehrt dann über *Organische Suche* zurück und kehrt schließlich direkt *oder über einen* E-Mail-Link ** ohne UTM-Parameter **vor dem Konversionsereignis zur** zurück. In diesem Beispiel besagt das [!DNL Google Analytics]-Cookie, dass die Quelle des Benutzers organisch ist, da dies die letzte Quelle vor der Konversion darstellt. Der *Pfad* des Benutzers vor diesem endgültigen Konversionsereignis wird ignoriert. Wenn der Benutzer die Website stattdessen über einen E-Mail-Link mit UTM besucht hat, würde das [!DNL Google Analytics]-Cookie sagen, dass die Quelle „E-Mail“ ist. Wenn also UTM-Parameter im Cookie vorhanden sind und der Benutzer über Direct eintritt, zeigt das [!DNL Google Analytics]-Cookie die UTM-Parameter anstelle von „direct“ an.

>[!NOTE]
>
>Die [!DNL Google Analytics] Cookie-Parameter eines bestimmten Benutzers werden gelöscht, wenn das Cookie [abläuft](https://developers.google.com/analytics/devguides/collection/analyticsjs/cookie-usage) oder wenn ein Benutzer seine Cookies im Browser löscht.*

### Attribution Erster Klick

Einige kostenpflichtige Attributionstools ermöglichen es Ihnen, „den Eierkuchen-Stapel“ von Quellen im Pfad eines Benutzers zu erfassen. In diesem Fall würde uns im obigen Beispiel die Attribution Erster Klick eine Paid Search mitteilen. Alternativ implementieren einige Websites ihre eigenen Cookies, die einen Pfannkuchen-Stapel erfassen und die erste Quelle in ihrer Datenbank speichern.

## Wie kann ich die Attribution analysieren?

[!DNL Google Analytics] Web-Oberfläche von verfügt über einige leistungsstarke Funktionen, mit denen Sie vier verschiedene Attributionsmodelle durchführen können:

1. Erster Klick
1. Letzter Klick
1. Linear (Teilt den Umsatz gleichmäßig auf alle Quellen im Pfad auf)
1. Gewichtete (benutzerdefinierte Attribution)

Nachdem Sie nun wissen, was das Attributionsmodell für jede Mikro- oder Makrokonvertierung ist, wird die Frage zu „Was machen Sie mit der Gesamtheit der Konversionen eines Benutzers?“.  Sehen Sie sich beispielsweise die UTMs an, die basierend auf der GA-Logik des letzten Klicks aufgezeichnet wurden:

* Benutzerregister unter „Organisch“
* Erster Kauf des Benutzers unter Paid Search $5.00
* Zweiter Kauf des Benutzers unter E-Mail $50.00
* Dritter Kauf des Nutzers unter Organic $10.00

Da fragt man sich: „Wie viel Umsatz machte mir die bezahlte Recherche? Von E-Mail?  Aus biologischem Anbau?“ Man könnte sagen, dass die Antworten 5, 50 und 10 sind (was auch immer die letzte Quelle war), oder man könnte auch sagen, dass man alle Einnahmen der ersten Quelle zuordnet (alle 65 gehen an Bio). Sie können auch einige gewichtete Analysen oder das lineare Modell (d. h. jeweils etwa 22) anwenden.

## Verwandte Dokumentation

* [Verfolgen Sie die Quelle der Bestellungsreferenz über  [!DNL Google Analytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Verfolgen Sie die Quelle der Benutzerreferenz in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Benutzergeräte-, Browser- und Betriebssystemdaten in der Datenbank tracken](../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../analysis/most-value-source-channel.md)
* [Konto  [!DNL Google Adwords] ](../importing-data/integrations/google-adwords.md)
* [Steigerung des ROI Ihrer Werbekampagnen](../analysis/roi-ad-camp.md)
* [Fünf Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
