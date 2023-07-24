---
title: quote_item-Tabelle
description: Erfahren Sie, wie Sie mit der Tabelle "quote_item"arbeiten.
exl-id: dad36e88-5986-4b52-8a0e-ac084fabb275
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# quote_item-Tabelle

Die `quote_item` table (`sales_flat_quote_item` auf M1) enthält Datensätze zu jedem Artikel, der einem Warenkorb hinzugefügt wird, unabhängig davon, ob der Warenkorb abgebrochen oder in einen Kauf umgewandelt wurde. Jede Zeile stellt ein Warenkorbelement dar. Aufgrund der potenziellen Größe dieser Tabelle empfiehlt Adobe, Datensätze regelmäßig zu löschen, wenn bestimmte Kriterien erfüllt sind, z. B. wenn nicht konvertierte Warenkörbe älter als 60 Tage sind.

>[!NOTE]
>
>Die Analyse von historischen, abgebrochenen Warenkörben ist nur möglich, wenn Sie keine Datensätze aus dem `quote` und `quote_item` Tabelle. Wenn Sie Datensätze löschen, können Sie nur die noch nicht aus Ihrer Datenbank entfernten Warenkörbe sehen.

## Allgemeine native Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `base_price` | Preis einer einzelnen Einheit eines Produkts zum Zeitpunkt der Hinzufügung des Artikels zum Warenkorb nach [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) werden angewendet und bevor Steuern, Versand- oder Warenkorbrabatte angewendet werden. Dies wird in der Basiswährung des Stores dargestellt. |
| `created_at` | Erstellungszeitstempel des Warenkorbelements, lokal in UTC gespeichert. Abhängig von Ihrer Konfiguration in [!DNL Commerce Intelligence], kann dieser Zeitstempel in eine Berichtszeitzone in [!DNL Commerce Intelligence] , die sich von der Zeitzone Ihrer Datenbank unterscheidet |
| `item_id` (PK) | Eindeutige Kennung für die Tabelle |
| `name` | Textname des Bestellelements |
| `parent_item_id` | `Foreign key` , das ein einfaches Produkt mit seinem übergeordneten Bundle oder konfigurierbaren Produkt verknüpft. Mitglied werden `quote_item.item_id` , um übergeordnete Produktattribute zu bestimmen, die mit einem einfachen Produkt verknüpft sind. Bei übergeordneten Warenkorbelementen (d. h. Bundle oder konfigurierbare Produktarten) muss die `parent_item_id` is `NULL` |
| `product_id` | `Foreign key` mit `catalog_product_entity` Tabelle. Mitglied werden `catalog_product_entity.entity_id` zur Bestimmung der Produktattribute, die mit dem Bestellelement verknüpft sind |
| `product_type` | Typ des Produkts, das dem Warenkorb hinzugefügt wurde. Potenzial [Produkttypen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html#product-types) include: einfach, konfigurierbar, gruppiert, virtuell, gebündelt und herunterladbar |
| `qty` | Menge der Einheiten, die im Warenkorb für den betreffenden Warenkorb enthalten sind |
| `quote_id` | `Foreign key` mit `quote` Tabelle. Mitglied werden `quote.entity_id` zur Bestimmung der mit dem Warenkorbelement verknüpften Warenkorbattribute |
| `sku` | Eindeutige Kennung für das Warenkorbelement |
| `store_id` | Fremdschlüssel, der mit dem `store` Tabelle. Mitglied werden `store.store_id` , um zu bestimmen, welche Commerce Store-Ansicht mit dem Warenkorbelement verknüpft ist |

{style="table-layout:auto"}

## Allgemeine berechnete Spalten

| **Spaltenname** | **Beschreibung** |
|---|---|
| `Cart creation date` | Zeitstempel, der mit dem Erstellungsdatum des Warenkorbs verknüpft ist. Errechnet durch Verbinden `quote_item.quote_id` nach `quote.entity_id` und die `created_at` timestamp |
| `Cart is active? (1/0)` | Boolesches Feld, das &quot;1&quot;zurückgibt, wenn der Warenkorb von einem Kunden erstellt wurde und noch nicht in eine Bestellung konvertiert wurde. Gibt &quot;0&quot;für konvertierte Warenkörbe oder Warenkörbe zurück, die vom Administrator erstellt wurden. Errechnet durch Verbinden `quote_item.quote_id` nach `quote.entity_id` und die `is_active` field |
| `Cart item total value (qty * base_price)` | Gesamtwert eines Artikels zum Zeitpunkt der Hinzufügung des Artikels zum Warenkorb nach [Katalogpreisregeln, gestaffelte Rabatte und Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) werden angewendet und bevor Steuern, Versand- oder Warenkorbrabatte angewendet werden. Wird durch Multiplikation der `qty` durch `base_price` |
| `Seconds since cart creation` | Verstrichene Zeit zwischen dem Erstellungsdatum des Warenkorbs und jetzt. Errechnet durch Verbinden `quote_item.quote_id` nach `quote.entity_id` und die `Seconds since cart creation` field |
| `Store name` | Name des Commerce-Stores, der mit dem Bestellelement verknüpft ist. Errechnet durch Verbinden `sales_order_item.store_id` nach `store.store_id` und die `name` field |

{style="table-layout:auto"}

## Allgemeine Metriken

| **Metrikname** | **Beschreibung** | **Bauwesen** |
|---|---|---|
| `Number of abandoned cart items` | Gesamtzahl der zum Warenkorb hinzugefügten Artikel, die bestimmte &quot;Abbruch&quot;-Bedingungen erfüllen | `Operation: Sum`<br/>`Operand: qty`<br/>`Timestamp: Cart creation date`<br>Filter:<br><br>- \[`A`\] `Cart is active? (1/0)` = 1<br>- \[`B`\] `Seconds since cart creation` > x, wobei &quot;x&quot;der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als abgebrochen gilt |
| `Abandoned cart item value` | Summe des Gesamtumsatzes, der mit Warenkörben verbunden ist, die bestimmte Bedingungen für den Abbruch erfüllen | `Operation: Sum`<br>`Operand: Cart item total value (qty * base_price)`<br>`Timestamp:` `Cart creation date`<br>Filter:<br><br>- \[`A`\] `Cart is active? (1/0)` = 1<br>- \[`B`\] `Seconds since cart creation` > x, wobei &quot;x&quot;der verstrichenen Zeit (in Sekunden) seit der Erstellung des Warenkorbs entspricht, ab der ein Warenkorb als abgebrochen gilt |

{style="table-layout:auto"}

## Verbindungswege für Fremdschlüssel

`catalog_product_entity`

* Mitglied werden `catalog_product_entity` -Tabelle verwenden, um Spalten zu erstellen, die mit dem Warenkorbelement verknüpfte Produktattribute zurückgeben.
   * Pfad: `quote_item.product_id` (viele) => `catalog_product_entity.entity_id` (eins)

`quote`

* Mitglied werden `quote` , um neue Spalten auf Warenkorbebene zu erstellen, die mit dem Warenkorbelement verknüpft sind.
   * Pfad: `quote_item.quote_id` (viele) => `quote.entity_id` (eins)

`quote_item`

* Mitglied werden `quote_item` , um Spalten zu erstellen, die Details der übergeordneten konfigurierbaren oder Bundle-SKU mit dem einfachen Produkt verknüpfen. [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) Hilfe bei der Konfiguration dieser Berechnungen, wenn sie im Data Warehousen-Manager erstellt werden.
   * Pfad: `quote_item.parent_item_id` (viele) => `quote_item.item_id` (eins)

`store`

* Mitglied werden `store` -Tabelle verwenden, um Spalten zu erstellen, die Details zum Commerce-Store zurückgeben, der mit dem Warenkorbelement verknüpft ist.
   * Pfad: `quote_item.store_id` (viele) => `store.store_id` (eins)
