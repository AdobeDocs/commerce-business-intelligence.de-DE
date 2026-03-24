---
title: Kundenabwanderung definieren
description: Erfahren Sie, wie Sie ein Dashboard einrichten, mit dem Sie Abwanderung für Ihre Transaktionskunden definieren können.
exl-id: fea8f7e9-c84c-4d49-a657-8b75140c113a
role: Admin, Developer, User
feature: Data Warehouse Manager, Reports, Dashboards
TQID: https://experienceleague.adobe.com/eDJBh7FlhuKjBa5ft4sqAfZavmBk4V9m-Iu-26cG2VI
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 482
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
>Stellen Sie sicher[ dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **Anfängliche Wiederholungsreihenfolgewahrscheinlichkeit**
* Metrik A: Allzeit-Wiederholungsaufträge
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Allzeitbestellungen
* [!UICONTROL Metric]: Anzahl der Bestellungen

* [!UICONTROL Formula]: Anfängliche Wahrscheinlichkeit für Wiederholungsreihenfolge
* 
  [!UICONTROL-Formel]: `A/B`
* 
  [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* 
  [!UICONTROL Chart type]: `Scalar`

* **Wiederholungsreihenwahrscheinlichkeit angegeben Monate seit Bestellung**
* Metrik A: Wiederholungsaufträge nach Monaten seit vorheriger Bestellung (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* 
  [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* Metrik B: Letzte Bestellungen nach Monaten seit Bestellung (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* 
  [!UICONTROL Perspective]: `Cumulative`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* Metrik C: Allzeit-Wiederholungsaufträge (ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Customer's order number greater than 1`

* 
  [!UICONTROL Gruppieren nach]: `Independent`

* Metrik-ID: Letzte Bestellungen (Ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]: `Is customer's last order? (Yes/No) = Yes`

* 
  [!UICONTROL Gruppieren nach]: `Independent`

* [!UICONTROL Formula]: Anfängliche Wahrscheinlichkeit für Wiederholungsreihenfolge
* 
  [!UICONTROL-Formel]: `(C-A)/(C+D-A-B)`
* 
  [!UICONTROL Format]: `Percent`

* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Months since previous order`
* Oben anzeigen.Unten: Die 24 wichtigsten Kategorien, sortiert nach Kategorienamen

* 
  [!UICONTROL Chart type]: `Line`

Der Bericht über die Wahrscheinlichkeit des ursprünglichen Wiederholungsauftrags stellt die Gesamtzahl der Wiederholungsaufträge/Gesamtaufträge dar. Jede Bestellung ist eine Möglichkeit, eine Wiederholungsreihenfolge zu erstellen. Die Anzahl der Wiederholungsreihenfolgen ist die Teilmenge derjenigen, die tatsächlich eine Wiederholungsreihenfolge ausführen.

Die von Ihnen verwendete Formel vereinfacht die Verarbeitung von (Gesamtzahl der Wiederholungsaufträge, die nach X Monaten erfolgt sind)/ (Gesamtzahl der Aufträge, die mindestens X Monate alt sind). Es zeigt uns, dass historisch gesehen, angesichts der Tatsache, dass X Monate seit einer Bestellung vergangen sind, eine Y%-Chance besteht, dass der Benutzer eine andere Bestellung aufgibt.

Nachdem Sie Ihr Dashboard erstellt haben, lautet die am häufigsten gestellte Frage: Wie verwende ich dies, um eine Abwanderungsschwelle zu bestimmen?

**Darauf gibt es keine „einzig richtige Antwort“.** empfiehlt Adobe jedoch, den Punkt zu finden, an dem die Linie den Wert kreuzt, der der Hälfte der ursprünglichen Wiederholungswahrscheinlichkeitsrate entspricht. An diesem Punkt kann man sagen: „Wenn ein Benutzer eine Wiederholungsreihenfolge vornimmt, dann hätte er sie wahrscheinlich schon gemacht.“ Letztlich besteht das Ziel darin, den Schwellenwert auszuwählen, bei dem es sinnvoll ist, von „Aufbewahrungs“- zu „Reaktivierungs“-Bemühungen zu wechseln.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie das Bild oben auf der Seite aussehen

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [ sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
