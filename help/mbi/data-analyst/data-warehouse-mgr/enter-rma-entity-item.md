---
title: Enterprise_RMA_ITEM_ENTITY-Tabelle
description: Learn how to analyze information about a specific item from a requested return.
exl-id: aa71cb3f-3e0b-4b6b-b4cc-dad103f79c51
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/jBMtEluq3XNIzItebuvDQ43PAuW6mAsyG7RkHn8URJ4
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 269
ht-degree: 0%

---

# enterprise_rma_item_entity Table

Each row in the `enterprise_rma_item_entity` table (often called `magento_rma_item_entity` in Commerce 2.x, but the name can be customized) contains information about a specific item from a requested return.

>[!NOTE]
>
>This table only comes standard with your Commerce account if you are an `Enterprise Edition` or `Enterprise Cloud Edition` customer.

## Gemeinsame native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `entity\_id` | Eindeutige Kennung für die Tabelle. Jedes `entity\_id` stellt ein Element dar, das zur Rücksendung angefordert wurde. |
| `rma\_entity\_id` | Fremdschlüssel, der der `enterprise\_rma`-Tabelle zugeordnet ist. |
| `status` | Der Status der Rückgabe des Elements. Die Werte umfassen u. a. „Received“, „Pending“, „Authorized“. Die Werte in diesem Status stimmen möglicherweise nicht mit dem Wert des Gesamtrückgabestatus überein. |
| `qty\_requested` | The quantity the customer requests for return. |
| `qty\_approved` | The quantity approved for return. |
| `qty\_returned` | The quantity returned. |
| `order\_item\_id` | Fremdschlüssel, der der `sales\_flat\_order\_item`-Tabelle zugeordnet ist. |
| `product\_sku` | Die SKU wird zurückgegeben. |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Return date\_requested` | Dies ist das Datum, an dem der Kunde die Rücksendung angefordert hat. |
| `Item price` | Der Preis des Artikels. |
| `Return item's total value (qty\_returned * price)` | Dies ist der gesamte Geldwert der zurückgegebenen Artikel. This is used to calculate the total return amount on the `enterprise\_rma` table. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Number of items returned` | Die Anzahl der zurückgegebenen Elemente. | Vorgangsspalte: Zurückgegebene Menge<br>Vorgang: Summe<br>Zeitstempel Spalte: Rückgabedatum angefordert |
| `Returned items' total value` | Der zurückgegebene Geldbetrag. | Vorgangsspalte: Gesamtwert des Rückgabeelements (zurückgegebene Menge * Preis)<br>Vorgang: Summe<br>Zeitstempel Spalte: Rückgabedatum angefordert |

{style="table-layout:auto"}

## Verbindungen zu anderen Tabellen

`enterprise_rma`

* Create joined columns such as `Return date\_requested` on the `enterprise_rma_item_entity` table via the following join:
* Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id ` (viele) => `enterprise_rma.entity_id` (eine)
* Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eine)

`sales_flat_order_item`

* Create joined columns on the  `enterprise_rma_item_entity` table via the following join:

* Commerce 1.x: `enterprise_rma_item_entity.order_item_id ` (viele) => `sales_flat_order_item.item_id` (eine)
* Commerce 2.x: `magento_rma_item_entity.order_item_id ` (viele) => `sales_order_item.item_id` (eine)
