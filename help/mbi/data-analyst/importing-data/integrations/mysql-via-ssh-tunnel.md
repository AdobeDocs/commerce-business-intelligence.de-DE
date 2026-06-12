---
title: Verbindung  [!DNL MySQL]  SSH-Tunnel
description: Erfahren Sie, wie Sie eine Verbindung  [!DNL MySQL]  SSH-Tunnel herstellen.
exl-id: 6b691a6a-9542-4e47-9b1d-d6d3c3dac357
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
TQID: https://experienceleague.adobe.com/WhcwNz65oubtSKnVGeoHfbEVbPvo1fq-RvpAcP96NEc
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 3a6b80d7bcfa5db4d86ab4da81239e3ea804f6ad
workflow-type: tm+mt
source-wordcount: 642
ht-degree: 0%

---

# [!DNL MySQL] über [!DNL SSH Tunnel] verbinden

* [Abrufen des  [!DNL Commerce Intelligence]  Schlüssels](#retrieve)
* [Zugriff auf die IP [!DNL Commerce Intelligence] Adresse zulassen](#allowlist)
* [Linux-Benutzer für erstellen [!DNL Commerce Intelligence]](#linux)
* [Erstellen Sie  [!DNL MySQL]  Benutzer für [!DNL Commerce Intelligence]](#mysql)
* [Geben Sie die Verbindungs- und Benutzerinformationen in ein [!DNL Commerce Intelligence]](#finish)

## SPRINGEN ZU

* [[!DNL MySQL] über `direct connection`](../integrations/mysql-via-a-direct-connection.md)
* [[!DNL MySQL] über [!DNL cPanel]](../integrations/mysql-via-cpanel.md)

Um Ihre [!DNL MySQL] Datenbank über eine `SSH tunnel` mit [!DNL Commerce Intelligence] zu verbinden, müssen Sie einige Schritte ausführen:

1. [!DNL Commerce Intelligence] `public key` abrufen
1. Zulassen des Zugriffs auf [!DNL Commerce Intelligence] `IP address`
1. Erstellen eines `Linux` Benutzers für [!DNL Commerce Intelligence]
1. Erstellen eines `MySQL` Benutzers für [!DNL Commerce Intelligence]
1. Geben Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] ein


## Abrufen des [!DNL Commerce Intelligence] öffentlichen Schlüssels {#retrieve}

Die `public key` wird verwendet, um den [!DNL Commerce Intelligence] `Linux` Benutzer zu autorisieren. Im nächsten Abschnitt erstellen Sie den Benutzer und importieren den Schlüssel.

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**.
1. Klicken Sie auf das Symbol `MySQL` .
1. Nachdem die Seite `MySQL credentials` geöffnet wurde, legen Sie den Umschalter `Encrypted` auf `Yes` fest. Dadurch wird das SSH-Setup-Formular angezeigt.
1. Der `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des gesamten Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

So navigieren Sie durch [!DNL Commerce Intelligence], um den Schlüssel abzurufen:

![Animierte Demonstration der MySQL-Verbindung über SSH-Tunnel](../../../assets/MySQL_SSH.gif)<!--{: width="770"}-->

## Zugriff auf die [!DNL Commerce Intelligence] IP-Adresse zulassen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff über Ihre IP-Adressen zulässig ist. Sie sind `54.88.76.97` und `34.250.211.151`, aber sie befinden sich auch auf der `MySQL credentials`. Siehe das blaue Kästchen oben in der GIF.

## Erstellen eines [!DNL Linux] Benutzers für [!DNL Commerce Intelligence] {#linux}

Dabei kann es sich um einen Produktions- oder Sekundärrechner handeln, sofern er Echtzeitdaten (oder häufig aktualisierte Daten) enthält. Sie können [diesen Benutzer &#x200B;](../../../administrator/account-management/restrict-db-access.md) beliebiger Weise einschränken, solange er das Recht behält, eine Verbindung zum `MySQL`-Server herzustellen.

1. Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stammordner auf Ihrem [!DNL Linux] aus:

```bash
        adduser rjmetric -p<password>
        mkdir /home/rjmetric
        mkdir /home/rjmetric/.ssh
```

1. Erinnern Sie sich an die `public key`, die Sie im ersten Abschnitt abgerufen haben? Um sicherzustellen, dass der Benutzer Zugriff auf die Datenbank hat, müssen Sie den Schlüssel in `authorized\_keys` importieren.

   Kopieren Sie den gesamten Schlüssel wie folgt in die `authorized\_keys`-Datei:

```bash
        touch /home/rjmetric/.ssh/authorized_keys
        "<PASTE KEY HERE>" >> /home/rjmetric/.ssh/authorized_keys
```

1. Um die Erstellung des Benutzers abzuschließen, ändern Sie die Berechtigungen für das `/home/rjmetric`-Verzeichnis, um den Zugriff über `SSH` zuzulassen:

```bash
        chown -R rjmetric:rjmetric /home/rjmetric
        chmod -R 700 /home/rjmetric/.ssh
        chmod 400 /home/rjmetric/.ssh/authorized_keys
```

>[!IMPORTANT]
>
>Wenn für die mit dem Server verknüpfte `sshd\_config`-Datei nicht die Standardoption festgelegt ist, haben nur bestimmte Benutzer Serverzugriff. Dies verhindert eine erfolgreiche Verbindung mit [!DNL Commerce Intelligence]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` auszuführen, um dem `rjmetric` Zugriff auf den Server zu gewähren.

## Erstellen eines [!DNL MySQL] Benutzers für [!DNL Commerce Intelligence] {#mysql}

Ihr Unternehmen benötigt möglicherweise einen anderen Prozess, aber die einfachste Möglichkeit, diesen Benutzer zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie bei [!DNL MySQL] als ein Benutzer mit dem Recht angemeldet sind, Berechtigungen zu erteilen:

```sql
    GRANT SELECT ON *.* TO 'rjmetric'@'localhost' IDENTIFIED BY '<secure password here>';
```

Ersetzen Sie `secure password here` durch ein sicheres Kennwort, das sich vom `SSH` Kennwort unterscheiden kann.

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen GRANT-Abfragen ausführen, die nur den Zugriff auf die von Ihnen zulässigen Daten zulassen.

## Eingabe der Verbindungs- und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um alles abzuschließen, müssen Sie die Verbindung und die Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Habt ihr die `MySQL credentials` offen gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]** und dann auf das Symbol [!DNL MySQL] . Vergessen Sie nicht, den Umschalter `Encrypted` auf `Yes` zu setzen.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Username`: Der Benutzername für den [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Password`: Das Kennwort für den [!DNL Commerce Intelligence] [!DNL MySQL]
* `Port`: [!DNL MySQL] Port auf Ihrem Server (standardmäßig 3306)
* `Host` Standardmäßig ist dies localhost. Im Allgemeinen ist dies der Wert der Bindungsadresse für Ihren [!DNL MySQL]-Server, der standardmäßig `127.0.0.1 (localhost)` ist, aber auch eine lokale Netzwerkadresse (z. B. `192.168.0.1`) oder die öffentliche IP-Adresse Ihres Servers sein kann.

  Den Wert finden Sie in Ihrer `my.cnf`-Datei (unter `/etc/my.cnf`) unter der Zeile, die `\[mysqld\]` liest. Wenn die Zeile „bind-address“ in dieser Datei auskommentiert ist, ist Ihr Server vor externen Verbindungsversuchen geschützt.

Im `SSH Connection` Abschnitt:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, für den [!DNL Commerce Intelligence] einen Tunnel erstellt
* `Username`: Der Benutzername für den [!DNL Commerce Intelligence] SSH-Benutzer ([!DNL Linux])
* `SSH Port`: SSH-Port auf dem Server (standardmäßig 22)

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um die Einrichtung abzuschließen.

>[!NOTE]
>
>Informationen zu Registrierung, Aktualisierung, Fehlermeldungen und Fehlerbehebung für SSH-Hostschlüssel finden Sie unter [SSH-Hostschlüsselüberprüfung](ssh-host-key-verification.md).

## verwandt {#related}

* [Überprüfung des SSH-Hostschlüssels](ssh-host-key-verification.md)
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
