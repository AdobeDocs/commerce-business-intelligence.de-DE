---
title: Analyse der zurückgegebenen Bestellungen
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das eine detaillierte Analyse der Rückgaben Ihres Stores bietet.
exl-id: 6a948561-45b7-4813-9661-ab42197ca5bd
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Zurückgegebene Bestellungen

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das eine detaillierte Analyse der Rückgaben Ihres Stores bietet.

![](../../assets/detailed-returns-dboard.png)

Bevor Sie beginnen, müssen Sie [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html)-Kunde sein und sollten sicherstellen, dass Ihr Unternehmen die `enterprise\_rma` für Rücksendungen verwendet.

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Nachzuverfolgende Spalten

* **`enterprise_rma`** oder **`rma`**
* **`entity_id`**
* **`status`**
* **`order_id`**
* **`customer_id`**
* **`date_requested`**

* **`enterprise_rma_item_entity`** oder **`rma_item_entity`**
* **`entity_id`**
* **`rma_entity_id`**
* **`qty_returned`**
* **`status`**
* **`order_item_id`**
* **`product_name`**
* **`product_sku`**

Zu erstellende Filtersätze

* **`enterprise_rma`**
* Name des Filtersatzes: `Returns we count`
* Filtersatz-Logik:
   * Platzhalter - geben Sie Ihre benutzerdefinierte Logik hier ein

* **`enterprise_rma_item_entity`**
* Name des Filtersatzes: `Returns items we count`
* Filtersatz-Logik:
   * Platzhalter - geben Sie Ihre benutzerdefinierte Logik hier ein

### Berechnete Spalten

Zu erstellende Spalten

* **`enterprise_rma`**
* **`Order's created at`**
* Definition auswählen: `Joined Column`
* [!UICONTROL Create Path]:
* &#x200B;
  [!UICONTROL Many]: `enterprise_rma.order_id`
* &#x200B;
  [!UICONTROL One]: `sales_flat_order.entity_id`

* [!UICONTROL table] auswählen: `sales_flat_order`
* [!UICONTROL column] auswählen: `created_at`
   * `enterprise_rma.order_id = sales_flat_order.entity_id`

* **`Customer's order number`**
* Definition auswählen: `Joined Column`
* [!UICONTROL table] auswählen: `sales_flat_order`
* [!UICONTROL column] auswählen: `Customer's order number`
   * `enterprise_rma.order_id = sales_flat_order.entity_id`

* **`Time between order's created_at and date_requested`** wird von einem Analyst im Rahmen Ihres `[RETURNS ANALYSIS]` Tickets erstellt

* **`enterprise_rma_item_entity`**
* **`return_date_requested`**
* Definition auswählen: `Joined Column`
* [!UICONTROL Create Path]:
   * &#x200B;

     [!UICONTROL Many]: `enterprise_rma_item_entity.rma_entity_id`
   * &#x200B;

     [!UICONTROL One]: `enterprise_rma.entity_id`

* [!UICONTROL table] auswählen: `enterprise_rma`
* [!UICONTROL column] auswählen: `date_requested`
   * `enterprise_rma_item_entity.rma_entity_id = enterprise_rma.entity_id`

* **`Return item total value (qty_returned * price)`** wird von einem Analyst im Rahmen Ihres `[RETURNS ANALYSIS]` Tickets erstellt

* **`sales_flat_order`**
* **`Order contains a return? (1=yes/0=No)`**
* Definition auswählen: `Exists`
* [!UICONTROL table] auswählen: `enterprise_rma`
   * `enterprise_rma.order_id = sales_flat_order.entity_id`

* **`Customer's previous order number`** wird von einem Analyst im Rahmen Ihres `[RETURNS ANALYSIS]` Tickets erstellt
* **`Customer's previous order contains return? (1=yes/0=no)`** wird von einem Analyst im Rahmen Ihres `[RETURNS ANALYSIS]` Tickets erstellt

>[!NOTE]
>
>Wenn Sie daran interessiert sind, nur die Geschäftszeiten für Sekunden bis zur Lösung oder Sekunden bis zur ersten Antwort zu analysieren, informieren Sie den Analyst, wenn Sie das Ticket anfordern.

