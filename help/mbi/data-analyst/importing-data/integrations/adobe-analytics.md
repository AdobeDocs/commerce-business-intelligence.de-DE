---
title: Adobe Analytics verbinden
description: Erfahren Sie, wie Sie den End-to-End-Journey-Fokus von  [!DNL Adobe Analytics]  und den E-Commerce-Fokus von zusammenführen [!DNL Commerce Intelligence].
exl-id: 824e1ee4-6b88-42f7-b265-29330dbc4407
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/KkiKySM2q8ewqhQ1kdUjLuTM4iOpzrZb5Ok-UvBBpJE
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
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 326
ht-degree: 0%

---

# [!DNL Adobe Analytics] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Adobe Analytics-Logo](../../../assets/adobe-analytic-slogo.png)

Die [!DNL Adobe Analytics] Integration für [!DNL Adobe Commerce Intelligence] ermöglicht es Ihnen, den End-to-End-Kunden-Journey-Fokus von [!DNL Adobe Analytics] und den E-Commerce-Fokus von [!DNL Commerce Intelligence] zusammenzuführen. Dadurch erhalten Sie einen vollständigen Überblick über die Gesamtleistung Ihres Stores.

Genauer gesagt bietet die [!DNL Adobe Analytics]-Integration für [!DNL Commerce Intelligence] Funktionen, mit denen Händler ihre [!DNL Adobe Commerce] und [!DNL Adobe Analytics] Datensätze kombinieren können.

- Erstellen Sie eine Verbindung von Ihrem bestehenden [!DNL Adobe Analytics]-Konto in [!DNL Commerce Intelligence].

- Wählen Sie bis zu 25 Metriken und Dimensionen aus einer Report Suite aus, die in Ihre Data Warehouse repliziert werden sollen.

- Verwenden Sie alle standardmäßigen [!DNL Commerce Intelligence], um replizierte [!DNL Adobe Analytics]-Daten zu transformieren, zusammenzuführen und Berichte dazu zu erstellen.

## Voraussetzungen für die Verbindung

Die folgenden Informationen werden für die Verbindung benötigt:

- [!DNL Adobe Analytics] Anmeldedaten

- `Name` und/oder `ID` [!DNL Adobe Analytics] Report Suite, aus der Daten repliziert werden sollen

- Liste der Metriken und Dimensionen, die nach [!DNL Commerce Intelligence] repliziert werden sollen

## Verbinden der [!DNL Adobe Analytics] für [!DNL Commerce Intelligence]

1. Navigieren Sie zur `Integrations` unter **[!DNL Manage Data** > **Integrations]**.

1. Klicken Sie auf **[!UICONTROL Add an Integration]**.

1. Klicken Sie auf das Symbol **[!UICONTROL Adobe Analytics]** , um auf die Seite zuzugreifen, auf der Sie die Verbindung Ihres [!DNL Adobe Analytics] Kontos autorisieren können.

1. Klicken Sie auf **[!UICONTROL Authorize with Adobe Analytics]**.

1. Geben Sie Ihre [!DNL Adobe Analytics] ein. Nach erfolgreicher Autorisierung werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.

1. Eine Liste der verfügbaren Report Suites wird angezeigt. Wählen Sie die Report Suite aus, aus der Sie die Daten importieren möchten, und klicken Sie dann auf **[!UICONTROL Continue]**.

1. Der Bildschirm zur Auswahl von Metriken und Dimensionen wird angezeigt. Wählen Sie mindestens eine Metrik und mindestens eine Dimension aus, bis zu einer kombinierten Summe von 25 Metriken und Dimensionen. Suchen Sie nach Namen oder scrollen Sie, um Ihre Komponenten zu finden, und klicken Sie dann auf die Kontrollkästchen, um sie auszuwählen. Klicken Sie auf **[!UICONTROL Continue]**.

1. Die ausgewählte Report Suite wird in einer Tabelle angezeigt. Klicken Sie auf **[!UICONTROL Save]** , um Ihre Auswahl zu bestätigen.

1. Informieren Sie das [!DNL Commerce Intelligence] [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)Team, dass Ihre Integration autorisiert ist, und es führt den ersten Verbindungsprozess für Sie aus.

Nachdem der anfängliche Verbindungsprozess ausgeführt wurde, ist Ihre Tabelle auf der Data Warehouse-Seite auf der Registerkarte `All Tables` verfügbar. Wählen Sie die Spalten aus, die Sie replizieren möchten, und die Daten werden nach der nächsten vollständigen Aktualisierung angezeigt.
