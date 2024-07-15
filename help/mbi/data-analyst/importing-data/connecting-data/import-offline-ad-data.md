---
title: Importieren anderer Anzeigenausgabedaten
description: Erfahren Sie, wie Sie Offline- oder andere Daten zu Werbeausgaben in [!DNL Commerce Intelligence] importieren.
exl-id: 6f12a397-0927-4e87-95ff-3a55ccc9e14b
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Importieren anderer Anzeigenausgabedaten

Durch das Hochladen Ihrer Daten zu Werbeausgaben können Sie den ROI Ihrer Kampagne messen, indem Sie Ihre Werbekosten und die `customer lifetime value (CLV)` der durch Ihre Kampagnen erworbenen Benutzer miteinander verbinden.

## Hochladen von Daten zu Werbekosten

Der erste Schritt bei der Analyse der Daten zu Anzeigenausgaben besteht darin, die Daten abzurufen. Da die meisten Werbeplattformen den Export von Berichten ermöglichen, empfiehlt Adobe, die Rohdaten von Ihrer Anzeigenplattform zu exportieren und direkt ohne Manipulation in [!DNL Commerce Intelligence] hochzuladen. Sie können Vorgänge für die Daten in Ihrer Data Warehouse durchführen, sodass Sie Ihre Bemühungen nicht verdoppeln müssen.

Nachdem Sie die Anzeigenausgabedaten exportiert haben, verwenden Sie die [`File Upload`-Funktion](../connecting-data/using-file-uploader.md) , um die Daten in Ihre Data Warehouse zu übertragen. Sie können neue Daten im Laufe der Zeit in dieselbe [!DNL Commerce Intelligence]-Tabelle hochladen.

## Offline-Quellen

Zusätzlich zu Ihren Online-Kampagnen können Sie auch offline Werbung schalten, z. B. im Radio oder auf einer Werbeplakette. Um dies zu berücksichtigen, können Sie eine Tabelle mit den Kostendaten manuell in [!DNL Commerce Intelligence] hochladen.

Die unten beschriebene Tabellenstruktur wird beim Erstellen einer `.csv` -Datei zur Aufzeichnung von Anzeigenausgabedaten empfohlen. Eine Vorlagendatei wird ebenfalls am Ende dieses Themas als Beispiel angehängt. Empfohlene Spalten:

* `ID` - Dies ist eine eindeutige Kennung für jede Datenzeile, die von der Datenbank als Primärschlüssel verwendet wird. Dies muss für jede Zeile anders sein.
* `Date` - Dies ist das Datum, an dem die Kampagne im Format JJJJ-MM-TT ausgeführt wurde.
* `Amount` - Dies ist der Betrag, den Sie für die Kampagne ausgegeben haben.
* `campaign` - Dies ist der Kampagnenname. Wenn Sie [!DNL Google Analytics] verwenden, um Ihre anderen Daten zu Werbeausgaben zu verfolgen, sollte dies mit dem Namen utm\_campaign übereinstimmen.
* `source` - Dies ist der Quellname. Wenn Sie [!DNL Google Analytics] verwenden, sollte dies mit dem `utm_source` -Namen übereinstimmen.
* `other` (Optional) - Sie können auch zusätzliche Spalten einfügen, die Ihnen bei der Segmentierung von Kampagnen und Kosten helfen. Es kann auch eine Möglichkeit sein, mehrere verschiedene UTM-Kampagnennamen zu Tracking-Zwecken in einer einzigen, kohärenten Kampagne zusammenzufassen. Anstatt dies manuell einzurichten, kann es sinnvoll sein, eine V-Suche in einem zweiten Blatt zu verwenden, um jeden Kampagnennamen mit dem anderen Namen abzugleichen und ihn hier dynamisch zu melden.

## Verwandte

* [ [!DNL AdWords] data verbinden](../integrations/google-adwords.md)
* [Steigerung des ROI bei Werbekampagnen](../../analysis/roi-ad-camp.md)
