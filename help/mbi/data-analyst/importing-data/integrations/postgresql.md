---
title: PostgreSQL über SSH-Tunnel verbinden
description: Erfahren Sie, wie Sie Ihre PostgreSQL-Datenbank über einen SSH-Tunnel mit Commerce Intelligence verbinden.
exl-id: da610988-21c1-4f5f-b4e2-e2deb175a2aa
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# [!DNL PostgreSQL] über [!DNL SSH Tunnel] verbinden

Um Ihre [!DNL PostgreSQL] Datenbank über eine [!DNL Commerce Intelligence] mit `SSH tunnel` zu verbinden, müssen Sie einige Schritte ausführen:

1. [Abrufen des  [!DNL Commerce Intelligence]  Schlüssels](#retrieve)
1. [Zugriff auf die IP [!DNL Commerce Intelligence] Adresse zulassen](#allowlist)
1. [Erstellen Sie  [!DNL Linux]  Benutzer für [!DNL Commerce Intelligence]](#linux)
1. [Erstellen Sie  [!DNL PostgreSQL]  Benutzer für [!DNL Commerce Intelligence]](#postgres)
1. [Geben Sie die Verbindungs- und Benutzerinformationen in ein [!DNL Commerce Intelligence]](#finish)

## Abrufen der [!DNL Commerce Intelligence] [!DNL public key] {#retrieve}

Die `public key` wird verwendet, um den [!DNL Commerce Intelligence] [!DNL Linux] Benutzer zu autorisieren. Jetzt erstellen Sie den Benutzer und importieren den Schlüssel.

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]**.
1. Klicken Sie auf das Symbol [!DNL PostgreSQL] .
1. Nachdem die Seite `PostgreSQL credentials` geöffnet wurde, legen Sie den Umschalter `Encrypted` auf `Yes` fest. Dadurch wird das `SSH`-Setup-Formular angezeigt.
1. Der `public key` befindet sich unter diesem Formular.

Lassen Sie diese Seite während des gesamten Tutorials geöffnet - Sie benötigen sie im nächsten Abschnitt und am Ende.

Nachstehend wird gezeigt, wie Sie durch [!DNL Commerce Intelligence] navigieren, um den Schlüssel abzurufen:

![Abrufen des öffentlichen RJMetrics-Schlüssels](../../../assets/get-mbi-public-key.gif)

## Zugriff auf die [!DNL Commerce Intelligence] IP-Adresse zulassen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff über Ihre IP-Adresse zulässig ist. Er ist `54.88.76.97/32`, befindet sich aber auch auf der Seite mit den `PostgreSQL`. Siehe das blaue Kästchen oben in der GIF.

## Erstellen eines [!DNL Linux] Benutzers für [!DNL Commerce Intelligence] {#linux}

Dabei kann es sich um einen Produktions- oder Sekundärrechner handeln, sofern er Echtzeitdaten (oder häufig aktualisierte Daten) enthält. Sie können [diesen Benutzer &#x200B;](../../../administrator/account-management/restrict-db-access.md) beliebiger Weise einschränken, solange er das Recht behält, eine Verbindung zum [!DNL PostgreSQL]-Server herzustellen.

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
```

>[!IMPORTANT]
>
>Wenn für die mit dem Server verknüpfte `sshd\_config`-Datei nicht die Standardoption festgelegt ist, haben nur bestimmte Benutzer Serverzugriff. Dies verhindert eine erfolgreiche Verbindung mit [!DNL Commerce Intelligence]. In diesen Fällen ist es erforderlich, einen Befehl wie `AllowUsers` auszuführen, um dem Benutzer „rjmetric“ Zugriff auf den Server zu gewähren.

## Erstellen eines [!DNL Commerce Intelligence] [!DNL Postgres] Benutzers {#postgres}

Ihr Unternehmen benötigt möglicherweise einen anderen Prozess, aber die einfachste Möglichkeit, diesen Benutzer zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie bei Postgres als ein Benutzer mit dem Recht angemeldet sind, Berechtigungen zu gewähren. Der Benutzer sollte auch Eigentümer des Schemas sein, auf das [!DNL Commerce Intelligence] Zugriff erhalten soll.

```sql
    GRANT CONNECT ON DATABASE <database name> TO rjmetric WITH PASSWORD <secure password>;GRANT USAGE ON SCHEMA <schema name> TO rjmetric;GRANT SELECT ON ALL TABLES IN SCHEMA <schema name> TO rjmetric;ALTER DEFAULT PRIVILEGES IN SCHEMA <schema name> GRANT SELECT ON TABLES TO rjmetric;
```

Ersetzen Sie `secure password` durch Ihr eigenes sicheres Kennwort, das sich vom SSH-Kennwort unterscheiden kann. Ersetzen Sie außerdem `database name` und `schema name` durch die entsprechenden Namen in Ihrer Datenbank.

Wenn Sie mehrere Datenbanken oder Schemata verbinden möchten, wiederholen Sie diesen Vorgang nach Bedarf.

## Eingabe der Verbindungs- und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um alles abzuschließen, müssen Sie die Verbindung und die Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den [!DNL PostgreSQL]-Anmeldeinformationen geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data > Connections]** und klicken Sie auf **[!UICONTROL Add a Data Source]** und dann auf das Symbol [!DNL PostgreSQL] . Vergessen Sie nicht, den Umschalter `Encrypted` auf `Yes` zu setzen.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Username`: Der RJMetrics Postgres-Benutzername (sollte rjmetric sein)
* `Password`: Das RJMetrics Postgres-Kennwort
* `Port`: PostgreSQL-Port auf dem Server (standardmäßig 5432)
* `Host`: 127.0.0.1

Unter `SSH Connection`:

* `Remote Address`: Die IP-Adresse oder der Hostname des Servers, auf den Sie SSH installieren möchten
* `Username`: Ihr SSH-Anmeldename (sollte rjmetrisch sein)
* `SSH Port`: SSH-Port auf dem Server (standardmäßig 22)

Wenn Sie fertig sind, klicken Sie auf **Speichern und testen** um die Einrichtung abzuschließen.

### verwandt

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
