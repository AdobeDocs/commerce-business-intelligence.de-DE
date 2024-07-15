---
title: Microsoft SQL Server verbinden
description: Erfahren Sie, wie Sie Ihre Microsoft SQL-Datenbank in vier Schritten mit [!DNL Commerce Intelligence] verbinden.
exl-id: 7f49d1dc-8fbb-4a8c-9d07-9a8195c266f5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# [!DNL Microsoft SQL] Server verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/MicrosoftSQLServer-logo.png)

In diesem Thema wird erläutert, wie Sie Ihre [!DNL Microsoft SQL]-Datenbank in vier Schritten mit [!DNL Commerce Intelligence] verbinden können. Dieser Prozess erfordert einige technische Kenntnisse im Zusammenhang mit Serververbindungen und SQL und kann Unterstützung von Entwicklern in Ihrem Team erfordern.

[!DNL Commerce Intelligence] unterstützt [!DNL Amazon RDS], [!DNL EC2], [!DNL Microsoft SQL Azure] und die meisten anderen Cloud-Server-Anbieter. Wenn Sie eine Frage zu Ihrem bestimmten Host haben, senden Sie [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um uns zu bitten, diese Informationen anzugeben.

Ihr System muss SELECT-Abfragen für Ihre Datenbank ausführen. Dies geschieht zunächst, um eine Momentaufnahme Ihrer Datenbankstruktur zu erhalten und dann regelmäßig, um Ihre Daten auf dem neuesten Stand zu halten. Ihre Updates sind inkrementell und Adobe schränkt die Aktualisierungshäufigkeit und -zeit ein, um unerwünschte Ladevorgänge auf Ihrem Server zu vermeiden.

Die beste Möglichkeit, dies zu tun, besteht darin, dass wir über TCP/IP eine Verbindung zu Ihrem Datenbankserver herstellen. Erstellen Sie für uns einen Benutzer, der nur SELECT-Abfragen ausführen kann (und optional nur Daten aus den angegebenen Tabellen auswählen kann). Dies muss für jeden Ihrer Server durchgeführt werden, mit dem Sie eine Verbindung zu [!DNL Commerce Intelligence] herstellen.

## Verbinden von `Microsoft SQL` mit [!DNL Commerce Intelligence]:

1. Stellen Sie sicher, dass Ihr Server Verbindungen über TCP/IP und die Authentifizierung im gemischten Modus zulässt.

1. Stellen Sie sicher, dass Ihre Firewall die Verbindung der dedizierten IP Ihres Servers ermöglicht.

   Die IP-Adresse, über die eine Verbindung zu Ihrem Server hergestellt wird, finden Sie im Abschnitt &quot;Verbindungen&quot;auf Ihrer `Settings` -Seite.

1. Erstellen Sie einen Benutzer, der zum Anmelden bei Ihrem Datenbankserver verwendet werden soll. Sie haben zwei Optionen, entweder über `UI` oder über einen `query`:
   * `UI`
   * [`Query`](http://sqlserverplanet.com/security/add-user) (zweites Beispiel)

1. Geben Sie die IP-Adresse, den Benutzernamen und das Kennwort des Servers in [!DNL Commerce Intelligence] unter **[!UICONTROL Manage Data** > **Connections]** ein.

   ![](../../../assets/manage-data-connections.png)

1. Klicken Sie auf **[!UICONTROL Add a Data Source]**.

1. Wählen Sie aus, um eine `Microsoft SQL` -Datenbank zu verbinden, und geben Sie Ihre Anmeldedaten in die Felder auf der neuen `Connections`-Seite ein.

   Wenn Sie `Windows Azure` verwenden, müssen Sie auch einen Datenbanknamen angeben.
