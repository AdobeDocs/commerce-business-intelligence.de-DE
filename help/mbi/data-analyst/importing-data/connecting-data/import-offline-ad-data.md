---
title: Importieren anderer Anzeigenausgabedaten
description: Erfahren Sie, wie Sie Offline- oder andere Daten zu Werbeausgaben in importieren [!DNL MBI].
exl-id: 6f12a397-0927-4e87-95ff-3a55ccc9e14b
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Importieren anderer Anzeigenausgabedaten

Durch das Hochladen Ihrer Werbeausgaben-Daten können Sie den ROI der Kampagne messen, indem Sie Ihre Werbekosten mit dem Kunden verbinden. `lifetime value (CLV)` der Benutzer, die durch Ihre Kampagnen erworben wurden.

## Hochladen von Daten zu Werbekosten

Der erste Schritt bei der Analyse der Daten zu Anzeigenausgaben besteht darin, die Daten abzurufen. Da die meisten Werbeplattformen den Export von Berichten ermöglichen, empfehlen wir, die Rohdaten von Ihrer Anzeigenplattform zu exportieren und direkt in [!DNL MBI] ohne Manipulationen. Sie können Vorgänge für die Daten in Ihrem Data Warehouse durchführen, sodass Sie Ihre Bemühungen nicht verdoppeln müssen.

Nachdem Sie die Anzeigenausgabedaten exportiert haben, verwenden Sie die [`File Upload` Funktion](../connecting-data/using-file-uploader.md) , um die Daten in Ihr Data Warehouse zu übertragen. Sie können neue Daten auf die gleiche [!DNL MBI] -Tabelle.

## Offline-Quellen

Zusätzlich zu Ihren Online-Kampagnen können Sie auch offline Werbung schalten, z. B. im Radio oder auf einer Werbeplakette. Um diese Fälle zu berücksichtigen, können Sie eine Tabelle mit den Kostendaten manuell in [!DNL MBI].

Die unten beschriebene Tabellenstruktur wird beim Erstellen einer `.csv` -Datei, um Anzeigenausgabedaten aufzuzeichnen. Eine Vorlagendatei wird ebenfalls am Ende dieses Artikels als Beispiel angehängt. Empfohlene Spalten:

* `ID` - Dies ist eine eindeutige Kennung für jede Datenzeile, die von der Datenbank als Primärschlüssel verwendet wird. Dies muss für jede Zeile anders sein.
* `Date` - Dies ist das Datum, an dem die Kampagne ausgeführt wurde, im Format JJJJ-MM-TT.
* `Amount` - Dies ist der Betrag, den Sie für die Kampagne ausgegeben haben.
* `campaign` - Dies ist der Kampagnenname. Wenn Sie [!DNL Google Analytics] um Ihre anderen Anzeigenausgabedaten zu verfolgen, sollte sie mit dem Namen utm\_campaign übereinstimmen.
* `source` - Dies ist der Quellname. Wenn Sie [!DNL Google Analytics], sollte dies mit dem `utm_source` name.
* `other` (Optional) - Sie können auch zusätzliche Spalten einfügen, die Ihnen bei der Segmentierung von Kampagnen und Kosten helfen. Es kann auch eine Möglichkeit sein, mehrere verschiedene UTM-Kampagnennamen zu Tracking-Zwecken in einer einzigen, kohärenten Kampagne zusammenzufassen. Anstatt dies manuell einzurichten, kann es sinnvoll sein, eine V-Suche in einem zweiten Blatt zu verwenden, um jeden Kampagnennamen mit dem anderen Namen abzugleichen und ihn hier dynamisch zu melden.

## Verwandte

* [Verbinden [!DNL AdWords] data](../integrations/google-adwords.md)
* [Steigerung des ROI bei Werbekampagnen](../../analysis/roi-ad-camp.md)
