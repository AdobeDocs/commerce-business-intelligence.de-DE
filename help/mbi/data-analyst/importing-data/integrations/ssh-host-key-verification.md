---
title: Überprüfung des SSH-Hostschlüssels
description: Erfahren Sie, wie Commerce Intelligence SSH-Hostschlüssel registriert, wie Sie sie aktualisieren, Fehler beheben und wann Sie sich an den Support für SSH-Tunnelverbindungen wenden können.
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
source-git-commit: b51e9fceba0c62f4ef3dde340d26cd78641ef3a2
workflow-type: tm+mt
source-wordcount: 1130
ht-degree: 0%

---

# Überprüfung des SSH-Hostschlüssels {#ssh-host-keys}

[!DNL Commerce Intelligence] verwendet eine strikte SSH-Hostschlüsselüberprüfung für verschlüsselte Datenbankverbindungen (SSH-Tunnel), einschließlich [MySQL](mysql-via-ssh-tunnel.md), [MongoDB](mongodb-via-ssh-tunnel.md) und [PostgreSQL](postgresql.md).

Während der **[!UICONTROL Save & Test]** registriert das System die SSH-Bastion-Hostschlüssel für Ihre Verbindung und speichert sie sicher pro Verbindung. Nach der Registrierung sind Replikation und Tunneling nur erfolgreich, wenn die Live-Bastion-Host-Schlüssel mit den registrierten Schlüsseln übereinstimmen.

Dieses Modell verbessert die Sicherheit, indem es Man-in-the-Middle-Angriffe und unerwartete Host-Änderungen blockiert. Dies bedeutet auch, dass die Rotation des Host-Schlüssels, fehlendes Vertrauensmaterial oder Infrastrukturänderungen als SSH-Host-Schlüssel-Fehler auf der Verbindung statt als generische Tunnelfehler auftauchen können.

>[!NOTE]
>
>**Admin** bedeutet, dass ein Benutzer Administratorberechtigungen für Ihr [!DNL Commerce Intelligence] hat, nicht für Ihre Adobe-Organisationskonsole, es sei denn, dies wurde anders angegeben. Nur Administratoren können **[!UICONTROL Refresh SSH Host Keys]** ausführen. Wenn diese Steuerung nicht angezeigt wird, bitten Sie einen Administrator in Ihrem Konto, die Aktualisierung auszuführen, oder wenden Sie sich an den Adobe-Support.

Sie können `known_hosts` Dateien nicht bearbeiten, hochladen oder verwalten. Registrierung und Aktualisierungsausführung in der Ihrem Konto zugewiesenen Adobe-Infrastruktur.

>[!IMPORTANT]
>
>Die Rotation des Host-Schlüssels erfordert eine Administratorin bzw. einen Administrator, um **[!UICONTROL Refresh SSH Host Keys]** auszuführen. **[!UICONTROL Save & Test]** Wenn sich die Bastionshostschlüssel geändert haben oder die Bastionsidentität geändert wurde (Hostname, IP oder Port), werden registrierte Schlüssel durch erneutes Ausführen oder erneutes Speichern der Verbindung nicht aktualisiert. Die Verbindung kann weiterhin fehlschlagen, bis ein Administrator die Hostschlüssel aktualisiert.

## Speichern und testen {#save-and-test}

**[!UICONTROL Save & Test]** führt **anfängliche SSH-Hostschlüsselregistrierung nur)**. Er ist absichtlich konservativ und dreht oder überschreibt keine Schlüssel, die bereits für die Verbindung registriert sind.

| Status des Host-Schlüssels | Speichervorgänge und Tests |
| --- | --- |
| Die Hostschlüssel sind noch nicht registriert | **[!UICONTROL Save & Test]** scannt den Bastion-Host und Port, registriert die Host-Schlüssel und speichert sie für diese Verbindung. |
| Die Hostschlüssel sind bereits registriert | **[!UICONTROL Save & Test]** überspringt die Registrierung. Vorhandene registrierte Schlüssel werden nicht überschrieben, gedreht oder gelöscht, auch wenn die Live-Bastion-Schlüssel nicht mehr übereinstimmen. |
| Die registrierten Schlüssel fehlen, sind leer oder ungültig | **[!UICONTROL Save & Test]** repariert kein ungültiges Vertrauensmaterial von sich aus. Ein Administrator muss **[!UICONTROL Refresh SSH Host Keys]** ausführen oder den Support kontaktieren, wenn die Fehler weiterhin bestehen |

Nach einer erfolgreichen ersten Registrierung führt **[!UICONTROL Save & Test]** später die Validierung der Anmeldeinformationen und Verbindungseinstellungen durch, lässt aber die registrierten SSH-Hostschlüssel unverändert.

## SSH-Hostschlüssel aktualisieren {#refresh-ssh-host-keys}

