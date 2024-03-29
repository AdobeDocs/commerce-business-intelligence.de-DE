---
title: Commerce-Abwanderung
description: Erfahren Sie, wie Sie Ihre Commerce-Abwanderungsrate generieren und analysieren.
exl-id: 8775cf0a-114d-4b48-8bd2-fc1700c59a12
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---

# Abwanderungsrate

Dieses Thema zeigt, wie Sie eine **Abwanderungsrate** für Ihre **Commerce-Kunden**. Im Gegensatz zu SaaS oder traditionellen Abonnementunternehmen verfügen Commerce-Kunden in der Regel nicht über einen konkreten **&quot;Abwanderungsereignis&quot;** um Ihnen zu zeigen, dass sie nicht mehr mit Ihren aktiven Kunden zählen sollten. Aus diesem Grund können Sie mit den folgenden Anweisungen einen Kunden anhand einer bestimmten Zeit, die seit seiner letzten Bestellung vergangen ist, als &quot;gebündelt&quot;definieren.

![](../../assets/Churn_rate_image.png)

Viele Kunden möchten Unterstützung bei der Konzeption dessen, was **timeframe** sollten sie anhand ihrer Daten verwenden. Wenn Sie das Kundenverhalten aus der Vergangenheit zur Definition von **Abwanderungszeitrahmen**, sollten Sie sich mit der [Abwanderung definieren](../analysis/define-cust-churn.md) Thema. Anschließend können Sie die Ergebnisse in der Formel für die Abwanderungsrate in den folgenden Anweisungen verwenden.

## Berechnete Spalten

Zu erstellende Spalten

* **`customer_entity`** table
* **`Customer's last order date`**
   * Wählen Sie eine [!UICONTROL definition]: `Max`
   * Auswählen [!UICONTROL table]: `sales_flat_order`
   * Auswählen [!UICONTROL column]: `created_at`
   * `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]: `Orders we count`

* **`Seconds since customer's last order date`**
   * Wählen Sie eine [!UICONTROL definition]: `Age`
   * Auswählen [!UICONTROL column]: `Customer's last order date`

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

## Metriken

* **Neue Kunden (nach Datum der ersten Bestellung)**
   * Zählte Kunden

>[!NOTE]
>
>Diese Metrik kann in Ihrem Konto vorhanden sein.

* Im **`customer_entity`** table
* Diese Metrik führt eine **Count**
* Im **`entity_id`** column
* Bestellt von der **`Customer's first order date`** timestamp
* [!UICONTROL Filter]:

* **Neue Kunden (nach letztem Bestelldatum)**
   * Zählte Kunden

  >[!NOTE]
  >
  >Diese Metrik kann in Ihrem Konto vorhanden sein.

* Im **`customer_entity`** table
* Diese Metrik führt eine **Count**
* Im **`entity_id`** column
* Bestellt von der **`Customer's last order date`** timestamp
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

## Berichte

* **Abwanderungsrate**
   * [!UICONTROL Metric]: Neue Kunden (nach Datum der ersten Bestellung)
   * [!UICONTROL Filter]: `Lifetime number of orders Greater Than 0`
   * 
     [!UICONTROL Perspective]: `Cumulative`
   * [!UICONTROL Metric]: `New customers (by last order date)`
   * [!UICONTROL Filter]:
   * Sekunden seit dem letzten Bestelldatum des Kunden >= [Ihr selbst definierter Cutoff für gedrehte Kunden ]**`^`**
   * `Lifetime number of orders Greater Than 0`

   * [!UICONTROL Metric]: `New customers (by last order date)`
   * [!UICONTROL Filter]: `Lifetime number of orders Greater Than 0`
   * 
     [!UICONTROL Perspective]: Cumulative
   * [!UICONTROL Formula]: `(B / ((A + B) - C)`
   * 
     [!UICONTROL Format]: Percentage

* *Metrik `A`:`New customers cumulative`*
* *Metrik `B`:`Churned customers by last order date`*
* *Metrik `C`:`Customers by last order date cumulative`*
* *`Formula`:`Repeat order probability`*
* *`Time period`:`All time (or custom range)`*
* *`Group by`:`Customer's order number`*
* *`Chart Type`:`Column`*

Unten finden Sie einige gängige Konvertierungen vom Typ Monat > Sekunde , Google stellt jedoch weitere Werte bereit, darunter Konversionen vom Typ Woche > Sekunden für alle benutzerdefinierten Werte, nach denen Sie suchen können.

| **Monate** | **Sekunden** |
|---|---|
| 3 | 7,776,000 |
| 6 | 15,552,000 |
| 9 | 23,328,000 |
| 12 | 31,104,000 |

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.
