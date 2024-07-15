---
title: Datei-Uploader verwenden
description: Erfahren Sie, wie Sie alle Ihre Daten in eine Data Warehouse einfügen können.
exl-id: 28db0e78-0222-431d-bbb9-6ef133686603
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---

# Datei-Uploader verwenden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

[!DNL Adobe Commerce Intelligence] ist nicht nur wegen seiner Visualisierungsfunktionen leistungsstark, sondern auch weil es Ihnen die Möglichkeit gibt, alle Ihre Daten in eine Data Warehouse zu übertragen. Selbst Daten, die außerhalb Ihrer Datenbanken und Integrationen liegen, können mit dem File Upload-Tool im Data Warehouse-Manager in [!DNL Commerce Intelligence] importiert werden.

Verwenden Sie Werbekampagnen als Beispiel. Wenn Sie sowohl Online- als auch Offline-Kampagnen ausführen, können Sie das gesamte Bild nicht abrufen, wenn Sie nur Daten aus einer Online-Integration analysieren. Durch das Hochladen einer Tabelle mit den Offline-Kampagnendaten können Sie beide Datensätze analysieren und ein tieferes Verständnis Ihrer Kampagnenleistung erhalten.

## Einschränkungen und Anforderungen {#require}

1. **Das einzige unterstützte Format für Datei-Uploads ist `CSV` oder`comma separated values`**. Wenn Sie in Excel arbeiten, können Sie die Datei mit der Funktion Speichern unter im Format `.csv` speichern.
1. **`CSV`-Dateien müssen`UTF-8 encoding`** verwenden. Meistens ist dies kein Problem. Wenn dieser Fehler beim Hochladen einer Datei auftritt, lesen Sie [diesen Support-Artikel](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/resolving-utf-8-errors-for-csv-file-uploads.html).
1. **Dateien dürfen nicht größer als 100 MB** sein. Wenn die Datei größer ist, trennen Sie die Tabelle in Blöcke und speichern Sie sie als einzelne Dateien. Sie können die Daten anhängen, nachdem die erste Datei geladen wurde.
1. **Alle Tabellen müssen einen`primary key`** aufweisen. Ihre Tabelle muss mindestens eine Spalte enthalten, die als `primary key` oder eine eindeutige Kennung für jede Zeile in der Tabelle verwendet werden kann. Jede Spalte, die als `primary key` bezeichnet wird, kann *never* null sein. Ein `primary key` kann so einfach sein wie das Hinzufügen einer Spalte, die jeder Zeile eine Zahl gibt, oder zwei miteinander verkettete Spalten, um eine Spalte mit eindeutigen Werten zu bilden (z. B. `campaign name` und `date`).

   Wenn eine Spalte (oder Spalten) als eindeutig gekennzeichnet ist, es jedoch Duplikate gibt, werden die Duplikate nicht importiert.

## Formatieren von Daten für den Upload {#formatting}

Bevor Sie Ihre Daten in [!DNL Commerce Intelligence] hochladen können, überprüfen Sie, ob sie gemäß den Richtlinien in diesem Abschnitt formatiert sind.

### Kopfzeile {#header}

Um sicherzustellen, dass Spalten ordnungsgemäß gekennzeichnet und importiert werden, stellen Sie sicher, dass die erste Zeile des Arbeitsblatts eine Kopfzeile ist, die die Daten in den einzelnen Spalten beschreibt.

Spaltennamen müssen eindeutig sein und dürfen nur Buchstaben, Zahlen, Leerzeichen und die folgenden Symbole enthalten: `$ % # /`. Wenn ein Spaltenname ein Komma enthält, wird er beim Hochladen der Datei in zwei Spalten aufgeteilt. Außerdem empfiehlt Adobe, dass die Datei weniger als 85 Spalten enthält, um die Aktualisierungsgeschwindigkeit zu optimieren.

### Daten mit Kommas {#commas}

Da Dateien im Format `CSV` vorliegen müssen, kann die Verwendung von Kommas Probleme beim Hochladen von Daten verursachen. `CSV` -Dateien verwenden Kommas, um neue Werte anzugeben. Daher wird eine Spalte mit einem Namen wie `Campaigns`, `August` als zwei Spalten (`Campaigns` und `August`) anstelle einer Spalte gelesen, wodurch alle Daten über eine Zeile verschoben werden. Adobe empfiehlt, Kommas soweit möglich zu vermeiden. Mit `Data Preview` können Sie sehen, ob Ihre Daten nach Abschluss einer Aktualisierung korrekt angezeigt werden.

### Datumsangaben

