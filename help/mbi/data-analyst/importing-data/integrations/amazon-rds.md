---
title: Amazon RDS verbinden
description: Erfahren Sie mehr über die Schritte zum Verbinden Ihrer RDS-Instanz.
exl-id: 02ad29c8-84d6-4b49-9ac1-e5f4feaa7fda
source-git-commit: 6b1bd96a0f9ae8bda3ae8db8ca78ad655079f2a4
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Verbinden [!DNL Amazon RDS]

[!DNL Amazon Relational Database Services (RDS)] ist ein verwalteter Datenbankdienst, der auf Datenbank-Engines ausgeführt wird, mit denen Sie wahrscheinlich bereits vertraut sind:

* [[!DNL MySQL]](../integrations/mysql-via-a-direct-connection.md)
* [[!DNL Microsoft SQL]](../integrations/microsoft-sql-server.md)
* [[!DNL PostgreSQL]](../integrations/postgresql.md)

Die Schritte zum Verbinden der [!DNL RDS] Die Instanz variiert je nach dem verwendeten Datenbanktyp und abhängig davon, ob Sie eine verschlüsselte Verbindung verwenden (z. B. eine [`SSH tunnel for MySQL`](../integrations/mysql-via-ssh-tunnel.md)), aber hier sind die Grundlagen.

## Autorisieren [!DNL Commerce Intelligence] , um auf Ihre Datenbank zuzugreifen

Auf der Seite mit den Anmeldedaten (**[!UICONTROL Manage Data** > **Integrations]**) sehen Sie für jede Datenbank ein Feld mit den IP-Adressen, die Sie für die Verbindung R autorisieren müssen.[!DNL RDS] nach [!DNL Commerce Intelligence]: `54.88.76.97` und `34.250.211.151`. Im Folgenden finden Sie die `MySQL credentials` Seite, auf der Sie das Feld &quot;IP-Adresse&quot;markiert haben:

![](../../../assets/RDS_IP.png)

Für [!DNL Commerce Intelligence] für eine erfolgreiche Verbindung mit Ihrer [!DNL RDS] müssen Sie diese IP-Adressen über die AWS-Verwaltungskonsole der entsprechenden Sicherheitsgruppe der Datenbank hinzufügen. Diese IP-Adressen können zu einer vorhandenen Gruppe hinzugefügt werden oder Sie können eine erstellen. Wichtig ist, dass die Gruppe berechtigt ist, auf die Instanz zuzugreifen, mit der Sie eine Verbindung herstellen möchten. [!DNL Commerce Intelligence].

Beim Hinzufügen von [!DNL Commerce Intelligence] IP-Adressen, stellen Sie sicher, dass Sie eine `/32` an das Ende der Adresse, die [!DNL Amazon] dass es sich um eine exakte IP-Adresse handelt. Keine Sorge; In der Benutzeroberfläche von AWS wird deutlich, dass dies erforderlich ist.

## Erstellen Sie eine `Linux` Benutzer für [!DNL Commerce Intelligence] {#linux}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie eine verschlüsselte Verbindung verwenden. Anweisungen hierzu finden Sie im Einrichtungsthema für die verwendete Datenbank (z. B.: MySQL). Die `Linux` Benutzer ermöglicht uns die Erstellung eines `SSH tunnel`, die sicherste Methode zum Senden von Daten über das Internet.

## Datenbankbenutzer erstellen für [!DNL Commerce Intelligence]

Dies ist der Teil des Prozesses, in dem die Schritte je nach verwendeter Datenbank variieren. Die Idee ist identisch, Sie erstellen jedoch einen Benutzer für [!DNL Commerce Intelligence] , der für den Zugriff auf Ihre Datenbank verwendet wird. Anleitung zum Erstellen einer Datenbank [!DNL Commerce Intelligence] -Benutzer finden Sie im Einrichtungsthema für die verwendete Datenbank.

## Verbindungsinformationen eingeben in [!DNL Commerce Intelligence]

Nachdem Sie die [!DNL Commerce Intelligence] Zugriff auf Ihre Instanz und Erstellung eines Benutzers für uns. Das Letzte, was Sie tun müssen, ist die Angabe der Verbindungsinformationen in [!DNL Commerce Intelligence].

Die Berechtigungsseiten für `MySQL`, `Microsoft SQL`und `PostgreSQL` auf die über `Integrations` page (**[!UICONTROL Manage Data** > **Integrations]**) durch Klicken auf **[!UICONTROL Add Integration]**. Wenn die Liste der Integrationen angezeigt wird, klicken Sie auf das Symbol für die Datenbank, die Sie verwenden, um zur Seite &quot;Anmeldeinformationen&quot;zu gelangen. Wenn Sie derzeit keinen Zugriff auf die benötigte Integration haben, wenden Sie sich an Ihr Adobe Account Team.

Um die Verbindung zu erstellen, benötigen Sie die folgenden Informationen:

* Die öffentliche Adresse Ihrer RDS-Instanz: Dies finden Sie im Abschnitt [!DNL AWS] Verwaltungskonsole.
* Der Anschluss, den Ihre Datenbankinstanz verwendet: Einige Datenbanken verfügen über einen Standardanschluss, mit dem die `Port` -Feld. Diese Informationen finden Sie auch in der Einrichtungsdokumentation für die Datenbank.
* Benutzername und Kennwort des Benutzers, den Sie für [!DNL Commerce Intelligence].

Wenn Sie eine verschlüsselte Verbindung verwenden, ändern Sie die `Encrypted` Umschalten auf der Seite mit den Datenbankanmeldeinformationen auf `Yes`. Dadurch wird ein zusätzliches Formular zum Einrichten der Verschlüsselung angezeigt:

![](../../../assets/sql-integration-encrypted-yes.png)


