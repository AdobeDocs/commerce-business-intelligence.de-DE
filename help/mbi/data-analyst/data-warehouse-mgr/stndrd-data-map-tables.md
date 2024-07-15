---
title: Daten mit Zuordnungstabellen standardisieren
description: Erfahren Sie, wie Sie mit Zuordnungstabellen arbeiten.
exl-id: e452ff87-f298-43d5-acc3-af58e53bd0bc
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Daten mit Zuordnungstabellen standardisieren

Stellen Sie sich vor, Sie befinden sich im `Report Builder` Erstellen eines `Revenue by State` Berichts. Alles läuft gut, bis Sie versuchen, Ihrem Bericht eine `billing state` -Gruppierung hinzuzufügen. Sie sehen dies:

![](../../assets/Messy_State_Segments.png)

## Wie konnte das passieren?

Leider kann ein Mangel an Standardisierung manchmal zu undurchsichtigen Daten und Kopfschmerzen bei der Erstellung von Berichten führen. In diesem Beispiel gab es für Ihre Kunden möglicherweise kein Dropdown-Menü oder keine standardisierte Möglichkeit, ihre Rechnungsstatusinformationen einzugeben. Dies führt zu verschiedenen Werten - `pa`, `PA`, `penna`, `pennsylvania` und `Pennsylvania` - für denselben Status, was zu einigen seltsamen Ergebnissen in den `Report Builder` führt.

Es ist möglich, dass es eine technische Ressource gibt, mit der Sie die Daten bereinigen oder die benötigten Spalten direkt in Ihre Datenbank einfügen können. Wenn nicht, gibt es eine andere Lösung - **die Zuordnungstabelle**. Mit einer Zuordnungstabelle können Sie schnell und einfach alle chaotischen Daten bereinigen und standardisieren, indem Sie Daten einer einzigen Ausgabe zuordnen.

>[!NOTE]
>
>Sie können keine Zuordnungstabelle für konsolidierte Tabellen erstellen, ohne Hilfe des Adobe-Supportteams zu erhalten.

## Wie erstelle ich es? {#how}

**Neuerung der Datenformatierung:**

* Stellen Sie sicher, dass das Arbeitsblatt über eine Kopfzeile verfügt.
* Vermeiden Sie die Verwendung von Kommas! Dies verursacht Probleme beim Hochladen der Datei.
* Verwenden Sie für Datumsangaben das standardmäßige Datumsformat &quot;`(YYYY-MM-DD HH:MM:SS)`&quot;.
* Prozentangaben müssen als Dezimalstellen angegeben werden.
* Stellen Sie sicher, dass alle führenden oder nachfolgenden Nullen korrekt beibehalten werden.

