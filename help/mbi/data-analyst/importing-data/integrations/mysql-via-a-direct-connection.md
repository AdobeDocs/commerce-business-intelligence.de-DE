---
title: Verbindung von MySQL über eine direkte Verbindung
description: Erfahren Sie, wie Sie eine Verbindung herstellen [!DNL MongoDB] über eine direkte Verbindung.
exl-id: 53765844-c9bb-4a16-b00c-ce9672f87415
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Verbinden [!DNL MySQL] Direkte Verbindung

## In diesem Thema

* [Zugriff auf [!DNL Commerce Intelligence] IP-Adresse](#allowlist)
* [Erstellen Sie eine [!DNL MySQL] Benutzer für [!DNL Commerce Intelligence]](#steptwo)
* [Verbindungsinformationen eingeben in [!DNL Commerce Intelligence]](#stepthree)

## Sprung zu

* [[!DNL MySQL] via ](../integrations/mysql-via-ssh-tunnel.md)
* [[!DNL MySQL] via [!DNL cPanel]](../integrations/mysql-via-cpanel.md)

>[!NOTE]
>
>[!DNL Adobe] empfiehlt die Verwendung von [SSH](../integrations/mysql-via-ssh-tunnel.md) oder eine andere Form der Verschlüsselung, um Ihre Daten zu sichern! Wenn dies keine Option ist, können Sie weiterhin direkt eine Verbindung herstellen [!DNL Commerce Intelligence] zu Ihrer Datenbank mithilfe der Anweisungen in diesem Thema.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL] Datenbank zu [!DNL Commerce Intelligence]. Diese Einstellungen können auch mit [!DNL Adobe Commerce] oder anderen eCommerce-Datenbanken, die MySQL verwenden.

## Zugriff auf [!DNL Commerce Intelligence] IP-Adressen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff von Ihren IP-Adressen aus gestattet wird. Sie sind `54.88.76.97` und `34.250.211.151`, aber es befindet sich auch auf der [!DNL MySQL] Anmeldeseite:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen Sie eine [!DNL MySQL] Benutzer für [!DNL Commerce Intelligence]

Die einfachste Methode zum Erstellen einer `MySQL` Benutzer für [!DNL Commerce Intelligence] führt die folgende Abfrage aus, wenn Sie angemeldet sind `MySQL` mit `GRANT` Berechtigungen. Ersetzen `Commerce Intelligence IP Address` mit dem [!DNL Commerce Intelligence] IP-Adresse und ersetzen `secure password` mit einem sicheren Kennwort Ihrer Wahl:

```sql
    GRANT SELECT ON *.* TO 'magentobi'@'<Commerce Intelligence IP address>' IDENTIFIED BY '<secure password>';
```

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen `GRANT` Abfragen, die nur den Zugriff auf die von Ihnen zulässigen Daten ermöglichen.

**Führen Sie die GRANT-Abfrage für alle erforderlichen IPs mit demselben Benutzer und Kennwort erneut aus.**

## Verbindungsinformationen in Commerce Intelligence eingeben

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL Commerce Intelligence]. Hast du die [!DNL MySQL] Berechtigungsseite öffnen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]** und klicken Sie dann auf [!DNL MySQL] Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem `Database Connection` Abschnitt:

* `Connection Nickname`: Geben Sie einen Namen für die Integration ein (z. B. Ecommerce Store)
* `Username`: Der Benutzername für die [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Password`: Das Kennwort für die [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Port`: MySQL-Port auf Ihrem Server (`3306` standardmäßig)
* `Host`: Standardmäßig ist dies localhost. Im Allgemeinen ist dies der bind-address-Wert für Ihre [!DNL MySQL] server, der standardmäßig `127.0.0.1 (localhost)`, kann aber auch eine lokale Netzwerkadresse sein (z. B. `192.168.0.1`) oder der öffentlichen IP-Adresse Ihres Servers.

  Der Wert befindet sich in der `my.cnf` Datei (befindet sich unter `/etc/my.cnf`) unter der Zeile, die lautet `\[mysqld\]`. Wenn die bind-address-Zeile in dieser Datei auskommentiert ist, wird Ihr Server vor externen Verbindungsversuchen geschützt.

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte Dokumentation

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
