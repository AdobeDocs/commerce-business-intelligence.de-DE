---
title: Datei-Uploader verwenden
description: Erfahren Sie, wie Sie alle Ihre Daten in eine Data Warehouse einfügen können.
exl-id: 28db0e78-0222-431d-bbb9-6ef133686603
source-git-commit: 8de036e2717aedef95a8bb908898fd9b9bc9c3fa
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 0%

---

# Datei-Uploader verwenden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

[!DNL MBI] ist nicht nur wegen seiner Visualisierungsfunktionen leistungsstark, sondern auch weil Sie damit alle Ihre Daten in eine Data Warehouse setzen können. Auch Daten, die außerhalb Ihrer Datenbanken und Integrationen liegen, können in [!DNL MBI] mithilfe des Tools &quot;Datei-Upload&quot;im Data Warehouse Manager.

Verwenden Sie Werbekampagnen als Beispiel. Wenn Sie sowohl Online- als auch Offline-Kampagnen ausführen, können Sie das gesamte Bild nicht abrufen, wenn Sie nur Daten aus einer Online-Integration analysieren. Durch das Hochladen einer Tabelle mit den Offline-Kampagnendaten können Sie beide Datensätze analysieren und ein tieferes Verständnis Ihrer Kampagnenleistung erhalten.

## Einschränkungen und Anforderungen {#require}

1. **Das einzige unterstützte Format für Datei-Uploads ist `CSV` oder`comma separated values`**. Wenn Sie in Excel arbeiten, können Sie die Datei mit der Funktion Speichern unter in `.csv` Format.
1. **`CSV`-Dateien müssen`UTF-8 encoding`**. Meistens ist dies kein Problem. Wenn dieser Fehler beim Hochladen einer Datei auftritt, [Artikel zum Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/resolving-utf-8-errors-for-csv-file-uploads.html?lang=en).
1. **Dateien dürfen nicht größer als 100 MB sein.**. Wenn die Datei größer ist, trennen Sie die Tabelle in Blöcke und speichern Sie sie als einzelne Dateien. Sie können die Daten anhängen, nachdem die erste Datei geladen wurde.
1. **Alle Tabellen müssen über eine`primary key`**. Ihre Tabelle muss mindestens eine Spalte enthalten, die als `primary key`oder eine eindeutige Kennung für jede Zeile in der Tabelle. Jede Spalte, die als `primary key` can *never* null sein. A `primary key` kann so einfach sein, wie das Hinzufügen einer Spalte, die jeder Zeile eine Zahl gibt, oder zwei miteinander verkettete Spalten, um eine Spalte mit eindeutigen Werten zu bilden (z. B. `campaign name` und `date`).

   Wenn eine Spalte (oder Spalten) als eindeutig gekennzeichnet ist, es jedoch Duplikate gibt, werden die Duplikate nicht importiert.

## Formatieren von Daten für den Upload {#formatting}

Vor dem Hochladen Ihrer Daten in [!DNL MBI], überprüfen Sie, ob die Formatierung den Richtlinien in diesem Abschnitt entspricht.

### Kopfzeile {#header}

Um sicherzustellen, dass Spalten ordnungsgemäß gekennzeichnet und importiert werden, stellen Sie sicher, dass die erste Zeile des Arbeitsblatts eine Kopfzeile ist, die die Daten in den einzelnen Spalten beschreibt.

Spaltennamen müssen eindeutig sein und dürfen nur Buchstaben, Zahlen, Leerzeichen und die folgenden Symbole enthalten: `$ % # /`. Wenn ein Spaltenname ein Komma enthält, wird er beim Hochladen der Datei in zwei Spalten aufgeteilt. Außerdem empfiehlt Adobe, dass die Datei weniger als 85 Spalten enthält, um die Aktualisierungsgeschwindigkeit zu optimieren.

### Daten mit Kommas {#commas}

Da Dateien in `CSV` -Format verwenden, kann die Verwendung von Kommas zu Problemen beim Hochladen von Daten führen. `CSV` -Dateien verwenden Kommas, um neue Werte anzugeben. Daher ist eine Spalte mit einem Namen wie `Campaigns`, `August` wird als zwei Spalten gelesen (`Campaigns` und `August`) anstatt einer Zeile, verschieben Sie alle Ihre Daten über eine Zeile. Adobe empfiehlt, Kommas soweit möglich zu vermeiden. Sie können `Data Preview` , um zu sehen, ob Ihre Daten nach Abschluss der Aktualisierung korrekt angezeigt werden.

### Datum

