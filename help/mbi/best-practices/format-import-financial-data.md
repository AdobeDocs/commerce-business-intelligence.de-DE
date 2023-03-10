---
title: Formatieren und Importieren von Finanzdaten
description: Erfahren Sie, wie Sie Finanzdaten formatieren und importieren.
exl-id: cdbed262-7cf1-4fd6-ad5a-c44d26dffba7
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Finanzdaten formatieren und importieren

In diesem Thema wird die beste Methode zum Importieren von Finanzdaten für die Analyse in [!DNL MBI].

Eine zweidimensionale, tabulatorübergreifende Datentabelle ist häufig das für Finanzdaten verwendete Format. Mit Werten, die sowohl in Spalten als auch in Zeilen durch Beschriftungen kategorisiert sind, ist diese Art von Layout mit menschlichen Augen und Tabellenwerkzeugen möglicherweise einfach anzuzeigen, aber für Datenbanken nicht benutzerfreundlich.

![](../../mbi/assets/crosstab.png)

So importieren und analysieren Sie diese Daten in [!DNL MBI], muss die Tabelle in eine eindimensionale Liste reduziert werden. Wenn der Wert reduziert wird, wird jeder Datenwert durch mehrere Beschriftungen kategorisiert, die sich alle in einer Zeile befinden, wobei jede Zeile eindeutig ist oder eine eindeutige Kennung aufweisen würde, z. B. eine Primärschlüsselspalte.

![](../../mbi/assets/flattened.png)

## Excel-Dateien für den Import formatieren

So reduzieren Sie eine zweidimensionale Tabelle mithilfe einer Excel-Pivot-Tabelle:

1. Öffnen Sie die Datei mit der zweidimensionalen Datentabelle.
1. Öffnen Sie den Assistenten PivotTable . Unter Windows lautet der Tastaturbefehl `Alt-D`. Geben Sie unter Mac OS `Command-Option-P`.
1. Auswählen **[!UICONTROL Multiple consolidated ranges]** und klicken Sie auf **[!UICONTROL Next]**.
1. Auswählen **[!UICONTROL I will create the page fields]** und klicken Sie auf **[!UICONTROL Next]**.
1. Wählen Sie den gesamten Datensatz in der zweidimensionalen Tabelle einschließlich der Beschriftungen aus. Stellen Sie sicher, dass `0` für die Anzahl der gewünschten Seitenfelder ausgewählt ist, und klicken Sie auf **[!UICONTROL Next]**.
1. Pivot-Tabellen in einem neuen Arbeitsblatt erstellen und auf **[!UICONTROL Finish]**.
1. Heben Sie die Auswahl der Spalten- und Zeilenfelder in der Feldliste auf.
1. Doppelklicken Sie auf den resultierenden numerischen Wert, um die reduzierten Quelldaten in einem neuen Blatt anzuzeigen.
   ![](../../mbi/assets/pivot-table-double-click.png)
1. Als `CSV` -Datei.

Das ist es! Die Datentabelle wurde in ein Listenformat konvertiert, wobei alle ursprünglichen Informationen beibehalten werden. Sie kann jetzt [importiert in [!DNL MBI]](../data-analyst/importing-data/connecting-data/using-file-uploader.md) zur Analyse.
