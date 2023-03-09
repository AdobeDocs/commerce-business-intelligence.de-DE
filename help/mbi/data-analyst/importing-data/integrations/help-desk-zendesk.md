---
title: Helpdesk Reporting für Zendesk
description: Erfahren Sie mehr über Ihre bevorzugten Verweiskanäle.
exl-id: b6142ef2-2be8-401f-ac35-f86fc68d204e
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Helpdesk-Reporting für [!DNL Zendesk]

>[!NOTE]
>
>Dies ist nur für Kunden verfügbar, die sich auf der `Pro` Planen und Verwenden der neuen Architektur. Sie befinden sich in der neuen Architektur, wenn Sie über die `Data Warehouse Views` -Bereich nach Auswahl `Manage Data` aus der Hauptsymbolleiste.

Konsolidierung Ihrer [!DNL Zendesk] -Daten mit Ihrer Transaktionsdatenbank sind eine hervorragende Möglichkeit, um besser zu verstehen, wie Ihre Kunden mit Ihren Vertriebs- oder Kundenerfolgsteams interagieren. Außerdem erfahren Sie, welche Art von Kunden Ihre Support-Plattform verwenden. Dieser Artikel zeigt, wie Sie ein Dashboard einrichten, um detaillierte Berichte über Ihre [!DNL Zendesk] Leistung und Bindung Ihrer Transaktionskunden.

Bevor Sie beginnen, möchten Sie Ihre [[!DNL Zendesk]](../integrations/zendesk.md). Diese Analyse enthält [Erweiterte berechnete Spalten](../../data-warehouse-mgr/adv-calc-columns.md).

<!-- Getting Started -->

## Erste Schritte

### Zu verfolgende Spalten

* `audits` table
* `_id`
* `created_at`
* `id`
* `ticket_id`
* `_updated_at`

* `audits_~_events` table
* `_sub_id`
* `_id_of_parent`
* `author_id`
* `field_name`
* `public`
* `type`
* `value`

* `tickets` table
* `_id`
* `assignee_id`
* `created_at`
* `id`
* `requester_id`
* `status`
* `updated_at`
* `via_~_source_~_from_~_address`
* `_updated_at`

* `users` table
* `_id`
* `created_at`
* `emails`
* `id`
* `role`
* `updated_at`
* `_updated_at`

### Zu erstellende Filtersätze

* `[!DNL Zendesk] Tickets` table
   * `status != deleted`

* `Filter set name`: `Tickets we count`
* `Filter set logic`:

## Berechnete Spalten

### Zu erstellende Spalten

* **`[!DNL Zendesk] user's`** table
   * `User is agent? (Yes/No) `
   * 
      * `Column type` - `Same Table > Calculation`

      * `Input columns` - `role`, `email`

      * `SQL Calculation` `- case when `A` is not `null` and `A!=`end-user` then `Yes` when `B` ist nicht `null` und `B` like `%@magento.com` then `Yes` else `No` end

      * Ersetzen `@magento.com` mit Ihrer Domäne

      * `Datatype` - `String`

* **`[Zendesk] audits_~_events`** table
   * Wählen Sie eine Definition aus: `Joined Column`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[Zendesk] audits_~_events.author_id8`
   * [!UICONTROL One]: `[Zendesk] users.id`

   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] users`
   * Wählen Sie eine [!UICONTROL column]: `User is agent? (Yes/No)`
   * [!UICONTROL Path]: `[Zendesk] audits_~_events.author_id = [!DNL Zendesk] users.id`

* **`Author is agent? (Yes/No)`**

