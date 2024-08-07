---
title: Empfohlene Daten-Dimensionen für Segmentierung und Filterung
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

Eine gute Segmentierung macht aus einer oberflächlichen Statistik eine Geschäftsmetrik, die Entscheidungen bestimmt.

Möchten Sie wissen, wer Ihre wertvollsten Kunden sind? Was sind Ihre wertvollsten Marketing-Kanäle? Welche Ihrer Produkte bewegen sich schneller und warum? Um zu einer dieser Antworten zu gelangen, müssen Sie zunächst Ihre Daten segmentieren.

Dieses Thema behandelt wichtige Segmente, die häufig Kunden empfohlen werden. Außerdem wird im Detail erläutert, auf welche Fragen diese Segmente Ihnen bei der Beantwortung helfen können. Technisch gesehen sind Segmente Datenspalten in Ihrer Datenbank. In [!DNL Adobe Commerce Intelligence] werden sie als Dimensionen bezeichnet.

![](../../mbi/assets/mbi-critical-segments.png)


## Benutzersegmente

Benutzersegmente helfen Ihnen dabei zu verstehen, wer Ihre Benutzer sind und wie sie sich verhalten.

* **Alter/Geburtsjahr**: Wie alt sind Ihre Benutzer? Wie alt sind Ihre aktivsten Benutzer? Es ist in der Regel sinnvoll, die Werte in Bereiche zu bündeln, um eine effektivere Analyse zu ermöglichen.
* **Geschlecht**: Interagieren unterschiedliche Geschlechter unterschiedlich mit Ihrer Website?
* **Adresse**: Woher kommen Ihre Benutzer? Sollten Sie Ihre Marketing-Maßnahmen auf eine bestimmte Region ausrichten? Haben Ihre jüngsten Werbekampagnen in Ihren Zielregionen wie erwartet ausgeführt?
* **Kunden-Akquise-Quelle**\: Wissen Sie, von welchem Marketing-Kanal Ihre Benutzer stammen? Haben sie auf eine Anzeige geklickt oder Sie über eine Suche gefunden? [Die Segmentierung Ihrer Daten nach der Benutzerakquise-Quelle](../data-analyst/analysis/google-track-user-acq.md) ist der erste Schritt zur Optimierung Ihrer neuen Kundenakquise. Schritt zwei besteht darin, mehr Geld für das auszugeben, was funktioniert, und das zu töten, was nicht ist.
* **Registrierungsgerät**: Haben sich Benutzer über Ihre App oder Ihre Website registriert? iOS oder Android™? Ist Ihre mobile Benutzerbasis groß genug, um mehr Ressourcen für die Entwicklung Ihres mobilen Produkts bereitzustellen? Wenn Sie dies noch nicht verfolgen, lesen Sie dieses Thema [über das Tracking des Benutzergeräts](../data-analyst/analysis/track-usr-dev-browser.md).
* **Verwiesen von**: Wer sind Ihre wichtigsten Einflussnehmer? Wie viele Benutzer wurden direkt von anderen weitergeleitet?
* **Branche**: Wenn Sie ein B2B-Unternehmen sind, in welchen Branchen arbeiten Ihre Benutzer? Welche Handelsorganisationen sind es wert, Mitglied zu werden?
* **Umfrageantworten**: Wenn Sie Kundenumfragen durchführen, verwenden Sie die Antworten als Segmente, um ein tieferes Profil zu erhalten. Sie können Fragen stellen, die das, was Sie über Ihre Benutzer wissen, ergänzen oder Ihre Ratschläge bestätigen.
* **Erster Bestellbetrag und Produktkategorie**: Besteht eine Korrelation zwischen dem Erstbestellungs- und zukünftigen Kaufverhalten eines Benutzers?

## Bestellungen/Ereignissegmente

Reihenfolge- und Ereignissegmente helfen bei der Analyse des Benutzerverhaltens und der Interaktion im Zeitverlauf.

