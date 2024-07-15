---
title: Dashboard-weite Filterung
description: Erfahren Sie, wie Sie Massenbearbeitungen aller Berichte in einem bestimmten Dashboard durchführen.
exl-id: 379d0027-8a7a-4062-a66a-4f06c37b806c
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Dashboard-weite Filterung

Mit einer Dashboard-weiten Filterung können Sie Massenbearbeitungen aller Berichte in einem bestimmten Dashboard vornehmen. Sie können dieselbe Analyse schnell über verschiedene Zeiträume oder für verschiedene Geschäfte anzeigen. Sie können die Leistung eines Vorjahres, Monats oder einer Woche einfach pro Geschäft vergleichen. Sie können ein komplettes Dashboard aktualisieren, um eine neu gestartete Kampagne aufzunehmen.

## Datumsfilter

Um den Datumsbereich oder das Intervall der Berichte in einem Dashboard zu ändern, klicken Sie auf das Kalendersymbol in der oberen rechten Ecke (![Kalender](../../assets/calendar-button.png)).

Sie können festlegen, dass Daten mit einem `Fixed Date Range` oder verschiedenen vorab berechneten `Moving Date Ranges` angezeigt werden:

![ Verschieben von Datumsbereichen](../../assets/moving_date_ranges.png)

Die Optionen für den anpassbaren Bereich `Last Full...` stellen den zuletzt vollständig abgeschlossenen Bereich dar, während `This...` der aktuelle, laufende Bereich ist. Wenn es beispielsweise Juni ist, lautet der `Last Full Month` _1. Mai - 31. Mai_, während der `This Month` der _1. Juni - Jetzt_ ist.

Oder erstellen Sie Ihre eigene `Custom Moving Range`\:

![benutzerdefinierter Bewegungsbereich](../../assets/custom-moving-range.png)

Wählen Sie auch aus, das Intervall zu ändern. Die Auswahl der Standardschaltfläche (![Zeitintervall Standard](../../assets/time_interval_default.png)) bedeutet, dass nur der Datumsbereich geändert wird:

![Zeitintervall](../../assets/time_interval.png)

Um alle Berichte auf ihren ursprünglichen Datumsbereich und ihr anfängliches Intervall wiederherzustellen, klicken Sie auf **[!UICONTROL Restore Defaults]** oder auf **[!UICONTROL Cancel]**.

Wenn Sie einen Datumsfilter für ein Dashboard angeben, wird dieser Filter nur auf dieses Dashboard angewendet. Sie wird nicht angewendet, wenn Sie zu anderen Dashboards navigieren.

>[!NOTE]
>
>Derzeit sind `Cohort Reports` und `SQL Reports` nicht enthalten, wenn Änderungen auf Dashboard-Ebene angewendet werden.

## Filter speichern

Um die Leistung eines bestimmten Stores zu analysieren, klicken Sie auf das Store-Symbol oben rechts (![Store-Filter](../../assets/store-filter.png)). Standardmäßig ist `Store Filter` auf `All Stores` gesetzt, was die Daten aller [Store-Ansichten](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-views.html) anzeigt, die auf Ihrer Commerce-Site verfügbar sind.

>[!NOTE]
>
>Ein Store-Filter ist für ein ganzes [!DNL Commerce Intelligence] -Konto aktiviert oder deaktiviert. Wenn ein Dashboard Berichte enthält, die nicht vom Filter betroffen sind (z. B. Berichte, die nicht auf [!DNL Adobe Commerce] -Daten basieren), werden diese Berichte bei Anwendung des Store-Filters nicht aktualisiert. Sie können [den Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) , wenn Sie der Meinung sind, dass ein Bericht auf der Grundlage der Store-Auswahl aktualisiert werden sollte, oder wenn Sie glauben, dass Ihr Konto-Store-Filter versehentlich deaktiviert ist.

Wenn Sie einen Store aus dem `Store Filter` auswählen, behält der Filter Ihre Auswahl bei, wenn Sie zwischen Dashboards navigieren. Wenn Sie Ihre Auswahl beibehalten, können Sie die Daten für den ausgewählten Store überall anzeigen, bis Sie &quot;`All Stores`&quot;auswählen.

## Filter für freigegebene Dashboards

Wenn bei freigegebenen Dashboards ein Benutzer den Datumsfilter konfiguriert, wird für andere Benutzer mit Zugriff auf das Dashboard derselbe Filter angewendet. Der Store-Filter gilt in diesem Fall jedoch nicht. Wenn der Dashboard-Eigentümer den Store-Filter konfiguriert und das Dashboard weitergibt, bleibt der konfigurierte Store-Filter nicht für einen anderen Benutzer bestehen. Benutzer müssen über [Bearbeitungszugriff](../../data-user/dashboards/share-dashboard-with-users.md) auf ein Dashboard verfügen, um die Dashboard-Filter anpassen zu können.
