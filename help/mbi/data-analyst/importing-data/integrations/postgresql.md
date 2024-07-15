---
title: PostgreSQL über den SSH-Tunnel verbinden
description: Erfahren Sie, wie Sie Ihre PostgreSQL-Datenbank über einen SSH-Tunnel mit Commerce Intelligence verbinden.
exl-id: da610988-21c1-4f5f-b4e2-e2deb175a2aa
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL PostgreSQL] über [!DNL SSH Tunnel] verbinden

Um Ihre [!DNL PostgreSQL] -Datenbank über eine `SSH tunnel` mit [!DNL Commerce Intelligence] zu verbinden, müssen Sie einige Schritte ausführen:

1. [Abrufen des öffentlichen Schlüssels [!DNL Commerce Intelligence] ](#retrieve)
1. [Zugriff auf die  [!DNL Commerce Intelligence] IP-Adresse zulassen](#allowlist)
1. [Erstellen eines [!DNL Linux] Benutzers für  [!DNL Commerce Intelligence]](#linux)
1. [Erstellen eines [!DNL PostgreSQL] Benutzers für  [!DNL Commerce Intelligence]](#postgres)
1. [Geben Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] ein.](#finish)

## Abrufen der [!DNL Commerce Intelligence] [!DNL public key] {#retrieve}

Der `public key` wird verwendet, um den [!DNL Commerce Intelligence] [!DNL Linux] Benutzer zu autorisieren. Jetzt erstellen Sie den Benutzer und importieren den Schlüssel.

1. Gehen Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]**.
1. Klicken Sie auf das Symbol &quot;[!DNL PostgreSQL]&quot;.
1. Nachdem die Seite `PostgreSQL credentials` geöffnet wurde, stellen Sie den Umschalter `Encrypted` auf `Yes` ein. Dadurch wird das Setup-Formular `SSH` angezeigt.
1. Die `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Nachstehend wird gezeigt, wie Sie durch [!DNL Commerce Intelligence] navigieren, um den Schlüssel abzurufen:

![Abrufen des öffentlichen Schlüssels &quot;RJMetrics&quot;](../../../assets/get-mbi-public-key.gif)

## Zugriff auf die [!DNL Commerce Intelligence] -IP-Adresse zulassen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass sie den Zugriff von Ihrer IP-Adresse aus gestattet. Er ist `54.88.76.97/32`, befindet sich aber auch auf der Seite mit den Anmeldedaten für `PostgreSQL`. Siehe blaue Box in der obigen GIF.

## Erstellen eines [!DNL Linux] Benutzers für [!DNL Commerce Intelligence] {#linux}

Dabei kann es sich um eine Produktions- oder Sekundärmaschine handeln, sofern diese Daten in Echtzeit (oder häufig aktualisiert) enthält. Sie können [diesen Benutzer auf beliebige Weise einschränken](../../../administrator/account-management/restrict-db-access.md), solange er das Recht behält, eine Verbindung zum [!DNL PostgreSQL]-Server herzustellen.

1. Um den neuen Benutzer hinzuzufügen, führen Sie die folgenden Befehle als Stamm auf Ihrem [!DNL Linux]-Server aus:

```bash
        adduser rjmetric -p<password>
        mkdir /home/rjmetric
        mkdir /home/rjmetric/.ssh
```

1. Erinnern Sie sich an die `public key`, die Sie im ersten Abschnitt abgerufen haben? Um sicherzustellen, dass der Benutzer Zugriff auf die Datenbank hat, müssen Sie den Schlüssel in `authorized\_keys` importieren.

   Kopieren Sie den gesamten Schlüssel wie folgt in die Datei `authorized\_keys` :

```bash
        touch /home/rjmetric/.ssh/authorized_keys
        "<PASTE KEY HERE>" >> /home/rjmetric/.ssh/authorized_keys
```

1. Um die Erstellung des Benutzers abzuschließen, ändern Sie die Berechtigungen für den Ordner &quot;`/home/rjmetric`&quot;, um den Zugriff über `SSH` zu ermöglichen:

```bash
        chown -R rjmetric:rjmetric /home/rjmetric
        chmod -R 700 /home/rjmetric/.ssh
```

>[!IMPORTANT]
>
>Wenn die mit dem Server verknüpfte `sshd\_config` -Datei nicht auf die Standardoption festgelegt ist, haben nur bestimmte Benutzer Zugriff auf den Server. Dies verhindert eine erfolgreiche Verbindung zu [!DNL Commerce Intelligence]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` auszuführen, um dem rjmetric-Benutzer Zugriff auf den Server zu gewähren.

## Erstellen eines [!DNL Commerce Intelligence] [!DNL Postgres] Benutzers {#postgres}

Ihr Unternehmen erfordert möglicherweise einen anderen Prozess. Die einfachste Möglichkeit zum Erstellen dieses Benutzers besteht jedoch darin, die folgende Abfrage auszuführen, wenn Sie sich bei Postgres als Benutzer mit der Berechtigung zum Gewähren von Berechtigungen anmelden. Dem Benutzer sollte auch das Schema gehören, auf das [!DNL Commerce Intelligence] Zugriff erhält.

```sql
    GRANT CONNECT ON DATABASE <database name> TO rjmetric WITH PASSWORD <secure password>;GRANT USAGE ON SCHEMA <schema name> TO rjmetric;GRANT SELECT ON ALL TABLES IN SCHEMA <schema name> TO rjmetric;ALTER DEFAULT PRIVILEGES IN SCHEMA <schema name> GRANT SELECT ON TABLES TO rjmetric;
```

Ersetzen Sie `secure password` durch Ihr eigenes sicheres Kennwort, das vom SSH-Kennwort abweichen kann. Stellen Sie außerdem sicher, dass Sie `database name` und `schema name` durch die entsprechenden Namen in Ihrer Datenbank ersetzen.

Wenn Sie mehrere Datenbanken oder Schemata verbinden möchten, wiederholen Sie diesen Prozess nach Bedarf.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den Anmeldedaten für [!DNL PostgreSQL] geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data > Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]**, dann auf das Symbol [!DNL PostgreSQL]. Vergessen Sie nicht, den Umschalter `Encrypted` auf `Yes` festzulegen.

Geben Sie die folgenden Informationen in diese Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Username`: Der Benutzername RJMetrics Postgres (sollte rjmetric sein)
* `Password`: Das RJMetrics Postgres-Kennwort
* `Port`: PostgreSQL-Anschluss auf Ihrem Server (standardmäßig 5432)
* `Host`: 127.0.0.1

Unter `SSH Connection`:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, in den Sie SSH durchführen werden
* `Username`: Ihr SSH-Anmeldename (sollte rjmetric sein)
* `SSH Port`: SSH-Port auf Ihrem Server (standardmäßig 22)

Klicken Sie abschließend auf **Speichern und testen** , um das Setup abzuschließen.

### Verwandte

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
