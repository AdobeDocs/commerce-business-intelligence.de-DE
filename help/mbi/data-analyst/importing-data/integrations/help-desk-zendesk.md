---
title: Helpdesk Reporting für Zendesk
description: Erfahren Sie mehr über Ihre bevorzugten Verweiskanäle.
exl-id: b6142ef2-2be8-401f-ac35-f86fc68d204e
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Helpdesk-Reporting für [!DNL Zendesk]

>[!NOTE]
>
>Dies ist nur für Clients verfügbar, die den `Pro` -Plan ausführen und die neue Architektur verwenden. Sie befinden sich in der neuen Architektur, wenn der Abschnitt `Data Warehouse Views` nach Auswahl von `Manage Data` in der Hauptsymbolleiste verfügbar ist.

Die Konsolidierung Ihrer [!DNL Zendesk] -Daten mit Ihrer Transaktionsdatenbank ist eine hervorragende Möglichkeit, um besser zu verstehen, wie Ihre Kunden mit Ihren Vertriebs- oder Kundenerfolgsteams interagieren. Außerdem erfahren Sie, welche Art von Kunden Ihre Support-Plattform verwenden. In diesem Thema wird gezeigt, wie Sie ein Dashboard einrichten, um detaillierte Berichte über Ihre [!DNL Zendesk] Leistung und Zeitdauer bei Ihren Transaktionskunden zu erhalten.

Bevor Sie beginnen, möchten Sie Ihre [[!DNL Zendesk]](../integrations/zendesk.md) verbinden. Diese Analyse enthält [erweiterte berechnete Spalten](../../data-warehouse-mgr/adv-calc-columns.md).

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

### Sets filtern, um sie zu erstellen

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

      * `SQL Calculation` `- case when `A` is not `null` and `A!=`end-user` gefolgt von `Yes`, wenn `B` nicht `null` und `B` wie `%@magento.com` ist, dann `Yes` else `No` Ende

      * Ersetzen Sie `@magento.com` durch Ihre Domäne

      * `Datatype` - `String`

* **`[!DNL Zendesk] audits_~_events`** table
   * Wählen Sie eine Definition aus: `Joined Column`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] audits_~_events.author_id8`
   * [!UICONTROL One]: `[!DNL Zendesk] users.id`

   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] users`
   * Wählen Sie einen [!UICONTROL column]: `User is agent? (Yes/No)`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits_~_events.author_id = [!DNL Zendesk] users.id`

* **`Author is agent? (Yes/No)`**

* **`[!DNL Zendesk] audits`** table
   * Wählen Sie eine Definition aus: `Exists`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] audits_~_events._id_of_parent`
   * [!UICONTROL One]: `[!DNL Zendesk] audits._id`

   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] audits_~_events`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits_~_events._id_of_parent = [!DNL Zendesk] audits._id`
   * [!UICONTROL Filter]:
   * `field_name` = `status`
   * `type` = `Change`
   * `value` = `solved`

   * Wählen Sie eine Definition aus: `Exists`
   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] audits_~_events`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits_~_events._id_of_parent = [!DNL Zendesk] audits._id`
   * [!UICONTROL Filter]: `Author is agent? (Yes/No)`
   * `type` = `Comment`
   * `public` = `1`

* **`Status changes to solved? (1/0)`**
* **`Is agent comment? (1/0)`**

* **`[!DNL Zendesk] Tickets`** table
   * Wählen Sie eine Definition aus: `Joined Column`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] tickets.requester_id`
   * [!UICONTROL One]: `[!DNL Zendesk] users.id`

   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] users`
   * Wählen Sie einen [!UICONTROL column]: `email`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.requester_id = [!DNL Zendesk] users.id`

   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] users`
   * Wählen Sie einen [!UICONTROL column]: `role`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.requester_id = [!DNL Zendesk] users.id`

   * Wählen Sie eine Definition aus: `Max`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] audits.ticket_id`
   * [!UICONTROL One]: `[!DNL Zendesk] tickets.id`

   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] audits`
   * Wählen Sie einen [!UICONTROL column]: `created_at`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits.ticket_id = [!DNL Zendesk] tickets.id`
   * [!UICONTROL Filter]:
   * `status` geändert in `solved = 1`

   * Wählen Sie eine Definition aus: `Min`
   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] audits`
   * Wählen Sie einen [!UICONTROL column]: `created_at`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits.ticket_id = [!DNL Zendesk] tickets.id`
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

     *`Datatype` - `String`

