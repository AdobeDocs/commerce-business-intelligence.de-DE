---
title: Analyse der Website-Aktivität und der Kundenkonversionsraten
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Website-Aktivität - einschließlich Seitenansichten, Sitzungen und Benutzern - sowie Ihre Kundenkonversionsrate im Laufe der Zeit verfolgt.
exl-id: 2b57d5b3-3bbf-4ec9-86a6-9fa850c1c459
role: Admin, User
feature: Reports, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Analyse der Website-Aktivität

Mit [!DNL Adobe Commerce Intelligence] können Sie Ihre Daten zu Werbekosten einfach in die übrigen Daten integrieren. Dadurch können Sie nicht nur die Aktivität Ihrer Website verstehen, sondern auch den Prozentsatz der Besucher Ihrer Website ableiten, die zu einem registrierten Benutzer werden oder einen Kauf tätigen.

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Ihre Website-Aktivität - einschließlich Seitenansichten, Sitzungen und Benutzern - sowie Ihre Kundenkonversionsrate im Zeitverlauf verfolgt.

## Voraussetzungen

**Importieren Sie Ihre Werbekostendaten** - Verbinden Sie [!DNL [Google AdWords]](../importing-data/integrations/google-adwords.md) mit [!DNL Adobe Commerce Intelligence] - Dadurch werden Ihre [!DNL AdWords] Ausgaben in Commerce Intelligence automatisch synchronisiert.

**Tracking der Benutzerakquise-Kanaldaten** - Um Ihre [!DNL Google AdWords] -Daten mit bestimmten Bestellungen in Ihrer Datenbank zu verknüpfen, müssen Sie die Benutzerakquise [über [!DNL Google Analytics E-commerce] verfolgen. ](../analysis/google-track-user-acq.md) Dadurch können Sie jede Bestellung mit einer UTM-Quelle und einem Medium verbinden.

## Benutzerakquise-Kampagnen

Diese Berichtserstellung basiert auf Folgendem:

* Metriken, die automatisch generiert werden, wenn Sie Ihre [!DNL Google AdWords] -Daten verbinden
* Grundlegende Metriken, die bereits für Ihr Konto verfügbar sein sollten, wie `Number of orders` und `New users`
* Dimensionen, die beim Verbinden Ihrer [!DNL Google Analytics Ecommerce] -Daten mit Ihrer Datenbank erstellt werden, z. B. die UTM-Quelle der Bestellung und das utm-Medium der Bestellung. Wenden Sie sich an das Supportteam, wenn diese Felder derzeit nicht in Ihrem Konto verfügbar sind.

## Berichte erstellen

**Erstellen Sie zunächst einen Bericht, der die Anzahl der Seitenansichten, Sitzungen und Benutzer im Zeitverlauf anzeigt:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **[!UICONTROL Add Metric]**, bewegen Sie den Mauszeiger über den Abschnitt [!DNL Google Analytics] unten im Dropdown-Menü und wählen Sie `Page Views` aus.
1. Fügen Sie eine weitere Metrik hinzu, bewegen Sie den Mauszeiger erneut über den Abschnitt [!DNL Google Analytics] und wählen Sie dieses Mal `Sessions` aus.
1. Fügen Sie eine dritte Metrik hinzu, bewegen Sie den Mauszeiger erneut über den Abschnitt [!DNL Google Analytics] und wählen Sie dieses Mal `Users` aus.
1. Ändern Sie jetzt Ihren Zeitraum in einen sich bewegenden Bereich von vor 31 Tagen auf vor 1 Tag und passen Sie das Zeitintervall auf `by day` an.
1. Geben Sie Ihrem Bericht einen Namen (z. B. `Page views, sessions and users by day`) und klicken Sie auf **[!UICONTROL Save]**.

**Der zweite Bericht untersucht die Anzahl der Seitenansichten im letzten Jahr:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf &quot;**[!UICONTROL Add Metric]**&quot;, bewegen Sie den Mauszeiger am unteren Rand des Dropdown-Menüs über den Abschnitt &quot;[!DNL Google Analytics]&quot; und wählen Sie &quot;_Seitenansichten_&quot;.
1. Ändern Sie Ihren Zeitraum in einen sich bewegenden Bereich von vor 13 Monaten bis vor 1 Monat und passen Sie das Zeitintervall auf `by month` an.
1. Geben Sie Ihrem Bericht einen Namen, z. B. `Page views by month,` und klicken Sie auf **[!UICONTROL Save]**.

