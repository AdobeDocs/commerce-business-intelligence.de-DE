---
title: Enterprise_Rma_Item_Entity-Tabelle
description: Erfahren Sie, wie Sie Informationen zu einem bestimmten Element aus einer angeforderten Rückgabe analysieren.
exl-id: aa71cb3f-3e0b-4b6b-b4cc-dad103f79c51
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# enterprise_rma_item_entity_table

Jede Zeile im `enterprise_rma_item_entity` Tabelle (häufig `magento_rma_item_entity` in Commerce 2.x, aber der Name kann angepasst werden) enthält Informationen zu einem bestimmten Element aus einer angeforderten Rückgabe.

>[!NOTE]
>
>Diese Tabelle ist nur dann standardmäßig in Ihrem Commerce-Konto enthalten, wenn Sie `Enterprise Edition` oder `Enterprise Cloud Edition` -Kunden.

## Allgemeine native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `entity\_id` | Eindeutige Kennung für die Tabelle. Jeder `entity\_id` stellt ein Element dar, das zur Rückgabe angefordert wurde. |
| `rma\_entity\_id` | Fremdschlüssel, der mit dem `enterprise\_rma` Tabelle. |
| `status` | Der Status der Rückgabe des Elements. Zu den Werten gehören u. a. &quot;empfangen&quot;, &quot;ausstehend&quot;, &quot;autorisiert&quot;. Die Werte in diesem Status stimmen möglicherweise nicht mit dem Wert des Status des Gesamt-Trackings überein. |
| `qty\_requested` | Die Menge, die der Kunde zur Rückgabe anfordert. |
| `qty\_approved` | Die zur Rückgabe genehmigte Menge. |
| `qty\_returned` | Die zurückgegebene Menge. |
| `order\_item\_id` | Fremdschlüssel, der mit dem `sales\_flat\_order\_item` Tabelle. |
| `product\_sku` | Die Sku, die zurückgegeben wird. |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Return date\_requested` | Dies ist das Datum, an dem der Kunde die Rückgabe angefordert hat. |
| `Item price` | Der Preis des Artikels. |
| `Return item's total value (qty\_returned * price)` | Dies ist der Gesamtgeldwert der zurückgegebenen Elemente. Dies wird verwendet, um die Gesamtrendite für die `enterprise\_rma` Tabelle. |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Number of items returned` | Die Anzahl der zurückgegebenen Elemente. | Vorgangsspalte: zurückgegebene qty<br>Vorgang: Summe<br>Zeitstempelspalte: Rückkehrtermin angefordert |
| `Returned items' total value` | Der zurückgegebene Geldbetrag. | Vorgangsspalte: Gesamtwert des Rückkehrartikels (zurückgegebene Menge * Preis)<br>Vorgang: Summe<br>Zeitstempelspalte: Rückkehrtermin angefordert |

{style="table-layout:auto"}

## Verbindungen zu anderen Tabellen

`enterprise_rma`

* Erstellen Sie verbundene Spalten wie `Return date\_requested` auf `enterprise_rma_item_entity` -Tabelle über den folgenden Join:
* Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id ` (viele) => `enterprise_rma.entity_id` (eins)
* Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eins)

`sales_flat_order_item`

* Erstellen Sie verbundene Spalten auf der Seite  `enterprise_rma_item_entity` -Tabelle über den folgenden Join:

* Commerce 1.x: `enterprise_rma_item_entity.order_item_id ` (viele) => `sales_flat_order_item.item_id` (eins)
* Commerce 2.x: `magento_rma_item_entity.order_item_id ` (viele) => `sales_order_item.item_id` (eins)
