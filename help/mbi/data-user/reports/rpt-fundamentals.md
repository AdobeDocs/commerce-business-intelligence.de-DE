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

Verwenden Sie Berichte in [!DNL Adobe Commerce Intelligence], um geschäftliche Fragen zu beantworten - egal, ob Sie einfach den Umsatz dieses Monats im Vergleich zum Vorjahr sehen möchten oder Ihre Anschaffungskosten für Ihre neueste [!DNL Google AdWords]-Kampagne verstehen möchten.

Wie sieht der Weg von der Frage zur Antwort genau aus?

Diese Route ist unten dargestellt, um Ihnen bei der Visualisierung dieses Prozesses zu helfen. Dieses Thema beleuchtet sowohl, wie Sie eine analytische Frage angehen, als auch die Backend-Logistik, die erforderlich ist, um Ihnen die benötigten Daten zu liefern.

## Beginnen wir mit der Frage

Sie wissen, dass Sie ständig Fragen stellen, um Ihr Geschäft zu verbessern, von der Erhöhung der Kundenzufriedenheit bis zur Senkung der Lieferkosten. Sie konzentrieren sich darauf, wie Sie Ihre Fragen in Analysen übersetzen können, die Ihnen bei der Entscheidungsfindung helfen.

Nehmen wir für dieses Beispiel an, dass Sie die folgende Frage beantworten möchten:

* Wie schnell konvertieren meine neuen Registrierenden?

## Kennzahlen identifizieren

Es ist an der Zeit, eine Liste möglicher Analysen und Messungen zu erstellen, um die Frage zu beantworten. Konzentrieren Sie sich in diesem Beispiel auf die folgende Metrik:

* Durchschnittliche Zeit von der Registrierung bis zum ersten Kaufdatum pro Verwendung.

Dadurch wird die durchschnittliche Zeit zwischen dem Registrierungsdatum und dem ersten Kaufdatum des Benutzers angezeigt und eine Vorstellung davon gegeben, wie sich Benutzer in diesem letzten Schritt im Konversionstrichter verhalten.

## Ermitteln der Daten

Zu verstehen, was zu messen ist, verschafft uns nur einen Teil des Weges dorthin. Um die durchschnittliche Zeit von der Registrierung bis zum ersten Kaufdatum pro Benutzer zu bewerten, müssen Sie alle Datenpunkte identifizieren, aus denen Ihre Kennzahl besteht.

Schlüsseln Sie Ihre Kennzahl in ihre Kernkomponenten auf. Sie müssen die Anzahl der registrierten Personen, die Anzahl der Personen, die einen Kauf getätigt haben und die Zeit zwischen diesen beiden Ereignissen kennen.

Auf höherer Ebene müssen Sie wissen, wo Sie diese Daten in der Datenbank finden, insbesondere:

* Die Tabelle, die jedes Mal, wenn sich jemand registriert, eine Datenzeile aufzeichnet
* Die Tabelle, die jedes Mal, wenn jemand einen Kauf tätigt, eine Datenzeile aufzeichnet
* Die Spalte, die verwendet werden kann, um die `purchase`-Tabelle mit der `customer`-Tabelle zu verbinden oder darauf zu verweisen - dies ermöglicht es uns zu wissen, wer einen Kauf getätigt hat

Auf einer detaillierteren Ebene müssen Sie die genauen Datenfelder identifizieren, die für diese Analyse verwendet werden:

* Die Datentabelle und -spalte, die das Registrierungsdatum eines Kunden enthalten: z. B. `user.created\_at`
* Die Datentabelle und -spalte, die ein Kaufdatum enthalten: z. B. `order.created\_at`

## Datenspalten für Analysen erstellen

Zusätzlich zu den oben beschriebenen nativen Datenspalten benötigen Sie auch einen Satz berechneter Datenfelder, um diese Analyse zu ermöglichen, einschließlich:

* `Customer's first purchase date`, das die `MIN(order.created_at` eines bestimmten Benutzers zurückgibt)

Diese wird dann verwendet, um Folgendes zu erstellen:

* `Time between a customer's registration date and first purchase date`, die die Zeit zurückgibt, die zwischen der Registrierung und dem ersten Kaufdatum eines bestimmten Benutzers verstrichen ist. Dies ist die Grundlage für Ihre Metrik später.

Beide Felder müssen auf Benutzerebene erstellt werden (z. B. in der `user`). Dies ermöglicht eine Normalisierung der Durchschnittsanalyse durch die Benutzer (d. h., der Nenner bei dieser Durchschnittsberechnung ist die Anzahl der Benutzer).

Hier kommt [!DNL Commerce Intelligence] ins Spiel! Sie können Ihre [!DNL Commerce Intelligence] Data Warehouse verwenden, um die oben genannten Spalten zu erstellen. Wenden Sie sich an das Adobe-Analyst-Team und geben Sie uns die spezifische Definition Ihrer neuen Spalten für die Erstellung an. Sie können auch den [Spalteneditor“ ](../../data-analyst/data-warehouse-mgr/creating-calculated-columns.md).

