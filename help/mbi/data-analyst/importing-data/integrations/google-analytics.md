---
title: Google Analytics verbinden
description: Erfahren Sie, wie Sie eine Verbindung zwischen Google Analytics und  [!DNL Commerce Intelligence] herstellen.
exl-id: 10e813f1-0306-4bdd-8222-e6364ac624de
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/wSR5SWYSfmNZkzp5QxTUwv6QSsynXYofmRkKbvMsohs
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 283
ht-degree: 0%

---

# [!DNL Google Analytics] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![Google Analytics-Logo](../../../assets/google-analytics-logo.png)

[!DNL Google Analytics] ist der am häufigsten verwendete Webanalysedienst im Internet. Durch die Implementierung von [!DNL Google Analytics] auf Ihrer Website können Sie verfolgen, wie Besucher Ihre Site verwenden, welche Inhalte attraktiv sind, wo Besucher die Site verlassen und vieles mehr. Die Analyse dieser Metriken in [!DNL Commerce Intelligence] verbessert zusammen mit anderen Daten den allgemeinen Zustand und die Benutzerfreundlichkeit Ihrer Site.

Beginnen Sie, indem Sie Ihre [!DNL Google Analytics]-Anmeldedaten in [!DNL Commerce Intelligence]:

1. Gehe zu **[!UICONTROL Manage Data** > **Integrations]**.

1. Klicken Sie auf **[!UICONTROL Add Integration]** rechts im Bildschirm.

1. Klicken Sie auf das Symbol [!DNL Google Analytics] . Dadurch wird die Seite mit den [!DNL Google Analytics]-Anmeldeinformationen geöffnet.

1. Geben Sie Ihre [!DNL Google Analytics] ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.

1. Eine Liste der Profil-IDs wird angezeigt. Markieren Sie die Profile, mit denen Sie eine Verbindung herstellen möchten[!DNL Commerce Intelligence]. Wenn Sie mehrere Profile haben und Hilfe bei der Identifizierung dessen benötigen, was ist, lesen Sie den Abschnitt Verbinden mehrerer [!DNL Google Analytics] Profile unten.

   ![Google Analytics-Admin-Seite mit Profil-ID in URL](../../../assets/list-profile-id.png)<!--{: width="600px"}-->

1. Die Änderungen werden automatisch gespeichert. Klicken Sie **auf „Zurück zu**&quot;, wenn Sie fertig sind.

## Mehrere [!DNL Google Analytics] verbinden

Möglicherweise sind mehrere Websites mit einem einzigen [!DNL Google Analytics]-Konto verbunden, das durch seine eigene [!DNL Google Analytics]-Profil-ID identifiziert wird. In diesem Fall haben Sie die Möglichkeit, alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einzuschließen. Markieren Sie die Profil-IDs, die Sie in den Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics]-Profil-ID einer bestimmten Website:

1. Anmelden bei [!DNL Google Analytics]
1. Zum [!DNL Google Analytics]-Dashboard der jeweiligen Website wechseln
1. Sehen Sie sich die URL an. Die Profil-ID entspricht den acht Zahlen, die am Ende der Zeile nach `p` folgen:

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Trennen von [!DNL Google Analytics] von [!DNL Commerce Intelligence] {#disconnect}

1. Rufen Sie [!DNL Google Analytics] Seite [Kontoeinstellungen](https://accounts.google.com/) auf.
1. Klicken Sie im Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandt:

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
* [Verbinden [!DNL Google Adwords]](../integrations/google-adwords.md)
* [Analyse der Website-Aktivität und der Konversionsraten der Kunden](../../analysis/web-act-cust-conversion.md)
* [Tracking von Benutzerakquise-Daten mithilfe von  [!DNL Google Analytics] -Cookies](../../analysis/google-track-user-acq.md)