**[!UICONTROL Refresh SSH Host Keys]** aktualisiert registrierte SSH-Hostschlüssel, wenn die Bastion geändert wurde oder wenn Vertrauensmaterial repariert werden muss. Ein Administrator startet die Aktualisierung über die Verbindung in **[!UICONTROL Data]** > **[!UICONTROL Connections]**.

Die Aktualisierung wird asynchron in der Ihrem Konto zugewiesenen Adobe-Infrastruktur ausgeführt. [!DNL Commerce Intelligence] kehrt zurück, nachdem die Aktualisierung in die Warteschlange gestellt wurde. Die Überprüfung auf der Workstation wird nicht ausgeführt.

Eine Aktualisierung **schreibt** registrierte Hostschlüssel nur, wenn eine der folgenden Bedingungen erfüllt ist:

* Registrierte Hostschlüssel fehlen
* Registrierte Hostschlüssel sind leer
* Registrierte Hostschlüssel können nicht gelesen werden
* Die Validierung von registrierten Hostschlüsseln schlägt fehl
* Bei einem neuen Scan werden andere Host-Schlüsselzeilen als die registrierten Schlüssel zurückgegeben
* Die Fingerabdrücke der Überprüfung und der registrierten Schlüssel stimmen nicht überein

Wenn die registrierten Schlüssel aktuell und gültig sind, wird die Aktualisierung abgeschlossen, ohne sie zu ändern.

>[!TIP]
>
>Führen Sie **[!UICONTROL Refresh SSH Host Keys]** aus, nachdem Ihr Team die SSH-Hostschlüssel auf der Bastion gedreht, den Bastion-Hostnamen oder die IP geändert oder den SSH-Endpunkt ersetzt hat. Warten Sie einige Minuten und führen Sie dann **[!UICONTROL Save & Test]** aus, um die Verbindung zu bestätigen.

## Kontomigration {#migration}

Die Migration von Trigger-Konten wird nicht durchgeführt. Adobe führt Datenserververschiebungen während der Wartung oder Skalierung durch und kopiert registrierte SSH-Hostschlüssel, sodass die strenge Überprüfung auch nach dem Verschieben funktioniert.

Nachdem Adobe Sie über den Abschluss der Migration informiert hat:

1. Führen Sie **[!UICONTROL Save & Test]** aus, um die Verbindung zu bestätigen. Registrierung sollte übersprungen werden, wenn Schlüssel erfolgreich kopiert wurden.
1. Wenn der SSH-Hostschlüsselfehler weiterhin auftritt, bitten Sie einen Administrator, **[!UICONTROL Refresh SSH Host Keys]** auszuführen, einige Minuten zu warten und dann erneut **[!UICONTROL Save & Test]**.
1. Wenden Sie sich an den Adobe-Support, wenn nach **[!UICONTROL Save & Test]** und bis zu zwei **[!UICONTROL Refresh SSH Host Keys]** weiterhin Fehler auftreten.

## Fehlermeldungen zum SSH-Host-Schlüssel {#ssh-host-key-errors}

Der Verbindungsstatus zeigt eine einzige benutzerfreundliche SSH-Host-Schlüsselmeldung an. Rohe OpenSSH-Fehler werden nicht im Dashboard angezeigt.

In der folgenden Tabelle werden häufige Meldungen wahrscheinlichen Ursachen und typischen nächsten Schritten zugeordnet.