Es empfiehlt sich, die Erstellung dieser berechneten Datenfelder in Ihrer Datenbank zu vermeiden, da dies eine unnötige Belastung für Ihre Produktions-Server darstellt.

## Metrik erstellen

Nachdem Sie nun über die erforderlichen Datenfelder für die Analyse verfügen, ist es an der Zeit, die entsprechende Metrik zu finden oder zu erstellen, um Ihre Analyse zu erstellen.

Führen Sie hier die folgende Berechnung durch:


_[SUMME der `Time between a customer's registration date and first purchase date`] / [Gesamtzahl der Kunden, die sich registriert und gekauft haben]_

Und Sie möchten sehen, dass diese Berechnung über die Zeit, oder den Trend, eingezeichnet wird basierend auf dem Registrierungsdatum eines Kunden. So erstellen Sie [diese Metrik](../../data-user/reports/ess-manage-data-metrics.md) in [!DNL Commerce Intelligence]:

1. Wechseln Sie zu **[!UICONTROL Data]** und wählen Sie die Registerkarte `Metrics` aus.
1. Klicken Sie auf **[!UICONTROL Add New Metric]** und wählen Sie die `user` aus (in der Sie die Dimensionen oben erstellt haben).
1. Wählen Sie aus dem Dropdown-Menü `Average` in der Spalte `Time between a customer's registration date and first purchase date``user` in der Tabelle nach `Customer's registration date` sortiert aus.
1. Fügen Sie alle relevanten Filter oder Filtersätze hinzu.

Diese Metrik ist jetzt bereit.

## Erstellen des Berichts

Wenn die neue Metrik eingerichtet ist, können Sie sie verwenden, um die durchschnittliche Zeit zwischen der Registrierung und dem ersten Kaufdatum nach Registrierungsdatum zu melden.

Wechseln Sie einfach zu einem beliebigen Dashboard und [erstellen Sie einen Bericht](../../data-user/reports/ess-manage-data-metrics.md) mithilfe der oben erstellten Metrik.

### `Visual Report Builder` {#visualrb}

[Die `Visual Report Builder`](../../data-user/reports/ess-rpt-build-visual.md) ist der einfachste Weg, Ihre Daten zu visualisieren. Wenn Sie mit SQL nicht vertraut sind oder schnell einen Bericht erstellen möchten, ist der Visual Report Builder Ihre beste Wahl. Mit nur wenigen Klicks können Sie Metriken hinzufügen, Ihre Daten segmentieren und Berichte erstellen, um sie in Ihrem gesamten Unternehmen zu verwalten. Diese Option ist sowohl für Anfänger als auch für Experten ideal, da sie keine technische Expertise erfordert.

|  |  |
|--- |--- |
| **Dies ist perfekt für…** | **Das ist nicht so toll für…** |
| - Alle Ebenen der Analyse/des technischen Erlebnisses<br>- Schnelles Erstellen von Berichten<br>- Erstellen von Analysen zur gemeinsamen Nutzung mit anderen Benutzern | - Analysen, die SQL-spezifische Funktionen erfordern<br>- Testen neuer Spalten - Berechnete Spalten hängen von Aktualisierungszyklen für die anfängliche Datenpopulation ab, während solche, die mit SQL erstellt wurden, nicht funktionieren. |

{style="table-layout:auto"}

### Berichtsbeschreibungen und Bilder

#### Hinzufügen von Beschreibungen zu Berichten

Beim Erstellen von Berichten, die für andere Mitglieder Ihres Teams freigegeben werden, empfiehlt Adobe, Beschreibungen hinzuzufügen, die es anderen Benutzenden ermöglichen, Ihre Analyse besser zu verstehen.

1. Klicken Sie oben in einem Bericht auf **[!UICONTROL i]** .
1. Geben Sie eine Beschreibung in das Wortfeld ein.
1. Klicken Sie auf **[!UICONTROL Save Description]**.

Siehe unten:

![Diagrammbeschreibung](../../assets/Chart_Description.gif)

#### Exportieren von Berichten als Bilder

Müssen Sie einen Bericht in eine Präsentation oder ein Dokument aufnehmen? Jeder Bericht kann über das `Report Options`-Menü oben rechts in jedem Bericht als Bild (im PNG-, PDF- oder SVG-Format) gespeichert werden.

1. Klicken Sie auf das Zahnradsymbol in der oberen rechten Ecke eines Berichts.
1. Wählen Sie im Dropdown-Menü `Enlarge` aus.
1. Wenn der Bericht größer wird, klicken Sie oben rechts im Bericht auf **[!UICONTROL Download]** .
1. Wählen Sie in der Dropdown-Liste das bevorzugte Bildformat aus. Der Download beginnt sofort.

Siehe unten:

![](../../assets/exp-rep-as-image.gif)
