---
title: Verbinden von Microsoft&reg;&reg; SQL Server
description: Erfahren Sie, wie Sie Ihre Microsoft&reg verbinden. SQL-Datenbank zu [!DNL MBI] in einem vierstufigen Prozess.
exl-id: 7f49d1dc-8fbb-4a8c-9d07-9a8195c266f5
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Microsoft® SQL Server verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/MicrosoftSQLServer-logo.png)

In diesem Artikel wird erläutert, wie Sie Ihre `Microsoft SQL` Datenbank zu [!DNL MBI] in einem vierstufigen Prozess. Dieser Prozess erfordert einige technische Kenntnisse im Zusammenhang mit Serververbindungen und SQL und kann Unterstützung von Entwicklern in Ihrem Team erfordern.

MBI-Unterstützung [!DNL Amazon RDS], [!DNL EC2], [!DNL Microsoft®; SQL Azure]und den meisten anderen Cloud-Server-Anbietern. Wenn Sie Fragen zu Ihrem bestimmten Host haben, [Support-Ticket einreichen](../../../guide-overview.md) Wir bitten um diese Information.

Ihr System muss SELECT-Abfragen für Ihre Datenbank ausführen. Dies geschieht zunächst, um eine Momentaufnahme Ihrer Datenbankstruktur zu erhalten und dann regelmäßig, um Ihre Daten auf dem neuesten Stand zu halten. Ihre Aktualisierungen sind inkrementell, und die Adobe beschränkt die Aktualisierungshäufigkeit und -zeit, um unerwünschte Serverlasten zu vermeiden.

Die beste Möglichkeit, dies zu tun, besteht darin, dass wir über TCP/IP eine Verbindung zu Ihrem Datenbankserver herstellen. Erstellen Sie für uns einen Benutzer, der nur SELECT-Abfragen ausführen kann (und optional nur Daten aus den von Ihnen angegebenen Tabellen auswählen kann). Dies muss für jeden Ihrer Server erfolgen, mit dem Sie eine Verbindung herstellen. [!DNL MBI].

## Verbinden `Microsoft SQL` nach [!DNL MBI]:

1. Stellen Sie sicher, dass Ihr Server Verbindungen über TCP/IP und die Authentifizierung im gemischten Modus zulässt.

1. Stellen Sie sicher, dass Ihre Firewall die Verbindung der dedizierten IP Ihres Servers ermöglicht.

   Die IP-Adresse, über die die Verbindung zu Ihrem Server hergestellt wird, finden Sie im Abschnitt Verbindungen Ihrer `Settings` Seite.

1. Erstellen Sie einen Benutzer, der zum Anmelden bei Ihrem Datenbankserver verwendet werden soll. Sie haben zwei Möglichkeiten: entweder via `UI` oder `query`:
   * `UI`
   * [`Query`](http://sqlserverplanet.com/security/add-user) (zweites Beispiel)

1. Geben Sie die IP-Adresse, den Benutzernamen und das Kennwort des Servers ein in [!DNL MBI] under **[!UICONTROL Manage Data** > **Connections]**.

   ![](../../../assets/manage-data-connections.png)

1. Klicken **[!UICONTROL Add a Data Source]**.

1. Wählen Sie aus, um eine Verbindung herzustellen. `Microsoft SQL` Datenbank und geben Sie Ihre Anmeldedaten in die Felder des neuen `Connections` Seite.

   Wenn Sie `Windows Azure`, müssen Sie auch einen Datenbanknamen angeben.
