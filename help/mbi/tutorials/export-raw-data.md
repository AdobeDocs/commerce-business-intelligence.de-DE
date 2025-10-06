---
title: Exportieren von Rohdaten
description: Erfahren Sie, wie Sie Datensätze aus Ihrer  [!DNL Commerce Intelligence] Data Warehouse exportieren, um sich einen genaueren Überblick über die Funktionen Ihres Dashboards zu verschaffen.
exl-id: 26decdaf-2b2c-4ca2-b3d5-0386892662e8
role: Admin, Data Architect, Data Engineer, Leader, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Exportieren von Rohdaten

Mithilfe von Rohdatenexporten können Sie Datensätze aus Ihrer Data Warehouse exportieren, um einen genaueren Überblick über die Funktionen Ihres Dashboards zu erhalten. Darüber hinaus können Rohdatenexporte Ihnen dabei helfen, [Datendiskrepanzen zu identifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html?lang=de).

Rohdatenexporte bieten Zugriff auf zusätzliche Spalten und Dimensionen, die durch De-Normalisierung und Voraggregation relevanter Metriken generiert wurden. `User's first order date` ist beispielsweise eine Dimension, die Sie für jeden Benutzer in [!DNL Commerce Intelligence] exportieren können, während sie möglicherweise nicht in Ihrer Datenbank verfügbar ist.

Dieses Tutorial behandelt Folgendes:

* [Auswahl der zu exportierenden Daten](#select)
* [Export herunterladen (](#download)
* [Zugriff auf historische Exporte](#historical)

## Schritt 1: Auswahl der zu exportierenden Daten {#select}

Es gibt zwei Möglichkeiten, Rohdaten in [!DNL Commerce Intelligence] zu exportieren:

1. auf Diagrammebene
1. auf Tabellenebene

### Exportieren auf Tabellenebene in der Registerkarte &quot;[!UICONTROL Manage Data]&quot;

Wenn Sie die Tabelle aus [!UICONTROL Manage Data] Registerkarte exportieren möchten, benötigen Sie [Admin](../administrator/user-management/user-management.md)-Berechtigungen.

1. Klicken Sie **[!UICONTROL Manage Data** > **&#x200B; Daten exportieren &#x200B;**> **Rohdatenexport]**.
1. Es wird eine `Export List` der kürzlich erstellten Datenexporte angezeigt, sofern vorhanden. Klicken Sie auf **[!UICONTROL Add Export]** , um einen Export zu erstellen.
1. Das Dialogfeld `New Raw Data Export` wird angezeigt. Hier können Sie Ihren Export anpassen, indem Sie Spalten und Filter auswählen oder die Auswahl aufheben:

   * `Table` : Das Feld `Table` wählt die Tabelle aus, aus der Daten exportiert werden. Standardmäßig wird die Tabelle angezeigt, in die Sie navigiert sind.
   * `Export Name` : Geben Sie in diesem Feld den Namen des Exports ein. Beispiel: `Philadelphia - Daily Revenue`.
   * `Available Columns` : In diesem Feld werden die Spalten (Dimensionen) in der Datenbank aufgelistet, die für die Aufnahme in den Export verfügbar sind. Um eine Spalte hinzuzufügen, klicken Sie auf ihren Namen.
   * `Selected Columns` : In diesem Feld werden die Spalten (Dimensionen) aufgelistet, die derzeit im Export enthalten sind. Um eine Spalte zu entfernen, klicken Sie auf ihren Namen.
   * `Filter` - In diesem Abschnitt werden die derzeit auf den Export angewendeten Filter aufgelistet. Diese Filter können geändert werden. Neue Filter können auch hinzugefügt werden, um einen bestimmten Datensatz zu exportieren.
   * Klicken Sie abschließend auf **[!UICONTROL Export Data]**.

### Exportieren auf Diagrammebene über das Dashboard

1. Klicken Sie auf das Zahnradsymbol in der oberen rechten Ecke eines beliebigen Diagramms.

1. Wählen Sie `Raw Export` aus dem Dropdown-Menü aus, um das Dialogfeld `Raw Export` anzuzeigen.

1. Passen Sie den Export an, indem Sie die `table`, `columns` und `filters` auswählen, die ein- oder ausgeschlossen werden sollen. Siehe vorherigen Abschnitt für detailliertere Informationen zu den Feldern in diesem Modul.

   >[!NOTE]
   >
   >Die Tabelle, die im Feld `Table` angezeigt wird, ist standardmäßig die Tabelle, die das Diagramm antreibt.

1. Klicken Sie abschließend auf **[!UICONTROL Export Data]**.

Betrachten Sie den gesamten Prozess auf der Diagrammebene.

![Animierte Demonstration des Exports von Rohdaten aus einem Diagramm](../assets/Chart-level_export.gif)

## Schritt 2: Export herunterladen {#download}

Der Export wird sofort nach Abschluss der Auswahl im Dialogfeld &quot;`Raw Data Export`&quot; verarbeitet. Da einige Exporte sehr groß sein können, sind sie auf 10 Millionen Zeilen beschränkt und können einige Zeit in Anspruch nehmen.

Um zu überprüfen, ob Ihr Export bereit ist, klicken Sie in der oberen rechten Ecke des Bildschirms auf **[!UICONTROL Raw Data Exports]** . Klicken Sie auf **[!UICONTROL Download]** , um eine komprimierte `.csv`-Datei Ihres Exports herunterzuladen.

![Animierte Demonstration zum Herunterladen einer exportierten CSV-Datei](../assets/Downloading_export.gif)

## Schritt 3: Zugriff auf historische Exporte {#historical}

Um Ihre vergangenen Exporte anzuzeigen, klicken Sie in der oberen rechten Ecke des Bildschirms auf **[!UICONTROL Raw Data Export]** . Ausstehende und abgeschlossene Berichte können bis zu sieben Tage lang aufgerufen werden.
