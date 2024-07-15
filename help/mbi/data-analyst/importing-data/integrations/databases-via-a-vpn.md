---
title: Datenbanken über VPN verbinden
description: Erfahren Sie, wie Sie Datenbanken über VPN anstatt über SSH-Tunnel verbinden.
exl-id: c7aa564d-42de-426e-92e9-f6e250a6abba
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Datenbanken über VPN verbinden

Während Adobe empfiehlt, dass Sie Ihre Datenbanken mit einem `SSH tunnel` verbinden, können Sie auch eine verschlüsselte `VPN` Verbindung verwenden, um die Sicherheit zu gewährleisten. Ein `VPN` kann für jede Ihrer Datenbankintegrationen verwendet werden. Um die Dinge einfach zu halten, entspricht der Prozess ungefähr dem Einrichten eines `SSH tunnel`:

1. [Erstellen eines [!DNL Commerce Intelligence] Datenbankbenutzers](#database)
1. [Erstellen eines  [!DNL Commerce Intelligence] VPN-Benutzers](#vpn)
1. [Zugriff auf die  [!DNL Commerce Intelligence] IP-Adresse zulassen](#allowlist)
1. [Geben Sie die Verbindung und VPN-Benutzerinformationen in Commerce Intelligence ein](#finish)

Zusätzlich zu den Datenbankberechtigungen müssen Sie die Anmeldeinformationen eingeben, damit ein VPN-Benutzer die Elemente einschließen kann. Jeder VPN-Benutzer funktioniert, aber Adobe empfiehlt Ihnen, einen [!DNL Commerce Intelligence] -Benutzer zu erstellen, da es Ihnen erleichtert, die Nutzer auf Ihrem Konto zu verfolgen.

## Datenbankbenutzer für [!DNL Commerce Intelligence] erstellen {#database}

Der Prozess zum Erstellen eines Datenbankbenutzers variiert je nach dem Datenbanktyp, den Sie verbinden. Um die Anweisungen für jeden Datenbanktyp anzuzeigen, klicken Sie auf die unten stehenden Links.

* [MICROSOFT SQL](../integrations/microsoft-sql-server.md)
* [MongoDB](../integrations/databases-via-a-vpn.md)
* [MySQL](../integrations/mysql-via-a-direct-connection.md)
* [PostgreSQL](../integrations/postgresql.md)

## Erstellen eines `VPN` Benutzers für [!DNL Commerce Intelligence] {#vpn}

Wie bereits erwähnt, funktioniert jeder gültige `VPN` -Benutzer. Adobe empfiehlt jedoch, einen Benutzer ausschließlich für die Verwendung von [!DNL Commerce Intelligence] zu erstellen.

## Zugriff auf die [!DNL Commerce Intelligence] -IP-Adressen zulassen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151`, befinden sich aber auch auf der Seite `credentials` für jede Datenbankintegration:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Eingabe der Verbindung und `VPN` Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite &quot;`credentials`&quot; der Datenbank geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]**. Klicken Sie auf **[!UICONTROL Add New Data Source]** und dann auf das Symbol für die Datenbank, mit der Sie eine Verbindung herstellen möchten. Vergessen Sie nicht, den Umschalter `Encrypted` auf `Yes` zu ändern.

Geben Sie die folgenden Informationen in diese Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Username`: Der Benutzername für den Datenbankbenutzer [!DNL Commerce Intelligence]
* `Password`: Das Kennwort für den Datenbankbenutzer [!DNL Commerce Intelligence]
* `Port`: Der Anschluss der Datenbank auf Ihrem Server. Die Standardeinstellungen lauten:
   * `MicrosoftSQL`: `1433`
   * `MongoDB`: `27017`
   * `MySQL`: `3306`
   * `PostgreSQL`: `5432`
* `Host`: Standardmäßig ist dies localhost `127.0.0.1`, es kann aber auch die öffentliche IP-Adresse Ihres Servers oder eine lokale Netzwerkadresse sein.
* `Database Name (optional)`: Wenn Sie nur den Zugriff auf eine Datenbank zugelassen haben (dies wird bei der Erstellung des Datenbankbenutzers angegeben), geben Sie hier den Namen dieser Datenbank ein.

Unter dem Abschnitt `Encryption Connection` :

* `Encryption Type`: Setzen Sie dies auf `Cisco IPsec VPN`
* `Gateway Address`: Die IP-Adresse des VPN-Servers
* `Group Name`: Der Name der für die Gruppenauthentifizierung verwendeten Gruppe
* `Group Secret`: Das Kennwort für die Gruppe.
* `Username`: Der Benutzername [!DNL Commerce Intelligence] `VPN`
* `Password`: Das Benutzerkennwort [!DNL Commerce Intelligence] `VPN`

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.
