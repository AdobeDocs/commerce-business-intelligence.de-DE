---
title: Kundenabwanderung definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie die Abwanderung Ihrer Transaktionskunden definieren können.
exl-id: fea8f7e9-c84c-4d49-a657-8b75140c113a
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Abwanderung von Transaktionskunden

In diesem Artikel zeigen wir, wie Sie ein Dashboard einrichten, mit dem Sie die Abwanderung Ihrer Transaktionskunden definieren können.

![](../../assets/churn-deashboard.png)

Diese Analyse enthält [Erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Berechnete Spalten

Zu erstellende Spalten

* `customer_entity` table
* `Customer's lifetime number of orders`
* Wählen Sie eine Definition aus: `Count`
* Wählen Sie eine [!UICONTROL table]: `sales_flat_order`
* Wählen Sie eine [!UICONTROL column]: **`entity_id`**
* [!UICONTROL Path]: sales_flach_order.customer_id = customer_entity.entity_id
* [!UICONTROL Filter]:
* Bestellungen, die wir zählen

* `sales_flat_order` table
* `Customer's lifetime number of orders`
* Wählen Sie eine Definition aus: Verbundene Spalte
* Wählen Sie eine [!UICONTROL table]: `customer_entity`
* Wählen Sie eine [!UICONTROL column]: `Customer's lifetime number of orders`
* [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
* [!UICONTROL Filter]: `Orders we count`

* `Seconds since created_at`
* Wählen Sie eine Definition aus: `Age`
* Wählen Sie eine [!UICONTROL column]: `created_at`

* **`Customer's order number`** wird von einem Analytiker im Rahmen Ihrer **[CHURN DEFINIEREN]** Ticket
* **`Is customer's last order`** wird von einem Analytiker im Rahmen Ihrer **[CHURN DEFINIEREN]** Ticket
* **`Seconds since previous order`** wird von einem Analytiker im Rahmen Ihrer **[CHURN DEFINIEREN]** Ticket
* **`Months since order`** wird von einem Analytiker im Rahmen Ihrer **[CHURN DEFINIEREN]** Ticket
* **`Months since previous order`** wird von einem Analytiker im Rahmen Ihrer **[CHURN DEFINIEREN]** Ticket

## Metriken

Keine neuen Metriken!

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

## Berichte

* **anfängliche Wiederholungsreihenwahrscheinlichkeit**
* Metrik A: Alle Wiederholungsaufträge
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Alle Zeitaufträge
* [!UICONTROL Metric]: Anzahl Bestellungen

* [!UICONTROL Formula]: anfängliche Wiederholungsreihenwahrscheinlichkeit
* 
   [!UICONTROL Formel]: `A/B`
* 

   [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* 

   [!UICONTROL Chart type]: `Scalar`

* **Wiederholungsbestellwahrscheinlichkeit seit Bestellung in Monaten**
* Metrik A: Bestellungen nach Monaten seit der vorherigen Bestellung wiederholen (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* 
   [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Letzte Bestellungen nach Monaten seit Bestellung (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* 
   [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* Metrik C: Wiederholungsreihenfolge (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* 

   [!UICONTROL Gruppe von]: `Independent`

* Metrik D: Alle letzten Bestellungen (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* 

   [!UICONTROL Gruppe von]: `Independent`

* [!UICONTROL Formula]: anfängliche Wiederholungsreihenwahrscheinlichkeit
* 
   [!UICONTROL Formel]: `(C-A)/(C+D-A-B)`
* 

   [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Months since previous order`
* Show top.bottom: Top 24 Kategorien, sortiert nach Kategoriename

* 

   [!UICONTROL Chart type]: `Line`

Der Bericht zur anfänglichen Wiederholungsbestellwahrscheinlichkeit stellt die Gesamtanzahl wiederholter Bestellungen/Gesamtbestellungen dar. Jede Bestellung bietet die Möglichkeit, eine Wiederholungsbestellung vorzunehmen. die Anzahl der Wiederholungsaufträge ist die Teilmenge der tatsächlich ausgeführten Bestellungen.

Die von uns verwendete Formel vereinfacht (Gesamtanzahl der Wiederholungsaufträge, die nach X Monaten erfolgten)/ (Gesamtbestellungen, die mindestens X Monate alt sind). Es zeigt uns, dass historisch gesehen, da es X Monate seit einer Bestellung ist, gibt es eine Y% Chance, dass der Benutzer eine andere Bestellung aufgibt.

Nachdem Sie Ihr Dashboard erstellt haben, erhalten wir am häufigsten folgende Frage: Wie kann ich dies verwenden, um eine Abwanderungsschwelle zu bestimmen?

**Darauf gibt es keine &quot;richtige Antwort&quot;.** Es wird jedoch empfohlen, den Punkt zu ermitteln, an dem die Zeile den Wert überschreitet, der der Hälfte der anfänglichen Wiederholwahrscheinlichkeitsrate entspricht. Dies ist der Punkt, an dem wir sagen können: &quot;Wenn ein Benutzer eine Wiederholungsreihenfolge vornehmen würde, hätte er dies wahrscheinlich bis jetzt getan.&quot; Letztlich besteht das Ziel darin, die Schwelle auszuwählen, an der es sinnvoll ist, von &quot;Bindung&quot;zu &quot;Reaktivierung&quot;zu wechseln.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Endergebnis kann wie das Bild oben auf der Seite aussehen

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach unser Professional Services-Team einbinden möchten, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).
