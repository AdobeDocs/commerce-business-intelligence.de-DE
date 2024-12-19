---
title: Andere Anzeigenausgabendaten importieren
description: Erfahren Sie, wie Sie Daten zu Offline- oder anderen Werbeausgaben in importieren [!DNL Commerce Intelligence].
exl-id: 6f12a397-0927-4e87-95ff-3a55ccc9e14b
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Andere Anzeigenausgabendaten importieren

Durch das Hochladen Ihrer Werbeausgabendaten können Sie den Kampagnen-ROI messen, indem Sie Ihre Werbekosten und die `customer lifetime value (CLV)` der aus Ihren Kampagnen erworbenen Benutzer vereinen.

## Hochladen von Werbekostendaten

Der erste Schritt bei der Analyse und Verwendung von Daten besteht darin, die Daten abzurufen. Da die meisten Werbeplattformen den Export von Berichten ermöglichen, empfiehlt Adobe, die Rohdaten von Ihrer Werbeplattform zu exportieren und ohne Manipulation direkt in [!DNL Commerce Intelligence] hochzuladen. Sie können Vorgänge mit den Daten auf Ihrem Data Warehouse durchführen, sodass Sie Ihre Anstrengungen nicht verdoppeln müssen.

Nachdem Sie die Daten zu Werbeausgaben exportiert haben, verwenden Sie die [`File Upload` Funktion](../connecting-data/using-file-uploader.md) um die Daten auf Ihren Data Warehouse zu bringen. Sie können im Laufe der Zeit neue Daten in dieselbe [!DNL Commerce Intelligence]-Tabelle hochladen.

## Offline-Quellen

Zusätzlich zu Ihren Online-Kampagnen können Sie auch Offline-Werbung schalten, z. B. im Radio oder auf einer Plakatwand. Um diesen Fällen Rechnung zu tragen, können Sie manuell eine Tabelle mit den Kostendaten in [!DNL Commerce Intelligence] hochladen.

Die unten untersuchte Tabellenstruktur wird beim Erstellen einer `.csv` zum Aufzeichnen und Ausgeben von Daten empfohlen. Eine Vorlagendatei wird ebenfalls am Ende dieses Themas angehängt, um als Beispiel zu dienen. Empfohlene Spalten sind:

* `ID` : Dies ist eine eindeutige Kennung für jede Datenzeile, die von der Datenbank als Primärschlüssel verwendet wird. Dieser muss für jede Zeile anders sein.
* `Date` - Dies ist das Datum, an dem die Kampagne ausgeführt wurde, im Format jjjjj-mm-tt.
* `Amount` : Dies ist der Betrag, den Sie für die Kampagne ausgegeben haben.
* `campaign` : Dies ist der Kampagnenname. Wenn Sie [!DNL Google Analytics] zum Nachverfolgen Ihrer anderen Anzeigenausgabendaten verwenden, sollte diese mit dem utm\_campaign-Namen übereinstimmen.
* `source` - Dies ist der Quellenname. Wenn Sie [!DNL Google Analytics] verwenden, sollte dies mit dem `utm_source` übereinstimmen.
* `other` (Optional) - Sie können auch zusätzliche Spalten einbeziehen, um Kampagnen und Kosten zu segmentieren. Außerdem kann es eine Möglichkeit sein, mehrere verschiedene UTM-Kampagnennamen zu Tracking-Zwecken in einer einzigen, kohärenten Kampagne zusammenzufassen. Anstatt dies manuell einzurichten, empfiehlt es sich möglicherweise, eine V-Suche zu verwenden, um ein zweites Blatt zu verwenden, um jeden Kampagnennamen mit dem anderen Namen abzugleichen und ihn hier dynamisch zu melden.

## verwandt

* [ [!DNL AdWords] ](../integrations/google-adwords.md)
* [Steigerung des ROI von Werbekampagnen](../../analysis/roi-ad-camp.md)
