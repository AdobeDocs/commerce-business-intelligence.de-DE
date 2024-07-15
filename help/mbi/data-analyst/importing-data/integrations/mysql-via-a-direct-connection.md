---
title: Verbindung von MySQL über eine direkte Verbindung
description: Erfahren Sie, wie Sie über eine direkte Verbindung eine Verbindung herstellen. [!DNL MongoDB]
exl-id: 53765844-c9bb-4a16-b00c-ce9672f87415
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# [!DNL MySQL] über direkte Verbindung verbinden

## In diesem Thema

* [Zugriff auf die  [!DNL Commerce Intelligence] IP-Adresse zulassen](#allowlist)
* [Erstellen eines [!DNL MySQL] Benutzers für  [!DNL Commerce Intelligence]](#steptwo)
* [Verbindungsinformationen in [!DNL Commerce Intelligence] eingeben](#stepthree)

## Springen Sie zu

* [[!DNL MySQL] via ](../integrations/mysql-via-ssh-tunnel.md)
* [[!DNL MySQL] via [!DNL cPanel]](../integrations/mysql-via-cpanel.md)

>[!NOTE]
>
>[!DNL Adobe] empfiehlt die Verwendung von [SSH](../integrations/mysql-via-ssh-tunnel.md) oder einer anderen Form der Verschlüsselung zur Sicherung Ihrer Daten! Wenn dies keine Option ist, können Sie mithilfe der Anweisungen in diesem Thema weiterhin [!DNL Commerce Intelligence] direkt mit Ihrer Datenbank verbinden.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL]-Datenbank mit [!DNL Commerce Intelligence]. Diese Einstellungen können auch mit [!DNL Adobe Commerce] oder anderen eCommerce-Datenbanken verwendet werden, die MySQL verwenden.

## Zugriff auf die [!DNL Commerce Intelligence] -IP-Adressen zulassen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151`, befinden sich aber auch auf der Seite mit den Anmeldedaten für [!DNL MySQL]:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen eines [!DNL MySQL] Benutzers für [!DNL Commerce Intelligence]

Die einfachste Möglichkeit, einen `MySQL` -Benutzer für [!DNL Commerce Intelligence] zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie bei `MySQL` mit `GRANT` -Berechtigungen angemeldet sind. Ersetzen Sie `Commerce Intelligence IP Address` durch die IP-Adresse [!DNL Commerce Intelligence] und ersetzen Sie `secure password` durch ein sicheres Kennwort Ihrer Wahl:

```sql
    GRANT SELECT ON *.* TO 'magentobi'@'<Commerce Intelligence IP address>' IDENTIFIED BY '<secure password>';
```

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen `GRANT`-Abfragen ausführen, die nur den Zugriff auf die Daten ermöglichen, die Sie zulassen.

**Führen Sie die GRANT-Abfrage für alle erforderlichen IPs mit demselben Benutzer und Kennwort erneut aus.**

## Verbindungsinformationen in Commerce Intelligence eingeben

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den Anmeldedaten für [!DNL MySQL] geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, und klicken Sie dann auf das Symbol [!DNL MySQL]. Vergessen Sie nicht, den Umschalter `Encrypted` auf `Yes` zu ändern.

Geben Sie die folgenden Informationen in diese Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Connection Nickname`: Geben Sie einen Namen für die Integration ein (z. B. E-Commerce Store)
* `Username`: Der Benutzername für den Benutzer [!DNL Commerce Intelligence] [!DNL MySQL]
* `Password`: Das Kennwort für den Benutzer [!DNL Commerce Intelligence] [!DNL MySQL]
* `Port`: MySQL-Port auf Ihrem Server (standardmäßig `3306`)
* `Host`: Standardmäßig ist dies localhost. Im Allgemeinen handelt es sich dabei um den bind-address-Wert für Ihren [!DNL MySQL]-Server, der standardmäßig `127.0.0.1 (localhost)` ist, aber auch eine lokale Netzwerkadresse (z. B. `192.168.0.1`) oder die öffentliche IP-Adresse Ihres Servers sein kann.

  Der Wert befindet sich in Ihrer `my.cnf`-Datei (unter `/etc/my.cnf`) unter der Zeile, die den Wert `\[mysqld\]` enthält. Wenn die bind-address-Zeile in dieser Datei auskommentiert ist, wird Ihr Server vor externen Verbindungsversuchen geschützt.

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte Dokumentation

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
