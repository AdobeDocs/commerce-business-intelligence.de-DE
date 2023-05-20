---
title: Identifizieren Ihrer wertvollsten Marketing-Quellen und -Kanäle
description: Erfahren Sie mehr über einige Berichte, mit denen Sie Ihre wertvollsten Marketing-Kanäle entdecken können.
exl-id: 8d25bc80-ea60-47db-b01b-04a23a24c14d
source-git-commit: 4cad1e05502630e13f7a2d341f263140a02b3d82
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# Erfolgreiche Marketing-Quellen identifizieren

Sie haben Ihre Zielgruppe recherchiert, Ihre Kampagne erstellt, in einige Marketing-Kanäle investiert. Wie funktionieren diese Kanäle jetzt, da einige Zeit vergangen ist? Welcher Kanal hat die meisten neuen Benutzer eingebracht? Welche Quelle hat am meisten zu Ihrem Gesamtumsatz beigetragen?

Mit [!DNL Adobe Commerce Intelligence]können Sie Ihre Umsätze und Benutzer einfach nach der Verweisquelle segmentieren, ob sie [!DNL [Google Analytics' UTM fields]](https://support.google.com/analytics/answer/1191184?hl=en) oder benutzerdefinierten Datenfeldern. Mit dieser Segmentierung können Sie Ihre leistungsstärksten Kanäle finden und Ihr Marketing-Budget besser investieren.

In diesem Thema werden einige Berichte untersucht, mit denen Sie Ihre wertvollsten Marketing-Kanäle ermitteln können:

* [Neue Benutzer nach Quellen](#newusersbysource)
* [Durchschnittlicher Umsatz während der Lebensdauer nach Benutzerquelle](#avglifetimerev)
* [Durchschnittlicher Bestellwert nach Benutzerquelle](#avgorderval)
* [Umsatz nach Datum der Benutzerregistrierung und Quellen](#revbyregdateandsource)
* [Wiederholen von Bestellungen nach Benutzerquelle](#repeatordersbysource)

## Voraussetzungen {#prereqs}

Um die Analysen in diesem Thema zu erstellen, benötigen Sie Zugriff auf Marketing-Akquise-/Verweisquelldaten. Wenn Sie es noch nicht verfolgen, müssen Sie [Bestellreferenz-Quelldaten aus [!DNL Google ECommerce]](../importing-data/integrations/google-ecommerce.md) in [!DNL Adobe Commerce Intelligence] bevor Sie fortfahren können. Durch das Hinzufügen von Benutzergeräteinformationen zu Ihren Analysen können Sie außerdem sehen, welche Technologie Ihre Referenzen verwenden.

## Neue Benutzer nach Quelle {#newusersbysource}

Die Bewertung der Leistung von Verweisquellen ist entscheidend, um Ihre wertvollsten Kanäle zu ermitteln. Dieser Bericht zeigt die Anzahl der neu registrierten Benutzer nach Akquisequelle im Zeitverlauf an, sodass Sie die Leistung der Verweisquellen beim Erwerb neuer registrierter Benutzer verfolgen können.

So erstellen Sie diesen Bericht im [Report Builder](../../tutorials/using-visual-report-builder.md), fügen Sie die **Neue Benutzer** Metrik (oder eine äquivalente Metrik, die die Anzahl neuer Benutzer im Zeitverlauf zählt) zum Bericht hinzu. Gehen Sie dann wie folgt vor:

1. Legen Sie die [!UICONTROL Time Period] in den Registrierungszeitraum, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Interval] auf monatlich.
1. Satz [!UICONTROL Group By] zur Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird die `stacked columns` [!UICONTROL chart type].

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines Berichts &quot;Neue Benutzer nach Quelle&quot;.](../../assets/New_Users_by_source.gif)

## Durchschnittlicher Umsatz während der Lebensdauer nach Benutzerquelle {#avglifetimerev}

Es ist wichtig, die Kanäle zu finden, die neue Benutzer einbringen, aber wie wertvoll sind diese Verweise insgesamt? Dieser Bericht zeigt den durchschnittlichen Umsatz von Benutzern aus bestimmten Akquise-Quellen über die gesamte Lebensdauer. Mit anderen Worten, Sie können damit sehen, ob Benutzer, die aus einer bestimmten Quelle erworben wurden, über ihre Lebensdauer mehr mit Ihnen verbringen als eine Gruppe von Benutzern, die aus einer anderen Quelle erworben wurden.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die **Durchschnittlicher Umsatz während der Lebensdauer** zum Bericht hinzu. Gehen Sie dann wie folgt vor:

1. Legen Sie die [!UICONTROL Time Period] auf den Zeitraum, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Interval] auf monatlich.
   [!UICONTROL Group By] zur Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird die `line chart` Typ.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen des durchschnittlichen Lebenszeitumsatzes nach Benutzerquelle](../../assets/Lifetime_revenue_by_user_source.gif).

In diesem Beispiel wird nur der Umsatz während der Lebensdauer untersucht. Sie können diese Analyse jedoch auch replizieren, um die [!UICONTROL Number of orders] oder [!UICONTROL Distinct buyers] durch die Verweisquelle.

## Durchschnittlicher Bestellwert nach Benutzerquelle {#avgorderval}

Um eine bessere Vorstellung davon zu erhalten, wie viel Geld Benutzer aus einer bestimmten Akquise-Quelle ausgeben, können Sie einen Bericht erstellen, der sich auf ihren durchschnittlichen Bestellwert bezieht. Auf diese Weise können Sie verfolgen, ob Benutzer, die aus einer bestimmten Quelle erworben wurden, mehr pro Bestellung ausgeben als Benutzer aus einer anderen Quelle.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die **Durchschnittlicher Bestellwert** Metrik und führen Sie dann die folgenden Schritte aus:

1. Legen Sie die [!UICONTROL Time Period] in den Registrierungszeitraum, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Time Interval] auf monatlich.
1. Satz [!UICONTROL Group By] zur Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird die **gestapelte Spalten** Diagrammtyp.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines durchschnittlichen Bestellwerts nach Benutzerquellenbericht](../../assets/Average_order_value_by_source.gif)

## Gesamtumsatz nach Datum der Benutzerregistrierung und Quelle {#revbyregdateandsource}

Mit der zuvor behandelten Analyse des Lebensdauerumsatzes können Sie den durchschnittlichen Umsatz von Benutzern aus verschiedenen Quellen anzeigen, aber was ist mit dem Gesamtumsatz während der Lebensdauer? Mit diesem Bericht können Sie ermitteln, wie viel Gesamtumsatz Benutzer generieren, die sich während eines bestimmten Zeitraums und aus einer bestimmten Quelle registriert haben.

Um diesen Bericht im Report Builder zu erstellen, fügen Sie die `Revenue by user registration date` Metrik. Wenn Sie [diese Metrik erstellt hat](../../data-user/reports/ess-manage-data-metrics.md) Sie können dies bereits tun, indem Sie die `Revenue` Metrik und ändern Sie die `time stamp` auf `creation date`. Gehen Sie nach dem Hinzufügen der Metrik wie folgt vor:

1. Legen Sie die [!UICONTROL Time Period] in den Registrierungszeitraum, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Time Interval] auf monatlich.
1. Satz [!UICONTROL Group By] zur Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird die `stacked columns` Diagrammtyp.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines Gesamtumsatzes nach Benutzerregistrierungsdatum und Quellbericht](../../assets/Revenue_by_user_registration_date_and_source.gif)

