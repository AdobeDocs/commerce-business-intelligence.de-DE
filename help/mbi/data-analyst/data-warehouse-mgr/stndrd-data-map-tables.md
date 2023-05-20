---
title: Daten mit Zuordnungstabellen standardisieren
description: Erfahren Sie, wie Sie mit Zuordnungstabellen arbeiten.
exl-id: e452ff87-f298-43d5-acc3-af58e53bd0bc
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Daten mit Zuordnungstabellen standardisieren

Stellen Sie sich vor, Sie befinden sich im `Report Builder` Erstellen eines `Revenue by State` Bericht. Alles läuft gut, bis Sie versuchen, eine `billing state` -Gruppierung zu Ihrem Bericht hinzufügen, wird dies angezeigt:

![](../../assets/Messy_State_Segments.png)

## Wie konnte das passieren?

Leider kann ein Mangel an Standardisierung manchmal zu undurchsichtigen Daten und Kopfschmerzen bei der Erstellung von Berichten führen. In diesem Beispiel gab es für Ihre Kunden möglicherweise kein Dropdown-Menü oder keine standardisierte Möglichkeit, ihre Rechnungsstatusinformationen einzugeben. Dies führt zu verschiedenen Werten - `pa`, `PA`, `penna`, `pennsylvania`und `Pennsylvania` - alle für denselben Status, was zu einigen seltsamen Ergebnissen in der `Report Builder`.

Es ist möglich, dass es eine technische Ressource gibt, mit der Sie die Daten bereinigen oder die benötigten Spalten direkt in Ihre Datenbank einfügen können. Wenn nicht, gibt es eine andere Lösung - **Zuordnungstabelle**. Mit einer Zuordnungstabelle können Sie schnell und einfach alle chaotischen Daten bereinigen und standardisieren, indem Sie Daten einer einzigen Ausgabe zuordnen.

>[!NOTE]
>
>Sie können keine Zuordnungstabelle für konsolidierte Tabellen erstellen, ohne Hilfe des Adobe Support-Teams zu erhalten.

## Wie erstelle ich es? {#how}

**Datenformatierungsaktualisierung:**

* Stellen Sie sicher, dass das Arbeitsblatt über eine Kopfzeile verfügt.
* Vermeiden Sie die Verwendung von Kommas! Dies verursacht Probleme beim Hochladen der Datei.
* Standarddatumsformat verwenden `(YYYY-MM-DD HH:MM:SS)` für Datumsangaben.
* Prozentangaben müssen als Dezimalstellen angegeben werden.
* Stellen Sie sicher, dass alle führenden oder nachfolgenden Nullen korrekt beibehalten werden.

Bevor Sie eintauchen, empfiehlt Adobe, dass Sie [Rohtabellendaten exportieren](../../tutorials/export-raw-data.md). Wenn Sie sich die Rohdaten zuerst ansehen, können Sie alle möglichen Kombinationen für die Daten untersuchen, die Sie bereinigen müssen, und so sicherstellen, dass die Zuordnungstabelle alles abdeckt.

Um eine Zuordnungstabelle zu erstellen, müssen Sie eine zweispaltige Tabelle erstellen, die auf die [Formatierungsregeln für Datei-Uploads](../../data-analyst/importing-data/connecting-data/using-file-uploader.md).

Geben Sie in der ersten Spalte die in Ihrer Datenbank gespeicherten Werte mit **nur einen Wert in jeder Zeile**. Beispiel: `pa` und `PA` kann nicht auf derselben Zeile stehen - jede Eingabe muss eine eigene Zeile aufweisen. Ein Beispiel finden Sie unten.

Geben Sie in der zweiten Spalte an, welche Werte diese Werte aufweisen sollen **sollte**. Fahren Sie mit dem Rechnungsstatusbeispiel fort, wenn Sie möchten `pa`, `PA`, `Pennsylvania`und `pennsylvania` einfach `PA`eingeben `PA` in dieser Spalte für jeden Eingabewert.

![](../../assets/Mapping_table_examples.jpg)

