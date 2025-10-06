---
title: MySQL über cPanel verbinden
description: Erfahren Sie, wie Sie MySQL über cPanel verbinden.
exl-id: 90b0a0b0-8c6b-4144-95b4-f588f18616c7
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# [!DNL MySQL] über [!DNL cPanel] verbinden

* [Erstellen Sie  [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer in [!DNL cPanel]](#cpanel)
* [Geben Sie Verbindungs- und Benutzerinformationen in ein [!DNL Commerce Intelligence]](#finish)

## Zu springen

* [[!DNL MySQL] über SSH-Tunnel](../integrations/mysql-via-ssh-tunnel.md)
* [[!DNL MySQL] über Direktverbindung](../integrations/mysql-via-a-direct-connection.md)

>[!IMPORTANT]
>
>[!DNL Adobe] empfiehlt die Verwendung von SSH oder einer anderen Form der Verschlüsselung, um Ihre Daten zu schützen! Wenn dies keine Option ist, können Sie [!DNL Commerce Intelligence] dennoch direkt mit Ihrer Datenbank verbinden, indem Sie die Anweisungen in diesem Thema verwenden.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL]-Datenbank mit [!DNL Commerce Intelligence] mithilfe von [!DNL cPanel]. Dieser Prozess kann auch verwendet werden, um [!DNL Adobe Commerce] und andere MySQL-basierte eCommerce-Datenbanken mit [!DNL Commerce Intelligence] zu verbinden.

1. Erstellen eines [!DNL Commerce Intelligence] [!DNL MySQL] Benutzers in [!DNL cPanel]
1. Eingabe von Verbindungs- und Benutzerinformationen in [!DNL Commerce Intelligence]

Erste Schritte.

## Erstellen eines [!DNL Commerce Intelligence] [!DNL MySQL] Benutzers in [!DNL cPanel] {#cpanel}

1. Melden Sie sich über Ihren Hosting-Anbieter bei [!DNL cPanel] an.
1. Klicken Sie auf **[!UICONTROL [!DNL MySQL] Databases]** im Abschnitt `Database` .
1. Scrollen Sie nach unten zum Abschnitt `Add New User` und erstellen Sie einen Benutzer für [!DNL Commerce Intelligence]:

   ![cPanel MySQL-Datenbankschnittstelle mit der Anzeige „Benutzerformular erstellen“](../../../assets/create-mbi-mysql-user-cpanel.png)

1. Klicken Sie auf **[!UICONTROL Create User]**.
1. Nachdem Sie den Benutzer erstellt haben, müssen Sie ihn mit einer Datenbank verknüpfen. Gehen Sie zurück zum Abschnitt `Add New User` . Sehen Sie sich die Einstellungen für `Add User to Database?` an.
1. Wählen Sie in der Dropdown-Liste `User` dieses Abschnitts den erstellten Benutzer aus.
1. Wählen Sie in der Dropdown-Liste `Database` dieses Abschnitts die Datenbank aus, mit der Sie eine Verbindung herstellen [!DNL Commerce Intelligence].
1. Klicken Sie auf **[!UICONTROL Add]**.
1. Wenn die Checkliste mit Berechtigungen angezeigt wird, aktivieren Sie das Kontrollkästchen neben `SELECT` - dies ist alles, was [!DNL Commerce Intelligence] mit Ihrer Datenbank verbinden muss.

## Eingabe der Verbindungs- und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um alles abzuschließen, müssen Sie die Verbindung und die Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den [!DNL MySQL]-Anmeldeinformationen geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]** und dann auf das Symbol [!DNL MySQL] .

Geben Sie im Abschnitt `Database Connection` die folgenden Informationen in diese Seite ein:

* `Username`: Der Benutzername für den [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Password`: Das Kennwort für den [!DNL Commerce Intelligence] [!DNL MySQL]
* `Port`: Port von MySQL auf Ihrem Server (standardmäßig `3306`)
* `Host`: Die öffentliche Adresse des `MySQL`-Servers, mit dem [!DNL Commerce Intelligence] eine Verbindung herstellt. Dies ist normalerweise die URL, mit der Sie sich bei `[!DNL cPanel]` anmelden.

Wenn Sie ein [`SSH tunnel`](../integrations/mysql-via-ssh-tunnel.md) verwenden, müssen Sie die Verschlüsselungsinformationen eingeben. Stellen Sie den Umschalter `Encrypted` auf `Yes` ein, um das Formular anzuzeigen.

* `Connection Type`: Dies auf `SSH Tunnel` setzen
* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, für den [!DNL Commerce Intelligence] einen Tunnel erstellt
* `Username`: Der Benutzername für den [!DNL Commerce Intelligence] `SSH (Linux)`-Benutzer, siehe [Anweisungen](../../../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md), wie Sie dies tun können, falls Sie dies noch nicht getan haben)
* `SSH Port`: SSH-Port auf Ihrem Server (standardmäßig `22`)

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um die Einrichtung abzuschließen.

## Verwandt:

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
