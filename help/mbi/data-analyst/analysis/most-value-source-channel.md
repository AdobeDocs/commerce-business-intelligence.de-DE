---
title: Identifizieren Ihrer wertvollsten Marketing-Quellen und -Kanäle
description: Erfahren Sie mehr über einige Berichte, mit denen Sie Ihre wertvollsten Marketing-Kanäle entdecken können.
exl-id: 8d25bc80-ea60-47db-b01b-04a23a24c14d
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---

# Erfolgreiche Marketing-Quellen identifizieren

Sie haben Ihre Zielgruppe recherchiert, Ihre Kampagne erstellt, in einige Marketing-Kanäle investiert. Wie funktionieren diese Kanäle jetzt, da einige Zeit vergangen ist? Welcher Kanal hat die meisten neuen Benutzer eingebracht? Welche Quelle hat am meisten zu Ihrem Gesamtumsatz beigetragen?

Mit [!DNL Adobe Commerce Intelligence] können Sie Ihren Umsatz und Ihre Benutzer ganz einfach nach Verweisquelle segmentieren, unabhängig davon, ob dies [!DNL [Google Analytics' UTM fields]](https://support.google.com/analytics/answer/1191184?hl=en) oder benutzerdefinierten Datenfeldern entspricht. Mit dieser Segmentierung können Sie Ihre leistungsstärksten Kanäle finden und Ihr Marketing-Budget besser investieren.

In diesem Thema werden einige Berichte untersucht, mit denen Sie Ihre wertvollsten Marketing-Kanäle ermitteln können:

* [Neue Benutzer nach Quellen](#newusersbysource)
* [Durchschnittlicher Umsatz während der Lebensdauer nach Benutzerquelle](#avglifetimerev)
* [Durchschnittlicher Bestellwert nach Benutzerquelle](#avgorderval)
* [Umsatz nach Datum der Benutzerregistrierung und Quellen](#revbyregdateandsource)
* [Wiederholen von Bestellungen nach Benutzerquelle](#repeatordersbysource)

## Voraussetzungen {#prereqs}

Um die Analysen in diesem Thema zu erstellen, benötigen Sie Zugriff auf Marketing-Akquise-/Verweisquelldaten. Wenn Sie es noch nicht verfolgen, müssen Sie [Verweisquelldaten von  [!DNL Google ECommerce]](../importing-data/integrations/google-ecommerce.md) bestellen in [!DNL Adobe Commerce Intelligence] laden, bevor Sie fortfahren können. Durch das Hinzufügen von Benutzergeräteinformationen zu Ihren Analysen können Sie außerdem sehen, welche Technologie Ihre Verweise verwenden.

## Neue Benutzer nach Quelle {#newusersbysource}

Die Bewertung der Leistung von Verweisquellen ist entscheidend, um Ihre wertvollsten Kanäle zu ermitteln. Dieser Bericht zeigt die Anzahl der neu registrierten Benutzer nach Akquisequelle im Zeitverlauf an, sodass Sie die Leistung der Verweisquellen bei der Akquise neuer registrierter Benutzer verfolgen können.

Um diesen Bericht im [Report Builder](../../tutorials/using-visual-report-builder.md) zu erstellen, fügen Sie die Metrik **Neue Benutzer** (oder eine äquivalente Metrik, die die Anzahl neuer Benutzer im Zeitverlauf zählt) zum Bericht hinzu. Gehen Sie dann wie folgt vor:

1. Setzen Sie &quot;[!UICONTROL Time Period]&quot;auf den Registrierungszeitraum, den Sie analysieren möchten.
1. Stellen Sie die [!UICONTROL Interval] auf monatlich ein.
1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird `stacked columns` [!UICONTROL chart type] verwendet.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen neuer Benutzer nach Quellbericht](../../assets/New_Users_by_source.gif)

## Durchschnittlicher Umsatz während der Lebensdauer nach Benutzerquelle {#avglifetimerev}

Es ist wichtig, die Kanäle zu finden, die neue Benutzer einbringen, aber wie wertvoll sind diese Verweise insgesamt? Dieser Bericht zeigt den durchschnittlichen Umsatz von Benutzern aus bestimmten Akquise-Quellen über die gesamte Lebensdauer. Mit anderen Worten, Sie können damit sehen, ob Benutzer, die aus einer bestimmten Quelle erworben wurden, über ihre Lebensdauer mehr mit Ihnen verbringen als eine Gruppe von Benutzern, die aus einer anderen Quelle erworben wurden.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie dem Bericht die Metrik **Durchschnittlicher Umsatz während der Lebensdauer** hinzu. Gehen Sie dann wie folgt vor:

1. Setzen Sie &quot;[!UICONTROL Time Period]&quot;auf den Zeitraum, den Sie analysieren möchten.
1. Stellen Sie die [!UICONTROL Interval] auf monatlich ein.
   [!UICONTROL Group By] , um die Akquise- (oder Verweisquelle) anzugeben und die Quellen auszuwählen, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Typ `line chart` verwendet.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines durchschnittlichen Umsatzes während der Lebensdauer nach Benutzerquelle](../../assets/Lifetime_revenue_by_user_source.gif).

In diesem Beispiel wird nur der Umsatz während der Lebensdauer untersucht. Sie können diese Analyse jedoch auch replizieren, um die [!UICONTROL Number of orders] oder [!UICONTROL Distinct buyers] nach Verweisquelle zu betrachten.

## Durchschnittlicher Bestellwert nach Benutzerquelle {#avgorderval}

Um eine bessere Vorstellung davon zu erhalten, wie viel Geld Benutzer aus einer bestimmten Akquise-Quelle ausgeben, können Sie einen Bericht erstellen, der sich auf ihren durchschnittlichen Bestellwert bezieht. Auf diese Weise können Sie verfolgen, ob Benutzer, die aus einer bestimmten Quelle erworben wurden, mehr pro Bestellung ausgeben als Benutzer aus einer anderen Quelle.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die Metrik **Durchschnittlicher Bestellwert** hinzu und führen Sie dann die folgenden Schritte aus:

1. Setzen Sie &quot;[!UICONTROL Time Period]&quot;auf den Registrierungszeitraum, den Sie analysieren möchten.
1. Stellen Sie die [!UICONTROL Time Interval] auf monatlich ein.
1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Diagrammtyp **gestapelte Spalten** verwendet.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines durchschnittlichen Bestellwerts nach Benutzerquellenbericht.](../../assets/Average_order_value_by_source.gif)

## Gesamtumsatz nach Datum der Benutzerregistrierung und Quelle {#revbyregdateandsource}

Mit der zuvor behandelten Analyse des Lebensdauerumsatzes können Sie den durchschnittlichen Umsatz von Benutzern aus verschiedenen Quellen anzeigen, aber was ist mit dem Gesamtumsatz während der Lebensdauer? Mit diesem Bericht können Sie ermitteln, wie viel Gesamtumsatz Benutzer generieren, die sich während eines bestimmten Zeitraums und aus einer bestimmten Quelle registriert haben.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die Metrik `Revenue by user registration date` hinzu. Wenn Sie diese Metrik noch nicht [ erstellt haben, können Sie dies tun, indem Sie die Metrik `Revenue` replizieren und die Metrik `time stamp` in `creation date` des Benutzers ändern. ](../../data-user/reports/ess-manage-data-metrics.md) Gehen Sie nach dem Hinzufügen der Metrik wie folgt vor:

1. Setzen Sie &quot;[!UICONTROL Time Period]&quot;auf den Registrierungszeitraum, den Sie analysieren möchten.
1. Stellen Sie die [!UICONTROL Time Interval] auf monatlich ein.
1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Diagrammtyp `stacked columns` verwendet.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines Gesamtumsatzes nach Registrierungsdatum und Quellbericht des Benutzers.](../../assets/Revenue_by_user_registration_date_and_source.gif)

## Wiederholen von Bestellungen nach Benutzerquelle {#repeatordersbysource}

Der Bericht zum durchschnittlichen Bestellwert zeigt Ihnen im Durchschnitt, wie viele Benutzer bei der Bestellung von einer bestimmten Quelle bezogen wurden. Dieser Bericht zeigt Ihnen jedoch nicht, ob dieselben Benutzer wiederholte Kunden sind. Mit den Quellen zum Wiederholen von Bestellungen durch Benutzer können Sie jedoch feststellen, ob Benutzer aus einer bestimmten Quelle mehr oder weniger Käufe wiederholen.

Um diesen Bericht im [Report Builder](../../tutorials/using-visual-report-builder.md) zu erstellen, fügen Sie die Metrik **Anzahl Bestellungen** hinzu und führen Sie dann die folgenden Schritte aus:

1. Setzen Sie &quot;[!UICONTROL Time Period]&quot;auf den Registrierungszeitraum, den Sie analysieren möchten.
1. Stellen Sie die [!UICONTROL Time Interval] auf monatlich ein.
1. Fügen Sie einen [!UICONTROL filter] hinzu, damit nur Benutzer mit Wiederholungsbestellungen einbezogen werden:

   Bestellnummer des Benutzers größer als 1

1. Setzen Sie [!UICONTROL Group By] auf die Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird der Diagrammtyp `stacked columns` verwendet.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen von Wiederholungsbestellungen nach Benutzerquellenbericht.](../../assets/Repeat_orders_by_user_source.gif)


## Aufwischen {#wrapup}

In diesem Thema wurden nur einige Analysen behandelt, mit denen Sie den Wert Ihrer Akquise- und Marketingkanäle analysieren können, aber dies ist nur die Spitze des Eisbergs.

## Verwandte {#related}

* [Verweisquelle der Bestellung über [!DNL Google ECommerce] verfolgen](../importing-data/integrations/google-ecommerce.md)
* [ [!DNL Google Adwords] Konto verbinden](../importing-data/integrations/google-adwords.md)
* [Erstellen von [!DNL Google ECommerce] Dimensionen mit Bestellungen und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
* [Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
