---
title: MySQL über cPanel verbinden
description: Erfahren Sie, wie Sie MySQL über cPanel verbinden.
exl-id: 90b0a0b0-8c6b-4144-95b4-f588f18616c7
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export, SQL Report Builder
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Verbinden [!DNL MySQL] via [!DNL cPanel]

* [Erstellen Sie eine [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer in [!DNL cPanel]](#cpanel)
* [Eingabe von Verbindungs- und Benutzerinformationen in [!DNL Commerce Intelligence]](#finish)

## Sprung zu

* [[!DNL MySQL] über SSH-Tunnel](../integrations/mysql-via-ssh-tunnel.md)
* [[!DNL MySQL] Direkte Verbindung](../integrations/mysql-via-a-direct-connection.md)

>[!IMPORTANT]
>
>[!DNL Adobe] empfiehlt die Verwendung von SSH oder einer anderen Form der Verschlüsselung, um Ihre Daten zu sichern! Wenn dies keine Option ist, können Sie weiterhin direkt eine Verbindung herstellen [!DNL Commerce Intelligence] zu Ihrer Datenbank mithilfe der Anweisungen in diesem Thema.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL] Datenbank zu [!DNL Commerce Intelligence] using [!DNL cPanel]. Dieser Prozess kann auch verwendet werden, um eine Verbindung herzustellen [!DNL Adobe Commerce] und anderen MySQL-basierten eCommerce-Datenbanken, um [!DNL Commerce Intelligence].

1. Erstellen Sie eine [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer in [!DNL cPanel]
1. Eingabe von Verbindungs- und Benutzerinformationen in [!DNL Commerce Intelligence]

Erste Schritte.

## Erstellen einer [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer in [!DNL cPanel] {#cpanel}

1. Anmelden bei [!DNL cPanel] über Ihren Hosting-Provider.
1. Klicken **[!UICONTROL [!DNL MySQL] Databases]**, befindet sich im `Database` Abschnitt.
1. Scrollen Sie nach unten zum `Add New User` und erstellen Sie einen Benutzer für [!DNL Commerce Intelligence]:

   ![](../../../assets/create-mbi-mysql-user-cpanel.png)

1. Klicken **[!UICONTROL Create User]**.
1. Nachdem Sie den Benutzer erstellt haben, müssen Sie ihn mit einer Datenbank verknüpfen. Gehen Sie zurück zu `Add New User` -Abschnitt - siehe Einstellungen für `Add User to Database?` Das ist es, was du brauchst.
1. Im `User` in diesem Abschnitt den von Ihnen erstellten Benutzer auswählen.
1. Im `Database` in diesem Abschnitt die Datenbank auswählen, zu der Sie eine Verbindung herstellen möchten [!DNL Commerce Intelligence].
1. Klicken **[!UICONTROL Add]**.
1. Wenn die Checkliste der Berechtigungen angezeigt wird, aktivieren Sie das Kontrollkästchen neben `SELECT` - das ist alles [!DNL Commerce Intelligence] muss eine Verbindung zu Ihrer Datenbank herstellen.

## Eingabe der Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] {#finish}

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]. Hast du die [!DNL MySQL] Berechtigungsseite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Manage Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann [!DNL MySQL] Symbol.

Geben Sie die folgenden Informationen auf dieser Seite im `Database Connection` Abschnitt:

* `Username`: Der Benutzername für die [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Password`: Das Kennwort für die [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Port`: MySQL-Port auf Ihrem Server (`3306` standardmäßig)
* `Host`: Die öffentliche Adresse der `MySQL` server [!DNL Commerce Intelligence] stellt Verbindungen her. Dies ist normalerweise die URL, mit der Sie sich anmelden `[!DNL cPanel]`.

Wenn Sie eine [`SSH tunnel`](../integrations/mysql-via-ssh-tunnel.md)müssen Sie die Verschlüsselungsinformationen eingeben. Legen Sie die `Encrypted` Umschalten auf `Yes` , um das Formular anzuzeigen.

* `Connection Type`: Legen Sie hier fest `SSH Tunnel`
* `Remote Address`: Die IP-Adresse oder der Hostname des Servers [!DNL Commerce Intelligence] in den
* `Username`: Der Benutzername für die [!DNL Commerce Intelligence] `SSH (Linux)` Benutzer, siehe [instructions](../../../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md) wie Sie dies durchführen können (falls noch nicht geschehen)
* `SSH Port`: SSH-Port auf Ihrem Server (`22` standardmäßig)

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
