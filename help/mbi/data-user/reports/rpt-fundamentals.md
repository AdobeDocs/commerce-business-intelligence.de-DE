---
title: Verwenden eines Berichts
description: Erfahren Sie, wie Sie Ihre Berichtsdaten verwenden.
exl-id: 94d4db27-0e06-4066-9c03-036b109d2d9b
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# Verwenden eines Berichts

Verwenden von Berichten in [!DNL Adobe Commerce Intelligence] um Ihnen bei der Beantwortung von Geschäftsfragen zu helfen - ob Sie einfach den Umsatz dieses Monats im Vergleich zum letzten Jahr sehen oder Ihre Akquisekosten für Ihre neuesten [!DNL Google AdWords] Kampagne.

Wie sieht der Weg von Frage zu Antwort genau aus?

Um Ihnen bei der Visualisierung dieses Prozesses zu helfen, wird diese Route unten zugeordnet. Dieses Thema zeigt, wie Sie eine analytische Frage angehen, und wie die Backend-Logistik, die erforderlich ist, um Ihnen die benötigten Daten zu liefern.

## Beginnen mit der Frage

Sie wissen, dass Sie ständig Fragen stellen, um Ihr Geschäft zu verbessern, von der Steigerung der Kundenzufriedenheit bis zur Senkung der Lieferkosten. Sie konzentrieren sich darauf, wie Sie Ihre Fragen in Analysen übersetzen können, die Ihnen bei der Entscheidungsfindung helfen.

Angenommen, Sie möchten die folgende Frage beantworten:

* Wie schnell konvertieren meine neuen Registrierungspflichtigen?

## Kennzeichnen einer Messung

Es ist an der Zeit, eine Liste möglicher Analysen und Messungen zu ermitteln, um die Frage zu beantworten. In diesem Beispiel konzentrieren Sie sich auf die folgende Metrik:

* Durchschnittliche Zeit von der Registrierung bis zum ersten Kaufdatum pro Verwendung.

Dies zeigt die durchschnittliche Zeit, die zwischen dem Registrierungsdatum und dem ersten Kaufdatum des Benutzers vergeht, und gibt eine Vorstellung davon, wie sich Benutzer bei diesem letzten Schritt im Konversionstrichter verhalten.

## Suchen nach Daten

Das Verständnis, was gemessen werden soll, bringt uns nur dazu, dorthin zu gelangen. Um die durchschnittliche Zeit von der Registrierung bis zum ersten Kaufdatum pro Benutzer zu bewerten, müssen Sie alle Datenpunkte identifizieren, aus denen Ihre Kennzahl besteht.

Schlüsseln Sie Ihre Kennzahl in die Kernkomponenten auf. Sie müssen wissen, wie viele Personen sich registriert haben, wie viele Personen einen Kauf getätigt haben und wie viel Zeit zwischen diesen beiden Ereignissen vergangen ist.

Auf einer höheren Ebene müssen Sie wissen, wo diese Daten in der Datenbank zu finden sind, insbesondere:

* Die Tabelle, die bei jeder Registrierung eine Datenzeile aufzeichnet
* Die Tabelle, die eine Datenzeile aufzeichnet, die jedes Mal, wenn ein Besucher einen Kauf tätigt,
* Die Spalte, die verwendet werden kann, um der `purchase` -Tabelle `customer` table - ermöglicht es uns zu wissen, wer einen Kauf getätigt hat

Auf einer detaillierteren Ebene müssen Sie die genauen Datenfelder identifizieren, die für diese Analyse verwendet werden:

* Die Datentabelle und -spalte mit dem Registrierungsdatum eines Kunden, z. B. `user.created\_at`
* Die Datentabelle und -spalte mit einem Kaufdatum, z. B.: `order.created\_at`

## Datenspalten für Analysen erstellen

Zusätzlich zu den oben genannten nativen Datenspalten benötigen Sie auch eine Reihe berechneter Datenfelder, um diese Analyse zu ermöglichen, darunter:

* `Customer's first purchase date` , der die `MIN(order.created_at`)

Dies wird dann zum Erstellen von Folgendem verwendet:

* `Time between a customer's registration date and first purchase date`, der die Zeit eines bestimmten Benutzers zwischen der Registrierung und dem ersten Kaufdatum zurückgibt. Dies ist die Grundlage für Ihre Metrik später.

Beide Felder müssen auf Benutzerebene erstellt werden (z. B. auf der `user` Tabelle). Dadurch kann die durchschnittliche Analyse von Benutzern normalisiert werden (d. h. der Nenner in dieser durchschnittlichen Berechnung ist die Anzahl der Benutzer).

Hier [!DNL Commerce Intelligence] Schritte ein! Sie können Ihre [!DNL Commerce Intelligence] Data Warehouse , um die obigen Spalten zu erstellen. Wenden Sie sich an das Adobe Analyst-Team und geben Sie uns die genaue Definition Ihrer neuen Spalten zur Erstellung an. Sie können auch die [Spalteneditor](../../data-analyst/data-warehouse-mgr/creating-calculated-columns.md).

