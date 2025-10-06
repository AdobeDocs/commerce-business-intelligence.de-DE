---
title: Commerce-Abwanderung
description: Erfahren Sie, wie Sie Ihre Commerce-Abwanderungsrate generieren und analysieren.
exl-id: 8775cf0a-114d-4b48-8bd2-fc1700c59a12
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---

# Abwanderungsrate

Dieses Thema zeigt, wie Sie eine **Abwanderungsrate** für Ihre **Commerce-Kunden** berechnen. Im Gegensatz zu SaaS oder herkömmlichen Abonnementunternehmen verfügen Commerce-Kunden normalerweise nicht über ein konkretes **-„Abwanderungsereignis“,** Ihnen zu zeigen, dass sie nicht mehr für Ihre aktiven Kunden zählen sollten. Aus diesem Grund können Sie mit den folgenden Anweisungen einen Kunden als „abgewandert“ definieren, basierend auf einer bestimmten Zeitspanne seit seiner letzten Bestellung.

![Visualisierung der Abwanderungsrate mit der Kundenbindung im Zeitverlauf](../../assets/Churn_rate_image.png)

Viele Kunden wünschen Hilfe beim Einstieg in die Konzeption **Zeitrahmens**, den sie basierend auf ihren Daten verwenden sollten. Wenn Sie zur Definition dieses **Abwanderungszeitrahmens“ das historische Kundenverhalten** möchten, sollten Sie sich mit dem Thema [Abwanderung definieren](../analysis/define-cust-churn.md) vertraut machen. Anschließend können Sie die Ergebnisse in der Formel für die Abwanderungsrate in den folgenden Anweisungen verwenden.

## Berechnete Spalten

Zu erstellende Spalten

* **`customer_entity`**
* **`Customer's last order date`**
   * [!UICONTROL definition] auswählen: `Max`
   * [!UICONTROL table] auswählen: `sales_flat_order`
   * [!UICONTROL column] auswählen: `created_at`
   * `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]: `Orders we count`

* **`Seconds since customer's last order date`**
   * [!UICONTROL definition] auswählen: `Age`
   * [!UICONTROL column] auswählen: `Customer's last order date`

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Metriken

* **Neue Kunden (nach Datum der ersten Bestellung)**
   * Kunden, die gezählt werden

>[!NOTE]
>
>Diese Metrik kann in Ihrem Konto vorhanden sein.

* In der **`customer_entity`**
* Diese Metrik führt eine **Anzahl** aus
* In der Spalte **`entity_id`**
* Sortiert nach dem **`Customer's first order date`** Zeitstempel
* [!UICONTROL Filter]:

* **Neue Kunden (nach letztem Bestelldatum)**
   * Kunden, die gezählt werden

  >[!NOTE]
  >
  >Diese Metrik kann in Ihrem Konto vorhanden sein.

* In der **`customer_entity`**
* Diese Metrik führt eine **Anzahl** aus
* In der Spalte **`entity_id`**
* Sortiert nach dem **`Customer's last order date`** Zeitstempel
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **Abwanderungsrate**
   * [!UICONTROL Metric]: Neue Kunden (nach Datum der ersten Bestellung)
   * [!UICONTROL Filter]: `Lifetime number of orders Greater Than 0`
   * &#x200B;
     [!UICONTROL Perspective]: `Cumulative`
   * [!UICONTROL Metric]: `New customers (by last order date)`
   * [!UICONTROL Filter]:
   * Sekunden seit dem letzten Bestelldatum des Kunden >= [Ihr selbst definierter Abgang für abgewanderte Kunden ]&#x200B;**`^`**
   * `Lifetime number of orders Greater Than 0`

   * [!UICONTROL Metric]: `New customers (by last order date)`
   * [!UICONTROL Filter]: `Lifetime number of orders Greater Than 0`
   * &#x200B;
     [!UICONTROL Perspective]: Cumulative
   * [!UICONTROL Formula]: `(B / ((A + B) - C)`
   * &#x200B;
     [!UICONTROL Format]: Percentage

* *`A`:`New customers cumulative`*
* *`B`:`Churned customers by last order date`*
* *`C`:`Customers by last order date cumulative`*
* *`Formula`:`Repeat order probability`*
* *`Time period`:`All time (or custom range)`*
* *`Group by`:`Customer's order number`*
* *`Chart Type`:`Column`*

Im Folgenden finden Sie einige häufige Monate > zweite Konversionen, aber Google liefert andere Werte, einschließlich Wochen > Sekunden Konversionen für alle benutzerdefinierten Werte, nach denen Sie suchen.

| **Monate** | **Sekunden** |
|---|---|
| 3 | 7.776.000 |
| 6 | 15.552.000 |
| 9 | 23.328.000 |
| 12 | 31.104.000 |

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.