Jeder Datensatz, der Datumsangaben enthält, muss die Variable [Standarddatumsformat](https://dev.mysql.com/doc/refman/5.7/en/datetime.html) `YYYY-MM-DD HH:MM:SS` oder `MM/DD/YYYY`.

### Sonderzeichen

Einige Sonderzeichen werden nicht akzeptiert. Beispiel: das Symbol für das Rohr `& # 1 2 4` wird als Spaltenerstellung interpretiert und verursacht beim Hochladen einer Datei Fehler.

### Dezimalzahlen

Währungswerte sollten den Datentyp aufweisen `Decimal Number` ausgewählt ist und diese Spalten automatisch auf zwei Dezimalstellen in Ihrer Data Warehouse gerundet werden. Wenn Sie Ihre Dezimalzahlen nicht runden möchten oder einen höheren Genauigkeitsgrad haben möchten, sollten Sie die `Non-Currency Decimal Number` Datentyp.

### Prozentsatz

Prozentangaben müssen als Dezimalstellen angegeben werden. Beispiel:

| **Rechts:** | **Falsch:** |
|-----|-----|
| `.05` | `5%` |
| `.23` | `23` |

{style="table-layout:auto"}

### Werte mit führenden und/oder nachfolgenden Nullen {#zeroes}

Einige Werte in Ihrer Datei - wie Postleitzahlen und IDs - können mit Nullen beginnen oder enden. Um sicherzustellen, dass die Nullen korrekt beibehalten und hochgeladen werden, können Sie den Formatierungstyp ändern (z. B. [von Zahl zu Text](https://support.microsoft.com/en-us/office/format-numbers-as-text-583160db-936b-4e52-bdff-6f1863518ba4?ui=en-us&amp;rs=en-us&amp;ad=us)) oder die Zahlenformatierung erzwingen.

Verwendung `US ZIP codes` als Beispiel für die Änderung der Zahlenformatierung. In [!DNL Excel]markieren, markieren Sie die Spalte, die `ZIP codes` und [Zahlenformat ändern](https://support.microsoft.com/en-us/office/display-numbers-as-postal-codes-61b55c9f-6fe3-4e54-96ca-9e85c38a5a1d?ui=en-us&amp;rs=en-us&amp;ad=us) nach `ZIP code`. Sie können auch ein benutzerdefiniertes Zahlenformat auswählen und im `Type` Fenster, eingeben `00000`. Beachten Sie, dass diese Methode Probleme verursachen kann, wenn einige Codes als `00000` und andere `00000-0000`.

Die `Type` kann [anders formatiert, um andere Datentypen aufzunehmen](https://support.microsoft.com/en-us/office/keeping-leading-zeros-and-large-numbers-1bf7b935-36e1-4985-842f-5dfa51f85fe7?correlationid=e1d4c2d3-cd5d-4a14-999d-437800274a90&amp;ui=en-us&amp;rs=en-us&amp;ad=us), wie IDs. Wenn eine `ID` ist neun Stellen lang, zum Beispiel die `Type` könnte `000000000` oder `000-000-000`. Dies würde sich ändern `123456` nach `000-123-456`.

Für [!DNL Google Docs] und [!DNL Apple Numbers] Ressourcen, siehe [Verwandte](#related) Liste unten auf dieser Seite.

## Hochladen von Daten {#uploading}

Jetzt, da Ihr Arbeitsblatt korrekt formatiert ist und [!DNL MBI]-friendly, fügen Sie es zu Ihrer Data Warehouse hinzu.

1. Gehen Sie zu **[!UICONTROL Data** > **File Uploads]**.

1. Klicken Sie auf **[!UICONTROL Upload to New Table]** Registerkarte.

1. Klicken **[!UICONTROL Choose File]** und wählen Sie die Datei aus. Klicken **[!UICONTROL Open]** , um den Upload zu starten.

   Nach Abschluss des Uploads eine Liste der Spalten [!DNL MBI] angezeigt.

1. Überprüfen Sie, ob die Spaltennamen und Datentypen korrekt sind. Prüfen Sie insbesondere, ob Datumsspalten als Datumsangaben und nicht als Zahlen gelesen werden.

   >[!NOTE]
   >
   >Die `datatype` ist wichtig, also überspringen Sie diesen Schritt nicht!

1. Wählen Sie die Spalte (oder Spalten) aus, aus der die `primary key` für die Tabelle verwenden, indem Sie die Kontrollkästchen unter dem Schlüsselsymbol aktivieren.

1. Nennen Sie die Tabelle.

1. Klicken **[!UICONTROL Save Table]**.

A *Erfolg!* wird oben im Bildschirm angezeigt, nachdem die Tabelle gespeichert wurde.

Wenn Sie eine Visualisierung benötigen, sehen Sie sich den gesamten Prozess an:

![](../../../assets/fileupload.gif)

Hochgeladene Tabellen werden unter der **Datei-Uploads** -Abschnitt der Tabellenliste (in den Optionen &quot;Alle Tabellen&quot;und &quot;Synchronisierte Tabellen&quot;) im Data Warehousen-Manager:

![](../../../assets/upload-tables.png)

## Aktualisieren oder Anhängen von Daten an eine vorhandene Tabelle {#appending}

Haben Sie neue Daten, die Sie zu einer bereits hochgeladenen Datei hinzufügen können? Kein Problem - Sie können Daten einfach aktualisieren und anhängen in [!DNL MBI].

1. Gehen Sie zu **[!UICONTROL Manage Data** > **File Uploads]**.

1. Klicken Sie auf **[!UICONTROL Edit/Upload `.csv`in bestehende Tabellen]** Registerkarte.

1. Klicken Sie im Dropdown-Menü auf den Namen der Tabelle, die Sie aktualisieren oder anhängen möchten.

1. Wählen Sie in der Dropdown-Liste die Option zum Umgang mit doppelten Zeilen aus:

   |  |  |
   |---|---|
   | `Overwrite old row with new row` | Dadurch werden vorhandene Daten durch neue Daten überschrieben, wenn eine Zeile sowohl in der vorhandenen Tabelle als auch in der neuen Datei denselben Primärschlüssel enthält. Dies ist die Methode, die für Spalten mit Werten verwendet wird, die sich im Laufe der Zeit ändern - z. B. eine Statusspalte. Vorhandene Daten werden überschrieben und mit den neuen Daten aktualisiert. Zeilen mit Primärschlüsseln, die nicht in der vorhandenen Tabelle enthalten sind, werden als neue Zeilen hinzugefügt. |
   | `Retain old row; discard new row` | Dadurch werden neue Daten ignoriert, wenn eine Zeile sowohl in der vorhandenen Tabelle als auch in der neuen Datei denselben Primärschlüssel enthält. |
   | `Purge all existing rows first and ignore duplicate keys within the file` | Dadurch werden alle vorhandenen Daten gelöscht und durch die neuen Daten aus der Datei ersetzt. Verwenden Sie diese Option nur, wenn Sie keine der Daten in der vorhandenen Tabelle benötigen. |

1. Klicken **[!UICONTROL Choose File]** und wählen Sie die Datei aus.

1. Klicken **[!UICONTROL Open]** , um den Upload zu starten.

   Nach Abschluss des Uploads [!DNL MBI] validiert die Datenstruktur in der Datei. A *Erfolg!* wird oben im Bildschirm angezeigt, nachdem die Tabelle gespeichert wurde.

## Datenverfügbarkeit {#availability}

Wie berechnete Spalten sind auch Daten aus Datei-Uploads nach Abschluss des nächsten Aktualisierungszyklus verfügbar. Wenn während des Datei-Uploads eine Aktualisierung durchgeführt wurde, stehen die Daten erst nach der nächsten Aktualisierung zur Verfügung. Sobald ein Aktualisierungszyklus abgeschlossen ist, können Sie zum `Data Preview` in Ihrer Data Warehouse, um sicherzustellen, dass die hochgeladene Datei und die Daten erwartungsgemäß angezeigt werden.

## Aufbrechen {#wrapup}

In diesem Artikel wurden nur die Grundlagen für die Verwendung des Datenimports behandelt. Möglicherweise möchten Sie jedoch etwas erweitertes tun. In den entsprechenden Artikeln finden Sie Anleitungen zum Formatieren und Importieren von Finanzdaten, E-Commerce, Werbeausgaben und anderen Datentypen.

Außerdem ist der Datei-Upload nicht die einzige Möglichkeit, Ihre Daten in [!DNL MBI]. Die [Datenimport-API](https://developer.adobe.com/commerce/services/reporting/import-api/) -Funktionen ermöglichen es Ihnen, beliebige Daten in Ihre [!DNL MBI] Data Warehouse.

## Verwandte {#related}

* [Finanzdaten formatieren und importieren](../../../best-practices/format-import-financial-data.md)
* [Importieren von Offline-/anderen Anzeigenausgabedaten](../connecting-data/import-offline-ad-data.md)
* [Erwartet[!DNL Google ECommerce] data](../integrations/google-ecommerce-data.md)

## Drittanbieterressourcen

* [Numbers Data Formatting Guide](http://www.dummies.com/how-to/content/how-to-choose-a-number-format-in-your-numbers-spre.html)
* [[!DNL Google Docs] Anleitung zur Datenformatierung](https://support.google.com/docs/answer/56470?hl=en)
