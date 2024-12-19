---
title: Erwartete Data Warehouse-Daten der Google Analytics
description: Erfahren Sie, wie Sie mit den Data Warehouse von Google Analytics interagieren können.
exl-id: 2b1305cd-5f34-43d9-b77f-a4f5b1d82c66
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '355'
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

In Ihrem Data Warehouse wird eine einzige Tabelle namens `report` erstellt.

Das Schema dieser Tabelle besteht aus den Metriken und Dimensionen, die Sie während des Einrichtungsprozesses ausgewählt haben, sowie zwei weiteren Spalten: `start-date` und `end-date`.

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

Mit der [!DNL Google Analytics Live] Integration ist hingegen jedes [!DNL Google Analytics] wie ein kleines Silo, das nicht auf dem [!DNL Commerce Intelligence] Data Warehouse abgelegt ist.

## Verwandt:

* [Verbinden [!DNL Google Analytics Warehoused]](../integrations/google-analytics-warehoused.md)
