---
title: Erwartete Google Analytics Warehouse-Daten
description: Erfahren Sie, wie Sie mit Ihren in Google Analytics gespeicherten Daten interagieren.
exl-id: 2b1305cd-5f34-43d9-b77f-a4f5b1d82c66
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Erwartet [!DNL Google Analytics] Warehouse-Daten

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../../administrator/user-management/user-management.md).

>[!NOTE]
>
>Einige Informationen wurden mit Zustimmung unserer Freunde unter [[!DNL Stitch]](https://www.stitchdata.com/docs/integrations/saas/google-analytics).

[!DNL Google Analytics Warehoused] Integration in [!DNL MBI] nutzt das [!DNL Google Analytics] [Core Reporting-API](https://developers.google.com/analytics/devguides/reporting/core/v3/).

>[!NOTE]
>
>Bestätigen Sie, dass alle verwendeten Dimensionen [kompatibel mit den Metriken](https://developers.google.com/analytics/devguides/reporting/core/dimsmets) Sie verwenden in `Report Builder`.

Eine einzige Tabelle namens `report` - wird in Ihrer Data Warehouse erstellt.

Das Schema dieser Tabelle setzt sich aus den Metriken und Dimensionen zusammen, die Sie während des Einrichtungsprozesses ausgewählt haben, sowie aus zwei weiteren Spalten: `start-date` und `end-date`.

Wenn Sie beispielsweise während der Einrichtung die folgenden Metriken und Dimensionen ausgewählt haben:

* `Metrics`: `ga:users`
* `Dimensions`: `ga:month`

Die Tabelle würde wie im folgenden Beispiel aussehen.

| **Spaltenname** | **Beschreibung** |
|-----|-----|
| `\_id` | Diese Spalte ist `primary key`. |
| `\_rjm\_record\_hash` | [!DNL MBI] eindeutige Kennung. Diese Spalte wird von [!DNL MBI]. |
| `\_updated\_at` | Diese Spalte enthält das letzte Mal, dass die Datenzeile aktualisiert wurde. Diese Spalte wird von [!DNL MBI]. |
| `start-date` | Identifikation des Tages, für den die Zeile ist. |
| `end-date` | Identifikation des Tages, für den die Zeile ist. |
| `month` | Ausgewählte Dimension: Monat der Sitzung, eine zweistellige Ganzzahl von 01 bis 12. |
| `users` | Ausgewählte Metrik: Die Gesamtzahl der Benutzer für den angeforderten Zeitraum. |

{style=&quot;table-layout:auto&quot;}

## Erinnerung: Unterschied zwischen Google Analytics Warehouse und Live-Integration

Der Hauptunterschied besteht darin, dass eine Integration gespeichert wird ([!DNL Google Analytics Warehoused]) und der andere nicht ([!DNL Google Analytics Live]). Im Falle von [!DNL Google Analytics Warehoused], ermöglicht dies die Manipulation Ihrer [!DNL Google Analytics] Daten und bietet Ihnen die Möglichkeit, [!DNL Google Analytics] und anderen Datenquellen, um eine aufschlussreiche Berichterstellung zu erstellen.

Schauen wir uns das einmal an [!DNL Google Analytics] Anzeigenkampagnen für ein Beispiel dessen, was aus Sicht der Manipulation möglich ist. Angenommen, Sie hatten mehrere Werbekampagnen für Q4 mit unterschiedlichen Namen. Die Kampagnen waren das Ergebnis einer spezifischen Marketinginitiative. Mit gespeicherten Daten können wir eine neue Spalte erstellen, die die betreffenden Kampagnennamen sucht und den Namen der Initiative für das 4. Quartal von `Operation Dumbo`.

Der Kombinationsaspekt ermöglicht Folgendes: [!DNL Google Analytics] Daten, die mit anderen Daten verknüpft werden sollen, um Analysen durchzuführen. Nehmen Sie beispielsweise `Total Time On Site By Ad Campaign` Daten aus [!DNL Google Analytics] und verbinden Sie es mit `Total Spent Per Campaign` Daten aus [!DNL Facebook Ads] um ein vollständiges Bild davon zu erhalten, wie viel Interaktion Sie kostet.

Mit dem [!DNL Google Analytics Live] Integration, [!DNL Google Analytics] Diagramm ist wie ein kleines Silo, das nicht in Ihrem [!DNL MBI] Data Warehouse.

## Verwandte:

* [Verbinden [!DNL Google Analytics Warehoused]](../integrations/google-analytics-warehoused.md)
