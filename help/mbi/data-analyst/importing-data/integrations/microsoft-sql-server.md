---
title: Microsoft SQL Server verbinden
description: Erfahren Sie, wie Sie Ihre Microsoft SQL [!DNL Commerce Intelligence] Datenbank in einem vierstufigen Prozess mit verbinden.
exl-id: 7f49d1dc-8fbb-4a8c-9d07-9a8195c266f5
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Verbindung [!DNL Microsoft SQL] Server herstellen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Microsoft SQL Server-Logo](../../../assets/MicrosoftSQLServer-logo.png)

In diesem Thema wird erläutert, wie Sie Ihre [!DNL Microsoft SQL]-Datenbank in einem vierstufigen Prozess mit [!DNL Commerce Intelligence] verbinden. Dieser Prozess erfordert einige technische Kenntnisse in Bezug auf Server-Verbindungen und SQL und erfordert möglicherweise Unterstützung von Entwicklern in Ihrem Team.

[!DNL Commerce Intelligence] unterstützt [!DNL Amazon RDS], [!DNL EC2], [!DNL Microsoft SQL Azure] und die meisten anderen Cloud-Server-Anbieter. Wenn Sie eine Frage zu Ihrem Gastgeber haben, [&#x200B; Sie (ein Support-Ticket &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)) uns bitten, diese Informationen bereitzustellen.

Ihr System muss SELECT-Abfragen in Ihrer Datenbank ausführen. Dies erfolgt zunächst, um einen Schnappschuss Ihrer Datenbankstruktur zu erhalten, und dann regelmäßig durch Überstunden, um Ihre Daten auf dem neuesten Stand zu halten. Ihre Aktualisierungen erfolgen inkrementell, und Adobe beschränkt die Aktualisierungshäufigkeit und -zeit, um eine unerwünschte Belastung Ihres Servers zu vermeiden.

Die beste Möglichkeit, dies zu tun, besteht darin, eine Verbindung zu Ihrem Datenbankserver über TCP/IP herzustellen. Erstellen Sie einen Benutzer, der nur SELECT-Abfragen ausführen kann (und optional nur Daten aus den von Ihnen angegebenen Tabellen auswählen kann). Dies muss für jeden Server geschehen, mit dem Sie eine Verbindung [!DNL Commerce Intelligence].

## Verbinden von `Microsoft SQL` mit [!DNL Commerce Intelligence]:

1. Stellen Sie sicher, dass Ihr Server Verbindungen über TCP/IP und Authentifizierung im gemischten Modus zulässt.

1. Stellen Sie sicher, dass Ihre Firewall der dedizierten IP-Adresse Ihres Servers die Verbindung ermöglicht.

   Die IP-Adresse, mit der eine Verbindung zu Ihrem Server hergestellt wird, finden Sie im Abschnitt Verbindungen Ihrer `Settings`.

1. Erstellen Sie einen Benutzer, der zum Anmelden bei Ihrem Datenbankserver verwendet werden soll. Sie haben zwei Möglichkeiten: entweder über `UI` oder über eine `query`:
   * `UI`
   * [`Query`](http://sqlserverplanet.com/security/add-user) (zweites Beispiel)

1. Geben Sie die IP-Adresse, den Benutzernamen und das Kennwort des Servers in [!DNL Commerce Intelligence] unter **[!UICONTROL Manage Data** > **Connections]** ein.

   ![Seite „Datenverbindungen verwalten“ mit Datenbankintegrationen](../../../assets/manage-data-connections.png)

1. Klicken Sie auf **[!UICONTROL Add a Data Source]**.

1. Wählen Sie aus, um eine `Microsoft SQL` Datenbank zu verbinden, und geben Sie Ihre Anmeldeinformationen in die Felder auf der neuen `Connections` ein.

   Wenn Sie `Windows Azure` verwenden, müssen Sie auch einen Datenbanknamen angeben.
