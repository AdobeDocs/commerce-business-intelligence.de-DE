---
title: Kontoeinstellungen verwalten
description: Erfahren Sie, wie Sie Ihre Kontoeinstellungen für Ihre Data Warehouse anpassen können.
exl-id: 847d51b1-287e-4c14-b64e-0bd9bfcccedc
role: Admin, User
feature: Accounts
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Kontoeinstellungen anpassen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen.](../../administrator/user-management/user-management.md)

In Ihrem [!DNL Commerce Intelligence] -Konto können Sie Ihre Kontoeinstellungen für Ihre Data Warehouse anpassen. Sie können darauf zugreifen, indem Sie Ihren Organisationsnamen in der oberen rechten Ecke eines Bildschirms auswählen und dann im Dropdown-Menü die Option **[!UICONTROL Account Settings]** auswählen.

* **[!UICONTROL Client Name:]** Diese Einstellung wird in der oberen rechten Ecke aller Dashboards und an anderer Stelle in Ihrem Konto angezeigt. Wenn Sie **[!UICONTROL "Vandelay Industries Co., Ltd]** auf nur **[!UICONTROL "Vandelay]** ändern möchten, tun Sie dies hier.

* **[!UICONTROL Currency:]** Dies ist die *Standardwährung* für alle Geldwerte in Ihrem Konto. Jedes Mal, wenn ein Dezimalwert oder ein Währungswert mit Ihrer Data Warehouse synchronisiert wird, bestimmt diese Einstellung das Symbol, das vor diesem Wert in Ihren Berichten platziert wird.

* **[!UICONTROL Blackout Hours:]** Diese Einstellung stellt sicher, dass Ihre Data Warehouse während der ausgewählten Tageszeiten nicht auf Ihre verbundenen Datenbanken zugreifen kann. Alle Stunden werden als Nullstunde und in Eastern Standard Time (EST) ausgedrückt. Wenn Sie beispielsweise nicht möchten, dass zwischen 9:00 Uhr EST und 13:00 Uhr EST auf Ihre Produktionsdatenbank zugegriffen wird, müssen Sie das folgende Ziffernarray eingeben: **9, 10, 11, 12**.

* **[!UICONTROL Forced update hours:]** Diese Einstellung stellt sicher, dass in Ihrem Data Warehouse-Konto *während der angegebenen Stunden* automatisch ein Update gestartet wird. Wie bei Blackout-Stunden befinden sich auch diese in ET. Wenn Sie beispielsweise möchten, dass Data Warehouse-Updates automatisch um **Mitternacht** und **Mittag** EST beginnen, müssen Sie das folgende Ziffernarray eingeben: **0, 12**.

* **[!UICONTROL Send email summaries if the data has not updated yet:]** Diese Option verwaltet Situationen, in denen eine E-Mail-Zusammenfassung geplant ist, *zu senden, bevor die Daten in einem ihrer Berichte aktualisiert werden*. Wenn Sie **Nein** auswählen, überspringt Ihr Konto den Versand der E-Mail zum geplanten Zeitpunkt. Stattdessen sendet Ihr Konto diese nach Aktualisierung Ihrer Daten. Wenn Sie &quot;**[!UICONTROL Yes]**&quot; auswählen, sendet Ihr Konto die E-Mail, enthält eine Meldung, die erklärt, dass die Daten veraltet sind, und sendet eine weitere E-Mail, sobald Ihre Daten aktualisiert wurden.

* **[!UICONTROL Enable data updates:]** Diese Option stellt sicher, dass Datenaktualisierungen für Ihr Konto ausgeführt werden. Wenn Sie die Einstellung auf **[!UICONTROL No]** ändern, werden die Datensynchronisation und Spaltenberechnungen in Ihrem Konto angehalten.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie **[!UICONTROL Save Customizations]** auswählen, nachdem Sie Änderungen vorgenommen haben.
