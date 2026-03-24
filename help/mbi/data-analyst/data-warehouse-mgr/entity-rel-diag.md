---
title: Entitätsbeziehungsdiagramme
description: Erfahren Sie mehr über einige ER-Diagramme, die Ihnen dabei helfen, die Beziehung zwischen einer Handvoll gängiger Commerce-Datenbanktabellen zu visualisieren.
exl-id: de7d419f-efbe-4d0c-95a8-155a12aa93f3
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/pWd5aVoaq2TPkGr37cNeF8CEZ63fItwCEez61eEgGBo
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 346
ht-degree: 0%

---

# Entitätsbeziehungsdiagramm

What is an **[!UICONTROL entity relationship (ER) diagram]**? An [!UICONTROL ER] diagram is a visualization of tables within a database and how they relate to each other. This topic contains a few [!UICONTROL ER] diagrams to help you visualize the relationship between a few common Adobe Commerce database tables.

>[!NOTE]
>
>In diesem Thema werden die Wörter **Join**, **relation** und **path** angezeigt. Diese Wörter werden alle verwendet, um zu beschreiben, wie zwei Tabellen verbunden sind.

## Commerce-[!UICONTROL ER]

![4_DB_chart](../../assets/4_DB_Chart.png)

Dieses `ER` stellt die Beziehungen zwischen den Kerntabellen in einer Commerce-Datenbank dar. Wenn Sie mehrere Beziehungen gleichzeitig betrachten, können Sie sehen, wie sich Daten über viele Tabellen hinweg verhalten würden.

Die folgenden Abschnitte enthalten `ER` Diagramme, die jeweils für zwei Tabellen spezifisch sind. Um ein Diagramm und die zugehörige Beschreibung anzuzeigen, klicken Sie auf die Kopfzeile für diesen Abschnitt.

## `customer\_entity & sales\_flat\_order`

![Ein Kunde und viele Bestellungen](../../assets/2_OneCustomerManyOrders.png)

Ein Kunde kann viele Bestellungen aufgeben. Die Beziehung zwischen diesen beiden Tabellen ist `customer\_entity.entity\_id = sales\_flat\_order.customer\_id`

>[!IMPORTANT]
>
>`customer\_entity.entity\_id` does not equal `sales\_flat\_order.entity\_id`. The first can be thought of as a `customer\_id` and the second can be thought of as an `order\_id.`

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, wird er wie folgt definiert:

![Entitätsbeziehungsdiagramm, das den Pfad von sales_flat_order zu customer_entity anzeigt](../../assets/SFO___CE_path.png)

## `sales\_flat\_order & sales\_flat\_order\_item`

![1_OneOrderManyItems](../../assets/1_OneOrderManyItems.png)

Eine Bestellung kann viele Artikel enthalten. Die Beziehung zwischen diesen beiden Tabellen ist `sales\_flat\_order.entity\_id = sales\_flat\_order\_item.order\_id`.

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, definieren Sie ihn wie unten gezeigt.

![Entitätsbeziehungsdiagramm, das den Pfad von sales_flat_order_item zu sales_flat_order anzeigt](../../assets/SFOI___SFO_path.png)

## `catalog\_product\_entity & sales\_flat\_order\_item`

![3_oneProductManyTimes](../../assets/3_OneProductManyTimes.png)

One product can be purchased many items. Die Beziehung zwischen diesen beiden Tabellen ist `catalog\_product\_entity.entity\_id = sales\_flat\_order\_item.product`.

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, definieren Sie ihn wie unten gezeigt.

![Entitätsbeziehungsdiagramm, das den Pfad von sales_flat_order_item zu catalog_product_entity anzeigt](../../assets/SFOI___CPE_path.png)
