---
title: Marketing-ROI
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Kanalanalyse verfolgt - einschließlich ROI insgesamt und nach Kampagne.
exl-id: 5de83998-e6cf-478d-bb6a-7a3dc77c2c0c
role: Admin,  User
feature: Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Marketing-ROI

>[!NOTE]
>
>Dieses Thema enthält Anweisungen für Clients, die die ursprüngliche Architektur und die neue Architektur verwenden. Sie befinden sich in der [neuen Architektur](../../administrator/account-management/new-architecture.md), wenn der Bereich &quot;Data Warehouse-Ansichten&quot;nach Auswahl von &quot;Daten verwalten&quot;in der Hauptsymbolleiste verfügbar ist.

Wenn Sie Geld für Online-Werbung ausgeben, möchten Sie Ihre Rendite aus diesen Ausgaben nachverfolgen und datenbasierte Entscheidungen über weitere Investitionen treffen. In diesem Thema erfahren Sie, wie Sie ein Dashboard einrichten, das Ihre Kanalanalyse verfolgt - einschließlich des ROI insgesamt und nach Kampagne.

![](../../assets/Marketing_dashboard_example.png)

Bevor Sie beginnen, möchten Sie Ihre [!DNL [Facebook Ads]](../importing-data/integrations/facebook-ads.md)-, [!DNL [Adwords]](../importing-data/integrations/google-adwords.md)- und [!DNL [Google Ecommerce]](../importing-data/integrations/google-ecommerce.md)-Konten verbinden und zusätzliche Daten zu den Werbeausgaben im Internet einbringen. Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Konsolidierte Tabellen

**Ursprüngliche Architektur:** Um Ihre Ausgaben aus verschiedenen Quellen wie [!DNL Facebook Ads] oder [!DNL Google Adwords] zusammenzuführen, empfiehlt Adobe, eine **konsolidierte Tabelle** aller Werbeausgaben zu erstellen. Sie benötigen einen Analysten, um diesen Schritt für Sie abzuschließen. Ist dies nicht der Fall, reichen Sie [eine Supportanfrage ](../../guide-overview.md#Submitting-a-Support-Ticket) mit dem Betreff `[MARKETING ROI ANALYSIS]` ein, und ein Analyst erstellt diese Tabelle.

**Neue Architektur:** Sie können dem Beispiel in [diesem Thema der Analysebibliothek](../../data-analyst/data-warehouse-mgr/create-dw-views.md) folgen. Konsolidierte Tabellen werden jetzt als Data Warehouse-Ansichten in der neuen Architektur bezeichnet.

## Berechnete Spalten

Zu erstellende Spalten

* **`Consolidated Digital Ad Spend`** table
* **`Campaign name`** wird von einem Adobe-Analyst im Rahmen Ihres **[MARKETING ROI ANALYSIS]**-Tickets erstellt

**Ursprüngliche und neue Architekturen:**

* **`sales_flat_order`** table
   * **`Order's GA campaign`**
      * Wählen Sie eine Definition aus: `Joined Column`
      * [!UICONTROL Create Path]:
      * 
        [!UICONTROL Many]: `sales_flat_order.increment_id`
      * 
        [!UICONTROL One]: `ecommerce####.transaction_id`

      * Wählen Sie einen [!UICONTROL table]: `ecommerce####`
      * Wählen Sie einen [!UICONTROL column]: `campaign`
      * [!UICONTROL Path]: `sales_flat_order.increment_id = ecommerce#####.transactionID`

   * **`Order's GA medium`**
      * Definition auswählen: Verbundene Spalte
      * Wählen Sie einen [!UICONTROL table]: `ecommerce####`
      * Wählen Sie einen [!UICONTROL column]: `medium`
      * [!UICONTROL Path]: sales_flach_order.Increment_id = ecommerce###.transactionId

   * **`Order's GA source`**
      * Definition auswählen: Verbundene Spalte
      * Wählen Sie einen [!UICONTROL table]: `ecommerce####`
      * Wählen Sie einen [!UICONTROL column]: `source`
      * [!UICONTROL Path]: sales_flach_order.Increment_id = ecommerce###.transactionId
^

* **`customer_entity`** table
* **`Customer's first order GA campaign`**
   * Wählen Sie eine Definition aus: `Max`
   * Wählen Sie einen [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie einen [!UICONTROL column]: `Order's GA campaign`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`Customer's first order GA source`**
   * Wählen Sie eine Definition aus: `Max`
   * Wählen Sie einen [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie einen [!UICONTROL column]: `Order's GA source`
   * [!UICONTROL Path]: sales_flach_order.customer_id = customer_entity.entity_id
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`Customer's first order GA medium`**
   * Wählen Sie eine Definition aus: `Max`
   * Wählen Sie einen [!UICONTROL table]: `sales_flat_order`
   * Wählen Sie einen [!UICONTROL column]: `Order's GA medium`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`
   * [!UICONTROL Filter]:
      * `Orders we count`
      * `Customer's order number = 1`

* **`sales_flat_order`** table
* **`Customer's first order GA campaign`**
   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie einen [!UICONTROL table]: `customer_entity`
   * Wählen Sie einen [!UICONTROL column]: `Customer's first order GA campaign`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

* **`Customer's first order GA source`**
   * Definition auswählen: Verbundene Spalte
   * Wählen Sie einen [!UICONTROL table]: `customer_entity`
   * Wählen Sie einen [!UICONTROL column]: `Customer's first order GA source`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

* **`Customer's first order GA medium`**
   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie einen [!UICONTROL table]: `customer_entity`
   * Wählen Sie einen [!UICONTROL column]: `Customer's first order GA medium`
   * [!UICONTROL Path]: `sales_flat_order.customer_id = customer_entity.entity_id`

## Metriken

* **Werbeausgaben**
* In der Tabelle **`Consolidated Digital Ad Spend`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`adCost`**
* Durch den Zeitstempel **`date`** geordnet

* **Anzeigenimpressionen**
* In der Tabelle **`Consolidated Digital Ad Spend`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`Impressions`**
* Durch den Zeitstempel **`Month`** geordnet

* **Anzeigenklicks**
* In der Tabelle **`Consolidated Digital Ad Spend`**
* Diese Metrik führt eine **Summe** aus.
* In der Spalte **`adClicks`**
* Durch den Zeitstempel **`Month`** geordnet

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

## Berichte

* **Werbeausgaben (ganze Zeit)**
   * [!UICONTROL Metric]: Werbeausgaben

* Metrik `A`: Anzeigenausgaben
* [!UICONTROL Time period]: `All time`
* 
  [!UICONTROL Intervall]: `None`
* 
  [!UICONTROL Chart Type]: `Scalar`

* **Akquise von Anzeigenkunden (immer)**
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

* **Bestellungen nach ga medium**
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

   * [!UICONTROL Metric]: Durchschnittliche Anzahl der Bestellungen während der Lebensdauer
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

Wenn Sie beim Erstellen dieser Analyse Fragen haben oder einfach das Professional Services-Team kontaktieren möchten, wenden Sie sich an den Support [.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)

### Verwandte

* [Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
* [Wie funktioniert die  [!DNL Google Analytics] UTM-Attribution?](../analysis/utm-attributes.md)
