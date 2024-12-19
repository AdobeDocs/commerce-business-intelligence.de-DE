---
title: Verwenden der berechneten Spalte „Datumsdifferenz“
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte „Datumsdifferenz berechnet“.
exl-id: 6ecab794-3466-4b3a-a929-3e56287522aa
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: 2433a614e9858684842804a0ae29fb67f0d41ead
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Berechnete Spalte „Datumsdifferenz“

In diesem Thema werden der Zweck und die Verwendung der `Date Difference` berechneten Spalte auf der **[!DNL Manage Data > Data Warehouse]** Seite beschrieben. Nachfolgend finden Sie eine Erläuterung der Funktionen, gefolgt von einem Beispiel und den Methoden zu seiner Erstellung.

**Erläuterung**

Der `Date Difference` Spaltentyp berechnet die Zeit zwischen zwei Ereignissen, die zu einem einzelnen Datensatz gehören, basierend auf den Ereignis-Zeitstempeln. Der in dieser Spalte berechnete Rohwert beträgt in Sekunden, er wird jedoch automatisch in Minuten, Stunden, Tage usw. konvertiert, um ihn in Berichten anzuzeigen. Bei Verwendung als Filter/Gruppieren nach sollte der Wert jedoch in Sekunden verwendet werden.

Eine `date difference` berechnete Spalte kann verwendet werden, um eine Metrik zu erstellen, die die durchschnittliche oder mediane Zeit zwischen zwei Ereignissen berechnet, z. B. die durchschnittliche Zeit zwischen der Kundenregistrierung und ihren ersten Bestellungen.

**Beispiel**

| **`id`** | **`timestamp_1`** | **`timestamp_2`** | **`Seconds between timestamp_2 and timestamp_1`** |
|--- |--- |--- |--- |
| `A` | 01.01.2015 00:00:00 | 01.01.2015 12:30:00 | 45000 |
| `B` | 01.01.2015 08:00:00 | 01.01.2015 10:00:00 | 7200 |

{style="table-layout:auto"}


Im obigen Beispiel ist die Spalte `Date Difference` die Spalte `Seconds between timestamp_2 and timestamp_1` . Er führt die `timestamp_2 minus timestamp_1` durch.

**Mechanik**

Die folgenden Schritte beschreiben, wie Sie eine `Date Difference` erstellen.

1. Navigieren Sie zur **[!DNL Manage Data > Data Warehouse]**.
1. Navigieren Sie zu der Tabelle, in der Sie diese Spalte erstellen möchten.
1. Klicken Sie auf **[!UICONTROL Create a Column]** und konfigurieren Sie Ihre Spalte wie folgt:
   * Wählen Sie `Column Definition Type` > `Same Table`
   * Wählen Sie `Column Definition Equation` > `DATE_DIFF = (Ending DATETIME - Starting DATETIME)`
   * Wählen Sie `Ending DATETIME` Spalte aus und wählen Sie das Feld Enddatum und -uhrzeit aus, was normalerweise das Ereignis ist, das später auftritt
   * Wählen Sie `Starting DATETIME` Spalte ** > Wählen Sie das Feld Anfangsdatum/Uhrzeit , das normalerweise das früher auftretende Ereignis ist

1. Geben Sie der Spalte einen Namen und klicken Sie auf **[!UICONTROL Save]**.
1. Die Spalte kann (sofort *verwendet*.

Als Beispiel wird das folgende Beispiel konfiguriert, um die `Seconds between order date and customer's creation date` zu berechnen:

![](../../assets/date_diff.png)
