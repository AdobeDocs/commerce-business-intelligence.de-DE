---
title: MySQL über SSH-Tunnel verbinden
description: Erfahren Sie, wie Sie MySQL über den SSH-Tunnel verbinden.
exl-id: 6b691a6a-9542-4e47-9b1d-d6d3c3dac357
source-git-commit: 8de036e2717aedef95a8bb908898fd9b9bc9c3fa
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Verbinden `MySQL` via `SSH Tunnel`

* [Rufen Sie die [!DNL MBI] öffentlicher Schlüssel](#retrieve)
* [Zugriff auf [!DNL MBI] IP-Adresse](#allowlist)
* [Linux erstellen](#linux)
* [Erstellen eines MySQL-Benutzers für [!DNL MBI]](#mysql)
* [Geben Sie die Verbindung und Benutzerinformationen in [!DNL MBI]](#finish)

## SPRINGEN ZU

* `MySQL via SSH tunnel`
* [&quot;MySQL&quot;](../integrations/mysql-via-a-direct-connection.md)
* [&quot;MySQL&quot;](../integrations/mysql-via-cpanel.md)

Um eine Verbindung herzustellen `MySQL` Datenbank zu [!DNL MBI] über eine `SSH tunnel`, müssen Sie (oder Ihr Team, falls Sie kein Techie sind) einige Dinge tun:

1. Rufen Sie die [!DNL MBI] `public key`
1. Zugriff auf [!DNL MBI] `IP address`
1. Erstellen Sie eine `Linux` Benutzer für [!DNL MBI]
1. Erstellen Sie eine `MySQL` Benutzer für [!DNL MBI]
1. Geben Sie die Verbindung und Benutzerinformationen in [!DNL MBI]

Erste Schritte.

## Abrufen der [!DNL MBI] öffentlicher Schlüssel {#retrieve}

Die `public key` wird verwendet, um die [!DNL MBI] `Linux` Benutzer. Im nächsten Abschnitt erstellen Sie den Benutzer und importieren den Schlüssel.

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**.
1. Klicken Sie auf `MySQL` Symbol.
1. Nach dem `MySQL credentials` Seite geöffnet wird, legen Sie die `Encrypted` Umschalten auf `Yes`. Dadurch wird das SSH-Setup-Formular angezeigt.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Wenn Sie etwas verloren sind, können Sie hier navigieren [!DNL MBI] , um den Schlüssel abzurufen:

![](../../../assets/MySQL_SSH.gif)<!--{: width="770"}-->

## Zugriff auf [!DNL MBI] IP-Adresse {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151` aber sie sind auch auf der `MySQL credentials` Seite. Sehen Sie die blaue Box in der GIF oben? Das ist es!

## Erstellen einer `Linux` Benutzer für [!DNL MBI] {#linux}

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können [diesen Benutzer einschränken](../../../administrator/account-management/restrict-db-access.md) wie Sie möchten, solange es das Recht behält, eine Verbindung mit dem `MySQL` Server.

1. Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stamm auf Ihrem `Linux` server:

```bash
        adduser rjmetric -p<password>
        mkdir /home/rjmetric
        mkdir /home/rjmetric/.ssh
```

1. Speichern Sie die `public key` Sie haben im ersten Abschnitt abgerufen? Um sicherzustellen, dass der Benutzer Zugriff auf die Datenbank hat, müssen Sie den Schlüssel in `authorized\_keys`.

   Kopieren Sie den gesamten Schlüssel in die `authorized\_keys` Datei wie folgt:

```bash
        touch /home/rjmetric/.ssh/authorized_keys
        "<PASTE KEY HERE>" >> /home/rjmetric/.ssh/authorized_keys
```

1. Um die Erstellung des Benutzers abzuschließen, ändern Sie die Berechtigungen für `/home/rjmetric` Verzeichnis, über das der Zugriff möglich ist `SSH`:

```bash
        chown -R rjmetric:rjmetric /home/rjmetric
        chmod -R 700 /home/rjmetric/.ssh
        chmod 400 /home/rjmetric/.ssh/authorized_keys
```

>[!IMPORTANT]
>
>Wenn die Variable `sshd\_config` -Datei, die mit dem Server verknüpft ist, nicht auf die Standardoption festgelegt, sondern nur bestimmte Benutzer haben Serverzugriff. Dies verhindert eine erfolgreiche Verbindung zu [!DNL MBI]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` , um `rjmetric` Benutzerzugriff auf den Server.

## Erstellen einer `MySQL` Benutzer für [!DNL MBI] {#mysql}

Ihr Unternehmen erfordert möglicherweise einen anderen Prozess, aber die einfachste Möglichkeit, diesen Benutzer zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie sich bei anmelden `MySQL` als Benutzer mit dem Recht, Berechtigungen zu gewähren:

```sql
    GRANT SELECT ON *.* TO 'rjmetric'@'localhost' IDENTIFIED BY '<secure password here>';
```

Ersetzen `secure password here` mit einem sicheren Kennwort, das sich von der `SSH` Kennwort.

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen GRANT-Abfragen ausführen, die nur den Zugriff auf die Daten ermöglichen, die Sie zulassen.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL MBI] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL MBI]. Hast du die `MySQL credentials` Seite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann das MySQL-Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem Abschnitt Datenbankverbindung :

* `Username`: Der Benutzername für die [!DNL MBI] MySQL-Benutzer
* `Password`: Das Kennwort für die [!DNL MBI] MySQL-Benutzer
* `Port`: MySQL-Port auf Ihrem Server (standardmäßig 3306)
* `Host` Standardmäßig ist dies localhost. Im Allgemeinen ist dies der bind-address-Wert für Ihren MySQL-Server, der standardmäßig `127.0.0.1 (localhost)`, kann aber auch eine lokale Netzwerkadresse sein (z. B. `192.168.0.1`) oder der öffentlichen IP-Adresse Ihres Servers.

   Der Wert befindet sich in der `my.cnf` Datei (befindet sich unter `/etc/my.cnf`) unter der Zeile, die lautet `\[mysqld\]`. Wenn die bind-address-Zeile in dieser Datei auskommentiert ist, wird Ihr Server vor externen Verbindungsversuchen geschützt.

Im `SSH Connection` Abschnitt:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers [!DNL MBI] in den
* `Username`: Der Benutzername für die [!DNL MBI] SSH-Benutzer (Linux®)
* `SSH Port`: SSH-Anschluss auf Ihrem Server (standardmäßig 22)

Das ist es! Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
