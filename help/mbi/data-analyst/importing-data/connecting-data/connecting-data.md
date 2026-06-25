---
title: Verbinden von Daten
description: Erfahren Sie, wie Sie die Tabellen durchsuchen, die für die Synchronisierung im Data Warehouse Manager verfügbar sind.
exl-id: 94beba8b-6a86-4af9-87fb-96b1cf8f8fa2
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration
TQID: https://experienceleague.adobe.com/WwUCbK9dC39RSVL8Nf0PdL10wAdxje-9deR20JScqj0
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: efc8727dd67a9ffcd7a8a1059ea93df8c6344599
workflow-type: tm+mt
source-wordcount: 628
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

Adobe empfiehlt, eine bewährte Verschlüsselungsmethode wie einen SSH-Tunnel zu verwenden, auch wenn Sie Ihre Datenbank mithilfe der Datenbankanmeldeinformationen direkt mit [!DNL Commerce Intelligence] verbinden können. Dadurch wird sichergestellt, dass Ihre Daten beim Eintritt in Ihre Data Warehouse sicher bleiben. Informationen zu Registrierung, Fehlern und Fehlerbehebung für SSH-Hostschlüssel finden Sie unter [SSH-Hostschlüsselüberprüfung](../integrations/ssh-host-key-verification.md).

Je nach Verbindungsmethode und Datenbanktyp sind möglicherweise technische Kenntnisse erforderlich, um die Einrichtung abzuschließen.

## `SaaS` Integrationen

![SaaS-Integrationssymbole mit verschiedenen unterstützten Plattformen](../../../assets/SaaS_icons.jpg)spree-commerce-logo.png

`SaaS` Integrationen sind Services wie [[!DNL Google Adwords]](../integrations/google-adwords.md), [[!DNL Salesforce]](../integrations/salesforce.md) und [[!DNL Zendesk]](../integrations/zendesk.md). Da sich Daten von Drittanbietern auf dem Server des Anbieters befinden, können Sie nicht direkt darauf zugreifen, wie Sie es mit den Daten in Ihrer Datenbank tun können.

Normalerweise ist das Einrichten einer Integration in [!DNL Commerce Intelligence] so einfach wie das Eingeben Ihrer Kontoanmeldeinformationen. Einige Dienste benötigen möglicherweise einen API-Schlüssel, um die Autorisierung abzuschließen. Anweisungen zum Generieren [&#x200B; benötigten Anmeldeinformationen finden &#x200B;](../integrations/integrations.md) im Abschnitt „Integrationen“.

## Datei-Upload

Sie sind sich nicht sicher, wie Sie Daten aus einer zusätzlichen Quelle in Ihre Data Warehouse übertragen können? [Die Verwendung der `File Upload`-Funktion](../connecting-data/using-file-uploader.md) ist eine gute Möglichkeit, Daten abzurufen, die Sie für die alltägliche Entscheidungsfindung nicht benötigen. Nach den Formatierungsregeln können Sie `.csv` Dateien schnell in Ihre Data Warehouse hochladen und mit anderen Datenquellen verbinden.

## [!DNL Commerce Intelligence] `Import API`

Wenn Sie den Abruf von Daten aus einer Ihrer eigenen Quellen automatisieren möchten, können Sie die [!DNL Commerce Intelligence] `Import API` verwenden. Grundsätzlich gilt: Wenn es sich nicht in einer Datenbank oder einer `SaaS`-Integration befindet, ist die `Import API` die beste Wahl.

Die Verwendung der API erfordert ein wenig technisches Know-how - jemand, der mit dem Schreiben und Verwalten eines kleinen Ruby- oder PHP-Skripts vertraut ist, ist mehr als qualifiziert.

Weitere Informationen zu den ersten Schritten mit dem `Import API` finden Sie auf der [Entwickler-Site](https://developer.adobe.com/commerce/services/reporting/) und [So generieren Sie einen API-Schlüssel](https://developer.adobe.com/commerce/services/reporting/import-api/).

## Hinzufügen einer Integration

Um eine Integration hinzuzufügen, klicken Sie auf **[!UICONTROL Manage Data** > **Connections]** und dann auf **[!UICONTROL Add a New Data Source]**. Klicken Sie auf das Symbol der Integration, die Sie hinzufügen möchten, und befolgen Sie die Anweisungen in den Hilfethemen, um Dinge einzurichten:

* [Häufig gestellte Fragen zur Integration](https://support.magento.com/hc/en-us/sections/360003161871-Integration-FAQ)
* [Verfügbare `SaaS` und `database` Integrationen](../integrations/integrations.md)
* [Konsolidieren von Tabellen](../../../best-practices/consolidating-your-tables.md)
* [Beschränken des Zugriffs auf die Datenbank](../../../administrator/account-management/restrict-db-access.md)

**Sie sehen keine Integration, die Sie möchten?** Einige Integrationen müssen aktiviert werden, damit sie in Ihrem Konto sichtbar sind. Wenn Sie nach etwas wie [!DNL Facebook] suchen, es aber nicht aufgeführt ist, [&#x200B; Sie ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

**Wenn Sie einen Fehlerstatus für eine Integration sehen** finden Sie im Abschnitt [Fehlerbehebung](https://support.magento.com/hc/en-us/sections/360003078151) Hilfe.

## Überwachen des Aktualisierungsstatus (optional)

Nachdem Sie Quellen verbunden haben, sollten Sie eine allgemeine Konsistenzprüfung automatisieren, um zu bestätigen, dass vollständige Aktualisierungen abgeschlossen werden. Verwenden Sie die [Update Cycle Status-API](https://developer.adobe.com/commerce/services/reporting/update-cycle-status-api/) in der Entwicklerdokumentation, um den zuletzt abgeschlossenen Aktualisierungszyklus für Ihren Client abzurufen und ihn in internen Dashboards oder Warnhinweisen anzuzeigen.

