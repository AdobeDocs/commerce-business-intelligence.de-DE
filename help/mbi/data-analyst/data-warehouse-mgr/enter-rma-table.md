---
title: enterprise_rma-Tabelle
description: Erfahren Sie, wie Sie Informationen zu einer bestimmten Rückgabeanforderung analysieren.
exl-id: a19cbc9a-e34f-4f4e-820f-9e413d1a552d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# enterprise_rma-Tabelle

Jede Zeile in der Tabelle `enterprise_rma` (in Adobe Commerce 2.x häufig als `magento_rma` bezeichnet, der Name kann jedoch angepasst werden) enthält Informationen zu einer bestimmten Rückgabeanforderung.

>[!NOTE]
>
>Diese Tabelle ist nur mit Ihrem Adobe Commerce-Konto standardmäßig verfügbar, wenn Sie `Enterprise Edition`- oder `Enterprise Cloud Edition`-Kunde sind.

## Allgemeine native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `entity\_id` | Eindeutige Kennung für die Tabelle. Jede `entity\_id` stellt eine Rückgabeanforderung dar. |
| `date\_requested` | Das Datum, an dem die Rückgabe angefordert wurde. |
| `status` | Der Status der Rückgabe. Zu den Werten gehören u. a. &quot;empfangen&quot;, &quot;ausstehend&quot;, &quot;autorisiert&quot;. |
| `order\_id` | Fremdschlüssel, der mit der Tabelle `sales\_flat\_order` verknüpft ist. |
| `customer\_id` | Fremdschlüssel, der mit der Tabelle `customer\_entity` verknüpft ist. |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Order's created\_at` | Dies ist das Datum der ursprünglichen Bestellung. Dies kann verwendet werden, um die Zeit zwischen Bestellung und Rückgabeanforderung zu erhalten. |
| `Customer's order number` | Dies ist die Auftragsnummer des Kunden, die der ursprünglichen Bestellung zugeordnet ist. |
| `Seconds between order's created\_at and return's date\_requested` | Die Anzahl der Sekunden vom Bestelldatum bis zur Rückgabeanforderung. |
| `Return's total value` | Dies ist der gesamte Geldbetrag, der zurückgegeben wird. Dies ist die Summe des individuellen Rückgabebetrags jedes Rückgabeelements. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Konstruktion** |
|---|---|---|
| `Number of returns` | Die Anzahl der angeforderten Rückgaben. | `Operation` column: `entity id`<br>`Operation`: `Count`<br>`Timestamp` column: `date requested` |
| `Total returned amount` | Der insgesamt zurückgegebene Geldbetrag. | `Operation `Spalte: `Return's total value`<br>`Operation`: Summe<br>`Timestamp` Spalte: Datum angefordert |
| `Average returned amount` | Der durchschnittliche Geldbetrag, der zurückgegeben wurde. | `Operation`` Column: Return's total value`<br>`Operation`: `Average`<br>`Timestamp` Spalte: `date requested` |
| `Average time to return` | Die durchschnittliche Zeit zwischen Bestellung und Rückgabe. | `Operation` Spalte: Sekunden zwischen der am erstellten Bestellung und dem angeforderten Datum der Rückgabe<br>`Operation`: `Average`<br>`Timestamp` Spalte: `date requested` |

{style="table-layout:auto"}

## Verbindungen zu anderen Tabellen

`sale_flat_order`

* Erstellen Sie verbundene Spalten, um mithilfe des folgenden Joins nach Attributen auf Bestellebene in der Tabelle `enterprise_rma` zu segmentieren und zu filtern:
   * Commerce 1.x: `enterprise_rma.order_id` (viele) => `sales_flat_order.entity_id` (eins)
   * Commerce 2.x: `magento_rma.order_id` (viele) => `sales_order.entity_id` (eins)

`enterprise_rma_item_entity`

* Erstellen Sie mit dem folgenden Join eine n:n-Spalte wie `Return's total value` auf der Tabelle `enterprise_rma`:
   * Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id` (viele) => `enterprise_rma.entity_id` (eins)
   * Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eins)
