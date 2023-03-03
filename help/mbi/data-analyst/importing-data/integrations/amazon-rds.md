---
title: Amazon RDS verbinden
description: Erfahren Sie mehr über die Schritte zum Verbinden Ihrer RDS-Instanz.
exl-id: 02ad29c8-84d6-4b49-9ac1-e5f4feaa7fda
source-git-commit: 6f018ab220f2ae573cbc9016f9efb83c27a254be
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# Amazon RDS verbinden

Amazon Relational Database Services (RDS) ist ein verwalteter Datenbankdienst, der auf Datenbank-Engines ausgeführt wird, mit denen Sie wahrscheinlich bereits vertraut sind - [[!DNL MySQL]](../integrations/mysql-via-a-direct-connection.md), [[!DNL Microsoft SQL]](../integrations/microsoft-sql-server.md)und [[!DNL PostgreSQ]](../integrations/postgresql.md).

Die Schritte zum Verbinden Ihrer RDS-Instanz variieren geringfügig abhängig vom verwendeten Datenbanktyp (unter den obigen Links finden Sie detaillierte Anweisungen für jede Datenbank) und davon, ob Sie eine verschlüsselte Verbindung verwenden (z. B. eine [`SSH tunnel for MySQL`](../integrations/mysql-via-ssh-tunnel.md)), aber hier sind die Grundlagen:

## Autorisieren [!DNL MBI] , um auf Ihre Datenbank zuzugreifen

Auf der Seite mit den Anmeldedaten (**[!UICONTROL Manage Data** > **Integrations]**) wird für jede Datenbank ein Feld mit den IP-Adressen angezeigt, die Sie für die Verbindung von RDS mit MBI autorisieren müssen: `54.88.76.97` und `34.250.211.151`. Im Folgenden finden Sie die `MySQL credentials` Seite, auf der das Feld &quot;IP-Adresse&quot;markiert wurde:

![](../../../assets/RDS_IP.png)

Für [!DNL MBI] Um eine erfolgreiche Verbindung mit Ihrer RDS-Instanz herzustellen, müssen Sie diese IP-Adressen über die AWS-Verwaltungskonsole der entsprechenden Sicherheitsgruppe für die Datenbank hinzufügen. Diese IP-Adressen können zu einer vorhandenen Gruppe hinzugefügt werden oder Sie können eine neue erstellen. Wichtig ist, dass die Gruppe berechtigt ist, auf die Instanz zuzugreifen, mit der Sie eine Verbindung herstellen möchten. [!DNL MBI].

Beim Hinzufügen von [!DNL MBI] IP-Adressen, stellen Sie sicher, dass Sie eine `/32` an das Ende der Adresse, um Amazon anzuzeigen, dass es sich um eine exakte IP-Adresse handelt. Keine Sorge; In der Benutzeroberfläche von AWS wird deutlich, dass dies erforderlich ist.

## Erstellen Sie eine `Linux` Benutzer für [!DNL MBI] {#linux}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie eine verschlüsselte Verbindung verwenden. Anweisungen hierzu finden Sie im Einrichtungsartikel für die verwendete Datenbank (z. B.: MySQL). Die `Linux` -Benutzer ermöglicht es uns, eine `SSH tunnel`, die sicherste Methode zum Senden von Daten über das Internet.

## Erstellen eines Datenbankbenutzers für MBI

Dies ist der Teil des Prozesses, in dem die Schritte je nach verwendeter Datenbank variieren. Die Idee ist jedoch identisch: Sie erstellen einen Benutzer für [!DNL MBI] , die für den Zugriff auf Ihre Datenbank verwendet wird. Anleitung zum Erstellen einer Datenbank [!DNL MBI] -Benutzer finden Sie im Setup-Artikel für die verwendete Datenbank.

## Verbindungsinformationen in MBI eingeben

Nachdem Sie die [!DNL MBI] Zugriff auf Ihre Instanz und Erstellung eines Benutzers für uns. Das Letzte, was Sie tun müssen, ist die Angabe der Verbindungsinformationen in [!DNL MBI].

Die Berechtigungsseiten für `MySQL`, `Microsoft SQL`und `PostgreSQL` auf die über `Integrations` page (**[!UICONTROL Manage Data** > **Integrations]**) durch Klicken auf **[!UICONTROL Add Integration]**. Wenn die Liste der Integrationen angezeigt wird, klicken Sie auf das Symbol für die Datenbank, die Sie verwenden, um zur Seite &quot;Anmeldeinformationen&quot;zu gelangen. Wenn Sie derzeit keinen Zugriff auf die benötigte Integration haben, wenden Sie sich an Ihr Adobe Account Team.

Um die Verbindung zu erstellen, benötigen wir die folgenden Informationen:

* Die öffentliche Adresse Ihrer RDS-Instanz: Dies finden Sie in der AWS-Verwaltungskonsole.
* Der Anschluss, den Ihre Datenbankinstanz verwendet: Einige Datenbanken verfügen über einen Standardanschluss, der automatisch mit dem `Port` -Feld. Diese Informationen finden Sie auch in unserer Einrichtungsdokumentation für die Datenbank.
* Benutzername und Kennwort des Benutzers, den Sie für [!DNL MBI].

Wenn Sie eine verschlüsselte Verbindung verwenden, ändern Sie die `Encrypted` Umschalten auf der Seite mit den Datenbankanmeldeinformationen auf `Yes`. Dadurch wird ein zusätzliches Formular zur Einrichtung der Verschlüsselung angezeigt:

![](../../../assets/sql-integration-encrypted-yes.png)

Das ist alles! Die Verbindung Ihrer RDS-Instanz ist abgeschlossen.
