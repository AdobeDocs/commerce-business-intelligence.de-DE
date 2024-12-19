---
title: Google Analytics - Benutzergeräte- und Browser-Daten in der Datenbank verfolgen
description: Erfahren Sie, wie viele Benutzer sich tatsächlich über Mobilgeräte anmelden und wie sich dies auf den Lebenszeitwert dieser Benutzer auswirkt.
exl-id: 57b1bc45-b139-4370-86ea-2fbd021aa14d
role: Admin, User
feature: Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Tracking [!UICONTROL Google Analytics]

Mit [!UICONTROL Google Analytics] können Sie [Informationen zur Empfehlungsquelle speichern](../analysis/google-track-user-acq.md) um zu verstehen, woher Ihre wertvollsten Benutzer kommen. In diesem Thema wird die Plattform (z. B. Gerät oder Browser) erläutert, an der Ihre Benutzerinnen und Benutzer arbeiten. Dadurch können Sie nachvollziehen, wie viele Benutzer sich tatsächlich über Mobilgeräte anmelden und wie sich dies auf den Lebenszeitwert dieser Benutzer auswirkt.

## Speichern von Benutzergerät- und Browser-Daten

Jedes Mal, wenn eine Anfrage an Ihre Website gesendet wird, sendet der Browser des Benutzers eine Benutzeragenten-Zeichenfolge mit Informationen über die Plattform, von der die Anfrage stammt. Im Folgenden finden Sie einige Beispiele für die Benutzeragenten-Zeichenfolge:

1. `Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_8\_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.116 Safari/537.36`
1. `Mozilla/5.0 (Windows NT 6.1; WOW64; rv:17.0) Gecko/17.0 Firefox/17.0`
1. `Mozilla/5.0 (iPhone; U; CPU iPhone OS 4\_0 like Mac OS X; en-us) AppleWebKit/532.9 (KHTML, like Gecko) Version/4.0.5 Mobile/8A293 Safari/6531.22.7`
1,` Mozilla/5.0 (iPad; CPU OS 5\_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B176 Safari/7534.48.3`
1. `Mozilla/5.0 (Linux; U; Android 2.2; en-us; Nexus One Build/FRF91) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1`

Wenn Sie genau hinschauen, sehen Sie, dass die Zeichenfolge Informationen über das Betriebssystem, den Browser und den Namen des Geräts enthält, das der Benutzer verwendet (sofern es einen Namen hat). Obwohl die Zeichenfolgen von Benutzeragenten von Plattform zu Plattform und sogar von Version stark variieren, ist es im Allgemeinen wahr, dass der Plattformname irgendwo in der Plattform vorhanden ist. Beispiel: #1 oben ist ein Mac mit dem Chrome-Browser, #2 oben ist ein Windows-Computer mit dem Firefox-Browser, #3 ist ein iPhone, #4 ist ein iPad und #5 ist ein Android-Gerät.

Auf diese Informationen kann der Server bei jeder Anforderung zugreifen. In PHP wird die user-agent-Zeichenfolge in `$_SERVER['HTTP_USER_AGENT']` gespeichert. In Ruby on Rails wird es in `request.env['HTTP_USER_AGENT']` gespeichert. Andere Sprachen und Umgebungen ermöglichen einen ähnlichen Zugriff.

### Wann sollten diese Daten aufgezeichnet werden?

[!DNL Adobe] empfiehlt, ein neues Feld mit dem Namen `Platform` oder `User-Agent` zu Ihren `Customers` und `Orders` Datenbanktabellen hinzuzufügen, um diese Informationen zu speichern, sobald ein Benutzer erstellt oder eine Bestellung aufgegeben wird. Wenn Sie eine SQL-Datenbank verwenden, sollte dieses Feld ein `VARCHAR(255)` sein. 

>[!NOTE]
>
>Die `User-Agent` Zeichenfolge darf viel länger sein, in der Praxis überschreitet sie diese Länge jedoch nur selten.

### Wie analysiere ich die nützlichen Segmente?

Es gibt eine Reihe von Bibliotheken, die Ihnen dabei helfen, die `User-Agent` Zeichenfolge in Komponenten wie Betriebssystem, Gerät usw. zu parsen. Weitere Informationen finden Sie im [ua](https://github.com/tobie/ua-parser)parser-Projekt.

Mit diesen neuen Informationen können Sie besser verstehen, wie Benutzer auf Ihre Site zugreifen. Anschließend können Sie deren Erlebnis anpassen oder Marketing-Kampagnen für bestimmte Gruppen erstellen.

## verwandt

* [Verfolgen Sie die Quelle der Bestellungsreferenz über  [!DNL Google Anaytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Verfolgen Sie die Quelle der Benutzerreferenz in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../analysis/most-value-source-channel.md)
* [Konto  [!DNL Google Adwords] ](../importing-data/integrations/google-adwords.md)
* [Steigerung des ROI Ihrer Werbekampagnen](../analysis/roi-ad-camp.md)
* [Wie funktioniert  [!DNL Google Analytics]  UTM-Attribution?](../analysis/utm-attributes.md)
