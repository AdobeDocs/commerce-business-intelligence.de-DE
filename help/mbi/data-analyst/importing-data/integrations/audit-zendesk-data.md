---
title: Zendesk-Daten überprüfen
description: Erfahren Sie mehr über die Schritte zum Exportieren Ihrer Zendesk-Daten.
exl-id: 3c8dcc72-3623-4c4e-a941-f431a97571e0
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Zendesk-Daten überprüfen

Etwas Seltsames in Ihren [[!DNL Zendesk] Daten](../integrations/exp-zendesk-data.md) gefunden? Um das Problem zu identifizieren, müssen Sie Ihre Daten untersuchen. Exportieren Sie dazu Ihre [!DNL Zendesk] -Daten in eine herunterladbare Datei.

## Datenexport aktivieren

Der Datenexport ist derzeit nicht für alle [!DNL Zendesk] -Konten aktiviert. Um diese Funktion zu aktivieren, senden [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), in dem Ihr [!DNL Zendesk]-Subdomänenname erwähnt wird.

>[!NOTE]
>
>Nur `Enterprise`- und `Plus`-Pläne haben derzeit Zugriff auf diese Funktion.

Nachdem der Datenexport aktiviert wurde, können nur Administratoren einer bestimmten E-Mail-Domäne Daten aus Ihrem [!DNL Zendesk] -Konto exportieren. Diese E-Mail-Domäne ist normalerweise dieselbe E-Mail-Domäne wie Ihr [!DNL Zendesk]. Die E-Mail-Domäne des Kontoinhabers wird standardmäßig verwendet. Sie können die Domäne jedoch bei Bedarf ändern.

## In eine herunterladbare Datei exportieren

1. Klicken Sie auf das Admin-Symbol (Zahnradlogo) in der Seitenleiste und wählen Sie **[!UICONTROL Manage** > **Reports]** aus.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Export]** .
1. Klicken Sie neben &quot;Vollständiger XML-Export&quot;, wie in der Abbildung unten dargestellt, auf &quot;**[!UICONTROL Request file]**&quot;.

   An dieser Stelle beginnt ein Build. Sie werden per E-Mail benachrichtigt, wenn er abgeschlossen ist.
   ![reports_export_new.png](../../../assets/reports_export_new.png)

1. Klicken Sie auf den Link in Ihrer E-Mail-Benachrichtigung, um eine ZIP-Datei mit dem Bericht herunterzuladen.

   Dieser Downloadlink ist mindestens drei Tage lang gültig.

Dieser Prozess erstellt eine XML-Datei mit allen Informationen, die in Ihrem aktuellen [!DNL Zendesk]-Konto gespeichert sind, einschließlich Ticketdaten (mit Kommentaren), Benutzerdaten und Kontodaten. An dieser Stelle können Sie [ein Support-Ticket senden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) (hängen Sie diese Datei an!) damit Sie Ihre Daten genauer betrachten können. Wenn die Datei zu groß ist, geben Sie sie über [!DNL Dropbox] oder [!DNL Google Drive] für das [!DNL Commerce Intelligence]-Team frei.

Weitere Informationen zu [!DNL Zendesk] -Dateiexporten finden Sie in der offiziellen [[!DNL Zendesk] Exportdokumentation](https://support.zendesk.com/hc/en-us/articles/4408886165402-Exporting-data-to-a-JSON-CSV-or-XML-file).
