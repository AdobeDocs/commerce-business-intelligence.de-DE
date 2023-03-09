---
title: MySQL über cPanel verbinden
description: Erfahren Sie, wie Sie MySQL über cPanel verbinden.
exl-id: 90b0a0b0-8c6b-4144-95b4-f588f18616c7
source-git-commit: e4ac176492913623ae461484c8ef2abe034e5f62
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MySQL über cPanel verbinden

* [Erstellen Sie eine [!DNL MBI] MySQL-Benutzer in cPanel](#cpanel)
* [Verbindung- und Benutzerinformationen in MBI eingeben](#finish)

## Sprung zu

* [MySQL über SSH-Tunnel](../integrations/mysql-via-ssh-tunnel.md)
* [MySQL über direkte Verbindung](../integrations/mysql-via-a-direct-connection.md)

* **`MySQL via cPanel`**

>[!IMPORTANT]
>
>Adobe empfiehlt die Verwendung von SSH oder einer anderen Verschlüsselungsform zur Sicherung Ihrer Daten! Wenn dies keine Option ist, können Sie weiterhin direkt eine Verbindung herstellen [!DNL MBI] zu Ihrer Datenbank mithilfe der Anweisungen in diesem Artikel.

Dieser Artikel führt Sie durch die direkte Verbindung Ihrer MySQL-Datenbank mit [!DNL MBI] using `cPanel`. Dieser Prozess kann auch verwendet werden, um eine Verbindung herzustellen [!DNL Adobe Commerce] und anderen MySQL-basierten eCommerce-Datenbanken, um [!DNL MBI].

1. Erstellen Sie eine [!DNL MBI] MySQL-Benutzer in `cPanel`
1. Eingabe von Verbindungs- und Benutzerinformationen in [!DNL MBI]

Erste Schritte.

## Erstellen einer [!DNL MBI] MySQL-Benutzer in `cPanel` {#cpanel}

1. Anmelden bei [`cPanel`](../../../data-analyst/importing-data/integrations/mysql-via-cpanel.md) über Ihren Hosting-Provider.
1. Klicken **[!UICONTROL MySQL Databases]**, befindet sich im `Database` Abschnitt.
1. Scrollen Sie nach unten zum `Add New User` und erstellen Sie einen Benutzer für [!DNL MBI]:

   ![](../../../assets/create-mbi-mysql-user-cpanel.png)

1. Klicken **[!UICONTROL Create User]**.
1. Nachdem Sie den Benutzer erstellt haben, müssen Sie ihn mit einer Datenbank verknüpfen. Gehen Sie zurück zu `Add New User` -Abschnitt - siehe Einstellungen für `Add User to Database?` Das ist es, was du brauchst.
1. Im `User` in diesem Abschnitt den von Ihnen erstellten Benutzer auswählen.
1. Im `Database` in diesem Abschnitt die Datenbank auswählen, zu der Sie eine Verbindung herstellen möchten [!DNL MBI].
1. Klicken **[!UICONTROL Add]**.
1. Wenn die Checkliste der Berechtigungen angezeigt wird, aktivieren Sie das Kontrollkästchen neben `SELECT` - das ist alles [!DNL MBI] muss eine Verbindung zu Ihrer Datenbank herstellen.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL MBI] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL MBI]. Haben Sie die Seite mit den MySQL-Anmeldeinformationen geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann das MySQL-Symbol.

Geben Sie die folgenden Informationen auf dieser Seite im `Database Connection` Abschnitt:

* `Username`: Der Benutzername für die [!DNL MBI] MySQL-Benutzer
* `Password`: Das Kennwort für die [!DNL MBI] MySQL-Benutzer
* `Port`: MySQL-Port auf Ihrem Server (`3306` standardmäßig)
* `Host`: Die öffentliche Adresse der `MySQL` server [!DNL MBI] stellt Verbindungen her. Dies ist normalerweise die URL, mit der Sie sich anmelden `cPanel`.

Wenn Sie eine [`SSH tunnel`](../integrations/mysql-via-ssh-tunnel.md)müssen Sie die Verschlüsselungsinformationen eingeben. Legen Sie die `Encrypted` Umschalten auf `Yes` , um das Formular anzuzeigen.

* `Connection Type`: Legen Sie hier fest `SSH Tunnel`
* `Remote Address`: Die IP-Adresse oder der Hostname des Servers [!DNL MBI] in den
* `Username`: Der Benutzername für die [!DNL MBI] `SSH (Linux)` Benutzer, siehe [instructions](../../../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md) wie Sie dies durchführen können (falls noch nicht geschehen)
* `SSH Port`: SSH-Port auf Ihrem Server (`22` standardmäßig)

Das ist es! Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
