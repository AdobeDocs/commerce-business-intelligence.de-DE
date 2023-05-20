---
title: Marketing-ROI
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Kanalanalyse verfolgt - einschließlich ROI insgesamt und nach Kampagne.
exl-id: 5de83998-e6cf-478d-bb6a-7a3dc77c2c0c
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# Marketing-ROI

>[!NOTE]
>
>Dieses Thema enthält Anweisungen für Clients, die die ursprüngliche Architektur und die neue Architektur verwenden. Sie befinden sich auf der [neue Architektur](../../administrator/account-management/new-architecture.md) Wenn Sie den Bereich &quot;Datenansichten&quot;nach Auswahl von &quot;Data Warehousen verwalten&quot;in der Hauptsymbolleiste verfügbar haben.

Wenn Sie Geld für Online-Werbung ausgeben, möchten Sie Ihre Rendite aus diesen Ausgaben nachverfolgen und datenbasierte Entscheidungen über weitere Investitionen treffen. In diesem Thema erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Kanalanalyse verfolgt - einschließlich des ROI insgesamt und nach Kampagne.

![](../../assets/Marketing_dashboard_example.png)

Bevor Sie beginnen, möchten Sie Ihre [!DNL [Facebook Ads]](../importing-data/integrations/facebook-ads.md), [!DNL [Adwords]](../importing-data/integrations/google-adwords.md)und [!DNL [Google Ecommerce]](../importing-data/integrations/google-ecommerce.md) und fügen Sie zusätzliche Daten zu den Ausgaben für Online-Werbung hinzu. Diese Analyse enthält [Erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Konsolidierte Tabellen

**Originalarchitektur:** Zusammenführen Ihrer Ausgaben aus verschiedenen Quellen, z. B. [!DNL Facebook Ads] oder [!DNL Google Adwords]empfiehlt Adobe, eine **konsolidierte Tabelle** der Werbeausgaben. Sie benötigen einen Analysten, um diesen Schritt für Sie abzuschließen. Wenn nicht, [Support-Anfrage einreichen](../../guide-overview.md#Submitting-a-Support-Ticket) mit dem Betreff `[MARKETING ROI ANALYSIS]`, und ein Analytiker erstellt diese Tabelle.

**Neue Architektur:** Sie können dem Beispiel in [Diese Analysebibliothek](../../data-analyst/data-warehouse-mgr/create-dw-views.md) Thema. Konsolidierte Tabellen werden jetzt als Data Warehousen-Ansichten für die neue Architektur bezeichnet.

## Berechnete Spalten

Zu erstellende Spalten

* **`Consolidated Digital Ad Spend`** table
* **`Campaign name`** von einem Adobe Analyst als Teil Ihrer **[MARKETING-ROI-ANALYSE]** Ticket

**Originalarchitekturen und neue Architekturen:**

* **`sales_flat_order`** table
   * **`Order's GA campaign`**
      * Wählen Sie eine Definition aus: `Joined Column`
      * [!UICONTROL Create Path]:
      * 
         [!UICONTROL Many]: `sales_flat_order.increment_id`
      * 

         [!UICONTROL One]: `ecommerce####.transaction_id`

      * Wählen Sie eine [!UICONTROL table]: `ecommerce####`
      * Wählen Sie eine [!UICONTROL column]: `campaign`
      * [!UICONTROL Path]: `sales_flat_order.increment_id = ecommerce#####.transactionID`
   * **`Order's GA medium`**
      * Wählen Sie eine Definition aus: Verbundene Spalte
      * Wählen Sie eine [!UICONTROL table]: `ecommerce####`
      * Wählen Sie eine [!UICONTROL column]: `medium`
      * [!UICONTROL Path]: sales_flach_order.increment_id = ecommerce###.transactionId
   * **`Order's GA source`**
      * Wählen Sie eine Definition aus: Verbundene Spalte
      * Wählen Sie eine [!UICONTROL table]: `ecommerce####`
      * Wählen Sie eine [!UICONTROL column]: `source`
      * [!UICONTROL Path]: sales_flach_order.increment_id = ecommerce###.transactionId ^



* **`customer_entity`** table
* **`Customer's first order GA campaign`**
   * Wählen Sie eine Definition aus: `Max`
   * Wählen Sie eine [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie eine [!UICONTROL column]: `Order's GA campaign`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`Customer's first order GA source`**
   * Wählen Sie eine Definition aus: `Max`
   * Wählen Sie eine [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie eine [!UICONTROL column]: `Order's GA source`
   * [!UICONTROL Path]: sales_flach_order.customer_id = customer_entity.entity_id
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`Customer's first order GA medium`**
   * Wählen Sie eine Definition aus: `Max`
   * Wählen Sie eine [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie eine [!UICONTROL column]: `Order's GA medium`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`sales_flat_order`** table
* **`Customer's first order GA campaign`**
   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie eine [!UICONTROL table]: `customer_entity`
   * Wählen Sie eine [!UICONTROL column]: `Customer's first order GA campaign`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

* **`Customer's first order GA source`**
   * Wählen Sie eine Definition aus: Verbundene Spalte
   * Wählen Sie eine [!UICONTROL table]: `customer_entity`
   * Wählen Sie eine [!UICONTROL column]: `Customer's first order GA source`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

* **`Customer's first order GA medium`**
   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie eine [!UICONTROL table]: `customer_entity`
   * Wählen Sie eine [!UICONTROL column]: `Customer's first order GA medium`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

## Metriken

* **Werbeausgaben**
* Im **`Consolidated Digital Ad Spend`** table
* Diese Metrik führt eine **Summe**
* Im **`adCost`** column
* Bestellt von der **`date`** timestamp

* **Anzeigenimpressionen**
* Im **`Consolidated Digital Ad Spend`** table
* Diese Metrik führt eine **Summe**
* Im **`Impressions`** column
* Bestellt von der **`Month`** timestamp

* **Anzeigenklicks**
* Im **`Consolidated Digital Ad Spend`** table
* Diese Metrik führt eine **Summe**
* Im **`adClicks`** column
* Bestellt von der **`Month`** timestamp

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

## Berichte

* **Werbeausgaben (alle Zeit)**
   * [!UICONTROL Metric]: Werbeausgaben

* Metrik `A`: Werbeausgaben
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Intervall]: `None`
* 

   [!UICONTROL Chart Type]: `Scalar`

* **Akquise von Anzeigenkunden (alle Zeiten)**
   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]

* Metrik `A`: `Ad customer acquisitions`
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Intervall]: `None`
* 

   [!UICONTROL Chart Type]: `Scalar`

* **Anzeigen-ROI**
   * [!UICONTROL Metric]: Werbeausgaben

   * [!UICONTROL Metric]: `New customers`
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]
   * [!UICONTROL Metric]: Durchschnittlicher Umsatz während der Lebensdauer
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]
   * [!UICONTROL Formula]: `((C - (A / B)) / (A / B))`
   * 

      [!UICONTROL Format]: `Percentage`



