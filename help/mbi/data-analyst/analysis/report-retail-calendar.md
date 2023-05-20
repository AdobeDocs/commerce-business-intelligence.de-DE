---
title: Berichterstellung für einen Einzelhandelskalender
description: Erfahren Sie, wie Sie die Struktur für die Verwendung eines 4-5-4-Einzelhandelskalenders in Ihrem [!DNL Commerce Intelligence] -Konto.
exl-id: 3754151c-4b0f-4238-87f2-134b8409e32b
source-git-commit: 4cad1e05502630e13f7a2d341f263140a02b3d82
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Berichterstellung für einen Einzelhandelskalender

Dieses Thema zeigt, wie die Struktur für die Verwendung einer [4-5-4 Einzelhandelskalender](https://nrf.com/resources/4-5-4-calendar) in [!DNL Adobe Commerce Intelligence] -Konto. Der visuelle ReportBuilder bietet unglaublich flexible Zeiträume, Intervalle und unabhängige Einstellungen. Diese Einstellungen funktionieren jedoch mit dem herkömmlichen Monatskalender.

Da viele Kunden ihren Kalender ändern, um Handels- oder Rechnungsdaten zu verwenden, veranschaulichen die folgenden Schritte, wie Sie mit Ihren Daten arbeiten und Berichte mithilfe von Einzelhandelsdaten erstellen. Obwohl die folgenden Anweisungen auf den 4-5-4-Einzelhandelskalender verweisen, können Sie sie für jeden bestimmten Kalender ändern, den Ihr Team verwendet, egal ob es sich um einen finanziellen oder nur einen benutzerdefinierten Zeitrahmen handelt.

Bevor Sie beginnen, sollten Sie [Datei-Uploader](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) und stellen Sie sicher, dass Sie die `.csv` -Datei. Dadurch wird sichergestellt, dass die Daten alle Ihre historischen Daten abdecken und die Daten in die Zukunft verschieben.

Diese Analyse enthält [Erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Sie können [herunterladen](../../assets/454-calendar.csv) a `.csv` Version des 4-5-4 Einzelhandelskalenders für die Einzelhandelsjahre 2014 bis 2017. Möglicherweise müssen Sie diese Datei entsprechend Ihrem internen Einzelhandelskalender anpassen und den Datumsbereich erweitern, um Ihren historischen und aktuellen Zeitrahmen zu unterstützen. Verwenden Sie nach dem Herunterladen der Datei den Datei-Uploader, um eine Einzelhandelskalender-Tabelle in Ihrer [!DNL Commerce Intelligence] Data Warehouse. Wenn Sie eine unveränderte Version des 4-5-4-Einzelhandelskalenders verwenden, stellen Sie sicher, dass die Struktur und die Datentypen der Felder in dieser Tabelle mit Folgendem übereinstimmen:

| Spaltenname | Spaltendatentyp | Primärer Schlüssel |
| --- | --- | --- |
| `Date Retail` | `Date & Time` | `Yes` |
| `Year Retail` | `Whole Number` | `No` |
| `Quarter Retail` | `Whole Number` | `No` |
| `Month Number Retail` | `Whole Number` | `No` |
| `Week Retail` | `Whole Number` | `No` |
| `Month Name Retail` | `Text` (Bis zu 255 Zeichen) | `No` |
| `Week Number of Month Retail` | `Whole Number` | `No` |

{style="table-layout:auto"}

## Zu erstellende Spalten

* **sales\_order** table
   * `INPUT` `created\_at` (JJJJ-MM-TT 00:00:00)
      * [!UICONTROL Column type]: – `Same table > Calculation`
      * [!UICONTROL Inputs]: – `created\_at`
      * [!UICONTROL Datatype]: – `Datetime`
      * [!UICONTROL Calculation]: - ` case when A is null then null else to\_char(A, 'YYYY-MM-DD 00:00:00') end`

* **Einzelhandelskalender** Datei-Upload-Tabelle
   * **Aktuelles Datum**
      * [!UICONTROL Column type]: `Same table > Calculation`
      * [!UICONTROL Inputs]: `Date Retail`
      * 
         [!UICONTROL Datatype]: `Datetime`
      * [!UICONTROL Calculation]: `case when A is null then null else to\_char(now(), 'YYYY-MM-DD 00:00:00') end`

         >[!NOTE]
         >
         >Die `now()` -Funktion ist spezifisch für PostgreSQL. Obwohl [!DNL Commerce Intelligence] Data Warehouse wird auf PostgreSQL gehostet, einige werden möglicherweise auf Redshift gehostet. Wenn die obige Berechnung einen Fehler zurückgibt, müssen Sie möglicherweise die Redshift-Funktion verwenden `getdate()` anstelle von `now()`.
   * **Aktuelles Verkaufsjahr** (Muss von Support-Analyst erstellt werden)
      * [!UICONTROL Column type]: E`vent Counter`
      * [!UICONTROL Local Key]: `Current date`
      * [!UICONTROL Remote Key]: `Retail calendar.Date Retail`
      * 
         [!UICONTROL Operation]: `Max`
      * [!UICONTROL Operation value]: `Year Retail`
   * **Im aktuellen Einzelhandelsjahr enthalten? (Ja/Nein)**
      * [!UICONTROL Column type]: `Same table > Calculation`
      * [!UICONTROL Inputs]:
         * `A` - `Year Retail`
         * `B` - `Current retail year`
      * 
         [!UICONTROL Datatype]: `String`
      * [!UICONTROL Calculation]: `case when A is null or B is null then null when A = B then 'Yes' else 'No' end`
   * **Im vorigen Einzelhandelsjahr enthalten? (Ja/Nein)**
      * [!UICONTROL Column type]: `Same table > Calculation`
      * [!UICONTROL Inputs]:
         * `A` - `Year Retail`
         * `B` - `Current retail year`
      * 
         [!UICONTROL Datatype]: String
      * [!UICONTROL Calculation]: `case when A is null or B is null then null when (A = (B-1)) then 'Yes' else 'No' end`


* **sales\_order** table
   * **Erstellt\_at (Einzelhandelsjahr)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: `Retail Calendar.Date Retail`
      * Wählen Sie eine [!UICONTROL table]: `Retail Calendar`
      * Wählen Sie eine [!UICONTROL column]: `Year Retail`
   * **Erstellt\_at (Einzelhandelswoche)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00
         * [!UICONTROL One]: Einzelhandelskalender.Datum Einzelhandel
      * Wählen Sie eine [!UICONTROL table]: `Retail Calendar`
      * Wählen Sie eine [!UICONTROL column]: `Week Retail`
   * **Erstellt\_at (Einzelhandelsmonat)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: `Retail Calendar.Date Retail`
      * Wählen Sie eine [!UICONTROL table]: `Retail Calendar`
      * Wählen Sie eine [!UICONTROL column]: `Month Number Retail`
   * **Im vorherigen Einzelhandelsjahr einschließen? (Ja/Nein)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: Einzelhandel `Calendar.Date Retail`
      * Wählen Sie eine [!UICONTROL table]: `Retail Calendar`
      * Wählen Sie eine [!UICONTROL column]: `Include in previous retail year? (Yes/No)`
   * **Im aktuellen Einzelhandelsjahr einschließen? (Ja/Nein)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: Einzelhandel `Calendar.Date Retail`
      * Wählen Sie eine [!UICONTROL table]: `Retail Calendar`
      * Wählen Sie eine [!UICONTROL column]: `Include in current retail year? (Yes/No)`

## Metriken

Hinweis: Für diese Analyse sind keine neuen Metriken erforderlich. Stellen Sie jedoch sicher, dass [Fügen Sie die neuen Spalten hinzu, die Sie in der Tabelle sales\_order als Dimensionen erstellt haben](../data-warehouse-mgr/manage-data-dimensions-metrics.md) für alle Metriken in der Tabelle sales\_order , bevor Sie mit den Berichten fortfahren.

## Berichte

* **Wöchentliche Bestellungen - Einzelhandelskalender (YoY)**
   * Metrik `A`: `2017`
      * [!UICONTROL Metric]: Anzahl Bestellungen
      * [!UICONTROL Filter]:
         * Erstellt\_at (Einzelhandelsjahr) = 2017
   * Metrik `B`: `2016`
      * [!UICONTROL Metric]: Anzahl Bestellungen
      * [!UICONTROL Filter]:
         * Erstellt\_at (Einzelhandelsjahr) = 2016
   * Metrik `C`: `2015`
      * [!UICONTROL Metric]: `Number of orders`
      * [!UICONTROL Filter]:
         * `Created\_at (retail Year) = 2015`
   * [!UICONTROL Time period]: `All time`
   * 
      [!UICONTROL Interval]: `None`
   * 
      [!UICONTROL Group by]: `Created\_at` (retail week)
   * 
      [!UICONTROL Chart type]: `Line`
      * Ausschalten `multiple Y-axes`

* **Übersicht über den Einzelhandelskalender (aktuelles Einzelhandelsjahr nach Monat)**
   * Metrik `A`: `Revenue`
      * 
         [!UICONTROL Metrik]: `Revenue`
      * [!UICONTROL Filter]:
         * 
            [!UICONTROL Include current retail year?]: `Yes`
   * Metrik `B`: `Orders`
      * [!UICONTROL Metric]: `Number of orders`
      * [!UICONTROL Filter]:
         * 
            [!UICONTROL Include current retail year?]: `Yes`
   * Metrik `C`: `Avg order value`
      * [!UICONTROL Metric]: `Avg order value`
      * [!UICONTROL Filter]:
         * 
            [!UICONTROL Include current retail year?]: `Yes`
   * [!UICONTROL Time period]: `All time`
   * 
      [!UICONTROL Interval]: `None`
   * 
      [!UICONTROL Group by]: `Created\_at` (retail month)
   * 

      [!UICONTROL Chart type]: `Line`

* **Übersicht über den Einzelhandelskalender (letztes Einzelhandelsjahr nach Monat)**
   * Metrik `A`: `Revenue`
      * 
         [!UICONTROL Metrik]: `Revenue`
      * [!UICONTROL Filter]:
         * 
            [!UICONTROL Include current retail year?]: `Yes`
   * Metrik `B`: `Orders`
      * [!UICONTROL Metric]: Anzahl Bestellungen
      * [!UICONTROL Filter]:
         * 
            [!UICONTROL Include current retail year?]: `Yes`
   * Metrik `C`: `Avg order value`
      * [!UICONTROL Metric]: `Avg order value`
      * [!UICONTROL Filter]:
         * 
            [!UICONTROL Include current retail year?]: `Yes`
   * [!UICONTROL Time period]: `All time`
   * 
      [!UICONTROL Interval]: `None`
   * 
      [!UICONTROL Group by]: `Created\_at` (retail month)
   * 

      [!UICONTROL Chart type]: `Line`

## Nächste Schritte

Im obigen Abschnitt wird beschrieben, wie Sie einen Einzelhandelskalender so konfigurieren, dass er mit einer beliebigen Metrik kompatibel ist, die auf Ihrer `sales\_order` -Tabelle (z. B. `Revenue` oder `Orders`). Sie können dies auch erweitern, um den Einzelhandelskalender für Metriken zu unterstützen, die auf einer beliebigen Tabelle basieren. Die einzige Anforderung besteht darin, dass diese Tabelle über ein gültiges Datum-Uhrzeit-Feld verfügt, das verwendet werden kann, um zur Einzelhandelskalender-Tabelle beizutreten.

Um beispielsweise Metriken auf Kundenebene in einem 4-5-4 Einzelhandelskalender anzuzeigen, erstellen Sie eine `Same Table` der `customer\_entity` -Tabelle ähnlich `\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)` weiter oben beschrieben. Diese Spalte kann dann zum Reproduzieren der `One to Many` JOINED\_COLUMN-Berechnungen (z. B. `Created_at (retail year)`) und `Include in previous retail year? (Yes/No)` durch Teilnahme an `customer\_entity` -Tabelle `Retail Calendar` Tabelle.

Vergessen Sie nicht, [Metriken alle neuen Spalten als Dimensionen hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) vor der Erstellung neuer Berichte.
