---
title: Enterprise_RMA_ITEM_ENTITY-Tabelle
description: Erfahren Sie, wie Sie Informationen zu einem bestimmten Element aus einer angeforderten Rücksendung analysieren können.
exl-id: aa71cb3f-3e0b-4b6b-b4cc-dad103f79c51
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '269'
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
| `entity\_id` | Eindeutige Kennung für die Tabelle. Jedes `entity\_id` stellt ein Element dar, das zur Rücksendung angefordert wurde. |
| `rma\_entity\_id` | Fremdschlüssel, der der `enterprise\_rma`-Tabelle zugeordnet ist. |
| `status` | Der Status der Rückgabe des Elements. Die Werte umfassen u. a. „Received“, „Pending“, „Authorized“. Die Werte in diesem Status stimmen möglicherweise nicht mit dem Wert des Gesamtrückgabestatus überein. |
| `qty\_requested` | Die Menge, die der Kunde für die Rücksendung anfordert. |
| `qty\_approved` | Die für die Rücksendung genehmigte Menge. |
| `qty\_returned` | Die zurückgegebene Menge. |
| `order\_item\_id` | Fremdschlüssel, der der `sales\_flat\_order\_item`-Tabelle zugeordnet ist. |
| `product\_sku` | Die SKU wird zurückgegeben. |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Return date\_requested` | Dies ist das Datum, an dem der Kunde die Rücksendung angefordert hat. |
| `Item price` | Der Preis des Artikels. |
| `Return item's total value (qty\_returned * price)` | Dies ist der gesamte Geldwert der zurückgegebenen Artikel. Dies wird zur Berechnung des Gesamtrenditebetrags für die `enterprise\_rma` verwendet. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Number of items returned` | Die Anzahl der zurückgegebenen Elemente. | Vorgangsspalte: Zurückgegebene Menge<br>Vorgang: Summe<br>Zeitstempel Spalte: Rückgabedatum angefordert |
| `Returned items' total value` | Der zurückgegebene Geldbetrag. | Vorgangsspalte: Gesamtwert des Rückgabeelements (zurückgegebene Menge * Preis)<br>Vorgang: Summe<br>Zeitstempel Spalte: Rückgabedatum angefordert |

{style="table-layout:auto"}

## Verbindungen zu anderen Tabellen

`enterprise_rma`

* Erstellen Sie verknüpfte Spalten wie `Return date\_requested` in der `enterprise_rma_item_entity` mithilfe des folgenden Joins:
* Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id ` (viele) => `enterprise_rma.entity_id` (eine)
* Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eine)

`sales_flat_order_item`

* Erstellen von verbundenen Spalten auf dem  Tabelle über folgenden Join `enterprise_rma_item_entity`:

* Commerce 1.x: `enterprise_rma_item_entity.order_item_id ` (viele) => `sales_flat_order_item.item_id` (eine)
* Commerce 2.x: `magento_rma_item_entity.order_item_id ` (viele) => `sales_order_item.item_id` (eine)
