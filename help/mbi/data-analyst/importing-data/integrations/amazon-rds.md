---
title: Amazon RDS verbinden
description: Erfahren Sie, wie Sie Ihre RDS-Instanz verbinden.
exl-id: 02ad29c8-84d6-4b49-9ac1-e5f4feaa7fda
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/KAjnETtFvi9EHUDY8SJ-TSEhP3zooQel5ZlN-E3QxIg
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 503
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

![Einstellungen der Amazon RDS-Sicherheitsgruppe zeigen die IP-Adresskonfiguration an](../../../assets/RDS_IP.png)

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

Die Seiten mit den Anmeldedaten für `MySQL`, `Microsoft SQL` und `PostgreSQL` werden über die `Integrations` (**[!UICONTROL Manage Data** > **Integrations]**) aufgerufen, indem Sie auf **[!UICONTROL Add Integration]** klicken. Wenn die Liste der Integrationen angezeigt wird, klicken Sie auf das Symbol für die verwendete Datenbank, um zur Seite mit den Anmeldedaten zu gelangen. Wenn Sie derzeit keinen Zugriff auf die benötigte Integration haben, wenden Sie sich an Ihr Adobe Account Team.

Um die Erstellung der Verbindung abzuschließen, benötigen Sie die folgenden Informationen:

* Die öffentliche Adresse Ihrer RDS-Instanz: Sie finden diese in der [!DNL AWS]-Verwaltungskonsole.
* Der Port, den Ihre Datenbankinstanz verwendet: Einige Datenbanken haben einen Standardport, der das `Port` automatisch ausfüllt. Diese Informationen finden Sie auch in der Einrichtungsdokumentation für die Datenbank.
* Der Benutzername und das Kennwort des Benutzers, den Sie für [!DNL Commerce Intelligence] erstellt haben.

Wenn Sie eine verschlüsselte Verbindung verwenden, ändern Sie den Umschalter `Encrypted` auf der Seite mit den Datenbank-Anmeldeinformationen in `Yes`. Dadurch wird ein zusätzliches Formular zum Einrichten der Verschlüsselung angezeigt:

![SQL-Integrationsformular mit aktivierter Verschlüsselung zeigt die Option Ja an](../../../assets/sql-integration-encrypted-yes.png)


