---
title: Google Analytics verbinden
description: Erfahren Sie, wie Sie Google Analytics verbinden können mit [!DNL Commerce Intelligence].
exl-id: 10e813f1-0306-4bdd-8222-e6364ac624de
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Verbinden [!DNL Google Analytics]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-analytics-logo.png)

[!DNL Google Analytics] ist der am häufigsten verwendete Webanalysedienst im Internet. Implementieren [!DNL Google Analytics] auf Ihrer Website können Sie verfolgen, wie Besucher Ihre Site nutzen, welche Inhalte attraktiv sind, wo Besucher aussteigen und vieles mehr. Analysieren dieser Metriken in [!DNL Commerce Intelligence]- zusammen mit anderen Datenelementen - die allgemeine Gesundheit und Benutzerfreundlichkeit Ihrer Site verbessern.

Erste Schritte mit der Eingabe Ihrer [!DNL Google Analytics] Anmeldedaten [!DNL Commerce Intelligence]:

1. Navigieren Sie zu **[!UICONTROL Manage Data** > **Integrations]**.

1. Klicken **[!UICONTROL Add Integration]** auf der rechten Seite des Bildschirms.

1. Klicken Sie auf [!DNL Google Analytics] Symbol. Dadurch wird die [!DNL Google Analytics] Seite mit Anmeldeinformationen.

1. Geben Sie Ihre [!DNL Google Analytics] Anmeldedaten. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence].

1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL Commerce Intelligence]. Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt Mehrere Profile verbinden . [!DNL Google Analytics] Profile weiter unten.

   ![](../../../assets/list-profile-id.png)<!--{: width="600px"}-->

1. Änderungen werden automatisch gespeichert. Klicken Sie daher auf **Zurück zu Verbindungen** wenn Sie fertig sind.

## Mehrere Verbindungen herstellen [!DNL Google Analytics] profiles

Möglicherweise sind mehrere Websites mit einer [!DNL Google Analytics] eigenem Konto [!DNL Google Analytics] Profil-ID. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence]. Überprüfen Sie die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID:

1. Anmelden [!DNL Google Analytics]
1. Rufen Sie die Website auf [!DNL Google Analytics] Dashboard
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht folgenden Zahlen `p` am Ende der Zeile:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Verbindung [!DNL Google Analytics] von [!DNL Commerce Intelligence] {#disconnect}

1. Besuchen Sie Ihre [!DNL Google Analytics] [Kontoeinstellungen](https://accounts.google.com/) Seite.
1. Unter dem `Security` und klicken Sie auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verbinden [!DNL Google Adwords]](../integrations/google-adwords.md)
* [Analyse der Website-Aktivität und der Kundenkonversionsraten](../../analysis/web-act-cust-conversion.md)
* [Tracking von Benutzerakquise-Daten mithilfe von [!DNL Google Analytics] Cookies](../../analysis/google-track-user-acq.md)