Es empfiehlt sich, diese berechneten Datenfelder nicht direkt in Ihrer Datenbank zu erstellen, da dies Ihre Produktionsserver unnötig belastet.

## Erstellen der Metrik

Nachdem Sie nun über die erforderlichen Datenfelder für die Analyse verfügen, ist es an der Zeit, die relevante Metrik zu finden oder zu erstellen, um Ihre Analyse zu erstellen.

Hier wird die folgende Berechnung durchgeführt:


_[SUM von `Time between a customer's registration date and first purchase date`] / [Gesamtzahl der Kunden, die sich registriert und gekauft haben]_

Und Sie möchten diese Berechnung im Zeitverlauf bzw. im Trend sehen, je nach Registrierungsdatum des Kunden. Und hier sehen Sie, wie Sie [diese Metrik erstellen](../../data-user/reports/ess-manage-data-metrics.md) in [!DNL Commerce Intelligence]:

1. Navigieren Sie zu **[!UICONTROL Data]** und wählen Sie die `Metrics` Registerkarte.
1. Klicks **[!UICONTROL Add New Metric]** und wählen Sie die `user` -Tabelle (in der Sie die oben genannten Dimensionen erstellt haben).
1. Wählen Sie aus der Dropdown-Liste `Average` auf`Time between a customer's registration date and first purchase date` in der `user` nach der `Customer's registration date`  Spalte.
1. Fügen Sie alle relevanten Filter oder Filtersätze hinzu.

Diese Metrik ist jetzt bereit.

## Berichtserstellung

Wenn die neue Metrik eingerichtet ist, können Sie sie verwenden, um die durchschnittliche Zeit zwischen der Registrierung und dem ersten Kaufdatum nach Registrierungsdatum zu melden.

Gehen Sie einfach zu einem beliebigen Dashboard und [einen Bericht erstellen](../../data-user/reports/ess-manage-data-metrics.md) unter Verwendung der oben erstellten Metrik.

### `Visual Report Builder` {#visualrb}

[Die `Visual Report Builder`](../../data-user/reports/ess-rpt-build-visual.md) ist die einfachste Möglichkeit, Ihre Daten zu visualisieren. Wenn Sie nicht mit SQL vertraut sind oder einen Bericht schnell erstellen möchten, ist Visual Report Builder die beste Wahl. Mit nur wenigen Klicks können Sie Metriken hinzufügen, Ihre Daten segmentieren und Berichte für Ihre gesamte Organisation erstellen. Diese Option eignet sich sowohl für Anfänger als auch für Experten, da sie keinerlei Fachkenntnisse erfordert.

|  |  |
|--- |--- |
| **Das ist perfekt für ...** | **Das ist nicht so toll für ...** |
| - Alle Ebenen der Analyse/des technischen Erlebnisses<br>- Schnelles Erstellen von Berichten<br>- Erstellen von Analysen zur Freigabe für andere Benutzer | - Analysen, die SQL-spezifische Funktionen erfordern<br>- Testen neuer Spalten - berechnete Spalten hängen von Aktualisierungszyklen für die anfängliche Datenpopulation ab, die mit SQL erstellten Spalten nicht. |

{style="table-layout:auto"}

### Berichtbeschreibungen und Bilder

#### Hinzufügen von Beschreibungen zu Berichten

Bei der Erstellung von Berichten, die mit anderen Team-Mitgliedern geteilt werden, empfiehlt Adobe das Hinzufügen von Beschreibungen, die es anderen Benutzern ermöglichen, Ihre Analyse besser zu verstehen.

1. Klicks **[!UICONTROL i]** oben in jedem Bericht.
1. Geben Sie eine Beschreibung in das Wortfeld ein.
1. Klicken **[!UICONTROL Save Description]**.

Siehe unten:

![Diagrammbeschreibung](../../assets/Chart_Description.gif)

#### Exportieren von Berichten als Bilder

Muss ein Bericht in eine Präsentation oder ein Dokument aufgenommen werden? Jeder Bericht kann als Bild gespeichert werden (im PNG-, PDF- oder SVG-Format), indem Sie die `Report Options` in der oberen rechten Ecke eines jeden Berichts.

1. Klicken Sie auf das Zahnradsymbol in der oberen rechten Ecke eines Berichts.
1. Wählen Sie aus der Dropdown-Liste `Enlarge`.
1. Wenn der Bericht vergrößert wird, klicken Sie **[!UICONTROL Download]** in der oberen rechten Ecke des Berichts.
1. Wählen Sie aus der Dropdown-Liste das gewünschte Bildformat aus. Der Download beginnt sofort.

Siehe unten:

![](../../assets/exp-rep-as-image.gif)
