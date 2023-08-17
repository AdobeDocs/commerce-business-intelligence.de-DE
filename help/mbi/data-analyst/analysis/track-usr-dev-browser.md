---
title: Google Analytics - Tracking von Benutzergeräte- und Browserdaten in Ihrer Datenbank
description: Erfahren Sie, wie viele Benutzer sich tatsächlich über Mobilgeräte anmelden und wie sich dies auf den Lebenszeitwert dieser Benutzer auswirkt.
exl-id: 57b1bc45-b139-4370-86ea-2fbd021aa14d
role: Admin, User
feature: Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# [!UICONTROL Google Analytics] Tracking

Mit [!UICONTROL Google Analytics] Sie können [Verweisquelleninformationen speichern](../analysis/google-track-user-acq.md) um zu verstehen, woher Ihre wertvollsten Benutzer kommen. Dieses Thema behandelt die Plattform (z. B. Gerät oder Browser), an der Ihre Benutzer arbeiten. Dadurch können Sie erkennen, wie viele Benutzer sich tatsächlich über Mobilgeräte anmelden und wie sich dies auf den Lebenszeitwert dieser Benutzer auswirkt.

## Speichern von Benutzergeräten und Browserdaten

Jedes Mal, wenn eine Anfrage an Ihre Website gesendet wird, sendet der Browser des Benutzers eine User-Agent-Zeichenfolge mit Informationen zur Plattform, von der die Anfrage stammt. Im Folgenden finden Sie einige Beispiele für die Zeichenfolge &quot;User-Agent&quot;:

1. `Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_8\_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.116 Safari/537.36`
1. `Mozilla/5.0 (Windows NT 6.1; WOW64; rv:17.0) Gecko/17.0 Firefox/17.0`
1. `Mozilla/5.0 (iPhone; U; CPU iPhone OS 4\_0 like Mac OS X; en-us) AppleWebKit/532.9 (KHTML, like Gecko) Version/4.0.5 Mobile/8A293 Safari/6531.22.7`
1.` Mozilla/5.0 (iPad; CPU OS 5\_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B176 Safari/7534.48.3`
1. `Mozilla/5.0 (Linux; U; Android 2.2; en-us; Nexus One Build/FRF91) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1`

Wenn Sie genau hinschauen, sehen Sie, dass die Zeichenfolge Informationen über das Betriebssystem, den Browser und den Namen des verwendeten Geräts enthält (sofern er einen Namen hat). Obwohl die Benutzeragenten-Zeichenfolgen von Plattform zu Plattform und sogar Versionen derselben Plattform stark variieren, ist es im Allgemeinen richtig, dass der Plattformname irgendwo in vorhanden ist. Beispiel: Nummer 1 oben ist eine Mac mit dem Chrome-Browser, Nummer 2 oben ist ein Windows-Computer mit dem Firefox-Browser, Nummer 3 ist ein iPhone, #4 ein iPad und #5 ein Android-Gerät.

Auf diese Informationen kann Ihr Server bei jeder Anfrage zugreifen. In PHP wird die User-Agent-Zeichenfolge in `$_SERVER['HTTP_USER_AGENT']`. In Ruby on Rails wird er in `request.env['HTTP_USER_AGENT']`. In anderen Sprachen und Umgebungen haben Sie ähnliche Möglichkeiten, darauf zuzugreifen.

### Wann sollten Sie diese Daten aufzeichnen?

[!DNL Adobe] empfiehlt, ein neues Feld mit dem Namen `Platform` oder `User-Agent` auf `Customers` und `Orders` Datenbanktabellen zum Speichern dieser Informationen bei jeder Erstellung eines Benutzers oder bei einer Bestellung. Wenn Sie eine SQL-Datenbank verwenden, sollte dieses Feld ein `VARCHAR(255)`. 

>[!NOTE]
>
>Die `User-Agent` -Zeichenfolge ist viel länger als dieser Wert zulässig, in der Praxis jedoch nur selten über diese Länge.

### Wie analysiere ich die nützlichen Segmente?

Es gibt eine Reihe von Bibliotheken, die Ihnen beim Analysieren der `User-Agent` -Zeichenfolge in Komponenten wie Betriebssystem, Gerät usw. Siehe Abschnitt [ua-parser-Projekt](https://github.com/tobie/ua-parser) , um mehr zu erfahren.

Mit diesen neuen Informationen können Sie besser verstehen, wie Benutzer auf Ihre Site zugreifen. Anschließend können Sie ihr Erlebnis anpassen oder Marketingkampagnen für bestimmte Gruppen erstellen.

## Verwandte

* [Verweisquelle für Bestellungen verfolgen über [!DNL Google Anaytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)
* [Verbinden Sie [!DNL Google Adwords] account](../importing-data/integrations/google-adwords.md)
* [Steigerung des ROI bei Werbekampagnen](../analysis/roi-ad-camp.md)
* [Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../analysis/utm-attributes.md)
