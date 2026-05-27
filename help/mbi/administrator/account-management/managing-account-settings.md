---
title: Kontoeinstellungen verwalten
description: Erfahren Sie, wie Sie Ihre Kontoeinstellungen für Ihre Data Warehouse anpassen.
exl-id: 847d51b1-287e-4c14-b64e-0bd9bfcccedc
role: Admin, User
feature: Accounts
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b6935462-7263-4ced-a703-60de6a5aeb2d
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
subfeature_v2:
  - id: a763c1a2-1d0a-40d7-9617-8139636fd12e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4e01225a6bd285afbe988b9c24e07e2ea34649fc
workflow-type: tm+mt
source-wordcount: 352
ht-degree: 0%

---

# Anpassen der Kontoeinstellungen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen.](../../administrator/user-management/user-management.md)

In Ihrem [!DNL Commerce Intelligence] können Sie Ihre Kontoeinstellungen für Ihre Data Warehouse anpassen. Sie können auf diese zugreifen, indem Sie in der oberen rechten Ecke eines beliebigen Bildschirms auf den Namen Ihres Unternehmens und anschließend im Dropdown-Menü auf **[!UICONTROL Account Settings]** klicken.

* **[!UICONTROL Client Name:]** Diese Einstellung wird in der oberen rechten Ecke aller Dashboards und überall in Ihrem Konto angezeigt. Wenn Sie **[!UICONTROL "Vandelay Industries Co., Ltd]** einfach in **[!UICONTROL "Vandelay]** ändern möchten, hier ist der richtige Weg.

* **[!UICONTROL Currency:]** Dies ist die *Standardwährung* für alle Geldwerte in Ihrem Konto. Jedes Mal, wenn ein Dezimal- oder Währungswert mit Ihrer Data Warehouse synchronisiert wird, bestimmt diese Einstellung, welches Symbol in Ihren Berichten vor diesem Wert platziert wird.

* **[!UICONTROL Blackout Hours:]** Mit dieser Einstellung wird sichergestellt, dass Ihre Data Warehouse während der ausgewählten Tageszeiten nicht auf Ihre verbundenen Datenbanken zugreift. Alle Stunden werden zur Nullstunde und in Eastern Standard Time (EST) angegeben. Wenn Sie beispielsweise nicht möchten, dass der Zugriff auf Ihre Produktionsdatenbank zwischen 9:00 :00 EST und 13:00 :00 EST erfolgt, sollten Sie das folgende Ziffernarray eingeben: **9, 10, 11, 12**.

* **[!UICONTROL Forced update hours:]** Mit dieser Einstellung wird sichergestellt, dass ein Data Warehouse-Update automatisch in Ihrem Konto *während der von* angegebenen Zeiten) beginnt. Wie bei Blackout Hours sind diese auch in ET. Wenn Data Warehouse-Aktualisierungen beispielsweise automatisch um 12:00 **12:** und **:** EST beginnen sollen, sollten Sie das folgende Ziffernarray eingeben: **0, 12**.

* **[!UICONTROL Send email summaries if the data has not updated yet:]** Mit dieser Option werden Situationen verwaltet, in denen eine E-Mail-Zusammenfassung gesendet werden soll *bevor die Daten in einem* aktualisiert werden. Wenn Sie **Nein** wählen, überspringt Ihr Konto den Versand der E-Mail zum geplanten Zeitpunkt. Stattdessen wird es von Ihrem Konto gesendet, sobald Ihre Daten aktualisiert wurden. Wenn Sie **[!UICONTROL Yes]** auswählen, sendet Ihr Konto die E-Mail, enthält eine Nachricht, in der erklärt wird, dass die Daten veraltet sind, und sendet eine weitere E-Mail, sobald Ihre Daten aktualisiert wurden.

* **[!UICONTROL Enable data updates:]** Mit dieser Option wird sichergestellt, dass Datenaktualisierungen in Ihrem Konto ausgeführt werden. Wenn Sie die Einstellung in **[!UICONTROL No]** ändern, werden die Datensynchronisierung und Spaltenberechnungen in Ihrem Konto angehalten.

>[!NOTE]
>
>Wählen Sie **[!UICONTROL Save Customizations]** aus, nachdem Sie Änderungen vorgenommen haben.
