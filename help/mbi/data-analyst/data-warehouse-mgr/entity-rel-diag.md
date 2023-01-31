---
title: Diagramme zur Entitätsbeziehung
description: Erfahren Sie mehr über einige ER-Diagramme, die Ihnen dabei helfen, die Beziehung zwischen einer Handvoll gängiger Commerce-Datenbanktabellen zu visualisieren.
exl-id: de7d419f-efbe-4d0c-95a8-155a12aa93f3
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Diagramm zur Entitätsbeziehung

Was ist eine **[!UICONTROL entity relationship (ER) diagram]**? Ein `ER` -Diagramm ist eine Visualisierung von Tabellen in einer Datenbank und deren Beziehung zueinander. Dieser Artikel enthält einige ER-Diagramme, mit denen Sie die Beziehung zwischen einer Handvoll gängiger Commerce-Datenbanktabellen visualisieren können.

>[!NOTE]
>
>In diesem Artikel sehen Sie die Wörter **join**, **Beziehung** und **path**. Anhand dieser Wörter wird beschrieben, wie zwei Tabellen miteinander verbunden sind.

## Core Commerce `ER` Abbildung

![4_DB_Chart](../../assets/4_DB_Chart.png)

Diese `ER` -Diagramm stellt die Beziehungen zwischen den Kerntabellen in einer Commerce-Datenbank dar. Indem Sie mehrere Beziehungen gleichzeitig anzeigen, können Sie sehen, wie sich Daten auf viele Tabellen beziehen würden.

Die folgenden Abschnitte enthalten `ER` Diagramme, die jeweils für zwei Tabellen spezifisch sind. Um ein Diagramm und die zugehörige Beschreibung anzuzeigen, klicken Sie auf die Kopfzeile für diesen Abschnitt.

## `customer\_entity & sales\_flat\_order`

![Ein Kunde, viele Bestellungen](../../assets/2_OneCustomerManyOrders.png)

Ein Kunde kann viele Bestellungen tätigen. Die Beziehung zwischen diesen beiden Tabellen ist `customer\_entity.entity\_id = sales\_flat\_order.customer\_id`

>[!IMPORTANT]
>
>`customer\_entity.entity\_id` ist nicht gleich `sales\_flat\_order.entity\_id`. Die erste kann als `customer\_id` und die zweite als `order\_id.` Weitere Informationen hierzu finden Sie im Abschnitt [`entity\_id` Abschnitt](https://support.magento.com/hc/en-us/articles/360016729951) der _[!DNL Magento]: Häufige Missverständnisse_ Artikel.

Within [!DNL MBI]Wenn der Pfad zwischen diesen beiden Tabellen noch nicht vorhanden ist, können Sie [Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, wird er wie folgt definiert:

![](../../assets/SFO___CE_path.png)

## `sales\_flat\_order & sales\_flat\_order\_item`

![1_OneOrderManyItems](../../assets/1_OneOrderManyItems.png)

Eine Bestellung kann viele Elemente enthalten. Die Beziehung zwischen diesen beiden Tabellen ist `sales\_flat\_order.entity\_id = sales\_flat\_order\_item.order\_id`.

Within [!DNL MBI]Wenn der Pfad zwischen diesen beiden Tabellen noch nicht vorhanden ist, können Sie [Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, wird er wie folgt definiert:

![](../../assets/SFOI___SFO_path.png)

## `catalog\_product\_entity & sales\_flat\_order\_item`

![3_OneProductManyTimes](../../assets/3_OneProductManyTimes.png)

Ein Produkt kann viele Artikel gekauft werden. Die Beziehung zwischen diesen beiden Tabellen ist `catalog\_product\_entity.entity\_id = sales\_flat\_order\_item.product`.

Within [!DNL MBI]Wenn der Pfad zwischen diesen beiden Tabellen noch nicht vorhanden ist, können Sie [Pfad erstellen](../data-warehouse-mgr/create-paths-calc-columns.md) auf der Registerkarte Data Warehouse . Wenn Sie bereit sind, den Pfad zu erstellen, wird er wie folgt definiert:

![](../../assets/SFOI___CPE_path.png)