Jeder Datensatz, der Datumsangaben enthält, muss das Standarddatumsformat ](https://dev.mysql.com/doc/refman/5.7/en/datetime.html) `YYYY-MM-DD HH:MM:SS` oder `MM/DD/YYYY` verwenden.[

### Sonderzeichen

Einige Sonderzeichen werden nicht akzeptiert. Beispielsweise wird das senkrechte Symbol `& # 1 2 4` als Spaltenerstellung interpretiert und verursacht beim Hochladen einer Datei Fehler.

### Dezimalzahlen

Bei Währungswerten sollte der Datentyp `Decimal Number` ausgewählt sein, und diese Spalten runden automatisch auf zwei Dezimalstellen in Ihrer Data Warehouse. Wenn Sie Ihre Dezimalzahlen nicht runden möchten oder einen höheren Genauigkeitsgrad haben möchten, sollten Sie den Datentyp `Non-Currency Decimal Number` auswählen.

### Prozentsatz

Prozentangaben müssen als Dezimalstellen angegeben werden. Beispiel:

| **Right:** | **Falsch:** |
|-----|-----|
| `.05` | `5%` |
| `.23` | `23` |

{style="table-layout:auto"}

### Werte mit führenden und/oder nachfolgenden Nullen {#zeroes}

Einige Werte in Ihrer Datei - wie Postleitzahlen und IDs - können mit Nullen beginnen oder enden. Um sicherzustellen, dass die Nullen korrekt beibehalten und hochgeladen werden, können Sie den Formatierungstyp ändern (z. B. [von Zahl in Text](https://support.microsoft.com/en-us/office/format-numbers-as-text-583160db-936b-4e52-bdff-6f1863518ba4?ui=en-us&amp;rs=en-us&amp;ad=us)) oder die Zahlenformatierung erzwingen.

Verwenden Sie `US ZIP codes` als Beispiel für die Änderung der Zahlenformatierung. Markieren Sie in [!DNL Excel] die Spalte mit `ZIP codes` und [ändern Sie das Zahlenformat](https://support.microsoft.com/en-us/office/display-numbers-as-postal-codes-61b55c9f-6fe3-4e54-96ca-9e85c38a5a1d?ui=en-us&amp;rs=en-us&amp;ad=us) in `ZIP code`. Sie können auch ein benutzerdefiniertes Zahlenformat auswählen und im Fenster `Type` den Wert `00000` eingeben. Beachten Sie, dass diese Methode Probleme verursachen kann, wenn einige Codes als `00000` und andere als `00000-0000` formatiert sind.

Der `Type` kann [ anders formatiert sein, um andere Datentypen aufzunehmen](https://support.microsoft.com/en-us/office/keeping-leading-zeros-and-large-numbers-1bf7b935-36e1-4985-842f-5dfa51f85fe7?correlationid=e1d4c2d3-cd5d-4a14-999d-437800274a90&amp;ui=en-us&amp;rs=en-us&amp;ad=us), z. B. IDs. Wenn ein `ID` beispielsweise neunstellig ist, könnte der `Type` `000000000` oder `000-000-000` sein. Dies würde `123456` in `000-123-456` ändern.

Ressourcen für [!DNL Google Docs] und [!DNL Apple Numbers] finden Sie in der Liste [Related](#related) unten auf dieser Seite.

## Hochladen von Daten {#uploading}

Nachdem das Arbeitsblatt korrekt formatiert und [!DNL Commerce Intelligence]-freundlich ist, fügen Sie es zu Ihrer Data Warehouse hinzu.

1. Gehen Sie zu **[!UICONTROL Data** > **File Uploads]**, um zu beginnen.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Upload to New Table]** .

1. Klicken Sie auf **[!UICONTROL Choose File]** und wählen Sie die Datei aus. Klicken Sie auf **[!UICONTROL Open]** , um den Upload zu starten.

   Nach Abschluss des Uploads wird eine Liste der Spalten [!DNL Commerce Intelligence] in Ihrer Datei angezeigt.

1. Überprüfen Sie, ob die Spaltennamen und Datentypen korrekt sind. Prüfen Sie insbesondere, ob Datumsspalten als Datumsangaben und nicht als Zahlen gelesen werden.

   >[!NOTE]
   >
   >Der `datatype` ist wichtig, überspringen Sie also diesen Schritt nicht!

1. Wählen Sie mithilfe der Kontrollkästchen unter dem Schlüsselsymbol die Spalte (oder Spalten) aus, aus der die `primary key` für die Tabelle besteht.

1. Nennen Sie die Tabelle.

1. Klicken Sie auf **[!UICONTROL Save Table]**.

Ein *Erfolg!Die Meldung* wird oben im Bildschirm angezeigt, nachdem die Tabelle gespeichert wurde.

Wenn Sie eine Visualisierung benötigen, sehen Sie sich den gesamten Prozess an:

![](../../../assets/fileupload.gif)

Hochgeladene Tabellen werden im Data Warehouse-Manager im Bereich **Datei-Uploads** der Tabellenliste (sowohl in den Optionen &quot;Alle Tabellen&quot;als auch &quot;Synchronisierte Tabellen&quot;) angezeigt:

![](../../../assets/upload-tables.png)

## Aktualisieren oder Anhängen von Daten an eine vorhandene Tabelle {#appending}

Haben Sie neue Daten, die Sie zu einer bereits hochgeladenen Datei hinzufügen können? Kein Problem - Sie können Daten einfach in [!DNL Commerce Intelligence] aktualisieren und anhängen.

1. Gehen Sie zu **[!UICONTROL Manage Data** > **File Uploads]**, um zu beginnen.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Edit/Upload `.csv`to Existing Tables]** .

1. Klicken Sie im Dropdown-Menü auf den Namen der Tabelle, die Sie aktualisieren oder anhängen möchten.

1. Wählen Sie in der Dropdown-Liste die Option zum Umgang mit doppelten Zeilen aus:

   | Option | Beschreibung |
   |---|---|
   | `Overwrite old row with new row` | Dadurch werden vorhandene Daten durch neue Daten überschrieben, wenn eine Zeile sowohl in der vorhandenen Tabelle als auch in der neuen Datei denselben Primärschlüssel enthält. Dies ist die Methode, die für Spalten mit Werten verwendet wird, die sich im Laufe der Zeit ändern - z. B. eine Statusspalte. Vorhandene Daten werden überschrieben und mit den neuen Daten aktualisiert. Zeilen mit Primärschlüsseln, die nicht in der vorhandenen Tabelle enthalten sind, werden als neue Zeilen hinzugefügt. |
   | `Retain old row; discard new row` | Dadurch werden neue Daten ignoriert, wenn eine Zeile sowohl in der vorhandenen Tabelle als auch in der neuen Datei denselben Primärschlüssel enthält. |
   | `Purge all existing rows first and ignore duplicate keys within the file` | Dadurch werden alle vorhandenen Daten gelöscht und durch die neuen Daten aus der Datei ersetzt. Verwenden Sie diese Option nur, wenn Sie keine der Daten in der vorhandenen Tabelle benötigen. |

1. Klicken Sie auf **[!UICONTROL Choose File]** und wählen Sie die Datei aus.

1. Klicken Sie auf **[!UICONTROL Open]** , um den Upload zu starten.

   Nach Abschluss des Uploads validiert [!DNL Commerce Intelligence] die Datenstruktur in der Datei. Ein *Erfolg!Die Meldung* wird oben im Bildschirm angezeigt, nachdem die Tabelle gespeichert wurde.

## Datenverfügbarkeit {#availability}

Wie berechnete Spalten sind auch Daten aus Datei-Uploads nach Abschluss des nächsten Aktualisierungszyklus verfügbar. Wenn während des Datei-Uploads eine Aktualisierung durchgeführt wurde, stehen die Daten erst nach der nächsten Aktualisierung zur Verfügung. Nach Abschluss eines Aktualisierungszyklus können Sie auf der Data Warehouse zur Registerkarte `Data Preview` navigieren, um sicherzustellen, dass die hochgeladene Datei und die Daten erwartungsgemäß angezeigt werden.

## Aufwischen {#wrapup}

In diesem Thema wurden nur die Grundlagen für die Verwendung des Datenimports behandelt. Möglicherweise möchten Sie jedoch etwas erweiterter vorgehen. In den entsprechenden Artikeln finden Sie Anleitungen zum Formatieren und Importieren von Finanzdaten, E-Commerce, Werbeausgaben und anderen Datentypen.

Außerdem ist der Datei-Upload nicht die einzige Möglichkeit, Ihre Daten in [!DNL Commerce Intelligence] zu übertragen. Mit den Funktionen der [Datenimport-API](https://developer.adobe.com/commerce/services/reporting/import-api/) können Sie beliebige Daten in Ihre [!DNL Commerce Intelligence]-Data Warehouse übertragen.

## Verwandte {#related}

* [Finanzdaten formatieren und importieren](../../../best-practices/format-import-financial-data.md)
* [Importieren von Offline-/anderen Anzeigenausgabedaten](../connecting-data/import-offline-ad-data.md)
* [Erwartete [!DNL Google ECommerce] Daten](../integrations/google-ecommerce-data.md)

## Drittanbieterressourcen

* [Handbuch zur Nummerndatenformatierung](http://www.dummies.com/how-to/content/how-to-choose-a-number-format-in-your-numbers-spre.html)
* [[!DNL Google Docs] Anleitung zur Datenformatierung](https://support.google.com/docs/answer/56470?hl=en)
