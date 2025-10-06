---
title: Kundenabwanderung definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Abwanderung für Ihre Transaktionskunden definieren können.
exl-id: fea8f7e9-c84c-4d49-a657-8b75140c113a
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Abwanderung von Transaktionskunden

In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, mit dem Sie die Abwanderung für Ihre Transaktionskunden definieren können.

![Dashboard „Kundenabwanderung“ mit Metriken zur Abwanderungsrate und Kundenbindung](../../assets/churn-deashboard.png)

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Berechnete Spalten

Zu erstellende Spalten

* `customer_entity`
* `Customer's lifetime number of orders`
* Definition auswählen: `Count`
* [!UICONTROL table] auswählen: `sales_flat_order`
* [!UICONTROL column] auswählen: **`entity_id`**
* [!UICONTROL Path]: sales_flat_order.customer_id = customer_entity.entity_id
* [!UICONTROL Filter]:
* Bestellungen, die gezählt werden

* `sales_flat_order`
* `Customer's lifetime number of orders`
* Definition auswählen: Verbundene Spalte
* [!UICONTROL table] auswählen: `customer_entity`
* [!UICONTROL column] auswählen: `Customer's lifetime number of orders`
* [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
* [!UICONTROL Filter]: `Orders we count`

* `Seconds since created_at`
* Definition auswählen: `Age`
* [!UICONTROL column] auswählen: `created_at`

* **`Customer's order number`** wird von einem Analysten im Rahmen Ihres Tickets für **[ABWANDERUNG DEFINIEREN]** erstellt
* **`Is customer's last order`** wird von einem Analysten im Rahmen Ihres Tickets für **[ABWANDERUNG DEFINIEREN]** erstellt
* **`Seconds since previous order`** wird von einem Analysten im Rahmen Ihres Tickets für **[ABWANDERUNG DEFINIEREN]** erstellt
* **`Months since order`** wird von einem Analysten im Rahmen Ihres Tickets für **[ABWANDERUNG DEFINIEREN]** erstellt
* **`Months since previous order`** wird von einem Analysten im Rahmen Ihres Tickets für **[ABWANDERUNG DEFINIEREN]** erstellt

## Metriken

Keine neuen Metriken!

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **Anfängliche Wiederholungsreihenfolgewahrscheinlichkeit**
* Metrik A: Allzeit-Wiederholungsaufträge
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Allzeitbestellungen
* [!UICONTROL Metric]: Anzahl der Bestellungen

* [!UICONTROL Formula]: Anfängliche Wahrscheinlichkeit für Wiederholungsreihenfolge
* &#x200B;
  [!UICONTROL -Formel]: `A/B`
* &#x200B;
  [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* &#x200B;
  [!UICONTROL Chart type]: `Scalar`

* **Wiederholungsreihenwahrscheinlichkeit angegeben Monate seit Bestellung**
* Metrik A: Wiederholungsaufträge nach Monaten seit vorheriger Bestellung (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* &#x200B;
  [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Letzte Bestellungen nach Monaten seit Bestellung (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* &#x200B;
  [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* Metrik C: Allzeit-Wiederholungsaufträge (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* &#x200B;
  [!UICONTROL Gruppieren nach]: `Independent`

* Metrik-ID: Letzte Bestellungen (Ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* &#x200B;
  [!UICONTROL Gruppieren nach]: `Independent`

* [!UICONTROL Formula]: Anfängliche Wahrscheinlichkeit für Wiederholungsreihenfolge
* &#x200B;
  [!UICONTROL -Formel]: `(C-A)/(C+D-A-B)`
* &#x200B;
  [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Months since previous order`
* Oben anzeigen.Unten: Die 24 wichtigsten Kategorien, sortiert nach Kategorienamen

* &#x200B;
  [!UICONTROL Chart type]: `Line`

Der Bericht über die Wahrscheinlichkeit des ursprünglichen Wiederholungsauftrags stellt die Gesamtzahl der Wiederholungsaufträge/Gesamtaufträge dar. Jede Bestellung ist eine Möglichkeit, eine Wiederholungsreihenfolge zu erstellen. Die Anzahl der Wiederholungsreihenfolgen ist die Teilmenge derjenigen, die tatsächlich eine Wiederholungsreihenfolge ausführen.

Die von Ihnen verwendete Formel vereinfacht die Verarbeitung von (Gesamtzahl der Wiederholungsaufträge, die nach X Monaten erfolgt sind)/ (Gesamtzahl der Aufträge, die mindestens X Monate alt sind). Es zeigt uns, dass historisch gesehen, angesichts der Tatsache, dass X Monate seit einer Bestellung vergangen sind, eine Y%-Chance besteht, dass der Benutzer eine andere Bestellung aufgibt.

Nachdem Sie Ihr Dashboard erstellt haben, lautet die am häufigsten gestellte Frage: Wie verwende ich dies, um eine Abwanderungsschwelle zu bestimmen?

**Darauf gibt es keine „einzig richtige Antwort“.** empfiehlt Adobe jedoch, den Punkt zu finden, an dem die Linie den Wert kreuzt, der der Hälfte der ursprünglichen Wiederholungswahrscheinlichkeitsrate entspricht. An diesem Punkt kann man sagen: „Wenn ein Benutzer eine Wiederholungsreihenfolge vornimmt, dann hätte er sie wahrscheinlich schon gemacht.“ Letztlich besteht das Ziel darin, den Schwellenwert auszuwählen, bei dem es sinnvoll ist, von „Aufbewahrungs“- zu „Reaktivierungs“-Bemühungen zu wechseln.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie das Bild oben auf der Seite aussehen

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [&#x200B; sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
