---
title: Kontoeinstellungen verwalten
description: Erfahren Sie, wie Sie Ihre Kontoeinstellungen für Ihren Data Warehouse anpassen.
exl-id: 847d51b1-287e-4c14-b64e-0bd9bfcccedc
role: Admin, User
feature: Accounts
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Anpassen der Kontoeinstellungen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen.](../../administrator/user-management/user-management.md)

In Ihrem [!DNL Commerce Intelligence]-Konto können Sie Ihre Kontoeinstellungen für Ihren Data Warehouse anpassen. Sie können auf diese zugreifen, indem Sie in der oberen rechten Ecke eines beliebigen Bildschirms auf den Namen Ihres Unternehmens und anschließend im Dropdown-Menü auf **[!UICONTROL Account Settings]** klicken.

* **[!UICONTROL Client Name:]** Diese Einstellung wird in der oberen rechten Ecke aller Dashboards und überall in Ihrem Konto angezeigt. Wenn Sie **[!UICONTROL "Vandelay Industries Co., Ltd]** einfach in **[!UICONTROL "Vandelay]** ändern möchten, hier ist der richtige Weg.

* **[!UICONTROL Currency:]** Dies ist die *Standardwährung* für alle Geldwerte in Ihrem Konto. Jedes Mal, wenn ein Dezimal- oder Währungswert mit Ihrem Data Warehouse synchronisiert wird, bestimmt diese Einstellung das Symbol, das in Ihren Berichten vor diesem Wert platziert wird.

* **[!UICONTROL Blackout Hours:]** Mit dieser Einstellung wird sichergestellt, dass Ihr Data Warehouse während der ausgewählten Tageszeiten nicht auf Ihre verbundenen Datenbanken zugreift. Alle Stunden werden zur Nullstunde und in Eastern Standard Time (EST) angegeben. Wenn Sie beispielsweise nicht möchten, dass der Zugriff auf Ihre Produktionsdatenbank zwischen 9:00 Uhr EST und 13:00 Uhr EST erfolgt, sollten Sie das folgende Array von Ziffern eingeben: **9, 10, 11, 12**.

* **[!UICONTROL Forced update hours:]** Mit dieser Einstellung wird sichergestellt, dass ein Data Warehouse-Update automatisch in Ihrem Konto *während der von* angegebenen Zeiten) beginnt. Wie bei Blackout Hours sind diese auch in ET. Wenn Sie beispielsweise möchten, dass Data Warehouse-Updates automatisch um **Mitternacht** und **&#x200B;**&#x200B;Uhr EST beginnen, sollten Sie das folgende Ziffernarray eingeben: **0, 12**.

* **[!UICONTROL Send email summaries if the data has not updated yet:]** Mit dieser Option werden Situationen verwaltet, in denen eine E-Mail-Zusammenfassung gesendet werden soll *bevor die Daten in einem* aktualisiert werden. Wenn Sie **Nein** wählen, überspringt Ihr Konto den Versand der E-Mail zum geplanten Zeitpunkt. Stattdessen wird es von Ihrem Konto gesendet, sobald Ihre Daten aktualisiert wurden. Wenn Sie **[!UICONTROL Yes]** auswählen, sendet Ihr Konto die E-Mail, enthält eine Nachricht, in der erklärt wird, dass die Daten veraltet sind, und sendet eine weitere E-Mail, sobald Ihre Daten aktualisiert wurden.

* **[!UICONTROL Enable data updates:]** Mit dieser Option wird sichergestellt, dass Datenaktualisierungen in Ihrem Konto ausgeführt werden. Wenn Sie die Einstellung in **[!UICONTROL No]** ändern, werden die Datensynchronisierung und Spaltenberechnungen in Ihrem Konto angehalten.

>[!NOTE]
>
>Wählen Sie **[!UICONTROL Save Customizations]** aus, nachdem Sie Änderungen vorgenommen haben.