| Nachricht oder Status | Was es bedeutet | Mögliche Ursachen | Typischer nächster Schritt |
| --- | --- | --- | --- |
| Überprüfung des SSH-Hostschlüssels fehlgeschlagen | Der Bastion-Hostschlüssel stimmt nicht mit eingeschriebenen Schlüsseln überein, oder Vertrauensmaterial ist unbrauchbar | SSH-Hostschlüssel rotiert auf der Bastion; Bastion Hostname, IP oder Port geändert; Registrierte Schlüssel fehlen, leer, ungültig oder unlesbar | Bestätigen Sie **Remote-Adresse** und **SSH-Port**. Fragen Sie Ihr Infrastruktur-Team, ob sich die Bastion-Hostschlüssel geändert haben. Bitten Sie einen Administrator, **[!UICONTROL Refresh SSH Host Keys]** auszuführen, warten Sie einige Minuten und führen Sie dann **[!UICONTROL Save & Test]** aus. |
| SSH-Hostschlüssel konnten nicht registriert werden | **[!UICONTROL Save & Test]** konnte Bastion-Hostschlüssel nicht scannen oder speichern | Bastion von Adobe-Infrastruktur nicht erreichbar; DNS-Fehler; Firewall blockiert [!DNL Commerce Intelligence] IP-Adressen; falsche **Remote-Adresse** oder **SSH-Port**; Host-Schlüssel-Scan-Fehler auf der Bastion | Überprüfen Sie die Firewall-Zulassungsauflistung mithilfe der [!DNL Commerce Intelligence] IP-Adressen auf der Seite mit den Datenbankanmeldeinformationen. Bestätigen Sie, dass die Bastion SSH am konfigurierten Port akzeptiert. Korrigieren Sie die Verbindungsfelder und führen Sie **[!UICONTROL Save & Test]** erneut aus. |
| SSH-Hostschlüssel fehlen oder sind ungültig | Die strenge Verifizierung blockierte den Tunnel, da eingeschriebenes Vertrauensmaterial fehlt oder beschädigt ist | Die erste Verbindung hat die Registrierung nicht abgeschlossen. Vorherige Aktualisierung ist fehlgeschlagen. Migration hat keine Schlüssel kopiert. Problem mit Adobe-Infrastruktur. | Bitte einen Administrator, **[!UICONTROL Refresh SSH Host Keys]** auszuführen, und dann **[!UICONTROL Save & Test]**. Wenden Sie sich an den Support, wenn der Fehler weiterhin auftritt. |
| Aktualisierung der SSH-Hostschlüssel konnte nicht abgeschlossen werden | Bei der Aktualisierung wurden registrierte Schlüssel nicht aktualisiert | Netzwerk-, DNS- oder Scan-Fehler während der Aktualisierung; Problem in der Adobe-Infrastruktur | Warte einige Minuten. Bitten Sie einen Administrator, **[!UICONTROL Refresh SSH Host Keys]** erneut auszuführen (zweiter Versuch, wenn der erste fehlgeschlagen ist). Erreichbarkeit und Zulassungsauflistung der Bastion bestätigen. Wenden Sie sich an den Support, wenn die Verbindung nach zwei Aktualisierungsversuchen und **[!UICONTROL Save & Test]** immer noch fehlschlägt. |

## Fehlerbehebung - Checkliste {#troubleshooting}

1. Bestätigen Sie **dass die Einstellungen** Remote-Adresse **, SSH-Port** und Linux-Benutzereinstellungen mit Ihren Bastion-Einstellungen übereinstimmen.
1. Bestätigen Sie, dass Ihre Firewall die [!DNL Commerce Intelligence] IP-Adressen zulässt, die auf der Seite mit den Datenbankanmeldeinformationen angezeigt werden.
1. Fragen Sie Ihr Infrastruktur-Team, ob SSH-Hostschlüssel auf der Bastion kürzlich geändert wurden.
1. Führen Sie **[!UICONTROL Save & Test]** aus, um Einstellungen zu überprüfen und Schlüssel zu registrieren, wenn noch keine vorhanden sind.
1. Bitten Sie einen Administrator, **[!UICONTROL Refresh SSH Host Keys]** auszuführen, einige Minuten zu warten und dann erneut **[!UICONTROL Save & Test]**. Wenn der Fehler durch die erste Aktualisierung nicht behoben wird, wiederholen Sie diesen Schritt.
1. Wenn bei der Verbindung nach zwei Aktualisierungsversuchen weiterhin der Fehler SSH-Hostschlüssel angezeigt wird, klicken Sie auf der Seite „Verbindung“ (oder auf Ihrem Konto-Support-Kanal) auf **[!UICONTROL Contact Support]**.

## Wann Adobe-Support kontaktiert werden sollte {#contact-support}

Support kontaktieren, wenn:

* Fehler im SSH-Hostschlüssel treten weiterhin auf, nachdem eine Administratorin oder ein Administrator **[!UICONTROL Refresh SSH Host Keys]** zweimal ausgeführt wurde und **[!UICONTROL Save & Test]** dennoch fehlschlägt
* **[!UICONTROL Refresh SSH Host Keys]** wird nie abgeschlossen oder der Verbindungsstatus ändert sich nach 15-30 Minuten nicht
* Die Fehler begannen sofort, nachdem Adobe Sie über die Kontomigration oder die Wartung des Datenservers informiert hatte
* Bastion-Einstellungen und Firewall-Zulassungsauflistung sind korrekt, Ihr Team hat die Host-Schlüssel nicht rotiert und Sie können immer noch keine Verbindung herstellen
* Sie benötigen einen Administrator, um **[!UICONTROL Refresh SSH Host Keys]** auszuführen, aber es ist kein Administrator für das Konto verfügbar

Geben Sie den Verbindungsnamen, die ungefähre Zeit des letzten **[!UICONTROL Save & Test]**- oder Aktualisierungsversuchs an und geben Sie an, ob sich die Bastion-Host-Schlüssel kürzlich geändert haben. Senden Sie keine privaten Schlüssel oder Passphrasen.

## verwandt {#related}

* [MySQL über SSH-Tunnel verbinden](mysql-via-ssh-tunnel.md)
* [MongoDB über SSH-Tunnel verbinden](mongodb-via-ssh-tunnel.md)
* [PostgreSQL über SSH-Tunnel verbinden](postgresql.md)
* [Erneute Authentifizierung von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
