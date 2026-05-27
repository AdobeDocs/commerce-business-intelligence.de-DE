---
title: Audit von Zendesk-Daten
description: Erfahren Sie, wie Sie Ihre Zendesk-Daten exportieren.
exl-id: 3c8dcc72-3623-4c4e-a941-f431a97571e0
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/EQmiSbzzvOONQ8-F1U9uMVpgXUKd2PEjcLXLVSgQSm8
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
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
source-wordcount: 306
ht-degree: 0%

---

# Audit von Zendesk-Daten

Etwas Seltsames in Ihren [[!DNL Zendesk] Daten](../integrations/exp-zendesk-data.md) gefunden? Um das Problem zu identifizieren, müssen Sie Ihre Daten untersuchen. Exportieren Sie dazu Ihre [!DNL Zendesk] in eine herunterladbare Datei.

## Aktivieren des Datenexports

Der Datenexport ist derzeit nicht für alle [!DNL Zendesk]-Konten aktiviert. Um diese Funktion zu aktivieren, [&#x200B; Sie „ein Support-Ticket &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)&quot; und geben Sie Ihren [!DNL Zendesk] Subdomain-Namen an.

>[!NOTE]
>
>Nur `Enterprise` und `Plus` Pläne haben derzeit Zugriff auf diese Funktion.

Nachdem der Datenexport aktiviert wurde, können nur Administratoren in einer bestimmten E-Mail-Domain Daten aus Ihrem [!DNL Zendesk]-Konto exportieren. Diese E-Mail-Domain ist in der Regel dieselbe E-Mail-Domain wie Ihre [!DNL Zendesk]. Standardmäßig wird die E-Mail-Domain des Kontoinhabers verwendet. Sie können die Domain jedoch bei Bedarf ändern.

## Exportieren in eine herunterladbare Datei

1. Klicken Sie auf das Admin-Symbol (Zahnradlogo) in der Seitenleiste und wählen Sie **[!UICONTROL Manage** > **Reports]**.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Export]** .
1. Klicken Sie neben Vollständiger XML-Export auf **[!UICONTROL Request file]** , wie in der Abbildung unten dargestellt.

   An dieser Stelle beginnt ein Build. Sie werden per E-Mail benachrichtigt, wenn er abgeschlossen ist.
   ![reports_export_new.png](../../../assets/reports_export_new.png)

1. Klicken Sie auf den Link in Ihrer E-Mail-Benachrichtigung, um eine ZIP-Datei mit dem Bericht herunterzuladen.

   Dieser Downloadlink ist mindestens drei Tage gültig.

Dieser Prozess erstellt eine XML-Datei, die alle im aktuellen [!DNL Zendesk] gespeicherten Informationen enthält, einschließlich Ticketdaten (mit Kommentaren), Benutzerdaten und Kontodaten. An dieser Stelle können Sie [ein Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) (stellen Sie sicher, dass Sie diese Datei anhängen!) So können Sie sich Ihre Daten genauer ansehen. Wenn die Datei zu groß ist, geben Sie sie über [!DNL Dropbox] oder [!DNL Google Drive] für das [!DNL Commerce Intelligence]-Team frei.

Weitere Informationen zu [!DNL Zendesk] Dateiexporten finden Sie in der offiziellen [[!DNL Zendesk] Exportdokumentation](https://support.zendesk.com/hc/en-us/articles/4408886165402-Exporting-data-to-a-JSON-CSV-or-XML-file).
