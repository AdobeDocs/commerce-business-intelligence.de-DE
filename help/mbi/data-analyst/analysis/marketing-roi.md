---
title: Marketing-ROI
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Kanalanalyse verfolgt - einschließlich des ROI insgesamt und nach Kampagne.
exl-id: 5de83998-e6cf-478d-bb6a-7a3dc77c2c0c
role: Admin,  User
feature: Reports, Dashboards
TQID: https://experienceleague.adobe.com/TJ0KsU551M5PkQcY-Ic0PuExtC9SCkO0MhZGdHL4N6g
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 529
ht-degree: 0%

---

# Marketing-ROI

>[!NOTE]
>
>Dieses Thema enthält Anweisungen für Clients, die die ursprüngliche und die neue Architektur verwenden. Sie befinden sich auf der [neuen Architektur](../../administrator/account-management/new-architecture.md), wenn Sie den Abschnitt &quot;Data Warehouse-Ansichten“ verfügbar haben, nachdem Sie in der Hauptsymbolleiste „Daten verwalten“ ausgewählt haben.

Wenn Sie Geld für Online-Werbung ausgeben, möchten Sie Ihre Rendite auf diese Ausgaben verfolgen und datengestützte Entscheidungen über weitere Investitionen treffen. Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Ihre Kanalanalyse verfolgt - einschließlich des ROI insgesamt und nach Kampagne.

![Marketing-Dashboard mit ROI-Metriken und Kampagnenleistung](../../assets/Marketing_dashboard_example.png)

Bevor Sie beginnen, sollten Sie Ihre [[!DNL [Facebook Ads]]](../importing-data/integrations/facebook-ads.md)-, [[!DNL [Adwords]]](../importing-data/integrations/google-adwords.md)- und [[!DNL [Google Ecommerce]]](../importing-data/integrations/google-ecommerce.md)-Konten verbinden und alle zusätzlichen Online-Daten zu Werbeausgaben einbringen. Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Konsolidierte Tabellen

