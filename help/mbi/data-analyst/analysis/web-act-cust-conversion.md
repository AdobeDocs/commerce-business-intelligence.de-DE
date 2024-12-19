---
title: Analyse der Website-Aktivität und der Konversionsraten der Kunden
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Website-Aktivität - einschließlich Seitenansichten, Sitzungen und Benutzern - und Ihre Kundenkonversionsrate im Laufe der Zeit verfolgt.
exl-id: 2b57d5b3-3bbf-4ec9-86a6-9fa850c1c459
role: Admin, User
feature: Reports, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Analysieren der Website-Aktivität

[!DNL Adobe Commerce Intelligence] können Sie Ihre Werbungskostendaten einfach mit den übrigen Daten integrieren. Auf diese Weise können Sie nicht nur Ihre Website-Aktivität verstehen, sondern auch den Prozentsatz der Besucher auf Ihrer Website ableiten, die ein registrierter Benutzer werden oder einen Kauf tätigen.

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Ihre Website-Aktivität - einschließlich Seitenansichten, Sitzungen und Benutzern - und Ihre Kundenkonversionsrate im Laufe der Zeit verfolgt.

## Voraussetzungen

**Importieren Sie Ihre Werbungskostendaten** - Verbinden Sie [!DNL [Google AdWords]](../importing-data/integrations/google-adwords.md) mit [!DNL Adobe Commerce Intelligence] - Dadurch werden Ihre [!DNL AdWords] in Commerce Intelligence automatisch synchronisiert.

**Benutzerakquise-Kanaldaten verfolgen** - Um Ihre [!DNL Google AdWords] mit bestimmten Bestellungen in Ihrer Datenbank zu verknüpfen, müssen Sie [Benutzerakquise verfolgen](../analysis/google-track-user-acq.md) über [!DNL Google Analytics E-commerce]. Auf diese Weise können Sie jede Bestellung mit einer UTM-Quelle und einem Medium verbinden.

## Kampagnen zur Benutzerakquise

Diese Sammlung von Berichten basiert auf Folgendem:

* Metriken, die beim Verbinden Ihrer [!DNL Google AdWords] automatisch generiert werden
* Grundlegende Metriken, die bereits in Ihrem Konto verfügbar sein sollten, z. B. `Number of orders` und `New users`
* Dimensionen, die beim Verbinden Ihrer [!DNL Google Analytics Ecommerce]-Daten mit Ihrer Datenbank erstellt werden, z. B. die UTM-Quelle der Bestellung und das UTM-Medium der Bestellung. Wenden Sie sich an das Support-Team , wenn diese Felder in Ihrem Konto derzeit nicht verfügbar sind

## Erstellen von Berichten

**Erstellen Sie zunächst einen Bericht, der die Anzahl der Seitenansichten, Sitzungen und Benutzer im Zeitverlauf anzeigt:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **[!UICONTROL Add Metric]**, bewegen Sie dann den Mauszeiger über den [!DNL Google Analytics] unten in der Dropdown-Liste und wählen Sie `Page Views` aus.
1. Fügen Sie eine weitere Metrik hinzu, indem Sie erneut den Mauszeiger über den [!DNL Google Analytics] Abschnitt bewegen und dieses Mal `Sessions` auswählen.
1. Fügen Sie eine dritte Metrik hinzu, indem Sie erneut den Mauszeiger über den [!DNL Google Analytics] Abschnitt bewegen und diesmal `Users` auswählen.
1. Ändern Sie nun Ihren Zeitraum in einen beweglichen Bereich von vor 31 Tagen bis vor 1 Tag und passen Sie das Zeitintervall auf `by day` an.
1. Geben Sie Ihrem Bericht einen Namen (z. B. `Page views, sessions and users by day`) und klicken Sie auf **[!UICONTROL Save]**.

**Der zweite Bericht untersucht die Anzahl der Seitenaufrufe im letzten Jahr:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **[!UICONTROL Add Metric]**, bewegen Sie den Mauszeiger über den [!DNL Google Analytics] unten in der Dropdown-Liste und wählen Sie _Seitenansichten_.
1. Ändern Sie Ihren Zeitraum in einen beweglichen Bereich von vor 13 Monaten bis vor 1 Monat und passen Sie das Zeitintervall auf `by month` an.
1. Geben Sie Ihrem Bericht einen Namen, z. B. `Page views by month,` und Click **[!UICONTROL Save]**.

