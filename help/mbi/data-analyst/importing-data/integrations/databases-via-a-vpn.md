---
title: Verbinden von Datenbanken über VPN
description: Erfahren Sie, wie Sie Datenbanken über VPN statt über SSH-Tunnel verbinden.
exl-id: c7aa564d-42de-426e-92e9-f6e250a6abba
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/0B7swwGIgBemitnx8Q4tyN8VtqwzcA-DYZdXHqzyNAk
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c32adafa-ed01-4b31-997e-2413013911b0
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 400
ht-degree: 0%

---

# Verbinden von Datenbanken über VPN

Adobe empfiehlt zwar, Ihre Datenbanken über eine `SSH tunnel` zu verbinden, Sie können aber auch eine verschlüsselte `VPN` verwenden, um die Sicherheit zu gewährleisten. Ein `VPN` kann für jede Ihrer Datenbankintegrationen verwendet werden, und um die Dinge einfach zu halten, ist der Prozess so ziemlich dasselbe wie das Einrichten eines `SSH tunnel`:

1. [Erstellen  [!DNL Commerce Intelligence]  Datenbankbenutzers](#database)
1. [Erstellen eines  [!DNL Commerce Intelligence] -VPN-Benutzers](#vpn)
1. [Zugriff auf die IP [!DNL Commerce Intelligence] Adresse zulassen](#allowlist)
1. [Geben Sie die Verbindungs- und VPN-Benutzerinformationen in Commerce Intelligence ein](#finish)

Zusätzlich zu den Datenbankanmeldeinformationen müssen Sie Anmeldeinformationen eingeben, damit ein VPN-Benutzer die Dinge abschließt. Jeder VPN-Benutzer funktioniert, aber Adobe empfiehlt, einen [!DNL Commerce Intelligence]-Benutzer zu erstellen, da es für Sie einfacher ist, die Benutzer in Ihrem Konto zu verfolgen.

## Erstellen einer Benutzerdatenbank für [!DNL Commerce Intelligence] {#database}

Der Prozess zum Erstellen eines Datenbankbenutzers hängt vom Datenbanktyp ab, den Sie verbinden. Klicken Sie auf die folgenden Links, um die Anweisungen für die einzelnen Datenbanktypen anzuzeigen.

* [MICROSOFT SQL](../integrations/microsoft-sql-server.md)
* [MongoDB](../integrations/databases-via-a-vpn.md)
* [MySQL](../integrations/mysql-via-a-direct-connection.md)
* [PostgreSQL](../integrations/postgresql.md)

## Erstellen eines `VPN` Benutzers für [!DNL Commerce Intelligence] {#vpn}

Wie bereits erwähnt, funktioniert jeder gültige `VPN`-Benutzer . Adobe empfiehlt jedoch, einen Benutzer nur für [!DNL Commerce Intelligence] Verwendung zu erstellen.

## Zulassen des Zugriffs auf die [!DNL Commerce Intelligence] IP-Adressen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff über Ihre IP-Adressen zulässig ist. Sie sind `54.88.76.97` und `34.250.211.151`, befinden sich aber auch auf der `credentials` Seite für jede Datenbankintegration:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Eingabe der Verbindungs- und `VPN` in [!DNL Commerce Intelligence] {#finish}

Um alles abzuschließen, müssen Sie die Verbindung und die Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite `credentials` geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]**. Klicken Sie auf **[!UICONTROL Add New Data Source]** und dann auf das Symbol für die Datenbank, die Sie verbinden möchten. Vergessen Sie nicht, den Umschalter `Encrypted` in `Yes` zu ändern.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Username`: Der Benutzername für den [!DNL Commerce Intelligence] Datenbankbenutzer
* `Password`: Das Kennwort für den [!DNL Commerce Intelligence] Datenbankbenutzer
* `Port`: Der Port der Datenbank auf Ihrem Server. Die Standardeinstellungen sind:
   * `MicrosoftSQL`: `1433`
   * `MongoDB`: `27017`
   * `MySQL`: `3306`
   * `PostgreSQL`: `5432`
* `Host`: Standardmäßig ist dies localhost `127.0.0.1`, aber es kann auch die öffentliche IP-Adresse Ihres Servers oder eine Adresse eines lokalen Netzwerks sein.
* `Database Name (optional)`: Wenn Sie nur den Zugriff auf eine Datenbank zulassen (dies wird während des Erstellungsschritts des Datenbankbenutzers angegeben), geben Sie den Namen dieser Datenbank hier ein.

Im Abschnitt `Encryption Connection` :

* `Encryption Type`: Dies auf `Cisco IPsec VPN` setzen
* `Gateway Address`: Die IP-Adresse des VPN-Servers
* `Group Name`: Der Name der für die Gruppenauthentifizierung verwendeten Gruppe
* `Group Secret`: Das Kennwort für die Gruppe.
* `Username`: Der [!DNL Commerce Intelligence] `VPN` Benutzername
* `Password`: Das [!DNL Commerce Intelligence] `VPN` Benutzerkennwort

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um die Einrichtung abzuschließen.