* **`[Zendesk] audits`** table
   * Wählen Sie eine Definition aus: `Exists`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[Zendesk] audits_~_events._id_of_parent`
   * [!UICONTROL One]: `[Zendesk] audits._id`

   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] audits_~_events`
   * [!UICONTROL Path]: `[Zendesk] audits_~_events._id_of_parent = [Zendesk] audits._id`
   * [!UICONTROL Filter]:
   * `field_name` = `status`
   * `type` = `Change`
   * `value` = `solved`

   * Wählen Sie eine Definition aus: `Exists`
   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] audits_~_events`
   * [!UICONTROL Path]: `[Zendesk] audits_~_events._id_of_parent = [Zendesk] audits._id`
   * [!UICONTROL Filter]: `Author is agent? (Yes/No)`
   * `type` = `Comment`
   * `public` = `1`

* **`Status changes to solved? (1/0)`**
* **`Is agent comment? (1/0)`**

* **`[Zendesk] Tickets`** table
   * Wählen Sie eine Definition aus: `Joined Column`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[Zendesk] tickets.requester_id`
   * [!UICONTROL One]: `[Zendesk] users.id`

   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] users`
   * Wählen Sie eine [!UICONTROL column]: `email`
   * [!UICONTROL Path]: `[Zendesk] tickets.requester_id = [Zendesk] users.id`

   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] users`
   * Wählen Sie eine [!UICONTROL column]: `role`
   * [!UICONTROL Path]: `[Zendesk] tickets.requester_id = [Zendesk] users.id`

   * Wählen Sie eine Definition aus: `Max`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[Zendesk] audits.ticket_id`
   * [!UICONTROL One]: `[Zendesk] tickets.id`

   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] audits`
   * Wählen Sie eine [!UICONTROL column]: `created_at`
   * [!UICONTROL Path]: `[Zendesk] audits.ticket_id = [Zendesk] tickets.id`
   * [!UICONTROL Filter]:
   * `status` geändert auf `solved = 1`

   * Wählen Sie eine Definition aus: `Min`
   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] audits`
   * Wählen Sie eine [!UICONTROL column]: `created_at`
   * [!UICONTROL Path]: `[Zendesk] audits.ticket_id = [Zendesk] tickets.id`
   * [!UICONTROL Filter]:
   * `Is agent comment? = 1`

* `Requester's email`
* `Requester's role`
* `Ticket's latest solved date`
* `First agent response date`
* `Seconds to resolution`
   * 
      * `Column type` - `Same Table > Date Difference`

      * `Ticket's latest solved date` minus `created_at`

* **`Seconds to first response`**
   * 
      * `Column type` - `Same Table > Date Difference`

      * `First agent response date` minus `created_at`

* **`Requester's ticket number`**
   * 
      * `Column type` - `Same Table > Event Number`

      * `Event Owner` - `requester_id`

      * `Event Rank` - `created_at`

* **`Ticket created_at (hour of day)`**
   * 
      * `Column type` - &quot;Dieselbe Tabelle > Berechnung&quot;

      * `Input columns` - `created_at`

      * `SQL Calculation` - `to_char(A,'HH24')::int`

      * `Datatype` - Ganzzahl

* **`Ticket created_at (day of week)`**
   * 
      * `Column type` - &quot;Dieselbe Tabelle > Berechnung&quot;

      * `Input columns` - `created_at`

      * `Calculation` - `to_char(A,'D')||'. '||to_char(A,'Day')`

      *`Datatype` – `String`


* **`customer_entity`** table
   * Wählen Sie eine Definition aus: `Count`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[Zendesk] tickets.email`
   * 

      [!UICONTROL One]: `customer_entity.email`

   * Wählen Sie eine [!UICONTROL table]: `[Zendesk] tickets`
   * [!UICONTROL Path]: `[Zendesk] tickets.email = customer_entity.email`
   * [!UICONTROL Filter]:
   * `Tickets we count`

* **`User's lifetime number of support tickets requested`**
* **`Has user filed a support ticket? (Yes/No)`**
   * 
      * `Column type` - &quot;Dieselbe Tabelle > Berechnung&quot;

      * `Input columns` - `User's lifetime number of support tickets requested`

      * `Calculation` - `case when A>0 then 'Yes' else 'No' end`

      * `Datatype` – `String`

* **`[Zendesk] Tickets`** table
   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie eine [!UICONTROL table]: `customer_entity`
   * Wählen Sie eine [!UICONTROL column]: `User's lifetime number of support tickets requested`
   * [!UICONTROL Path]: `[Zendesk] tickets.email = customer_entity.email`

* **`Requester's lifetime number of support tickets`**

## Metriken

* **[!DNL Zendesk]Neue Tickets**
   * `Tickets we count`

