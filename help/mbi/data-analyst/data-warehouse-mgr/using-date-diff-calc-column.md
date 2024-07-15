---
title: Verwenden der Spalte "Datumsdifferenz berechnet"
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte Datumsdifferenz berechnet .
exl-id: 6ecab794-3466-4b3a-a929-3e56287522aa
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: 2433a614e9858684842804a0ae29fb67f0d41ead
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Datumsdifferenz berechnet Spalte

In diesem Thema werden der Zweck und die Verwendung der auf der Seite **[!DNL Manage Data > Data Warehouse]** verfügbaren Spalte mit der berechneten `Date Difference` -Zahl erläutert. Nachstehend finden Sie eine Erläuterung dessen, was es tut, gefolgt von einem Beispiel und der Methode, sie zu erstellen.

**Erklärung**

Der Spaltentyp `Date Difference` berechnet anhand der Zeitstempel des Ereignisses die Zeit zwischen zwei Ereignissen, die zu einem einzigen Datensatz gehören. Der in dieser Spalte berechnete Rohwert wird in Sekunden angegeben. Er wird jedoch automatisch in Minuten, Stunden, Tage usw. umgewandelt, um in Berichten angezeigt zu werden. Wenn Sie den Wert jedoch als Filter/Gruppe von verwenden, möchten Sie ihn in Sekunden verwenden.

Eine berechnete Spalte vom Typ `date difference` kann verwendet werden, um eine Metrik zu erstellen, die die durchschnittliche oder mittlere Zeit zwischen zwei Ereignissen berechnet, z. B. die durchschnittliche Zeit zwischen der Registrierung eines Kunden und seinen ersten Bestellungen.

**Beispiel**

| **`id`** | **`timestamp_1`** | **`timestamp_2`** | **`Seconds between timestamp_2 and timestamp_1`** |
|--- |--- |--- |--- |
| `A` | 01.01.2015 00:00:00 | 12.1.2015:30:00 | 45000 |
| `B` | 01.01.2015:00:00 | 10.01.2015 10:00:00 | 7200 |

{style="table-layout:auto"}


Im obigen Beispiel ist die Spalte `Date Difference` die Spalte `Seconds between timestamp_2 and timestamp_1` . Er führt die Berechnung `timestamp_2 minus timestamp_1` durch.

**Mechanics**

In den folgenden Schritten wird beschrieben, wie Sie eine `Date Difference` -Spalte erstellen.

1. Navigieren Sie zur Seite &quot;**[!DNL Manage Data > Data Warehouse]**&quot;.
1. Navigieren Sie zu der Tabelle, für die Sie diese Spalte erstellen möchten.
1. Klicken Sie auf **[!UICONTROL Create a Column]** und konfigurieren Sie Ihre Spalte wie folgt:
   * Wählen Sie `Column Definition Type` > `Same Table`
   * Wählen Sie `Column Definition Equation` > `DATE_DIFF = (Ending DATETIME - Starting DATETIME)`
   * Wählen Sie die Spalte `Ending DATETIME` aus > Wählen Sie das Feld für die Enddatumszeit aus, was normalerweise dem Ereignis entspricht, das später auftritt
   * Wählen Sie `Starting DATETIME` column** > Wählen Sie das Feld für den Startzeitpunkt aus, was normalerweise dem zuvor aufgetretenen Ereignis entspricht.

1. Geben Sie einen Namen für die Spalte ein und klicken Sie auf **[!UICONTROL Save]**.
1. Die Spalte ist verfügbar, um *unmittelbar* zu verwenden.

Im folgenden Beispiel wird zur Berechnung des `Seconds between order date and customer's creation date`-Werts konfiguriert:

![](../../assets/date_diff.png)
