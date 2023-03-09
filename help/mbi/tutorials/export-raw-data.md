---
title: Rohdaten exportieren
description: Erfahren Sie, wie Sie Datensätze aus Ihren [!DNL MBI] Data Warehouse für einen genaueren Einblick in die Funktionen Ihres Dashboards.
exl-id: 26decdaf-2b2c-4ca2-b3d5-0386892662e8
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Rohdaten exportieren

Mithilfe von Rohdatenexporten können Sie Datensätze aus Ihren [!DNL MBI] Data Warehouse für einen genaueren Einblick in die Funktionen Ihres Dashboards. Außerdem können Ihnen Rohdatenexporte helfen [Datendiskrepanzen bestimmen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html?lang=en).

Beim Export von Rohdaten erhalten Sie Zugriff auf zusätzliche Spalten und Dimensionen, die durch die Aufhebung der Normalisierung und Voraggregation relevanter Metriken generiert werden. Beispiel: `User's first order date` ist eine Dimension, die Sie für jeden Benutzer in [!DNL MBI], während sie möglicherweise nicht in Ihrer Datenbank verfügbar ist.

Dieses Tutorial behandelt Folgendes:

* [Zu exportierende Daten auswählen](#select)
* [Herunterladen des Exports (](#download)
* [Zugriff auf historische Exporte](#historical)

## Schritt 1: Zu exportierende Daten auswählen {#select}

Es gibt zwei Möglichkeiten, Rohdaten in zu exportieren [!DNL MBI]: auf Diagrammebene oder auf Tabellenebene.

### Exportieren auf Tabellenebene in `Manage Data` Registerkarte

Wenn Sie die Tabelle aus `Manage Data` Registerkarte [Admin](../administrator/user-management/user-management.md) Berechtigungen.

1. Klicken **[!UICONTROL Manage Data** > ** Daten exportieren **> **Rohdatenexport]** um zu beginnen.
1. Sie sehen eine `Export List` der kürzlich erstellten Datenexporte, sofern vorhanden. Klicken **[!UICONTROL Add Export]** , um einen Export zu erstellen.
1. Die `New Raw Data Export` angezeigt. Hier können Sie Ihren Export anpassen, indem Sie Spalten und Filter auswählen oder deaktivieren:

   * `Table` - die `Table` wählt die Tabelle aus, aus der Daten exportiert werden. Standardmäßig wird dadurch die Tabelle angezeigt, in die Sie navigiert sind.
   * `Export Name` - Geben Sie in diesem Feld den Namen des Exports ein. Beispiel: `Philadelphia - Daily Revenue`.
   * `Available Columns` - Dieses Feld listet die Spalten (Dimensionen) Ihrer Datenbank auf, die für den Export verfügbar sind. Um eine Spalte hinzuzufügen, klicken Sie auf ihren Namen.
   * `Selected Columns` - In diesem Feld werden die Spalten (Dimensionen) aufgelistet, die derzeit im Export enthalten sind. Um eine Spalte zu entfernen, klicken Sie auf ihren Namen.
   * `Filter` - In diesem Abschnitt werden die derzeit für den Export angewendeten Filter aufgelistet. Diese Filter können geändert werden. Es können auch neue Filter hinzugefügt werden, um einen bestimmten Datensatz zu exportieren.
   * Klicken Sie abschließend auf **[!UICONTROL Export Data]**.

### Exportieren auf Diagrammebene über das Dashboard

1. Klicken Sie auf das Zahnradsymbol in der oberen rechten Ecke eines beliebigen Diagramms.
1. Auswählen `Raw Export` aus dem Dropdown-Menü, um die `Raw Export` angezeigt.
1. Anpassen des Exports durch Auswahl der `table`, `columns`und `filters` ein- oder auszuschließen. Weitere Informationen zu den Feldern in diesem Modul finden Sie im vorherigen Abschnitt .
   >[!NOTE]
   >
   >Die Tabelle, die im `Table` -Feld ist standardmäßig die Tabelle, die das Diagramm steuert.

1. Klicken Sie abschließend auf **[!UICONTROL Export Data]**.

Betrachten Sie den gesamten Prozess auf Diagrammebene.

![](../assets/Chart-level_export.gif)

## Schritt 2: Herunterladen des Exports {#download}

Der Export beginnt unmittelbar nach Abschluss Ihrer Auswahl im `Raw Data Export` angezeigt. Da einige Exporte groß sein können, sind sie auf 10 Millionen Zeilen beschränkt und können einige Zeit in Anspruch nehmen.

Um zu überprüfen, ob der Export fertig ist, klicken Sie auf **[!UICONTROL Raw Data Exports]** in der oberen rechten Ecke des Bildschirms. Klicken **[!UICONTROL Download]** zum Herunterladen einer komprimierten Datei `.csv` -Datei Ihres Exports.

![](../assets/Downloading_export.gif)

## Schritt 3: Zugriff auf historische Exporte {#historical}

Um Ihre bisherigen Exporte anzuzeigen, klicken Sie auf **[!UICONTROL Raw Data Export]** in der oberen rechten Ecke des Bildschirms. Auf ausstehende und abgeschlossene Berichte kann bis zu sieben Tage zugegriffen werden.

Herzlichen Glückwunsch! Du bist fertig.
