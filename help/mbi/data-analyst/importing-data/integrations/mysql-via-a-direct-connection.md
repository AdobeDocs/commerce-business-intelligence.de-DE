---
title: Verbindung von MySQL über eine direkte Verbindung
description: Erfahren Sie, wie Sie eine Verbindung herstellen [!DNL MongoDB] über eine direkte Verbindung.
exl-id: 53765844-c9bb-4a16-b00c-ce9672f87415
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Verbinden [!DNL MongoDB] Direkte Verbindung

## In diesem Artikel

* [Zugriff auf [!DNL MBI] IP-Adresse](#allowlist)
* [Erstellen Sie eine ](#steptwo)
* [Verbindungsinformationen eingeben in [!DNL MBI]](#stepthree)

## Sprung zu

* [&quot;MySQL über SSH-Tunnel&quot;](../integrations/mysql-via-ssh-tunnel.md)
* `MySQL via direct connection`
* [&quot;MySQL via cPanel&quot;](../integrations/mysql-via-cpanel.md)

>[!NOTE]
>
>Es wird dringend empfohlen, [SSH](../integrations/mysql-via-ssh-tunnel.md) oder eine andere Form der Verschlüsselung, um Ihre Daten zu sichern! Wenn dies keine Option ist, können Sie weiterhin direkt eine Verbindung herstellen [!DNL MBI] zu Ihrer Datenbank mithilfe der Anweisungen in diesem Artikel.

In diesem Artikel führen wir Sie durch die direkte Verbindung Ihrer MySQL-Datenbank zu [!DNL MBI]. Diese Einstellungen können auch mit Commerce- oder anderen eCommerce-Datenbanken verwendet werden, die MySQL verwenden.

## Zugriff auf [!DNL MBI] IP-Adressen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, muss Ihre Firewall so konfiguriert werden, dass sie den Zugriff von unseren IP-Adressen aus gestattet. Sie sind `54.88.76.97` und `34.250.211.151`, aber es befindet sich auch auf der Seite mit den MySQL-Anmeldeinformationen:

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen eines MySQL-Benutzers für [!DNL MBI]

Die einfachste Methode zum Erstellen einer `MySQL` Benutzer für [!DNL MBI] führt die folgende Abfrage aus, wenn Sie angemeldet sind `MySQL` mit `GRANT` Berechtigungen. Ersetzen `MBI IP Address` mit dem [!DNL MBI] IP-Adresse und ersetzen `secure password` mit einem sicheren Kennwort Ihrer Wahl:

```sql
    GRANT SELECT ON *.* TO 'magentobi'@'<MBI IP address>' IDENTIFIED BY '<secure password>';
```

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen `GRANT` Abfragen, die nur den Zugriff auf die von Ihnen zulässigen Daten ermöglichen.

**Führen Sie die GRANT-Abfrage für alle erforderlichen IPs mit demselben Benutzer und Kennwort erneut aus.**

## Verbindungsinformationen in MBI eingeben

Um Elemente einzuschließen, müssen Sie die Verbindung und Benutzerinformationen in [!DNL MBI]. Haben Sie die Seite mit den MySQL-Anmeldeinformationen geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]**, dann das MySQL-Symbol. Vergessen Sie nicht, die `Encrypted` Umschalten auf `Yes`.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem `Database Connection` Abschnitt:

* `Connection Nickname`: Geben Sie einen Namen für die Integration ein (z. B. Ecommerce Store)
* `Username`: Der Benutzername für die [!DNL MBI] MySQL-Benutzer
* `Password`: Das Kennwort für die [!DNL MBI] MySQL-Benutzer
* `Port`: MySQL-Port auf Ihrem Server (`3306` standardmäßig)
* `Host`: Standardmäßig ist dies localhost. Im Allgemeinen ist dies der bind-address-Wert für Ihren MySQL-Server, der standardmäßig auf `127.0.0.1 (localhost)`, kann aber auch eine lokale Netzwerkadresse sein (z. B. `192.168.0.1`) oder der öffentlichen IP-Adresse Ihres Servers.

   Der Wert befindet sich in der `my.cnf` Datei (normalerweise unter `/etc/my.cnf`) unter der Zeile, die lautet `\[mysqld\]`. Wenn die bind-address-Zeile in dieser Datei auskommentiert ist, wird Ihr Server vor externen Verbindungsversuchen geschützt.

Das ist es! Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um das Setup abzuschließen.

## Verwandte Dokumentation

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=en)
