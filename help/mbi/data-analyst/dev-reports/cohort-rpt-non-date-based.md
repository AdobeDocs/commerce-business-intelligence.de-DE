---
title: Report Builder der Kohorte für nicht datumsbasierte Kohorten
description: Erfahren Sie, wie Sie Benutzer nach einer ähnlichen Aktivität oder einem ähnlichen Attribut gruppieren.
exl-id: c7b85ce9-113c-4ffc-855f-3d53fe2347d8
source-git-commit: 6b1bd96a0f9ae8bda3ae8db8ca78ad655079f2a4
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# [!DNL Cohort Report Builder] für nicht datumsbasierte Kohorten

Die [`Cohort Report Builder`](../dev-reports/cohort-rpt-bldr.md) ist eine großartige Möglichkeit für Händler, zu untersuchen, wie sich verschiedene Teilmengen von Benutzern im Laufe der Zeit verhalten. In der Vergangenheit wurde die `Cohort Report Builder` wurde für die Benutzergruppierung nach `cohort date` (z. B. der Satz aller Kunden, die in einem bestimmten Monat ihren ersten Kauf getätigt haben). Die `Non-Date Based Cohort` bietet Ihnen jetzt die Möglichkeit, Benutzer nach einer ähnlichen Aktivität oder einem ähnlichen Attribut zu gruppieren. Sehen Sie sich einige Anwendungsfälle für diese Funktion an.

## Nutzungsszenarios

Dies ist keine umfassende Liste, aber hier sind einige potenzielle Analysen, die mit dieser Funktion durchgeführt werden können.

* Prüfung des Umsatzes, den Kunden durch [!DNL Google] versus [!DNL Facebook]
* Analyse von Kunden, deren erster Kauf in den USA getätigt wurde, im Vergleich zu Kanada
* Betrachten Sie das Verhalten der Kunden, die durch verschiedene Werbekampagnen erworben wurden.

## Erstellen einer Analyse

1. Klicken **[!UICONTROL Report Builder]** auf der linken Registerkarte oder **[!UICONTROL Add Report** > **Create Report]** in jedem Dashboard.

1. Im `Report Builder Selection` Bildschirm, klicken Sie auf **[!UICONTROL Create Report]** neben dem `Visual Report Builder` -Option.

### Hinzufügen einer Metrik

Jetzt sind Sie im `Report Builder`, fügen Sie die Metrik hinzu, für die Sie die Analyse durchführen möchten (Beispiel: `Revenue` oder `Orders`).

>[!NOTE]
>
>Nativ [!DNL Google Analytics] -Metriken sind nicht mit der `Cohort Report Builder`. Ziel dieses Beispiels ist es, den Umsatz von Erstbestellern, die über verschiedene [!DNL Google Analytics] Quellen.

### Umschalten `Metric View` nach `Cohort`

![Umschalten der Metrikansicht zur Kohorte](../../assets/1-toggle-metric-view-to-cohort.png)

Dadurch wird ein neues Fenster geöffnet, in dem Sie die Details des Kohortenberichts konfigurieren können.

Zum Erstellen eines Kohortenberichts sind fünf Spezifikationen erforderlich:

1. Gruppieren der Kohorten
1. Kohorten auswählen
1. Zeitstempel der Aktion
1. Zeitraum der ersten Aktion der Kohorte
1. Zeitraum nach Auftreten der Kohorte

![Kohortengruppen](../../assets/2-cohort-groups.png)<!--{: width="200" height="224"}-->

!![cohort-first-action-time-range]<!--(../../assets/3-cohort-first-action-time-range.png){: width="400" height="554"}-->

#### 1. Gruppierung `cohorts`

`Cohorts` nach einem Verhaltenscharakter gruppiert werden, in diesem Beispiel `Customer's first order GA source`. Die hier verfügbaren Optionen sind Spalten, die bereits als `groupable` für die Metrik.

#### 2. Auswahl der Kohorten

Sie können alle Ergebnisse für das angegebene Merkmal anzeigen. Da dies viele `cohorts`, können Sie die spezifische `cohorts` (entspricht den verschiedenen verfügbaren Werten für `Customer's first order GA source`), die Sie benötigen.

![Kohortengruppen](../../assets/4-cohort-groups.png)<!--{: width="300" height="338"}-->

#### 3. `Action timestamp`

Auf diese Weise können Sie eine datumsbasierte Spalte auswählen, die nicht mit der Spalte übereinstimmt, auf der die Metrik erstellt wird. Unten sehen Sie, wie Sie den Zeitraum auswählen, der für die angegebene `action timestamp`.

#### 4. `Cohort first action time range`

Hier wählen Sie den Datumsbereich aus, der die Variable `cohorts action timestamp` (d. h. Kunden, die die erste Bestellung von November 2017 bis Oktober 2018 aufgegeben haben). Dabei kann es sich um einen sich bewegenden Datumsbereich oder einen festen Datumsbereich handeln.

#### 5. `Time range after cohort occurrence`

Möchten Sie die `cohorts` über Zeit nach Monat, Woche oder Jahr? Hier erfolgt die Auswahl. Unter diesem Abschnitt wählen Sie die `time range` nach `cohort action timestamp` aufgetreten. Dies zeigt beispielsweise Daten aus 12 Monaten für die Kunden, die innerhalb des Aktionszeitraums die erste Bestellung aufgegeben haben.

![cohort-first-action-time-range](../../assets/5-cohort-first-action-time-range.png)<!--{: width="400" height="557"}-->

>[!NOTE]
>
>[!UICONTROL Filters] auf Ihre Metriken angewendet werden, bleiben intakt, wenn Sie zwischen `Standard` und `Cohort` Ansichten.

### Verwandte

Siehe [`Perspectives`](../../data-analyst/dev-reports/cohort-rpt-bldr.md).
