---
title: Entitätsbeziehungsdiagramme
description: Erfahren Sie mehr über einige ER-Diagramme, die Ihnen dabei helfen, die Beziehung zwischen einer Handvoll gängiger Commerce-Datenbanktabellen zu visualisieren.
exl-id: de7d419f-efbe-4d0c-95a8-155a12aa93f3
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: 'https://experienceleague.adobe.com/pWd5aVoaq2TPkGr37cNeF8CEZ63fItwCEez61eEgGBo'
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
    internal-label: Commerce Intelligence
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
    internal-label: Data Warehouse Manager
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
    internal-label: Order Management System
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4d217dbe-2c9a-5839-94d7-471fd31623b7
    internal-label: Data Integration
  - id: 5d2a63cb-5675-5572-9de5-bc904157ef45
    internal-label: Commerce Tables
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
source-git-commit: fdbaf74705fb224414ac8cb69f6a1b34277e3f79
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%
---
# Entitätsbeziehungsdiagramm

Was ist ein **[!UICONTROL entity relationship (ER) diagram]**? Ein [!UICONTROL ER] ist eine Visualisierung von Tabellen innerhalb einer Datenbank und ihrer Beziehung zueinander. Dieses Thema enthält einige [!UICONTROL ER], die Ihnen helfen, die Beziehung zwischen einigen gängigen Adobe Commerce-Datenbanktabellen zu visualisieren.

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
>`customer\_entity.entity\_id` ist nicht gleich `sales\_flat\_order.entity\_id`. Das erste kann als `customer\_id` betrachtet werden, und das zweite kann als `order\_id.` betrachtet werden

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, wird er wie folgt definiert:

![Entitätsbeziehungsdiagramm, das den Pfad von sales_flat_order zu customer_entity anzeigt](../../assets/SFO___CE_path.png)

## `sales\_flat\_order & sales\_flat\_order\_item`

![1_OneOrderManyItems](../../assets/1_OneOrderManyItems.png)

Eine Bestellung kann viele Artikel enthalten. Die Beziehung zwischen diesen beiden Tabellen ist `sales\_flat\_order.entity\_id = sales\_flat\_order\_item.order\_id`.

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, definieren Sie ihn wie unten gezeigt.

![Entitätsbeziehungsdiagramm, das den Pfad von sales_flat_order_item zu sales_flat_order anzeigt](../../assets/SFOI___SFO_path.png)

## `catalog\_product\_entity & sales\_flat\_order\_item`

![3_oneProductManyTimes](../../assets/3_OneProductManyTimes.png)

Ein Produkt kann viele Artikel gekauft werden. Die Beziehung zwischen diesen beiden Tabellen ist `catalog\_product\_entity.entity\_id = sales\_flat\_order\_item.product`.

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, definieren Sie ihn wie unten gezeigt.

![Entitätsbeziehungsdiagramm, das den Pfad von sales_flat_order_item zu catalog_product_entity anzeigt](../../assets/SFOI___CPE_path.png)
