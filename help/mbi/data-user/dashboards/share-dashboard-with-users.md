---
title: Dashboards für andere Benutzer freigeben
description: Erfahren Sie, wie Sie Dashboards für andere Benutzer freigeben können.
exl-id: 6279b049-d1b2-4d40-b30b-ee8772e990f4
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Dashboards für andere Benutzer freigeben

Die Freigabe von Dashboards ist eine hervorragende Möglichkeit, Ihr Team in der Warteschlange zu halten und eine partizipative Diskussion zu fördern. Durch die Erstellung und Freigabe eines zentralen Dashboards können Sie Ihrem Team die benötigten Informationen bereitstellen und gleichzeitig die Kontrolle behalten. [[!DNL Adobe] empfiehlt](../../best-practices/share-dashboard-best-practice.md){: target=&quot;_blank&quot;}, das Sie gewähren `Edit` Rechte an ausgewählte Personen festzulegen, um versehentliche Änderungen zu minimieren.

>[!NOTE]
>
>Wenn das Dashboard, auf das Sie zugreifen, Berichte enthält, die mit Metriken erstellt wurden, auf die ein bestimmter Benutzer keinen Zugriff hat, wird in den Berichten eine `Error Loading Data` Nachricht. Wenn die Daten für den jeweiligen Benutzer angezeigt werden sollen, wird ein [Admin-Benutzer](../../administrator/user-management/user-management.md) muss Zugriff auf alle in diesen Berichten verwendeten Metriken gewähren.

## Dashboard freigeben

1. Klicken **[!UICONTROL Share Dashboard]** oben auf dem Bildschirm.

   Eine Liste aller Benutzer in Ihrer [!DNL Commerce Intelligence] -Konto angezeigt.

1. Um einen Benutzer auszuwählen, für den das Dashboard freigegeben werden soll, aktivieren Sie das Kontrollkästchen links neben seinem Namen.

   Um alle Benutzer auszuwählen/deren Auswahl aufzuheben, klicken Sie auf **[!UICONTROL Select]** und wählen Sie `Everyone` oder `None`zurück.

1. Berechtigungen können von Benutzer zu Benutzer oder en masse festgelegt werden.

   *So legen Sie individuelle Berechtigungen fest* klicken **[!UICONTROL None]** rechts neben dem Namen des Benutzers. Wählen Sie in diesem Dropdown-Menü den Berechtigungstyp des Benutzers aus.

   *So legen Sie Berechtigungen in Massen fest* klicken **[!UICONTROL Set Permissions]**. Wählen Sie in diesem Dropdown-Menü den Berechtigungstyp aus, den die ausgewählten Benutzer haben sollen.

   >[!NOTE]
   >
   >Sie können diese Funktion auch verwenden, um zuvor festgelegte Berechtigungen zu aktualisieren. Wenn Sie beispielsweise die Freigabe des Dashboards für eine Person beenden möchten, legen Sie deren Berechtigungen auf `None`.

1. Um das Dashboard freizugeben, klicken Sie auf **[!UICONTROL Save Changes]**. Die ausgewählten Benutzer erhalten eine E-Mail, in der sie zum Anzeigen des Dashboards eingeladen werden.

Beispiel:

![Freigabe-Dashboard](../../assets/Share_Dashboards.gif)
