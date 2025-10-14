---
title: Verbinden von MySQL über eine direkte Verbindung
description: Erfahren Sie, wie Sie eine  [!DNL MongoDB]  über eine Direktverbindung herstellen.
exl-id: 53765844-c9bb-4a16-b00c-ce9672f87415
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# [!DNL MySQL] über Direktverbindung verbinden

## In diesem Thema

* [Zugriff auf die IP [!DNL Commerce Intelligence] Adresse zulassen](#allowlist)
* [Erstellen Sie  [!DNL MySQL]  Benutzer für [!DNL Commerce Intelligence]](#steptwo)
* [Verbindungsinformationen eingeben in [!DNL Commerce Intelligence]](#stepthree)

## Zu springen

* [[!DNL MySQL] über &#x200B;](../integrations/mysql-via-ssh-tunnel.md)
* [[!DNL MySQL] über [!DNL cPanel]](../integrations/mysql-via-cpanel.md)

>[!NOTE]
>
>[!DNL Adobe] empfiehlt die Verwendung von [SSH](../integrations/mysql-via-ssh-tunnel.md) oder einer anderen Form der Verschlüsselung, um Ihre Daten zu schützen! Wenn dies keine Option ist, können Sie [!DNL Commerce Intelligence] dennoch direkt mit Ihrer Datenbank verbinden, indem Sie die Anweisungen in diesem Thema verwenden.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL] mit [!DNL Commerce Intelligence]. Diese Einstellungen können auch mit [!DNL Adobe Commerce] oder anderen eCommerce-Datenbanken verwendet werden, die MySQL verwenden.

## Zulassen des Zugriffs auf die [!DNL Commerce Intelligence] IP-Adressen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff über Ihre IP-Adressen zulässig ist. Sie sind `54.88.76.97` und `34.250.211.151`, befinden sich aber auch auf der Seite [!DNL MySQL] Anmeldeinformationen :

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen eines [!DNL MySQL] Benutzers für [!DNL Commerce Intelligence]

Die einfachste Möglichkeit, einen `MySQL` Benutzer für [!DNL Commerce Intelligence] zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie mit `MySQL` Berechtigungen bei `GRANT` angemeldet sind. Ersetzen Sie `Commerce Intelligence IP Address` durch die [!DNL Commerce Intelligence] IP-Adresse und ersetzen Sie `secure password` durch ein sicheres Kennwort Ihrer Wahl:

```sql
    GRANT SELECT ON *.* TO 'magentobi'@'<Commerce Intelligence IP address>' IDENTIFIED BY '<secure password>';
```

Um den Zugriff dieses Benutzers auf Daten in bestimmten Datenbanken, Tabellen oder Spalten zu beschränken, können Sie stattdessen Abfragen ausführen, `GRANT` nur den Zugriff auf die Daten zulassen, die Sie zulassen.

**Führen Sie die GRANT-Abfrage für alle erforderlichen IPs mit demselben Benutzer und Kennwort erneut aus.**

## Verbindungsinformationen in Commerce Intelligence eingeben

Um alles abzuschließen, müssen Sie die Verbindung und die Benutzerinformationen in [!DNL Commerce Intelligence] eingeben. Haben Sie die Seite mit den [!DNL MySQL]-Anmeldeinformationen geöffnet gelassen? Wenn nicht, gehen Sie zu **[!UICONTROL Data** > **Connections]** und klicken Sie auf **[!UICONTROL Add New Data Source]** und klicken Sie dann auf das Symbol [!DNL MySQL] . Vergessen Sie nicht, den Umschalter `Encrypted` in `Yes` zu ändern.

Geben Sie die folgenden Informationen auf dieser Seite ein, beginnend mit dem Abschnitt `Database Connection` :

* `Connection Nickname`: Geben Sie einen Namen für die Integration ein (z. B. E-Commerce-Store)
* `Username`: Der Benutzername für den [!DNL Commerce Intelligence] [!DNL MySQL] Benutzer
* `Password`: Das Kennwort für den [!DNL Commerce Intelligence] [!DNL MySQL]
* `Port`: Port von MySQL auf Ihrem Server (standardmäßig `3306`)
* `Host`: Standardmäßig ist dies localhost. Im Allgemeinen ist dies der Wert der Bindungsadresse für Ihren [!DNL MySQL]-Server, der standardmäßig `127.0.0.1 (localhost)` ist, aber auch eine lokale Netzwerkadresse (z. B. `192.168.0.1`) oder die öffentliche IP-Adresse Ihres Servers sein kann.

  Den Wert finden Sie in Ihrer `my.cnf`-Datei (unter `/etc/my.cnf`) unter der Zeile, die `\[mysqld\]` liest. Wenn die Zeile „bind-address“ in dieser Datei auskommentiert ist, ist Ihr Server vor externen Verbindungsversuchen geschützt.

Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save & Test]** , um die Einrichtung abzuschließen.

## Verwandte Dokumentation

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
