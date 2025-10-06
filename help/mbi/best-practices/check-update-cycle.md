---
title: Überprüfen des Status des Aktualisierungszyklus
description: Erfahren Sie, wie Sie den Status des Aktualisierungszyklus überprüfen.
exl-id: bd65f2bb-86c1-4e83-a132-797694ddb086
role: Admin, Data Architect, Data Engineer, User
feature: Dashboards
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Aktualisierungszyklus-Fortschritt

Wenn Sie sich bei Ihrem [!DNL Adobe Commerce Intelligence]-Dashboard anmelden, gibt es mehrere Möglichkeiten, den Status Ihres letzten Aktualisierungszyklus zu überprüfen. Alles hängt von der Art der [Benutzerberechtigungen](../administrator/user-management/user-management.md) ab, die Sie haben.

## Warum sollte ich den Status des Aktualisierungszyklus überprüfen?

Die Überprüfung des Status-Aktualisierungszyklus ist nützlich, wenn Sie die Daten in Ihrem [!DNL Commerce Intelligence]-Konto prüfen. Wenn Sie [Ergebnisse sehen, die nicht Ihren Erwartungen entsprechen](../data-analyst/data-warehouse-mgr/data-and-updates-faq.md) z. B. der tägliche Umsatz in [!DNL Commerce Intelligence] nicht mit dem übereinstimmt, was Sie auf Ihrer E-Commerce-Plattform oder in Ihrem [[!DNL Google] E-Commerce-Umsatz sehen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-google-ecommerce-revenue-discrepancies.html) können Sie den letzten Datenpunkt überprüfen, um festzustellen, ob das Problem behoben wird, sobald eine Aktualisierung abgeschlossen ist.

## [!UICONTROL Read-Only] und [!UICONTROL Standard] Benutzer

`Read-only` Benutzer können sich bei ihrem Dashboard anmelden und sehen, wie kürzlich die Daten aktualisiert wurden, indem sie den Mauszeiger über das Symbol oben rechts auf der Seite bewegen. Dies zeigt an, wann der letzte Datenpunkt abgerufen wurde.

![Zeitstempel der letzten erfolgreichen Datenaktualisierung in der -Benutzeroberfläche](../../mbi/assets/last-success-data.png)

## Benutzer [!UICONTROL Admin]

`Admin` Benutzer können sich beim Dashboard anmelden und den letzten obigen Datenpunkt zusammen mit einem kurzen Statussymbol ihrer Kontointegrationen sehen.

Admin-Benutzer können auch auf &quot;**[!UICONTROL Manage Data]**&quot; > &quot;**[!UICONTROL Integrations]**&quot; klicken, um weitere Informationen zu erhalten.

![Seite Datenintegrationen verwalten mit Verbindungsdetails und Aktualisierungsstatus](../../mbi/assets/detail-manage-data-integrations.png)

Auf dieser Seite werden der aktuelle Aktualisierungsstatus und die Zeit der letzten abgeschlossenen Aktualisierung angezeigt.

Wenn eine Aktualisierung ausgeführt wird, wird ein Link angezeigt, über den Sie nach Abschluss der Aktualisierung eine E-Mail-Benachrichtigung anfordern können.

Wenn keine Aktualisierung ausgeführt wird, wird ein Link angezeigt, über den Sie den Start einer Aktualisierung erzwingen können.

>[!NOTE]
>
>Wenn Sie Ausfallzeiten haben (Zeit, zu der Sie Ihre Daten nicht aktualisieren [!DNL Commerce Intelligence]), wird beim Erzwingen einer Aktualisierung ein Aktualisierungszyklus gestartet, der die Einschränkungen dieser Ausfallzeiten nicht berücksichtigt.
