---
title: Google Analytics - Übersicht über die Benutzerakquise-Quelldaten
description: Erfahren Sie, wie Sie Ihre Daten nach Benutzerakquise-Quelle segmentieren.
exl-id: 2ce3e4f9-4741-4ada-b822-ec6a5ca94497
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 0%

---

# Segmentierung nach Quelle der Benutzerakquise

>[!NOTE]
>
>Der folgende Prozess unterstützt nicht [!DNL GoogleUniversal Analytics].

Die Möglichkeit, Ihre Daten nach der Benutzerakquise zu segmentieren, ist für die effektive Verwaltung Ihres Marketingplans von entscheidender Bedeutung. Wenn Sie die Akquise-Quelle neuer Benutzer kennen, erfahren Sie, welche Kanäle die besten Renditen erzielen. Zudem können Sie Ihrem Team so Marketing-Dollars mit Sicherheit zuweisen.

Wenn Sie die Benutzerakquise-Quellen noch nicht in Ihrer Datenbank verfolgen, [!DNL MBI] können Ihnen bei den ersten Schritten helfen:

## Tracking der Benutzerakquise-Quelle

Es werden zwei Methoden empfohlen, um Verweisquelldaten basierend auf Ihrer Einrichtung zu verfolgen:

### (Option 1) Verfolgen von Auftrags-Verweisquelldaten über [!DNL Google Analytics E-Commerce] (einschließlich [!DNL Shopify] Stores)

Wenn Sie [!DNL Google Analytics E-Commerce] zur Nachverfolgung Ihrer Auftrags- und Verkaufsdaten können Sie unsere [!DNL [Google Analytics E-Commerce Connector]](../importing-data/integrations/google-ecommerce.md) , um die Verweisquelldaten jeder Bestellung zu synchronisieren. Auf diese Weise können Sie Umsätze und Bestellungen nach Verweisquellen segmentieren (z. B. `utm_source` oder `utm_medium`) und erhalten außerdem ein Gefühl für die Kundenakquise-Quellen über [!DNL MBI] benutzerdefinierte Dimensionen wie `User's first order source`.

