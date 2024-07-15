---
title: Google Analytics verbinden
description: Erfahren Sie, wie Sie Google Analytics mit [!DNL Commerce Intelligence] verbinden.
exl-id: 10e813f1-0306-4bdd-8222-e6364ac624de
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# [!DNL Google Analytics] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-analytics-logo.png)

[!DNL Google Analytics] ist der am häufigsten verwendete Webanalysedienst im Internet. Durch die Implementierung von [!DNL Google Analytics] auf Ihrer Website können Sie verfolgen, wie Besucher Ihre Site nutzen, welche Inhalte attraktiv sind, wo Besucher aussteigen und vieles mehr. Die Analyse dieser Metriken in [!DNL Commerce Intelligence] zusammen mit anderen Datenelementen verbessert den allgemeinen Zustand und die Benutzerfreundlichkeit Ihrer Site.

Geben Sie zunächst Ihre [!DNL Google Analytics] -Anmeldedaten in [!DNL Commerce Intelligence] ein:

1. Wechseln Sie zu &quot;**[!UICONTROL Manage Data** > **Integrations]**&quot;.

1. Klicken Sie auf **[!UICONTROL Add Integration]** rechts auf dem Bildschirm.

1. Klicken Sie auf das Symbol &quot;[!DNL Google Analytics]&quot;. Dadurch wird die Seite mit den Anmeldedaten für [!DNL Google Analytics] geöffnet.

1. Geben Sie Ihre [!DNL Google Analytics] -Anmeldedaten ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] umgeleitet.

1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL Commerce Intelligence] Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt Mehrere [!DNL Google Analytics] Profile verbinden weiter unten.

   ![](../../../assets/list-profile-id.png)<!--{: width="600px"}-->

1. Die Änderungen werden automatisch gespeichert. Klicken Sie daher nach Abschluss auf **Zurück zu Verbindungen** .

## Mehrere [!DNL Google Analytics] Profile verbinden

Möglicherweise sind mehrere Websites mit einem einzelnen [!DNL Google Analytics] -Konto verbunden, das durch ihre eigene [!DNL Google Analytics] -Profil-ID identifiziert wird. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einschließen. Überprüfen Sie die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID einer bestimmten Website:

1. Anmelden bei [!DNL Google Analytics]
1. Gehen Sie zum Dashboard der jeweiligen Website mit dem Tag &quot;[!DNL Google Analytics]&quot;
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht Zahlen nach `p` am Ende der Zeile:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## [!DNL Google Analytics] von [!DNL Commerce Intelligence] trennen {#disconnect}

1. Besuchen Sie die Seite [!DNL Google Analytics] [Kontoeinstellungen](https://accounts.google.com/) .
1. Klicken Sie unter dem Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte:

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verbinden [!DNL Google Adwords]](../integrations/google-adwords.md)
* [Analyse der Website-Aktivität und der Kundenkonversionsraten](../../analysis/web-act-cust-conversion.md)
* [Benutzerakquise-Daten mithilfe von [!DNL Google Analytics] Cookies verfolgen](../../analysis/google-track-user-acq.md)
