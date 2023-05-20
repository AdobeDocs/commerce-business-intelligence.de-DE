---
title: Benennen von Berichten und Elementen in Commerce Intelligence
description: Best Practices für die Benennung von Berichten und Elementen in [!DNL Commerce Intelligence].
exl-id: c662cedd-c779-4254-b04b-f3092a538c85
source-git-commit: 4cad1e05502630e13f7a2d341f263140a02b3d82
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Berichte und Elemente benennen

Bevor Sie mit dem Erstellen beginnen in[!DNL Adobe Commerce Intelligence], möchte Adobe einige Geheimnisse für den Erfolg teilen. Es ist wichtig zu wissen, wie Sie Metriken, Filter usw. erstellen, aber Ihre gesamte Arbeit kann unnötig sein, wenn Sie nicht finden können, was Sie benötigen, oder wenn es Unklarheiten gibt.

## Warum ist die Nomenklatur wichtig? {#why}

Die Art und Weise, wie Sie berechnete Spalten, Metriken und Berichte benennen, macht es erforderlich, dass verschiedene Benutzer durch Ihre [!DNL Commerce Intelligence] -Konto. Beachten Sie bei der Benennung dieser Funktionen die drei CSS:

* **KLARHEIT** - So können Sie auf einen Blick feststellen, was ein Bericht zeigt, was eine Metrik bewirkt usw.
* **KONSISTENZ** - damit Sie (und das Adobe-Supportteam) Elemente und Berichte in Ihrem Konto leicht finden und verstehen können.
* **GLAUBWÜRDIGKEIT** - um andere datengestützte Dienste anzuregen und zu stärken [!DNL Commerce Intelligence] Benutzer, müssen Sie sich darauf verlassen, wie sie die Daten verstehen und verwenden!

Lesen Sie weiter für bewährte und wahre Nomenklatur Tipps!

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

[!DNL Adobe] empfiehlt die Groß-/Kleinschreibung des ersten Buchstabens mit dem Rest der Zeichen in Kleinbuchstaben, es sei denn, es handelt sich um einen ordnungsgemäßen Schreibstil der Groß-/Kleinschreibung. Beispiel: **Bestellnummer des Benutzers** anstelle von **Bestellnummer des Benutzers.**

Das ist wirklich eine Frage der Präferenz, aber die Sache, die man sich merken muss, ist, mit dem, was man wählt, konsistent zu sein.

### Entitätskonsistenz {#entity}

Wahrscheinlich haben Sie bereits eine Nomenklatur in Ihrem Unternehmen. Halten Sie die von Ihnen eingerichteten Metriken und Dimensionen konsistent mit denen in anderen Datenbanken und Tools. Beispiel:

* Benutzer vs. Kunde vs. Mitglied vs. Konto
* Unternehmen vs. Konto vs. Organisation
* Registrierung vs. Erstellung

### Rechtschreibung und Grammatik {#spelling}

Vergewissern Sie sich, dass Sie Ihre Rechtschreibung überprüfen und nicht die pesky Besitzungen vergessen!

## Diagramme {#charts}

Beim Benennen [charts](../tutorials/using-visual-report-builder.md)ist es am nützlichsten, diese Formel zu verwenden: **(Datenperspektive) + (Metrik) + (Zeitraum) + (Zeitintervall)**

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

Beim Benennen neuer [Dimensionen](../data-analyst/data-warehouse-mgr/creating-calculated-columns.md)ist es am nützlichsten, diese Formel zu verwenden: **(Entität) + (Nth) + (Zeitrahmen) + (Berechnung) + (Kommentare)**. Beispiel:

Erster 30-Tage-Umsatz des Benutzers
* Bestellnummer des Benutzers
* Bestellnummer des Benutzers (auf Prüfung warten)

## Filtersätze {#filterset}

[Filtersätze](../data-user/reports/ess-manage-data-filters.md) werden in der Regel so benannt, dass die Informationen, die sie einschließen oder ausschließen, erläutert werden. Beispiel: Benennen eines Filtersatzes **Artikel bestellen, die wir zählen** ermöglicht es jedem Benutzer, einzusteigen, die Logik des Filtersatzes anzuzeigen und zu verstehen, welche Bestellinformationen bestimmen, was im gesamten Unternehmen gezählt wird. Beachten Sie, dass Filtersätze sowohl auf berechnete Spalten als auch auf Metriken angewendet werden können und daher leicht verständlich sein sollten.

## Metriken {#metrics}

[Metriken](../data-user/reports/ess-manage-data-metrics.md) sind im Wesentlichen Fragen, auf die Sie regelmäßig antworten möchten. Wie viele Bestellungen gab es im letzten Monat? Welchen durchschnittlichen Lebenszeitwert haben Ihre Kunden? Es ist Best Practice, Metriken zu benennen, die die Antwort widerspiegeln, die sie Benutzern geben. Wenn dieselbe Metrik für einen bestimmten Store oder eine bestimmte Abteilung gefiltert wurde, sollte sie als solche gekennzeichnet werden. Beispiel:

Durchschnittlicher LTV-Nutzer (erste 30 Tage) Store-Name - Umsatz

Schließlich kann dieselbe Metrik manchmal nach verschiedenen Zeitstempeln organisiert werden, je nachdem, wie einzelne Benutzer sie berechnen. Wenn ja, stellen Sie sicher, dass Sie den Zeitstempel in den Namen aufnehmen:

Umsatz (ausgeliefert\_at) Umsatz (erstellt\_at)

## Aufbrechen {#wrapup}

Die frühzeitige Festlegung von Stil- und Benennungskonventionen hilft Ihnen bei der erfolgreichen Einrichtung Ihrer [!DNL Commerce Intelligence] -Konto. Beachten Sie die drei CSS: Klarheit, Kohärenz und Glaubwürdigkeit.
