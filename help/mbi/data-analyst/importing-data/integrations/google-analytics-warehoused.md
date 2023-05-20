---
title: Google Analytics Warehouse verbinden
description: Erfahren Sie, wie Besucher Ihre Site nutzen, welche Inhalte attraktiv sind, wo Besucher aussteigen und vieles mehr.
exl-id: b9879399-9e1a-4f36-b510-8426ebc83aeb
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Verbinden [!DNL Google Analytics Warehoused]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

![](../../../assets/google-analytics-logo.png)

[!DNL Google Analytics] ist der am häufigsten verwendete Webanalysedienst im Internet. Implementieren [!DNL Google Analytics] auf Ihrer Website können Sie verfolgen, wie Besucher Ihre Site nutzen, welche Inhalte attraktiv sind, wo Besucher aussteigen und vieles mehr. [!DNL Google Analytics Warehoused] ist eine separate Integration von Ihrer vorhandenen [!DNL Google Analytics] Integration. Sie ermöglicht eine bessere Analyse, da die [!DNL Google Analytics] Daten in Ihrer Data Warehouse, die sich vom Live-Feed der vorhandenen [!DNL Google Analytics] Integration. Analysieren dieser Metriken in [!DNL Commerce Intelligence]- zusammen mit anderen Datenelementen - die allgemeine Gesundheit und Benutzerfreundlichkeit Ihrer Site verbessern.

## Unterschied zwischen GA Warehouse und Live-Integration

Der Hauptunterschied besteht darin, dass eine Integration gespeichert wird ([!DNL Google Analytics Warehoused]) und der andere nicht ([!DNL Google Analytics Live]). Im Falle von [!DNL Google Analytics Warehoused], ermöglicht dies die Manipulation Ihrer [!DNL Google Analytics] Daten und bietet Ihnen die Möglichkeit, [!DNL Google Analytics] und anderen Datenquellen, um eine aufschlussreiche Berichterstellung zu erstellen.

Sehen Sie sich an [!DNL Google Analytics] Anzeigenkampagnen für ein Beispiel dessen, was aus Sicht der Manipulation möglich ist. Angenommen, Sie hatten mehrere Werbekampagnen für das vierte Quartal mit unterschiedlichen Namen. Die Kampagnen waren das Ergebnis einer spezifischen Marketinginitiative. Mit gespeicherten Daten können Sie eine Spalte erstellen, in der die betreffenden Kampagnennamen gesucht werden und die den Namen der Initiative des vierten Quartals `Operation Dumbo`.

Der Kombinationsaspekt ermöglicht Folgendes: [!DNL Google Analytics] Daten, die mit anderen Daten verknüpft werden sollen, um Analysen durchzuführen. Nehmen Sie beispielsweise `Total Time On Site By Ad Campaign` Daten aus [!DNL Google Analytics] und verbinden Sie es mit `Total Spent Per Campaign` Daten aus [!DNL Facebook Ads] um ein vollständiges Bild davon zu erhalten, wie viel Interaktion Sie kostet.

Mit dem [!DNL Google Analytics Live] Integration, [!DNL Google Analytics] -Diagramm ist wie ein kleines Silo, das nicht in Ihrer Data Warehouse gespeichert ist.

## Verbinden [!DNL Google Analytics Warehoused]

>[!INFO]
>
>[!DNL Google Analytics Warehoused] ist `Premium` Integration. [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) , wenn Sie Interesse daran haben, diese Integration Ihrem Abonnement hinzuzufügen.

1. Navigieren Sie zu `Connections` Seite unter **[!UICONTROL Admin** > **Integrations]**.
1. Klicken **[!UICONTROL Add an Integration]**, auf der rechten Seite.
1. Klicken Sie auf [!DNL Google Analytics Warehoused] Symbol. Dadurch wird die [!DNL Google Analytics] Seite mit Anmeldeinformationen.
1. Geben Sie Ihre [!DNL Google Analytics] Anmeldedaten. Nach Abschluss des Autorisierungsprozesses werden Sie zurück zu [!DNL Commerce Intelligence].
1. Eine Liste der Profil-IDs wird angezeigt. Überprüfen Sie die Profile, mit denen Sie eine Verbindung herstellen möchten. [!DNL Commerce Intelligence]. Wenn Sie mehrere Profile haben und dabei behilflich sein müssen, welche Profile identifiziert werden können, lesen Sie den Abschnitt Mehrere Profile verbinden . [!DNL Google Analytics] Profile weiter unten.

## Mehrere Verbindungen herstellen [!DNL Google Analytics] profiles

Möglicherweise sind mehrere Websites mit einer [!DNL Google Analytics] eigenem Konto [!DNL Google Analytics] Profil-ID. In diesem Fall können Sie alle Ihre Profil-IDs in [!DNL Commerce Intelligence]. Überprüfen Sie die Profil-IDs, die Sie im Schritt zur Profilauswahl einbeziehen möchten.

So identifizieren Sie die [!DNL Google Analytics] Profil-ID:

1. Anmelden [!DNL Google Analytics]
1. Rufen Sie die Website auf [!DNL Google Analytics] Dashboard
1. Sehen Sie sich die URL an - die Profil-ID entspricht den acht folgenden Zahlen `p` am Zeilenende

   `www.google.com/analytics/web/#home/a11345062w43527078p**XXXXXXXX**/`

## Verbindung [!DNL Google Analytics Warehoused] von [!DNL Commerce Intelligence] {#disconnect}

1. Besuchen Sie Ihre [!DNL Google Analytics] [Kontoeinstellungen](https://myaccount.google.com/intro) Seite.
1. Unter dem `Security` und klicken Sie auf **[!UICONTROL edit]** neben `Authorizing` Anwendungen und Sites.
1. Klicken **[!UICONTROL revoke access]** neben [!DNL Commerce Intelligence].

## Verwandte Dokumentation

* [Erneutes Authentifizieren von Integrationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-reauthenticating-integrations.html)
* [Verbinden [!DNL Google Adwords]](../integrations/google-adwords.md)
* [Analyse der Website-Aktivität und der Kundenkonversionsraten](../../analysis/web-act-cust-conversion.md)
* [Tracking von Benutzerakquise-Daten mithilfe von [!DNL Google Analytics] Cookies](../../analysis/google-track-user-acq.md)
