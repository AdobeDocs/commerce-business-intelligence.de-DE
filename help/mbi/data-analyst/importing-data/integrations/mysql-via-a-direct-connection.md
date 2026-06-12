---
title: Verbinden von MySQL über eine direkte Verbindung
description: Erfahren Sie, wie Sie eine  [!DNL MongoDB]  über eine Direktverbindung herstellen.
exl-id: 53765844-c9bb-4a16-b00c-ce9672f87415
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/HkKVLKV9RpLIWN-YY5GggdnlHeBB2Xg9odAbSZklHGE
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 3a6b80d7bcfa5db4d86ab4da81239e3ea804f6ad
workflow-type: tm+mt
source-wordcount: 399
ht-degree: 0%

---

# [!DNL MySQL] über Direktverbindung verbinden

## In diesem Thema

* [Zugriff auf die IP [!DNL Commerce Intelligence] Adresse zulassen](#allowlist)
* [Erstellen Sie  [!DNL MySQL]  Benutzer für [!DNL Commerce Intelligence]](#steptwo)
* [Verbindungsinformationen eingeben in [!DNL Commerce Intelligence]](#stepthree)

## Zu springen

* [[!DNL MySQL] über `SSH tunnel`](../integrations/mysql-via-ssh-tunnel.md)
* [Überprüfung des SSH-Hostschlüssels](../integrations/ssh-host-key-verification.md)
* [[!DNL MySQL] über [!DNL cPanel]](../integrations/mysql-via-cpanel.md)

>[!NOTE]
>
>[!DNL Adobe] empfiehlt die Verwendung von [SSH](../integrations/mysql-via-ssh-tunnel.md) oder einer anderen Form der Verschlüsselung, um Ihre Daten zu schützen! Informationen zur Überprüfung des SSH-Hostschlüssels finden Sie unter [SSH-Hostschlüsselüberprüfung](../integrations/ssh-host-key-verification.md). Wenn dies keine Option ist, können Sie [!DNL Commerce Intelligence] dennoch direkt mit Ihrer Datenbank verbinden, indem Sie die Anweisungen in diesem Thema verwenden.

Dieses Thema führt Sie durch die direkte Verbindung Ihrer [!DNL MySQL] mit [!DNL Commerce Intelligence]. Diese Einstellungen können auch mit [!DNL Adobe Commerce] oder anderen eCommerce-Datenbanken verwendet werden, die MySQL verwenden.

## Zulassen des Zugriffs auf die [!DNL Commerce Intelligence] IP-Adressen {#allowlist}

Damit die Verbindung erfolgreich hergestellt werden kann, müssen Sie Ihre Firewall so konfigurieren, dass der Zugriff über Ihre IP-Adressen zulässig ist. Sie sind `54.88.76.97` und `34.250.211.151`, befinden sich aber auch auf der Seite [!DNL MySQL] Anmeldeinformationen :

![MBI_Allow_Access_IPs.png](../../../assets/MBI_allow_access_IPs.png)

## Erstellen eines [!DNL MySQL] Benutzers für [!DNL Commerce Intelligence]

Die einfachste Möglichkeit, einen `MySQL` Benutzer für [!DNL Commerce Intelligence] zu erstellen, besteht darin, die folgende Abfrage auszuführen, wenn Sie mit `GRANT` Berechtigungen bei `MySQL` angemeldet sind. Ersetzen Sie `Commerce Intelligence IP Address` durch die [!DNL Commerce Intelligence] IP-Adresse und ersetzen Sie `secure password` durch ein sicheres Kennwort Ihrer Wahl:

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

* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
