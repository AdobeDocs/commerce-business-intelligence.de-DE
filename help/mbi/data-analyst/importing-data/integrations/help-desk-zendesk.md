---
title: Helpdesk-Berichte für Zendesk
description: Erfahren Sie mehr über Ihre wertvollsten Empfehlungskanäle.
exl-id: b6142ef2-2be8-401f-ac35-f86fc68d204e
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Helpdesk-Berichte für [!DNL Zendesk]

>[!NOTE]
>
>Dies ist nur für Clients verfügbar, die sich im `Pro` befinden und die neue Architektur verwenden. Sie befinden sich auf der neuen Architektur, wenn der Abschnitt &quot;`Data Warehouse Views`&quot; verfügbar ist, nachdem Sie `Manage Data` in der Hauptsymbolleiste ausgewählt haben.

Die Konsolidierung Ihrer [!DNL Zendesk] mit Ihrer Transaktionsdatenbank ist eine hervorragende Möglichkeit, um besser zu verstehen, wie Ihre Kunden mit Ihren Vertriebs- oder Customer Success-Teams interagieren. Außerdem erfahren Sie, welche Kundinnen und Kunden Ihre Support-Plattform verwenden. Dieses Thema zeigt, wie Sie ein Dashboard einrichten, um granulare Berichte über Ihre [!DNL Zendesk] und die Verbindung mit Ihren Transaktionskunden zu erhalten.

Bevor Sie beginnen, verbinden Sie Ihre [[!DNL Zendesk]](../integrations/zendesk.md). Diese Analyse enthält [erweiterte berechnete Spalten](../../data-warehouse-mgr/adv-calc-columns.md).

<!-- Getting Started -->

## Erste Schritte

### Nachzuverfolgende Spalten

* `audits`
* `_id`
* `created_at`
* `id`
* `ticket_id`
* `_updated_at`

* `audits_~_events`
* `_sub_id`
* `_id_of_parent`
* `author_id`
* `field_name`
* `public`
* `type`
* `value`

* `tickets`
* `_id`
* `assignee_id`
* `created_at`
* `id`
* `requester_id`
* `status`
* `updated_at`
* `via_~_source_~_from_~_address`
* `_updated_at`

* `users`
* `_id`
* `created_at`
* `emails`
* `id`
* `role`
* `updated_at`
* `_updated_at`

### Zu erstellende Filtersätze

* `[!DNL Zendesk] Tickets`
   * `status != deleted`

* `Filter set name`: `Tickets we count`
* `Filter set logic`:

## Berechnete Spalten

### Zu erstellende Spalten

* **`[!DNL Zendesk] user's`**
   * `User is agent? (Yes/No) `
   * &#x200B;
      * `Column type` - `Same Table > Calculation`

      * `Input columns` - `role`, `email`

      * `SQL Calculation` `- case when `A` is not `NULL` and `A!=`end-user` dann `Yes`, wenn `B` nicht `null` ist, und `B` wie `%@magento.com` dann `Yes` andernfalls `No` Ende

      * `@magento.com` durch Ihre Domain ersetzen

      * `Datatype` - `String`

* **`[!DNL Zendesk] audits_~_events`**
   * Definition auswählen: `Joined Column`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] audits_~_events.author_id8`
   * [!UICONTROL One]: `[!DNL Zendesk] users.id`

   * [!UICONTROL table] auswählen: `[!DNL Zendesk] users`
   * [!UICONTROL column] auswählen: `User is agent? (Yes/No)`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits_~_events.author_id = [!DNL Zendesk] users.id`

* **`Author is agent? (Yes/No)`**

