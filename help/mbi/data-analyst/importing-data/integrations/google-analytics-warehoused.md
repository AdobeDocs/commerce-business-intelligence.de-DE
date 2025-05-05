---
title: Google Analytics mit Lagerort verbinden
description: Erfahren Sie, wie Sie verfolgen können, wie Besucher Ihre Site verwenden, welche Inhalte attraktiv sind, wo Besucher die Site verlassen und vieles mehr.
exl-id: b9879399-9e1a-4f36-b510-8426ebc83aeb
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# [!DNL Google Analytics Warehoused] verbinden

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-analytics-logo.png)

[!DNL Google Analytics] ist der am häufigsten verwendete Webanalysedienst im Internet. Durch die Implementierung von [!DNL Google Analytics] auf Ihrer Website können Sie verfolgen, wie Besucher Ihre Site verwenden, welche Inhalte attraktiv sind, wo Besucher die Site verlassen und vieles mehr. [!DNL Google Analytics Warehoused] ist eine separate Integration von Ihrer vorhandenen [!DNL Google Analytics]. Es ermöglicht eine bessere Analyse, da sich die [!DNL Google Analytics] Daten auf Ihrem Data Warehouse befinden, was sich vom Live-Feed der vorhandenen [!DNL Google Analytics]-Integration unterscheidet. Die Analyse dieser Metriken in [!DNL Commerce Intelligence] verbessert zusammen mit anderen Daten den allgemeinen Zustand und die Benutzerfreundlichkeit Ihrer Site.

## Unterschied zwischen GA Warehouse- und Live-Integration

Das wichtigste Unterscheidungsmerkmal besteht darin, dass eine Integration gespeichert wird ([!DNL Google Analytics Warehoused]) und die andere nicht ([!DNL Google Analytics Live]). Im Falle von [!DNL Google Analytics Warehoused] ermöglicht dies die Manipulation Ihrer [!DNL Google Analytics] und bietet Ihnen die Möglichkeit, [!DNL Google Analytics] und andere Datenquellen zu kombinieren, um aufschlussreiche Berichte zu erstellen.

Ein Beispiel dafür, was aus Sicht der Manipulation getan werden kann, finden Sie in [!DNL Google Analytics] Anzeigenkampagnen . Angenommen, Sie hatten mehrere Anzeigenkampagnen für das vierte Quartal mit unterschiedlichen Namen. Die Kampagnen waren das Ergebnis einer bestimmten Marketing-Initiative. Mit gespeicherten Daten können Sie eine Spalte erstellen, die die betreffenden Kampagnennamen findet und den Namen der Initiative für das vierte Quartal von `Operation Dumbo` zurückgibt.

Der Kombinationsaspekt ermöglicht es, [!DNL Google Analytics] Daten mit anderen Daten zu verbinden, um Analysen durchzuführen. Nehmen Sie beispielsweise `Total Time On Site By Ad Campaign` Daten aus [!DNL Google Analytics] und verbinden Sie sie mit `Total Spent Per Campaign` Daten aus [!DNL Facebook Ads], um ein vollständiges Bild darüber zu erhalten, wie viel Interaktion Sie kostet.

Mit der [!DNL Google Analytics Live] Integration ist hingegen jedes [!DNL Google Analytics] wie ein kleines Silo, das nicht auf dem Data Warehouse abgelegt ist.

## [!DNL Google Analytics Warehoused]

>[!INFO]
>
>[!DNL Google Analytics Warehoused] ist eine `Premium`. [Wenden Sie sich an den ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de), wenn Sie diese Integration zu Ihrem Abonnement hinzufügen möchten.

1. Navigieren Sie zur `Connections` unter **[!UICONTROL Admin** > **Integrations]**.
1. Klicken Sie auf der rechten Seite auf **[!UICONTROL Add an Integration]**.
1. Klicken Sie auf das Symbol [!DNL Google Analytics Warehoused] . Dadurch wird die Seite mit den [!DNL Google Analytics]-Anmeldeinformationen geöffnet.
1. Geben Sie Ihre [!DNL Google Analytics] ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] weitergeleitet.
1. Eine Liste der Profil-IDs wird angezeigt. Markieren Sie die Profile, mit denen Sie eine Verbindung herstellen möchten[!DNL Commerce Intelligence]. Wenn Sie mehrere Profile haben und Hilfe bei der Identifizierung dessen benötigen, was ist, lesen Sie den Abschnitt Verbinden mehrerer [!DNL Google Analytics] Profile unten.

## Mehrere [!DNL Google Analytics] verbinden

Möglicherweise sind mehrere Websites mit einem einzigen [!DNL Google Analytics]-Konto verbunden, das durch seine eigene [!DNL Google Analytics]-Profil-ID identifiziert wird. In diesem Fall haben Sie die Möglichkeit, alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einzuschließen. Markieren Sie die Profil-IDs, die Sie in den Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics]-Profil-ID einer bestimmten Website:

1. Anmelden bei [!DNL Google Analytics]
1. Zum [!DNL Google Analytics]-Dashboard der jeweiligen Website wechseln
1. URL überprüfen - die Profil-ID entspricht den acht Zahlen, die auf `p` am Ende der Zeile folgen

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Trennen von [!DNL Google Analytics Warehoused] von [!DNL Commerce Intelligence] {#disconnect}

1. Rufen Sie [!DNL Google Analytics] Seite [Kontoeinstellungen](https://myaccount.google.com/intro) auf.
1. Klicken Sie im Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte Dokumentation

* [Integrationen erneut authentifizieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html?lang=de)
* [Verbinden [!DNL Google Adwords]](../integrations/google-adwords.md)
* [Analyse der Website-Aktivität und der Konversionsraten der Kunden](../../analysis/web-act-cust-conversion.md)
* [Tracking von Benutzerakquise-Daten mithilfe von  [!DNL Google Analytics] -Cookies](../../analysis/google-track-user-acq.md)
