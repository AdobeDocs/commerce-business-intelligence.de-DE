---
title: Formatieren und Importieren von Finanzdaten
description: Erfahren Sie, wie Sie Finanzdaten formatieren und importieren.
exl-id: cdbed262-7cf1-4fd6-ad5a-c44d26dffba7
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Finanzdaten formatieren und importieren

In diesem Thema wird die beste Methode zum Importieren von Finanzdaten für die Analyse in [!DNL Adobe Commerce Intelligence] erläutert.

Eine zweidimensionale, tabulatorübergreifende Datentabelle ist häufig das für Finanzdaten verwendete Format. Mit Werten, die sowohl in Spalten als auch in Zeilen durch Beschriftungen kategorisiert sind, ist diese Art von Layout mit menschlichen Augen und Tabellenwerkzeugen möglicherweise einfach anzuzeigen, aber für Datenbanken nicht benutzerfreundlich.

![](../../mbi/assets/crosstab.png)

Um diese Daten in [!DNL Commerce Intelligence] zu importieren und zu analysieren, muss die Tabelle in eine eindimensionale Liste reduziert werden. Wenn der Wert reduziert wird, wird jeder Datenwert durch mehrere Beschriftungen kategorisiert, die sich alle in einer Zeile befinden, wobei jede Zeile eindeutig ist oder eine eindeutige Kennung aufweisen würde, z. B. eine Primärschlüsselspalte.

![](../../mbi/assets/flattened.png)

## Excel-Dateien für den Import formatieren

So reduzieren Sie eine zweidimensionale Tabelle mit einer [!DNL Excel] Pivot-Tabelle:

1. Öffnen Sie die Datei mit der zweidimensionalen Datentabelle.
1. Öffnen Sie den Assistenten PivotTable . In [!DNL Windows] ist der Tastaturbefehl `Alt-D`. Geben Sie in [!DNL Mac OS] den Wert `Command-Option-P` ein.
1. Wählen Sie **[!UICONTROL Multiple consolidated ranges]** und klicken Sie auf **[!UICONTROL Next]**.
1. Wählen Sie **[!UICONTROL I will create the page fields]** und klicken Sie auf **[!UICONTROL Next]**.
1. Wählen Sie den gesamten Datensatz in der zweidimensionalen Tabelle einschließlich der Titel aus. Stellen Sie sicher, dass für die Anzahl der gewünschten Seitenfelder `0` ausgewählt ist, und klicken Sie auf **[!UICONTROL Next]**.
1. Erstellen Sie die Pivot-Tabelle in einem neuen Arbeitsblatt und klicken Sie auf **[!UICONTROL Finish]**.
1. Heben Sie die Auswahl der Spalten- und Zeilenfelder in der Feldliste auf.
1. Doppelklicken Sie auf den resultierenden numerischen Wert, um die reduzierten Quelldaten in einem neuen Blatt anzuzeigen.
   ![](../../mbi/assets/pivot-table-double-click.png)
1. Speichern Sie sie als `CSV` -Datei.

## Aufwischen

Die Datentabelle wurde in ein Listenformat konvertiert, wobei alle ursprünglichen Informationen beibehalten werden. Sie kann jetzt für die Analyse [in  [!DNL Commerce Intelligence]](../data-analyst/importing-data/connecting-data/using-file-uploader.md) importiert werden.
