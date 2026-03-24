---
title: Tabelle enterprise_rma
description: Learn how to analyze information about a specific return request.
exl-id: a19cbc9a-e34f-4f4e-820f-9e413d1a552d
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/ofPlk5xNr8aspjFlpzEtDtjcOPm9DrQFYX9-vPDfK6w
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 267
ht-degree: 0%

---

# Tabelle enterprise_rma

Each row in the `enterprise_rma` table (often called `magento_rma` in Adobe Commerce 2.x, but the name can be customized) contains information about a specific return request.

>[!NOTE]
>
>This table only comes standard with your Adobe Commerce account if you are an `Enterprise Edition` or `Enterprise Cloud Edition` customer.

## Gemeinsame native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `entity\_id` | Eindeutige Kennung für die Tabelle. Jede `entity\_id` stellt eine Rückgabeanfrage dar. |
| `date\_requested` | Das Datum, an dem die Rückgabe angefordert wurde. |
| `status` | Der Status der Rücksendung. Die Werte umfassen u. a. „Received“, „Pending“, „Authorized“. |
| `order\_id` | Foreign key associated with the `sales\_flat\_order` table. |
| `customer\_id` | Fremdschlüssel, der der `customer\_entity`-Tabelle zugeordnet ist. |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Order's created\_at` | Dies ist das Datum der ursprünglichen Bestellung. Dies kann verwendet werden, um die Zeit zwischen der Bestellung und der Rücksendung zu ermitteln. |
| `Customer's order number` | Dies ist die Bestellnummer des Kunden, die mit der ursprünglichen Bestellung verknüpft ist. |
| `Seconds between order's created\_at and return's date\_requested` | Die Anzahl der Sekunden vom Bestelldatum bis zur Rückgabeanfrage. |
| `Return's total value` | Dies ist der gesamte Geldbetrag, der zurückgegeben wird. Dies ist die Summe des individuellen Rücksendungsbetrags jedes einzelnen Rücksendungspostens. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Number of returns` | The number of returns requested. | `Operation`: `entity id`<br>`Operation`: `Count`<br>`Timestamp` Spalte: `date requested` |
| `Total returned amount` | Der insgesamt zurückgegebene Geldbetrag. | `Operation `Spalte: `Return's total value`<br>`Operation`: Summe<br>`Timestamp` Spalte: angefordertes Datum |
| `Average returned amount` | Der durchschnittliche zurückgegebene Geldbetrag. | `Operation`` Column: Return's total value`<br>`Operation`: `Average`<br>`Timestamp` Spalte: `date requested` |
| `Average time to return` | Die durchschnittliche Zeit von der Bestellung bis zur Rückkehr. | `Operation` Column: Seconds between order&#39;s created at and return&#39;s date requested<br>`Operation`: `Average`<br>`Timestamp` Column: `date requested` |

{style="table-layout:auto"}

## Connections to Other Tables

`sale_flat_order`

* Create joined columns to segment and filter by order-level attributes on the `enterprise_rma` table via the following join:
   * Commerce 1.x: `enterprise_rma.order_id` (viele) => `sales_flat_order.entity_id` (eine)
   * Commerce 2.x: `magento_rma.order_id` (viele) => `sales_order.entity_id` (eine)

`enterprise_rma_item_entity`

* Erstellen Sie Viele-zu-eins-Spalten wie `Return's total value` in der `enterprise_rma`-Tabelle über den folgenden Join:
   * Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id` (viele) => `enterprise_rma.entity_id` (eine)
   * Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eine)
