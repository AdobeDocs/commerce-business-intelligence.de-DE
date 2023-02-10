---
title: Anbinden von PostgreSQL über den SSH-Tunnel
description: Erfahren Sie, wie Sie Ihre PostgreSQL-Datenbank mit [!DNL MBI] über einen SSH-Tunnel.
exl-id: da610988-21c1-4f5f-b4e2-e2deb175a2aa
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Verbinden `PostgreSQL` via `SSH` Tunnel

Um eine Verbindung herzustellen `PostgreSQL` Datenbank zu [!DNL MBI] über eine `SSH tunnel`, müssen Sie (oder Ihr Team, falls Sie kein Techie sind) einige Dinge tun:

1. [Rufen Sie die [!DNL MBI] öffentlicher Schlüssel](#retrieve)
1. [Zugriff auf [!DNL MBI] IP-Adresse](#allowlist)
1. [Erstellen eines Linux-Benutzers für [!DNL MBI] ](#linux)
1. [Erstellen eines Postgres-Benutzers für [!DNL MBI] ](#postgres)
1. [Verbindung und Benutzerinformationen in MBI eingeben](#finish)

Es ist nicht so kompliziert, wie es klingen könnte. Erste Schritte.

## Abrufen der [!DNL MBI] `public key` {#retrieve}

Die `public key` wird verwendet, um die [!DNL MBI] Linux-Benutzer. Im nächsten Abschnitt erstellen wir den Benutzer und importieren den Schlüssel.

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]**.
1. Klicken Sie auf `PostgreSQL` Symbol.
1. Nach dem `PostgreSQL credentials` Seite geöffnet wird, legen Sie die `Encrypted` Umschalten auf `Yes`. Dadurch wird die `SSH` Formular einrichten.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Wenn Sie etwas verloren sind, können Sie hier navigieren [!DNL MBI] , um den Schlüssel abzurufen:

![Abrufen des öffentlichen Schlüssels &quot;RJMetrics&quot;](../../../assets/get-mbi-public-key.gif)

## Zugriff auf [!DNL MBI] IP-Adresse {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, muss Ihre Firewall so konfiguriert werden, dass sie den Zugriff von unserer IP-Adresse aus gestattet. it `54.88.76.97/32`, aber es befindet sich auch auf der `PostgreSQL` Seite mit Anmeldeinformationen. Sehen Sie die blaue Box in der GIF oben? Das ist es!

## Erstellen einer `Linux` Benutzer für [!DNL MBI] {#linux}

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können [diesen Benutzer einschränken](../../../administrator/account-management/restrict-db-access.md) wie Sie möchten, solange es das Recht behält, eine Verbindung zum PostgreSQL Server herzustellen.

1. Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stamm auf Ihrem `Linux` server:

```bash
        adduser rjmetric -p<password>
        mkdir /home/rjmetric
        mkdir /home/rjmetric/.ssh
```

1. Speichern Sie die `public key` haben wir im ersten Abschnitt abgerufen? Um sicherzustellen, dass der Benutzer Zugriff auf die Datenbank hat, müssen wir den Schlüssel in `authorized\_keys`.

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
>Wenn die Variable `sshd\_config` -Datei, die mit dem Server verknüpft ist, nicht auf die Standardoption festgelegt ist, haben nur bestimmte Benutzer Zugriff auf den Server. Dadurch wird verhindert, dass eine erfolgreiche Verbindung zu [!DNL MBI]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` , um dem rjmetric-Benutzer Zugriff auf den Server zu gewähren.

## Erstellen einer [!DNL MBI] Postgres-Benutzer {#postgres}

Ihr Unternehmen erfordert möglicherweise einen anderen Prozess. Die einfachste Möglichkeit zum Erstellen dieses Benutzers besteht jedoch darin, die folgende Abfrage auszuführen, wenn Sie sich bei Postgres als Benutzer mit der Berechtigung zum Gewähren von Berechtigungen anmelden. Der Benutzer sollte auch Eigentümer des Schemas sein, das [!DNL MBI] wird Zugriff auf gewährt.

```sql
    GRANT CONNECT ON DATABASE <database name> TO rjmetric WITH PASSWORD <secure password>;GRANT USAGE ON SCHEMA <schema name> TO rjmetric;GRANT SELECT ON ALL TABLES IN SCHEMA <schema name> TO rjmetric;ALTER DEFAULT PRIVILEGES IN SCHEMA <schema name> GRANT SELECT ON TABLES TO rjmetric;
```

Ersetzen `secure password` mit Ihrem eigenen sicheren Kennwort, das sich vom SSH-Kennwort unterscheiden kann. Stellen Sie außerdem sicher, dass Sie `database name` und `schema name` mit den entsprechenden Namen in Ihrer Datenbank.

Wenn Sie mehrere Datenbanken oder Schemata verbinden möchten, wiederholen Sie diesen Vorgang nach Bedarf.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL MBI] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL MBI]. Haben Sie die Seite mit den PostgreSQL-Anmeldedaten geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data > Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]** und dann das PostgreSQL-Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem Abschnitt Datenbankverbindung :

* `Username`: Der Benutzername RJMetrics Postgres (sollte rjmetric sein)
* `Password`: Das Kennwort für RJMetrics Postgres
* `Port`: PostgreSQL-Anschluss auf Ihrem Server (standardmäßig 5432)
* `Host`: 127.0.0.1

under `SSH Connection`:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, in den wir SSH durchführen werden
* `Username`: Unser SSH-Anmeldename (sollte rjmetric sein)
* `SSH Port`: SSH-Anschluss auf Ihrem Server (standardmäßig 22)

Das ist es! Wenn Sie fertig sind, klicken Sie auf **Speichern und testen** , um das Setup abzuschließen.

### Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
