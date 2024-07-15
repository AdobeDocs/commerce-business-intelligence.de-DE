---
title: Google Analytics Warehouse verbinden
description: Erfahren Sie, wie Besucher Ihre Site nutzen, welche Inhalte attraktiv sind, wo Besucher aussteigen und vieles mehr.
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

[!DNL Google Analytics] ist der am häufigsten verwendete Webanalysedienst im Internet. Durch die Implementierung von [!DNL Google Analytics] auf Ihrer Website können Sie verfolgen, wie Besucher Ihre Site nutzen, welche Inhalte attraktiv sind, wo Besucher aussteigen und vieles mehr. [!DNL Google Analytics Warehoused] ist eine separate Integration von Ihrer vorhandenen [!DNL Google Analytics]-Integration. Dies ermöglicht eine bessere Analyse, da die [!DNL Google Analytics] -Daten in Ihrer Data Warehouse vorhanden sind, die sich vom Live-Feed der vorhandenen [!DNL Google Analytics] -Integration unterscheiden. Die Analyse dieser Metriken in [!DNL Commerce Intelligence] zusammen mit anderen Datenelementen verbessert den allgemeinen Zustand und die Benutzerfreundlichkeit Ihrer Site.

## Unterschied zwischen GA Warehouse und Live-Integration

Der Hauptunterschied besteht darin, dass eine Integration gespeichert wird ([!DNL Google Analytics Warehoused]) und die andere nicht ([!DNL Google Analytics Live]). Im Fall von [!DNL Google Analytics Warehoused] ermöglicht dies die Manipulation Ihrer [!DNL Google Analytics] -Daten und gibt Ihnen die Möglichkeit, [!DNL Google Analytics] und andere Datenquellen zu kombinieren, um aufschlussreiche Berichte zu erstellen.

Sehen Sie sich [!DNL Google Analytics] Anzeigenkampagnen an, um ein Beispiel dafür zu erhalten, was aus Sicht der Manipulation möglich ist. Angenommen, Sie hatten mehrere Werbekampagnen für das vierte Quartal mit unterschiedlichen Namen. Die Kampagnen waren das Ergebnis einer spezifischen Marketinginitiative. Mit gespeicherten Daten können Sie eine Spalte erstellen, in der die betreffenden Kampagnennamen gesucht und der vierte Quartalsinitiative-Name `Operation Dumbo` zurückgegeben wird.

Durch den kombinierten Aspekt können [!DNL Google Analytics] -Daten mit anderen Daten verknüpft werden, um Analysen durchzuführen. Nehmen Sie beispielsweise `Total Time On Site By Ad Campaign` Daten von [!DNL Google Analytics] und vergleichen Sie sie mit `Total Spent Per Campaign` Daten von [!DNL Facebook Ads], um ein vollständiges Bild davon zu erhalten, wie viel Interaktion Sie kostet.

Bei der Integration von [!DNL Google Analytics Live] dagegen ist jedes [!DNL Google Analytics]-Diagramm wie ein kleines Silo, das nicht in Ihrer Data Warehouse gespeichert ist.

## Verbinden von [!DNL Google Analytics Warehoused]

>[!INFO]
>
>[!DNL Google Analytics Warehoused] ist eine `Premium` Integration. [Wenden Sie sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) , wenn Sie daran interessiert sind, diese Integration zu Ihrem Abonnement hinzuzufügen.

1. Wechseln Sie zur Seite `Connections` unter **[!UICONTROL Admin** > **Integrations]**.
1. Klicken Sie auf **[!UICONTROL Add an Integration]** rechts.
1. Klicken Sie auf das Symbol &quot;[!DNL Google Analytics Warehoused]&quot;. Dadurch wird die Seite mit den Anmeldedaten für [!DNL Google Analytics] geöffnet.
1. Geben Sie Ihre [!DNL Google Analytics] -Anmeldedaten ein. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence] umgeleitet.
1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL Commerce Intelligence] Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt Mehrere [!DNL Google Analytics] Profile verbinden weiter unten.

## Mehrere [!DNL Google Analytics] Profile verbinden

Möglicherweise sind mehrere Websites mit einem einzelnen [!DNL Google Analytics] -Konto verbunden, das durch ihre eigene [!DNL Google Analytics] -Profil-ID identifiziert wird. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence] einschließen. Überprüfen Sie die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID einer bestimmten Website:

1. Anmelden bei [!DNL Google Analytics]
1. Gehen Sie zum Dashboard der jeweiligen Website mit dem Tag &quot;[!DNL Google Analytics]&quot;
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht Zahlen nach `p` am Ende der Zeile

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## [!DNL Google Analytics Warehoused] von [!DNL Commerce Intelligence] trennen {#disconnect}

1. Besuchen Sie die Seite [!DNL Google Analytics] [Kontoeinstellungen](https://myaccount.google.com/intro) .
1. Klicken Sie unter dem Abschnitt `Security` auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken Sie auf **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte Dokumentation

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verbinden [!DNL Google Adwords]](../integrations/google-adwords.md)
* [Analyse der Website-Aktivität und der Kundenkonversionsraten](../../analysis/web-act-cust-conversion.md)
* [Benutzerakquise-Daten mithilfe von [!DNL Google Analytics] Cookies verfolgen](../../analysis/google-track-user-acq.md)
