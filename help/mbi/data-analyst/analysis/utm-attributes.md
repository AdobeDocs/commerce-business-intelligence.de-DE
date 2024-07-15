---
title: Google Analytics- und UTM-Zuordnung
description: Erfahren Sie mehr über den Quellzuordnungsprozess der Google Analytics.
exl-id: 48b8a3d3-f1ac-4d3f-8f65-db1245c9ae0a
role: Admin, Data Architect, Data Engineer, User
feature: Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# [!DNL Google Analytics] und UTM-Attribution

Es ist wichtig, [Benutzer-Akquise-Quelle verfolgen](../../data-analyst/analysis/google-track-user-acq.md), um [die leistungsschwächsten Werbekampagnen zu identifizieren](../../data-analyst/analysis/most-value-source-channel.md). In diesem Thema wird der Quellzuordnungsprozess von [!DNL Google Analytics] untersucht. Mit anderen Worten, welche Information wird aufgezeichnet, wenn.

## Was ist Attribution?

Bei `Attribution` geht es darum, eine Verweisquelle für eine bestimmte Aktivität anzugeben. Bei diesen Aktivitäten handelt es sich normalerweise um Makrokonversionen oder Mikrokonversionen, bei denen es sich um Makros wie **Einkäufe** handelt, bei denen es sich um Mikro-Vorgänge wie **Registrierung, E-Mail-Anmeldung, Blogkommentar usw. handelt.**

Idealerweise wird jedes Mal, wenn ein Konversionsereignis auftritt, eine Verweisquelle aufgezeichnet. Aber wie wird die Quelle bestimmt?