* **`[!DNL Zendesk] audits`**
   * Definition auswählen: `Exists`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] audits_~_events._id_of_parent`
   * [!UICONTROL One]: `[!DNL Zendesk] audits._id`

   * [!UICONTROL table] auswählen: `[!DNL Zendesk] audits_~_events`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits_~_events._id_of_parent = [!DNL Zendesk] audits._id`
   * [!UICONTROL Filter]:
   * `field_name` = `status`
   * `type` = `Change`
   * `value` = `solved`

   * Definition auswählen: `Exists`
   * [!UICONTROL table] auswählen: `[!DNL Zendesk] audits_~_events`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits_~_events._id_of_parent = [!DNL Zendesk] audits._id`
   * [!UICONTROL Filter]: `Author is agent? (Yes/No)`
   * `type` = `Comment`
   * `public` = `1`

* **`Status changes to solved? (1/0)`**
* **`Is agent comment? (1/0)`**

* **`[!DNL Zendesk] Tickets`**
   * Definition auswählen: `Joined Column`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] tickets.requester_id`
   * [!UICONTROL One]: `[!DNL Zendesk] users.id`

   * [!UICONTROL table] auswählen: `[!DNL Zendesk] users`
   * [!UICONTROL column] auswählen: `email`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.requester_id = [!DNL Zendesk] users.id`

   * Definition auswählen: `Joined Column`
   * [!UICONTROL table] auswählen: `[!DNL Zendesk] users`
   * [!UICONTROL column] auswählen: `role`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.requester_id = [!DNL Zendesk] users.id`

   * Definition auswählen: `Max`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] audits.ticket_id`
   * [!UICONTROL One]: `[!DNL Zendesk] tickets.id`

   * [!UICONTROL table] auswählen: `[!DNL Zendesk] audits`
   * [!UICONTROL column] auswählen: `created_at`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits.ticket_id = [!DNL Zendesk] tickets.id`
   * [!UICONTROL Filter]:
   * `status` geändert in `solved = 1`

   * Definition auswählen: `Min`
   * [!UICONTROL table] auswählen: `[!DNL Zendesk] audits`
   * [!UICONTROL column] auswählen: `created_at`
   * [!UICONTROL Path]: `[!DNL Zendesk] audits.ticket_id = [!DNL Zendesk] tickets.id`
   * [!UICONTROL Filter]:
   * `Is agent comment? = 1`

* `Requester's email`
* `Requester's role`
* `Ticket's latest solved date`
* `First agent response date`
* `Seconds to resolution`
   * &#x200B;
      * `Column type` - `Same Table > Date Difference`

      * `Ticket's latest solved date` minus `created_at`

* **`Seconds to first response`**
   * &#x200B;
      * `Column type` - `Same Table > Date Difference`

      * `First agent response date` minus `created_at`

* **`Requester's ticket number`**
   * &#x200B;
      * `Column type` - `Same Table > Event Number`

      * `Event Owner` - `requester_id`

      * `Event Rank` - `created_at`

* **`Ticket created_at (hour of day)`**
   * &#x200B;
      * `Column type` - „Gleiche Tabelle > Berechnung“

      * `Input columns` - `created_at`

      * `SQL Calculation` - `to_char(A,'HH24')::int`

      * `Datatype` - Ganzzahl

* **`Ticket created_at (day of week)`**
   * &#x200B;
      * `Column type` - „Gleiche Tabelle > Berechnung“

      * `Input columns` - `created_at`

      * `Calculation` - `to_char(A,'D')||'. '||to_char(A,'Day')`

     *`Datatype` - `String`

* **`customer_entity`**
   * Definition auswählen: `Count`
   * [!UICONTROL Create Path]:
   * [!UICONTROL Many]: `[!DNL Zendesk] tickets.email`
   * &#x200B;
     [!UICONTROL ONE]: `customer_entity.email`

   * [!UICONTROL table] auswählen: `[!DNL Zendesk] tickets`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.email = customer_entity.email`
   * [!UICONTROL Filter]:
   * `Tickets we count`

* **`User's lifetime number of support tickets requested`**
* **`Has user filed a support ticket? (Yes/No)`**
   * &#x200B;
      * `Column type` - „Gleiche Tabelle > Berechnung“

      * `Input columns` - `User's lifetime number of support tickets requested`

      * `Calculation` - `case when A>0 then 'Yes' else 'No' end`

      * `Datatype` - `String`

* **`[!DNL Zendesk] Tickets`**
   * Definition auswählen: `Joined Column`
   * [!UICONTROL table] auswählen: `customer_entity`
   * [!UICONTROL column] auswählen: `User's lifetime number of support tickets requested`
   * [!UICONTROL Path]: `[!DNL Zendesk] tickets.email = customer_entity.email`

* **`Requester's lifetime number of support tickets`**

## Metriken

* **[!DNL Zendesk]neue Tickets**
   * `Tickets we count`

* In der **`[!DNL Zendesk] tickets`**
* Diese Metrik führt eine **Anzahl** aus
* In der Spalte **`id`**
* Sortiert nach dem **`created_at`** Zeitstempel
* [!UICONTROL Filter]:

* **[!DNL Zendesk]gelöste Tickets**
   * `Tickets we count`
   * Status IN `closed, solved`

* In der **`[!DNL Zendesk] tickets`**
* Diese Metrik führt eine **Anzahl** aus
* In der Spalte **`id`**
* Sortiert nach dem **`created_at`** Zeitstempel
* [!UICONTROL Filter]:

