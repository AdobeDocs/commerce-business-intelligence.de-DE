---
title: Verbinden von [!DNL MongoDB] über SSH-Tunnel
description: Erfahren Sie, wie Sie [!DNL MongoDB] über den SSH-Tunnel verbinden.
exl-id: 3557a8c7-c4c5-4742-ae30-125c719aca39
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# [!DNL MongoDB] über SSH-Tunnel verbinden

Um Ihre [!DNL MongoDB] -Datenbank über einen SSH-Tunnel mit [!DNL Commerce Intelligence] zu verbinden, müssen Sie einige Schritte unternehmen:

1. [Abrufen des öffentlichen Schlüssels [!DNL Commerce Intelligence] ](#retrieve)
1. [Zugriff auf die  [!DNL Commerce Intelligence] IP-Adresse zulassen](#allowlist)
1. [Linux-Benutzer für Commerce Intelligence erstellen](#linux)
1. [Erstellen eines [!DNL MongoDB] Benutzers für Commerce Intelligence](#mongodb)
1. [Geben Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] ein.](#finish)

>[!NOTE]
>
>Aufgrund des technischen Charakters dieses Setups empfiehlt Adobe, dass Sie in einem Entwickler eine Schleife durchführen, um herauszufinden, ob Sie dies noch nicht getan haben.

## Abrufen des öffentlichen Schlüssels [!DNL Commerce Intelligence] {#retrieve}

Der `public key` wird verwendet, um den [!DNL Commerce Intelligence] `Linux` Benutzer zu autorisieren. Der nächste Abschnitt erläutert Ihnen schrittweise, wie Sie den Benutzer erstellen und die Schlüssel importieren können.

1. Gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**.
1. Klicken Sie auf das Symbol &quot;[!DNL MONGODB]&quot;.
1. Nachdem die Seite mit den Anmeldedaten für [!DNL MongoDB] geöffnet wurde, ändern Sie den Umschalter für `Encrypted` in `Yes`. Dadurch wird das SSH-Setup-Formular angezeigt.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Wenn Sie etwas verloren haben, können Sie hier durch [!DNL Commerce Intelligence] navigieren, um den Schlüssel abzurufen:

![Abrufen des öffentlichen Schlüssels &quot;RJMetrics&quot;](../../../assets/MongoDB_Public_Key.gif)<!--{:.zoom}-->

## Zugriff auf die [!DNL Commerce Intelligence] -IP-Adresse zulassen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151`, befinden sich aber auch auf der Seite mit den Anmeldedaten für [!DNL MongoDB]:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen eines `Linux` Benutzers für [!DNL Commerce Intelligence] {#linux}

>[!IMPORTANT]
>
>Wenn die mit dem Server verknüpfte `sshd_config` -Datei nicht auf die Standardoption festgelegt ist, haben nur bestimmte Benutzer Zugriff auf den Server. Dies verhindert eine erfolgreiche Verbindung zu [!DNL Commerce Intelligence]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` auszuführen, um dem `rjmetric` -Benutzer Zugriff auf den Server zu gewähren.

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können diesen Benutzer beliebig einschränken, solange er das Recht behält, eine Verbindung zum [!DNL MongoDB] -Server herzustellen.

Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stamm auf Ihrem `Linux`-Server aus:

```bash
    adduser rjmetric -p
    mkdir /home/rjmetric
    mkdir /home/rjmetric/.ssh
```

Erinnern Sie sich an die `public key`, die Sie im ersten Abschnitt abgerufen haben? Um sicherzustellen, dass der Benutzer Zugriff auf die Datenbank hat, müssen Sie den Schlüssel in `authorized_keys` importieren. Kopieren Sie den gesamten Schlüssel wie folgt in die Datei `authorized_keys` :

```bash
    touch /home/rjmetric/.ssh/authorized_keys
    "< PASTE KEY HERE >" >> /home/rjmetric/.ssh/authorized_keys
```

Um die Erstellung des Benutzers abzuschließen, ändern Sie die Berechtigungen für den Ordner /home/rjmetric , um den Zugriff über SSH zuzulassen:

```bash
    chown -R rjmetric:rjmetric /home/rjmetric
    chmod -R 700 /home/rjmetric/.ssh
```

## Erstellen eines [!DNL Commerce Intelligence] [!DNL MongoDB] Benutzers {#mongodb}

[!DNL MongoDB] -Server haben zwei Ausführungsmodi: [einer mit der Option &quot;auth&quot;](#auth) `(mongod -- auth)` und einer ohne, [der Standardmodus](#default). Die Schritte zum Erstellen eines [!DNL MongoDB] -Benutzers hängen davon ab, welchen Modus Ihr Server verwendet. Überprüfen Sie den Modus, bevor Sie fortfahren.

### Wenn Ihr Server die Option `Auth` verwendet: {#auth}

Wenn Sie eine Verbindung zu mehreren Datenbanken herstellen, können Sie den Benutzer hinzufügen, indem Sie sich bei [!DNL MongoDB] als Administrator anmelden und die folgenden Befehle ausführen.

>[!NOTE]
>
>Zum Anzeigen aller verfügbaren Datenbanken benötigt der Benutzer [!DNL Commerce Intelligence] die Berechtigung zum Ausführen von `listDatabases.`

Mit diesem Befehl wird dem [!DNL Commerce Intelligence] -Benutzer Zugriff auf `to all databases` gewährt:

```bash
    use admin
    db.createUser('rjmetric', '< secure password here >', true)
```

Verwenden Sie diesen Befehl, um den [!DNL Commerce Intelligence] Benutzerzugriff `to a single database` zu gewähren:

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

Wenn Ihr Server den Modus `auth` nicht verwendet, ist Ihr [!DNL MongoDB] -Server auch ohne Benutzernamen und Kennwort zugänglich. Sie sollten jedoch sicherstellen, dass die `mongodb.conf`-Datei `(/etc/mongodb.conf)` die folgenden Zeilen enthält. Wenn nicht, starten Sie Ihren Server neu, nachdem Sie sie hinzugefügt haben.

```bash
    bind_ip = 127.0.0.1
    noauth = true
```

Um Ihren [!DNL MongoDB] -Server an eine andere Adresse zu binden, passen Sie den Datenbank-Hostnamen im nächsten Schritt entsprechend an.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den Anmeldedaten für [!DNL MongoDB] geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Data > Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann auf das Symbol [!DNL MongoDB]. Vergessen Sie nicht, den Umschalter `Encrypted` auf `Yes` zu ändern.

Geben Sie die folgenden Informationen in diese Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Host`: `127.0.0.1`
* `Username`: Der Benutzername [!DNL Commerce Intelligence] [!DNL MongoDB] (sollte `rjmetric` sein)
* `Password`: Das Kennwort [!DNL Commerce Intelligence] [!DNL MongoDB]
* `Port`: MongoDB-Anschluss auf Ihrem Server (standardmäßig `27017`)
* `Database Name` (Optional): Wenn Sie nur den Zugriff auf eine Datenbank zugelassen haben, geben Sie hier den Namen dieser Datenbank an.

Unter dem Abschnitt `SSH Connection` :

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, in den Sie SSH durchführen werden
* `Username`: Der Benutzername für [!DNL Commerce Intelligence] Linux (SSH) (sollte rjmetric sein)
* `SSH Port`: Der SSH-Port auf Ihrem Server (standardmäßig 22)

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save Test]** , um das Setup abzuschließen.

### Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
