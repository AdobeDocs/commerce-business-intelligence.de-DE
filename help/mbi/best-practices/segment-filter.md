---
title: Empfohlene Dimensionen für die Segmentierung und Filterung
description: Erfahren Sie mehr über Best Practices für die Segmentierung und Filterung.
exl-id: 66391bce-bdeb-4e9d-8089-1c796e00d91e
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# Segmentierung und Filterung

Eine gute Segmentierung wandelt eine oberflächliche Statistik in eine Geschäftsmetrik um, die Entscheidungen bestimmt.

Möchten Sie wissen, wer Ihre wertvollsten Kunden sind? Was sind Ihre wertvollsten Marketing-Kanäle? Welche Ihrer Produkte bewegen sich schneller und warum? Um zu einer dieser Antworten zu gelangen, müssen Sie zunächst Ihre Daten segmentieren.

Dieses Thema behandelt wichtige Segmente, die Kunden häufig empfohlen werden. Es wird auch detailliert beschrieben, welche Fragen Ihnen diese Segmente beantworten können. Technisch gesehen sind Segmente Datenspalten in Ihrer Datenbank. [!DNL Adobe Commerce Intelligence] werden sie als Dimensionen bezeichnet.

![](../../mbi/assets/mbi-critical-segments.png)


## Benutzersegmente

Mithilfe von Benutzersegmenten können Sie besser verstehen, wer Ihre Benutzer sind und wie sie sich verhalten.

* **Alter / Geburtsjahr**: Wie alt sind Ihre Benutzer? Wie alt sind Ihre aktivsten Benutzer? Für eine effektivere Analyse ist es in der Regel sinnvoll, die Werte in Bereiche zu unterteilen.
* **Geschlecht**: Binden verschiedene Geschlechter unterschiedlich mit Ihrer Website ein?
* **Adresse**: Woher kommen Ihre User? Sollten Sie Ihre Marketing-Maßnahmen auf eine bestimmte Region konzentrieren? Haben Ihre letzten Werbekampagnen in Ihren Zielregionen wie erwartet funktioniert?
* **Quelle der Kundenakquise**\: Wissen Sie, von welchem Marketing-Kanal Ihre Benutzer kommen? Haben sie auf eine Anzeige geklickt oder Sie über die Suche gefunden? [Die Segmentierung Ihrer Daten nach ](../data-analyst/analysis/google-track-user-acq.md) ist der erste Schritt zur Optimierung der Neukundengewinnung. Schritt zwei besteht darin, mehr Geld für das auszugeben, was funktioniert, und das zu töten, was nicht funktioniert.
* **Registriergerät**: Haben sich Benutzer über Ihre Mobile App oder Ihre Website registriert? iOS oder Android™? Ist Ihr mobiler Benutzerstamm groß genug, um mehr Ressourcen für die Entwicklung Ihres mobilen Produkts bereitzustellen? Wenn Sie dies noch nicht verfolgen, lesen Sie den Abschnitt [Informationen zum Tracking von Benutzergeräten](../data-analyst/analysis/track-usr-dev-browser.md).
* **Referenziert von**: Wer sind Ihre Top-Influencer? Wie viele Benutzer wurden von anderen direkt weitergeleitet?
* **Branche**: Wenn Sie ein B2B-Unternehmen sind, in welchen Branchen arbeiten Ihre Anwender? Welchen Handelsorganisationen ist der Beitritt wert?
* **Umfrageantworten**: Wenn Sie Kundenumfragen durchführen, verwenden Sie die Antworten als Segmente für eine tiefergehende Profilerstellung. Sie können Fragen stellen, die das ergänzen, was Sie bereits über Ihre Benutzer wissen, oder Ihre Vermutungen bestätigen.
* **Erster Bestellbetrag und Produktkategorie**: Besteht eine Korrelation zwischen der ersten Bestellung eines Benutzers und zukünftigen Kaufmustern?

## Bestellungen/Ereignissegmente

Order- und Ereignissegmente helfen dabei, das Benutzerverhalten und die Interaktion im Laufe der Zeit zu analysieren.

