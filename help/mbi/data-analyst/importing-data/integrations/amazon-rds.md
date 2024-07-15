---
title: Amazon RDS verbinden
description: Erfahren Sie, wie Sie Ihre RDS-Instanz verbinden.
exl-id: 02ad29c8-84d6-4b49-9ac1-e5f4feaa7fda
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# [!DNL Amazon RDS] verbinden

[!DNL Amazon Relational Database Services (RDS)] ist ein verwalteter Datenbankdienst, der auf Datenbank-Engines ausgeführt wird, mit denen Sie wahrscheinlich bereits vertraut sind:

* [[!DNL MySQL]](../integrations/mysql-via-a-direct-connection.md)
* [[!DNL Microsoft SQL]](../integrations/microsoft-sql-server.md)
* [[!DNL PostgreSQL]](../integrations/postgresql.md)

Die Schritte zum Verbinden Ihrer [!DNL RDS]-Instanz hängen vom verwendeten Datenbanktyp ab und davon, ob Sie eine verschlüsselte Verbindung (wie z. B. [`SSH tunnel for MySQL`](../integrations/mysql-via-ssh-tunnel.md)) verwenden. Hier finden Sie jedoch die Grundlagen.

## [!DNL Commerce Intelligence] für den Zugriff auf Ihre Datenbank autorisieren

Auf der Seite mit den Anmeldedaten (**[!UICONTROL Manage Data** > **Integrations]**) für jede Datenbank wird ein Feld mit den IP-Adressen angezeigt, die Sie für die Verbindung von R[!DNL RDS] mit [!DNL Commerce Intelligence]: `54.88.76.97` und `34.250.211.151` autorisieren müssen. Im Folgenden sehen Sie die Seite &quot;`MySQL credentials`&quot;, auf der Sie das Feld für die IP-Adresse markiert haben:

![](../../../assets/RDS_IP.png)

Damit [!DNL Commerce Intelligence] erfolgreich eine Verbindung mit Ihrer [!DNL RDS]-Instanz herstellen kann, müssen Sie diese IP-Adressen über die AWS-Verwaltungskonsole der entsprechenden Sicherheitsgruppe für die Datenbank hinzufügen. Diese IP-Adressen können zu einer vorhandenen Gruppe hinzugefügt werden oder Sie können eine erstellen. Wichtig ist, dass die Gruppe berechtigt ist, auf die Instanz zuzugreifen, mit der Sie eine Verbindung herstellen möchten.[!DNL Commerce Intelligence]

Stellen Sie beim Hinzufügen der [!DNL Commerce Intelligence] IP-Adressen sicher, dass Sie am Ende der Adresse eine `/32` hinzufügen, um [!DNL Amazon] anzugeben, dass es sich um eine exakte IP-Adresse handelt. Machen Sie sich keine Gedanken; in der Benutzeroberfläche von AWS wird deutlich, dass dies erforderlich ist.

## Erstellen eines `Linux` Benutzers für [!DNL Commerce Intelligence] {#linux}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie eine verschlüsselte Verbindung verwenden. Anweisungen hierzu finden Sie im Setup-Thema der verwendeten Datenbank (z. B. MySQL). Mit dem Benutzer `Linux` können wir einen `SSH tunnel` erstellen, die sicherste Methode zum Senden von Daten über das Internet.

## Datenbankbenutzer für [!DNL Commerce Intelligence] erstellen

Dies ist der Teil des Prozesses, in dem die Schritte je nach verwendeter Datenbank variieren. Die Idee ist jedoch die gleiche, Sie erstellen einen Benutzer für [!DNL Commerce Intelligence] , der für den Zugriff auf Ihre Datenbank verwendet wird. Anweisungen zum Erstellen eines Datenbankbenutzers [!DNL Commerce Intelligence] finden Sie im Einrichtungsthema für die verwendete Datenbank.

## Verbindungsinformationen in [!DNL Commerce Intelligence] eingeben

Nachdem Sie [!DNL Commerce Intelligence] Zugriff auf Ihre Instanz gewährt und einen Benutzer für uns erstellt haben, müssen Sie als Letztes die Verbindungsinformationen in [!DNL Commerce Intelligence] eingeben.

Die Berechtigungsseiten für `MySQL`, `Microsoft SQL` und `PostgreSQL` werden über die Seite `Integrations` (**[!UICONTROL Manage Data** > **Integrations]**) aufgerufen, indem Sie auf **[!UICONTROL Add Integration]** klicken. Wenn die Liste der Integrationen angezeigt wird, klicken Sie auf das Symbol für die Datenbank, die Sie verwenden, um zur Seite &quot;Anmeldeinformationen&quot;zu gelangen. Wenn Sie derzeit keinen Zugriff auf die benötigte Integration haben, wenden Sie sich an Ihr Adobe-Account-Team.

Um die Verbindung zu erstellen, benötigen Sie die folgenden Informationen:

* Die öffentliche Adresse Ihrer RDS-Instanz: Diese finden Sie in der Verwaltungskonsole [!DNL AWS] .
* Der Anschluss, den Ihre Datenbankinstanz verwendet: Einige Datenbanken verfügen über einen Standardanschluss, der automatisch das Feld `Port` füllt. Diese Informationen finden Sie auch in der Einrichtungsdokumentation für die Datenbank.
* Der Benutzername und das Kennwort des von Ihnen für [!DNL Commerce Intelligence] erstellten Benutzers.

Wenn Sie eine verschlüsselte Verbindung verwenden, ändern Sie den Umschalter `Encrypted` auf der Seite mit den Datenbankberechtigungen in `Yes`. Dadurch wird ein zusätzliches Formular zum Einrichten der Verschlüsselung angezeigt:

![](../../../assets/sql-integration-encrypted-yes.png)


