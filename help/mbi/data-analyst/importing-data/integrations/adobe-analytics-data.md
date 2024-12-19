---
title: expected [!DNL Adobe Analytics] data
description: Erfahren Sie, wie Sie Ihre RDS-Instanz verbinden.
exl-id: 4df66ec1-c7f3-4b02-8f0f-49cada99c14c
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Erwartete [!DNL Adobe Analytics]

Die [!DNL Adobe Analytics] Integration für [!DNL Adobe Commerce Intelligence] verwendet die [Analytics 2.0 Reporting-API](https://developer.adobe.com/analytics-apis/docs/2.0/#!AdobeDocs/analytics-2.0-apis/master/README.md).

>[!INFO]
>
>Um sicherzustellen, dass Sie die erwarteten Daten erhalten, können Sie zunächst in der [!DNL Adobe Analytics] Workspace einen Bericht mit Ihren gewünschten Metriken und Dimensionen erstellen. Auf diese Weise können Sie die Kompatibilität und Verfügbarkeit von Daten überprüfen.

In Ihrem Data Warehouse wird eine Tabelle pro verbundener Report Suite mit dem Namen `report-suite-<ID>` erstellt (wobei `<ID>` eine eindeutige, von [!DNL Commerce Intelligence] generierte ID ist).

Das Schema dieser Tabelle besteht aus den Metriken und Dimensionen, die Sie im Einrichtungsprozess der Integration ausgewählt haben. Zur Identifizierung werden von [!DNL Commerce Intelligence] auch mehrere zusätzliche Spalten generiert.

Wenn Sie beispielsweise während des Setups die folgende Metrik und Dimension ausgewählt haben:
- `Metric`: `Page views`
- `Dimension`: `Page`

Die Tabelle würde die folgenden Spalten enthalten:

| Spaltenname | Beschreibung |
| --- | --- |
| `_id` | Diese Spalte ist der Primärschlüssel. |
| `_item_hash` | [!DNL Commerce Intelligence] eindeutige Kennung. Diese Spalte wird von [!DNL Commerce Intelligence] erstellt. |
| `_updated_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. Es wird von [!DNL Commerce Intelligence] erstellt. |
| `start_date` | Startdatum der eingeschlossenen Daten für die Zeile `start_date` ist immer 00:00 Uhr desselben Tages innerhalb einer Reihe. |
| `end_date` | Enddatum der eingeschlossenen Daten für die Zeile `end_date` ist immer 23:59 Uhr desselben Tages innerhalb einer Reihe. |
| `page_views` | Ausgewählte Metrik: Die Gesamtzahl der Seitenansichten für den identifizierten Zeitraum. |
| `page` | Ausgewählte Dimension: Einzelne Seitennamen mit verfolgten Ansichten. |

Mit den Optionen *Synchronisieren* oder Nicht synchronisieren *auf der `Data Warehouse` können Sie steuern, welche der ausgewählten Metriken* Dimensionen Daten in Ihrer [!DNL Commerce Intelligence]-Tabelle verfügbar haben. Spalten, die derzeit nicht synchronisiert werden, werden grau angezeigt. Wenn Sie die Synchronisierung einer Spalte beenden, können Sie die Synchronisierung später erneut starten.

## Aktuelle Einschränkungen

In diesem Abschnitt werden die Einschränkungen der [!DNL Adobe Analytics] für [!DNL Commerce Intelligence] beschrieben.

| Einschränkung | Beschreibung |
| --- | --- |
| `Historical data period` | Wie bei anderen Integrationen von Drittanbietern ruft die [!DNL Adobe Analytics]-Integration eine begrenzte Menge an historischen Daten ab und behält dann die Daten auf dem neuesten Stand. Der historische Zeitraum ist auf 2 Wochen konfiguriert. |
| `Empty component combinations` | Einige Kombinationen von Metriken und Dimensionen enthalten keine Daten. Wenn eine solche Kombination für die Replikation ausgewählt ist, schließt [!DNL Commerce Intelligence] die Spalte aus der replizierten Tabelle aus. Um diese Kombination zu vermeiden, können Sie zunächst einen Bericht in der [[!DNL Adobe Analytics] Workspace erstellen](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html) um zu überprüfen, ob Sie die erwarteten Daten erhalten. |
| `Re-authorization cadence` | Die [!DNL Adobe Analytics] Integration muss alle zwei Wochen erneut autorisiert werden. Um die Autorisierung erneut durchzuführen, gehen Sie zur Seite Bearbeiten für die Integration und klicken Sie auf **[!UICONTROL Re-Authorize with [!DNL Adobe Analytics]]**. |
| `One dimension per row` | [!DNL Adobe Analytics] stellt Metrikdaten für jeweils eine Dimension bereit. Wenn Sie beim Einrichten mehrere Dimensionen auswählen, enthält jede Zeile in Ihrer [!DNL Commerce Intelligence] einen einzelnen Dimensionswert und NULL für jede andere Dimension. |
