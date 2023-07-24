---
title: Google Analytics und UTM-Zuordnung
description: Erfahren Sie mehr über den Quellzuordnungsprozess von Google Analytics.
exl-id: 48b8a3d3-f1ac-4d3f-8f65-db1245c9ae0a
role: Admin, Data Architect, Data Engineer, User
feature: Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# [!DNL Google Analytics] und UTM-Attribution

Es ist von entscheidender Bedeutung, [Benutzerakquise-Quelle verfolgen](../../data-analyst/analysis/google-track-user-acq.md) nach [Identifizieren von Werbekampagnen mit der besten Leistung](../../data-analyst/analysis/most-value-source-channel.md). Dieses Thema untersucht die [!DNL Google Analytics] Quellattributionsprozess. Mit anderen Worten, welche Information wird aufgezeichnet, wenn.

## Was ist Attribution?

`Attribution` Es geht darum, eine Verweisquelle für eine bestimmte Aktivität anzugeben. Bei diesen Aktivitäten handelt es sich normalerweise um Makrokonversionen oder Mikrokonversionen, wobei Makro-Vorgänge wie **purchases**, wobei Mikro Dinge wie **Registrierung, E-Mail-Anmeldung, Blog-Kommentar,** und so weiter.

Idealerweise wird jedes Mal, wenn ein Konversionsereignis auftritt, eine Verweisquelle aufgezeichnet. Aber wie wird die Quelle bestimmt?

Die Realität ist, dass Benutzer oft aus vielen Quellen kommen, bevor sie eine Mikro- oder Makrokonversion treffen/begehen. Beispielsweise können sie über organische Verbindungen zur Site gelangen, dann aussteigen, dann über eine gebührenpflichtige Suche anfangen, dann verlassen und dann direkt zur Site selbst kommen. Diese Quell-Tracking-Informationen werden der Site oft über UTM-Parameter bereitgestellt, aber es gibt auch komplexere Systeme. Für Ihre Zwecke konzentrieren Sie sich auf [UTM](https://support.google.com/analytics/answer/1033867?hl=en&amp;ref_topic=1032998).

## Wie funktioniert [!DNL Google Analytics] Attributverweisquellen über UTM-Parameter?

Wenn die UTM-Parameter in der URL angegeben sind, werden sie analysiert und in eine [!DNL Google Analytics] [Cookie](https://en.wikipedia.org/wiki/HTTP_cookie). Wenn eine Website nicht über [!DNL Google Analytics], hat es keinen Sinn, UTMs zu haben. [!DNL Google Analytics] enthält Regeln dafür, wie es mit einem Benutzer umgeht, der während seiner Lebensdauer mehrere URLs mit UTMs durchführt (mehr dazu später). Angenommen, die Website ist so konfiguriert, dass UTM-Parameter in einer externen Datenbank erfasst werden, wenn eine Mikro- oder Makrokonversion stattfindet, unabhängig davon, was in der [!DNL Google Analytics] -Cookie zum Zeitpunkt der Konvertierung in die Datenbank repliziert wird.

## Erstklick vs. Letzter Klick

### Last-Click-Attribution

Die Attribution des letzten Klicks ist das am häufigsten verwendete Attributionsmodell von [!DNL Google Analytics]. In diesem Fall wird die [!DNL Google Analytics] -Cookie stellt die UTM-Parameter für die neueste Quelle vor dem Konversionsereignis dar, und zwar [in der Datenbank aufgezeichnet](../../data-analyst/analysis/google-track-user-acq.md). Die [!DNL Google Analytics] -Cookie überschreibt nur die vorherigen UTM-Parameter, wenn der Benutzer auf eine neue URL klickt, die einen neuen Satz von UTM-Parametern enthält.

Betrachten Sie beispielsweise einen Benutzer, der eine Website zum ersten Mal über besucht [!DNL Google Analytics] *Paid Search*, kehrt dann über zurück *organische Suche* und kehrt schließlich zur *Website direkt* oder über *E-Mail-Link* **ohne UTM-Parameter** vor dem Konversionsereignis. In diesem Beispiel wird die [!DNL Google Analytics] -Cookie sagt, dass die Quelle des Benutzers organisch ist, da dies die letzte Quelle vor der Konvertierung darstellt. Die *path* des Benutzers, bevor dieses endgültige Konversionsereignis ignoriert wird. Wenn der Benutzer stattdessen die Website über einen E-Mail-Link mit UTM besucht, wird die [!DNL Google Analytics] -Cookie würde sagen, dass die Quelle &quot;E-Mail&quot;lautet. Wenn im Cookie vorhandene UTM-Parameter vorhanden sind und der Benutzer über Direkt eingebunden wird, wird die [!DNL Google Analytics] -Cookie zeigt die UTM-Parameter anstelle von &quot;direkt&quot;an.

>[!NOTE]
>
>Ein bestimmter Benutzer [!DNL Google Analytics] Cookie-Parameter werden gelöscht, wenn das Cookie [expires](https://developers.google.com/analytics/devguides/collection/analyticsjs/cookie-usage)oder wenn ein Benutzer seine Cookies im Browser löscht.*

### Erstklick-Attribution

Einige gebührenpflichtige Zuordnungstools ermöglichen es Ihnen, den &quot;Pancake-Stapel&quot;von Quellen im Pfad eines Benutzers zu erfassen. In diesem Fall würde uns die Attribution des ersten Klicks im obigen Beispiel die gebührenpflichtige Suche mitteilen. Alternativ können einige Websites eigene Cookies implementieren, die einen Pancake-Stapel erfassen und die erste Quelle in ihrer Datenbank speichern.

## Wie kann die Attribution analysiert werden?

[!DNL Google Analytics] verfügt über eine robuste Funktionalität in der Web-Oberfläche, mit der Sie vier verschiedene Attributionsmodelle durchführen können:

1. Erstklick
1. Letztklick
1. linear (Aufteilung des Umsatzes gleichmäßig auf alle Quellen im Pfad)
1. gewichtete (benutzerdefinierte Attribution)

Nachdem Sie nun verstanden haben, was das Attributionsmodell für jede Mikro- oder Makrokonversion ist, lautet die Frage &quot;Was machen Sie mit der Gesamtheit der Konversionen eines Benutzers?&quot;  Betrachten Sie beispielsweise die aufgezeichneten UTMs basierend auf der GA-Logik des letzten Klicks:

* Benutzerregister unter &quot;Organisch&quot;
* Erstkauf des Benutzers unter Paid Search $5.00
* Zweiter Kauf des Benutzers unter E-Mail $50.00
* Dritter Kauf des Benutzers unter kostenlosen $10.00

Hier fragen Sie: &quot;Wie viel Umsatz habe ich aus der gebührenpflichtigen Suche erhalten? Von E-Mail?  Aus Bio?&quot; Sie könnten sagen, dass die Antworten 5, 50 und 10 sind (egal, welche Quelle zuletzt verwendet wurde), oder Sie könnten auch sagen, dass Sie alle Umsätze der ersten Quelle zuordnen (alle 65 gehen zu &quot;organisch&quot;). Sie können auch eine gewichtete Analyse anwenden oder das lineare Modell anwenden (d. h. ungefähr 22 pro Modell).

## Verwandte Dokumentation

* [Verweisquelle für Bestellungen verfolgen über [!DNL Google Analytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)
* [Verbinden Sie Ihre [!DNL Google Adwords] account](../importing-data/integrations/google-adwords.md)
* [Erhöhen Sie den ROI Ihrer Werbekampagnen.](../analysis/roi-ad-camp.md)
* [Fünf Best Practices für das UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