**Das dritte Diagramm zeigt die Absprungrate des letzten Jahres:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf &quot;**[!UICONTROL Add Metric]**&quot;, bewegen Sie den Mauszeiger am unteren Rand des Dropdown-Menüs über den Abschnitt &quot;[!DNL Google Analytics]&quot; und wählen Sie &quot;_Absprungrate_&quot;.
1. Ändern Sie Ihren Zeitraum in einen sich bewegenden Bereich von vor 13 Monaten bis vor 1 Monat und passen Sie das Zeitintervall auf `by month` an.
1. Geben Sie Ihrem Bericht einen Namen, z. B. `Bounce rate by month` und klicken Sie auf **[!UICONTROL Save]**.

**Betrachten Sie nun die durchschnittliche Sitzungslänge neuer Besucher im Vergleich zu wiederkehrenden Besuchern:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **UICONTROL Metrik hinzufügen**, bewegen Sie die Maus über den Abschnitt [!DNL Google Analytics] unten im Dropdown-Menü und wählen Sie `Average Session Length` aus.
1. Ändern Sie Ihren Zeitraum in einen sich bewegenden Bereich von vor 13 Monaten bis vor 1 Monat und passen Sie das Zeitintervall auf `by month` an?
1. Fügen Sie eine `Group by` hinzu und wählen Sie `New or returning visitor` aus.  Markieren Sie das Feld `Show All` und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Geben Sie Ihrem Bericht einen Namen, z. B. `Average session length` und klicken Sie auf **[!UICONTROL Save]**.

**Als Nächstes sehen Sie sich Ihre wichtigsten verweisenden Domänen in den letzten 30 Tagen an:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **[!UICONTROL Add Metric]**, bewegen Sie den Mauszeiger über den Abschnitt [!DNL Google Analytics] unten im Dropdown-Menü und wählen Sie `Sessions` aus.
1. Ändern Sie Ihren Zeitraum in einen sich bewegenden Bereich von vor 31 Tagen auf vor 1 Tag und passen Sie das Zeitintervall auf `none` an.
1. Fügen Sie eine `Group by` hinzu und wählen Sie `ga:source` aus.  Aktivieren Sie das Feld _Alle anzeigen_ und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Fügen Sie weitere `group by` hinzu und wählen Sie `ga:medium` aus. Markieren Sie erneut das Feld `Show All` und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Geben Sie Ihrem Bericht einen Namen, z. B. `Top 20 Referring Domains, 30 Days`, und klicken Sie auf **[!UICONTROL Save]**.

**Sehen Sie sich schließlich die Konversion an:**

1. Erstellen Sie einen Bericht.
1. Fügen Sie die folgenden Metriken hinzu:

* `New users`
   * Klicken Sie unter dem Metriknamen auf **[!UICONTROL Hide]** .

* `Number of orders`
   * Fügen Sie einen Filter für `Customer's order number` = 1 hinzu und klicken Sie auf **[!UICONTROL Apply]**
   * Benennen Sie die Metrik um, indem Sie auf den Metriknamen klicken, sie `Number of first orders` aufrufen und dann auf **[!UICONTROL Hide]** klicken.

* `Number of orders`
   * **[!UICONTROL Hide]** die Metrik

* `Users`
   * **[!UICONTROL Hide]** die Metrik
   * Ändern Sie den Zeitraum in `24 months ago to now` und passen Sie das Zeitintervall auf `by month` an.
   * Fügen Sie die folgenden Formeln hinzu, indem Sie auf **[!UICONTROL Formula]** klicken.
   * A/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Umbenennen der Formel `Registration conversion`
   * B/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Umbenennen der Formel `First order conversion`
   * C/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Umbenennen der Formel `Any order conversion`

* Geben Sie Ihrem Bericht nun einen Namen, z. B. `Conversion by month`, und klicken Sie dann auf **[!UICONTROL Save]**.

## Nächste Schritte

Nachdem Sie nun Zugriff auf Daten zu Ihrem Web-Traffic und Ihren Konversionsraten haben, können Sie damit beginnen, Geschäftsentscheidungen zu fördern, z. B. Welche Sites am besten geeignet sind, Traffic zu Ihrer Site zu leiten? Oder welche Ihrer Kampagnen am effektivsten sind, um Kunden mit dem hohen Lebenszeitwert zu gewinnen?

Wenn Sie die Anzeigenausgaben und die Marketingstrategie anpassen, können Sie die Ergebnisse in [!DNL Commerce Intelligence] weiterhin verfolgen und dieses Dashboard durchlaufen, um die sich entwickelnden Prioritäten Ihres Unternehmens zu erfüllen.
