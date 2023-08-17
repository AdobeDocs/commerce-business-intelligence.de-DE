---
title: Erwartet [!DNL Adobe Analytics] Daten
description: Erfahren Sie, wie Sie Ihre RDS-Instanz verbinden.
exl-id: 4df66ec1-c7f3-4b02-8f0f-49cada99c14c
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Erwartet [!DNL Adobe Analytics] Daten

Die [!DNL Adobe Analytics] Integration für [!DNL Adobe Commerce Intelligence] verwendet die [Analytics 2.0 Reporting-API](https://developer.adobe.com/analytics-apis/docs/2.0/#!AdobeDocs/analytics-2.0-apis/master/README.md).

>[!INFO]
>
>Um sicherzustellen, dass Sie die erwarteten Daten erhalten, können Sie zunächst einen Bericht im [!DNL Adobe Analytics] Arbeitsbereich mit Ihren gewünschten Metriken und Dimensionen. Auf diese Weise können Sie die Kompatibilität und Verfügbarkeit von Daten überprüfen.

Eine Tabelle pro verbundener Report Suite namens `report-suite-<ID>` , `<ID>` ist eine eindeutige ID, die von [!DNL Commerce Intelligence]) wird in Ihrer Data Warehouse erstellt.

Das Schema dieser Tabelle setzt sich aus den Metriken und Dimensionen zusammen, die Sie beim Einrichten der Integration ausgewählt haben. Mehrere zusätzliche Spalten werden ebenfalls von [!DNL Commerce Intelligence]zu Identifizierungszwecken.

Wenn Sie beispielsweise während der Einrichtung die folgende Metrik und Dimension ausgewählt haben:
- `Metric`: `Page views`
- `Dimension`: `Page`

Die Tabelle würde die folgenden Spalten enthalten:

| Spaltenname | Beschreibung |
| --- | --- |
| `_id` | Diese Spalte ist der Primärschlüssel. |
| `_item_hash` | [!DNL Commerce Intelligence] eindeutige Kennung. Diese Spalte wird von [!DNL Commerce Intelligence]. |
| `_updated_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. Sie wird von [!DNL Commerce Intelligence]. |
| `start_date` | Startdatum der eingeschlossenen Daten für die Zeile. `start_date` ist immer 00:00 Uhr desselben Tages innerhalb einer Zeile. |
| `end_date` | Enddatum der eingeschlossenen Daten für die Zeile. `end_date` ist immer 23:59 des gleichen Tages innerhalb einer Zeile. |
| `page_views` | Ausgewählte Metrik: Die Gesamtanzahl der Seitenansichten für den angegebenen Zeitraum. |
| `page` | Ausgewählte Dimension: Einzelne Seitennamen mit verfolgten Ansichten. |

Legen Sie fest, welche der ausgewählten Metriken und Dimensionen Daten in Ihrer [!DNL Commerce Intelligence] -Tabelle mithilfe der *Synchronisieren* oder *unsync* Optionen in `Data Warehouse` Seite. Spalten, die derzeit nicht synchronisiert werden, werden grau dargestellt. Wenn Sie die Synchronisierung einer Spalte stoppen, können Sie sie später erneut synchronisieren.

## Aktuelle Einschränkungen

In diesem Abschnitt werden die Einschränkungen der [!DNL Adobe Analytics] Integration für [!DNL Commerce Intelligence].

| Einschränkung | Beschreibung |
| --- | --- |
| `Historical data period` | Wie bei anderen Drittanbieterintegrationen muss die Variable [!DNL Adobe Analytics] -Integration ruft eine begrenzte Anzahl historischer Daten ab und aktualisiert dann weiterhin Daten. Der historische Zeitraum ist auf 2 Wochen konfiguriert. |
| `Empty component combinations` | Einige Kombinationen aus Metriken und Dimensionen enthalten keine Daten. Wenn eine solche Kombination für die Replikation ausgewählt wird, [!DNL Commerce Intelligence] schließt die Spalte aus der replizierten Tabelle aus. Um die Auswahl einer solchen Kombination zu vermeiden, können Sie zunächst einen Bericht im [[!DNL Adobe Analytics] Arbeitsbereich](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html) um zu überprüfen, ob Sie die erwarteten Daten erhalten. |
| `Re-authorization cadence` | Neuautorisierung der [!DNL Adobe Analytics] Die Integration ist alle zwei Wochen erforderlich. Um eine erneute Autorisierung vorzunehmen, navigieren Sie zur Seite Bearbeiten für die Integration und klicken Sie auf **[!UICONTROL Re-Authorize with [!DNL Adobe Analytics]]**. |
| `One dimension per row` | [!DNL Adobe Analytics] stellt Metrikdaten für jeweils eine Dimension bereit. Wenn Sie während der Einrichtung mehrere Dimensionen auswählen, wird jede Zeile in Ihrer [!DNL Commerce Intelligence] -Tabelle enthält einen einzelnen Dimensionswert und Nullen für jede andere Dimension. |