## Was muss ich tun? [!DNL Commerce Intelligence] verwenden? {#use}

Nachdem Sie die Erstellung der Zuordnungstabelle abgeschlossen haben, müssen Sie [Datei hochladen](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) in [!DNL Commerce Intelligence] und [eine verbundene Spalte erstellen](../../data-analyst/data-warehouse-mgr/calc-column-types.md) , das das neue Feld in die gewünschte Tabelle verschiebt. Sie können dies tun, nachdem die Datei mit Ihrer Data Warehouse synchronisiert wurde.

Im folgenden Beispiel wird die Spalte verschoben, die Sie für die `mapping_state` table (`state_input`) auf `customer_address` -Tabelle mit einer verbundenen Spalte. Dies ermöglicht es uns, nach der Sauberkeit zu gruppieren `state_input` in Ihren Berichten anstelle der `state` Spalte.

So erstellen Sie die `joined` Navigieren Sie im Data Warehousen-Manager zu der Tabelle, zu der das Feld verschoben werden soll. In diesem Beispiel wäre dies die `customer_address` Tabelle.

1. Klicken **[!UICONTROL Create a Column]**.
1. Auswählen `Joined Column` von `Definition` Dropdown-Liste.
1. Geben Sie der Spalte einen Namen, der sie vom `state` in Ihrer Datenbank. Benennen Sie die Spalte. `billing state (mapped)` damit Sie feststellen können, welche Spalte bei der Segmentierung in ReportBuilder verwendet werden soll.
1. Der Pfad, den Sie zum Verbinden der Tabellen benötigen, ist nicht vorhanden. Daher müssen Sie eine erstellen. Klicken **[!UICONTROL Create new path]**  im `Select a table and column` Dropdown-Liste.

   Wenn Sie sich nicht sicher sind, was die Tabellenbeziehung ist oder wie Sie die primären und Fremdschlüssel richtig definieren, überprüfen Sie [das Tutorial](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md) für Hilfe.

   * Im `Many` die Tabelle, in die Sie das Feld umsiedeln möchten, auswählen (für uns ist es erneut `customer_address`) und der `Foreign Key` Spalte oder `state` -Spalte im Beispiel.
   * Im `One` und wählen Sie die `mapping` und `Primary key` Spalte. In diesem Fall wählen Sie die `state_input` aus der `mapping_state` Tabelle.
   * Hier sehen Sie, wie der Pfad aussieht:

      ![](../../assets/State_Mapping_Path.png)

1. Klicken Sie abschließend auf **[!UICONTROL Save]** , um den Pfad zu erstellen.
1. Der Pfad wird möglicherweise nicht sofort nach dem Speichern aufgefüllt. Klicken Sie in diesem Fall auf die `Path` und wählen Sie den erstellten Pfad aus.
1. Klicken **[!UICONTROL Save]** , um die Spalte zu erstellen.

## Was mache ich jetzt? {#wrapup}

Nach Abschluss eines Aktualisierungszyklus können Sie Ihre neue zugeordnete Spalte verwenden, um Ihre Daten ordnungsgemäß zu segmentieren, anstatt die unrichtige Spalte aus Ihrer Datenbank zu verwenden. Sehen Sie sich Ihre Gruppierungsoptionen jetzt an - kein Stressversagen mehr:

![](../../assets/Clean_State_Segments.png)

Zuordnungstabellen sind jederzeit praktisch, wenn Sie einige potenziell unsaubere Daten in Ihrer Data Warehouse bereinigen möchten. Zuordnungstabellen können jedoch auch für einige andere coole Anwendungsfälle verwendet werden, z. B. [Replizieren Ihrer [!DNL Google Analytics channels] in [!DNL Commerce Intelligence]](../data-warehouse-mgr/rep-google-analytics-channels.md).

### Verwandte

* [Grundlegendes zu und Auswerten von Tabellenbeziehungen](../data-warehouse-mgr/table-relationships.md)
* [Pfade für berechnete Spalten erstellen/löschen](../data-warehouse-mgr/create-paths-calc-columns.md)
