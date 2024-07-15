---
title: MySQL über cPanel verbinden
description: Erfahren Sie, wie Sie MySQL über cPanel verbinden.
exl-id: 90b0a0b0-8c6b-4144-95b4-f588f18616c7
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# [!DNL MySQL] über [!DNL cPanel] verbinden

* [Erstellen eines  [!DNL Commerce Intelligence] [!DNL MySQL] Benutzers in  [!DNL cPanel]](#cpanel)
* [Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben](#finish)

## Springen Sie zu

* [[!DNL MySQL] über SSH-Tunnel](../integrations/mysql-via-ssh-tunnel.md)
* [[!DNL MySQL] über direkte Verbindung](../integrations/mysql-via-a-direct-connection.md)

>[!IMPORTANT]
>
>[!DNL Adobe] empfiehlt die Verwendung von SSH oder einer anderen Form der Verschlüsselung, um Ihre Daten zu sichern! Wenn dies keine Option ist, können Sie mithilfe der Anweisungen in diesem Thema weiterhin [!DNL Commerce Intelligence] direkt mit Ihrer Datenbank verbinden.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL]-Datenbank mit [!DNL Commerce Intelligence] mithilfe von [!DNL cPanel]. Dieser Prozess kann auch verwendet werden, um [!DNL Adobe Commerce] und andere MySQL-basierte eCommerce-Datenbanken mit [!DNL Commerce Intelligence] zu verbinden.

1. Erstellen eines [!DNL Commerce Intelligence] [!DNL MySQL] Benutzers in [!DNL cPanel]
1. Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben

Erste Schritte.

## Erstellen eines [!DNL Commerce Intelligence] [!DNL MySQL] Benutzers in [!DNL cPanel] {#cpanel}

1. Melden Sie sich über Ihren Hosting-Provider bei [!DNL cPanel] an.
1. Klicken Sie auf &quot;**[!UICONTROL [!DNL MySQL] Databases]**&quot;, der sich im Abschnitt &quot;`Database`&quot; befindet.
1. Scrollen Sie nach unten zum Abschnitt `Add New User` und erstellen Sie einen Benutzer für [!DNL Commerce Intelligence]:

   ![](../../../assets/create-mbi-mysql-user-cpanel.png)

1. Klicken Sie auf **[!UICONTROL Create User]**.
1. Nachdem Sie den Benutzer erstellt haben, müssen Sie ihn mit einer Datenbank verknüpfen. Gehen Sie zurück zum Abschnitt &quot;`Add New User`&quot;- siehe Einstellungen für &quot;`Add User to Database?`&quot;. Dies ist es, was Sie benötigen.
1. Wählen Sie in der Dropdown-Liste `User` dieses Abschnitts den erstellten Benutzer aus.
1. Wählen Sie in der Dropdown-Liste `Database` dieses Abschnitts die Datenbank aus, mit der Sie eine Verbindung herstellen möchten.[!DNL Commerce Intelligence]
1. Klicken Sie auf **[!UICONTROL Add]**.
1. Wenn die Checkliste der Berechtigungen angezeigt wird, aktivieren Sie das Kontrollkästchen neben `SELECT` - dies ist alles, was [!DNL Commerce Intelligence] für die Verbindung mit Ihrer Datenbank benötigt.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den Anmeldedaten für [!DNL MySQL] geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann auf das Symbol [!DNL MySQL].

Geben Sie die folgenden Informationen in diese Seite im Abschnitt `Database Connection` ein:

* `Username`: Der Benutzername für den Benutzer [!DNL Commerce Intelligence] [!DNL MySQL]
* `Password`: Das Kennwort für den Benutzer [!DNL Commerce Intelligence] [!DNL MySQL]
* `Port`: MySQL-Port auf Ihrem Server (standardmäßig `3306`)
* `Host`: Die öffentliche Adresse des `MySQL` -Servers [!DNL Commerce Intelligence] stellt eine Verbindung her. Dies ist normalerweise die URL, mit der Sie sich bei `[!DNL cPanel]` anmelden.

Wenn Sie einen [`SSH tunnel`](../integrations/mysql-via-ssh-tunnel.md) verwenden, müssen Sie die Verschlüsselungsinformationen eingeben. Setzen Sie den Umschalter `Encrypted` auf `Yes` , um das Formular anzuzeigen.

* `Connection Type`: Setzen Sie dies auf `SSH Tunnel`
* `Remote Address`: Die IP-Adresse oder der Hostname des Servers [!DNL Commerce Intelligence] wird durch einen Tunnel in
* `Username`: Der Benutzername für den Benutzer [!DNL Commerce Intelligence] `SSH (Linux)`, siehe [Anweisungen](../../../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md), wie Sie dies tun können, falls Sie dies noch nicht getan haben.)
* `SSH Port`: SSH-Port auf Ihrem Server (standardmäßig `22`)

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
