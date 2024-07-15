---
title: Google Analytics - Tracking der Benutzerakquise - Source-Daten - Überblick
description: Erfahren Sie, wie Sie Ihre Daten nach der Benutzerakquise-Quelle segmentieren.
exl-id: 2ce3e4f9-4741-4ada-b822-ec6a5ca94497
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: 3098909fdccb726108c24f2424e4ba4c1db9d1c2
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 1%

---

# Segmentierung nach Quelle der Benutzerakquise

>[!NOTE]
>
>Der unten stehende Prozess unterstützt [!DNL Google Universal Analytics] nicht.

Die Möglichkeit, Ihre Daten nach der Benutzerakquise zu segmentieren, ist für die effektive Verwaltung Ihres Marketingplans von entscheidender Bedeutung. Wenn Sie die Akquise-Quelle neuer Benutzer kennen, erfahren Sie, welche Kanäle die besten Renditen erzielen. Zudem können Sie Ihrem Team so Marketing-Dollars mit Sicherheit zuweisen.

Wenn Sie noch nicht die Benutzerakquise-Quellen in Ihrer Datenbank verfolgen, kann [!DNL Adobe Commerce Intelligence] Ihnen bei den ersten Schritten helfen:

## Tracking der Benutzerakquise-Quelle

[!DNL Adobe] empfiehlt zwei Methoden, um Verweisquellendaten basierend auf Ihrer Einrichtung zu verfolgen:

### (Option 1) Verfolgen von Auftrags-Verweisquelldaten über [!DNL Google Analytics E-Commerce]

Wenn Sie [!DNL Google Analytics E-Commerce] verwenden, um Ihre Auftrags- und Verkaufsdaten zu verfolgen, können Sie die [!DNL [Google Analytics E-Commerce Connector]](../importing-data/integrations/google-ecommerce.md) verwenden, um die Verweisquelldaten jeder Bestellung zu synchronisieren. Auf diese Weise können Sie Umsätze und Bestellungen nach Verweisquelle segmentieren (z. B. `utm_source` oder `utm_medium`). Sie erhalten außerdem ein Gefühl für Kundenakquisequellen über [!DNL Commerce Intelligence] benutzerdefinierte Dimensionen wie `User's first order source`.

### (Option 2) Speichern der Akquise-Quelldaten von [!DNL Google Analytics] in Ihrer Datenbank

