---
title: Google Analytics - Übersicht über Source-Daten zur Benutzerakquise verfolgen
description: Erfahren Sie, wie Sie Ihre Daten nach Benutzerakquise-Quelle segmentieren.
exl-id: 2ce3e4f9-4741-4ada-b822-ec6a5ca94497
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: 3098909fdccb726108c24f2424e4ba4c1db9d1c2
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 1%

---

# Segmentierung nach Benutzerakquise-Quelle

>[!NOTE]
>
>Der folgende Prozess unterstützt keine [!DNL Google Universal Analytics].

Die Möglichkeit, Ihre Daten nach der Quelle der Benutzerakquise zu segmentieren, ist für die effektive Verwaltung Ihres Marketing-Plans von entscheidender Bedeutung. Wenn Sie die Akquise neuer Benutzer kennen, zeigen Sie, welche Kanäle die besten Renditen erzielen, und ermöglicht es Ihrem Team, Marketing-Mittel mit Zuversicht zuzuweisen.

Wenn Sie nicht bereits Benutzerakquise-Quellen in Ihrer Datenbank verfolgen, können [!DNL Adobe Commerce Intelligence] Ihnen bei den ersten Schritten behilflich sein:

## Tracking der Benutzerakquise-Quelle

[!DNL Adobe] empfiehlt zwei Methoden zum Nachverfolgen von Verweisquelldaten basierend auf Ihrer Einrichtung:

### (Option 1) Verfolgen Sie Quelldaten zu Bestellungsreferenzen über [!DNL Google Analytics E-Commerce]

Wenn Sie [!DNL Google Analytics E-Commerce] verwenden, um Ihre Auftrags- und Verkaufsdaten zu verfolgen, können Sie die [[!DNL [Google Analytics E-Commerce Connector]]](../importing-data/integrations/google-ecommerce.md) verwenden, um die Bezugsquelldaten jeder Bestellung zu synchronisieren. Auf diese Weise können Sie Umsatz und Bestellungen nach Empfehlungsquelle (z. B. `utm_source` oder `utm_medium`) segmentieren. Sie erhalten auch ein Gefühl für die Quellen der Kundenakquise über [!DNL Commerce Intelligence] benutzerdefinierten Dimensionen wie `User's first order source`.

### (Option 2) Speichern der Quelldaten der [!DNL Google Analytics] in Ihrer Datenbank

