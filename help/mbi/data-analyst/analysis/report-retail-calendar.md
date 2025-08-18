---
title: Berichterstattung über einen Einzelhandelskalender
description: Erfahren Sie, wie Sie die Struktur einrichten, um einen 4-5-4-Einzelhandelskalender in Ihrem - [!DNL Commerce Intelligence]  zu verwenden.
exl-id: 3754151c-4b0f-4238-87f2-134b8409e32b
role: Admin, Data Architect, Data Engineer, User
feature: Data Warehouse Manager, Reports, Dashboards
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Reporting über einen Einzelhandelskalender

Dieses Thema zeigt, wie Sie die Struktur einrichten, um einen [4-5-4 Einzelhandelskalender ](https://nrf.com/resources/4-5-4-calendar) Ihrem [!DNL Adobe Commerce Intelligence]-Konto zu verwenden. Der Visual Report Builder bietet unglaublich flexible Zeitbereiche, Intervalle und unabhängige Einstellungen. Alle diese Einstellungen funktionieren jedoch mit dem herkömmlichen monatlichen Kalender.

Da viele Kunden ihren Kalender so ändern, dass er Einzelhandels- oder Buchhaltungstermine verwendet, veranschaulichen die folgenden Schritte, wie Sie mit Ihren Daten arbeiten und Berichte mit Einzelhandelsterminen erstellen. Obwohl die folgenden Anweisungen auf den Einzelhandelskalender 4-5-4 verweisen, können Sie ihn für jeden spezifischen Kalender ändern, den Ihr Team verwendet, sei es finanziell oder nur in einem benutzerdefinierten Zeitrahmen.

Bevor Sie beginnen, sollten Sie [Datei-Uploader](../../data-analyst/importing-data/connecting-data/using-file-uploader.md) überprüfen und sicherstellen, dass Sie die `.csv` Datei verlängert haben. Dadurch wird sichergestellt, dass die Datumsangaben alle historischen Daten abdecken und in die Zukunft verschoben werden.

Diese Analyse enthält [erweiterte berechnete Spalten](../data-warehouse-mgr/adv-calc-columns.md).

## Erste Schritte

Sie [ eine ](../../assets/454-calendar.csv) Version `.csv` 4-5-4 Einzelhandelskalenders für die Einzelhandelsjahre 2014 bis 2017 herunterladen. Möglicherweise müssen Sie diese Datei an Ihren internen Einzelhandelskalender anpassen und den Datumsbereich erweitern, um Ihren historischen und aktuellen Zeitrahmen zu unterstützen. Verwenden Sie nach dem Herunterladen der Datei den Datei-Uploader, um eine Einzelhandelskalendertabelle in Ihrer [!DNL Commerce Intelligence] Data Warehouse zu erstellen. Wenn Sie eine unveränderte Version des Einzelhandelskalenders 4-5-4 verwenden, stellen Sie sicher, dass die Struktur und die Datentypen der Felder in dieser Tabelle den folgenden Werten entsprechen:

| Spaltenname | Spaltendatentyp | Primärer Schlüssel |
| --- | --- | --- |
| `Date Retail` | `Date & Time` | `Yes` |
| `Year Retail` | `Whole Number` | `No` |
| `Quarter Retail` | `Whole Number` | `No` |
| `Month Number Retail` | `Whole Number` | `No` |
| `Week Retail` | `Whole Number` | `No` |
| `Month Name Retail` | `Text` (bis zu 255 Zeichen) | `No` |
| `Week Number of Month Retail` | `Whole Number` | `No` |

{style="table-layout:auto"}

## Zu erstellende Spalten

* **sales\_order** Tabelle
   * `INPUT` `created\_at` (JJJJ-MM-TT 00:00:00)
      * [!UICONTROL Column type]: - `Same table > Calculation`
      * [!UICONTROL Inputs]: - `created\_at`
      * [!UICONTROL Datatype]: - `Datetime`
      * [!UICONTROL Calculation]: - ` case when A is null then null else to\_char(A, 'YYYY-MM-DD 00:00:00') end`

* **Einzelhandelskalender** Datei-Upload-Tabelle
   * **Aktuelles Datum**
      * [!UICONTROL Column type]: `Same table > Calculation`
      * [!UICONTROL Inputs]: `Date Retail`
      * 
        [!UICONTROL Datentyp]: `Datetime`
      * [!UICONTROL Calculation]: `case when A is null then null else to\_char(now(), 'YYYY-MM-DD 00:00:00') end`

        >[!NOTE]
        >
        >Die obige `now()` ist spezifisch für PostgreSQL. Obwohl die meisten [!DNL Commerce Intelligence] Data Warehouses auf PostgreSQL gehostet werden, können einige auf Redshift gehostet werden. Wenn die obige Berechnung einen Fehler zurückgibt, müssen Sie möglicherweise die Redshift-Funktion `getdate()` anstelle von `now()` verwenden.

   * **Aktuelles Einzelhandelsjahr** (Muss von einem Support-Analysten erstellt werden)
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
        [!UICONTROL Datentyp]: `String`
      * [!UICONTROL Calculation]: `case when A is null or B is null then null when A = B then 'Yes' else 'No' end`
   * **Im vorigen Einzelhandelsjahr enthalten? (Ja/Nein)**
      * [!UICONTROL Column type]: `Same table > Calculation`
      * [!UICONTROL Inputs]:
         * `A` - `Year Retail`
         * `B` - `Current retail year`
      * 
        [!UICONTROL Datentyp]: String
      * [!UICONTROL Calculation]: `case when A is null or B is null then null when (A = (B-1)) then 'Yes' else 'No' end`

* **sales\_order** Tabelle
   * **Created\_at (Einzelhandelsjahr)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: `Retail Calendar.Date Retail`
      * [!UICONTROL table] auswählen: `Retail Calendar`
      * [!UICONTROL column] auswählen: `Year Retail`
   * **Created\_at (Einzelhandelswoche)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: sales\_order.\[INPUT\] created\_at (JJJJ-MM-TT 00:00:00
         * [!UICONTROL One]: retail calendar.date.retail
      * [!UICONTROL table] auswählen: `Retail Calendar`
      * [!UICONTROL column] auswählen: `Week Retail`
   * **Created\_at (Einzelhandelsmonat)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: `Retail Calendar.Date Retail`
      * [!UICONTROL table] auswählen: `Retail Calendar`
      * [!UICONTROL column] auswählen: `Month Number Retail`
   * **Im vorigen Einzelhandelsjahr einbeziehen? (Ja/Nein)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: `Calendar.Date Retail`
      * [!UICONTROL table] auswählen: `Retail Calendar`
      * [!UICONTROL column] auswählen: `Include in previous retail year? (Yes/No)`
   * **Im aktuellen Einzelhandelsjahr einbeziehen? (Ja/Nein)**
      * [!UICONTROL Column type]: `One to Many > JOINED\_COLUMN`
      * Pfad -
         * [!UICONTROL Many]: `sales\_order.\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`
         * [!UICONTROL One]: `Calendar.Date Retail`
      * [!UICONTROL table] auswählen: `Retail Calendar`
      * [!UICONTROL column] auswählen: `Include in current retail year? (Yes/No)`

## Metriken

Hinweis: Für diese Analyse sind keine neuen Metriken erforderlich. Achten Sie jedoch darauf, [die neuen Spalten, die Sie in der Tabelle „sales\_order“ als Dimensionen erstellt haben](../data-warehouse-mgr/manage-data-dimensions-metrics.md) für alle Metriken in der Tabelle „sales\_order“ hinzuzufügen, bevor Sie mit den Berichten fortfahren.

## Berichte

* **Wöchentliche Bestellungen - Einzelhandelskalender (JJ)**
   * `A`: `2017`
      * [!UICONTROL Metric]: Anzahl der Bestellungen
      * [!UICONTROL Filter]:
         * Erstellt\_at (Einzelhandelsjahr) = 2017
   * `B`: `2016`
      * [!UICONTROL Metric]: Anzahl der Bestellungen
      * [!UICONTROL Filter]:
         * Erstellt\_at (Einzelhandelsjahr) = 2016
   * `C`: `2015`
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
      * `multiple Y-axes` ausschalten

* **Einzelhandelskalender - Übersicht (aktuelles Einzelhandelsjahr nach Monat)**
   * `A`: `Revenue`
      * 
        [!UICONTROL-Metrik]: `Revenue`
      * [!UICONTROL Filter]:
         * 
           [!UICONTROL Include current retail year?]: `Yes`
   * `B`: `Orders`
      * [!UICONTROL Metric]: `Number of orders`
      * [!UICONTROL Filter]:
         * 
           [!UICONTROL Include current retail year?]: `Yes`
   * `C`: `Avg order value`
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

* **Einzelhandelskalender - Übersicht (vorheriges Einzelhandelsjahr nach Monat)**
   * `A`: `Revenue`
      * 
        [!UICONTROL-Metrik]: `Revenue`
      * [!UICONTROL Filter]:
         * 
           [!UICONTROL Include current retail year?]: `Yes`
   * `B`: `Orders`
      * [!UICONTROL Metric]: Anzahl der Bestellungen
      * [!UICONTROL Filter]:
         * 
           [!UICONTROL Include current retail year?]: `Yes`
   * `C`: `Avg order value`
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

Oben wird beschrieben, wie Sie einen Einzelhandelskalender so konfigurieren, dass er mit jeder Metrik kompatibel ist, die auf Ihrer `sales\_order`-Tabelle erstellt wird (z. B. `Revenue` oder `Orders`). Sie können dies auch erweitern, um den Einzelhandelskalender für Metriken zu unterstützen, die auf einer beliebigen Tabelle basieren. Die einzige Anforderung besteht darin, dass diese Tabelle über ein gültiges Datums-/Uhrzeitfeld verfügt, das zum Verbinden mit der Einzelhandelskalendertabelle verwendet werden kann.

Um beispielsweise Metriken auf Kundenebene in einem Einzelhandelskalender der Kategorien 4-5-4 anzuzeigen, erstellen Sie eine `Same Table` Berechnung in der `customer\_entity`, ähnlich wie oben beschrieben `\[INPUT\] created\_at (yyyy-mm-dd 00:00:00)`. Sie können diese Spalte dann verwenden, um die `One to Many` JOINED\_COLUMN-Berechnungen (wie `Created_at (retail year)`) und `Include in previous retail year? (Yes/No)` zu reproduzieren, indem Sie die Tabelle `customer\_entity` mit der Tabelle `Retail Calendar` verbinden.

Vergessen Sie nicht, [alle neuen Spalten als Dimensionen zu Metriken hinzuzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md) bevor Sie neue Berichte erstellen.