* Im **`[Zendesk] tickets`** table
* Diese Metrik führt eine **Count**
* Im **`id`** column
* Bestellt von der **`created_at`** timestamp
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Gelöste Tickets**
   * `Tickets we count`
   * status IN `closed, solved`

* Im **`[Zendesk] tickets`** table
* Diese Metrik führt eine **Count**
* Im **`id`** column
* Bestellt von der **`created_at`** timestamp
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Unique Users, die Tickets einreichen**
   * `Tickets we count`

* Im **`[Zendesk] tickets`** table
* Diese Metrik führt eine **Count Distinct**
* Im **`requester_id`** column
* Bestellt von der **`created_at`** timestamp
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Durchschnittliche/mittlere Ticketauflösungszeit**
   * `Tickets we count`
   * status IN `closed, solved`

* Im **`[Zendesk] tickets`** table
* Diese Metrik führt eine **Durchschnitt (oder Medianwert)**
* Im **`Seconds to resolution`** column
* Bestellt von der **`created_at`** timestamp
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Durchschnittliche/mittlere Zeit bis erste Antwort**
   * Zu zählende Tickets
   * Status IN geschlossen, gelöst

* Im **`[Zendesk] tickets`** table
* Diese Metrik führt eine **Durchschnitt (oder Medianwert)**
* Im **`Seconds to first response`** column
* Bestellt von der **`created_at`** timestamp
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher, dass [Metriken alle neuen Spalten als Dimensionen hinzufügen](../../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.

### Berichte

* **[!UICONTROL New/Open/Pending tickets]**
   * [!UICONTROL Metric]: `New Tickets`
   * [!UICONTROL Filter]:
   * status IN `new, open, pending`

* Metrik `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Closed/Solved tickets]**
   * [!UICONTROL Metric]: `New Tickets`
   * [!UICONTROL Filter]:
   * status IN `solved, closed`

* Metrik `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Average time to first response]**
   * [!UICONTROL Metric]: `Average time to first response`

* Metrik `A`: `Average time to first response`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Average time to resolution]**
   * [!UICONTROL Metric]: `Average time to resolution`
   * [!UICONTROL Filter]:
   * status IN `solved, closed`

* Metrik `A`: `Average time to resolution`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Tickets by status]**
   * [!UICONTROL Metric]: `New Tickets`

* Metrik `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Group by`: `status`
* `Chart Type`: `Stacked Column`

* **[!UICONTROL Number of new and solved tickets]**
   * [!UICONTROL Metric]: `New Tickets`

   * [!UICONTROL Metric]: `New Tickets`

* Metrik `A`: `New tickets`
* Metrik `B`: `Solved tickets`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Line`

* **[!UICONTROL Time to first response]**
   * [!UICONTROL Metric]: `Average time to first response`

* Metrik `A`: `Average time to first response`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Column`

* **[!UICONTROL Time to resolution]**
   * [!UICONTROL Metric]: `Average time to resolution`
   * [!UICONTROL Filter]:
   * status IN `solved, closed`

* Metrik `A`: `Average time to resolution`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Column`

* **[!UICONTROL Distinct users filing tickets]**
   * [!UICONTROL Metric]: `Distinct users filing tickets`

* Metrik `A`: `Distinct users filing tickets`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Column`

* **[!UICONTROL Peak ticket days]**
   * [!UICONTROL Metric]: `New Tickets`

* Metrik `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Group by`: `Ticket created_at (day of week)`
* `Chart Type`: `Pie`

* **[!UICONTROL Peak ticket hours]**
   * [!UICONTROL Metric]:`New Tickets`

   * `Show top/bottom`: `Top 100% sorted by created_at (hour of the day)`

* Metrik `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Group by`: `Ticket created_at (hour of the day)`
* `Chart Type`: `Pie`

* **[!UICONTROL Avg LTV of users who have and have not filed tickets]**
   * [!UICONTROL Metric]: `Average lifetime revenue`

* Metrik `A`: `Average lifetime revenue`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Group by`: `User has filed a support ticket?`
* `Chart Type`: `Column`

* **[!UICONTROL Number of new users who have and have not filed tickets]**
   * 

      [!UICONTROL Metrik]: Users

* Metrik `A`: `New users`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Group by`: `User has filed a support ticket?`
* `Chart Type`: `Column`
