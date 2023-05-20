---
title: Verbinden [!DNL MySQL] über SSH-Tunnel
description: Erfahren Sie, wie Sie eine Verbindung herstellen [!DNL MySQL] über SSH-Tunnel.
exl-id: 6b691a6a-9542-4e47-9b1d-d6d3c3dac357
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Verbinden [!DNL MySQL] via [!DNL SSH Tunnel]

* [Rufen Sie die [!DNL Commerce Intelligence] öffentlicher Schlüssel](#retrieve)
* [Zugriff auf [!DNL Commerce Intelligence] IP-Adresse](#allowlist)
* [Erstellen eines Linux-Benutzers für [!DNL Commerce Intelligence]](#linux)
* [Erstellen Sie eine [!DNL MySQL] Benutzer für [!DNL Commerce Intelligence]](#mysql)
* [Geben Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]](#finish)

## SPRINGEN ZU

* [[!DNL MySQL] via ](../integrations/mysql-via-a-direct-connection.md)
* [[!DNL MySQL] via [!DNL cPanel]](../integrations/mysql-via-cpanel.md)

Um eine Verbindung herzustellen [!DNL MySQL] Datenbank zu [!DNL Commerce Intelligence] über eine `SSH tunnel`müssen Sie einige Schritte ausführen:

1. Rufen Sie die [!DNL Commerce Intelligence] `public key`
1. Zugriff auf [!DNL Commerce Intelligence] `IP address`
1. Erstellen Sie eine `Linux` Benutzer für [!DNL Commerce Intelligence]
1. Erstellen Sie eine `MySQL` Benutzer für [!DNL Commerce Intelligence]
1. Geben Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]


## Abrufen der [!DNL Commerce Intelligence] öffentlicher Schlüssel {#retrieve}

Die `public key` wird verwendet, um die [!DNL Commerce Intelligence] `Linux` Benutzer. Im nächsten Abschnitt erstellen Sie den Benutzer und importieren den Schlüssel.

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**.
1. Klicken Sie auf `MySQL` Symbol.
1. Nach dem `MySQL credentials` Seite geöffnet wird, legen Sie die `Encrypted` Umschalten auf `Yes`. Dadurch wird das SSH-Setup-Formular angezeigt.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

So navigieren Sie durch [!DNL Commerce Intelligence] , um den Schlüssel abzurufen:

![](../../../assets/MySQL_SSH.gif)<!--{: width="770"}-->

## Zugriff auf [!DNL Commerce Intelligence] IP-Adresse {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151` aber sie befinden sich auch auf der `MySQL credentials` Seite. Siehe blaue Box in der obigen GIF.

## Erstellen einer [!DNL Linux] Benutzer für [!DNL Commerce Intelligence] {#linux}

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können [diesen Benutzer einschränken](../../../administrator/account-management/restrict-db-access.md) wie Sie möchten, solange es das Recht behält, eine Verbindung mit dem `MySQL` Server.

1. Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stamm auf Ihrem [!DNL Linux] server:

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
>Wenn die Variable `sshd\_config` -Datei, die mit dem Server verknüpft ist, nicht auf die Standardoption festgelegt, sondern nur bestimmte Benutzer haben Serverzugriff. Dies verhindert eine erfolgreiche Verbindung zu [!DNL Commerce Intelligence]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` , um `rjmetric` Benutzerzugriff auf den Server.

## Erstellen einer [!DNL MySQL] Benutzer für [!DNL Commerce Intelligence] {#mysql}

Ihr Unternehmen erfordert möglicherweise einen anderen Prozess, aber die einfachste Möglichkeit, diesen Benutzer zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie sich bei anmelden [!DNL MySQL] als Benutzer mit dem Recht, Berechtigungen zu gewähren:

```sql
    GRANT SELECT ON *.* TO 'rjmetric'@'localhost' IDENTIFIED BY '<secure password here>';
```

Ersetzen `secure password here` mit einem sicheren Kennwort, das sich von der `SSH` Kennwort.

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen GRANT-Abfragen ausführen, die nur den Zugriff auf die Daten ermöglichen, die Sie zulassen.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]. Hast du die `MySQL credentials` Seite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann [!DNL MySQL] Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem `Database Connection` Abschnitt:

* `Username`: Der Benutzername für die [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Password`: Das Kennwort für die [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Port`: [!DNL MySQL] Anschluss auf Ihrem Server (standardmäßig 3306)
* `Host` Standardmäßig ist dies localhost. Im Allgemeinen ist dies der bind-address-Wert für Ihre [!DNL MySQL] server, der standardmäßig `127.0.0.1 (localhost)`, kann aber auch eine lokale Netzwerkadresse sein (z. B. `192.168.0.1`) oder der öffentlichen IP-Adresse Ihres Servers.

   Der Wert befindet sich in der `my.cnf` Datei (befindet sich unter `/etc/my.cnf`) unter der Zeile, die lautet `\[mysqld\]`. Wenn die bind-address-Zeile in dieser Datei auskommentiert ist, wird Ihr Server vor externen Verbindungsversuchen geschützt.

Im `SSH Connection` Abschnitt:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers [!DNL Commerce Intelligence] in den
* `Username`: Der Benutzername für die [!DNL Commerce Intelligence] SSH ([!DNL Linux]) Benutzer
* `SSH Port`: SSH-Anschluss auf Ihrem Server (standardmäßig 22)

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
