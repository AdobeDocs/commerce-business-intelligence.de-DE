---
title: Dashboard-weite Filterung
description: Erfahren Sie, wie Sie Massenbearbeitungen aller Berichte in einem bestimmten Dashboard durchführen.
exl-id: 379d0027-8a7a-4062-a66a-4f06c37b806c
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/6wixrQXkvGMF9c36wrGJ4Qj23HqJ--Mr0XMYMBhujjo
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 449
ht-degree: 0%

---

# Dashboard-weite Filterung

Mit der Dashboard-weiten Filterung können Sie Massenbearbeitungen aller Berichte in einem bestimmten Dashboard durchführen. Sie können dieselbe Analyse schnell über verschiedene Zeiträume oder für verschiedene Stores anzeigen. Sie können die Leistung eines Vorjahres, eines Monats oder einer Woche pro Geschäft leicht vergleichen. Sie können ein ganzes Dashboard aktualisieren, um eine neu gestartete Kampagne aufzunehmen.

## Datumsfilter

Um den Datumsbereich oder das Intervall von Berichten in einem Dashboard zu ändern, klicken Sie auf das Kalendersymbol in der oberen rechten Ecke (![Kalender](../../assets/calendar-button.png)).

Sie können Daten mithilfe eines `Fixed Date Range` oder verschiedener vorberechneter `Moving Date Ranges` anzeigen:

![Verschieben von Datumsbereichen](../../assets/moving_date_ranges.png)

Die Optionen für den `Last Full...` Bereich für bewegte Bereiche stellen den zuletzt vollständig abgeschlossenen Bereich dar, während `This...` der aktuelle Bereich für laufende Prozesse ist. Wenn es zum Beispiel Juni ist, lautet der `Last Full Month` _1. Mai - 31._, während `This Month` ist _1. Juni - Jetzt_.

Oder erstellen Sie Ihr eigenes `Custom Moving Range`\:

![Benutzerdefinierter Verschiebungsbereich](../../assets/custom-moving-range.png)

Wählen Sie auch aus, das Intervall zu ändern. Durch Auswahl der Schaltfläche Standard ![Standardzeitintervall](../../assets/time_interval_default.png) wird nur der Datumsbereich geändert:

![Zeitintervall](../../assets/time_interval.png)

Um alle Berichte in ihrem ursprünglichen Datumsbereich und Intervall wiederherzustellen, klicken Sie auf **[!UICONTROL Restore Defaults]** oder auf **[!UICONTROL Cancel]**.

Wenn Sie einen Datumsfilter für ein Dashboard angeben, wird dieser Filter nur auf dieses Dashboard angewendet. Sie wird nicht angewendet, wenn Sie zu anderen Dashboards navigieren.

>[!NOTE]
>
>Derzeit sind `Cohort Reports` und `SQL Reports` beim Anwenden von Änderungen auf Dashboard-Ebene nicht enthalten.

## Filter speichern

Um zu analysieren, wie sich ein bestimmter Store entwickelt, klicken Sie auf das Store-Symbol in der oberen rechten Ecke (![Store-Filter](../../assets/store-filter.png)). Standardmäßig ist `Store Filter` auf `All Stores` festgelegt, wodurch die Daten aus allen [Store-Ansichten](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-views.html) angezeigt werden, die auf Ihrer Commerce-Site verfügbar sind.

>[!NOTE]
>
>Ein Speicherfilter ist für ein ganzes [!DNL Commerce Intelligence]-Konto aktiviert oder deaktiviert. Wenn ein Dashboard Berichte enthält, die nicht vom Filter betroffen sind (z. B. Berichte, die nicht auf [!DNL Adobe Commerce] Daten basieren), werden diese Berichte nicht aktualisiert, wenn der Speicherfilter angewendet wird. Sie können [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) wenn Sie der Meinung sind, dass ein Bericht basierend auf der Store-Auswahl aktualisiert werden sollte oder wenn Sie der Meinung sind, dass Ihr Account-Store-Filter versehentlich deaktiviert ist.

Wenn Sie einen Store aus der `Store Filter` auswählen, behält der Filter Ihre Auswahl bei, wenn Sie zwischen Dashboards navigieren. Wenn Sie Ihre Auswahl beibehalten, können Sie Daten für Ihren ausgewählten Store überall anzeigen, bis Sie `All Stores` auswählen.

## Filter für freigegebene Dashboards

Wenn bei gemeinsam genutzten Dashboards ein Benutzer den Datumsfilter konfiguriert, wird derselbe Filter auf andere Benutzer mit Zugriff auf das Dashboard angewendet. Der Speicherfilter ist in diesem Fall jedoch nicht anwendbar. Wenn der Dashboard-Inhaber den Store-Filter konfiguriert und das Dashboard freigibt, bleibt der konfigurierte Store-Filter nicht für einen anderen Benutzer erhalten. Ein Benutzer muss [Bearbeitungszugriff](../../data-user/dashboards/share-dashboard-with-users.md) auf ein Dashboard haben, um die Dashboard-Filter anpassen zu können.