>[!NOTE]
>
>Für Shopify-Benutzer**: Aktivieren [!DNL [Google Analytics E-Commerce] tracking in Shopify](http://docs.shopify.com/manual/settings/general/google-analytics#ecommerce-tracking) vor dem Verbinden [!DNL Google Analytics E-Commerce] Konto [!DNL MBI].

### (Option 2) Speichern [!DNL Google Analytics]&quot; Akquise-Quelldaten in Ihrer Datenbank

In diesem Artikel werden wir erklären, wie Sie sparen [!DNL Google Analytics] Akquise-Kanal-Informationen in Ihre eigene Datenbank - nämlich die `source`, `medium`, `term`, `content`, `campaign`und `gclid` Parameter, die beim ersten Besuch eines Benutzers auf Ihrer Website vorhanden waren. Eine Erläuterung dieser Parameter finden Sie in der [!DNL [Google Analytics] documentation](http://support.google.com/analytics/bin/answer.py?hl=en&amp;answer=1191184). Anschließend werden wir einige der leistungsstarken Marketing-Analysen untersuchen, die mit diesen Informationen in [!DNL MBI].

#### Warum?

Wenn Sie sich nur die Standardeinstellung ansehen [!DNL Google Analytics] Konversions- und Akquise-Metriken, erhalten Sie nicht das gesamte Bild. Während die Anzahl der Konversionen aus der kostenlosen Suche im Vergleich zur gebührenpflichtigen Suche interessant ist, was können Sie mit diesen Informationen machen? Sollten Sie mehr Geld für die gebührenpflichtige Suche ausgeben? Das hängt vom Wert der Kunden ab, die von diesem Kanal stammen, was von Google Analytics nicht bereitgestellt wird.

>[!NOTE]
>
>[!DNL [Google Analytics eCommerce Tracking]](https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingEcommerce) verhindert dieses Problem durch Speichern von Transaktionsdaten in [!DNL Google Analytics], aber diese Lösung funktioniert nicht für Nicht-eCommerce-Sites und bestimmte Tools wie die Kohortenanalyse sind nicht einfach in der [!DNL Google Analytics] -Schnittstelle.

Was ist, wenn Sie allen Kunden, die von einer bestimmten E-Mail-Kampagne erworben wurden, eine E-Mail-Folgevereinbarung senden möchten? Oder integrieren Sie Akquisedaten in Ihr CRM-System? Das ist unmöglich in [!DNL Google Analytics] - tatsächlich gegen die Nutzungsbedingungen für [!DNL Google Analytics] , um alle Daten zu speichern, die eine Person identifizieren.  Das bedeutet jedoch nicht, dass Sie diese Daten nicht selbst speichern können.

#### Die Methode

[!DNL Google Analytics] speichert Besucherverweisinformationen in einem Cookie namens `__utmz`. Nachdem dieses Cookie gesetzt wurde (durch die Variable [!DNL Google Analytics] Trackingcode), wird der Inhalt mit jeder nachfolgenden Anfrage des Benutzers an Ihre Domäne gesendet. So können Sie z.B. in PHP den Inhalt von `$_COOKIE['__utmz']` und Sie würden eine Zeichenfolge sehen, die ungefähr so aussieht:

> `100000000.12345678.1.1.utmcsr=google|utmccn=(organic)|utmcmd=organic|utmctr=rj metrics`

Es gibt eindeutig einige Akquise-Quelldaten, die in der Zeichenfolge kodiert sind, und wir haben getestet, um sicherzustellen, dass dies die neueste Akquisequelle und die zugehörigen Kampagnendaten des Besuchers sind. Jetzt müssen wir nur wissen, wie wir die Daten extrahieren können. Glücklicherweise hat Justin Cutroni zuvor beschrieben, wie diese Kodierung funktioniert, und hat einen JavaScript-Code freigegeben, um die wichtigsten Informationen zu extrahieren.

Wir nahmen diesen Code und übersetzten ihn in ein [PHP-Bibliothek wird auf github gehostet](https://github.com/RJMetrics/referral-grabber-php).   So verwenden Sie die Bibliothek: `include` einen Verweis auf `ReferralGrabber.php` und dann

> `$data = ReferralGrabber::parseGoogleCookie($_COOKIE['__utmz']);`

Die zurückgegebene `$data` Array ist eine Zuordnung der Schlüssel `source`, `medium`, `term`, `content`, `campaign`, `gclid` und die entsprechenden Werte.

Es wird empfohlen, Ihrer Datenbank eine neue Tabelle hinzuzufügen, die beispielsweise `user_referral`, wobei die Spalten wie folgt lauten: `id INT PRIMARY KEY, user_id INT NOT NULL, source VARCHAR(255), medium VARCHAR(255), term VARCHAR(255), content VARCHAR(255), campaign VARCHAR(255), gclid VARCHAR(255)`. Wenn sich ein Benutzer anmeldet, rufen Sie die Verweisinformationen ab und speichern Sie sie in dieser Tabelle.

#### Verwendung dieser Daten

Wie können wir jetzt, da wir die Benutzerakquise-Quelle speichern, diese verwenden?

Nehmen wir an, wir verwenden eine SQL-Datenbank und verfügen über eine `users` -Tabelle mit der folgenden Struktur:

| ID | E-MAIL | JOIN_DATE | ACQ_SOURCE | ACQ_MEDIUM |
|--- |--- |--- |--- |--- |
| 1 | john@abc.com | 24.01.2012 | google | organisch |
| 2 | jim@abc.com | 24.01.2012 | google | cpc |
| 3 | joe@def.com | 25.01.2012 | direct | - |
| 4 | jess@ghi.com | 26.01.2012 | Verweis | techcrunch.com |
| 5 | jen@ghi.net | 30.01.2012 | other | organisch |
| ... | ... | ... | ... | ... |

Zunächst können wir die Anzahl der Benutzer aus den einzelnen Verweiskanälen zählen, indem wir die folgende Abfrage für Ihre Datenbank ausführen:

> `SELECT acq_source, COUNT(id) as user_count FROM users GROUP BY acq_source;`

Das Ergebnis sieht ungefähr so aus:

| ACQ_SOURCE | USER_COUNT |
|--- |--- |
| google | 294 |
| direct | 156 |
| Verweis | 55 |
| other | 16 |

Das ist interessant, aber von begrenztem Nutzen. Was wir wirklich gerne wissen würden, ist die Wachstumsrate dieser Zahlen im Zeitverlauf, die Höhe der Einnahmen, die durch jede Akquisequelle generiert werden, eine [Kohortenanalyse](http://cohortanalysis.com/) der Benutzer aus den einzelnen Quellen und der Wahrscheinlichkeit, dass ein Benutzer aus einem dieser Kanäle als Kunde zurückkehrt. Die für diese Analysen erforderlichen Abfragen sind komplex. Deshalb haben wir [!DNL MBI]. Mit diesen Informationen können wir unsere rentabelsten Akquisekanäle bestimmen und unsere Marketing-Zeit und unser Geld entsprechend ausrichten.

### Verwandte

* **[Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](https://support.magento.com/hc/en-us/articles/360016732911)**
* **[Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)**
* **[Verbinden Sie Ihre [!DNL Google Adwords] account](../importing-data/integrations/google-adwords.md)**
* **[Erhöhen Sie den ROI Ihrer Werbekampagnen.](../analysis/roi-ad-camp.md)**
* **[Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../analysis/utm-attributes.md)**
