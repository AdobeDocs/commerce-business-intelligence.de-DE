---
title: Enterprise_RMA_ITEM_ENTITY-Tabelle
description: Erfahren Sie, wie Sie Informationen zu einem bestimmten Element aus einer angeforderten Rücksendung analysieren können.
exl-id: aa71cb3f-3e0b-4b6b-b4cc-dad103f79c51
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/jBMtEluq3XNIzItebuvDQ43PAuW6mAsyG7RkHn8URJ4
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 08a466710b782238003c6bdb8cefacd07134291c
workflow-type: tm+mt
source-wordcount: 271
ht-degree: 0%

---

# enterprise_rma_item_entity-Tabelle

Jede Zeile in der `enterprise_rma_item_entity` (in Commerce 2.x häufig als `magento_rma_item_entity` bezeichnet, der Name kann jedoch angepasst werden) enthält Informationen zu einem bestimmten Element aus einer angeforderten Rückgabe.

>[!NOTE]
>
>Diese Tabelle wird nur dann standardmäßig mit Ihrem Commerce-Konto geliefert, wenn Sie `Enterprise Edition` oder `Enterprise Cloud Edition` sind.

## Gemeinsame native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `entity_id` | Eindeutige Kennung für die Tabelle. Jedes `entity_id` stellt ein Element dar, das zur Rücksendung angefordert wurde. |
| `rma_entity_id` | Fremdschlüssel, der der `enterprise_rma`-Tabelle zugeordnet ist. |
| `status` | Der Status der Rückgabe des Elements. Die Werte umfassen u. a. „Received“, „Pending“, „Authorized“. Die Werte in diesem Status stimmen möglicherweise nicht mit dem Wert des Gesamtrückgabestatus überein. |
| `qty_requested` | Die Menge, die der Kunde für die Rücksendung anfordert. |
| `qty_approved` | Die für die Rücksendung genehmigte Menge. |
| `qty_returned` | Die zurückgegebene Menge. |
| `order_item_id` | Fremdschlüssel, der der `sales_flat_order_item`-Tabelle zugeordnet ist. |
| `product_sku` | Die SKU wird zurückgegeben. |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Return date_requested` | Dies ist das Datum, an dem der Kunde die Rücksendung angefordert hat. |
| `Item price` | Der Preis des Artikels. |
| `Return item's total value (qty_returned * price)` | Dies ist der gesamte Geldwert der zurückgegebenen Artikel. Dies wird zur Berechnung des Gesamtrenditebetrags für die `enterprise_rma` verwendet. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Number of items returned` | Die Anzahl der zurückgegebenen Elemente. | Vorgangsspalte: Zurückgegebene Menge<br>Vorgang: Summe<br>Zeitstempel Spalte: Rückgabedatum angefordert |
| `Returned items' total value` | Der zurückgegebene Geldbetrag. | Vorgangsspalte: Gesamtwert des Rückgabeelements (zurückgegebene Menge * Preis)<br>Vorgang: Summe<br>Zeitstempel Spalte: Rückgabedatum angefordert |

{style="table-layout:auto"}

## Verbindungen zu anderen Tabellen

`enterprise_rma`

* Erstellen Sie verknüpfte Spalten wie `Return date_requested` in der `enterprise_rma_item_entity` mithilfe des folgenden Joins:
* Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id ` (viele) => `enterprise_rma.entity_id` (eine)
* Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eine)

`sales_flat_order_item`

* Erstellen Sie verknüpfte Spalten in der `enterprise_rma_item_entity`-Tabelle über den folgenden Join:

* Commerce 1.x: `enterprise_rma_item_entity.order_item_id ` (viele) => `sales_flat_order_item.item_id` (eine)
* Commerce 2.x: `magento_rma_item_entity.order_item_id ` (viele) => `sales_order_item.item_id` (eine)
