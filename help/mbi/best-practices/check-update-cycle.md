---
title: Überprüfen des Aktualisierungszyklusstatus
description: Erfahren Sie, wie Sie den Status des Aktualisierungszyklus überprüfen.
exl-id: bd65f2bb-86c1-4e83-a132-797694ddb086
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Fortschritt des Aktualisierungszyklus

Wenn Sie sich bei Ihrem [!DNL MBI] Dashboard gibt es mehrere Möglichkeiten, den Status Ihres letzten Aktualisierungszyklus zu überprüfen. Alles hängt vom Typ [Benutzerberechtigungen](../administrator/user-management/user-management.md) haben.

## Warum sollte ich den Status des Aktualisierungszyklus überprüfen?

Die Überprüfung des Status-Aktualisierungszyklus ist nützlich, wenn Sie die Daten in Ihrem [!DNL MBI] -Konto. Wenn [Ergebnisse, die nicht Ihren Erwartungen entsprechen](../data-analyst/data-warehouse-mgr/data-and-updates-faq.md)z. B. täglicher Umsatz in [!DNL MBI] nicht mit dem übereinstimmen, was Sie in Ihrer E-Commerce-Plattform oder in Ihrer [[!DNL Google] E-Commerce-Umsätze](https://support.magento.com/hc/en-us/articles/360016505232) Sie können den letzten Datenpunkt überprüfen, um festzustellen, ob das Problem nach Abschluss einer Aktualisierung behoben wird.

## [!UICONTROL Read-Only] und [!UICONTROL Standard]** Benutzer

`Read-only` -Benutzer können sich bei ihrem Dashboard anmelden und sehen, wie kürzlich die Daten aktualisiert wurden, indem sie den Mauszeiger über das Symbol oben rechts auf der Seite bewegen. Dadurch wird angezeigt, wann der letzte Datenpunkt abgerufen wurde.

![](../../mbi/assets/last-success-data.png)

## [!UICONTROL Admin] Benutzer

`Admin` -Benutzer können sich beim Dashboard anmelden und den letzten Datenpunkt oben sowie ein kurzes Statussymbol ihrer Kontointegrationen anzeigen.

Für weitere Details können Admin-Benutzer auf **[!UICONTROL Manage Data]** > **[!UICONTROL Integrations]**.

![](../../mbi/assets/detail-manage-data-integrations.png)

Auf dieser Seite werden der aktuelle Aktualisierungsstatus und der Zeitpunkt der letzten abgeschlossenen Aktualisierung angezeigt.

Wenn derzeit eine Aktualisierung durchgeführt wird, wird ein Link angezeigt, über den nach Abschluss der Aktualisierung eine E-Mail-Benachrichtigung angefordert werden kann.

Wenn keine Aktualisierung ausgeführt wird, wird ein Link angezeigt, über den das Starten einer Aktualisierung erzwungen werden kann.

>[!NOTE]
>
>Wenn Sie Stunden des Ausfalls haben (Uhrzeit, zu der Sie nicht möchten [!DNL MBI] zum Aktualisieren Ihrer Daten), wird beim Erzwingen einer Aktualisierung ein Aktualisierungszyklus gestartet, der die Einschränkungen dieser Blackout-Zeiten nicht berücksichtigt.
