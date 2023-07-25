---
title: Anbinden von PostgreSQL über den SSH-Tunnel
description: Erfahren Sie, wie Sie Ihre PostgreSQL-Datenbank über einen SSH-Tunnel mit Commerce Intelligence verbinden.
exl-id: da610988-21c1-4f5f-b4e2-e2deb175a2aa
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Verbinden [!DNL PostgreSQL] via [!DNL SSH Tunnel]

Um eine Verbindung herzustellen [!DNL PostgreSQL] Datenbank zu [!DNL Commerce Intelligence] über eine `SSH tunnel`müssen Sie einige Schritte ausführen:

1. [Rufen Sie die [!DNL Commerce Intelligence] öffentlicher Schlüssel](#retrieve)
1. [Zugriff auf [!DNL Commerce Intelligence] IP-Adresse](#allowlist)
1. [Erstellen Sie eine [!DNL Linux] Benutzer für [!DNL Commerce Intelligence]](#linux)
1. [Erstellen Sie eine [!DNL PostgreSQL] Benutzer für [!DNL Commerce Intelligence]](#postgres)
1. [Geben Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]](#finish)

## Abrufen der [!DNL Commerce Intelligence] [!DNL public key] {#retrieve}

Die `public key` wird verwendet, um die [!DNL Commerce Intelligence] [!DNL Linux] Benutzer. Jetzt erstellen Sie den Benutzer und importieren den Schlüssel.

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]**.
1. Klicken Sie auf [!DNL PostgreSQL] Symbol.
1. Nach dem `PostgreSQL credentials` Seite geöffnet wird, legen Sie die `Encrypted` Umschalten auf `Yes`. Dadurch wird die `SSH` Formular einrichten.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Nachstehend wird gezeigt, wie Sie durch [!DNL Commerce Intelligence] , um den Schlüssel abzurufen:

![Abrufen des öffentlichen Schlüssels &quot;RJMetrics&quot;](../../../assets/get-mbi-public-key.gif)

## Zugriff auf [!DNL Commerce Intelligence] IP-Adresse {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihrer IP-Adresse aus gestattet wird. Es ist `54.88.76.97/32`, aber es befindet sich auch auf der `PostgreSQL` Seite mit Anmeldeinformationen. Siehe blaue Box in der obigen GIF.

## Erstellen einer [!DNL Linux] Benutzer für [!DNL Commerce Intelligence] {#linux}

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können [diesen Benutzer einschränken](../../../administrator/account-management/restrict-db-access.md) wie Sie möchten, solange es das Recht behält, eine Verbindung mit dem [!DNL PostgreSQL] Server.

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
```

>[!IMPORTANT]
>
>Wenn die Variable `sshd\_config` -Datei, die mit dem Server verknüpft ist, nicht auf die Standardoption festgelegt, sondern nur bestimmte Benutzer haben Serverzugriff. Dies verhindert eine erfolgreiche Verbindung zu [!DNL Commerce Intelligence]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` , um dem rjmetric-Benutzer Zugriff auf den Server zu gewähren.

## Erstellen einer [!DNL Commerce Intelligence] [!DNL Postgres] Benutzer {#postgres}

Ihr Unternehmen erfordert möglicherweise einen anderen Prozess. Die einfachste Möglichkeit zum Erstellen dieses Benutzers besteht jedoch darin, die folgende Abfrage auszuführen, wenn Sie sich bei Postgres als Benutzer mit der Berechtigung zum Gewähren von Berechtigungen anmelden. Der Benutzer sollte auch Eigentümer des Schemas sein, das [!DNL Commerce Intelligence] wird Zugriff auf gewährt.

```sql
    GRANT CONNECT ON DATABASE <database name> TO rjmetric WITH PASSWORD <secure password>;GRANT USAGE ON SCHEMA <schema name> TO rjmetric;GRANT SELECT ON ALL TABLES IN SCHEMA <schema name> TO rjmetric;ALTER DEFAULT PRIVILEGES IN SCHEMA <schema name> GRANT SELECT ON TABLES TO rjmetric;
```

Ersetzen `secure password` mit Ihrem eigenen sicheren Kennwort, das vom SSH-Kennwort abweichen kann. Stellen Sie außerdem sicher, dass Sie `database name` und `schema name` mit den entsprechenden Namen in Ihrer Datenbank.

Wenn Sie mehrere Datenbanken oder Schemata verbinden möchten, wiederholen Sie diesen Vorgang nach Bedarf.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]. Hast du die [!DNL PostgreSQL] Berechtigungsseite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data > Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]**, dann [!DNL PostgreSQL] Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem `Database Connection` Abschnitt:

* `Username`: Der Benutzername RJMetrics Postgres (sollte rjmetric sein)
* `Password`: Das Kennwort für RJMetrics Postgres
* `Port`: PostgreSQL-Anschluss auf Ihrem Server (standardmäßig 5432)
* `Host`: 127.0.0.1

under `SSH Connection`:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, auf dem SSH ausgeführt wird
* `Username`: Ihr SSH-Anmeldename (sollte rjmetric sein)
* `SSH Port`: SSH-Anschluss auf Ihrem Server (standardmäßig 22)

Wenn Sie fertig sind, klicken Sie auf **Speichern und testen** , um das Setup abzuschließen.

### Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
