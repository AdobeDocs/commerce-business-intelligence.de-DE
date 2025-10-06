---
title: Formatieren und Importieren von Finanzdaten
description: Erfahren Sie, wie Sie Finanzdaten formatieren und importieren.
exl-id: cdbed262-7cf1-4fd6-ad5a-c44d26dffba7
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Finanzdaten formatieren und importieren

In diesem Thema wird die beste Möglichkeit zum Importieren von Finanzdaten für die Analyse in [!DNL Adobe Commerce Intelligence] erläutert.

Eine zweidimensionale tabellenübergreifende Datentabelle ist häufig das Format, das für Finanzdaten verwendet wird. Bei Werten, die nach Beschriftungen in Spalten und Zeilen kategorisiert sind, ist diese Art von Layout möglicherweise einfach mit menschlichen Augen und Tabellen-Tools zu sehen, aber es ist nicht datenbankfreundlich.

![Kreuztabellenformat mit Daten im Pivot-Tabellen-Layout](../../mbi/assets/crosstab.png)

Um diese Daten in [!DNL Commerce Intelligence] zu importieren und zu analysieren, muss die Tabelle in eine eindimensionale Liste reduziert werden. Wenn sie reduziert wird, wird jeder Datenwert durch mehrere Kennzeichnungen kategorisiert, die sich alle in einer einzigen Zeile befinden, wobei jede Zeile eindeutig ist oder einen eindeutigen Bezeichner hätte, z. B. eine Primärschlüsselspalte.

![Reduziertes Format mit Daten im Spaltenlayout](../../mbi/assets/flattened.png)

## Excel-Dateien für den Import formatieren

So reduzieren Sie eine zweidimensionale Tabelle mithilfe einer [!DNL Excel] Pivot-Tabelle:

1. Öffnen Sie die Datei mit der zweidimensionalen Datentabelle.
1. Öffnen Sie den PivotTable-Assistenten. In [!DNL Windows] ist der Tastaturbefehl `Alt-D`. Geben Sie [!DNL Mac OS] `Command-Option-P` ein.
1. Wählen Sie **[!UICONTROL Multiple consolidated ranges]** und klicken Sie auf **[!UICONTROL Next]**.
1. Wählen Sie **[!UICONTROL I will create the page fields]** und klicken Sie auf **[!UICONTROL Next]**.
1. Wählen Sie den gesamten Datensatz in der zweidimensionalen Tabelle aus, einschließlich der Beschriftungen. Stellen Sie sicher, dass für die Anzahl der gewünschten Seitenfelder `0` ausgewählt ist, und klicken Sie auf **[!UICONTROL Next]**.
1. Erstellen Sie die Pivot-Tabelle in einem neuen Blatt und klicken Sie auf **[!UICONTROL Finish]**.
1. Heben Sie die Auswahl der Spalten- und Zeilenfelder in der Feldliste auf.
1. Doppelklicken Sie auf den resultierenden numerischen Wert, um die reduzierten Quelldaten in einem neuen Blatt anzuzeigen.
   ![Excel-Pivot-Tabelle-Feldliste mit Doppelklick zum Erweitern](../../mbi/assets/pivot-table-double-click.png)
1. Als `CSV` speichern.

## Verpackung

Die Datentabelle wurde in ein Listenformat konvertiert, wobei alle ursprünglichen Informationen beibehalten wurden, und kann jetzt zur [ in  [!DNL Commerce Intelligence]](../data-analyst/importing-data/connecting-data/using-file-uploader.md) importiert werden.