## Wiederholen von Bestellungen nach Benutzerquelle {#repeatordersbysource}

Der Bericht zum durchschnittlichen Bestellwert zeigt Ihnen im Durchschnitt, wie viele Benutzer bei der Bestellung von einer bestimmten Quelle bezogen wurden. Dieser Bericht zeigt Ihnen jedoch nicht, ob dieselben Benutzer wiederholte Kunden sind. Mit den Quellen zum Wiederholen von Bestellungen durch Benutzer können Sie jedoch feststellen, ob Benutzer aus einer bestimmten Quelle mehr oder weniger Käufe wiederholen.

So erstellen Sie diesen Bericht im [Report Builder](../../tutorials/using-visual-report-builder.md), fügen Sie die **Anzahl Bestellungen** Metrik und führen Sie dann die folgenden Schritte aus:

1. Legen Sie die [!UICONTROL Time Period] in den Registrierungszeitraum, den Sie analysieren möchten.
1. Legen Sie die [!UICONTROL Time Interval] auf monatlich.
1. Hinzufügen einer [!UICONTROL filter] sodass nur Benutzer mit Wiederholungsbestellungen einbezogen werden:

   Bestellnummer des Benutzers größer als 1

1. Satz [!UICONTROL Group By] zur Akquise- (oder Verweisquelle) und wählen Sie die Quellen aus, die Sie einbeziehen möchten.
1. In diesem Beispiel wird die `stacked columns` Diagrammtyp.

Im Folgenden finden Sie eine visuelle exemplarische Vorgehensweise:

![Erstellen eines Berichts zur Wiederholung von Bestellungen nach Benutzerquellen .](../../assets/Repeat_orders_by_user_source.gif)


## Aufbrechen {#wrapup}

In diesem Thema wurden nur einige Analysen behandelt, mit denen Sie den Wert Ihrer Akquise- und Marketingkanäle analysieren können, aber dies ist nur die Spitze des Eisbergs.

## Verwandte {#related}

* [Verweisquelle für Tracking von Bestellungen über [!DNL Google ECommerce]](../importing-data/integrations/google-ecommerce.md)
* [Verbinden Ihrer [!DNL Google Adwords] account](../importing-data/integrations/google-adwords.md)
* [Erstellen [!DNL Google ECommerce] Dimensionen mit Bestellungen und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
* [Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
