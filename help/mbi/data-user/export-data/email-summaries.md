---
title: Erstellen automatisierter E-Mail-Zusammenfassungen
description: Erfahren Sie, wie Sie automatisierte E-Mail-Zusammenfassungen erstellen.
exl-id: a9aea4fc-9193-467f-8554-3ad77ac3fa73
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Erstellen automatisierter E-Mail-Zusammenfassungen

E-Mail-Zusammenfassungen sind ein leistungsstarkes Kommunikationswerkzeug, mit dem Sie den Status und die Trends Ihres Unternehmens mit wichtigen Interessengruppen teilen können. Mit E-Mail-Zusammenfassungen können Sie:

* Grafische E-Mail-Zusammenfassungen mit Berichten
* E-Mail-Zusammenfassungsautor vom Empfang der E-Mail einschließen oder ausschließen
* Versandzeitpunkt der E-Mail planen
* Vorhandene geplante E-Mail-Zusammenfassungen bearbeiten, löschen und anhalten

## Neue E-Mail-Zusammenfassung erstellen

1. Klicken Sie auf **[!DNL Manage Data]** und dann auf **[!UICONTROL Email Summary]** in der Seitenleiste.

   Wenn Sie zum ersten Mal eine E-Mail-Zusammenfassung erstellen, werden auf dieser Seite keine gespeicherten Zusammenfassungen angezeigt.

1. Klicken Sie oben rechts auf **[!UICONTROL Create New Email Summary]** .

1. Geben Sie einen Namen für die Zusammenfassung ein.

   Wählen Sie einen Namen aus, der die in der Zusammenfassung enthaltenen Elemente wiedergibt. Beispiel: `AOV Comparison`.

1. Wählen Sie im Abschnitt `Choose Content` die Berichte aus, die Sie in die Zusammenfassung aufnehmen möchten.

   Sie können bis zu zehn Berichte auswählen, deren Inhaber Sie sind. Nachdem Sie einen Bericht ausgewählt haben, verwenden Sie die angezeigten Symbole, um auszuwählen, ob der Bericht als Tabelle oder Diagramm gesendet werden soll. Wenn Sie den Bericht als Zahl gespeichert haben, können Sie ihn nur als Zahl senden. Informationen zum Senden einer E-Mail-Zusammenfassung mit einem Bericht mit veralteten Daten finden Sie unter [Verwalten Ihrer Kontoeinstellungen](../../administrator/account-management/managing-account-settings.md).

   >[!NOTE]
   >
   >`Cohort` -Berichte sind nur verfügbar, wenn Sie die neue Architektur verwenden.

1. (Optional) Wählen Sie `Send Email To Me` aus, wenn Sie die E-Mail erhalten möchten.

1. Um andere Benutzer in die E-Mail einzuschließen, geben Sie deren E-Mail-Adressen in das Feld `Add Email Recipients` ein, getrennt durch Kommas, Leerzeichen, Tabs oder Semikolons.

## Email-Zusammenfassung planen

Im Feld `Set when to send the Email Summary` können Sie angeben, wann die E-Mail-Zusammenfassungen gesendet werden sollen. Optionen sind:

* `Manual`
* `Once`
* `Repeating`

### E-Mail-Zusammenfassung speichern , um sie zu einem späteren Zeitpunkt zu senden

1. Wählen Sie `Manual` aus dem Feld `Set when to send the Email Summary` aus.

1. Klicken Sie auf **[!UICONTROL Save]**.

   Dadurch wird die Zusammenfassung in der Liste der E-Mail-Zusammenfassungen gespeichert.

1. Wenn Sie bereit sind, die Zusammenfassung zu senden, klicken Sie auf das Zahnradsymbol und wählen Sie `Send Now` aus.

### E-Mail-Zusammenfassung einmal senden

1. Wählen Sie `Once` aus dem Feld `Set when to send the Email Summary` aus.

1. Geben Sie das Startdatum im Kalender `Select Start Date` an.

1. Geben Sie im Feld `Select time to send` die Zeit für den Versand der E-Mail an.

### Wiederholungszeitplan erstellen

1. Wählen Sie `Repeating` aus dem Feld `Set when to send the Email Summary` aus.

1. Wählen Sie im Feld `Set Frequency` die Option `Daily`, `Weekly` oder `Monthly` aus.

1. Geben Sie das Startdatum im Kalender `Select Start Date` an.

1. Geben Sie im Feld `Select time to send` die Zeit für den Versand der E-Mail an.

1. (Optional) Um ein Enddatum anzugeben, wählen Sie &quot;`End Date`&quot;und wählen Sie das Enddatum aus dem Kalender aus.

## Vorhandene E-Mail-Zusammenfassung ändern

Nachdem Sie eine E-Mail-Zusammenfassung erstellt und gespeichert haben, zeigt die Seite `Email Summaries` eine Liste aller gespeicherten Zusammenfassungen an. Sie können die einzelnen Zeilen erweitern (`+`), um weitere Informationen zu erhalten. Die Spalten in dieser Ansicht sind:

* `Email Name` - Name der E-Mail-Zusammenfassung
* `Content` - Inhaltstyp innerhalb der Zusammenfassung, z. B. die Namen von Berichten. Informationen zum Senden einer E-Mail-Zusammenfassung mit einem Bericht mit veralteten Daten finden Sie unter [Verwalten Ihrer Kontoeinstellungen](../../administrator/account-management/managing-account-settings.md).
* `Scheduled` - Häufigkeit, Datum und Uhrzeit der Übermittlung der E-Mail-Zusammenfassung
* `Recipients` - Empfänger der E-Mail-Zusammenfassung
* `Created Date` - Datum der Erstellung der E-Mail-Zusammenfassung
* `Status` - `Paused` oder `Active`

Klicken Sie auf das Zahnradsymbol rechts neben jeder Zeile, um:

* `Send Now` - Sendet die E-Mail-Zusammenfassung sofort an alle angegebenen Empfänger
* `Edit` - Ändert die Details der E-Mail-Zusammenfassung
* `Pause/Active` - Ermöglicht es Ihnen, die Zustellung der E-Mail-Zusammenfassung anzuhalten oder die Zusammenfassung basierend auf ihrer Konfiguration zu aktivieren
* `Delete` - Löscht die E-Mail-Zusammenfassung
