---
title: Audit von Zendesk-Daten
description: Erfahren Sie, wie Sie Ihre Zendesk-Daten exportieren.
exl-id: 3c8dcc72-3623-4c4e-a941-f431a97571e0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Audit von Zendesk-Daten

Etwas Seltsames in Ihren [[!DNL Zendesk] Daten](../integrations/exp-zendesk-data.md) gefunden? Um das Problem zu identifizieren, müssen Sie Ihre Daten untersuchen. Exportieren Sie dazu Ihre [!DNL Zendesk] in eine herunterladbare Datei.

## Aktivieren des Datenexports

Der Datenexport ist derzeit nicht für alle [!DNL Zendesk]-Konten aktiviert. Um diese Funktion zu aktivieren, [ Sie „ein Support-Ticket ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)&quot; und geben Sie Ihren [!DNL Zendesk] Subdomain-Namen an.

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

Dieser Prozess erstellt eine XML-Datei, die alle im aktuellen [!DNL Zendesk] gespeicherten Informationen enthält, einschließlich Ticketdaten (mit Kommentaren), Benutzerdaten und Kontodaten. An dieser Stelle können Sie [ein Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) (fügen Sie unbedingt diese Datei bei!), damit Sie sich Ihre Daten genauer ansehen können. Wenn die Datei zu groß ist, geben Sie sie über [!DNL Dropbox] oder [!DNL Google Drive] für das [!DNL Commerce Intelligence]-Team frei.

Weitere Informationen zu [!DNL Zendesk] Dateiexporten finden Sie in der offiziellen [[!DNL Zendesk] Exportdokumentation](https://support.zendesk.com/hc/en-us/articles/4408886165402-Exporting-data-to-a-JSON-CSV-or-XML-file).
