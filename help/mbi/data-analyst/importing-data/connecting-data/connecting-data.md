---
title: Verbinden von Daten
description: Erfahren Sie, wie Sie die Tabellen durchsuchen, die für die Synchronisierung im Data Warehouse Manager verfügbar sind.
exl-id: 94beba8b-6a86-4af9-87fb-96b1cf8f8fa2
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Verbinden von Daten

[!DNL Adobe Commerce Intelligence] werden Datenquellen als `integrations` bezeichnet. Nachdem eine `integration` erfolgreich verbunden wurde, können Sie die Tabellen durchsuchen, die für die Synchronisierung im Data Warehouse Manager verfügbar sind.

Integrationen werden über die Seite `Connections` hinzugefügt und verwaltet, auf die durch Klicken auf **[!UICONTROL Manage Data** > **Connections]** zugegriffen werden kann. Hier sehen Sie:

* Eine Liste aller mit Ihrem Konto verbundenen Integrationen

* Der Integrationstyp

* Status ([!DNL Google Analytics] und [!DNL Data Import API] Verbindungen haben leere Statusfelder)

* Das letzte Mal, dass ein Verbindungstest (`Last Connection Started` Spalte) durchgeführt wurde

![data\_sources\_table.png](../../../assets/Data_Sources_Table.png)

## Integrationstypen

Es gibt vier Möglichkeiten, Ihre Daten in [!DNL Commerce Intelligence] zu übertragen: eine Datenbank verbinden, eine SaaS-Integration verbinden, eine `.csv` hochladen oder die Adobe-API verwenden.

## Datenbankintegrationen

![Database\_icons.jpg](../../../assets/Database_icons.jpg)

[!DNL Commerce Intelligence] unterstützt SQL-basierte und NoSQL-Datenbanken wie [MySQL](../../importing-data/integrations/mysql-via-ssh-tunnel.md), [Microsoft SQL](../integrations/microsoft-sql-server.md), [MongoDB](../integrations/mongodb-via-ssh-tunnel.md) und [PostgreSQL](../integrations/postgresql.md).

Adobe empfiehlt, eine bewährte Verschlüsselungsmethode wie einen SSH-Tunnel zu verwenden, auch wenn Sie Ihre Datenbank mithilfe der Datenbankanmeldeinformationen direkt mit [!DNL Commerce Intelligence] verbinden können. Dadurch wird sichergestellt, dass Ihre Daten beim Eintritt in Ihre Data Warehouse sicher bleiben.

Je nach Verbindungsmethode und Datenbanktyp sind möglicherweise technische Kenntnisse erforderlich, um die Einrichtung abzuschließen.

## `SaaS` Integrationen

![](../../../assets/SaaS_icons.jpg)spree-commerce-logo.png

`SaaS` Integrationen sind Services wie [[!DNL Google Adwords]](../integrations/google-adwords.md), [[!DNL Salesforce]](../integrations/salesforce.md) und [[!DNL Zendesk]](../integrations/zendesk.md). Da sich Daten von Drittanbietern auf dem Server des Anbieters befinden, können Sie nicht direkt darauf zugreifen, wie Sie es mit den Daten in Ihrer Datenbank tun können.

Normalerweise ist das Einrichten einer Integration in [!DNL Commerce Intelligence] so einfach wie das Eingeben Ihrer Kontoanmeldeinformationen. Einige Dienste benötigen möglicherweise einen API-Schlüssel, um die Autorisierung abzuschließen. Anweisungen zum Generieren [ benötigten Anmeldeinformationen finden ](../integrations/integrations.md) im Abschnitt „Integrationen“.

## Datei-Upload

Sie sind sich nicht sicher, wie Sie Daten aus einer zusätzlichen Quelle in Ihre Data Warehouse übertragen können? [Die Verwendung der `File Upload`-Funktion](../connecting-data/using-file-uploader.md) ist eine gute Möglichkeit, Daten abzurufen, die Sie für die alltägliche Entscheidungsfindung nicht benötigen. Nach den Formatierungsregeln können Sie `.csv` Dateien schnell in Ihre Data Warehouse hochladen und mit anderen Datenquellen verbinden.

## [!DNL Commerce Intelligence] `Import API`

Wenn Sie den Abruf von Daten aus einer Ihrer eigenen Quellen automatisieren möchten, können Sie die [!DNL Commerce Intelligence] `Import API` verwenden. Grundsätzlich gilt: Wenn es sich nicht in einer Datenbank oder einer `SaaS`-Integration befindet, ist die `Import API` die beste Wahl.

Die Verwendung der API erfordert ein wenig technisches Know-how - jemand, der mit dem Schreiben und Verwalten eines kleinen Ruby- oder PHP-Skripts vertraut ist, ist mehr als qualifiziert.

Weitere Informationen zu den ersten Schritten mit dem `Import API` finden Sie auf der [Entwickler-Site](https://developer.adobe.com/commerce/services/reporting/) und [So generieren Sie einen API-Schlüssel](https://developer.adobe.com/commerce/services/reporting/import-api/).

## Hinzufügen einer Integration

Um eine Integration hinzuzufügen, klicken Sie auf **[!UICONTROL Manage Data** > **Connections]** und dann auf **[!UICONTROL Add a New Data Source]**. Klicken Sie auf das Symbol der Integration, die Sie hinzufügen möchten, und befolgen Sie die Anweisungen in den Hilfethemen, um Dinge einzurichten:

* [Häufig gestellte Fragen zur Integration](https://support.magento.com/hc/en-us/sections/360003161871-Integration-FAQ)
* [Verfügbar ](../integrations/integrations.md)
* [Konsolidieren von Tabellen](../../../best-practices/consolidating-your-tables.md)
* [Beschränken des Zugriffs auf die Datenbank](../../../administrator/account-management/restrict-db-access.md)

**Sie eine Integration nicht sehen, die Sie möchten?** Einige Integrationen müssen aktiviert werden, damit sie in Ihrem Konto sichtbar sind. Wenn Sie nach etwas wie [!DNL Facebook] suchen, es aber nicht aufgeführt ist, [ Sie ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

**Wenn Sie einen Fehlerstatus für eine Integration sehen** finden Sie im Abschnitt [Fehlerbehebung](https://support.magento.com/hc/en-us/sections/360003078151) Hilfe.
