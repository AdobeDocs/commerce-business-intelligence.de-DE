---
title: Grafiken zur Massenbearbeitung in Dashboards
description: Erfahren Sie, wie Sie die Massenbearbeitungsfunktion in [!DNL Commerce Intelligence].
exl-id: 576ffabb-5e5d-4251-9662-951e2cd30f31
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Diagramme für die Massenbearbeitung in Dashboards

Dank der Massenbearbeitung können Sie die Namen und Daten von Diagrammen in Ihren Dashboards einfach ändern. Sie möchten beispielsweise, dass alle Diagramme in einem bestimmten Dashboard auf einen einzigen Store verweisen und monatlich anstatt vierteljährlich einen Bericht erstellen. Anstatt alles manuell zu ändern, lassen Sie die `bulk-editing` -Funktion verwenden. In diesem Thema erfahren Sie, wie Sie Folgendes verwenden:

* [Die [!DNL Find/Replace] Funktion](#findreplace)

* [Die [!DNL Prepend Name] Funktion](#prepend)

* [Die [!DNL Change Dates] Funktion](#dates)

Beachten Sie jedoch Folgendes: *Müssen diese Änderungen dauerhaft sein?* Wenn nicht, sollten Sie das Dashboard klonen und dann die Daten im neuen Dashboard ändern. Auf diese Weise können Sie Ihr ursprüngliches Dashboard beibehalten und gleichzeitig die gewünschten Änderungen vornehmen.

>[!NOTE]
>
>Wenn Sie zahlreiche Berichte ändern, kann der Aktualisierungsprozess einige Zeit in Anspruch nehmen.

## Verwenden [!DNL Find/Replace] {#findreplace}

1. Klicken Sie auf das Zahnrad (![](../../assets/gear-icon.png)) neben dem Namen Ihres Dashboards angezeigt wird, können Sie die [!UICONTROL Bulk Edit Reports] Fenster.

1. Klicks **[!UICONTROL Chart Title Find and Replace]** im Popup-Fenster angezeigt.

1. Im `Chart Title Find` eingeben, die gesuchten Wörter oder Zeichen eingeben.

1. Im `Replace With` -Feld, geben Sie die Wörter oder Zeichen ein, die die im `Find` -Feld.

1. Klicken **[!UICONTROL Update Reports]**.

Beispiel:

![Massenbearbeitung](../../assets/bulk_edit.gif)

## Vorabausstehend `Chart Names` {#prepend}

1. Klicken Sie auf das Zahnrad (![](../../assets/gear-icon.png)) neben dem Namen Ihres Dashboards angezeigt wird, können Sie die [!UICONTROL Bulk Edit Reports] Fenster.

1. Klicks **[!UICONTROL Prepend Report Names]** im Popup-Fenster angezeigt.

1. Geben Sie die Wörter oder Zeichen ein, denen Sie Ihre Diagramme voranstellen möchten.

1. Klicken **[!UICONTROL Update Reports]**.

Beispiel:

![Prepend](../../assets/prepend.gif)

## Ändern `Dates` {#dates}

1. Klicken Sie auf das Zahnrad (![](../../assets/gear-icon.png)) neben dem Namen Ihres Dashboards angezeigt werden, und wählen Sie dann die [!UICONTROL Bulk Edit Reports] Fenster.

1. Klicks **[!UICONTROL Change Dates]** im Popup-Fenster.

1. Festlegen der neuen `Start/End Date` und `Time Interval`. Sie können diese Felder auch unverändert lassen.

1. Klicken **[!UICONTROL Update Reports]**.

Beispiel:

![Datum ändern](../../assets/dates.gif)
