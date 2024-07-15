---
title: Schwelle für kostenlosen Versand
description: Erfahren Sie, wie Sie ein Dashboard einrichten, das die Leistung Ihrer Schwelle für den kostenlosen Versand verfolgt.
exl-id: a90ad89b-96d3-41f4-bfc4-f8c223957113
role: Admin,  User
feature: Data Warehouse Manager, Dashboards, Reports
source-git-commit: 6bdbdbcc652d476fa2a22589ac99678d5855e6fe
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Kostenloser Versand

>[!NOTE]
>
>Dieses Thema enthält Anweisungen für Clients, die die ursprüngliche Architektur und die neue Architektur verwenden. Sie befinden sich in der neuen Architektur, wenn der Abschnitt `Data Warehouse Views` nach Auswahl von `Manage Data` in der Hauptsymbolleiste verfügbar ist.

In diesem Thema erfahren Sie, wie Sie ein Dashboard einrichten, das die Leistung Ihrer Schwelle für den kostenlosen Versand verfolgt. Dieses Dashboard, wie unten gezeigt, eignet sich hervorragend zum A/B-Test von zwei kostenlosen Versandschwellen. Ihr Unternehmen kann beispielsweise unsicher sein, ob Sie kostenlosen Versand zu 50 US-Dollar oder 100 US-Dollar anbieten sollten. Sie sollten einen A/B-Test mit zwei zufälligen Untergruppen Ihrer Kunden durchführen und die Analyse in [!DNL Commerce Intelligence] durchführen.

Bevor Sie beginnen, möchten Sie zwei separate Zeiträume identifizieren, in denen Sie unterschiedliche Werte für die Schwelle für den kostenlosen Versand in Ihrem Geschäft hatten.

![](../../assets/free_shipping_threshold.png)

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Berechnete Spalten

Wenn Sie sich in der ursprünglichen Architektur befinden (z. B. wenn Sie die Option `Data Warehouse Views` unter dem Menü `Manage Data` nicht haben), wenden Sie sich an das Supportteam, um die folgenden Spalten zu erstellen. In der neuen Architektur können diese Spalten über die Seite `Manage Data > Data Warehouse` erstellt werden. Im Folgenden finden Sie ausführliche Anweisungen.

* **`sales_flat_order`** table
   * Diese Berechnung erstellt Behälter in Schritten, die in Bezug auf Ihre typischen Warenkorbgrößen liegen. Dies kann von Schritten bis zu 5, 10, 50, 100 reichen.

* **`Order subtotal (buckets)`** Originalarchitektur: Von einem Analytiker im Rahmen Ihres `[FREE SHIPPING ANALYSIS]`-Tickets erstellt
* **`Order subtotal (buckets)`** Neue Architektur:
   * Wie oben erwähnt, werden bei dieser Berechnung die Behälter in Schritten erstellt, die in Bezug auf Ihre typischen Warenkorbgrößen liegen. Wenn Sie über eine native Spalte mit Zwischensummen verfügen, z. B. `base_subtotal`, kann diese als Grundlage für diese neue Spalte verwendet werden. Ist dies nicht der Fall, kann es sich um eine berechnete Spalte handeln, die Versand- und Rabatte vom Umsatz ausschließt.

  >[!NOTE]
  >
  >Die &quot;Bucket&quot;-Größen hängen davon ab, was für Sie als Kunde geeignet ist. Sie könnten mit Ihrem `average order value` beginnen und einige Behälter erstellen, die kleiner und größer als dieser Betrag sind. Wenn Sie sich die unten stehende Berechnung ansehen, sehen Sie, wie Sie einen Teil der Abfrage einfach kopieren, bearbeiten und zusätzliche Behälter erstellen können. Das Beispiel erfolgt in Schritten von 50.

   * `Column type - Same table, Column definition - Calculation, Column Inputs-` `base_subtotal` oder `calculated column`, `Datatype`: `Integer`
   * [!UICONTROL Calculation]: `case when A >= 0 and A<=200 then 0 - 200`
wenn `A< 200` und `A <= 250` dann `201 - 250`
wenn `A<251` und `A<= 300` dann `251 - 300`
wenn `A<301` und `A<= 350` dann `301 - 350`
wenn `A<351` und `A<=400`, dann `351 - 400`
wenn `A<401` und `A<=450`, dann `401 - 450`
else &#39;over 450&#39;
end


## Metriken

Keine neuen Metriken!!

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

## Berichte

* **Durchschnittlicher Bestellwert mit Versandregel A**
   * [!UICONTROL Metric]: `Average order value`

* Metrik `A`: `Average Order Value`
* [!UICONTROL Time period]: `Time period with shipping rule A`
* 
  [!UICONTROL Interval]: `None`
* 
  [!UICONTROL Chart Type]: `Scalar`

* **Anzahl der Bestellungen nach Zwischensummenbehälter mit Versandregel A**
   * [!UICONTROL Metric]: `Number of orders`

  >[!NOTE]
  >
  >Sie können das Tail-Ende abschneiden, indem Sie die oberen `X` `sorted by` `Order subtotal` (Buckets) in den `Show top/bottom` anzeigen.

* Metrik `A`: `Number of orders`
* [!UICONTROL Time period]: `Time period with shipping rule A`
* 
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Order subtotal (buckets)`
* 
  [!UICONTROL Chart Type]: `Column`

* **Prozentsatz der Bestellungen nach Zwischensummen mit Versandregel A**
   * [!UICONTROL Metric]: `Number of orders`

   * [!UICONTROL Metric]: `Number of orders`
   * 
     [!UICONTROL Gruppe von]: `Independent`
   * [!UICONTROL Formula]: `(A / B)`
   * 
     [!UICONTROL Format]: `%`

* Metrik `A`: `Number of orders by subtotal (hide)`
* Metrik `B`: `Total number of orders (hide)`
* [!UICONTROL Formula]: `% of orders`
* [!UICONTROL Time period]: `Time period with shipping rule A`
* 
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Order subtotal (buckets)`
* 
  [!UICONTROL Chart Type]: `Line`

* **Prozentsatz der Bestellungen, deren Teilsumme die Versandregel A übersteigt**
   * [!UICONTROL Metric]: `Number of orders`
   * 
     [!UICONTROL Perspective]: `Cumulative`

   * [!UICONTROL Metric]: `Number of orders`
   * 
     [!UICONTROL Gruppe von]: `Independent`

   * [!UICONTROL Formula]: `1- (A / B)`
   * 
     [!UICONTROL Format]: `%`

* Metrik `A`: `Number of orders by subtotal`
* Metrik `B`: `Total number of orders (hide)`
* [!UICONTROL Formula]: `% of orders`
* [!UICONTROL Time period]: `Time period with shipping rule A`
* 
  [!UICONTROL Interval]: `None`
* [!UICONTROL Group by]: `Order subtotal (buckets)`
* 
  [!UICONTROL Chart Type]: `Line`


Wiederholen Sie die obigen Schritte und Berichte für den Versand B und den Zeitraum mit der Versandregel B.

Nachdem Sie alle Berichte kompiliert haben, können Sie sie nach Bedarf im Dashboard organisieren. Das Ergebnis kann wie das Bild oben auf dieser Seite aussehen.
