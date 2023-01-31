---
title: Microsoft SQL Server verbinden
description: Erfahren Sie, wie Sie Ihre Microsoft SQL-Datenbank mit [!DNL MBI] in einem vierstufigen Prozess.
exl-id: 7f49d1dc-8fbb-4a8c-9d07-9a8195c266f5
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Microsoft SQL Server verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/MicrosoftSQLServer-logo.png)

In diesem Artikel wird erläutert, wie Sie Ihre `Microsoft SQL` Datenbank zu [!DNL MBI] in einem vierstufigen Prozess. Dieser Prozess erfordert einige technische Kenntnisse im Zusammenhang mit Serververbindungen und SQL und kann Unterstützung von Entwicklern in Ihrem Team erfordern.

Wir unterstützen [!DNL Amazon RDS], [!DNL EC2], [!DNL Microsoft SQL Azure]und den meisten anderen Cloud-Server-Anbietern. Wenn Sie Fragen zu Ihrem bestimmten Host haben, [Support-Ticket einreichen](../../../guide-overview.md) Wir bitten um diese Information.

Unser System muss SELECT-Abfragen für Ihre Datenbank ausführen. Dies geschieht zunächst, um eine Momentaufnahme Ihrer Datenbankstruktur zu erhalten und dann regelmäßig, um unsere Daten auf dem neuesten Stand zu halten. Unsere Updates sind stufenweise, und wir beschränken die Aktualisierungshäufigkeit und -zeit, um unerwünschte Ladevorgänge auf Ihrem Server zu vermeiden.

Die beste Möglichkeit, dies zu tun, besteht darin, dass wir über TCP/IP eine Verbindung zu Ihrem Datenbankserver herstellen. Erstellen Sie für uns einen Benutzer, der nur SELECT-Abfragen ausführen kann (und optional nur Daten aus den von Ihnen angegebenen Tabellen auswählen kann). Dies muss für jeden Ihrer Server durchgeführt werden, mit dem Sie eine Verbindung herstellen. [!DNL MBI].

## Verbinden `Microsoft SQL` nach [!DNL MBI]:

1. Stellen Sie sicher, dass Ihr Server Verbindungen über TCP/IP und die Authentifizierung im gemischten Modus zulässt.

1. Stellen Sie sicher, dass Ihre Firewall die Verbindung der dedizierten IP-Adresse unseres Servers ermöglicht.

   Sie finden die IP-Adresse, die wir für die Verbindung mit Ihrem Server verwenden, im Abschnitt Verbindungen Ihrer `Settings` Seite.

1. Erstellen Sie einen Benutzer, mit dem wir uns bei Ihrem Datenbankserver anmelden.  Sie haben zwei Möglichkeiten: entweder via `UI` oder `query`:
   * `UI`
   * [`Query`](http://sqlserverplanet.com/security/add-user) (zweites Beispiel)

1. Geben Sie IP-Adresse, Benutzername und Kennwort des Servers ein in [!DNL MBI] under **[!UICONTROL Manage Data** > **Connections]**.

   ![](../../../assets/manage-data-connections.png)

1. Klicken **[!UICONTROL Add a Data Source]**.

1. Wählen Sie aus, um eine Verbindung herzustellen. `Microsoft SQL` Datenbank und geben Sie Ihre Anmeldedaten in die Felder des neuen `Connections` Seite.

   Wenn Sie `Windows Azure`, müssen Sie auch einen Datenbanknamen angeben.
