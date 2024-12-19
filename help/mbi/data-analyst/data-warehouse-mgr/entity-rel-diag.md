---
title: Entitätsbeziehungsdiagramme
description: Erfahren Sie mehr über einige ER-Diagramme, die Ihnen dabei helfen, die Beziehung zwischen einer Handvoll gängiger Commerce-Datenbanktabellen zu visualisieren.
exl-id: de7d419f-efbe-4d0c-95a8-155a12aa93f3
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '319'
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

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse erstellen. Wenn Sie bereit sind, den Pfad zu erstellen, wird er wie folgt definiert:

![](../../assets/SFO___CE_path.png)

## `sales\_flat\_order & sales\_flat\_order\_item`

![1_OneOrderManyItems](../../assets/1_OneOrderManyItems.png)

Eine Bestellung kann viele Artikel enthalten. Die Beziehung zwischen diesen beiden Tabellen ist `sales\_flat\_order.entity\_id = sales\_flat\_order\_item.order\_id`.

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse verwenden. Wenn Sie bereit sind, den Pfad zu erstellen, definieren Sie ihn wie unten gezeigt.

![](../../assets/SFOI___SFO_path.png)

## `catalog\_product\_entity & sales\_flat\_order\_item`

![3_oneProductManyTimes](../../assets/3_OneProductManyTimes.png)

Ein Produkt kann viele Artikel gekauft werden. Die Beziehung zwischen diesen beiden Tabellen ist `catalog\_product\_entity.entity\_id = sales\_flat\_order\_item.product`.

Wenn der Pfad zwischen diesen beiden Tabellen in [!DNL Commerce Intelligence] nicht vorhanden ist, können Sie [den Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse erstellen. Wenn Sie bereit sind, den Pfad zu erstellen, definieren Sie ihn wie unten gezeigt.

![](../../assets/SFOI___CPE_path.png)