Bevor Sie eintauchen, empfiehlt Adobe, die rohen Tabellendaten ](../../tutorials/export-raw-data.md) zu exportieren. [ Wenn Sie sich die Rohdaten zuerst ansehen, können Sie alle möglichen Kombinationen für die Daten untersuchen, die Sie bereinigen müssen, und so sicherstellen, dass die Zuordnungstabelle alles abdeckt.

Um eine Zuordnungstabelle zu erstellen, müssen Sie eine zweispaltige Tabelle erstellen, die den [Formatierungsregeln für Datei-Uploads](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) folgt.

Geben Sie in der ersten Spalte die in Ihrer Datenbank gespeicherten Werte mit **nur einem Wert in jeder Zeile** ein. Beispielsweise können sich `pa` und `PA` nicht in derselben Zeile befinden - jede Eingabe muss über eine eigene Zeile verfügen. Ein Beispiel finden Sie unten.

Geben Sie in der zweiten Spalte ein, was diese Werte **sein sollen**. Wenn Sie möchten, dass `pa`, `PA`, `Pennsylvania` und `pennsylvania` einfach `PA` sind, geben Sie in dieser Spalte für jeden Eingabewert `PA` ein.

![](../../assets/Mapping_table_examples.jpg)

## Was muss ich in [!DNL Commerce Intelligence] tun, um es zu verwenden? {#use}

Nachdem Sie die Erstellung der Zuordnungstabelle abgeschlossen haben, müssen Sie die Datei ](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) in [!DNL Commerce Intelligence] hochladen und [ eine zusammengeführte Spalte erstellen](../../data-analyst/data-warehouse-mgr/calc-column-types.md), die das neue Feld in die gewünschte Tabelle verschiebt. [ Sie können dies tun, nachdem die Datei mit Ihrer Data Warehouse synchronisiert wurde.

In diesem Beispiel wird die Spalte, die Sie für die Tabelle `mapping_state` (`state_input`) erstellt haben, mithilfe einer zusammengeführten Spalte in die Tabelle `customer_address` verschoben. Auf diese Weise können wir in Ihren Berichten nach der sauberen Spalte `state_input` statt nach der Spalte `state` gruppieren.

Um die Spalte `joined` zu erstellen, navigieren Sie zur Tabelle, in die das Feld im Data Warehouse-Manager verschoben wird. In diesem Beispiel wäre dies die Tabelle `customer_address`.

1. Klicken Sie auf **[!UICONTROL Create a Column]**.
1. Wählen Sie `Joined Column` aus dem Dropdown-Menü `Definition` aus.
1. Geben Sie der Spalte einen Namen, der sie von der Spalte `state` in Ihrer Datenbank unterscheidet. Benennen Sie die Spalte mit &quot;`billing state (mapped)`&quot;, damit Sie feststellen können, welche Spalte bei der Segmentierung in ReportBuilder verwendet werden soll.
1. Der Pfad, den Sie zum Verbinden der Tabellen benötigen, ist nicht vorhanden. Daher müssen Sie eine erstellen. Klicken Sie im Dropdown-Menü `Select a table and column` auf **[!UICONTROL Create new path]** .

   Wenn Sie sich nicht sicher sind, was die Tabellenbeziehung ist oder wie die primären und Fremdschlüssel richtig definiert werden, finden Sie in [dem Tutorial](../../data-analyst/data-warehouse-mgr/create-paths-calc-columns.md) einige Hilfe.

   * Wählen Sie auf der Seite &quot;`Many`&quot;die Tabelle aus, in die das Feld umgeleitet wird (für uns ist dies wiederum &quot;`customer_address`&quot;), und im Beispiel die Spalte &quot;`Foreign Key`&quot; oder &quot;`state`&quot;.
   * Wählen Sie auf der Seite `One` die Tabelle `mapping` und die Spalte `Primary key` aus. In diesem Fall wählen Sie die Spalte `state_input` aus der Tabelle `mapping_state` aus.
   * Hier sehen Sie, wie der Pfad aussieht:

     ![](../../assets/State_Mapping_Path.png)

1. Klicken Sie abschließend auf **[!UICONTROL Save]** , um den Pfad zu erstellen.
1. Der Pfad wird möglicherweise nicht sofort nach dem Speichern ausgefüllt. Klicken Sie in diesem Fall auf das Feld `Path` und wählen Sie den erstellten Pfad aus.
1. Klicken Sie auf **[!UICONTROL Save]** , um die Spalte zu erstellen.

## Was mache ich jetzt? {#wrapup}

Nach Abschluss eines Aktualisierungszyklus können Sie Ihre neue zugeordnete Spalte verwenden, um Ihre Daten ordnungsgemäß zu segmentieren, anstatt die unrichtige Spalte aus Ihrer Datenbank zu verwenden. Sehen Sie sich Ihre Gruppierungsoptionen jetzt an - kein Stressversagen mehr:

![](../../assets/Clean_State_Segments.png)

Zuordnungstabellen sind jederzeit praktisch, wenn Sie einige potenziell unsaubere Daten in Ihrer Data Warehouse bereinigen möchten. Zuordnungstabellen können jedoch auch für einige andere coole Anwendungsfälle verwendet werden, z. B. [Replizieren Ihrer [!DNL Google Analytics channels] in [!DNL Commerce Intelligence]](../data-warehouse-mgr/rep-google-analytics-channels.md).

### Verwandte

* [Grundlegendes zu und Auswerten von Tabellenbeziehungen](../data-warehouse-mgr/table-relationships.md)
* [Pfade für berechnete Spalten erstellen/löschen](../data-warehouse-mgr/create-paths-calc-columns.md)
