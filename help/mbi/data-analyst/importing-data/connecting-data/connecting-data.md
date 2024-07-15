---
title: Daten verbinden
description: Erfahren Sie, wie Sie die Tabellen durchsuchen, die im Data Warehouse-Manager synchronisiert werden können.
exl-id: 94beba8b-6a86-4af9-87fb-96b1cf8f8fa2
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Daten verbinden

In [!DNL Adobe Commerce Intelligence] werden Datenquellen als `integrations` bezeichnet. Nachdem eine `integration` -Verbindung erfolgreich hergestellt wurde, können Sie die Tabellen durchsuchen, die im Data Warehouse-Manager für die Synchronisierung verfügbar sind.

Integrationen werden über die Seite `Connections` hinzugefügt und verwaltet, auf die durch Klicken auf **[!UICONTROL Manage Data** > **Connections]** zugegriffen werden kann. Hier sehen Sie:

* eine Liste aller mit Ihrem Konto verbundenen Integrationen

* Integrationstyp

* Status ([!DNL Google Analytics] - und [!DNL Data Import API] -Verbindungen haben leere Statusfelder)

* der letzten Durchführung eines Verbindungstests (`Last Connection Started` -Spalte)

![data\_sources\_table.png](../../../assets/Data_Sources_Table.png)

## Integrationstypen

Es gibt vier Möglichkeiten, Ihre Daten in [!DNL Commerce Intelligence] zu übertragen: eine Datenbank zu verbinden, eine SaaS-Integration zu verbinden, eine `.csv` -Datei hochzuladen oder die Adobe-API zu verwenden.

## Datenbankintegrationen

![Database\_icons.jpg](../../../assets/Database_icons.jpg)

[!DNL Commerce Intelligence] unterstützt SQL-basierte und NoSQL-Datenbanken wie [MySQL](../../importing-data/integrations/mysql-via-ssh-tunnel.md), [Microsoft SQL](../integrations/microsoft-sql-server.md), [MongoDB](../integrations/mongodb-via-ssh-tunnel.md) und [PostgreSQL](../integrations/postgresql.md).

Sie können Ihre Datenbank zwar direkt mit [!DNL Commerce Intelligence] über Datenbankberechtigungen verbinden, Adobe empfiehlt jedoch die Verwendung einer bewährten Verschlüsselungsmethode wie einem SSH-Tunnel. Dadurch wird sichergestellt, dass Ihre Daten sicher und sicher bleiben, während sie in Ihre Data Warehouse gelangen.

Abhängig von der Verbindungsmethode und dem Datenbanktyp kann ein gewisser technischer Sachverstand erforderlich sein, um die Einrichtung abzuschließen.

## `SaaS` Integrationen

![](../../../assets/SaaS_icons.jpg)spree-commerce-logo.png

`SaaS` Integrationen sind Dienste wie [[!DNL Google Adwords]](../integrations/google-adwords.md), [[!DNL Salesforce]](../integrations/salesforce.md) und [[!DNL Zendesk]](../integrations/zendesk.md). Da Daten von Drittanbietern auf dem Server des Anbieters gespeichert sind, können Sie mit den Daten in Ihrer Datenbank nicht direkt darauf zugreifen.

In der Regel ist das Einrichten einer Integration in [!DNL Commerce Intelligence] so einfach wie das einfache Eingeben Ihrer Kontoanmeldeinformationen. Einige Dienste benötigen möglicherweise einen API-Schlüssel, um die Autorisierung abzuschließen. Anweisungen zum Generieren benötigter Anmeldeinformationen finden Sie im Abschnitt [Integrationen](../integrations/integrations.md) .

## Datei-Upload

Sie wissen nicht genau, wie Sie Daten von einer zusätzlichen Quelle in Ihre Data Warehouse bekommen? [Die Verwendung der `File Upload`-Funktion](../connecting-data/using-file-uploader.md) ist eine gute Möglichkeit, Daten abzurufen, die Sie für die tägliche Entscheidungsfindung nicht benötigen. Nach den Formatierungsregeln können Sie schnell `.csv` -Dateien in Ihre Data Warehouse hochladen und sie mit anderen Datenquellen verbinden.

## [!DNL Commerce Intelligence] `Import API`

Wenn Sie den Abruf von Daten aus einer Ihrer eigenen Quellen lieber automatisieren möchten, können Sie die [!DNL Commerce Intelligence] `Import API` verwenden. Wenn es sich nicht um eine Datenbank- oder eine `SaaS`-Integration handelt, ist die `Import API`-Funktion die beste Wette.

Die Verwendung der API erfordert ein wenig technisches Know-how - jemand, der sich mit dem Schreiben und Verwalten eines kleinen Ruby- oder PHP-Skripts auskennt, ist mehr als qualifiziert.

Weitere Informationen zu den ersten Schritten mit dem `Import API` finden Sie auf der [Entwickler-Site](https://developer.adobe.com/commerce/services/reporting/) und auf der [, wie Sie einen API-Schlüssel generieren](https://developer.adobe.com/commerce/services/reporting/import-api/).

## Hinzufügen einer Integration

Um eine Integration hinzuzufügen, klicken Sie auf **[!UICONTROL Manage Data** > **Connections]** und dann auf **[!UICONTROL Add a New Data Source]**. Klicken Sie auf das Symbol der Integration, die Sie hinzufügen möchten, und befolgen Sie die Anweisungen in den Hilfethemen, um Elemente einzurichten:

* [Häufig gestellte Fragen zur Integration](https://support.magento.com/hc/en-us/sections/360003161871-Integration-FAQ)
* [Verfügbar ](../integrations/integrations.md)
* [Tabellen konsolidieren](../../../best-practices/consolidating-your-tables.md)
* [Einschränken des Zugriffs auf Ihre Datenbank](../../../administrator/account-management/restrict-db-access.md)

**Sie sehen keine gewünschte Integration?** Einige Integrationen müssen aktiviert sein, damit sie in Ihrem Konto sichtbar sind. Wenn Sie nach etwas wie [!DNL Facebook] suchen, aber nicht aufgeführt ist, senden Sie [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

**Wenn Sie einen Fehlerstatus für eine Integration sehen**, finden Sie Hilfe im Abschnitt [Fehlerbehebung](https://support.magento.com/hc/en-us/sections/360003078151) .
