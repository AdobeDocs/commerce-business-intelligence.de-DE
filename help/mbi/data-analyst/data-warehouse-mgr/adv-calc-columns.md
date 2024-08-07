---
title: Erweiterte berechnete Spaltentypen
description: Lernen Sie die Grundlagen für die meisten Anwendungsspaltenfälle kennen - Sie können jedoch eine berechnete Spalte wünschen, die etwas komplexer ist als das, was der Data Warehouse Manager erstellen kann.
exl-id: 9871fa19-95b3-46e4-ae2d-bd7c524d12db
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# Erweiterte berechnete Spaltentypen

Bei vielen Analysen, die Sie erstellen möchten, wird möglicherweise eine **neue Spalte** verwendet, die Sie `group by` oder `filter by` verwenden möchten. Das Tutorial zum Erstellen berechneter Spalten ](../data-warehouse-mgr/creating-calculated-columns.md) umfasst die Grundlagen für die meisten Anwendungsfälle. Sie können jedoch eine berechnete Spalte wünschen, die etwas komplexer ist als das, was der Data Warehouse Manager erstellen kann.
[
{: #top}

Diese Spaltenarten können vom Adobe-Team der Data Warehouse-Analysten erstellt werden. Um eine neue berechnete Spalte zu definieren, geben Sie die folgenden Informationen an:

1. Die **`definition`** dieser Spalte (einschließlich Eingabe, Formeln oder Formatierung)
1. Die **`table`** , für die Sie die Spalte erstellen möchten
1. Beliebige **`example data points`** , die beschreiben, was die Spalte enthalten soll

Im Folgenden finden Sie einige gängige Beispiele für erweiterte berechnete Spalten, die für Benutzer häufig nützlich sind:

* [Ereignis sequenziell sortieren (oder ordnen)](#compareevents)
* [Ermitteln der Zeit zwischen zwei Ereignissen](#twoevents)
* [Vergleich sequenzieller Ereigniswerte](#sequence)
* [Währung konvertieren](#currency)
* [Zeitzonen konvertieren](#timezone)
* [Sonstiges](#else)

## Ich versuche, Ereignisse sequenziell zu ordnen {#compareevents}

Dies wird als berechnete Spalte mit der **Ereignisnummer** bezeichnet. Das bedeutet, dass Sie versuchen, die Sequenz zu finden, in der Ereignisse für einen bestimmten Ereigniseigentümer aufgetreten sind, z. B. einen Kunden oder Benutzer.

Im Folgenden finden Sie ein Beispiel:

| **`event\_id`** | **`owner\_id`** | **`timestamp`** | **`Owner's event number`** |
|-----|-----|-----|-----|
| 1 | `A` | 01.01.2015 00:00:00 | 1 |
| 2 | `B` | 01.01.2015 00:30:00 | 1 |
| 3 | `A` | 01.01.2015:00:00 | 2 |
| 4 | `A` | 2015-01-02 13:00:00 | 3 |
| 5 | `B` | 03.01.2015 13:00:00 | 2 |

{style="table-layout:auto"}

Eine Spalte mit der berechneten Ereignisnummer kann verwendet werden, um Unterschiede im Verhalten zwischen Erstereignissen, Wiederholungsereignissen oder n Ereignissen in Ihren Daten zu erkennen.

Möchten Sie die Spalte mit der Bestellnummer des Kunden in Aktion sehen? Klicken Sie auf das Bild, um es als Dimension vom Typ Gruppe nach in einem Bericht zu sehen.

![Verwenden einer Spalte mit der berechneten Ereignisnummer zur Gruppierung nach der Bestellnummer des Kunden.](../../assets/EventNumber.gif)<!--{: style="max-width: 500px;"}-->

Um diesen Typ berechneter Spalten zu erstellen, müssen Sie Folgendes wissen:

* Die Tabelle, auf der Sie diese Spalte erstellen möchten
* Das Feld, das den Eigentümer der Ereignisse angibt (`owner\_id` in diesem Beispiel)
* Das Feld, nach dem die Ereignisse sortiert werden sollen (`timestamp` in diesem Beispiel)

[Zurück zum Anfang](#top)

## Ich versuche, die Zeit zwischen zwei Ereignissen zu finden. {#twoevents}

Dies wird als berechnete Spalte vom Typ `date difference` bezeichnet. Dies bedeutet, dass Sie versuchen, die Zeit zwischen zwei Ereignissen zu finden, die zu einem einzigen Datensatz gehören, basierend auf den Ereignis-Zeitstempeln.

Im Folgenden finden Sie ein Beispiel:

| `id` | `timestamp\_1` | `timestamp\_2` | `Seconds between timestamp\_2 and timestamp\_1` |
|-----|-----|-----|-----|
| `A` | 01.01.2015 00:00:00 | 12.1.2015:30:00 | 45000 |
| `B` | 01.01.2015:00:00 | 10.01.2015 10:00:00 | 7200 |

{style="table-layout:auto"}

Eine berechnete Datumsdifferenz -Spalte kann verwendet werden, um eine Metrik zu erstellen, die die durchschnittliche oder mittlere Zeit zwischen zwei Ereignissen berechnet. Klicken Sie auf das folgende Bild, um zu sehen, wie die Metrik `Average time to first order` in einem Bericht verwendet wird.

![Verwenden einer Spalte mit der Datumsdifferenz, die berechnet wird, um die durchschnittliche Zeit bis zur ersten Bestellung zu berechnen.](../../assets/DateDifference.gif)<!--{: style="max-width: 500px;"}-->

Um diesen Typ berechneter Spalten zu erstellen, müssen Sie Folgendes wissen:

* Die Tabelle, auf der Sie diese Spalte erstellen möchten
* Die beiden Zeitstempel, zwischen denen Sie den Unterschied kennen möchten

[Zurück zum Anfang](#top)

## Ich versuche, sequenzielle Ereigniswerte zu vergleichen. {#sequence}

Dies wird als **sequenzieller Ereignisvergleich** bezeichnet. Das bedeutet, dass Sie versuchen, die Differenz zwischen einem Wert (Währung, Zahl, Zeitstempel) und dem entsprechenden Wert für das vorherige Ereignis des Eigentümers zu finden.

Im Folgenden finden Sie ein Beispiel:

| **`event\_id`** | **`owner\_id`** | **`timestamp`** | **`Seconds since owner's previous event`** |
|-----|-----|-----|-----|
| 1 | `A` | 01.01.2015 00:00:00 | NULL |
| 2 | `B` | 01.01.2015 00:30:00 | NULL |
| 3 | `A` | 01.01.2015:00:00 | 7720 |
| 4 | `A` | 2015-01-02 13:00:00 | 126000 |
| 5 | `B` | 03.01.2015 13:00:00 | 217800 |

{style="table-layout:auto"}

Ein sequenzieller Ereignisvergleich kann verwendet werden, um die durchschnittliche oder mittlere Zeit zwischen den einzelnen sequenziellen Ereignissen zu ermitteln. Klicken Sie auf das folgende Bild, um die Metriken **Durchschnittliche und mittlere Zeit zwischen Bestellungen** in Aktion anzuzeigen.

=![Verwenden einer Spalte mit einem sequenziellen Ereignisvergleich, die berechnet wird, um die durchschnittliche und die mittlere Zeit zwischen Bestellungen zu berechnen.](../../assets/SeqEventComp.gif)<!--{: style="max-width: 500px;"}-->

Um diesen Typ berechneter Spalten zu erstellen, müssen Sie Folgendes wissen:

* Die Tabelle, auf der Sie diese Spalte erstellen möchten
* Das Feld, das den Eigentümer der Ereignisse angibt (`owner\_id` im Beispiel)
* Das Wertefeld, das den Unterschied zwischen den einzelnen sequenziellen Ereignissen anzeigen soll (`timestamp` in diesem Beispiel)

[Zurück zum Anfang](#top)

## Ich versuche, die Währung umzurechnen. {#currency}

Eine berechnete Spalte mit der **Währungsumrechnung** konvertiert Transaktionsbeträge von einer aufgezeichneten Währung in eine Berichtswährung, basierend auf dem Wechselkurs zum Zeitpunkt des Ereignisses.

Im Folgenden finden Sie ein Beispiel:

| **`id`** | **`timestamp`** | **`transaction\_value\_EUR`** | **`transaction\_value\_USD`** |
|-----|-----|-----|-----|
| `1` | 01.01.2015 00:00:00 | 30 | 33,57 |
| `2` | 2015-01-02 00:00:00 | 50 | 55,93 |

{style="table-layout:auto"}

Um diesen Typ berechneter Spalten zu erstellen, müssen Sie Folgendes wissen:

* Die Tabelle, auf der Sie diese Spalte erstellen möchten
* Die Spalte des Transaktionsbetrags, die konvertiert werden soll
* Die Spalte, die die Währung angibt, in der die Daten aufgezeichnet wurden (normalerweise ein ISO-Code)
* Die bevorzugte Berichtswährung

[Zurück zum Anfang](#top)

## Ich versuche, Zeitzonen zu konvertieren. {#timezone}

Eine berechnete Spalte mit **Zeitzonenkonvertierung** konvertiert die Zeitstempel für eine bestimmte Datenquelle aus ihrer aufgezeichneten Zeitzone in eine Berichterstellungszeitzone.

Im Folgenden finden Sie ein Beispiel:

| **`id`** | **`timestamp\_UTC`** | **`timestamp\_ET`** |
|-----|-----|-----|
| `1` | 01.01.2015 00:00:00 | 12.12.2014 19:00:00 |
| `2` | 12.1.2015:00:00 | 01.01.2015:00:00 |

{style="table-layout:auto"}

Um diesen Typ berechneter Spalten zu erstellen, müssen Sie Folgendes wissen:

* Die Tabelle, auf der Sie diese Spalte erstellen möchten
* Die Zeitstempelspalte, die konvertiert werden soll
* Die Zeitzone, in der die Daten aufgezeichnet wurden
* Die bevorzugte Zeitzone für die Berichterstellung

[Zurück zum Anfang](#top)

## Ich versuche, etwas zu tun, das hier nicht aufgeführt ist. {#else}

Keine Sorge. Nur weil es hier nicht aufgeführt ist, bedeutet das nicht, dass es nicht möglich ist. Das Adobe-Team von Data Warehouse-Analysten kann helfen.

Um eine neue berechnete Spalte zu definieren, senden [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) mit Details zu dem, was Sie erstellen möchten.

## Verwandte Dokumentation

* [Berechnete Spalten erstellen](../data-warehouse-mgr/creating-calculated-columns.md)
* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md)
* [Erstellen von [!DNL Google ECommerce] Dimensionen mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
