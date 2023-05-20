---
title: Datenbanken über VPN verbinden
description: Erfahren Sie, wie Sie Datenbanken über VPN anstatt über SSH-Tunnel verbinden.
exl-id: c7aa564d-42de-426e-92e9-f6e250a6abba
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Datenbanken über VPN verbinden

Adobe empfiehlt, Ihre Datenbanken mit einer `SSH tunnel`, können Sie auch eine verschlüsselte `VPN` Verbindung, um die Sicherheit zu gewährleisten. A `VPN` kann für beliebige Datenbankintegrationen verwendet werden. Um die Dinge einfach zu halten, entspricht der Prozess ungefähr der Einrichtung einer `SSH tunnel`:

1. [Erstellen Sie eine [!DNL Commerce Intelligence] Datenbankbenutzer](#database)
1. [Erstellen Sie eine [!DNL Commerce Intelligence] VPN-Benutzer](#vpn)
1. [Zugriff auf [!DNL Commerce Intelligence] IP-Adresse](#allowlist)
1. [Geben Sie die Verbindung und VPN-Benutzerinformationen in Commerce Intelligence ein.](#finish)

Zusätzlich zu den Datenbankberechtigungen müssen Sie die Anmeldeinformationen eingeben, damit ein VPN-Benutzer die Elemente einschließen kann. Jeder VPN-Benutzer funktioniert, aber Adobe empfiehlt, eine [!DNL Commerce Intelligence] -Benutzer, da es Ihnen erleichtert, die Benutzer in Ihrem Konto zu verfolgen.

## Erstellen eines Datenbankbenutzers für [!DNL Commerce Intelligence] {#database}

Der Prozess zum Erstellen eines Datenbankbenutzers variiert je nach dem Datenbanktyp, den Sie verbinden. Um die Anweisungen für jeden Datenbanktyp anzuzeigen, klicken Sie auf die unten stehenden Links.

* [Microsoft SQL](../integrations/microsoft-sql-server.md)
* [MongoDB](../integrations/databases-via-a-vpn.md)
* [MySQL](../integrations/mysql-via-a-direct-connection.md)
* [PostgreSQL](../integrations/postgresql.md)

## Erstellen einer `VPN` Benutzer für [!DNL Commerce Intelligence] {#vpn}

Wie bereits erwähnt, sind alle gültigen `VPN` -Benutzer funktioniert, aber Adobe empfiehlt, einen Benutzer ausschließlich für [!DNL Commerce Intelligence] verwenden.

## Zugriff auf [!DNL Commerce Intelligence] IP-Adressen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151`, aber es befindet sich auch auf der `credentials` Seite für jede Datenbankintegration:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Eingeben der Verbindung und `VPN` Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]. Haben Sie die Datenbank verlassen? `credentials` Seite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]**. Klicken **[!UICONTROL Add New Data Source]** und klicken Sie dann auf das Symbol für die Datenbank, mit der Sie eine Verbindung herstellen möchten. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem `Database Connection` Abschnitt:

* `Username`: Der Benutzername für die [!DNL Commerce Intelligence] Datenbankbenutzer
* `Password`: Das Kennwort für die [!DNL Commerce Intelligence] Datenbankbenutzer
* `Port`: Der Datenbankanschluss auf Ihrem Server. Die Standardeinstellungen sind:
   * `MicrosoftSQL`: `1433`
   * `MongoDB`: `27017`
   * `MySQL`: `3306`
   * `PostgreSQL`: `5432`
* `Host`: Standardmäßig ist dies localhost `127.0.0.1`, aber es kann sich auch um die öffentliche IP-Adresse Ihres Servers oder eine lokale Netzwerkadresse handeln.
* `Database Name (optional)`: Wenn Sie nur Zugriff auf eine Datenbank gewährt haben (dies wird im Schritt zur Erstellung des Datenbankbenutzers angegeben), geben Sie hier den Namen dieser Datenbank ein.

Unter dem `Encryption Connection` Abschnitt:

* `Encryption Type`: Legen Sie hier fest `Cisco IPsec VPN`
* `Gateway Address`: Die IP-Adresse des VPN-Servers
* `Group Name`: Der Name der Gruppe, die für die Gruppenauthentifizierung verwendet wird
* `Group Secret`: Das Kennwort für die Gruppe.
* `Username`: Die [!DNL Commerce Intelligence] `VPN` Benutzername
* `Password`: Die [!DNL Commerce Intelligence] `VPN` Benutzerkennwort

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.
