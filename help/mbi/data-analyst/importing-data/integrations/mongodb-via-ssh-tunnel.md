---
title: Verbinden [!DNL MongoDB] über SSH-Tunnel
description: Erfahren Sie, wie Sie eine Verbindung herstellen [!DNL MongoDB] über SSH-Tunnel.
exl-id: 3557a8c7-c4c5-4742-ae30-125c719aca39
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# Verbinden [!DNL MongoDB] über SSH-Tunnel

Um eine Verbindung herzustellen [!DNL MongoDB] Datenbank zu [!DNL MBI] über einen SSH-Tunnel müssen Sie (oder Ihr Team, falls Sie kein Techniker sind) einige Dinge tun:

1. [Rufen Sie die [!DNL MBI] öffentlicher Schlüssel](#retrieve)
1. [Zugriff auf [!DNL MBI] IP-Adresse](#allowlist)
1. [Linux erstellen](#linux)
1. [Erstellen Sie eine [!DNL MongoDB] Benutzer für MBI](#mongodb)
1. [Geben Sie die Verbindung und Benutzerinformationen in [!DNL MBI]](#finish)

>[!NOTE]
>
>Aufgrund des technischen Charakters dieses Setups empfiehlt Adobe, in einem Entwickler eine Schleife durchzuführen, um herauszufinden, ob Sie dies noch nicht getan haben.

## Abrufen der [!DNL MBI] öffentlicher Schlüssel {#retrieve}

Die `public key` wird verwendet, um die [!DNL MBI] `Linux` Benutzer. Der nächste Abschnitt erläutert Ihnen schrittweise, wie Sie den Benutzer erstellen und die Schlüssel importieren können.

1. Navigieren Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**.
1. Klicken Sie auf [!DNL MONGODB] Symbol.
1. Nach dem [!DNL MongoDB] Die Seite mit den Anmeldedaten wird geöffnet. Ändern Sie `Encrypted` Umschalten auf `Yes`. Dadurch wird das SSH-Setup-Formular angezeigt.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Wenn Sie etwas verloren sind, können Sie hier navigieren [!DNL MBI] , um den Schlüssel abzurufen:

![Abrufen des öffentlichen Schlüssels &quot;RJMetrics&quot;](../../../assets/MongoDB_Public_Key.gif)<!--{:.zoom}-->

## Zugriff auf [!DNL MBI] IP-Adresse {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151`, aber es befindet sich auch auf der [!DNL MongoDB] Anmeldeseite:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen einer `Linux` Benutzer für [!DNL MBI] {#linux}

>[!IMPORTANT]
>
>Wenn die Variable `sshd_config` -Datei, die mit dem Server verknüpft ist, nicht auf die Standardoption festgelegt, sondern nur bestimmte Benutzer haben Serverzugriff. Dies verhindert eine erfolgreiche Verbindung zu [!DNL MBI]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` , um `rjmetric` Benutzerzugriff auf den Server.

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können diesen Benutzer beliebig einschränken, solange er das Recht behält, sich mit dem [!DNL MongoDB] Server.

Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stamm auf Ihrem `Linux` server:

```bash
    adduser rjmetric -p
    mkdir /home/rjmetric
    mkdir /home/rjmetric/.ssh
```

Speichern Sie die `public key` Sie haben im ersten Abschnitt abgerufen? Um sicherzustellen, dass der Benutzer Zugriff auf die Datenbank hat, müssen Sie den Schlüssel in `authorized_keys`. Kopieren Sie den gesamten Schlüssel in die `authorized_keys` Datei wie folgt:

```bash
    touch /home/rjmetric/.ssh/authorized_keys
    "< PASTE KEY HERE >" >> /home/rjmetric/.ssh/authorized_keys
```

Um die Erstellung des Benutzers abzuschließen, ändern Sie die Berechtigungen für den Ordner /home/rjmetric , um den Zugriff über SSH zuzulassen:

```bash
    chown -R rjmetric:rjmetric /home/rjmetric
    chmod -R 700 /home/rjmetric/.ssh
```

## Erstellen einer [!DNL MBI] [!DNL MongoDB] Benutzer {#mongodb}

[!DNL MongoDB] -Server haben zwei Ausführungsmodi: [mit der Option &quot;auth&quot;](#auth) `(mongod -- auth)` und ohne [, der standardmäßig](#default). Die Schritte zum Erstellen einer [!DNL MongoDB] Der Benutzer variiert je nach verwendetem Modus. Überprüfen Sie den Modus, bevor Sie fortfahren.

### Wenn Ihr Server `Auth` Option: {#auth}

Wenn Sie eine Verbindung zu mehreren Datenbanken herstellen, können Sie den Benutzer hinzufügen, indem Sie sich bei [!DNL MongoDB] als Administrator verwenden und die folgenden Befehle ausführen.

>[!NOTE]
>
>Um alle verfügbaren Datenbanken anzuzeigen, muss die [!DNL MBI] Der Benutzer benötigt die Berechtigungen zum Ausführen `listDatabases.`

Mit diesem Befehl wird [!DNL MBI] Benutzerzugriff `to all databases`:

```bash
    use admin
    db.createUser('rjmetric', '< secure password here >', true)
```

Verwenden Sie diesen Befehl, um die [!DNL MBI] Benutzerzugriff `to a single database`:

```bash
    use < database name >
    db.createUser('rjmetric', '< secure password here >', true)
```

Dadurch wird eine Antwort wie die folgende ausgegeben:

```bash
    {
    "id": ObjectId("< some object id here >"),
    "user": "rjmetric",
    "readOnly": true,
    "pwd": "< some hash here >"
    }
```

### Wenn Ihr Server die Standardoption verwendet {#default}

Wenn Ihr Server nicht verwendet `auth` mode, Ihre [!DNL MongoDB] auf den Server auch ohne Benutzernamen und Kennwort zugegriffen werden kann. Sie sollten jedoch sicherstellen, dass die `mongodb.conf` file `(/etc/mongodb.conf)` weist die folgenden Zeilen auf - wenn nicht, starten Sie Ihren Server neu, nachdem Sie sie hinzugefügt haben.

```bash
    bind_ip = 127.0.0.1
    noauth = true
```

So binden Sie Ihre [!DNL MongoDB] an eine andere Adresse zu senden, passen Sie den Datenbank-Hostnamen im nächsten Schritt entsprechend an.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL MBI] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL MBI]. Hast du die [!DNL MongoDB] Berechtigungsseite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Data > Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann [!DNL MongoDB] Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem `Database Connection` Abschnitt:

* `Host`: `127.0.0.1`
* `Username`: Die [!DNL MBI] [!DNL MongoDB] Benutzername (sollte `rjmetric`)
* `Password`: Die [!DNL MBI] [!DNL MongoDB] password
* `Port`: MongoDB-Anschluss auf Ihrem Server (`27017` standardmäßig)
* `Database Name` (Optional): Wenn Sie nur Zugriff auf eine Datenbank gewährt haben, geben Sie hier den Namen dieser Datenbank an.

Unter dem `SSH Connection` Abschnitt:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, auf dem SSH ausgeführt wird
* `Username`: Die [!DNL MBI] Linux® (SSH)-Benutzername (sollte rjmetric sein)
* `SSH Port`: Der SSH-Port auf Ihrem Server (standardmäßig 22)

Das ist es! Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save Test]** , um das Setup abzuschließen.

### Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
