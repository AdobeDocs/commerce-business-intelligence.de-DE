---
title: Daten mit Zuordnungstabellen standardisieren
description: Erfahren Sie, wie Sie mit Zuordnungstabellen arbeiten.
exl-id: e452ff87-f298-43d5-acc3-af58e53bd0bc
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Daten mit Zuordnungstabellen standardisieren

Angenommen, Sie sind im `Report Builder` und erstellen einen `Revenue by State`. Alles läuft gut, bis Sie versuchen, Ihrem Bericht eine `billing state` Gruppierung hinzuzufügen, und Sie Folgendes sehen:

![Diagramm mit unübersichtlichen Zustandssegmenten mit inkonsistenter Benennung](../../assets/Messy_State_Segments.png)

## Wie konnte das passieren?

Unglücklicherweise kann ein Mangel an Standardisierung manchmal zu unübersichtlichen Daten und Kopfschmerzen beim Erstellen von Berichten führen. In diesem Beispiel gab es möglicherweise kein Dropdown-Menü oder keine standardisierte Methode für Ihre Kunden, ihre Rechnungsstatusinformationen einzugeben. Dies führt zu verschiedenen Werten - `pa`, `PA`, `penna`, `pennsylvania` und `Pennsylvania` - alle für denselben Status, was zu einigen seltsamen Ergebnissen im `Report Builder` führt.

Es ist möglich, dass es eine technische Ressource gibt, die Ihnen dabei helfen kann, die Daten zu bereinigen oder die benötigten Spalten direkt in Ihre Datenbank einzufügen. Andernfalls gibt es eine andere Lösung - **die Zuordnungstabelle**. Mit einer Zuordnungstabelle können Sie mühelos und schnell fehlerhafte Daten bereinigen und standardisieren, indem Sie sie einer einzelnen Ausgabe zuordnen.

>[!NOTE]
>
>Eine Zuordnungstabelle für konsolidierte Tabellen kann nicht ohne Hilfe des Adobe-Supportteams erstellt werden.

## Wie erstelle ich sie? {#how}

**Aktualisierung der Datenformatierung:**

* Stellen Sie sicher, dass Ihr Arbeitsblatt eine Kopfzeile enthält.
* Vermeiden Sie Kommas! Es verursacht Probleme beim Hochladen der Datei.
* Verwenden Sie das standardmäßige Datumsformat `(YYYY-MM-DD HH:MM:SS)` Datumsangaben.
* Prozentsätze müssen als Dezimalzahlen eingegeben werden.
* Stellen Sie sicher, dass vorangestellte oder nachfolgende Nullen korrekt beibehalten werden.

Bevor Sie eintauchen, empfiehlt Adobe [Exportieren der Rohtabellendaten](../../tutorials/export-raw-data.md). Wenn Sie die Rohdaten zuerst betrachten, können Sie alle möglichen Kombinationen für die Daten untersuchen, die Sie bereinigen müssen, und so sicherstellen, dass die Zuordnungstabelle alles abdeckt.

Um eine Zuordnungstabelle zu erstellen, müssen Sie eine zweispaltige Tabelle erstellen, die den [Formatierungsregeln für Datei-Uploads](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) folgt.

