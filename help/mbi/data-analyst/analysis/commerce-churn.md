---
title: Commerce Churn
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

Dieses Thema zeigt, wie Sie eine **Abwanderungsrate** für Ihre **Commerce-Kunden** berechnen. Im Gegensatz zu SaaS oder herkömmlichen Abonnementunternehmen verfügen Commerce-Kunden in der Regel nicht über ein konkretes **&quot;Abwanderungsereignis&quot;**, das Ihnen zeigt, dass sie Ihre aktiven Kunden nicht mehr berücksichtigen sollten. Aus diesem Grund können Sie mit den folgenden Anweisungen einen Kunden anhand einer bestimmten Zeit, die seit seiner letzten Bestellung vergangen ist, als &quot;gebündelt&quot;definieren.

![](../../assets/Churn_rate_image.png)

Viele Kunden möchten Unterstützung bei der Konzeption des **Zeitrahmens**, den sie basierend auf ihren Daten verwenden sollten. Wenn Sie dieses **Abwanderungszeitrahmen** mit dem historischen Kundenverhalten definieren möchten, sollten Sie sich mit dem Thema [Abwanderungsdefinition](../analysis/define-cust-churn.md) vertraut machen. Anschließend können Sie die Ergebnisse in der Formel für die Abwanderungsrate in den folgenden Anweisungen verwenden.

## Berechnete Spalten

Zu erstellende Spalten

* **`customer_entity`** table
* **`Customer's last order date`**
   * Wählen Sie einen [!UICONTROL definition]: `Max`
   * Wählen Sie [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie [!UICONTROL column]: `created_at`
   * `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]: `Orders we count`

* **`Seconds since customer's last order date`**
   * Wählen Sie einen [!UICONTROL definition]: `Age`
   * Wählen Sie [!UICONTROL column]: `Customer's last order date`

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

## Metriken

* **Neue Kunden (nach Datum der ersten Bestellung)**
   * Zählte Kunden

>[!NOTE]
>
>Diese Metrik kann in Ihrem Konto vorhanden sein.

* In der Tabelle **`customer_entity`**
* Diese Metrik führt eine **Zählung** aus
* In der Spalte **`entity_id`**
* Durch den Zeitstempel **`Customer's first order date`** geordnet
* [!UICONTROL Filter]:

* **Neue Kunden (nach Datum der letzten Bestellung)**
   * Zählte Kunden

  >[!NOTE]
  >
  >Diese Metrik kann in Ihrem Konto vorhanden sein.

* In der Tabelle **`customer_entity`**
* Diese Metrik führt eine **Zählung** aus
* In der Spalte **`entity_id`**
* Durch den Zeitstempel **`Customer's last order date`** geordnet
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

## Berichte

* **Abwanderungsrate**
   * [!UICONTROL Metric]: Neue Kunden (nach Datum der ersten Bestellung)
   * [!UICONTROL Filter]: `Lifetime number of orders Greater Than 0`
   * 
     [!UICONTROL Perspective]: `Cumulative`
   * [!UICONTROL Metric]: `New customers (by last order date)`
   * [!UICONTROL Filter]:
   * Sekunden seit dem letzten Bestelldatum des Kunden >= [Ihr selbst definierter Cutoff für abgesicherte Kunden ]**`^`**
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

| **Months** | **Seconds** |
|---|---|
| 3 | 7.776.000 |
| 6 | 15.552.000 |
| 9 | 23.328.000 |
| 12 | 31.104.000 |

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.