### Metriken

* **Rückgabe**
* In der **`enterprise_rma`**
* Diese Metrik führt eine **Anzahl** aus
* In der Spalte **`entity_id`**
* Sortiert nach der **`date_requested`**
* [!UICONTROL Filter]: `Returns we count`

* **Zurückgegebene Elemente**
* In der **`enterprise_rma_item_entity`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`qty_approved`**
* Sortiert nach der **`return date_requested`**
* [!UICONTROL Filter]: `Returns we count`

* **Zurückgegebener Artikelgesamtwert**
* In der **`enterprise_rma_item_entity`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`Returned item total value (qty_returned * price)`**
* Sortiert nach der **`return date_requested`**
* [!UICONTROL Filter]: `Returns we count`

* **Durchschnittliche Zeit zwischen Bestellung und Rücksendung**
* In der **`enterprise_rma`**
* Diese Metrik führt einen **Durchschnitt** aus
* In der Spalte **`Time between order's created_at and date_requested`**
* Sortiert nach der **`date_requested`**
* [!UICONTROL Filter]: `Returns we count`

>[!NOTE]
>
>Stellen Sie sicher[ dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

### Berichte

* **Wiederholungsreihenwahrscheinlichkeit nach einer Rücksendung**
* `A`: `Number of orders with returns`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Order contains a return? (1=yes/0=No) = 1`
   * `Is in current month? = No`

* `B`: `Non-last orders with returns`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Is customer's last order? (1=yes/0=no) = 0`
   * `Order contains a return? (1=yes/0=No) = 1`

* Formel: Wahrscheinlichkeit der Wiederholungsreihenfolge
* [!UICONTROL Formula]: `B / A`
* &#x200B;
  [!UICONTROL Format]: `Percentage`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `Customer's order number`
* &#x200B;
  [!UICONTROL Diagrammtyp]: `Bar`

* **Durchschn. Zeit bis zur Rückkehr (alle Zeiten)**
* `A`: `Avg time between order and return`
* [!UICONTROL Metric]: `Avg time between order and return`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* &#x200B;
  [!UICONTROL Diagrammtyp]: `Number`

* **Prozent der Bestellungen mit einer Rücksendung**
* `A`: `Number of orders`
* [!UICONTROL Metric]: `Number of orders`

* `B`: `Orders w/ return`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Order contains a return? (1=yes/0=No) = 1`

* Formel: % der Bestellungen mit Rücksendung
* [!UICONTROL Formula]: `B / A`
* &#x200B;
  [!UICONTROL Format]: `Percentage`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Chart Type]: `Number - % of orders with return`

* **Rückgegebener Umsatz nach Monat**
* `A`: `Returned item total value`
* [!UICONTROL Metric]: `Returned item total value`

* [!UICONTROL Time period]: `All time`
* [!UICONTROL Interval]: `By month`
* &#x200B;
  [!UICONTROL Diagrammtyp]: `Line`

* **Kunden, die eine Rückgabe getätigt und nicht erneut gekauft haben**
* `A`: `Number of orders with returns`
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:
   * `Order contains a return? (1=yes/0=No) = 1`
   * `Is customer's last order? (1=yes/0=no) = 1`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* &#x200B;
  [!UICONTROL Gruppieren nach]: `Customer_email`
* &#x200B;
  [!UICONTROL Diagrammtyp]: `Table`

* **Rückgaberate nach Artikel**
* Metrik `A`: `Returned items` (Ausblenden)
* [!UICONTROL Metric]: Zurückgegebene Elemente

* Metrik `B`: `Items sold` (Ausblenden)
* [!UICONTROL Metric]: `Number of orders`
* [!UICONTROL Filter]:

* [!UICONTROL Formula]: `Return %`
* [!UICONTROL Formula]: `B / A`
* &#x200B;
  [!UICONTROL Format]: `Percentage`

* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* [!UICONTROL Group by]: `product_sku AND/OR product_name`
* &#x200B;
  [!UICONTROL Diagrammtyp]: `Table`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie im obigen Beispiel-Dashboard aussehen.

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder das Professional Services-Team kontaktieren möchten, wenden [ sich an den ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).
