---
title: Erwartete Data Warehouse-Daten in Google Analytics
description: Erfahren Sie, wie Sie mit Ihren in Google Analytics gespeicherten Daten interagieren können.
exl-id: 2b1305cd-5f34-43d9-b77f-a4f5b1d82c66
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
TQID: https://experienceleague.adobe.com/-Pulnv7J-TmXxL0msB6nhuMKIWbCpS0163rewp9BOvc
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 355
ht-degree: 0%

---

# Erwartete [!DNL Google Analytics Warehoused]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

>[!NOTE]
>
>Einige Informationen wurden mit Erlaubnis Ihrer Freunde bei [[!DNL Stitch]](https://www.stitchdata.com/docs/integrations/saas/google-analytics) verwendet.

[!DNL Google Analytics Warehoused] Integration in [!DNL Commerce Intelligence] verwendet die [!DNL Google Analytics]Core Reporting [API](https://developers.google.com/analytics/devguides/reporting/core/v3/).

>[!NOTE]
>
>Um unerwartete oder unsinnige Ergebnisse zu vermeiden, stellen Sie sicher, dass alle verwendeten Dimensionen [mit einer oder mehreren Metriken kompatibel](https://ga-dev-tools.google/dimensions-metrics-explorer/) die Sie im `Report Builder` verwenden.

In Ihrer Data Warehouse wird eine einzige Tabelle mit dem Namen `report` erstellt.

Das Schema dieser Tabelle besteht aus den Metriken und Dimensionen, die Sie während des Einrichtungsprozesses ausgewählt haben, sowie aus zwei weiteren Spalten: `start-date` und `end-date`.

Wenn Sie beispielsweise während des Setups die folgenden Metriken und Dimensionen ausgewählt haben:

* `Metrics`: `ga:users`
* `Dimensions`: `ga:month`

Die Tabelle würde wie im folgenden Beispiel aussehen.

| **Spaltenname** | **Beschreibung** |
|-----|-----|
| `\_id` | Diese Spalte ist die `primary key`. |
| `\_rjm\_record\_hash` | [!DNL Commerce Intelligence] eindeutige Kennung. Diese Spalte wird von [!DNL Commerce Intelligence] erstellt. |
| `\_updated\_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. Diese Spalte wird von [!DNL Commerce Intelligence] erstellt. |
| `start-date` | Identifikation des Tages, an dem die Zeile angezeigt wird. |
| `end-date` | Identifikation des Tages, an dem die Zeile angezeigt wird. |
| `month` | Ausgewählte Dimension: Monat der Sitzung, eine zweistellige Ganzzahl von 01 bis 12. |
| `users` | Ausgewählte Metrik: Die Gesamtzahl der Benutzer für den angeforderten Zeitraum. |

{style="table-layout:auto"}

## Was ist der Unterschied zwischen [!DNL Google Analytics Warehoused] und [!DNL Live Integration]?

Das wichtigste Unterscheidungsmerkmal besteht darin, dass eine Integration gespeichert wird ([!DNL Google Analytics Warehoused]) und die andere nicht ([!DNL Google Analytics Live]). In [!DNL Google Analytics Warehoused] Fällen ermöglicht dies die Manipulation Ihrer [!DNL Google Analytics] und bietet Ihnen die Möglichkeit, [!DNL Google Analytics] und andere Datenquellen zu kombinieren, um aufschlussreiche Berichte zu erstellen.

Ein Beispiel dafür, was aus Sicht der Manipulation getan werden kann, finden Sie in [!DNL Google Analytics] Anzeigenkampagnen . Angenommen, Sie verfügen über mehrere Anzeigenkampagnen für das 4. Quartal mit unterschiedlichen Namen. Die Kampagnen waren das Ergebnis einer bestimmten Marketing-Initiative. Mit gespeicherten Daten können Sie eine Spalte erstellen, die die betreffenden Kampagnennamen findet und den Namen der `Operation Dumbo` im 4. Quartal zurückgibt.

Der Kombinationsaspekt ermöglicht es, [!DNL Google Analytics] Daten mit anderen Daten zu verbinden, um Analysen durchzuführen. Nehmen Sie beispielsweise `Total Time On Site By Ad Campaign` Daten aus [!DNL Google Analytics] und verbinden Sie sie mit `Total Spent Per Campaign` Daten aus [!DNL Facebook Ads], um ein vollständiges Bild darüber zu erhalten, wie viel Interaktion Sie kostet.

Mit der [!DNL Google Analytics Live] Integration ist hingegen jedes [!DNL Google Analytics] wie ein kleines Silo, das nicht in Ihrem [!DNL Commerce Intelligence] Data Warehouse gespeichert ist.

## Verwandt:

* [Verbinden [!DNL Google Analytics Warehoused]](../integrations/google-analytics-warehoused.md)