**Das dritte Diagramm zeigt die Absprungrate im letzten Jahr:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **[!UICONTROL Add Metric]**, bewegen Sie den Mauszeiger über den [!DNL Google Analytics] unten im Dropdown-Menü und wählen Sie _Absprungrate_.
1. Ändern Sie Ihren Zeitraum in einen beweglichen Bereich von vor 13 Monaten bis vor 1 Monat und passen Sie das Zeitintervall auf `by month` an.
1. Geben Sie Ihrem Bericht einen Namen wie `Bounce rate by month` und klicken Sie auf **[!UICONTROL Save]**.

**Betrachten Sie nun die durchschnittliche Sitzungsdauer bei neuen Besuchern im Vergleich zu wiederkehrenden Besuchern:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie **UICONTROL Metrik hinzufügen**, bewegen Sie den Mauszeiger über den [!DNL Google Analytics] am unteren Rand des Dropdown-Menüs und wählen Sie `Average Session Length` aus.
1. Ändern Sie Ihren Zeitraum in einen beweglichen Bereich von vor 13 Monaten bis vor 1 Monat und passen Sie das Zeitintervall auf `by month` an?
1. Fügen Sie eine `Group by` hinzu und wählen Sie `New or returning visitor` aus.  Aktivieren Sie das `Show All` und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Geben Sie Ihrem Bericht einen Namen wie `Average session length` und klicken Sie auf **[!UICONTROL Save]**.

**Sehen Sie sich als Nächstes Ihre am häufigsten verweisenden Domains in den letzten 30 Tagen an:**

1. Erstellen Sie einen Bericht.
1. Klicken Sie auf **[!UICONTROL Add Metric]**, bewegen Sie den Mauszeiger über den [!DNL Google Analytics] unten im Dropdown-Menü und wählen Sie `Sessions` aus.
1. Ändern Sie Ihren Zeitraum in einen beweglichen Bereich von vor 31 Tagen bis vor einem Tag und passen Sie das Zeitintervall auf `none` an.
1. Fügen Sie eine `Group by` hinzu und wählen Sie `ga:source` aus.  Markieren Sie das _Alle anzeigen_ und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Fügen Sie eine weitere `group by` hinzu und wählen Sie `ga:medium` aus. Aktivieren Sie erneut das Kontrollkästchen `Show All` und klicken Sie dann auf **[!UICONTROL Apply]**.
1. Geben Sie Ihrem Bericht einen Namen wie `Top 20 Referring Domains, 30 Days` und klicken Sie auf **[!UICONTROL Save]**.

**Sehen Sie sich abschließend die Konversion an:**

1. Erstellen Sie einen Bericht.
1. Fügen Sie die folgenden Metriken hinzu:

* `New users`
   * Klicken Sie unter dem Metriknamen auf **[!UICONTROL Hide]** .

* `Number of orders`
   * Fügen Sie einen Filter für `Customer's order number` = 1 hinzu und klicken Sie **[!UICONTROL Apply]**
   * Benennen Sie die Metrik um, indem Sie auf den Namen der Metrik klicken, sie `Number of first orders` aufrufen und dann auf **[!UICONTROL Hide]** klicken

* `Number of orders`
   * Metrik **[!UICONTROL Hide]**

* `Users`
   * Metrik **[!UICONTROL Hide]**
   * Ändern Sie den Zeitraum in `24 months ago to now` und passen Sie das Zeitintervall auf `by month` an.
   * Fügen Sie die folgenden Formeln hinzu, indem Sie auf **[!UICONTROL Formula]** klicken.
   * A/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Formel `Registration conversion` umbenennen
   * B/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Formel `First order conversion` umbenennen
   * C/D und klicken Sie dann auf **[!UICONTROL Apply]**
   * Formel `Any order conversion` umbenennen

* Geben Sie Ihrem Bericht nun einen Namen wie `Conversion by month` und klicken Sie dann auf **[!UICONTROL Save]**.

## Nächste Schritte

Nachdem Sie nun Zugriff auf Daten zu Ihrem Web-Traffic und Ihren Konversionsraten haben, können Sie damit beginnen, dies zu untersuchen, um Geschäftsentscheidungen zu fördern, z. B. Welche Sites eignen sich am besten, um Traffic auf Ihre Site zu lenken? Oder welche Ihrer Kampagnen sind am effektivsten bei der Akquise von Kunden mit dem hohen Lifetime Value?

Wenn Sie die Ausgaben für Anzeigen und die Marketing-Strategie anpassen, können Sie die Ergebnisse in [!DNL Commerce Intelligence] verfolgen und auf diesem Dashboard iterieren, um die sich entwickelnden Prioritäten Ihres Unternehmens zu erfüllen.
