---
title: Tabelle quote_item
description: Erfahren Sie, wie Sie mit der Tabelle quote_item arbeiten.
exl-id: dad36e88-5986-4b52-8a0e-ac084fabb275
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/wLNm1g1L6-0Ded-bZT991KvJi3dVO6zA4i2qftiX2J0
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 686
ht-degree: 0%

---

# quote_item-Tabelle

Die `quote_item` Tabelle (`sales_flat_quote_item` auf M1) enthält Datensätze zu jedem Artikel, der einem Warenkorb hinzugefügt wurde, unabhängig davon, ob der Warenkorb abgebrochen oder in einen Kauf umgewandelt wurde. Jede Zeile stellt ein Warenkorbelement dar. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind.

>[!NOTE]
>
>Die Analyse historischer, Transaktionsabbrüche ist nur möglich, wenn Sie keine Datensätze aus der `quote`- und `quote_item` löschen. Wenn Sie Datensätze löschen, können Sie nur die noch nicht aus Ihrer Datenbank entfernten Warenkörbe sehen.

## Gemeinsame native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_price` | Preis einer einzelnen Einheit eines Produkts zum Zeitpunkt, als der Artikel zum Warenkorb hinzugefügt wurde, nach [Katalogpreisregeln, gestaffelten Rabatten und Sonderpreisen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) und bevor Steuern, Versand oder Warenkorbabschläge angewendet werden. Dies wird in der Basiswährung des Stores dargestellt. |
| `created_at` | Erstellungszeitstempel des Warenkorbelements, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence] kann dieser Zeitstempel in eine Berichtszeitzone umgewandelt werden, [!DNL Commerce Intelligence] sich von Ihrer Datenbankzeitzone unterscheidet |
| `item_id` (K) | Eindeutige Kennung der Tabelle |
| `name` | Textname des Bestellartikels |
| `parent_item_id` | `Foreign key`, das ein einfaches Produkt auf sein übergeordnetes Bundle oder konfigurierbares Produkt bezieht. Join-`quote_item.item_id`, um übergeordnete Produktattribute zu bestimmen, die mit einem einfachen Produkt verknüpft sind. Für übergeordnete Warenkorbartikel (d. h. Bundle oder konfigurierbare Produkttypen) wird der `parent_item_id` `NULL` |
| `product_id` | Der `catalog_product_entity` Tabelle zugeordnete `Foreign key` Mit `catalog_product_entity.entity_id` verbinden, um Produktattribute zu bestimmen, die mit dem Auftragselement verknüpft sind |
| `product_type` | Typ des Produkts, das dem Warenkorb hinzugefügt wurde. Mögliche [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) sind: einfach, konfigurierbar, gruppiert, virtuell, gebündelt und herunterladbar |
| `qty` | Menge der im Warenkorb enthaltenen Einheiten für den jeweiligen Warenkorbartikel |
| `quote_id` | Der `quote` Tabelle zugeordnete `Foreign key` Join to `quote.entity_id`, um die mit dem Warenkorbelement verknüpften Warenkorbattribute zu bestimmen |
| `sku` | Eindeutige Kennung für den Artikel im Warenkorb |
| `store_id` | Fremdschlüssel, der der `store`-Tabelle zugeordnet ist. Join to `store.store_id`, um zu bestimmen, welche Commerce-Store-Ansicht mit dem Warenkorbelement verknüpft ist |

{style="table-layout:auto"}

## Gemeinsame berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Cart creation date` | Zeitstempel, der mit dem Erstellungsdatum des Warenkorbs verknüpft ist. Berechnet durch Verbinden von `quote_item.quote_id` mit `quote.entity_id` und Zurückgeben des `created_at` Zeitstempels |
| `Cart is active? (1/0)` | Boolesches Feld, das „1“ zurückgibt, wenn der Warenkorb von einem Kunden erstellt wurde und noch nicht in eine Bestellung konvertiert wurde. Gibt „0“ für konvertierte Warenkörbe oder Warenkörbe zurück, die über den Administrator erstellt wurden. Berechnet durch Verbinden von `quote_item.quote_id` mit `quote.entity_id` und Zurückgeben des `is_active` |
| `Cart item total value (qty * base_price)` | Gesamtwert eines Artikels zum Zeitpunkt der Hinzufügung des Artikels zu einem Warenkorb, nachdem [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) angewendet wurden und bevor Steuern, Versand oder Warenkorbabschläge angewendet wurden. Berechnet durch Multiplizieren des `qty` mit dem `base_price` |
| `Seconds since cart creation` | Verstrichene Zeit zwischen dem Erstellungsdatum des Warenkorbs und jetzt. Berechnet durch Verbinden von `quote_item.quote_id` mit `quote.entity_id` und Zurückgeben des `Seconds since cart creation` |
| `Store name` | Name des Commerce-Stores, der mit dem Auftragselement verknüpft ist. Berechnet durch Verbinden von `sales_order_item.store_id` mit `store.store_id` und Zurückgeben des `name` |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Baugewerbe** |
|---|---|---|
| `Number of abandoned cart items` | Gesamtmenge der Artikel, die zum Warenkorb hinzugefügt wurden und bestimmte Bedingungen für den „Abbruch“ erfüllen | `Operation: Sum`<br/>`Operand: qty`<br/>`Timestamp: Cart creation date`<br>Filter:<br><br>- \[`A`\] `Cart is active? (1/0)` = 1<br>- \[`B`\] `Seconds since cart creation` > x, wobei „x“ der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als verlassen gilt |
| `Abandoned cart item value` | Summe des Gesamtumsatzes, der mit Warenkörben verbunden ist, die bestimmte Bedingungen für einen „Abbruch“ erfüllen | `Operation: Sum`<br>`Operand: Cart item total value (qty * base_price)`<br>`Timestamp:` `Cart creation date`<br>Filter:<br><br>- \[`A`\] `Cart is active? (1/0)` = 1<br>- \[`B`\] `Seconds since cart creation` > x, wobei „x“ der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als verlassen gilt |

{style="table-layout:auto"}

## Fremdschlüssel-Verknüpfungspfade

`catalog_product_entity`

* Mit `catalog_product_entity` Tabelle verbinden, um Spalten zu erstellen, die Produktattribute zurückgeben, die mit dem Warenkorbelement verknüpft sind.
   * Pfad: `quote_item.product_id` (viele) => `catalog_product_entity.entity_id` (eins)

`quote`

* Mit `quote` Tabelle verbinden, um neue Spalten auf Warenkorbebene zu erstellen, die mit dem Warenkorbelement verknüpft sind.
   * Pfad: `quote_item.quote_id` (viele) => `quote.entity_id` (eins)

`quote_item`

* Verbinden Sie sich mit `quote_item` , um Spalten zu erstellen, die Details der übergeordneten konfigurierbaren oder Bundle-SKU mit dem einfachen Produkt verknüpfen. [Wenden Sie sich an den &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um Hilfe bei der Konfiguration dieser Berechnungen zu erhalten, falls Sie etwas in Data Warehouse Manager erstellen.
   * Pfad: `quote_item.parent_item_id` (viele) => `quote_item.item_id` (eins)

`store`

* Join `store` Tabelle, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Warenkorbelement verknüpft ist.
   * Pfad: `quote_item.store_id` (viele) => `store.store_id` (eins)
