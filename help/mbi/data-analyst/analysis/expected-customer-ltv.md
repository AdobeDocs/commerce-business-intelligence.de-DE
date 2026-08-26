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
source-git-commit: 02934da4962380494ab8a2becf5f06efb15d84dc
workflow-type: tm+mt
source-wordcount: 540
ht-degree: 38%

---

# Analyse des erwarteten Lebenszeitwerts

Dieses Thema zeigt, wie Sie ein Dashboard einrichten, das Ihnen hilft, das Wachstum des Kundenlebenszeitwerts und den erwarteten Lebenszeitwert Ihrer Kunden zu verstehen.

![Dashboard zur Analyse des erwarteten Lebenszeitwerts mit Prognosen zum Kundenwert](../../assets/exp-lifetim-value-anyalysis.png)

Diese Analyse steht nur Pro Account Kunden mit der neuen Architektur zur Verfügung. Wenn Ihr Konto Zugriff auf die `Persistent Views` in der `Manage Data` Seitenleiste hat, befinden Sie sich auf der neuen Architektur und können die hier aufgeführten Anweisungen befolgen, um diese Analyse selbst zu erstellen.

Bevor Sie beginnen, sollten Sie sich mit dem &quot;[&#x200B; Report Builder“ vertraut machen](../dev-reports/cohort-rpt-bldr.md)

## Berechnete Spalten

In der Tabelle **Bestellungen** zu erstellende Spalten bei Verwendung von **30-Tage-Monaten**:

* [!UICONTROL Column name]&#x200B;: `Months between first order and this order`
* [!UICONTROL Column type]&#x200B;: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]&#x200B;: `CALCULATION`
* [!UICONTROL Column input]: A = `Seconds between customer's first order date and this order`
* &#x200B;
  [!UICONTROL Datatype]&#x200B;: `Integer`
* **Definition:**`case when A is null then null when A <= 0 then '1'::int else (ceil(A)/2629800)::int end`

* [!UICONTROL Column name]&#x200B;: `Months since order`
* [!UICONTROL Column type]&#x200B;: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]&#x200B;: `CALCULATION`
* [!UICONTROL Column input]: A = `created_at`
* &#x200B;
  [!UICONTROL Datatype]&#x200B;: `Integer`
* Definition `case when created_at is null then null else (ceil((extract(epoch from current_timestamp) - extract(epoch from created_at))/2629800))::int end`

In der **`orders`** zu erstellende Spalten bei Verwendung von **Kalender** Monaten:

* [!UICONTROL Column name]&#x200B;: `Calendar months between first order and this order`
* [!UICONTROL Column type]&#x200B;: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]&#x200B;: `CALCULATION`
* [!UICONTROL Column inputs]:
  * `A` = `created_at`
  * `B` = `Customer's first order date`

* &#x200B;
  [!UICONTROL Datatype]&#x200B;: `Integer`
* Definition `case when (A::date is null) or (B::date is null) then null else ((date_part('year',A::date) - date_part('year',B::date))*12 + date_part('month',A::date) - date_part('month',B::date))::int end`

* [!UICONTROL Column name]&#x200B;: `Calendar months since order`
* [!UICONTROL Column type]&#x200B;: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]&#x200B;: `CALCULATION`
* [!UICONTROL Column input]: `A` = `created_at`
* &#x200B;
  [!UICONTROL Datatype]&#x200B;: `Integer`
* **Definition:**`case when A is null then null else ((date_part('year',current_timestamp::date) - date_part('year',A::date))*12 + date_part('month',current_timestamp::date) - date_part('month',A::date))::int end`

* [!UICONTROL Column name]&#x200B;: `Is in current month? (Yes/No)`
* [!UICONTROL Column type]&#x200B;: `Same Table`
* &#x200B;
  [!UICONTROL Column equation]&#x200B;: `CALCULATION`
* [!UICONTROL Column input]: A = `created_at`
* &#x200B;
  [!UICONTROL Datatype]&#x200B;: `String`
* Definition `case when A is null then null when (date_trunc('month', current_timestamp::date))::varchar = (date_trunc('month', A::date))::varchar then 'Yes' else 'No' end`

## Metriken

### Anweisungen zur Metrik

Zu erstellende Metriken

* **Unterschiedliche Kunden nach Datum der ersten Bestellung**
  * Wenn Sie Gastbestellungen aktivieren, verwenden Sie `customer_email`

* In der **`orders`**
* Diese Metrik führt eine **Anzahl unterschiedlicher Werte**
* In der Spalte **`customer_id`**
* Sortiert nach dem **`Customer's first order date`** Zeitstempel

>[!NOTE]
>
>Stellen Sie sicher[&#x200B; dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

## Berichte

### Berichtsanweisungen

**Erwarteter Umsatz pro Kunde und Monat**

* `A`: `Revenue (hide)`
  * `Calendar months between first order and this order` `<= X` (Wählen Sie eine vernünftige Zahl für X, z. B. 24 Monate)
  * `Is in current month?` = `No`

* &#x200B;
  [!UICONTROL -Metrik]&#x200B;: `Revenue`
* [!UICONTROL Filter]:

* `B`: `All time customers (hide)`
  * `Is in current month?` = `No`

* [!UICONTROL Metric]&#x200B;: `New customers by first order date`
* [!UICONTROL Filter]:

* `C`: `All time customers by month since first order (hide)`
  * `Calendar months since order` `<= X`
  * `Is in current month?` = `No`

* [!UICONTROL Metric]&#x200B;: `New customers by first order date`
* [!UICONTROL Filter]:

* [!UICONTROL Formula]&#x200B;: `Expected revenue`
* [!UICONTROL Formula]&#x200B;: `A / (B - C)`
* &#x200B;
  [!UICONTROL Format]&#x200B;: `Currency`

Weitere Diagrammdetails

* [!UICONTROL Time period]&#x200B;: `All time`
* Zeitintervall: `None`
* [!UICONTROL Group by]: `Calendar months between first order and this order` - Alle anzeigen
* Ändern Sie mithilfe des Stiftsymbols neben dem `group by` die `group by` für die `All time customers` Metrik in „Unabhängig“
* Bearbeiten Sie die `Show top/bottom` wie folgt:
  * [!UICONTROL Revenue]&#x200B;: `Top 24 sorted by Calendar months between first order and this order`
  * [!UICONTROL All time customers]&#x200B;: `Top 24 sorted by All time customers`
  * [!UICONTROL All time customers by month since first order]&#x200B;: `Top 24 sorted by All time customers by month since first order`

**Durchschnittlicher Umsatz pro Monat nach Kohorte**

* `A`: `Revenue`
* &#x200B;
  [!UICONTROL Metric view]&#x200B;: `Cohort`
* [!UICONTROL Cohort date]&#x200B;: `Customer's first order date`
* [!UICONTROL Perspective]&#x200B;: `Average value per cohort member`

**Kumulativer durchschnittlicher Umsatz pro Monat nach Kohorte**

* `A`: `Revenue`
* &#x200B;
  [!UICONTROL Metric view]&#x200B;: `Cohort`
* [!UICONTROL Cohort date]&#x200B;: `Customer's first order date`
* [!UICONTROL Perspective]&#x200B;: `Cumulative average value per cohort member`

Nachdem Sie alle Berichte kompiliert haben, können Sie sie im Dashboard nach Bedarf organisieren. Das Ergebnis kann wie das Bild oben auf der Seite aussehen.

Wenn Sie beim Erstellen dieser Analyse auf Fragen stoßen oder einfach das Professional Services-Team kontaktieren möchten, wenden [&#x200B; sich an den Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies).
