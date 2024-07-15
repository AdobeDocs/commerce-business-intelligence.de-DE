---
title: Grafiken zur Massenbearbeitung in Dashboards
description: Erfahren Sie, wie Sie die Massenbearbeitungsfunktion in [!DNL Commerce Intelligence] verwenden.
exl-id: 576ffabb-5e5d-4251-9662-951e2cd30f31
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Diagramme für die Massenbearbeitung in Dashboards

Dank der Massenbearbeitung können Sie die Namen und Daten von Diagrammen in Ihren Dashboards einfach ändern. Sie möchten beispielsweise, dass alle Diagramme in einem bestimmten Dashboard auf einen einzigen Store verweisen und monatlich anstatt vierteljährlich einen Bericht erstellen. Anstatt alles manuell zu ändern, lassen Sie die Funktion `bulk-editing` die Arbeit erledigen. In diesem Thema erfahren Sie, wie Sie Folgendes verwenden:

* [Die Funktion [!DNL Find/Replace] ](#findreplace)

* [Die Funktion [!DNL Prepend Name] ](#prepend)

* [Die Funktion [!DNL Change Dates] ](#dates)

Beachten Sie jedoch Folgendes: *Müssen diese Änderungen dauerhaft sein?* Wenn nicht, sollten Sie das Dashboard klonen und dann die Daten im neuen Dashboard ändern. Auf diese Weise können Sie Ihr ursprüngliches Dashboard beibehalten und gleichzeitig die gewünschten Änderungen vornehmen.

>[!NOTE]
>
>Wenn Sie zahlreiche Berichte ändern, kann der Aktualisierungsprozess einige Zeit in Anspruch nehmen.

## Verwenden von [!DNL Find/Replace] {#findreplace}

1. Klicken Sie auf das Zahnradsymbol (![](../../assets/gear-icon.png)) neben dem Namen Ihres Dashboards und dann auf das Fenster [!UICONTROL Bulk Edit Reports] .

1. Klicken Sie im Popup auf **[!UICONTROL Chart Title Find and Replace]** .

1. Geben Sie im Feld `Chart Title Find` die gesuchten Wörter oder Zeichen ein.

1. Geben Sie im Feld `Replace With` die Wörter oder Zeichen ein, die das ersetzen sollen, was im Feld `Find` enthalten ist.

1. Klicken Sie auf **[!UICONTROL Update Reports]**.

Beispiel:

![Massenbearbeitung](../../assets/bulk_edit.gif)

## Voreingestellt `Chart Names` {#prepend}

1. Klicken Sie auf das Zahnradsymbol (![](../../assets/gear-icon.png)) neben dem Namen Ihres Dashboards und dann auf das Fenster [!UICONTROL Bulk Edit Reports] .

1. Klicken Sie im Popup auf **[!UICONTROL Prepend Report Names]** .

1. Geben Sie die Wörter oder Zeichen ein, denen Sie Ihre Diagramme voranstellen möchten.

1. Klicken Sie auf **[!UICONTROL Update Reports]**.

Beispiel:

![prepend](../../assets/prepend.gif)

## Ändern von `Dates` {#dates}

1. Klicken Sie auf das Zahnradsymbol (![](../../assets/gear-icon.png)) neben dem Namen Ihres Dashboards und wählen Sie dann das Fenster [!UICONTROL Bulk Edit Reports] aus.

1. Klicken Sie im Popup-Fenster auf &quot;**[!UICONTROL Change Dates]**&quot;.

1. Legen Sie die neuen Werte `Start/End Date` und `Time Interval` fest. Sie können diese Felder auch unverändert lassen.

1. Klicken Sie auf **[!UICONTROL Update Reports]**.

Beispiel:

![ Datum ändern](../../assets/dates.gif)
