---
title: Daten verbinden
description: Erfahren Sie, wie Sie die Tabellen durchsuchen, die im Data Warehouse Manager für die Synchronisierung verfügbar sind.
exl-id: 94beba8b-6a86-4af9-87fb-96b1cf8f8fa2
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Daten verbinden

In [!DNL MBI], werden Datenquellen aufgerufen. `integrations`. Nach `integration` erfolgreich verbunden ist, können Sie die Tabellen durchsuchen, die im Data Warehouse Manager für die Synchronisierung verfügbar sind.

Integrationen werden hinzugefügt und mithilfe der `Connections` Seite, auf die durch Klicken auf **[!UICONTROL Manage Data** > **Connections]**. Hier sehen Sie eine Liste aller mit Ihrem Konto verbundenen Integrationen, den Integrationstyp, den Status ([!DNL Google Analytics] und [!DNL Data Import API] -Verbindungen haben leere Statusfelder) und das letzte Mal, wenn ein Verbindungstest (`Last Connection` Spalte &quot;Gestartet&quot;) ausgeführt wurde.

![data\_sources\_table.png](../../../assets/Data_Sources_Table.png)

## Integrationstypen

Es gibt vier Möglichkeiten, Ihre Daten zu integrieren [!DNL MBI]: eine Datenbank verbinden, eine SaaS-Integration verbinden, eine `.csv` oder verwenden Sie unsere API.

## Datenbankintegrationen

![Database\_icons.jpg](../../../assets/Database_icons.jpg)

[!DNL MBI] unterstützt SQL-basierte und NoSQL-Datenbanken wie [MySQL](../../importing-data/integrations/mysql-via-ssh-tunnel.md), [Microsoft SQL](../integrations/microsoft-sql-server.md), [MongoDB](../integrations/mongodb-via-ssh-tunnel.md)und [PostgreSQL](../integrations/postgresql.md).

Während Sie Ihre Datenbank direkt mit [!DNL MBI] Verwenden Sie Datenbankberechtigungen. Wir empfehlen Ihnen, eine bewährte Verschlüsselungsmethode wie einen SSH-Tunnel zu verwenden. Dadurch wird sichergestellt, dass Ihre Daten beim Eintritt in Ihr Data Warehouse sicher und sicher bleiben.

Je nach Verbindungsmethode und Datenbanktyp ist möglicherweise technisches Know-how erforderlich, um die Einrichtung abzuschließen.

## `SaaS` Integrationen

![](../../../assets/SaaS_icons.jpg)

`SaaS` Integrationen sind Dienste wie [[!DNL Google Adwords]](../integrations/google-adwords.md), [[!DNL Salesforce]](../integrations/salesforce.md)und [[!DNL Zendesk]](../integrations/zendesk.md). Da Drittanbieterdaten auf dem Server des Anbieters gespeichert sind, können Sie mit den Daten in Ihrer Datenbank nicht direkt darauf zugreifen.

In den meisten Fällen können Sie eine Integration in [!DNL MBI] ist so einfach wie die einfache Eingabe Ihrer Kontoanmeldeinformationen. Einige Dienste benötigen möglicherweise einen API-Schlüssel, um die Autorisierung abzuschließen. Sehen Sie sich dazu die [Integrationsabschnitt](../integrations/integrations.md) für Anweisungen zum Generieren der benötigten Anmeldeinformationen.

## Datei-Upload

Sie wissen nicht genau, wie Sie Daten von einer zusätzlichen Quelle in Ihr Data Warehouse übertragen können. [Verwenden der `File Upload` Funktion](../connecting-data/using-file-uploader.md) ist eine gute Möglichkeit, Daten abzurufen, die Sie für die tägliche Entscheidungsfindung nicht benötigen. Nach unseren Formatierungsregeln können Sie schnell hochladen `.csv` -Dateien in Ihr Data Warehouse und verbinden Sie sie mit anderen Datenquellen.

## [!DNL MBI] `Import API`

Wenn Sie den Abruf von Daten aus einer Ihrer eigenen Quellen lieber automatisieren möchten, können Sie die [!DNL MBI] `Import API`. Grundsätzlich: wenn sie sich nicht in einer Datenbank oder einer `SaaS` Integration, `Import API` -Funktion ist Ihre beste Wette.

Die Verwendung der API erfordert ein wenig technisches Know-how - jemand, der sich mit dem Schreiben und Verwalten eines kleinen Ruby- oder PHP-Skripts auskennt, ist mehr als qualifiziert.

Weitere Informationen zu den ersten Schritten mit dem `Import API`, sehen Sie sich die [Entwicklersite](https://developer.adobe.com/commerce/services/reporting/) und [Erstellen eines API-Schlüssels](https://developer.adobe.com/commerce/services/reporting/import-api/).

## Hinzufügen einer Integration

Um eine Integration hinzuzufügen, klicken Sie auf **[!UICONTROL Manage Data** > **Connections]** und klicken Sie anschließend auf **[!UICONTROL Add a New Data Source]**. Klicken Sie auf das Symbol der Integration, die Sie hinzufügen möchten, und befolgen Sie die Anweisungen in unseren Hilfeartikeln, um Elemente einzurichten:

* [Integrations-FAQs](https://support.magento.com/hc/en-us/sections/360003161871-Integration-FAQ)
* [Verfügbar ](../integrations/integrations.md)
* [Tabellen konsolidieren](../../../best-practices/consolidating-your-tables.md)
* [Einschränken des Zugriffs auf Ihre Datenbank](../../../administrator/account-management/restrict-db-access.md)

**Sie sehen keine gewünschte Integration?** Einige Integrationen müssen aktiviert sein, damit sie in Ihrem Konto sichtbar sind. Wenn Sie etwas suchen - zum Beispiel [!DNL Facebook] - aber nicht aufgeführt ist; [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).

**Wenn ein Fehlerstatus für eine Integration angezeigt wird**, nicht panisch - sehen Sie sich die [Abschnitt zur Fehlerbehebung](https://support.magento.com/hc/en-us/sections/360003078151) für Hilfe.
