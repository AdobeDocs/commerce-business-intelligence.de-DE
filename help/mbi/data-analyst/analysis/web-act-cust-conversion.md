---
title: Analyse der Website-Aktivität und der Kundenkonversionsraten
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Website-Aktivität - einschließlich Seitenansichten, Sitzungen und Benutzern - sowie Ihre Kundenkonversionsrate im Laufe der Zeit verfolgt.
exl-id: 2b57d5b3-3bbf-4ec9-86a6-9fa850c1c459
role: Admin, User
feature: Reports, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# Analyse der Website-Aktivität

[!DNL Adobe Commerce Intelligence] ermöglicht Ihnen die einfache Integration Ihrer Daten zu Werbekosten mit den übrigen Daten. Dadurch können Sie nicht nur die Aktivität Ihrer Website verstehen, sondern auch den Prozentsatz der Besucher Ihrer Website ableiten, die zu einem registrierten Benutzer werden oder einen Kauf tätigen.

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Ihre Website-Aktivität - einschließlich Seitenansichten, Sitzungen und Benutzern - sowie Ihre Kundenkonversionsrate im Zeitverlauf verfolgt.

## Voraussetzungen

**Importieren von Daten zu Werbekosten** - Verbinden [!DNL [Google AdWords]](../importing-data/integrations/google-adwords.md) nach [!DNL Adobe Commerce Intelligence] - die automatisch Ihre [!DNL AdWords] Ausgaben für Commerce Intelligence.

**Tracking der Benutzerakquisekanaldaten** - So binden Sie Ihre [!DNL Google AdWords] Daten für bestimmte Bestellungen in Ihrer Datenbank, müssen Sie [Benutzerakquise verfolgen](../analysis/google-track-user-acq.md) via [!DNL Google Analytics E-commerce]. Dadurch können Sie jede Bestellung mit einer UTM-Quelle und einem Medium verbinden.

## Benutzerakquise-Kampagnen

Diese Berichtserstellung basiert auf Folgendem:

* Metriken, die automatisch generiert werden, wenn Sie Ihre [!DNL Google AdWords] data
* Grundlegende Metriken, die bereits für Ihr Konto verfügbar sein sollten, z. B. `Number of orders` und `New users`
* Dimensionen, die beim Beitritt zu Ihrer [!DNL Google Analytics Ecommerce] Daten in Ihre Datenbank, wie z. B. die utm-Quelle der Bestellung und das utm-Medium der Bestellung. Wenden Sie sich an das Supportteam, wenn diese Felder derzeit nicht in Ihrem Konto verfügbar sind.

## Berichte erstellen

**Erstellen Sie zunächst einen Bericht, der die Anzahl der Seitenansichten, Sitzungen und Benutzer im Zeitverlauf anzeigt:**

1. Erstellen Sie einen Bericht.
1. Klicks **[!UICONTROL Add Metric]**, dann mit der Maus über [!DNL Google Analytics] im unteren Bereich des Dropdown-Menüs und wählen Sie `Page Views`.
1. Fügen Sie eine weitere Metrik hinzu und bewegen Sie den Mauszeiger erneut über die [!DNL Google Analytics] dieses Mal `Sessions`.
1. Fügen Sie eine dritte Metrik hinzu und bewegen Sie den Mauszeiger erneut über die [!DNL Google Analytics] dieses Mal `Users`.
1. Ändern Sie jetzt Ihren Zeitraum in einen sich bewegenden Bereich von vor 31 Tagen auf vor 1 Tag und passen Sie das Zeitintervall an `by day`.
1. Geben Sie Ihrem Bericht einen Namen (z. B. `Page views, sessions and users by day`) und klicken Sie auf **[!UICONTROL Save]**.

**Der zweite Bericht untersucht die Anzahl der Seitenansichten im vergangenen Jahr:**

1. Erstellen Sie einen Bericht.
1. Klicks **[!UICONTROL Add Metric]**, bewegen Sie die Maus über [!DNL Google Analytics] im unteren Bereich des Dropdown-Menüs und wählen Sie _Seitenansichten_.
1. Ändern Sie Ihren Zeitraum von vor 13 Monaten in einen sich bewegenden Bereich und passen Sie das Zeitintervall an auf `by month`.
1. Benennen Sie den Bericht, z. B. `Page views by month,` und klicken **[!UICONTROL Save]**.

**Die dritte Grafik zeigt die Absprungrate des vergangenen Jahres:**

