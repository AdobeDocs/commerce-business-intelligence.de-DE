---
title: Zendesk-Daten überprüfen
description: Erfahren Sie mehr über die Schritte zum Exportieren Ihrer Zendesk-Daten.
exl-id: 3c8dcc72-3623-4c4e-a941-f431a97571e0
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Zendesk-Daten überprüfen

Etwas Seltsames in Ihrem [[!DNL Zendesk] data](../integrations/exp-zendesk-data.md)? Um das Problem zu identifizieren, müssen Sie Ihre Daten untersuchen. Dies kann durch Exportieren Ihrer [!DNL Zendesk] Daten in eine herunterladbare Datei.

## Datenexport aktivieren

Der Datenexport ist derzeit nicht für alle [!DNL Zendesk] Konten. So aktivieren Sie diese Funktion: [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), die Ihre [!DNL Zendesk] Name der Subdomäne.

>[!NOTE]
>
>Nur `Enterprise` und `Plus` Pläne haben derzeit Zugriff auf diese Funktion.

Nachdem der Datenexport aktiviert wurde, können nur Administratoren einer bestimmten E-Mail-Domäne Daten aus Ihrer [!DNL Zendesk] -Konto. Diese E-Mail-Domäne ist normalerweise dieselbe E-Mail-Domäne wie Ihre [!DNL Zendesk]. Die E-Mail-Domäne des Kontoinhabers wird standardmäßig verwendet. Sie können die Domäne jedoch bei Bedarf ändern.

## In eine herunterladbare Datei exportieren

1. Klicken Sie auf das Admin-Symbol (Zahnradlogo) in der Seitenleiste und wählen Sie **[!UICONTROL Manage** > **Reports]**.
1. Klicken Sie auf **[!UICONTROL Export]** Registerkarte.
1. Klicken **[!UICONTROL Request file]** neben &quot;Vollständiger XML-Export&quot;, wie in der Abbildung unten dargestellt.

   Ab diesem Zeitpunkt beginnt ein Build. Sie werden per E-Mail benachrichtigt, wenn sie abgeschlossen ist.
   ![reports_export_new.png](../../../assets/reports_export_new.png)

1. Klicken Sie auf den Link in Ihrer E-Mail-Benachrichtigung, um eine ZIP-Datei mit dem Bericht herunterzuladen.

   Dieser Downloadlink ist mindestens drei Tage lang gültig.

Dieser Prozess erstellt eine XML-Datei, die alle in Ihrer aktuellen [!DNL Zendesk] -Konto, einschließlich Ticketdaten (mit Kommentaren), Benutzerdaten und Kontodaten. An dieser Stelle können Sie [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) (Achten Sie darauf, diese Datei anzuhängen!) damit Sie Ihre Daten genauer betrachten können. Wenn die Datei zu groß ist, teilen Sie sie mit der [!DNL Commerce Intelligence] Team via [!DNL Dropbox] oder [!DNL Google Drive].

Weitere Informationen finden Sie unter [!DNL Zendesk] Dateiexporte, siehe [[!DNL Zendesk] Exportdokumentation](https://support.zendesk.com/hc/en-us/articles/4408886165402-Exporting-data-to-a-JSON-CSV-or-XML-file).