**Ursprüngliche Architektur:** Um Ihre Ausgaben aus verschiedenen Quellen wie [!DNL Facebook Ads] oder [!DNL Google Adwords] zusammenzuführen, empfiehlt Adobe die Erstellung **konsolidierten Tabelle** aller Ihrer Werbeausgaben. Sie benötigen einen Analysten, um diesen Schritt für Sie auszuführen. Andernfalls reichen Sie [eine Support-Anfrage](../../guide-overview.md#Submitting-a-Support-Ticket) mit dem `[MARKETING ROI ANALYSIS]` ein, und ein Analyst erstellt diese Tabelle.

**Neue Architektur:** Sie können dem Beispiel in [diesem Analysis Library](../../data-analyst/data-warehouse-mgr/create-dw-views.md)-Thema folgen. Konsolidierte Tabellen werden jetzt mit der neuen Architektur als Data Warehouse-Ansichten bezeichnet.

## Berechnete Spalten

Zu erstellende Spalten

* **`Consolidated Digital Ad Spend`**
* **`Campaign name`** wird von einem Adobe-Analysten im Rahmen Ihres **[MARKETING ROI ANALYSIS]** Tickets erstellt

**Originale und neue Architekturen:**

* **`sales_flat_order`**
   * **`Order's GA campaign`**
      * Definition auswählen: `Joined Column`
      * [!UICONTROL Create Path]:
      * &#x200B;
        [!UICONTROL Many]: `sales_flat_order.increment_id`
      * &#x200B;
        [!UICONTROL One]: `ecommerce####.transaction_id`

      * [!UICONTROL table] auswählen: `ecommerce####`
      * [!UICONTROL column] auswählen: `campaign`
      * [!UICONTROL Path]: `sales_flat_order.increment_id = ecommerce#####.transactionID`

   * **`Order's GA medium`**
      * Definition auswählen: Verbundene Spalte
      * [!UICONTROL table] auswählen: `ecommerce####`
      * [!UICONTROL column] auswählen: `medium`
      * [!UICONTROL Path]: sales_flat_order.increment_id = eCommerce######.transactionId

   * **`Order's GA source`**
      * Definition auswählen: Verbundene Spalte
      * [!UICONTROL table] auswählen: `ecommerce####`
      * [!UICONTROL column] auswählen: `source`
      * [!UICONTROL Path]: sales_flat_order.increment_id = eCommerce######.transactionId
^

* **`customer_entity`**
* **`Customer's first order GA campaign`**
   * Definition auswählen: `Max`
   * [!UICONTROL table] auswählen: `sales_flat_order`
   * [!UICONTROL column] auswählen: `Order's GA campaign`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`Customer's first order GA source`**
   * Definition auswählen: `Max`
   * [!UICONTROL table] auswählen: `sales_flat_order`
   * [!UICONTROL column] auswählen: `Order's GA source`
   * [!UICONTROL Path]: sales_flat_order.customer_id = customer_entity.entity_id
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`Customer's first order GA medium`**
   * Definition auswählen: `Max`
   * [!UICONTROL table] auswählen: `sales_flat_order`
   * [!UICONTROL column] auswählen: `Order's GA medium`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`sales_flat_order`**
* **`Customer's first order GA campaign`**
   * Definition auswählen: `Joined Column`
   * [!UICONTROL table] auswählen: `customer_entity`
   * [!UICONTROL column] auswählen: `Customer's first order GA campaign`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

* **`Customer's first order GA source`**
   * Definition auswählen: Verbundene Spalte
   * [!UICONTROL table] auswählen: `customer_entity`
   * [!UICONTROL column] auswählen: `Customer's first order GA source`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

* **`Customer's first order GA medium`**
   * Definition auswählen: `Joined Column`
   * [!UICONTROL table] auswählen: `customer_entity`
   * [!UICONTROL column] auswählen: `Customer's first order GA medium`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

## Metriken

* **Werbeausgaben**
* In der **`Consolidated Digital Ad Spend`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`adCost`**
* Sortiert nach dem **`date`** Zeitstempel

* **Anzeigen-Impressions**
* In der **`Consolidated Digital Ad Spend`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`Impressions`**
* Sortiert nach dem **`Month`** Zeitstempel

* **Anzeigenklicks**
* In der **`Consolidated Digital Ad Spend`**
* Diese Metrik führt eine **Summe“**
* In der Spalte **`adClicks`**
* Sortiert nach dem **`Month`** Zeitstempel

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

* **Werbeausgaben (alle Zeiten)**
   * [!UICONTROL Metric]: Werbeausgaben

* `A`: Werbeausgaben
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* &#x200B;
  [!UICONTROL Chart Type]: `Scalar`

* **Kundenakquise hinzufügen (jederzeit)**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

* `A`: `Ad customer acquisitions`
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* &#x200B;
  [!UICONTROL Chart Type]: `Scalar`

* **Ad ROI**
   * [!UICONTROL Metric]: Werbeausgaben

   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

   * [!UICONTROL Metric]: Durchschnittlicher Lebensdauerumsatz
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

   * [!UICONTROL Formula]: `((C - (A / B)) / (A / B))`
   * &#x200B;
     [!UICONTROL Format]: `Percentage`

* `A`: `Ad Spend (hide)`
* `B`: `Ad customer acquisitions (hide)`
* `C`: `Average LTV (hide)`
* [!UICONTROL Formula]: `Ads ROI`
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* &#x200B;
  [!UICONTROL Chart Type]: `Scalar`

* **Bestellungen nach GA-Medium**
   * &#x200B;
     [!UICONTROL -Metrik]: `Orders`

* `A`: `Orders`
* [!UICONTROL Time period]: `All time`
* [!UICONTROL Interval]: `By Month`
* [!UICONTROL Group by]: `Order's medium`
* &#x200B;
  [!UICONTROL Chart Type]: `Area`

* **Anzeige-ROI nach Kampagne**
   * [!UICONTROL Metric]: `Ad Spend`

   * [!UICONTROL Metric]:`New customers`
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

   * [!UICONTROL Metric]: Durchschnittlicher Lebensdauerumsatz
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

   * [!UICONTROL Metric]: Durchschnittliche Anzahl der Bestellungen während der gesamten Lebensdauer
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

   * [!UICONTROL Formula]: `(A / B)`
   * &#x200B;
     [!UICONTROL Format]: `Currency`

   * [!UICONTROL Formula]: `(C - (A / B))`
   * &#x200B;
     [!UICONTROL Format]: `Currency`

   * [!UICONTROL Formula]: `((C - (A / B)) / (A / B))`
   * &#x200B;
     [!UICONTROL Format]: `Percentage`

   * [!UICONTROL Metric]: `Ad Clicks`

   * [!UICONTROL Metric]: `Ad Impressions`

   * [!UICONTROL Formula]: `(H / I)`
   * &#x200B;
     [!UICONTROL Format]: `Percentage`

   * [!UICONTROL Formula]: `(A / H)`
   * &#x200B;
     [!UICONTROL Format]: `Currency`

* `A`: `Ad Spend` (ausblenden)
* `B`: `Ad customer acquisitions`
* `C`: `Average LTV`
* `D`: `Average lifetime # of orders`
* &#x200B;
  [!UICONTROL -Formel]: `CAC`
* [!UICONTROL Formula]: `Avg return`
* [!UICONTROL Formula]: `Ads ROI`
* `H`: `adClicks`
* `I`: `Impressions`
* &#x200B;
  [!UICONTROL -Formel]: `CTR`
* &#x200B;
  [!UICONTROL -Formel]: `CPC`
* [!UICONTROL Time period]: `All time`
* &#x200B;
  [!UICONTROL Intervall]: `None`
* &#x200B;
  [!UICONTROL Gruppieren nach]: `campaign` (Verwenden der Kampagne „Erster Auftrag des Kunden“ für Nicht-Anzeigen-Ausgabentabellen-Metriken)
* &#x200B;
  [!UICONTROL Chart Type]: `Table`

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [&#x200B; sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

### verwandt

* [Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
* [Wie funktioniert  [!DNL Google Analytics]  UTM-Attribution?](../analysis/utm-attributes.md)
