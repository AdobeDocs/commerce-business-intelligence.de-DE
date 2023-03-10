---
title: Kontoeinstellungen verwalten
description: Erfahren Sie, wie Sie Ihre Kontoeinstellungen für Ihre Data Warehouse anpassen können.
exl-id: 847d51b1-287e-4c14-b64e-0bd9bfcccedc
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Kontoeinstellungen anpassen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen.](../../administrator/user-management/user-management.md)

In [!DNL MBI] -Konto können Sie Ihre Kontoeinstellungen für Ihre Data Warehouse anpassen. Sie können darauf zugreifen, indem Sie Ihren Organisationsnamen in der oberen rechten Ecke eines beliebigen Bildschirms auswählen und dann **[!UICONTROL Account Settings]** aus dem Dropdown-Menü aus.

* **[!UICONTROL Client Name:]** Diese Einstellung wird in der oberen rechten Ecke aller Dashboards und an anderer Stelle in Ihrem Konto angezeigt. Wenn Sie sich ändern möchten **[!UICONTROL "Vandelay Industries Co., Ltd]** nur **[!UICONTROL "Vandelay]**, ist dies der Ort, um dies zu tun.

* **[!UICONTROL Currency:]** Dies ist die *Standardwährung* für alle Geldwerte in Ihrem Konto. Jedes Mal, wenn ein Dezimalwert oder ein Währungswert mit Ihrer Data Warehouse synchronisiert wird, bestimmt diese Einstellung das Symbol, das vor diesem Wert in Ihren Berichten platziert wird.

* **[!UICONTROL Blackout Hours:]** Mit dieser Einstellung wird sichergestellt, dass Ihre Data Warehouse während der ausgewählten Tageszeiten nicht auf Ihre verbundenen Datenbanken zugreifen kann. Alle Stunden werden als Nullstunde und in Eastern Standard Time (EST) ausgedrückt. Wenn Sie beispielsweise nicht möchten, dass zwischen 9:00 Uhr EST und 13:00 Uhr EST auf Ihre Produktionsdatenbank zugegriffen wird, geben Sie das folgende Ziffernarray ein: **9, 10, 11, 12**.

* **[!UICONTROL Forced update hours:]** Mit dieser Einstellung wird sichergestellt, dass die Aktualisierung einer Data Warehouse automatisch in Ihrem Konto beginnt *während der Stunden* angegeben haben. Wie bei Blackout-Stunden befinden sich auch diese in ET. Wenn Sie beispielsweise möchten, dass Aktualisierungen der Data Warehouse automatisch am **Mitternacht** und **Mittag** EST: Sie sollten das folgende Ziffernarray eingeben: **0, 12**.

* **[!UICONTROL Send email summaries if the data has not updated yet:]** Diese Option verwaltet Situationen, in denen eine E-Mail-Zusammenfassung zum Senden geplant ist *vor den Daten in einem seiner Berichte* aktualisiert wird. Wenn Sie **Nein**, überspringt Ihr Konto den Versand der E-Mail zum geplanten Zeitpunkt. Stattdessen sendet Ihr Konto diese nach Aktualisierung Ihrer Daten. Wenn Sie **[!UICONTROL Yes]**, sendet Ihr Konto die E-Mail, enthält eine Meldung, die erklärt, dass die Daten veraltet sind, und sendet eine weitere E-Mail, sobald Ihre Daten aktualisiert wurden.

* **[!UICONTROL Enable data updates:]** Mit dieser Option wird sichergestellt, dass Datenaktualisierungen für Ihr Konto ausgeführt werden. Wenn Sie die Einstellung auf **[!UICONTROL No]**, werden die Datensynchronisationen und Spaltenberechnungen in Ihrem Konto angehalten.

>[!NOTE]
>
>Wählen Sie **[!UICONTROL Save Customizations]** nachdem Sie Änderungen vorgenommen haben.
