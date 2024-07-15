---
title: Google Analytics - Tracking von Benutzergeräte- und Browserdaten in Ihrer Datenbank
description: Erfahren Sie, wie viele Benutzer sich tatsächlich über Mobilgeräte anmelden und wie sich dies auf den Lebenszeitwert dieser Benutzer auswirkt.
exl-id: 57b1bc45-b139-4370-86ea-2fbd021aa14d
role: Admin, User
feature: Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# [!UICONTROL Google Analytics] Tracking

Mit [!UICONTROL Google Analytics] können Sie [Verweisquelleninformationen speichern](../analysis/google-track-user-acq.md), um zu verstehen, woher Ihre wertvollsten Benutzer stammen. Dieses Thema behandelt die Plattform (z. B. Gerät oder Browser), an der Ihre Benutzer arbeiten. Dadurch können Sie erkennen, wie viele Benutzer sich tatsächlich über Mobilgeräte anmelden und wie sich dies auf den Lebenszeitwert dieser Benutzer auswirkt.

## Speichern von Benutzergeräten und Browserdaten

Jedes Mal, wenn eine Anfrage an Ihre Website gesendet wird, sendet der Browser des Benutzers eine User-Agent-Zeichenfolge mit Informationen zur Plattform, von der die Anfrage stammt. Im Folgenden finden Sie einige Beispiele für die Zeichenfolge &quot;User-Agent&quot;:

1. `Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_8\_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.116 Safari/537.36`
1. `Mozilla/5.0 (Windows NT 6.1; WOW64; rv:17.0) Gecko/17.0 Firefox/17.0`
1. `Mozilla/5.0 (iPhone; U; CPU iPhone OS 4\_0 like Mac OS X; en-us) AppleWebKit/532.9 (KHTML, like Gecko) Version/4.0.5 Mobile/8A293 Safari/6531.22.7`
1.` Mozilla/5.0 (iPad; CPU OS 5\_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B176 Safari/7534.48.3`
1. `Mozilla/5.0 (Linux; U; Android 2.2; en-us; Nexus One Build/FRF91) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1`

Wenn Sie genau hinschauen, sehen Sie, dass die Zeichenfolge Informationen über das Betriebssystem, den Browser und den Namen des verwendeten Geräts enthält (sofern er einen Namen hat). Obwohl die Benutzeragenten-Zeichenfolgen von Plattform zu Plattform und sogar Versionen derselben Plattform stark variieren, ist es im Allgemeinen richtig, dass der Plattformname irgendwo in vorhanden ist. Beispiel: Nummer 1 oben ist eine Mac mit dem Chrome-Browser, Nummer 2 oben ist ein Windows-Computer mit dem Firefox-Browser, Nummer 3 ist eine iPhone, Nummer 4 ist eine iPad und #5 ist ein Android-Gerät.

Auf diese Informationen kann Ihr Server bei jeder Anfrage zugreifen. In PHP wird die User-Agent-Zeichenfolge in `$_SERVER['HTTP_USER_AGENT']` gespeichert. In Ruby on Rails wird er in `request.env['HTTP_USER_AGENT']` gespeichert. In anderen Sprachen und Umgebungen haben Sie ähnliche Möglichkeiten, darauf zuzugreifen.

### Wann sollten Sie diese Daten aufzeichnen?

[!DNL Adobe] empfiehlt, ein neues Feld namens `Platform` oder `User-Agent` zu Ihren `Customers`- und `Orders`-Datenbanktabellen hinzuzufügen, um diese Informationen zu speichern, sobald ein Benutzer erstellt oder eine Bestellung aufgegeben wird. Wenn Sie eine SQL-Datenbank verwenden, sollte dieses Feld ein `VARCHAR(255)` sein. 

>[!NOTE]
>
>Die Zeichenfolge `User-Agent` darf viel länger sein als dieser Wert, in der Praxis ist sie jedoch selten länger.

### Wie analysiere ich die nützlichen Segmente?

Es gibt eine Reihe von Bibliotheken, die Ihnen beim Parsen der `User-Agent`-Zeichenfolge in Komponenten wie Betriebssystem, Gerät usw. helfen. Weitere Informationen finden Sie im [ua-parser-Projekt](https://github.com/tobie/ua-parser) .

Mit diesen neuen Informationen können Sie besser verstehen, wie Benutzer auf Ihre Site zugreifen. Anschließend können Sie ihr Erlebnis anpassen oder Marketingkampagnen für bestimmte Gruppen erstellen.

## Verwandte

* [Verfolgen der Verweisquelle für Bestellungen über [!DNL Google Anaytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)
* [ [!DNL Google Adwords] Konto verbinden](../importing-data/integrations/google-adwords.md)
* [Steigerung des ROI bei Werbekampagnen](../analysis/roi-ad-camp.md)
* [Wie funktioniert die  [!DNL Google Analytics] UTM-Attribution?](../analysis/utm-attributes.md)
