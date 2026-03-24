---
title: Erstellen automatisierter E-Mail-Zusammenfassungen
description: Erfahren Sie, wie Sie automatisierte E-Mail-Zusammenfassungen erstellen.
exl-id: a9aea4fc-9193-467f-8554-3ad77ac3fa73
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/e6PatGqkzOXmxOYhzvDEkNrXCktjz3rIVWkxhleG4mI
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 604
ht-degree: 0%

---

# Erstellen automatisierter E-Mail-Zusammenfassungen

E-Mail-Zusammenfassungen sind ein leistungsstarkes Kommunikationstool, mit dem Sie den Status und die Trends Ihres Unternehmens mit wichtigen Stakeholdern teilen können. E-Mail-Zusammenfassungen bieten folgende Möglichkeiten:

* Grafische E-Mail-Zusammenfassungen mit Berichten
* Einschließen oder Ausschließen des Autors der E-Mail-Zusammenfassung vom Erhalt der E-Mail
* Zeitplan für den Versand der E-Mail
* Bearbeiten, Löschen und Anhalten vorhandener geplanter E-Mail-Zusammenfassungen

## Neue E-Mail-Zusammenfassung erstellen

1. Klicken Sie auf **[!DNL Manage Data]** und dann in der Seitenleiste auf **[!UICONTROL Email Summary]** .

   Wenn Sie zum ersten Mal eine E-Mail-Zusammenfassung erstellen, werden auf dieser Seite keine gespeicherten Zusammenfassungen angezeigt.

1. Klicken Sie oben rechts auf **[!UICONTROL Create New Email Summary]** .

1. Geben Sie einen Namen für die Zusammenfassung ein.

   Wählen Sie einen Namen, der angibt, was in der Zusammenfassung enthalten ist. Beispiel: `AOV Comparison`.

1. Wählen Sie im Abschnitt `Choose Content` die Berichte aus, die Sie in die Zusammenfassung aufnehmen möchten.

   Sie haben zwei Möglichkeiten, Inhalte hinzuzufügen:

   * **Einzelne Berichte auswählen** - Wählen Sie bestimmte Berichte aus Ihren Dashboards aus
   * **Gesamtes Dashboard auswählen** - Alle Berichte aus einem Dashboard so einbeziehen, wie sie im Dashboard-Layout angezeigt werden

   Sie können bis zu zehn Berichte auswählen, deren Inhaber Sie sind. Nachdem Sie einen Bericht ausgewählt haben, verwenden Sie die angezeigten Symbole, um auszuwählen, ob dieser Bericht als Tabelle oder Diagramm gesendet werden soll. Wenn Sie den Bericht als Zahl gespeichert haben, können Sie ihn nur als Zahl senden. Informationen zum Senden einer E-Mail-Zusammenfassung, die einen Bericht mit veralteten Daten enthält, finden Sie unter [Verwalten Ihrer Kontoeinstellungen](../../administrator/account-management/managing-account-settings.md).

   Zum Hinzufügen ganzer Dashboards stehen die folgenden Format- und Löschoptionen zur Verfügung:

   * Ändert das Berichtsformat in ein Diagramm oder eine Tabelle
   * Berichte aus der E-Mail löschen
   * Wählen Sie diese Option, um eine CSV-Datei für tabellarische Berichte einzuschließen, damit die Empfänger direkt in ihrem Posteingang auf rohe, exportierbare Daten zugreifen können.

   >[!NOTE]
   >
   >`Cohort` Berichte sind nur verfügbar, wenn Sie die neue Architektur verwenden.

   >[!NOTE]
   >
   >Große CSV-Anhänge werden bis zu einer Gesamtgröße von 25 MB pro E-Mail unterstützt.

1. (Optional) Wählen Sie `Send Email To Me` aus, wenn Sie die E-Mail erhalten möchten.

1. Wenn Sie andere Benutzer in die E-Mail einbeziehen möchten, geben Sie ihre E-Mail-Adressen in das Feld `Add Email Recipients` ein, getrennt durch Kommas, Leerzeichen, Tabulatoren oder Semikolons.

## E-Mail-Zusammenfassung planen

Im Feld `Set when to send the Email Summary` können Sie angeben, wann die E-Mail-Zusammenfassung gesendet werden soll. Die Optionen sind:

* `Manual`
* `Once`
* `Repeating`

### E-Mail-Zusammenfassung speichern, um sie zu einem späteren Zeitpunkt zu senden

1. Wählen Sie `Manual` aus dem Feld `Set when to send the Email Summary` aus.

1. Klicken Sie auf **[!UICONTROL Save]**.

   Speichert die Zusammenfassung in der Liste der E-Mail-Zusammenfassungen.

1. Wenn Sie bereit sind, die Zusammenfassung zu senden, klicken Sie auf das Zahnradsymbol und wählen Sie `Send Now` aus.

### E-Mail-Zusammenfassung einmal senden

1. Wählen Sie `Once` aus dem Feld `Set when to send the Email Summary` aus.

1. Geben Sie das Startdatum im `Select Start Date` an.

1. Geben Sie im Feld `Select time to send` die Zeit an, zu der die E-Mail gesendet werden soll.

### Wiederholungszeitplan erstellen

1. Wählen Sie `Repeating` aus dem Feld `Set when to send the Email Summary` aus.

1. Wählen Sie im Feld `Set Frequency` die Option `Daily`, `Weekly` oder `Monthly` aus.

1. Geben Sie das Startdatum im `Select Start Date` an.

1. Geben Sie im Feld `Select time to send` die Zeit an, zu der die E-Mail gesendet werden soll.

1. (Optional) Um ein Enddatum anzugeben, wählen Sie `End Date` und dann das Enddatum aus dem Kalender aus.

## Vorhandene E-Mail-Zusammenfassung ändern

Nachdem Sie eine E-Mail-Zusammenfassung erstellt und gespeichert haben, zeigt die `Email Summaries` eine Liste aller gespeicherten Zusammenfassungen an. Sie können (`+`) in jeder Zeile erweitern, um weitere Informationen zu erhalten. Die Spalten in dieser Ansicht sind:

* `Email Name` - Name der E-Mail-Zusammenfassung
* `Content` - Typ des Inhalts in der Zusammenfassung, z. B. die Namen von Berichten
* `Scheduled` - Häufigkeit, Datum und Uhrzeit des Versands der E-Mail-Zusammenfassung
* `Recipients` - Empfänger der E-Mail-Zusammenfassung
* `Created Date` - Datum, an dem die E-Mail-Zusammenfassung erstellt wurde
* `Status` - `Paused` oder `Active`

>[!NOTE]
>
>Informationen zum Senden einer E-Mail-Zusammenfassung, die einen Bericht mit veralteten Daten enthält, finden Sie unter [Verwalten Ihrer Kontoeinstellungen](../../administrator/account-management/managing-account-settings.md).

Klicken Sie auf das Zahnradsymbol rechts neben jeder Zeile, um:

* `Send Now`: Senden der E-Mail-Zusammenfassung sofort an alle angegebenen Empfänger
* `Edit` - Ändern der Details der E-Mail-Zusammenfassung
* `Pause/Active` - Pausieren oder Aktivieren des E-Mail-Übersichtsversands
* `Delete` - E-Mail-Zusammenfassung löschen
