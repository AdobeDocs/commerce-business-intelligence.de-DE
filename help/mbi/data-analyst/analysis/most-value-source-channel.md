---
title: Identifizieren Ihrer wertvollsten Marketing-Quellen und -Kanäle
description: Erfahren Sie mehr über einige Berichte, mit denen Sie Ihre wertvollsten Marketing-Kanäle aufdecken können.
exl-id: 8d25bc80-ea60-47db-b01b-04a23a24c14d
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---

# Identifizieren erfolgreicher Marketing-Quellen

Sie haben Ihre Zielgruppe recherchiert, Ihre Kampagne erstellt und in ein paar Marketing-Kanäle investiert. Nun, da einige Zeit vergangen ist, wie funktionieren diese Kanäle? Welcher Kanal hat die meisten neuen Benutzer hervorgebracht? Welche Quelle hat am meisten zu Ihrem Gesamtumsatz beigetragen?

Mit [!DNL Adobe Commerce Intelligence] können Sie Ihre Umsätze und Benutzer einfach nach Empfehlungsquelle segmentieren, unabhängig davon, ob diese [[!DNL [Google Analytics' UTM fields]]](https://support.google.com/analytics/answer/1191184?hl=en) oder benutzerdefinierten Datenfeldern entspricht. Diese Segmentierung ermöglicht es Ihnen, die Kanäle mit der besten Leistung zu finden und Ihr Marketing-Budget besser zu investieren.

In diesem Thema werden einige Berichte vorgestellt, mit denen Sie Ihre wertvollsten Marketing-Kanäle aufdecken können:

* [Neue Benutzer nach Quellen](#newusersbysource)
* [Durchschnittlicher Lebensdauerumsatz nach Benutzerquelle](#avglifetimerev)
* [Durchschnittlicher Bestellwert nach Benutzerquelle](#avgorderval)
* [Umsatz nach Benutzerregistrierungsdatum und Quellen](#revbyregdateandsource)
* [Wiederholungsaufträge nach Benutzerquelle](#repeatordersbysource)

## Voraussetzungen {#prereqs}

Um die Analysen in diesem Thema zu erstellen, benötigen Sie Zugriff auf Daten aus Marketing-Akquise-/Empfehlungsquellen. Wenn Sie sie noch nicht verfolgen, müssen Sie [Daten zu Bestellungsreferenzen aus [!DNL Google ECommerce]](../importing-data/integrations/google-ecommerce.md) in [!DNL Adobe Commerce Intelligence] importieren, bevor Sie fortfahren können. Durch Hinzufügen von Benutzergeräteinformationen zu Ihren Analysen können Sie außerdem sehen, welche Technologie Ihre Empfehlungen verwenden.

## Neue Benutzer nach Quelle {#newusersbysource}

Die Bewertung der Leistung von Empfehlungsquellen ist für die Bestimmung Ihrer wertvollsten Kanäle von entscheidender Bedeutung. Dieser Bericht zeigt die Anzahl der neu registrierten Benutzer nach Akquise-Quelle im Laufe der Zeit an, sodass Sie die Leistung von Empfehlungsquellen bei der Akquise neuer registrierter Benutzer verfolgen können.

Um diesen Bericht im [Report Builder ](../../tutorials/using-visual-report-builder.md) zu erstellen, fügen Sie die Metrik **Neue Benutzer** (oder eine äquivalente Metrik, die die Anzahl der neuen Benutzer im Zeitverlauf zählt) zum Bericht hinzu. Gehen Sie dann wie folgt vor:

1. Legen Sie die [!UICONTROL Time Period] auf den Registrierungszeitraum fest, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Interval] auf monatlich fest.
1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird die [!UICONTROL chart type] `stacked columns` verwendet.

Im Folgenden finden Sie eine visuelle Anleitung:

![Erstellen eines Berichts „Neue Benutzer nach Quelle“.](../../assets/New_Users_by_source.gif)

## Durchschnittlicher Lebensdauerumsatz nach Benutzerquelle {#avglifetimerev}

Es ist wichtig, die Kanäle zu finden, über die neue Benutzende eingebunden werden. Aber wie wertvoll sind diese Empfehlungen insgesamt? Dieser Bericht zeigt den durchschnittlichen Lebensdauerumsatz von Benutzern aus bestimmten Akquise-Quellen im Zeitverlauf. Mit anderen Worten: Auf diese Weise können Sie sehen, ob Benutzer, die von einer bestimmten Quelle erworben wurden, während ihres Lebenszyklus mehr für Sie ausgeben als eine Gruppe von Benutzern, die von einer anderen Quelle erfasst wurden.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die Metrik **Durchschnittlicher Lebensdauerumsatz** zum Bericht hinzu. Gehen Sie dann wie folgt vor:

1. Legen Sie die [!UICONTROL Time Period] auf den Zeitraum fest, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Interval] auf monatlich fest.
   [!UICONTROL Group By] Sie auf die Quelle der Akquise (oder Empfehlung) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der `line chart` verwendet.

Im Folgenden finden Sie eine visuelle Anleitung:

![Durchschnittlicher Lebensdauerumsatz nach Benutzerquelle ](../../assets/Lifetime_revenue_by_user_source.gif).

In diesem Beispiel wird nur der Lebensdauerumsatz untersucht. Sie können diese Analyse aber auch replizieren, um die [!UICONTROL Number of orders] oder [!UICONTROL Distinct buyers] nach Empfehlungsquelle zu untersuchen.

## Durchschnittlicher Bestellwert nach Benutzerquelle {#avgorderval}

Um eine bessere Vorstellung davon zu bekommen, wie viel Geld Benutzer aus einer bestimmten Akquisitionsquelle ausgeben, können Sie einen Bericht erstellen, der ihren durchschnittlichen Bestellwert berücksichtigt. Auf diese Weise können Sie verfolgen, ob Benutzer, die von einer bestimmten Quelle erworben wurden, mehr pro Bestellung ausgeben als Benutzer aus einer anderen Quelle.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die Metrik **Durchschnittlicher Bestellwert** hinzu und führen Sie dann die folgenden Schritte aus:

1. Legen Sie die [!UICONTROL Time Period] auf den Registrierungszeitraum fest, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Time Interval] auf monatlich fest.
1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Diagrammtyp **Gestapelte Spalten** verwendet.

Im Folgenden finden Sie eine visuelle Anleitung:

![Bericht „Durchschnittlicher Bestellwert nach Benutzerquelle“ wird erstellt.](../../assets/Average_order_value_by_source.gif)

## Gesamtumsatz nach Benutzerregistrierungsdatum und Quelle {#revbyregdateandsource}

Die zuvor behandelte Analyse des Lebensdauerumsatzes ermöglicht es, den durchschnittlichen Lebensdauerumsatz von Benutzern anzuzeigen, der aus verschiedenen Quellen erzielt wurde. Was ist aber mit dem gesamten Lebensdauerumsatz? Dieser Bericht ermöglicht es Ihnen festzustellen, wie viel Umsatz Benutzer insgesamt generieren, die sich während einer bestimmten Zeit registriert und aus einer bestimmten Quelle generiert haben.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die `Revenue by user registration date` hinzu. Wenn Sie [diese Metrik](../../data-user/reports/ess-manage-data-metrics.md) noch nicht erstellt haben, können Sie dies tun, indem Sie die `Revenue` Metrik replizieren und die `time stamp` in die `creation date` des Benutzers ändern. Nachdem Sie die Metrik hinzugefügt haben, gehen Sie wie folgt vor:

1. Legen Sie die [!UICONTROL Time Period] auf den Registrierungszeitraum fest, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Time Interval] auf monatlich fest.
1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Diagrammtyp `stacked columns` verwendet.

Im Folgenden finden Sie eine visuelle Anleitung:

![Erstellen eines Berichts Gesamtumsatz nach Benutzerregistrierungsdatum und Quelle.](../../assets/Revenue_by_user_registration_date_and_source.gif)

## Wiederholungsaufträge nach Benutzerquelle {#repeatordersbysource}

Der Bericht „Durchschnittlicher Bestellwert“ zeigt im Durchschnitt an, wie viele Benutzer bei der Bestellung von einer bestimmten Quelle bezogen haben. In diesem Bericht wird jedoch nicht angezeigt, ob es sich bei denselben Benutzern um Bestandskunden handelt. Mit den Wiederholungsaufträgen nach Benutzerquellen können Sie jedoch sehen, ob Benutzer aus einer bestimmten Quelle mehr oder weniger Wiederholungskäufe tätigen.

Um diesen Bericht im Report Builder [&#128279;](../../tutorials/using-visual-report-builder.md) zu erstellen, fügen Sie die Metrik **Anzahl der Bestellungen** hinzu und führen Sie dann folgende Schritte aus:

1. Legen Sie die [!UICONTROL Time Period] auf den Registrierungszeitraum fest, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Time Interval] auf monatlich fest.
1. Fügen Sie eine [!UICONTROL filter] hinzu, sodass nur Benutzer mit Wiederholungsaufträgen einbezogen werden:

   Bestellnummer des Benutzers größer als 1

1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Diagrammtyp `stacked columns` verwendet.

Im Folgenden finden Sie eine visuelle Anleitung:

![Erstellen eines Berichts zu Wiederholungsaufträgen nach Benutzerquelle.](../../assets/Repeat_orders_by_user_source.gif)


## Verpackung {#wrapup}

Dieses Thema hat nur einige Analysen angesprochen, mit denen Sie den Wert Ihrer Akquise- und Marketing-Kanäle analysieren können, aber dies ist nur die Spitze des Eisbergs.

## verwandt {#related}

* [Verweisquelle für Tracking-Reihenfolge über [!DNL Google ECommerce]](../importing-data/integrations/google-ecommerce.md)
* [Verbinden Ihres [!DNL Google Adwords] Kontos](../importing-data/integrations/google-adwords.md)
* [ [!DNL Google ECommerce]  mit Bestellungen und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
* [Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
