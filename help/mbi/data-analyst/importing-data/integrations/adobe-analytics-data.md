---
title: expected [!DNL Adobe Analytics] data
description: Erfahren Sie, wie Sie Ihre RDS-Instanz verbinden.
exl-id: 4df66ec1-c7f3-4b02-8f0f-49cada99c14c
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/vA-1cABpxQNwI8xTF4Elkgv2geudkp5tnBH1l6-PZiY
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 0%

---

# Erwartete [!DNL Adobe Analytics]

Die [!DNL Adobe Analytics] Integration für [!DNL Adobe Commerce Intelligence] verwendet die [Analytics 2.0 Reporting-API](https://developer.adobe.com/analytics-apis/docs/2.0/#!AdobeDocs/analytics-2.0-apis/master/README.md).

>[!INFO]
>
>Um sicherzustellen, dass Sie die erwarteten Daten erhalten, können Sie zunächst in der [!DNL Adobe Analytics] Workspace einen Bericht mit Ihren gewünschten Metriken und Dimensionen erstellen. Auf diese Weise können Sie die Kompatibilität und Verfügbarkeit von Daten überprüfen.

In Ihrer Data Warehouse wird eine Tabelle pro verbundener Report Suite mit dem Namen `report-suite-<ID>` erstellt (wobei `<ID>` eine eindeutige, von [!DNL Commerce Intelligence] generierte ID ist).

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
| `start_date` | Startdatum der eingeschlossenen Daten für die Zeile `start_date` ist immer 00:00 desselben Tages innerhalb einer Zeile. |
| `end_date` | Enddatum der eingeschlossenen Daten für die Zeile `end_date` ist immer 23:59 desselben Tages innerhalb einer Reihe. |
| `page_views` | Ausgewählte Metrik: Die Gesamtzahl der Seitenansichten für den identifizierten Zeitraum. |
| `page` | Ausgewählte Dimension: Einzelne Seitennamen mit verfolgten Ansichten. |

Mit den Optionen *Synchronisieren* oder Nicht synchronisieren *auf der `Data Warehouse` können Sie steuern, welche der ausgewählten Metriken* Dimensionen Daten in Ihrer [!DNL Commerce Intelligence]-Tabelle verfügbar haben. Spalten, die derzeit nicht synchronisiert werden, werden grau angezeigt. Wenn Sie die Synchronisierung einer Spalte beenden, können Sie die Synchronisierung später erneut starten.

## Aktuelle Einschränkungen

In diesem Abschnitt werden die Einschränkungen der [!DNL Adobe Analytics] für [!DNL Commerce Intelligence] beschrieben.

| Einschränkung | Beschreibung |
| --- | --- |
| `Historical data period` | Wie bei anderen Integrationen von Drittanbietern ruft die [!DNL Adobe Analytics]-Integration eine begrenzte Menge an historischen Daten ab und behält dann die Daten auf dem neuesten Stand. Der historische Zeitraum ist auf 2 Wochen konfiguriert. |
| `Empty component combinations` | Einige Kombinationen von Metriken und Dimensionen enthalten keine Daten. Wenn eine solche Kombination für die Replikation ausgewählt ist, schließt [!DNL Commerce Intelligence] die Spalte aus der replizierten Tabelle aus. Um diese Kombination zu vermeiden, können Sie zunächst einen Bericht in der [[!DNL Adobe Analytics] Workspace erstellen](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=de) um zu überprüfen, ob Sie die erwarteten Daten erhalten. |
| `Re-authorization cadence` | Die [!DNL Adobe Analytics] Integration muss alle zwei Wochen erneut autorisiert werden. Um die Autorisierung erneut durchzuführen, gehen Sie zur Seite Bearbeiten für die Integration und klicken Sie auf **[!UICONTROL Re-Authorize with [!DNL Adobe Analytics]]**. |
| `One dimension per row` | [!DNL Adobe Analytics] stellt Metrikdaten für jeweils eine Dimension bereit. Wenn Sie beim Einrichten mehrere Dimensionen auswählen, enthält jede Zeile in Ihrer [!DNL Commerce Intelligence] einen einzelnen Dimensionswert und NULL für jede andere Dimension. |