* **[!UICONTROL Billing / Shipping Address]**: Woher kommen die meisten Ihrer Bestellungen? Gibt es einen Unterschied zwischen Abrechnungs- und Versandadressen?
* **[!UICONTROL Status]**: Wie viele Ihrer Bestellungen konnten nicht abgeschlossen werden? Wie hoch ist das Verhältnis der ausstehenden Bestellungen in den letzten sieben Tagen?
* **[!UICONTROL Customer acquisition source]**: Neben der Verfolgung von Benutzerakquise-Daten auf Benutzerebene können Sie auch [diese auf Bestell- oder Ereignisebene verfolgen](../data-analyst/analysis/google-track-user-acq.md). Ein Benutzer, der sich über eine Quelle registriert hat, kann auch weiterhin über andere Quellen auf Ihre Website zugreifen.
* **[!UICONTROL Device]**: Steigt die Anzahl der Bestellungen auf Mobilgeräten? Wie viel Ihres Umsatzes wird durch mobile Käufe generiert? (Wenn Sie dies noch nicht verfolgen, finden Sie in diesem Thema [Informationen zum Verfolgen von Bestellgerätedaten](../data-analyst/analysis/track-usr-dev-browser.md) weitere Informationen.
* **[!UICONTROL Fulfillment Center]**: Welches Ihrer Fulfillment-Zentren generiert den meisten Umsatz? Wenn Sie den Unterschied zwischen Bestellzeit und Versandzeit analysieren, welches Ausführungscenter reagiert am besten?
* **[!UICONTROL Delivery Carrier]**: Welcher ist der beliebteste Anbieter? Welcher Netzbetreiber hat die geringste Anzahl an zurückgegebenen Artikeln?
* **[!UICONTROL Discount / Coupon Codes]**: Generieren Ihre Promotions tatsächlich ein zusätzliches Geschäft? Wie viele zusätzliche Artikel haben Ihre Kunden zusätzlich zum Artikel gekauft? Wie beeinflussen Gutscheine Ihren durchschnittlichen Bestellwert? Wie hoch ist Ihre durchschnittliche Marge bei diskontierten und nicht diskontierten Artikeln?
* **[!UICONTROL Satisfaction / Rating]**: Wie zufrieden sind Ihre Kunden mit ihren Bestellungen? Sind Ihre Kunden wahrscheinlich auf Sie verweisen?

## Produktsegmente

Mit Produktsegmenten können Sie Merchandising-Entscheidungen treffen.

* **[!UICONTROL Merchant / Brand]**: Verkauft eine bestimmte Marke schneller als der Rest? Welche Marken sind leistungsschwach?
* **[!UICONTROL Type / Category]**: Genießen unterschiedliche Benutzersegmente unterschiedliche Typen von Produkten? Welche Produktkategorien generieren das sich am häufigsten wiederholende Geschäft?
* **[!UICONTROL Discount / Coupon Codes]**: Schaden Promotions dem Verkauf von Produkten ohne Rabatt? Wie beeinflussen Gutscheine den wahrgenommenen Wert Ihrer Produkte?
* **[!UICONTROL Social Activity]**: Besteht ein Zusammenhang zwischen dem in sozialen Medien generierten Buzz und der für ein Produkt verkauften Menge?
* **[!UICONTROL Size / Variant]**: Wie hoch ist das Verhältnis des Bestands, das Sie für jede Variante benötigen? Welche Varianten können zu Rabattpreisen verkauft werden?

Wenn Sie an Merchandising interessiert sind, sehen Sie sich [an, wie Sie Produktsegmente verwenden können, um das Wiederholungsgeschäft zu fördern](../data-analyst/analysis/most-value-source-channel.md).

## Kundenprofile erstellen

Experten für Segmentierung möchten möglicherweise über eindimensionale Segmente hinausgehen und mit der Erstellung echter Kundenprofile beginnen. Beispielsweise werden Personen zwischen 13 und 24 Jahren, die sich über ein Mobilgerät registriert haben, in die Gruppe &quot;Young &amp; Mobile&quot;aufgenommen. Wie unterscheidet sich das Verhalten dieser Gruppe vom Rest Ihrer Benutzerbasis?

Diese Art von Analyse machen Marketer in Fortune 1000-Unternehmen den ganzen Tag. Vor der Einführung Cloud-basierter Business Intelligence-Plattformen wie [!DNL Commerce Intelligence] war sie für den Rest von uns größtenteils außer Reichweite. Zum Glück ist dies nicht mehr der Fall.

## Verfolgen neuer Segmente

Der erste Schritt zur Segmentierung Ihrer Metriken nach den oben genannten Dimensionen besteht darin sicherzustellen, dass Sie diese Daten in Ihrer Datenbank verfolgen. Wenn sie nicht verfolgt wird, wenden Sie sich an Ihr Technikerteam und finden Sie eine Möglichkeit, das Tracking dieser Daten zu starten.

Nachdem Sie bestätigt haben, dass die Daten in Ihrer Datenbank nachverfolgt werden, wenden Sie sich an [das Supportteam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um die Dimensionen an Ihre [!DNL Commerce Intelligence] -Metriken und -diagramme zu senden. Sie können auch das Tool *Feldverwaltung* verwenden, um diese Felder in [!DNL Commerce Intelligence] zu verfolgen.

## Verwandte

* [Datenbank für Analysen optimieren](../best-practices/opt-db-analysis.md)
