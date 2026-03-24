---
title: Massenbearbeitung von Diagrammen in Dashboards
description: Erfahren Sie, wie Sie die Funktion zur Massenbearbeitung in  [!DNL Commerce Intelligence] verwenden.
exl-id: 576ffabb-5e5d-4251-9662-951e2cd30f31
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
TQID: https://experienceleague.adobe.com/FcFTKq9TvldFwo7nl-bGRyup1uxscjrnOutJcA-h-5c
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 260
ht-degree: 0%

---

# Diagramme für die Massenbearbeitung in Dashboards

Die Massenbearbeitungsfunktion erleichtert das Ändern von Diagrammnamen und Datumsangaben in Ihren Dashboards. Sie möchten beispielsweise, dass alle Diagramme in einem bestimmten Dashboard auf einen einzelnen Store verweisen und Berichte auf monatlicher Basis und nicht vierteljährlich erstellen. Anstatt alles manuell zu ändern, lassen Sie die `bulk-editing` die Arbeit erledigen. In diesem Thema erfahren Sie, wie Sie Folgendes verwenden:

* [Die  [!DNL Find/Replace] ](#findreplace)

* [Die  [!DNL Prepend Name] ](#prepend)

* [Die  [!DNL Change Dates] ](#dates)

Berücksichtigen Sie dabei Folgendes: *Müssen diese Änderungen dauerhaft sein?* Wenn nicht, klonen Sie das Dashboard und ändern Sie dann die Daten im neuen Dashboard. Auf diese Weise können Sie Ihr ursprüngliches Dashboard beibehalten und gleichzeitig die benötigten Änderungen vornehmen.

>[!NOTE]
>
>Wenn Sie zahlreiche Berichte ändern, kann der Aktualisierungsprozess eine Weile dauern.

## Verwenden von [!DNL Find/Replace] {#findreplace}

1. Klicken Sie auf das Zahnradsymbol ![Zahnradsymbol](../../assets/gear-icon.png) neben dem Namen Ihres Dashboards und dann auf das [!UICONTROL Bulk Edit Reports].

1. Klicken Sie im Popup auf **[!UICONTROL Chart Title Find and Replace]** .

1. Geben Sie im Feld `Chart Title Find` die Wörter oder Zeichen ein, die Sie suchen möchten.

1. Geben Sie im Feld `Replace With` die Wörter oder Zeichen ein, die den Inhalt des `Find` ersetzen sollen.

1. Klicken Sie auf **[!UICONTROL Update Reports]**.

Beispiel:

![Massenbearbeitung](../../assets/bulk_edit.gif)

## `Chart Names` voranstellen {#prepend}

1. Klicken Sie auf das Zahnradsymbol ![Zahnradsymbol](../../assets/gear-icon.png) neben dem Namen Ihres Dashboards und dann auf das [!UICONTROL Bulk Edit Reports].

1. Klicken Sie im Popup auf **[!UICONTROL Prepend Report Names]** .

1. Geben Sie die Wörter oder Zeichen ein, denen Sie Ihre Diagramme voranstellen möchten.

1. Klicken Sie auf **[!UICONTROL Update Reports]**.

Beispiel:

![voranstellen](../../assets/prepend.gif)

## Ändern von `Dates` {#dates}

1. Klicken Sie auf das Zahnradsymbol ![Zahnradsymbol](../../assets/gear-icon.png) neben dem Namen Ihres Dashboards und wählen Sie dann das [!UICONTROL Bulk Edit Reports] aus.

1. Klicken Sie im Popup-Fenster auf **[!UICONTROL Change Dates]** .

1. Legen Sie die neuen `Start/End Date` und `Time Interval` fest. Sie können diese Felder auch unverändert lassen.

1. Klicken Sie auf **[!UICONTROL Update Reports]**.

Beispiel:

![Ändern von Datumsangaben](../../assets/dates.gif)