Die Realität ist, dass Benutzer oft aus vielen Quellen kommen, bevor sie eine Mikro- oder Makrokonversion treffen/begehen. Beispielsweise können sie über organische Verbindungen zur Site gelangen, dann aussteigen, dann über eine gebührenpflichtige Suche anfangen, dann verlassen und dann direkt zur Site selbst kommen. Diese Quell-Tracking-Informationen werden der Site oft über UTM-Parameter bereitgestellt, aber es gibt auch komplexere Systeme. Konzentrieren Sie sich für Ihre Zwecke auf [UTM](https://support.google.com/analytics/answer/1033867?hl=en&amp;ref_topic=1032998).

## Wie ordnet [!DNL Google Analytics] Verweisquellen über UTM-Parameter zu?

Wenn die UTM-Parameter in der URL angegeben werden, werden sie analysiert und in ein [!DNL Google Analytics] [Cookie](https://en.wikipedia.org/wiki/HTTP_cookie) eingefügt. Wenn eine Website nicht über &quot;[!DNL Google Analytics]&quot; verfügt, hat dies keinen Sinn. [!DNL Google Analytics] verfügt über Regeln dafür, wie es mit einem Benutzer umgeht, der während seiner Lebensdauer mehrere URLs mit UTMs erreicht (mehr dazu später). Wenn die Website so konfiguriert ist, dass UTM-Parameter in einer externen Datenbank erfasst werden, wird bei einer Mikro- oder Makrokonversion das, was zum Zeitpunkt der Konvertierung im [!DNL Google Analytics] -Cookie enthalten ist, in die Datenbank repliziert.

## Erstklick vs. Letzter Klick

### Last-Click-Attribution

Die Attribution des letzten Klicks ist das gängigste Attributionsmodell, das von [!DNL Google Analytics] verwendet wird. In diesem Fall stellt das Cookie [!DNL Google Analytics] die UTM-Parameter für die letzte Quelle vor dem Konversionsereignis dar, und dies wird [in der Datenbank aufgezeichnet](../../data-analyst/analysis/google-track-user-acq.md). Das Cookie [!DNL Google Analytics] überschreibt nur die vorherigen UTM-Parameter, wenn der Benutzer auf eine neue URL klickt, die einen neuen Satz von UTM-Parametern enthält.

Betrachten Sie beispielsweise einen Benutzer, der zuerst eine Website über [!DNL Google Analytics] *gebührenpflichtige Suche* besucht, dann über *organische Suche* zurückkehrt und schließlich direkt *zur* Website zurückkehrt oder über einen *E-Mail-Link* **ohne UTM-Parameter** vor dem Konversionsereignis zurückkehrt. In diesem Beispiel sagt das Cookie [!DNL Google Analytics], dass die Quelle des Benutzers organisch ist, da dies die letzte Quelle vor der Konvertierung darstellt. Der *Pfad* des Benutzers vor diesem letzten Konversionsereignis wird ignoriert. Wenn der Benutzer stattdessen die Website über einen E-Mail-Link mit UTM besucht, würde das [!DNL Google Analytics] -Cookie sagen, dass die Quelle &quot;E-Mail&quot;ist. Wenn also im Cookie vorhandene UTM-Parameter vorhanden sind und der Benutzer über Direkt eingeht, zeigt das [!DNL Google Analytics] -Cookie die UTM-Parameter anstelle von &quot;direct&quot;.

>[!NOTE]
>
>Die [!DNL Google Analytics] -Cookie-Parameter eines bestimmten Benutzers werden gelöscht, wenn das Cookie [abläuft](https://developers.google.com/analytics/devguides/collection/analyticsjs/cookie-usage) oder wenn ein Benutzer seine Cookies im Browser löscht.*

### Erstklick-Attribution

Einige gebührenpflichtige Zuordnungstools ermöglichen es Ihnen, den &quot;Pancake-Stapel&quot;von Quellen im Pfad eines Benutzers zu erfassen. In diesem Fall würde uns die Attribution des ersten Klicks im obigen Beispiel die gebührenpflichtige Suche mitteilen. Alternativ können einige Websites eigene Cookies implementieren, die einen Pancake-Stapel erfassen und die erste Quelle in ihrer Datenbank speichern.

## Wie kann die Attribution analysiert werden?

[!DNL Google Analytics] verfügt über eine robuste Funktionalität in der Web-Oberfläche, mit der Sie vier verschiedene Attributionsmodelle durchführen können:

1. Erstklick
1. last click
1. linear (Aufteilung des Umsatzes gleichmäßig auf alle Quellen im Pfad)
1. gewichtete (benutzerdefinierte Attribution)

Nachdem Sie nun verstanden haben, was das Attributionsmodell für jede Mikro- oder Makrokonversion ist, lautet die Frage &quot;Was machen Sie mit der Gesamtheit der Konversionen eines Benutzers?&quot;  Betrachten Sie beispielsweise die aufgezeichneten UTMs basierend auf der GA-Logik des letzten Klicks:

* Benutzerregister unter &quot;Organisch&quot;
* Erstkauf des Benutzers unter Paid Search $5.00
* Zweiter Kauf des Benutzers unter E-Mail $50.00
* Dritter Kauf des Benutzers unter kostenlosen $10.00

Hier fragen Sie: &quot;Wie viel Umsatz habe ich aus der gebührenpflichtigen Suche erhalten? Von E-Mail?  Aus Bio?&quot; Sie könnten sagen, dass die Antworten 5, 50 und 10 sind (egal, welche Quelle zuletzt verwendet wurde), oder Sie könnten auch sagen, dass Sie alle Umsätze der ersten Quelle zuordnen (alle 65 gehen zu &quot;organisch&quot;). Sie können auch eine gewichtete Analyse anwenden oder das lineare Modell anwenden (d. h. ungefähr 22 pro Modell).

## Verwandte Dokumentation

* [Verfolgen der Verweisquelle für Bestellungen über [!DNL Google Analytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)
* [ [!DNL Google Adwords] Konto verbinden](../importing-data/integrations/google-adwords.md)
* [Steigerung des ROI bei Werbekampagnen](../analysis/roi-ad-camp.md)
* [Fünf Best Practices für das UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