In diesem Thema wird erläutert, wie Sie die [!DNL Google Analytics] Akquise-Kanal-Informationen in Ihrer eigenen Datenbank speichern - nämlich die Parameter `source`, `medium`, `term`, `content`, `campaign` und `gclid`, die beim ersten Besuch eines Benutzers auf Ihrer Website vorhanden waren. Eine Erläuterung dieser Parameter finden Sie in der [[!DNL Google Analytics] Dokumentation](https://support.google.com/analytics/answer/1191184?hl=en#zippy=%2Cin-this-article). Anschließend werden einige der leistungsstarken Marketing-Analysen untersucht, die mit diesen Informationen in [!DNL Commerce Intelligence] durchgeführt werden können.

#### Warum?

Wenn Sie nur die standardmäßigen Konversions- und Akquise-Metriken für [!DNL Google Analytics] betrachten, erhalten Sie nicht das gesamte Bild. Während die Anzahl der Konversionen aus der kostenlosen Suche im Vergleich zur gebührenpflichtigen Suche interessant ist, was können Sie mit diesen Informationen machen? Sollten Sie mehr Geld für die gebührenpflichtige Suche ausgeben? Das hängt vom Wert der Kunden ab, die von diesem Kanal kommen, was keine Google Analytics bietet.

>[!NOTE]
>
>[[!DNL Google Analytics eCommerce Tracking]](https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingEcommerce) behebt dieses Problem, indem Transaktionsdaten in [!DNL Google Analytics] gespeichert werden. Diese Lösung funktioniert jedoch nicht für Nicht-eCommerce-Sites. Bestimmte Tools wie die Kohortenanalyse sind in der Oberfläche von [!DNL Google Analytics] nicht einfach zu handhaben.

Was ist, wenn Sie allen Kunden, die von einer bestimmten E-Mail-Kampagne erworben wurden, eine E-Mail-Folgevereinbarung senden möchten? Oder integrieren Sie Akquisedaten in Ihr CRM-System? Dies ist in [!DNL Google Analytics] unmöglich - Tatsächlich widerspricht es den Nutzungsbedingungen für [!DNL Google Analytics], Daten zu speichern, die eine Person identifizieren. Sie können diese Daten jedoch selbst speichern.

#### Die Methode

[!DNL Google Analytics] speichert Besucherverweisinformationen in einem Cookie namens `__utmz`. Nachdem dieses Cookie gesetzt wurde (durch den Trackingcode [!DNL Google Analytics] ), wird sein Inhalt mit jeder nachfolgenden Anforderung von diesem Benutzer an Ihre Domäne gesendet. In PHP zum Beispiel könnten Sie den Inhalt von `$_COOKIE['__utmz']` auschecken und eine Zeichenfolge sehen, die ungefähr so aussieht:

`100000000.12345678.1.1.utmcsr=google|utmccn=(organic)|utmcmd=organic|utmctr=rj metrics`

Es gibt eindeutig einige Akquise-Quelldaten, die in der Zeichenfolge kodiert sind. Dies wird getestet, um sicherzustellen, dass dies die neueste Akquisequelle und die damit verbundenen Kampagnendaten des Besuchers ist. Jetzt müssen Sie wissen, wie Sie die Daten extrahieren können.

Dieser Code wurde in eine [PHP-Bibliothek übersetzt, die auf github](https://github.com/RJMetrics/referral-grabber-php) gehostet wird. Um die Bibliothek zu verwenden, `include` einen Verweis auf `ReferralGrabber.php` und rufen Sie dann

`$data = ReferralGrabber::parseGoogleCookie($_COOKIE['__utmz']);`

Das zurückgegebene `$data` -Array ist eine Zuordnung der Schlüssel `source`, `medium`, `term`, `content`, `campaign`, `gclid` und ihrer jeweiligen Werte.

Adobe empfiehlt das Hinzufügen einer Tabelle zu Ihrer Datenbank, z. B. &quot;`user_referral`&quot;, mit den Spalten &quot;`id INT PRIMARY KEY, user_id INT NOT NULL, source VARCHAR(255), medium VARCHAR(255), term VARCHAR(255), content VARCHAR(255), campaign VARCHAR(255), gclid VARCHAR(255)`&quot;. Wenn sich ein Benutzer anmeldet, rufen Sie die Verweisinformationen ab und speichern Sie sie in dieser Tabelle.

#### Verwendung dieser Daten

Wie können Sie jetzt, da Sie die Benutzerakquise-Quelle speichern, diese verwenden?

Angenommen, Sie verwenden eine SQL-Datenbank und haben eine `users` -Tabelle mit der folgenden Struktur:

| ID | E-MAIL | JOIN_DATE | ACQ_SOURCE | ACQ_MEDIUM |
|--- |--- |--- |--- |--- |
| 1 | john@abc.com | 24.01.2012 | google | organisch |
| 2 | jim@abc.com | 24.01.2012 | google | cpc |
| 3 | joe@def.com | 25.01.2012 | direct | - |
| 4 | jess@ghi.com | 26.01.2012 | Verweis | techcrunch.com |
| 5 | jen@ghi.net | 30.01.2012 | other | organisch |
| ... | ... | ... | ... | ... |

Zunächst können Sie die Anzahl der Benutzer aus den einzelnen Verweiskanälen zählen, indem Sie die folgende Abfrage für Ihre Datenbank ausführen:

`SELECT acq_source, COUNT(id) as user_count FROM users GROUP BY acq_source;`

Das Ergebnis sieht ungefähr so aus:

| ACQ_SOURCE | USER_COUNT |
|--- |--- |
| google | 294 |
| direct | 156 |
| Verweis | 55 |
| other | 16 |

Das ist interessant, aber von begrenztem Nutzen. Was Sie wirklich gerne wissen möchten, ist:

* Die Wachstumsrate dieser Zahlen im Zeitverlauf
* Höhe des Umsatzes, der von den einzelnen Akquisequellen generiert wird
* Eine [Kohortenanalyse](https://en.wikipedia.org/wiki/Cohort_analysis) von Benutzern aus den einzelnen Quellen
* Die Wahrscheinlichkeit, dass ein Benutzer aus einem dieser Kanäle in Zukunft als Kunde zurückkehrt

Die für diese Analysen erforderlichen Abfragen sind komplex. Mit diesen Informationen können Sie Ihre rentabelsten Akquisekanäle bestimmen und Marketing-Zeit und -Geld entsprechend ausrichten.

### Verwandte

* **[Erkunden Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)**
* **[Verbinden Sie Ihr [!DNL Google Adwords] Konto](../importing-data/integrations/google-adwords.md)**
* **[Steigern des ROI Ihrer Werbekampagnen](../analysis/roi-ad-camp.md)**
* **[Wie funktioniert die  [!DNL Google Analytics] UTM-Attribution?](../analysis/utm-attributes.md)**