In diesem Thema wird erläutert, wie Sie [!DNL Google Analytics] Informationen zum Akquisekanal in Ihrer eigenen Datenbank speichern können - insbesondere die Parameter `source`, `medium`, `term`, `content`, `campaign` und `gclid`, die beim ersten Besuch einer Benutzerin oder eines Benutzers auf Ihrer Website vorhanden waren. Eine Erläuterung dieser Parameter finden Sie in der [[!DNL Google Analytics] Dokumentation](https://support.google.com/analytics/answer/1191184?hl=en#zippy=%2Cin-this-article). Anschließend erkunden Sie einige der leistungsstarken Marketing-Analysen, die mit diesen Informationen in [!DNL Commerce Intelligence] durchgeführt werden können.

#### Warum?

Wenn Sie sich nur die standardmäßigen [!DNL Google Analytics]- und Akquise-Metriken ansehen, erhalten Sie nicht das ganze Bild. Die Anzahl der Konversionen aus der organischen Suche im Vergleich zur Paid Search ist zwar interessant, aber was kann man mit diesen Informationen tun? Sollte man mehr Geld für bezahlte Suche ausgeben? Das hängt vom Wert der Kunden ab, die über diesen Kanal kommen, was von Google Analytics nicht bereitgestellt wird.

>[!NOTE]
>
>[[!DNL Google Analytics eCommerce Tracking]](https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingEcommerce) löst dieses Problem, indem Transaktionsdaten in [!DNL Google Analytics] gespeichert werden. Diese Lösung funktioniert jedoch nicht für Nicht-E-Commerce-Sites. Außerdem sind bestimmte Tools wie die Kohortenanalyse in der [!DNL Google Analytics] nicht einfach durchzuführen.

Was ist, wenn Sie allen Kunden, die aus einer bestimmten E-Mail-Kampagne gewonnen haben, einen Folgevertrag per E-Mail zukommen lassen möchten? Oder Akquisedaten in Ihr CRM-System integrieren? Dies ist in [!DNL Google Analytics] unmöglich - tatsächlich verstößt es gegen die Nutzungsbedingungen, wenn [!DNL Google Analytics] Daten speichern, die eine Person identifizieren. Aber Sie können diese Daten selbst speichern.

#### Die -Methode

[!DNL Google Analytics] speichert Informationen zur Besucherreferenz in einem Cookie namens `__utmz`. Nachdem dieses Cookie (durch den [!DNL Google Analytics]-Trackingcode) gesetzt wurde, wird sein Inhalt bei jeder nachfolgenden Anforderung dieses Benutzers an Ihre Domain gesendet. In PHP könnte man zum Beispiel den Inhalt von `$_COOKIE['__utmz']` überprüfen und man würde eine Zeichenfolge sehen, die in etwa so aussieht:

`100000000.12345678.1.1.utmcsr=google|utmccn=(organic)|utmcmd=organic|utmctr=rj metrics`

Es gibt eindeutig einige Akquise-Quelldaten, die in der Zeichenfolge codiert sind. Dies wird getestet, um zu bestätigen, dass es sich um die neueste Akquisequelle des Besuchers und die zugehörigen Kampagnendaten handelt. Jetzt müssen Sie wissen, wie Sie die Daten extrahieren.

Dieser Code wurde in eine [PHP-Bibliothek auf GitHub gehostet](https://github.com/RJMetrics/referral-grabber-php). Um die Bibliothek zu verwenden, `include` Sie einen Verweis auf `ReferralGrabber.php` und rufen Sie dann auf

`$data = ReferralGrabber::parseGoogleCookie($_COOKIE['__utmz']);`

Das zurückgegebene `$data`-Array ist eine Zuordnung der Schlüssel `source`, `medium`, `term`, `content`, `campaign`, `gclid` und der entsprechenden Werte.

Adobe empfiehlt, der Datenbank eine Tabelle namens &quot;`user_referral`&quot; mit folgenden Spalten hinzuzufügen: &quot;`id INT PRIMARY KEY, user_id INT NOT NULL, source VARCHAR(255), medium VARCHAR(255), term VARCHAR(255), content VARCHAR(255), campaign VARCHAR(255), gclid VARCHAR(255)`&quot;. Wenn sich ein Benutzer anmeldet, rufen Sie die Verweisinformationen ab und speichern Sie sie in dieser Tabelle.

#### Verwendung dieser Daten

Wie können Sie jetzt, da Sie die Quelle für die Benutzerakquise speichern, diese verwenden?

Angenommen, Sie verwenden eine SQL-Datenbank und verfügen über eine `users` mit der folgenden Struktur:

| ID | E-MAIL | JOIN_DATE | ACQ_SOURCE | ACQ_MEDIUM |
|--- |--- |--- |--- |--- |
| 1 | john@abc.com | 24.01.2012 | googeln | organisch |
| 2 | jim@abc.com | 24.01.2012 | googeln | CPC |
| 3 | joe@def.com | 25.01.2012 | direkt | - |
| 4 | jess@ghi.com | 26.01.2012 | Empfehlung | techcrunch.com |
| 5 | jen@ghi.net | 30.01.2012 | Sonstige | organisch |
| … | … | … | … | … |

Zunächst können Sie die Anzahl der Benutzer zählen, die von jedem Empfehlungskanal kommen, indem Sie die folgende Abfrage für Ihre Datenbank ausführen:

`SELECT acq_source, COUNT(id) as user_count FROM users GROUP BY acq_source;`

Das Ergebnis sieht in etwa so aus:

| ACQ_SOURCE | USER_COUNT |
|--- |--- |
| googeln | 294 |
| direkt | 156 |
| Empfehlung | 55 |
| Sonstige | 16 |

Das ist interessant, aber von begrenztem Nutzen. Was Sie wirklich wissen möchten, ist:

* Die Wachstumsrate dieser Zahlen im Zeitverlauf
* Die Höhe des Umsatzes, der durch jede Akquise generiert wird
* Eine [Kohortenanalyse](https://en.wikipedia.org/wiki/Cohort_analysis) der Benutzer, die aus jeder Quelle stammen
* Die Wahrscheinlichkeit, dass ein Benutzer aus einem dieser Kanäle in Zukunft als Kunde zurückkehrt

Die für diese Analysen erforderlichen Abfragen sind komplex. Anhand dieser Informationen können Sie Ihre profitabelsten Akquisitionskanäle bestimmen und Marketing-Zeit und -Geld entsprechend ausrichten.

### verwandt

* **[Entdecken Sie Ihre wertvollsten Akquise-Quellen und -Kanäle](../analysis/most-value-source-channel.md)**
* **[Verbinden Sie Ihr [!DNL Google Adwords] Konto](../importing-data/integrations/google-adwords.md)**
* **[Erhöhen Sie den ROI Ihrer Werbekampagnen](../analysis/roi-ad-camp.md)**
* **[Wie funktioniert  [!DNL Google Analytics]  UTM-Attribution?](../analysis/utm-attributes.md)**
