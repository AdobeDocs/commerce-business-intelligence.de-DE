---
title: Kundenabwanderung definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie die Abwanderung Ihrer Transaktionskunden definieren können.
exl-id: fea8f7e9-c84c-4d49-a657-8b75140c113a
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Abwanderung von Transaktionskunden

In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, mit dem Sie die Abwanderung Ihrer Transaktionskunden definieren können.

![](../../assets/churn-deashboard.png)

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Berechnete Spalten

Zu erstellende Spalten

* `customer_entity` table
* `Customer's lifetime number of orders`
* Wählen Sie eine Definition aus: `Count`
* Wählen Sie einen [!UICONTROL table]: `sales_flat_order`
* Wählen Sie einen [!UICONTROL column]: **`entity_id`**
* [!UICONTROL Path]: sales_flach_order.customer_id = customer_entity.entity_id
* [!UICONTROL Filter]:
* Bestellungen, die gezählt werden

* `sales_flat_order` table
* `Customer's lifetime number of orders`
* Definition auswählen: Verbundene Spalte
* Wählen Sie einen [!UICONTROL table]: `customer_entity`
* Wählen Sie einen [!UICONTROL column]: `Customer's lifetime number of orders`
* [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
* [!UICONTROL Filter]: `Orders we count`

* `Seconds since created_at`
* Wählen Sie eine Definition aus: `Age`
* Wählen Sie einen [!UICONTROL column]: `created_at`

* **`Customer's order number`** wird von einem Analysten im Rahmen Ihres **[DEFINING CHURN]**-Tickets erstellt
* **`Is customer's last order`** wird von einem Analysten im Rahmen Ihres **[DEFINING CHURN]**-Tickets erstellt
* **`Seconds since previous order`** wird von einem Analysten im Rahmen Ihres **[DEFINING CHURN]**-Tickets erstellt
* **`Months since order`** wird von einem Analysten im Rahmen Ihres **[DEFINING CHURN]**-Tickets erstellt
* **`Months since previous order`** wird von einem Analysten im Rahmen Ihres **[DEFINING CHURN]**-Tickets erstellt

## Metriken

Keine neuen Metriken!

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

## Berichte

* **anfängliche Wiederholungsauftragswahrscheinlichkeit**
* Metrik A: Wiederholungsaufträge in Echtzeit
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Allzeitbestellungen
* [!UICONTROL Metric]: Anzahl der Bestellungen

* [!UICONTROL Formula]: Anfangswahrscheinlichkeit der Wiederholungsreihenfolge
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
* Metrik A: Bestellungen nach Monaten seit vorheriger Bestellung wiederholen (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* 
  [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Letzte Bestellungen nach Monaten seit der Bestellung (Verbergen)
* [!UICONTROL Metric]: `Number of orders`
* 
  [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* Metrik C: Wiederholungsreihenfolgen (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* 
  [!UICONTROL Gruppe von]: `Independent`

* Metrik D: Letzte Bestellungen (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* 
  [!UICONTROL Gruppe von]: `Independent`

* [!UICONTROL Formula]: Anfangswahrscheinlichkeit der Wiederholungsreihenfolge
* 
  [!UICONTROL Formel]: `(C-A)/(C+D-A-B)`
* 
  [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Months since previous order`
* Top.bottom anzeigen: Top 24 Kategorien, sortiert nach Kategoriename

* 
  [!UICONTROL Chart type]: `Line`

Der Bericht zur anfänglichen Wiederholungsbestellwahrscheinlichkeit stellt die Gesamtanzahl wiederholter Bestellungen/Gesamtbestellungen dar. Jede Bestellung ist eine Möglichkeit, eine Wiederholungsbestellung zu tätigen. Die Anzahl der Wiederholungsaufträge ist die Teilmenge der Bestellungen, die tatsächlich ausgeführt werden.

Die Formel, die Sie verwenden, vereinfacht die Verwendung von (Gesamtanzahl der Wiederholungsaufträge, die nach X Monaten erfolgten)/ (Gesamtbestellungen, die mindestens X Monate alt sind). Es zeigt uns, dass es historisch gesehen, da es seit einer Bestellung X Monate sind, eine Y% Chance gibt, dass der Benutzer eine andere Bestellung aufgibt.

Nachdem Sie Ihr Dashboard erstellt haben, lautet die häufigste Frage: Wie kann ich damit einen Abwanderungsschwellenwert bestimmen?

**Hierauf gibt es keine &quot;richtige Antwort&quot;.** Adobe empfiehlt jedoch, den Punkt zu ermitteln, an dem die Zeile den Wert überschreitet, der der Hälfte der anfänglichen Wiederholwahrscheinlichkeitsrate entspricht. An dieser Stelle können Sie sagen: &quot;Wenn ein Benutzer eine Wiederholungsreihenfolge durchführt, hätte er dies wahrscheinlich bis jetzt getan.&quot; Letztlich besteht das Ziel darin, die Schwelle auszuwählen, an der es sinnvoll ist, von &quot;Bindung&quot;zu &quot;Reaktivierung&quot;zu wechseln.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das Bild oben auf der Seite aussehen

Wenn Sie beim Erstellen dieser Analyse Fragen haben oder einfach das Professional Services-Team kontaktieren möchten, wenden Sie sich an den Support [.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)
