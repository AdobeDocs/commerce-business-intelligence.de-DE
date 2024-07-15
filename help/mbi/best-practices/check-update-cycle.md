---
title: Überprüfen des Aktualisierungszyklusstatus
description: Erfahren Sie, wie Sie den Status des Aktualisierungszyklus überprüfen.
exl-id: bd65f2bb-86c1-4e83-a132-797694ddb086
role: Admin, Data Architect, Data Engineer, User
feature: Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Fortschritt des Aktualisierungszyklus

Wenn Sie sich bei Ihrem [!DNL Adobe Commerce Intelligence] -Dashboard anmelden, gibt es mehrere Möglichkeiten, den Status Ihres letzten Aktualisierungszyklus zu überprüfen. Das alles hängt vom Typ der [Benutzerberechtigungen](../administrator/user-management/user-management.md) ab, die Sie haben.

## Warum sollte ich den Status des Aktualisierungszyklus überprüfen?

Die Überprüfung des Status-Aktualisierungszyklus ist nützlich, wenn Sie die Daten in Ihrem [!DNL Commerce Intelligence] -Konto überprüfen. Wenn Sie beispielsweise [Ergebnisse sehen, die nicht Ihren Erwartungen entsprechen](../data-analyst/data-warehouse-mgr/data-and-updates-faq.md), stimmen die täglichen Verkäufe in [!DNL Commerce Intelligence] nicht mit denen in Ihrer E-Commerce-Plattform oder Ihrem [[!DNL Google] E-Commerce-Umsatz](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-google-ecommerce-revenue-discrepancies.html) überein, können Sie den letzten Datenpunkt überprüfen, um festzustellen, ob das Problem nach Abschluss der Aktualisierung behoben wurde.

## [!UICONTROL Read-Only] und [!UICONTROL Standard] Benutzer

`Read-only` -Benutzer können sich bei ihrem Dashboard anmelden und sehen, wie kürzlich die Daten aktualisiert wurden, indem sie den Mauszeiger über das Symbol oben rechts auf der Seite bewegen. Dies zeigt, wann der letzte Datenpunkt abgerufen wurde.

![](../../mbi/assets/last-success-data.png)

## [!UICONTROL Admin] Benutzer

`Admin` -Benutzer können sich beim Dashboard anmelden und den letzten Datenpunkt oben sowie ein kurzes Statussymbol ihrer Kontointegrationen anzeigen.

Für weitere Details können Admin-Benutzer auf **[!UICONTROL Manage Data]** > **[!UICONTROL Integrations]** klicken.

![](../../mbi/assets/detail-manage-data-integrations.png)

Auf dieser Seite werden der aktuelle Aktualisierungsstatus und der Zeitpunkt der letzten abgeschlossenen Aktualisierung angezeigt.

Wenn eine Aktualisierung ausgeführt wird, wird ein Link angezeigt, über den nach Abschluss der Aktualisierung eine E-Mail-Benachrichtigung angefordert werden kann.

Wenn keine Aktualisierung ausgeführt wird, wird ein Link angezeigt, über den das Starten einer Aktualisierung erzwungen werden kann.

>[!NOTE]
>
>Wenn Sie Blackout-Stunden haben (Zeit, in der Sie Ihre Daten nicht mit [!DNL Commerce Intelligence] aktualisieren möchten), wird beim Erzwingen einer Aktualisierung ein Aktualisierungszyklus gestartet, der die Einschränkungen dieser Blackout-Stunden nicht berücksichtigt.
