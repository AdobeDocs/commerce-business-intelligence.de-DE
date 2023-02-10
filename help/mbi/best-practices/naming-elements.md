---
title: Berichte und Elemente in MBI benennen
description: Best Practices für die Benennung von Berichten und Elementen in [!DNL MBI].
exl-id: c662cedd-c779-4254-b04b-f3092a538c85
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Berichte und Elemente benennen

Bevor Sie mit dem Erstellen beginnen in[!DNL MBI], wollen wir einige unserer Geheimnisse für den Erfolg teilen. Es ist wichtig zu wissen, wie man Metriken, Filter usw. erstellt, aber alles, was funktioniert, ist unnötig, wenn man nicht finden kann, was man braucht, oder wenn es Unklarheiten gibt.

## Warum ist die Nomenklatur wichtig? {#why}

Die Art und Weise, wie Sie berechnete Spalten, Metriken und Berichte benennen, macht es erforderlich, dass verschiedene Benutzer durch Ihre [!DNL MBI] -Konto. Beachten Sie bei der Benennung dieser Funktionen die drei CSS:

* **KLARHEIT** - So können Sie auf einen Blick feststellen, was ein Bericht zeigt, was eine Metrik bewirkt usw.
* **KONSISTENZ** - damit Sie (und unser Supportteam) Elemente und Berichte in Ihrem Konto leicht finden und verstehen können.
* **GLAUBWÜRDIGKEIT** - um andere datengestützte Dienste anzuregen und zu stärken [!DNL MBI] Benutzer, müssen Sie sich darauf verlassen, wie sie die Daten verstehen und verwenden!

Lesen Sie weiter für unsere bewährten und wahren Nomenklatur Tipps!

## Allgemeine Best Practices {#general}

### Seien Sie aussagekräftig {#meaningful}

Seien Sie nach Möglichkeit spezifisch! Wenn es beispielsweise das Land ist, wissen Sie, ob es sich um das Versand- oder das Rechnungsland handelt? Ist es die Stadt des Benutzers oder die Stadt des Deals?

**Schlechtes Beispiel:**
Umsatz

Das ist vage und sagt uns nicht viel.

**Gute Beispiele:**
Umsatz (Grundbetrag + Gebühr) Versandland des Benutzers

Diese Beispiele sind spezifisch, was das Verwirrungspotenzial verringert.

### Konsistent mit Großschreibung sein {#capitalize}

Wir sind große Fans des ersten Buchstabens Großbuchstabe, Rest der Zeichen Kleinbuchstaben, es sei denn, der richtige Substantiv-Stil der Großschreibung. Beispiel: **Bestellnummer des Benutzers** anstelle von **Bestellnummer des Benutzers.**

Das ist wirklich eine Frage der Präferenz, aber die Sache, die man sich merken muss, ist, mit dem, was man wählt, konsistent zu sein.

### Entitätskonsistenz {#entity}

Wahrscheinlich haben Sie bereits eine Nomenklatur in Ihrem Unternehmen. Halten Sie die von Ihnen eingerichteten Metriken und Dimensionen konsistent mit denen in anderen Datenbanken und Tools. Beispiel:

* Benutzer vs. Kunde vs. Mitglied vs. Konto
* Unternehmen vs. Konto vs. Organisation
* Registrierung vs. Erstellung

### Rechtschreibung und Grammatik {#spelling}

Achten Sie darauf, die Rechtschreibung zu überprüfen und nicht die pesky Besitzungen zu vergessen!

## Diagramme {#charts}

Beim Benennen [charts](../tutorials/using-visual-report-builder.md), ist es für uns am nützlichsten, diese Formel zu verwenden: **(Datenperspektive) + (Metrik) + (Zeitraum) + (Zeitintervall)**

**Schlechtes Beispiel:**
Umsatz

Das sagt uns nichts über den Bericht, was schlecht ist.

**Gutes Beispiel:**
Kumulativer Umsatz nach 30 Tagen pro Monat

Das sagt uns **just** was im Bericht steht, was fantastisch ist.

## Dashboards {#dashboards}

Dashboards sollten so benannt werden, dass sie die darin enthaltenen Berichte thematisch darstellen. Wenn Ihr Dashboard beispielsweise nur Informationen zum Umsatz und zu Bestellungen enthält, sollten Sie die Benennung in etwa wie folgt erwägen: **Speichername - Umsatz und Bestellungen.**

Wenn Ihr Dashboard dagegen ein Ort ist, an dem Sie mit verschiedenen Berichten experimentieren, sollten Sie es nennen. **Sandbox Ihres Namens** sodass Sie wissen, dass es sich bei den in enthaltenen Berichten um Entwürfe handelt.

## Dimensionen (berechnete Spalten) {#dimensions}

Beim Benennen neuer [Dimensionen](../data-analyst/data-warehouse-mgr/creating-calculated-columns.md), ist es für uns am nützlichsten, diese Formel zu verwenden: **(Entität) + (Nth) + (Zeitrahmen) + (Berechnung) + (Kommentare)**. Beispiel:

Erster 30-Tage-Umsatz des Benutzers
* Bestellnummer des Benutzers
* Bestellnummer des Benutzers (auf Prüfung warten)

## Filtersätze {#filterset}

[Filtersätze](../data-user/reports/ess-manage-data-filters.md) werden in der Regel so benannt, dass die Informationen, die sie einschließen oder ausschließen, erläutert werden. Beispiel: Benennen eines Filtersatzes **Artikel bestellen, die wir zählen** ermöglicht es jedem Benutzer, einzusteigen, die Logik des Filtersatzes anzuzeigen und zu verstehen, welche Bestellinformationen bestimmen, was im gesamten Unternehmen gezählt wird. Beachten Sie, dass Filtersätze sowohl auf berechnete Spalten als auch auf Metriken angewendet werden können und daher leicht verständlich sein sollten.

## Metriken {#metrics}

[Metriken](../data-user/reports/ess-manage-data-metrics.md) sind im Wesentlichen Fragen, auf die Sie regelmäßig antworten möchten. Wie viele Bestellungen gab es im letzten Monat? Wie hoch ist der durchschnittliche Lebenszeitwert unserer Kunden? Es ist im Allgemeinen Best Practice, Metriken zu benennen, die die Antwort widerspiegeln, die sie Benutzern geben. Wenn dieselbe Metrik für einen bestimmten Store oder eine bestimmte Abteilung gefiltert wurde, sollte sie als solche gekennzeichnet werden. Beispiel:

Durchschnittlicher LTV-Nutzer (erste 30 Tage) Store-Name - Umsatz

Schließlich kann dieselbe Metrik manchmal nach verschiedenen Zeitstempeln organisiert werden, je nachdem, wie einzelne Benutzer sie berechnen. Ist dies der Fall, stellen Sie sicher, dass Sie den Zeitstempel in den Namen einschließen:

Umsatz (ausgeliefert\_at) Umsatz (erstellt\_at)

## Aufbrechen {#wrapup}

Die frühzeitige Festlegung von Stil- und Benennungskonventionen hilft Ihnen bei der erfolgreichen Einrichtung Ihrer [!DNL MBI] -Konto. Denken Sie an die drei Cs: Klarheit, Kohärenz und Glaubwürdigkeit.
