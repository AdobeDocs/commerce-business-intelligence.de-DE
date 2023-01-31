---
title: Kontoeinstellungen verwalten
description: Erfahren Sie, wie Sie eine Reihe von Kontoeinstellungen für Ihr Data Warehouse anpassen können.
exl-id: 847d51b1-287e-4c14-b64e-0bd9bfcccedc
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Kontoeinstellungen anpassen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen.](../../administrator/user-management/user-management.md)

In [!DNL MBI] -Konto können Sie eine Reihe von Kontoeinstellungen für Ihr Data Warehouse anpassen. Sie können darauf zugreifen, indem Sie Ihren Organisationsnamen in der oberen rechten Ecke eines beliebigen Bildschirms auswählen und dann **[!UICONTROL Account Settings]** aus dem Dropdown-Menü aus.

* **[!UICONTROL Client Name:]** Diese Einstellung wird in der oberen rechten Ecke aller Dashboards und an anderer Stelle in Ihrem Konto angezeigt. Wenn Sie sich ändern möchten **[!UICONTROL "Vandelay Industries Co., Ltd]** nur **[!UICONTROL "Vandelay]**, ist dies der Ort, um dies zu tun.

* **[!UICONTROL Currency:]** Dies ist die *Standardwährung* für alle Geldwerte in Ihrem Konto. Jedes Mal, wenn ein Dezimalwert oder ein Währungswert mit Ihrem Data Warehouse synchronisiert wird, bestimmt diese Einstellung das Symbol, das vor diesem Wert in Ihren Berichten platziert wird.

* **[!UICONTROL Blackout Hours:]** Diese Einstellung stellt sicher, dass Ihr Data Warehouse während der ausgewählten Tageszeiten nicht auf Ihre verbundenen Datenbanken zugreift. Alle Stunden werden als Nullstunde und in Eastern Standard Time (EST) ausgedrückt. Wenn Sie beispielsweise nicht möchten, dass zwischen 9:00 Uhr EST und 13:00 Uhr EST auf Ihre Produktionsdatenbank zugegriffen wird, geben Sie das folgende Ziffernarray ein: **9, 10, 11, 12**.

* **[!UICONTROL Forced update hours:]** Diese Einstellung stellt sicher, dass in Ihrem Konto automatisch eine Data Warehouse-Aktualisierung beginnt *Stunden* angegeben haben. Wie bei Blackout-Stunden befinden sich auch diese in ET. Beispiel: Sie möchten, dass Data Warehouse-Aktualisierungen automatisch am **Mitternacht** und **Mittag** EST: Sie sollten das folgende Ziffernarray eingeben: **0, 12**.

* **[!UICONTROL Send email summaries if the data has not updated yet:]** Diese Option teilt dem System mit, was in Situationen zu tun ist, in denen eine E-Mail-Zusammenfassung für den Versand geplant ist *vor den Daten in einem seiner Berichte* wird bis zur Gegenwart aktualisiert. Wenn Sie **Nein**, überspringt Ihr Konto den Versand der E-Mail zum geplanten Zeitpunkt und sendet sie stattdessen, sobald Ihre Daten aktualisiert wurden. Wenn Sie **[!UICONTROL Yes]** senden, sendet Ihr Konto die E-Mail, fügt eine Meldung mit dem Hinweis ein, dass die Daten veraltet sind, und sendet eine weitere E-Mail, sobald Ihre Daten aktualisiert wurden.

* **[!UICONTROL Enable data updates:]** Mit dieser Option wird sichergestellt, dass Datenaktualisierungen für Ihr Konto ausgeführt werden. Wenn Sie die Einstellung auf **[!UICONTROL No]**, werden Datensynchronisationen und Spaltenberechnungen in Ihrem Konto vollständig angehalten.

>[!NOTE]
>
>Wählen Sie **[!UICONTROL Save Customizations]** nachdem Sie Änderungen vorgenommen haben.
