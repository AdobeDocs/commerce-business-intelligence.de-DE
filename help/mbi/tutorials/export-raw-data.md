---
title: Rohdaten exportieren
description: Hier erfahren Sie, wie Sie Datensätze von Ihrer [!DNL Commerce Intelligence] Data Warehouse exportieren können, um sich einen genaueren Überblick über die Funktionen Ihres Dashboards zu verschaffen.
exl-id: 26decdaf-2b2c-4ca2-b3d5-0386892662e8
role: Admin, Data Architect, Data Engineer, Leader, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Rohdaten exportieren

Mithilfe von Rohdatenexporten können Sie Datensätze von Ihrer Data Warehouse exportieren, um sich einen genaueren Überblick über die Funktionen Ihres Dashboards zu verschaffen. Außerdem können Sie durch den Export von Rohdaten [Diskrepanzen bei den Daten erkennen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.html).

Beim Export von Rohdaten erhalten Sie Zugriff auf zusätzliche Spalten und Dimensionen, die durch die Aufhebung der Normalisierung und Voraggregation relevanter Metriken generiert werden. Beispielsweise ist `User's first order date` eine Dimension, die Sie für jeden Benutzer in [!DNL Commerce Intelligence] exportieren können, während sie möglicherweise nicht in Ihrer Datenbank verfügbar ist.

Dieses Tutorial behandelt Folgendes:

* [Zu exportierende Daten auswählen](#select)
* [Herunterladen des Exports (](#download)
* [Zugriff auf historische Exporte](#historical)

## Schritt 1: Auswahl der zu exportierenden Daten {#select}

Es gibt zwei Möglichkeiten, Rohdaten in [!DNL Commerce Intelligence] zu exportieren:

1. auf Diagrammebene
1. auf Tabellenebene

### Exportieren auf Tabellenebene in Ihre Registerkarte [!UICONTROL Manage Data]

Wenn Sie die Tabelle über die Registerkarte [!UICONTROL Manage Data] exportieren möchten, benötigen Sie [Admin](../administrator/user-management/user-management.md) -Berechtigungen.

1. Klicken Sie auf **[!UICONTROL Manage Data** > ** Daten exportieren **> **Rohdatenexport]**.
1. Es wird ein `Export List` der kürzlich erstellten Datenexporte angezeigt, sofern vorhanden. Klicken Sie auf **[!UICONTROL Add Export]** , um einen Export zu erstellen.
1. Das Dialogfeld `New Raw Data Export` wird angezeigt. Hier können Sie Ihren Export anpassen, indem Sie Spalten und Filter auswählen oder deaktivieren:

   * `Table` - Das Feld `Table` wählt die Tabelle aus, aus der Daten exportiert werden. Standardmäßig wird dadurch die Tabelle angezeigt, in die Sie navigiert sind.
   * `Export Name` - Geben Sie in dieses Feld den Namen des Exports ein. Beispiel: `Philadelphia - Daily Revenue`.
   * `Available Columns` - Dieses Feld listet die Spalten (Dimensionen) in Ihrer Datenbank auf, die für den Export verfügbar sind. Um eine Spalte hinzuzufügen, klicken Sie auf ihren Namen.
   * `Selected Columns` - Dieses Feld listet die Spalten (Dimensionen) auf, die derzeit im Export enthalten sind. Um eine Spalte zu entfernen, klicken Sie auf ihren Namen.
   * `Filter` - In diesem Abschnitt werden die Filter aufgelistet, die derzeit auf den Export angewendet werden. Diese Filter können geändert werden. Außerdem können neue Filter hinzugefügt werden, um einen bestimmten Datensatz zu exportieren.
   * Klicken Sie abschließend auf **[!UICONTROL Export Data]**.

### Exportieren auf Diagrammebene über das Dashboard

1. Klicken Sie auf das Zahnradsymbol in der oberen rechten Ecke eines beliebigen Diagramms.

1. Wählen Sie `Raw Export` aus der Dropdown-Liste aus, um das Dialogfeld `Raw Export` anzuzeigen.

1. Passen Sie den Export an, indem Sie die Werte `table`, `columns` und `filters` auswählen, die ein- oder ausgeschlossen werden sollen. Weitere Informationen zu den Feldern in diesem Modul finden Sie im vorherigen Abschnitt .

   >[!NOTE]
   >
   >Die Tabelle, die im Feld `Table` angezeigt wird, ist standardmäßig die Tabelle, die das Diagramm steuert.

1. Klicken Sie abschließend auf **[!UICONTROL Export Data]**.

Betrachten Sie den gesamten Prozess auf Diagrammebene.

![](../assets/Chart-level_export.gif)

## Schritt 2: Herunterladen des Exports {#download}

Der Export beginnt unmittelbar nach Abschluss Ihrer Auswahl im Dialogfeld `Raw Data Export` mit der Verarbeitung. Da einige Exporte groß sein können, sind sie auf 10 Millionen Zeilen beschränkt und können einige Zeit in Anspruch nehmen.

Um zu überprüfen, ob der Export fertig ist, klicken Sie oben rechts im Bildschirm auf **[!UICONTROL Raw Data Exports]** . Klicken Sie auf **[!UICONTROL Download]** , um eine komprimierte `.csv` -Datei Ihres Exports herunterzuladen.

![](../assets/Downloading_export.gif)

## Schritt 3: Zugriff auf historische Exporte {#historical}

Um Ihre bisherigen Exporte anzuzeigen, klicken Sie oben rechts im Bildschirm auf **[!UICONTROL Raw Data Export]** . Auf ausstehende und abgeschlossene Berichte kann bis zu sieben Tage zugegriffen werden.