* Metrik `A`: `Ad Spend (hide)`
* Metrik `B`: `Ad customer acquisitions (hide)`
* Metrik `C`: `Average LTV (hide)`
* [!UICONTROL Formula]: `Ads ROI`
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Intervall]: `None`
* 

   [!UICONTROL Chart Type]: `Scalar`

* **Bestellungen nach ga-Medium**
   * 

      [!UICONTROL Metrik]: `Orders`

* Metrik `A`: `Orders`
* [!UICONTROL Time period]: `All time`
* [!UICONTROL Interval]: `By Month`
* [!UICONTROL Group by]: `Order's medium`
* 

   [!UICONTROL Chart Type]: `Area`

* **Anzeigen-ROI nach Kampagne**
   * [!UICONTROL Metric]: `Ad Spend`

   * [!UICONTROL Metric]:`New customers`
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]
   * [!UICONTROL Metric]: Durchschnittlicher Umsatz während der Lebensdauer
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]
   * [!UICONTROL Metric]: Durchschnittliche Anzahl der Bestellungen über die Lebensdauer
   * [!UICONTROL Filters]:
      * `User's first order's source LIKE %google%`
      * `User's first order's source LIKE %facebook%`
      * `User's first order's source LIKE %fb%`
      * `User's first order's medium IN cpc, ppc`
      * Filterlogik: ([`A`] ODER [`B`] ODER [`C`]) UND [`D`]
   * [!UICONTROL Formula]: `(A / B)`
   * 

      [!UICONTROL Format]: `Currency`

   * [!UICONTROL Formula]: `(C - (A / B))`
   * 

      [!UICONTROL Format]: `Currency`

   * [!UICONTROL Formula]: `((C - (A / B)) / (A / B))`
   * 

      [!UICONTROL Format]: `Percentage`

   * [!UICONTROL Metric]: `Ad Clicks`

   * [!UICONTROL Metric]: `Ad Impressions`

   * [!UICONTROL Formula]: `(H / I)`
   * 

      [!UICONTROL Format]: `Percentage`

   * [!UICONTROL Formula]: `(A / H)`
   * 

      [!UICONTROL Format]: `Currency`




* Metrik `A`: `Ad Spend` (ausblenden)
* Metrik `B`: `Ad customer acquisitions`
* Metrik `C`: `Average LTV`
* Metrik `D`: `Average lifetime # of orders`
* 
   [!UICONTROL Formel]: `CAC`
* [!UICONTROL Formula]: `Avg return`
* [!UICONTROL Formula]: `Ads ROI`
* Metrik `H`: `adClicks`
* Metrik `I`: `Impressions`
* 
   [!UICONTROL Formel]: `CTR`
* 
   [!UICONTROL Formel]: `CPC`
* [!UICONTROL Time period]: `All time`
* 
   [!UICONTROL Intervall]: `None`
* 
   [!UICONTROL Gruppe von]: `campaign` (Verwenden der Kampagne &quot;Erstbestellung&quot;des Kunden für die Tabellenmetriken ohne Anzeigenausgaben)
* 

   [!UICONTROL Chart Type]: `Table`

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

### Verwandte

* [Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
* [Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../analysis/utm-attributes.md)