* **[!DNL Zendesk]Unterschiedliche Benutzer, die Tickets einreichen**
   * `Tickets we count`

* In der **`[!DNL Zendesk] tickets`**
* Diese Metrik führt eine **Anzahl unterschiedlicher Werte**
* In der Spalte **`requester_id`**
* Sortiert nach dem **`created_at`** Zeitstempel
* [!UICONTROL Filter]:

* **[!DNL Zendesk]durchschnittliche/mittlere Zeit für die Ticketauflösung**
   * `Tickets we count`
   * Status IN `closed, solved`

* In der **`[!DNL Zendesk] tickets`**
* Diese Metrik führt einen **Durchschnitt (oder Median) aus**
* In der Spalte **`Seconds to resolution`**
* Sortiert nach dem **`created_at`** Zeitstempel
* [!UICONTROL Filter]:

* **[!DNL Zendesk]durchschnittliche/mediane Zeit bis zum ersten Ansprechen**
   * Tickets, die gezählt werden
   * Status IN geschlossen, gelöst

* In der **`[!DNL Zendesk] tickets`**
* Diese Metrik führt einen **Durchschnitt (oder Median) aus**
* In der Spalte **`Seconds to first response`**
* Sortiert nach dem **`created_at`** Zeitstempel
* [!UICONTROL Filter]:

>[!NOTE]
>
>Stellen Sie sicher[ dass Sie alle neuen Spalten als Dimensionen zu Metriken hinzufügen](../../../data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.

### Berichte

* **[!UICONTROL New/Open/Pending tickets]**
   * [!UICONTROL Metric]: `New Tickets`
   * [!UICONTROL Filter]:
   * Status IN `new, open, pending`

* `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Closed/Solved tickets]**
   * [!UICONTROL Metric]: `New Tickets`
   * [!UICONTROL Filter]:
   * Status IN `solved, closed`

* `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Average time to first response]**
   * [!UICONTROL Metric]: `Average time to first response`

* `A`: `Average time to first response`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Average time to resolution]**
   * [!UICONTROL Metric]: `Average time to resolution`
   * [!UICONTROL Filter]:
   * Status IN `solved, closed`

* `A`: `Average time to resolution`
* `Time period`: `All time`
* `Interval`: `None`
* `Chart Type`: `Scalar`

* **[!UICONTROL Tickets by status]**
   * [!UICONTROL Metric]: `New Tickets`

* `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Group by`: `status`
* `Chart Type`: `Stacked Column`

* **[!UICONTROL Number of new and solved tickets]**
   * [!UICONTROL Metric]: `New Tickets`

   * [!UICONTROL Metric]: `New Tickets`

* `A`: `New tickets`
* `B`: `Solved tickets`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Line`

* **[!UICONTROL Time to first response]**
   * [!UICONTROL Metric]: `Average time to first response`

* `A`: `Average time to first response`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Column`

* **[!UICONTROL Time to resolution]**
   * [!UICONTROL Metric]: `Average time to resolution`
   * [!UICONTROL Filter]:
   * Status IN `solved, closed`

* `A`: `Average time to resolution`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Column`

* **[!UICONTROL Distinct users filing tickets]**
   * [!UICONTROL Metric]: `Distinct users filing tickets`

* `A`: `Distinct users filing tickets`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Chart Type`: `Column`

* **[!UICONTROL Peak ticket days]**
   * [!UICONTROL Metric]: `New Tickets`

* `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Group by`: `Ticket created_at (day of week)`
* `Chart Type`: `Pie`

* **[!UICONTROL Peak ticket hours]**
   * [!UICONTROL Metric]:`New Tickets`

   * `Show top/bottom`: `Top 100% sorted by created_at (hour of the day)`

* `A`: `New tickets`
* `Time period`: `All time`
* `Interval`: `None`
* `Group by`: `Ticket created_at (hour of the day)`
* `Chart Type`: `Pie`

* **[!UICONTROL Avg LTV of users who have and have not filed tickets]**
   * [!UICONTROL Metric]: `Average lifetime revenue`

* `A`: `Average lifetime revenue`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Group by`: `User has filed a support ticket?`
* `Chart Type`: `Column`

* **[!UICONTROL Number of new users who have and have not filed tickets]**
   * &#x200B;
     [!UICONTROL -Metrik]: Users

* `A`: `New users`
* `Time period`: `All time`
* `Interval`: `Monthly`
* `Group by`: `User has filed a support ticket?`
* `Chart Type`: `Column`
