---
title: Analyse des erwarteten Lebensdauerwerts (LTV) für Pro
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das Ihnen hilft, das Wachstum des Kundenlebenszeitwerts und den erwarteten Lebenszeitwert Ihrer Kunden zu verstehen.
exl-id: e353b92a-ff3b-466b-b519-4f86d054c0bc
role: Admin, User
feature: Data Warehouse Manager, Reports, Dashboards
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4e01225a6bd285afbe988b9c24e07e2ea34649fc
workflow-type: tm+mt
source-wordcount: 318
ht-degree: 0%

---

# Analyse des erwarteten Lebenszeitwerts

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Ihnen hilft, das Wachstum des Kundenlebenszeitwerts und den erwarteten Lebenszeitwert Ihrer Kunden zu verstehen.

![Dashboard zur Analyse des erwarteten Lebenszeitwerts mit Prognosen zum Kundenwert](../../assets/exp-lifetim-value-anyalysis.png)

Diese Analyse steht nur Pro Account Kunden mit der neuen Architektur zur Verfügung. Wenn Ihr Konto Zugriff auf die `Persistent Views` in der `Manage Data` Seitenleiste hat, befinden Sie sich auf der neuen Architektur und können die hier aufgeführten Anweisungen befolgen, um diese Analyse selbst zu erstellen.

Bevor Sie beginnen, sollten Sie sich mit dem &quot;[&#x200B; Report Builder“ vertraut machen](../dev-reports/cohort-rpt-bldr.md)

## Berechnete Spalten

In der Tabelle **Bestellungen** zu erstellende Spalten bei Verwendung von **30-Tage-Monaten**:

* [!UICONTROL Column name]: `Months between first order and this order`
* [!UICONTROL Column type]: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]: `CALCULATION`
* [!UICONTROL Column input]: A = `Seconds between customer's first order date and this order`
* &#x200B;
  [!UICONTROL Datatype]: `Integer`
* **Definition:**`case when A is null then null when A <= 0 then '1'::int else (ceil(A)/2629800)::int end`

* [!UICONTROL Column name]: `Months since order`
* [!UICONTROL Column type]: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]: `CALCULATION`
* [!UICONTROL Column input]: A = `created_at`
* &#x200B;
  [!UICONTROL Datatype]: `Integer`
* Definition `case when created_at is null then null else (ceil((extract(epoch from current_timestamp) - extract(epoch from created_at))/2629800))::int end`

In der **`orders`** zu erstellende Spalten bei Verwendung von **Kalender** Monaten:

* [!UICONTROL Column name]: `Calendar months between first order and this order`
* [!UICONTROL Column type]: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]: `CALCULATION`
* [!UICONTROL Column inputs]:
   * `A` = `created_at`
   * `B` = `Customer's first order date`

* &#x200B;
  [!UICONTROL Datatype]: `Integer`
* Definition `case when (A::date is null) or (B::date is null) then null else ((date_part('year',A::date) - date_part('year',B::date))*12 + date_part('month',A::date) - date_part('month',B::date))::int end`

* [!UICONTROL Column name]: `Calendar months since order`
* [!UICONTROL Column type]: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]: `CALCULATION`
* [!UICONTROL Column input]: `A` = `created_at`
* &#x200B;
  [!UICONTROL Datatype]: `Integer`
* **Definition:**`case when A is null then null else ((date_part('year',current_timestamp::date) - date_part('year',A::date))*12 + date_part('month',current_timestamp::date) - date_part('month',A::date))::int end`

* [!UICONTROL Column name]: `Is in current month? (Yes/No)`
* [!UICONTROL Column type]: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]: `CALCULATION`
* [!UICONTROL Column input]: A = `created_at`
* &#x200B;
  [!UICONTROL Datatype]: `String`
* Definition `case when A is null then null when (date_trunc('month', current_timestamp::date))::varchar = (date_trunc('month', A::date))::varchar then 'Yes' else 'No' end`

## Metriken

### Metric instructions

Metrics to create

* **Distinct customers by first order date**
   * Wenn Sie Gastbestellungen aktivieren, verwenden Sie `customer_email`

* In der **`orders`**
* This metric performs a **Count Distinct Values**
* On the **`customer_id`** column
* Ordered by the **`Customer's first order date`** timestamp

>[!NOTE]
>
>Make sure to [add all new columns as dimensions to metrics](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) before building new reports.

## Berichte

### Berichtsanweisungen

**Erwarteter Umsatz pro Kunde und Monat**

* `A`: `Revenue (hide)`
   * `Calendar months between first order and this order` `<= X` (Wählen Sie eine vernünftige Zahl für X, z. B. 24 Monate)
   * `Is in current month?` = `No`

* &#x200B;
  [!UICONTROL Metric]: `Revenue`
* [!UICONTROL Filter]:

* `B`: `All time customers (hide)`
   * `Is in current month?` = `No`

* [!UICONTROL Metric]: `New customers by first order date`
* [!UICONTROL Filter]:

* `C`: `All time customers by month since first order (hide)`
   * `Calendar months since order` `<= X`
   * `Is in current month?` = `No`

* [!UICONTROL Metric]: `New customers by first order date`
* [!UICONTROL Filter]:

* [!UICONTROL Formula]: `Expected revenue`
* [!UICONTROL Formula]: `A / (B - C)`
* &#x200B;
  [!UICONTROL Format]: `Currency`

Weitere Diagrammdetails

* [!UICONTROL Time period]: `All time`
* Zeitintervall: `None`
* [!UICONTROL Group by]: `Calendar months between first order and this order` - Alle anzeigen
* Ändern Sie mithilfe des Stiftsymbols neben dem `group by` die `All time customers` für die `group by` Metrik in „Unabhängig“
* Bearbeiten Sie die `Show top/bottom` wie folgt:
   * [!UICONTROL Revenue]: `Top 24 sorted by Calendar months between first order and this order`
   * [!UICONTROL All time customers]: `Top 24 sorted by All time customers`
   * [!UICONTROL All time customers by month since first order]: `Top 24 sorted by All time customers by month since first order`

**Avg revenue per month by cohort**

* `A`: `Revenue`
* &#x200B;
  [!UICONTROL Metric view]: `Cohort`
* [!UICONTROL Cohort date]: `Customer's first order date`
* [!UICONTROL Perspective]: `Average value per cohort member`

**Cumulative avg revenue per month by cohort**

* `A`: `Revenue`
* &#x200B;
  [!UICONTROL Metric view]: `Cohort`
* [!UICONTROL Cohort date]: `Customer's first order date`
* [!UICONTROL Perspective]: `Cumulative average value per cohort member`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. The result may look like the image at the top of the page.

If you run into any questions while building this analysis, or simply want to engage the Professional Services team, [contact support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
