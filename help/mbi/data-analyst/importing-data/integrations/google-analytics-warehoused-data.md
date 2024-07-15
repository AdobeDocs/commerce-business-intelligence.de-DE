---
title: Erwartete Google Analytics Warehouse-Daten
description: Erfahren Sie, wie Sie mit Ihren Google Analytics-gespeicherten Daten interagieren können.
exl-id: 2b1305cd-5f34-43d9-b77f-a4f5b1d82c66
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Erwartete [!DNL Google Analytics Warehoused] Daten

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

>[!NOTE]
>
>Einige Informationen wurden mit Erlaubnis Ihrer Freunde bei [[!DNL Stitch]](https://www.stitchdata.com/docs/integrations/saas/google-analytics) verwendet.

Die Integration von [!DNL Google Analytics Warehoused] in [!DNL Commerce Intelligence] verwendet die [!DNL Google Analytics] [Core-Berichterstellungs-API](https://developers.google.com/analytics/devguides/reporting/core/v3/).

>[!NOTE]
>
>Um unerwartete oder unsinnige Ergebnisse zu vermeiden, vergewissern Sie sich, dass alle verwendeten Dimensionen [mit einer oder mehreren Metriken](https://ga-dev-tools.google/dimensions-metrics-explorer/) kompatibel sind, die Sie in den `Report Builder` verwenden.

Eine einzelne Tabelle - mit dem Namen `report` - wird in Ihrer Data Warehouse erstellt.

Das Schema dieser Tabelle besteht aus den Metriken und Dimensionen, die Sie während des Einrichtungsprozesses ausgewählt haben, sowie zwei weiteren Spalten: `start-date` und `end-date`.

Wenn Sie beispielsweise während der Einrichtung die folgenden Metriken und Dimensionen ausgewählt haben:

* `Metrics`: `ga:users`
* `Dimensions`: `ga:month`

Die Tabelle würde wie im folgenden Beispiel aussehen.

| **Spaltenname** | **Beschreibung** |
|-----|-----|
| `\_id` | Diese Spalte ist die `primary key`. |
| `\_rjm\_record\_hash` | [!DNL Commerce Intelligence] eindeutige Kennung. Diese Spalte wird von [!DNL Commerce Intelligence] erstellt. |
| `\_updated\_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. Diese Spalte wird von [!DNL Commerce Intelligence] erstellt. |
| `start-date` | Identifikation des Tages, für den die Zeile ist. |
| `end-date` | Identifikation des Tages, für den die Zeile ist. |
| `month` | Ausgewählte Dimension: Monat der Sitzung, eine zweistellige Ganzzahl von 01 bis 12. |
| `users` | Ausgewählte Metrik: Die Gesamtanzahl der Benutzer für den angeforderten Zeitraum. |

{style="table-layout:auto"}

## Was ist der Unterschied zwischen [!DNL Google Analytics Warehoused] und [!DNL Live Integration]

Der Hauptunterschied besteht darin, dass eine Integration gespeichert wird ([!DNL Google Analytics Warehoused]) und die andere nicht ([!DNL Google Analytics Live]). Bei [!DNL Google Analytics Warehoused] ermöglicht dies die Manipulation Ihrer [!DNL Google Analytics] -Daten und gibt Ihnen die Möglichkeit, [!DNL Google Analytics] und andere Datenquellen zu kombinieren, um aufschlussreiche Berichte zu erstellen.

Sehen Sie sich [!DNL Google Analytics] Anzeigenkampagnen an, um ein Beispiel dafür zu erhalten, was aus Sicht der Manipulation möglich ist. Angenommen, Sie hatten mehrere Werbekampagnen für Q4 mit unterschiedlichen Namen. Die Kampagnen waren das Ergebnis einer spezifischen Marketinginitiative. Mit gespeicherten Daten können Sie eine Spalte erstellen, in der die betreffenden Kampagnennamen gesucht werden und der für das 4. Quartal vorgesehene Initiativname `Operation Dumbo` zurückgegeben wird.

Durch den kombinierten Aspekt können [!DNL Google Analytics] -Daten mit anderen Daten verknüpft werden, um Analysen durchzuführen. Nehmen Sie beispielsweise `Total Time On Site By Ad Campaign` Daten von [!DNL Google Analytics] und vergleichen Sie sie mit `Total Spent Per Campaign` Daten von [!DNL Facebook Ads], um ein vollständiges Bild davon zu erhalten, wie viel Interaktion Sie kostet.

Bei der [!DNL Google Analytics Live] -Integration hingegen ähnelt jedes [!DNL Google Analytics] -Diagramm einem kleinen Silo, das nicht in Ihrer [!DNL Commerce Intelligence] -Data Warehouse gespeichert ist.

## Verwandte:

* [Verbinden [!DNL Google Analytics Warehoused]](../integrations/google-analytics-warehoused.md)