* **[!UICONTROL Billing / Shipping Address]**: Woher kommen die meisten Bestellungen? Gibt es einen Unterschied zwischen Abrechnungs- und Versandadressen?
* **[!UICONTROL Status]**: Wie viele Ihrer Bestellungen konnten nicht abgeschlossen werden? Wie hoch ist das Verhältnis der ausstehenden Bestellungen in den letzten sieben Tagen?
* **[!UICONTROL Customer acquisition source]**: Sie können Benutzerakquise-Daten nicht nur auf Benutzerebene verfolgen, sondern [ auch auf Auftrags- oder Ereignisebene ](../data-analyst/analysis/google-track-user-acq.md). Ein Benutzer, der sich über eine Quelle registriert hat, kann weiterhin über andere Quellen auf Ihre Site zugreifen.
* **[!UICONTROL Device]**: Steigt die Anzahl der Bestellungen für Mobilgeräte? Wie viel Ihres Umsatzes wird durch Käufe für Mobilgeräte generiert? (Wenn Sie dies noch nicht nachverfolgen, lesen Sie den Abschnitt [Nachverfolgen von Gerätedaten für Bestellungen](../data-analyst/analysis/track-usr-dev-browser.md).
* **[!UICONTROL Fulfillment Center]**: Welches Ihrer Fulfillment-Center generiert die meisten Umsätze? Wenn Sie den Unterschied zwischen Bestellzeit und Versandzeit analysieren, welches Fulfillment Center reagiert am besten?
* **[!UICONTROL Delivery Carrier]**: Welcher ist der beliebteste Anbieter? Welcher Spediteur hat die geringste Anzahl an zurückgesandten Artikeln?
* **[!UICONTROL Discount / Coupon Codes]**: Generieren Ihre Werbeaktionen tatsächlich zusätzliches Geschäft? Wie viele zusätzliche Artikel kauften Ihre Kunden zusätzlich zum Artikel im Angebot? Wie wirken sich Gutscheine auf Ihren durchschnittlichen Bestellwert aus? Wie hoch ist die durchschnittliche Marge für ermäßigte und nicht ermäßigte Artikel?
* **[!UICONTROL Satisfaction / Rating]**: Wie zufrieden sind Ihre Kunden mit ihren Bestellungen? Verweisen Ihre Kunden das Geschäft wahrscheinlich an Sie?

## Produktsegmente

Produktsegmente helfen Ihnen bei Merchandising-Entscheidungen.

* **[!UICONTROL Merchant / Brand]**: Verkauft sich eine bestimmte Marke schneller als der Rest? Welche Marken sind leistungsschwach?
* **[!UICONTROL Type / Category]**: Genießen verschiedene Benutzersegmente verschiedene Produktarten? Welche Produktkategorien erzeugen die meisten Wiederholungsgeschäfte?
* **[!UICONTROL Discount / Coupon Codes]**: Schränken Werbeaktionen den Verkauf von nicht ermäßigten Produkten ein? Wie wirken sich Gutscheine auf den wahrgenommenen Wert Ihrer Produkte aus?
* **[!UICONTROL Social Activity]**: Gibt es eine Korrelation zwischen dem in den sozialen Medien erzeugten Buzz und der für ein Produkt verkauften Menge?
* **[!UICONTROL Size / Variant]**: Wie hoch ist das Verhältnis des Inventars, das Sie für jede Variante benötigen? Welche Varianten können zu Rabattpreisen verkauft werden?

Wenn Sie sich für Merchandising interessieren, finden Sie unter [Verwendung von Produktsegmenten zur Förderung des Wiederholungsgeschäfts](../data-analyst/analysis/most-value-source-channel.md) weitere Informationen.

## Kundenprofile erstellen

Segmentierungsexperten sollten über eindimensionale Segmente hinausgehen und mit der Erstellung echter Kundenprofile beginnen. Zum Beispiel Personen zwischen 13 und 24 Jahren, die sich über ein Mobilgerät registriert haben, in eine Gruppe „Jung &amp; Mobil“ gestellt. Wie verhält sich diese Gruppe im Vergleich zum Rest der Benutzerbasis?

Diese Art von Analyse machen Marketing-Experten der Fortune 1000-Unternehmen den ganzen Tag. Vor der Einführung Cloud-basierter Business-Intelligence-Plattformen wie [!DNL Commerce Intelligence] war dies für den Rest von uns größtenteils unerreichbar. Glücklicherweise ist dies nicht mehr der Fall.

## Tracking neuer Segmente

Um Ihre Metriken anhand der oben genannten Dimensionen zu segmentieren, müssen Sie als Erstes sicherstellen, dass Sie diese Daten in Ihrer Datenbank nachverfolgen. Wenn es nicht verfolgt wird, wenden Sie sich an Ihr Tech-Team und finden Sie einen Weg, um mit dem Tracking dieser Daten zu beginnen.

Nachdem Sie bestätigt haben, dass die Daten in Ihrer Datenbank verfolgt werden, [ Sie sich an das Support-](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um die Dimensionen in Ihre [!DNL Commerce Intelligence] Metriken und Diagramme zu übertragen. Sie können auch das Tool *Feldverwaltung* verwenden, um diese Felder in [!DNL Commerce Intelligence] zu verfolgen.

## verwandt

* [Datenbank für Analysen optimieren](../best-practices/opt-db-analysis.md)
