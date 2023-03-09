---
title: Verwenden der Spalte "Datumsdifferenz berechnet"
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte Datumsdifferenz berechnet .
exl-id: 6ecab794-3466-4b3a-a929-3e56287522aa
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 2%

---

# Datumsdifferenz berechnet Spalte

In diesem Thema werden Zweck und Verwendung der `Date Difference` in der Spalte **[!DNL Manage Data > Data Warehouse]** Seite. Nachstehend finden Sie eine Erläuterung dessen, was es tut, gefolgt von einem Beispiel und der Methode, sie zu erstellen.

**Erklärung**

Die `Date Difference` Spaltentyp: findet die Zeit zwischen zwei Ereignissen, die zu einem einzelnen Datensatz gehören, basierend auf den Ereignis-Zeitstempeln. Der in dieser Spalte berechnete Rohwert wird in Sekunden angegeben. Er wird jedoch automatisch in Minuten, Stunden, Tage usw. umgewandelt, um in Berichten angezeigt zu werden. Wenn Sie den Wert jedoch als Filter/Gruppe von verwenden, möchten Sie ihn in Sekunden verwenden.

A `date difference` Eine berechnete Spalte kann verwendet werden, um eine Metrik zu erstellen, die die durchschnittliche oder mittlere Zeit zwischen zwei Ereignissen berechnet, z. B. die durchschnittliche Zeit zwischen der Registrierung eines Kunden und seinen ersten Bestellungen.

**Beispiel**

| **`id`** | **`timestamp_1`** | **`timestamp_2`** | **`Seconds between timestamp_2 and timestamp_1`** |
|--- |--- |--- |--- |
| `A` | 2015-01-01 00:00:00 | 2015-01-01 12:30:00 | 45000 |
| `B` | 2015-01-01 08:00:00 | 2015-01-01 10:00:00 | 7200 |

{style="table-layout:auto"}


Im obigen Beispiel wird die `Date Difference` Spalte ist `Seconds between timestamp_2 and timestamp_1` Spalte. Er führt die Berechnung durch `timestamp_2 minus timestamp_1`.

**Mechanik**

In den folgenden Schritten wird beschrieben, wie Sie eine `Date Difference` Spalte.

1. Navigieren Sie zum **[!DNL Manage Data > Data Warehouse]** Seite.
1. Navigieren Sie zu der Tabelle, für die Sie diese Spalte erstellen möchten.
1. Klicken **[!UICONTROL Create a Column]** und konfigurieren Sie Ihre Spalte wie folgt:
   * Auswählen `Column Definition Type` > `Same Table`
   * Auswählen `Column Definition Equation` > `DATE_DIFF = (Ending DATETIME - Starting DATETIME)`
   * Auswählen `Ending DATETIME` column > Wählen Sie das Enddatumszeitfeld aus, normalerweise das Ereignis, das später auftritt
   * Auswählen `Starting DATETIME` column** > Wählen Sie das Feld für den Startzeitpunkt aus, das normalerweise dem zuvor aufgetretenen Ereignis entspricht.

1. Geben Sie der Spalte einen Namen und klicken Sie auf **[!UICONTROL Save]**.
1. Die Spalte kann verwendet werden *sofort*.

Im folgenden Beispiel wird zur Berechnung der Variablen `Seconds between order date and customer's creation date`:

![](../../assets/date_diff.png)
