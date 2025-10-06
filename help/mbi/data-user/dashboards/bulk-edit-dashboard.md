---
title: Massenbearbeitung von Diagrammen in Dashboards
description: Erfahren Sie, wie Sie die Funktion zur Massenbearbeitung in  [!DNL Commerce Intelligence] verwenden.
exl-id: 576ffabb-5e5d-4251-9662-951e2cd30f31
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Diagramme für die Massenbearbeitung in Dashboards

Die Massenbearbeitungsfunktion erleichtert das Ändern von Diagrammnamen und Datumsangaben in Ihren Dashboards. Sie möchten beispielsweise, dass alle Diagramme in einem bestimmten Dashboard auf einen einzelnen Store verweisen und Berichte auf monatlicher Basis und nicht vierteljährlich erstellen. Anstatt alles manuell zu ändern, lassen Sie die `bulk-editing` die Arbeit erledigen. In diesem Thema erfahren Sie, wie Sie Folgendes verwenden:

* [Die  [!DNL Find/Replace] &#x200B;](#findreplace)

* [Die  [!DNL Prepend Name] &#x200B;](#prepend)

* [Die  [!DNL Change Dates] &#x200B;](#dates)

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