* **`customer_entity`** table
   * Wählen Sie eine Definition aus: `Count`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] tickets.email`
   * 
     [!UICONTROL One]: `customer_entity.email`

   * Wählen Sie einen [!UICONTROL table]: `[!DNL Zendesk] tickets`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.email = customer_entity.email`
   * [!UICONTROL Filter]:
   * `Tickets we count`

* **`User's lifetime number of support tickets requested`**
* **`Has user filed a support ticket? (Yes/No)`**
   * 
      * `Column type` - &quot;Dieselbe Tabelle > Berechnung&quot;

      * `Input columns` - `User's lifetime number of support tickets requested`

      * `Calculation` - `case when A>0 then 'Yes' else 'No' end`

      * `Datatype` - `String`

* **`[!DNL Zendesk] Tickets`** table
   * Wählen Sie eine Definition aus: `Joined Column`
   * Wählen Sie einen [!UICONTROL table]: `customer_entity`
   * Wählen Sie einen [!UICONTROL column]: `User's lifetime number of support tickets requested`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.email = customer_entity.email`

* **`Requester's lifetime number of support tickets`**

## Metriken

* **[!DNL Zendesk]Neue Tickets**
   * `Tickets we count`

* In der Tabelle **`[!DNL Zendesk] tickets`**
* Diese Metrik führt eine **Zählung** aus
* In der Spalte **`id`**
* Durch den Zeitstempel **`created_at`** geordnet
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Gelöste Tickets**
   * `Tickets we count`
   * Status IN `closed, solved`

* In der Tabelle **`[!DNL Zendesk] tickets`**
* Diese Metrik führt eine **Zählung** aus
* In der Spalte **`id`**
* Durch den Zeitstempel **`created_at`** geordnet
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Unique Users, die Tickets abschicken**
   * `Tickets we count`

* In der Tabelle **`[!DNL Zendesk] tickets`**
* Diese Metrik führt einen **Count Distinct** aus
* In der Spalte **`requester_id`**
* Durch den Zeitstempel **`created_at`** geordnet
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Durchschnittliche/mittlere Zeitdauer der Ticketauflösung**
   * `Tickets we count`
   * Status IN `closed, solved`

* In der Tabelle **`[!DNL Zendesk] tickets`**
* Diese Metrik führt einen **Durchschnitt (oder Median)** aus.
* In der Spalte **`Seconds to resolution`**
* Durch den Zeitstempel **`created_at`** geordnet
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Durchschnittliche/mittlere Zeit bis erste Antwort**
   * Zu zählende Tickets
   * Status IN geschlossen, gelöst

* In der Tabelle **`[!DNL Zendesk] tickets`**
* Diese Metrik führt einen **Durchschnitt (oder Median)** aus.
* In der Spalte **`Seconds to first response`**
* Durch den Zeitstempel **`created_at`** geordnet
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher, dass Sie [alle neuen Spalten als Dimensionen zu den Metriken hinzufügen](../../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) , bevor Sie neue Berichte erstellen.

### Berichte

* **[!UICONTROL New/Open/Pending tickets]**
   * [!UICONTROL Metric]: `New Tickets`
   * [!UICONTROL Filter]:
   * Status IN `new, open, pending`

* Metrik `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Closed/Solved tickets]**
   * [!UICONTROL Metric]: `New Tickets`
   * [!UICONTROL Filter]:
   * Status IN `solved, closed`

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
   * Status IN `solved, closed`

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
   * Status IN `solved, closed`

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
