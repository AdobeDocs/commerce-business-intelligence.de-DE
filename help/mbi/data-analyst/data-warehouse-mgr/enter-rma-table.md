---
title: Tabelle enterprise_rma
description: Erfahren Sie, wie Sie Informationen zu einer bestimmten Rückgabeanfrage analysieren können.
exl-id: a19cbc9a-e34f-4f4e-820f-9e413d1a552d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Tabelle enterprise_rma

Jede Zeile in der `enterprise_rma` (in Adobe Commerce 2.x häufig als `magento_rma` bezeichnet, der Name kann jedoch angepasst werden) enthält Informationen zu einer bestimmten Rückgabeanfrage.

>[!NOTE]
>
>Diese Tabelle wird nur dann standardmäßig mit Ihrem Adobe Commerce-Konto geliefert, wenn Sie `Enterprise Edition` oder `Enterprise Cloud Edition` sind.

## Gemeinsame native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `entity\_id` | Eindeutige Kennung für die Tabelle. Jede `entity\_id` stellt eine Rückgabeanfrage dar. |
| `date\_requested` | Das Datum, an dem die Rückgabe angefordert wurde. |
| `status` | Der Status der Rücksendung. Die Werte umfassen u. a. „Received“, „Pending“, „Authorized“. |
| `order\_id` | Fremdschlüssel, der der `sales\_flat\_order`-Tabelle zugeordnet ist. |
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
| `Number of returns` | Die Anzahl der angeforderten Rücksendungen. | `Operation`: `entity id`<br>`Operation`: `Count`<br>`Timestamp` Spalte: `date requested` |
| `Total returned amount` | Der insgesamt zurückgegebene Geldbetrag. | `Operation `Spalte: `Return's total value`<br>`Operation`: Summe<br>`Timestamp` Spalte: angefordertes Datum |
| `Average returned amount` | Der durchschnittliche zurückgegebene Geldbetrag. | `Operation`` Column: Return's total value`<br>`Operation`: `Average`<br>`Timestamp` Spalte: `date requested` |
| `Average time to return` | Die durchschnittliche Zeit von der Bestellung bis zur Rückkehr. | `Operation` Spalte: Sekunden zwischen dem Erstellungsdatum des Auftrags und dem Rückgabedatum der Anforderung<br>`Operation`: `Average`<br>`Timestamp` Spalte: `date requested` |

{style="table-layout:auto"}

## Verbindungen zu anderen Tabellen

`sale_flat_order`

* Erstellen Sie verknüpfte Spalten, um mithilfe der folgenden Verknüpfung zu segmentieren und nach Attributen auf Auftragsebene in der `enterprise_rma`-Tabelle zu filtern:
   * Commerce 1.x: `enterprise_rma.order_id` (viele) => `sales_flat_order.entity_id` (eine)
   * Commerce 2.x: `magento_rma.order_id` (viele) => `sales_order.entity_id` (eine)

`enterprise_rma_item_entity`

* Erstellen Sie Viele-zu-eins-Spalten wie `Return's total value` in der `enterprise_rma`-Tabelle über den folgenden Join:
   * Commerce 1.x: `enterprise_rma_item_entity.rma_entity_id` (viele) => `enterprise_rma.entity_id` (eine)
   * Commerce 2.x: `magento_rma_item_entity.rma_entity_id ` (viele) => `magento_rma.entity_id` (eine)
