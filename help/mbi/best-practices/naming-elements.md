---
title: Benennen von Berichten und Elementen in Commerce Intelligence
description: Best Practices für die Benennung von Berichten und Elementen in [!DNL Commerce Intelligence].
exl-id: c662cedd-c779-4254-b04b-f3092a538c85
role: Admin, User
feature: Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---

# Berichte und Elemente benennen

Bevor Sie mit dem Erstellen in [!DNL Adobe Commerce Intelligence] beginnen, möchte Adobe einige Erfolgsgeheimnisse teilen. Es ist wichtig zu wissen, wie Metriken, Filter usw. erstellt werden, aber Ihre gesamte Arbeit kann umsonst sein, wenn Sie nicht finden können, was Sie benötigen, oder wenn Unklarheiten bestehen.

## Warum ist die Nomenklatur wichtig? {#why}

Die Art und Weise, wie Sie Ihre berechneten Spalten, Metriken und Berichte benennen, bestimmt die Leichtigkeit, mit der verschiedene Benutzer durch Ihr [!DNL Commerce Intelligence] navigieren können. Beachten Sie beim Benennen dieser Funktionen die drei folgenden Cs:

* **KLARHEIT** - Auf einen Blick erkennen Sie also, was in einem Bericht angezeigt wird, was eine Metrik tut usw.
* **KONSISTENZ** - Damit Sie (und das Adobe-Supportteam) Elemente und Berichte in Ihrem Account einfach finden und verstehen können.
* **GLAUBWÜRDIGKEIT** - Um andere datengesteuerte [!DNL Commerce Intelligence]-Benutzer zu inspirieren und zu befähigen, müssen Sie Vertrauen in die Art und Weise schaffen, wie sie die Daten verstehen und verwenden!

Lesen Sie weiter für bewährte Nomenklaturtipps!

## Allgemeine Best Practices {#general}

### Bedeutung haben {#meaningful}

Seien Sie wann immer möglich genau! Wenn es sich beispielsweise um das Land handelt, wissen Sie dann, ob es sich um das Versand- oder das Abrechnungsland handelt? Ist es die Stadt des Nutzers oder die Stadt des Deals?

**Ungültiges Beispiel:**
Einnahmen

Das ist vage und sagt uns nicht viel.

**Gute Beispiele:**
Einnahmen (Gesamtsumme + Gebühr)
Versandland des Benutzers

Diese Beispiele sind spezifisch, was das Verwirrungspotenzial verringert.

### Konsistenz mit der Groß-/Kleinschreibung {#capitalize}

[!DNL Adobe] wird empfohlen, dass der erste Buchstabe großgeschrieben wird, während der Rest der Zeichen kleingeschrieben ist, es sei denn, der Substantivstil wird großgeschrieben. Beispiel: **Bestellnummer des Benutzers** anstatt **Bestellnummer des Benutzers.**

Dies ist wirklich eine Frage der Präferenz, aber die Sache, an die man denken sollte, ist, mit allem, was man wählt, konsistent zu sein.

### Einheitlichkeit der Entität {#entity}

Wahrscheinlich haben Sie bereits eine Nomenklatur in Ihrem Unternehmen. Halten Sie die von Ihnen eingerichteten Metriken und Dimensionen konsistent mit dem, was in anderen Datenbanken und Tools verwendet wird. Beispiel:

* Benutzer vs. Kunde vs. Mitglied vs. Konto
* Firma vs. Konto vs. Organisation
* Registrierung vs. Erstellung

### Rechtschreibung und Grammatik {#spelling}

Achten Sie darauf, Ihre Schreibweise zu überprüfen und vergessen Sie nicht diese nervigen Possessives!

## Diagramme {#charts}

Bei der Benennung [Diagramme](../tutorials/using-visual-report-builder.md) ist es am nützlichsten, diese Formel zu verwenden: **(Datenperspektive) + (Metrik) + (Zeitraum) + (Zeitintervall)**

**Ungültiges Beispiel:**
Einnahmen

Das sagt uns nichts über den Bericht aus, was schlecht ist.

**Gutes Beispiel:**
Kumulativer Umsatz nach 30 Tagen und Monat

Das sagt uns **genau** was in dem Bericht steht, was fantastisch ist.

## Dashboards {#dashboards}

Dashboards sollten so benannt werden, dass sie die darin enthaltenen Berichte thematisch darstellen. Wenn Ihr Dashboard beispielsweise nur Informationen zu Umsatz und Bestellungen enthält, sollten Sie es z. B. **Store-Name - Umsatz und Bestellungen“ benennen**

Wenn Ihr Dashboard jedoch ein Ort ist, an dem Sie mit verschiedenen Berichten experimentieren, sollten Sie es **Sandbox Ihres Namens“ benennen** damit Sie wissen, dass die darin enthaltenen Berichte Entwürfe sind.

## Dimensionen (berechnete Spalten) {#dimensions}

Beim Benennen neuer [Dimensionen](../data-analyst/data-warehouse-mgr/creating-calculated-columns.md) ist es am nützlichsten, diese Formel zu verwenden: **(Entität) + (N-te) + (Zeitrahmen) + (Berechnung) + (Kommentare)**. Beispiel:

Umsatz des Benutzers für die ersten 30 Tage
* Bestellnummer des Benutzers
* Auftragsnummer des Benutzers (Prüfung ausstehend)

## Filtersätze {#filterset}

[Filtersätze](../data-user/reports/ess-manage-data-filters.md) werden normalerweise so benannt, dass sie die Informationen erläutern, die sie einschließen oder ausschließen. Beispielsweise ermöglicht die Benennung eines Filtersatzes **Bestellungselemente, die wir zählen** jedem Benutzer, hineinzugehen, die Logik des Filtersatzes anzuzeigen und zu verstehen, welche Bestellungsinformationen bestimmen, was im gesamten Unternehmen gezählt wird. Denken Sie daran, dass Filtersätze sowohl auf berechnete Spalten als auch auf Metriken angewendet werden können und leicht verständlich sein sollten.

## Metriken {#metrics}

[Metriken](../data-user/reports/ess-manage-data-metrics.md) sind im Wesentlichen Fragen, auf die Sie regelmäßig Antworten finden möchten. Wie viele Bestellungen gab es im letzten Monat? Wie hoch ist der durchschnittliche Lebenszeitwert Ihrer Kunden? Es empfiehlt sich, Metriken so zu benennen, dass sie die Antwort widerspiegeln, die sie den Benutzern geben. Wenn dieselbe Metrik nach einem bestimmten Geschäft oder einer bestimmten Abteilung gefiltert wurde, sollten diese als solche gekennzeichnet werden. Beispiel:

Durchschnittliche Kunden-LTV (erste 30 Tage)
Name speichern - Umsatz

Schließlich kann dieselbe Metrik manchmal durch verschiedene Zeitstempel organisiert werden, je nachdem, wie die einzelnen Benutzer sie berechnen. Wenn ja, stellen Sie sicher, dass Sie den Zeitstempel in den Namen aufnehmen:

Umsatz (versendet\_at)
Umsatz (erstellt\_at)

## Verpackung {#wrapup}

Das frühzeitige Einrichten von Stil- und Namenskonventionen hilft Ihnen bei der erfolgreichen Einrichtung Ihres [!DNL Commerce Intelligence]. Denken Sie an die drei Dinge: Klarheit, Konsistenz und Glaubwürdigkeit.
