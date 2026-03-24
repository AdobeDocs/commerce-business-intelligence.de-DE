---
title: Andere Anzeigenausgabendaten importieren
description: Erfahren Sie, wie Sie Daten zu Offline- oder anderen Werbeausgaben in importieren [!DNL Commerce Intelligence].
exl-id: 6f12a397-0927-4e87-95ff-3a55ccc9e14b
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/jx-MMry1-XGeM4htPkH6GC1Et5nYjyD7aWn3p-nmcC8
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 369
ht-degree: 0%

---

# Andere Anzeigenausgabendaten importieren

Durch das Hochladen Ihrer Werbeausgabendaten können Sie den Kampagnen-ROI messen, indem Sie Ihre Werbekosten und die `customer lifetime value (CLV)` der aus Ihren Kampagnen erworbenen Benutzer vereinen.

## Hochladen von Werbekostendaten

Der erste Schritt bei der Analyse und Verwendung von Daten besteht darin, die Daten abzurufen. Da die meisten Werbeplattformen den Export von Berichten ermöglichen, empfiehlt Adobe, die Rohdaten aus Ihrer Werbeplattform zu exportieren und ohne Manipulation direkt in [!DNL Commerce Intelligence] hochzuladen. Sie können Vorgänge mit den Daten in Ihrer Data Warehouse durchführen, sodass Sie Ihre Anstrengungen nicht verdoppeln müssen.

Nachdem Sie die Daten zu Werbeausgaben exportiert haben, verwenden Sie die [`File Upload` Funktion](../connecting-data/using-file-uploader.md) um die Daten in Ihre Data Warehouse zu bringen. Sie können im Laufe der Zeit neue Daten in dieselbe [!DNL Commerce Intelligence]-Tabelle hochladen.

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

* [&#x200B; [!DNL AdWords] &#x200B;](../integrations/google-adwords.md)
* [Steigerung des ROI von Werbekampagnen](../../analysis/roi-ad-camp.md)