1. Erstellen Sie einen Bericht.
1. Klicks **[!UICONTROL Add Metric]**, bewegen Sie die Maus über [!DNL Google Analytics] im unteren Bereich des Dropdown-Menüs und wählen Sie _Absprungrate_.
1. Ändern Sie Ihren Zeitraum von vor 13 Monaten in einen sich bewegenden Bereich und passen Sie das Zeitintervall an auf `by month`.
1. Benennen Sie den Bericht, z. B. `Bounce rate by month`und Klicken **[!UICONTROL Save]**.

**Betrachten Sie nun die durchschnittliche Sitzungslänge neuer Besucher im Vergleich zu wiederkehrenden Besuchern:**

1. Erstellen Sie einen Bericht.
1. Klicks **UICONTROL Metrik hinzufügen**, bewegen Sie die Maus über [!DNL Google Analytics] im unteren Bereich des Dropdown-Menüs und wählen Sie `Average Session Length`.
1. Ändern Sie Ihren Zeitraum von vor 13 Monaten in einen sich bewegenden Bereich und passen Sie das Zeitintervall an auf `by month`?
1. Hinzufügen einer `Group by` und wählen `New or returning visitor`.  Überprüfen Sie die `Show All` und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Benennen Sie den Bericht, z. B. `Average session length`und Klicken **[!UICONTROL Save]**.

**Sehen Sie sich als Nächstes Ihre wichtigsten Referrer-Domänen aus den letzten 30 Tagen an:**

1. Erstellen Sie einen Bericht.
1. Klicks **[!UICONTROL Add Metric]**, bewegen Sie die Maus über [!DNL Google Analytics] im unteren Bereich des Dropdown-Menüs und wählen Sie `Sessions`.
1. Ändern Sie Ihren Zeitraum von vor 31 Tagen in einen sich bewegenden Bereich und passen Sie das Zeitintervall an `none`.
1. Hinzufügen einer `Group by` und wählen `ga:source`.  Überprüfen Sie die _Alle anzeigen_ und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Weitere hinzufügen `group by` und wählen `ga:medium`. Überprüfen Sie erneut die `Show All` und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Benennen Sie den Bericht, z. B. `Top 20 Referring Domains, 30 Days`und klicken Sie auf **[!UICONTROL Save]**.

**Sehen Sie sich schließlich die Konversion an:**

1. Erstellen Sie einen Bericht.
1. Fügen Sie die folgenden Metriken hinzu:

* `New users`
   * Klicks **[!UICONTROL Hide]** unterhalb des Metriknamens

* `Number of orders`
   * Filter hinzufügen für `Customer's order number` = 1 und klicken Sie **[!UICONTROL Apply]**
   * Benennen Sie die Metrik um, indem Sie auf den Metriknamen klicken und sie aufrufen. `Number of first orders`Klicken Sie auf **[!UICONTROL Hide]**

* `Number of orders`
   * **[!UICONTROL Hide]** die Metrik

* `Users`
   * **[!UICONTROL Hide]** die Metrik
   * Ändern Sie den Zeitraum in `24 months ago to now`und passen Sie das Zeitintervall an `by month`.
   * Fügen Sie die folgenden Formeln hinzu, indem Sie auf **[!UICONTROL Formula]**.
   * Klicken Sie auf A/D und dann auf **[!UICONTROL Apply]**
   * Formel umbenennen `Registration conversion`
   * B/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Formel umbenennen `First order conversion`
   * C/D und klicken Sie auf **[!UICONTROL Apply]**
   * Formel umbenennen `Any order conversion`

* Benennen Sie nun Ihren Bericht, z. B. `Conversion by month`und klicken Sie anschließend auf **[!UICONTROL Save]**.

## Nächste Schritte

Nachdem Sie nun Zugriff auf Daten zu Ihrem Web-Traffic und Ihren Konversionsraten haben, können Sie damit beginnen, Geschäftsentscheidungen zu fördern, z. B. Welche Sites am besten geeignet sind, Traffic zu Ihrer Site zu leiten? Oder welche Ihrer Kampagnen am effektivsten sind, um Kunden mit dem hohen Lebenszeitwert zu gewinnen?

Bei der Anpassung der Werbeausgaben und der Marketingstrategie können Sie die Ergebnisse in [!DNL Commerce Intelligence], die auf diesem Dashboard zur Erfüllung der sich entwickelnden Prioritäten Ihres Unternehmens verwendet wird.
