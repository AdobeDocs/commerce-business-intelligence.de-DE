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

[!DNL Amazon Relational Database Services (RDS)] ist ein verwalteter Datenbank-Service, der auf Datenbank-Engines ausgeführt wird, mit denen Sie wahrscheinlich bereits vertraut sind:

* [[!DNL MySQL]](../integrations/mysql-via-a-direct-connection.md)
* [[!DNL Microsoft SQL]](../integrations/microsoft-sql-server.md)
* [[!DNL PostgreSQL]](../integrations/postgresql.md)

Die Schritte zum Verbinden Ihrer [!DNL RDS]-Instanz variieren je nach verwendetem Datenbanktyp und ob Sie eine verschlüsselte Verbindung (wie eine [`SSH tunnel for MySQL`](../integrations/mysql-via-ssh-tunnel.md)) verwenden. Hier finden Sie jedoch die Grundlagen.

## Autorisieren von [!DNL Commerce Intelligence] für den Zugriff auf Ihre Datenbank

Auf der Seite Anmeldedaten (**[!UICONTROL Manage Data** > **Integrations]**) für jede Datenbank wird ein Feld mit den IP-Adressen angezeigt, die Sie für die Verbindung von R[!DNL RDS] mit [!DNL Commerce Intelligence]: `54.88.76.97` und `34.250.211.151` autorisieren müssen. Im Folgenden sehen Sie die `MySQL credentials`, auf der Sie das Feld „IP-Adresse“ markiert haben:

![](../../../assets/RDS_IP.png)

Damit [!DNL Commerce Intelligence] erfolgreich eine Verbindung mit Ihrer [!DNL RDS]-Instanz herstellen können, müssen Sie diese IP-Adressen über die Verwaltungskonsole von AWS der entsprechenden Datenbanksicherheitsgruppe hinzufügen. Diese IP-Adressen können zu einer vorhandenen Gruppe hinzugefügt oder erstellt werden. Wichtig ist, dass die Gruppe berechtigt ist, auf die Instanz zuzugreifen, mit der Sie eine Verbindung herstellen [!DNL Commerce Intelligence].

Stellen Sie beim Hinzufügen der [!DNL Commerce Intelligence] IP-Adressen sicher, dass Sie am Ende der Adresse eine `/32` hinzufügen, um anzugeben, [!DNL Amazon] es sich um eine exakte IP-Adresse handelt. Machen Sie sich keine Sorgen. Die AWS-Benutzeroberfläche macht deutlich, dass dies erforderlich ist.

## Erstellen eines `Linux` Benutzers für [!DNL Commerce Intelligence] {#linux}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie eine verschlüsselte Verbindung verwenden. Anweisungen hierzu finden Sie im Setup-Thema der von Ihnen verwendeten Datenbank (z. B. MySQL). Der `Linux` Benutzer ermöglicht uns, eine `SSH tunnel` zu erstellen, was die sicherste Methode zum Senden von Daten über das Internet ist.

## Erstellen einer Benutzerdatenbank für [!DNL Commerce Intelligence]

Dies ist der Teil des Prozesses, in dem die Schritte je nach verwendeter Datenbank variieren. Die Idee ist jedoch dieselbe, wenn Sie einen Benutzer für [!DNL Commerce Intelligence] erstellen, der für den Zugriff auf Ihre Datenbank verwendet wird. Anweisungen zum Erstellen einer Datenbank [!DNL Commerce Intelligence] Benutzer finden Sie im Setup-Thema für die verwendete Datenbank.

## Verbindungsinformationen in [!DNL Commerce Intelligence] eingeben

Nachdem Sie [!DNL Commerce Intelligence] Zugriff auf Ihre Instanz gewährt und einen Benutzer für uns erstellt haben, müssen Sie die Verbindungsinformationen zuletzt in [!DNL Commerce Intelligence] eingeben.

Die Seiten mit den Anmeldedaten für `MySQL`, `Microsoft SQL` und `PostgreSQL` werden über die `Integrations` (**[!UICONTROL Manage Data** > **Integrations]**) aufgerufen, indem Sie auf **[!UICONTROL Add Integration]** klicken. Wenn die Liste der Integrationen angezeigt wird, klicken Sie auf das Symbol für die verwendete Datenbank, um zur Seite mit den Anmeldedaten zu gelangen. Wenn Sie derzeit keinen Zugriff auf die benötigte Integration haben, wenden Sie sich an Ihr Adobe-Account-Team.

Um die Erstellung der Verbindung abzuschließen, benötigen Sie die folgenden Informationen:

* Die öffentliche Adresse Ihrer RDS-Instanz: Sie finden diese in der [!DNL AWS]-Verwaltungskonsole.
* Der Port, den Ihre Datenbankinstanz verwendet: Einige Datenbanken haben einen Standardport, der das `Port` automatisch ausfüllt. Diese Informationen finden Sie auch in der Einrichtungsdokumentation für die Datenbank.
* Der Benutzername und das Kennwort des Benutzers, den Sie für [!DNL Commerce Intelligence] erstellt haben.

Wenn Sie eine verschlüsselte Verbindung verwenden, ändern Sie den Umschalter `Encrypted` auf der Seite mit den Datenbank-Anmeldeinformationen in `Yes`. Dadurch wird ein zusätzliches Formular zum Einrichten der Verschlüsselung angezeigt:

![](../../../assets/sql-integration-encrypted-yes.png)


