---
title: MBI Essentials vs. Pro
description: Erfahren Sie, wie sich MBI Essentials von MBI Pro unterscheidet.
exl-id: 624a6285-8497-43d9-a56d-8ae503e0e2dd
source-git-commit: 23177d8235987354e17cca72d753b5c4afa0dcc9
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 4%

---

# [!DNL MBI Essentials] vs [!DNL MBI Pro]

In der folgenden Tabelle werden die Elemente beschrieben, die in älteren Versionen enthalten sind `Essentials` -Konto und ein aktuelles MBI-Konto. Adobe bietet keine Angebote mehr an `Essentials`.

|  | **`MBI Essentials`** | **`MBI Pro`** |
|-----|-----|-----|
| `Pre-Defined Reports` | Bis zu 100 | Benutzerdefiniert |
| `Pre-Defined Dashboards` | 5-6 | Benutzerdefiniert |
| `New Custom Report Creation` | Ja | Ja |
| `Commerce Tables` | 4-6 | Unbegrenzt |
| `Log-ins/User Accounts` | 10 | 20 |
| `User Permissions` | Ja | Ja |
| `Data Warehouse Manager` | Nicht verfügbar | Verfügbar |
| `Email Reports` | Ja | Ja |
| `Cohort Report Builder` | Ja | Ja |
| `Google Analytics Live Integration` | Ja | Unbegrenzt |
| `3rd Party Integrations` | Nicht verfügbar | Verfügbar |
| `Full API Access` | Nein | Ja |
| `Access to CS, AM, or Analysts` | Nein | Ja |
| `Professional Services` | Verfügbar | Verfügbar |

{style="table-layout:auto"}

>[!NOTE]
>
>Die Anzahl der Tabellen hängt vom Checkout ab.

**Enthaltene Tabellen**

* `sales\_order`
* `sales\_order\_item`
* `sales\_order\_address`
* `customer\_entity`
* `customer\_group`
* `store`

## In Grundlagen enthaltene Spalten

Elemente in _kursiv_ sind berechnete Felder.

* `sales_order` table
   * `entity_id`
   * `base_grand_total`
   * `customer_id`
   * `status`
   * `customer_email`
   * `store_id`
   * `base_currency_code`
   * `billing_address_id`
   * `shipping_address_id`
   * `base_shipping_amount`
   * `base_tax_amount`
   * `coupon_code`
   * `created_at`
   * `updated_at`
   * `base_subtotal`
   * `customer_group_id`
   * `base_discount_amount`
   * `base_discount_invoiced`
   * `increment_id`
   * `Customer's order number`
   * `Customer's first order date`
   * `Customer's lifetime number of orders`
   * `Is customer's last order?`
   * `Billing address region`
   * `Shipping address country`
   * `Customer's lifetime revenue`
   * `Seconds between customer's first order date and this order`
   * `Seconds since previous order`
   * `Store name`
   * `Customer's lifetime number of coupons`
   * `Customer's order number (previous-current)`
   * `Shipping address region`
   * `Number of items in order`
   * `Billing address city`
   * `Shipping address city`
   * `Customer's group code`
   * `Customer's first order's billing region`
   * `Customer's first order's coupon_code`
   * `Customer's creation date`
   * `Billing address country`

* `sales_order_item` table
   * `item_id`
   * `qty_ordered`
   * `base_price`
   * `name`
   * `order_id`
   * `sku`
   * `product_type`
   * `product_id`
   * `created_at`
   * `updated_at`
   * `parent_item_id`
   * `store_id`
   * `base_discount_amount`
   * `base_discount_invoiced`
   * `Order's coupon_code`
   * `Order item total value (quantity * price)`
   * `Order's increment_id`
   * `Customer's email`
   * `Customer's lifetime number of orders`
   * `Store name`
   * `Customer's order number`
   * `Order's status`
   * `Customer's lifetime revenue`

* `sales_order_address` table
   * `entity_id`
   * `city`
   * `region`
   * `country_id`

* `customer_entity` table
   * `entity_id`
   * `email`
   * `group_id`
   * `created_at`
   * `updated_at`
   * `store_id`
   * `Customer's lifetime revenue`
   * `Customer's lifetime number of coupons`
   * `Customer's first order date`
   * `Customer's lifetime number of orders`
   * `Seconds since customer's first order date`
   * `Customer's first 30 day revenue`
   * `Customer's first order's billing region`
   * `Customer's first order's coupon_code`
   * `Customer's group code`
   * `Store name`

* `customer_group` table
   * `customer_group_id`
   * `customer_group_code`

* `store` table
   * `store_id`
   * `name`