Geben Sie in der ersten Spalte die in Ihrer Datenbank gespeicherten Werte ein (**einen Wert in jeder Zeile**. Beispielsweise dürfen sich `pa` und `PA` nicht in derselben Zeile befinden - jede Eingabe muss eine eigene Zeile haben. Ein Beispiel finden Sie unten.

Geben Sie in der zweiten Spalte an, wie **Werte lauten**. Wenn Sie wie beim Beispiel für den Fakturastatus `pa`, `PA`, `Pennsylvania` und `pennsylvania` einfach `PA` möchten, geben Sie `PA` in dieser Spalte für jeden Eingabewert ein.

![Beispielzuordnungstabelle mit Originalwerten und standardisierten Werten](../../assets/Mapping_table_examples.jpg)

## Was muss ich tun, [!DNL Commerce Intelligence] es zu verwenden? {#use}

Nachdem Sie die Zuordnungstabelle fertig erstellt haben, müssen Sie [die Datei hochladen](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) in [!DNL Commerce Intelligence] und [eine verbundene Spalte erstellen](../../data-analyst/data-warehouse-mgr/calc-column-types.md) die das neue Feld in die gewünschte Tabelle verschiebt. Sie können dies tun, nachdem die Datei mit Ihrer Data Warehouse synchronisiert wurde.

In diesem Beispiel wird die Spalte, die Sie in der `mapping_state` (`state_input`) erstellt haben, mithilfe einer verbundenen Spalte in die `customer_address` Tabelle verschoben. Auf diese Weise können wir in Ihren Berichten nach der Spalte `state_input` bereinigen anstatt nach der Spalte `state` gruppieren.

Um die `joined` Spalte zu erstellen, navigieren Sie zu der Tabelle, in die das Feld im Data Warehouse Manager verschoben wird. In diesem Beispiel wäre dies die `customer_address`.

1. Klicken Sie auf **[!UICONTROL Create a Column]**.
1. Wählen Sie `Joined Column` aus dem Dropdown-Menü `Definition` aus.
1. Geben Sie der Spalte einen Namen, der sie von der `state` Spalte in Ihrer Datenbank unterscheidet. Benennen Sie die Spalte `billing state (mapped)`, damit Sie sehen können, welche Spalte bei der Segmentierung in Report Builder verwendet werden soll.
1. Der Pfad, den Sie zum Verbinden der Tabellen benötigen, existiert nicht. Daher müssen Sie einen erstellen. Klicken Sie in der Dropdown-Liste **[!UICONTROL Create new path]** auf `Select a table and column` .

   Wenn Sie sich nicht sicher sind, was die Tabellenbeziehung ist oder wie Sie die Primär- und Fremdschlüssel richtig definieren, finden Sie im [Tutorial](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md) Hilfe.

   * Wählen Sie auf der `Many` Seite die Tabelle aus, in die Sie das Feld verschieben möchten (auch hier: `customer_address`), und wählen Sie im Beispiel die `Foreign Key` Spalte oder `state` Spalte aus.
   * Wählen Sie auf der `One` Seite die `mapping` und die `Primary key` aus. In diesem Fall würden Sie die `state_input` aus der `mapping_state` auswählen.
   * Im Folgenden sehen Sie, wie der Pfad aussieht:

     ![Data Warehouse Manager zeigt den Berechnungspfad der Statuszuordnung an](../../assets/State_Mapping_Path.png)

1. Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save]** , um den Pfad zu erstellen.
1. Der Pfad wird möglicherweise nicht sofort nach dem Speichern ausgefüllt. Klicken Sie in diesem Fall auf das `Path` und wählen Sie den erstellten Pfad aus.
1. Klicken Sie auf **[!UICONTROL Save]** , um die Spalte zu erstellen.

## Was soll ich jetzt tun? {#wrapup}

Nach Abschluss eines Aktualisierungszyklus können Sie Ihre neue verknüpfte Spalte verwenden, um Ihre Daten ordnungsgemäß zu segmentieren, anstatt die Spalte mit der Meldung aus Ihrer Datenbank. Schauen Sie sich jetzt Ihre Gruppierungsoptionen an - kein Stress mehr:

![Diagramm mit Segmenten mit sauberem Status nach der Standardisierung](../../assets/Clean_State_Segments.png)

Zuordnungstabellen sind immer dann praktisch, wenn Sie einige potenziell fehlerhafte Daten in Ihrer Data Warehouse bereinigen möchten. Zuordnungstabellen können jedoch auch für einige andere coole Anwendungsfälle verwendet werden, z. B. [Replizieren Ihrer  [!DNL Google Analytics channels] in [!DNL Commerce Intelligence]](../data-warehouse-mgr/rep-google-analytics-channels.md).

### verwandt

* [Verstehen und Auswerten von Tabellenbeziehungen](../data-warehouse-mgr/table-relationships.md)
* [Erstellen/Löschen von Pfaden für berechnete Spalten](../data-warehouse-mgr/create-paths-calc-columns.md)
