---
title: Formatieren und Importieren von Finanzdaten
description: Erfahren Sie, wie Sie Finanzdaten formatieren und importieren.
exl-id: cdbed262-7cf1-4fd6-ad5a-c44d26dffba7
role: Admin, Developer, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager
TQID: https://experienceleague.adobe.com/O1WKa98rRVw1dcgNQPsORit2gmZNn1Wi7H-Q4J7KcA0
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 278
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
