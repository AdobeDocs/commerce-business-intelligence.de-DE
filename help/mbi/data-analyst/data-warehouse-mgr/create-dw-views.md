---
title: Erstellen und Verwenden von Data Warehouse-Ansichten
description: Erfahren Sie mehr über eine Methode zum Erstellen neuer in Lagern gespeicherter Tabellen durch Ändern einer vorhandenen Tabelle oder durch Zusammenführen oder Konsolidieren mehrerer Tabellen mithilfe von SQL.
exl-id: 5aa571c9-7f38-462c-8f1b-76a826c9dc55
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 9%

---

# Arbeiten mit Data Warehouse-Ansichten

In diesem Dokument werden der Zweck und die Verwendung von `Data Warehouse Views` durch Navigieren zu **[!UICONTROL Manage Data]** > **[!UICONTROL Data Warehouse Views]**. Im Folgenden finden Sie eine Erläuterung der Funktion und der Erstellung von Ansichten sowie ein Beispiel für die Verwendung von `Data Warehouse Views` zur Konsolidierung [!DNL Facebook] und [!DNL AdWords] Daten ausgeben.

## Allgemeiner Zweck

Die `Data Warehouse Views` -Funktion ist eine Methode zum Erstellen neuer, in Lagern gespeicherter Tabellen durch Ändern einer vorhandenen Tabelle oder durch Zusammenführen oder Konsolidieren mehrerer Tabellen mithilfe von SQL. Einmal `Data Warehouse View` von einem Aktualisierungszyklus erstellt und verarbeitet wurde, wird sie in Ihrer Data Warehouse als neue Tabelle unter `Data Warehouse Views` wie unten gezeigt:

![](../../assets/Data_Warehouse.png)

Von hier aus funktioniert Ihre neue Ansicht wie jede andere Tabelle, sodass Sie neue berechnete Spalten erstellen oder Metriken und Berichte darüber erstellen können.

`Data Warehouse Views` werden in erster Linie dazu verwendet, mehrere ähnliche, aber unterschiedliche Tabellen zusammenzufassen, sodass alle Berichte auf einer einzigen neuen Tabelle erstellt werden können. Beispiele sind die Konsolidierung von Tabellen aus einer Legacy-Datenbank und einer Live-Datenbank, um historische und aktuelle Daten zu kombinieren, oder die Kombination mehrerer Anzeigenquellen wie Facebook und AdWords zu einer einzigen `Consolidated ad spend` Tabelle.

Wenn Sie mit SQL vertraut sind, verwenden beide dieser Konsolidierungsbeispiele die Variable `UNION` -Funktion, können Sie jedoch beim Erstellen einer neuen Ansicht jede beliebige PostgreSQL-Syntax und -Funktionen verwenden.

## Erstellen und Verwalten von Data Warehouse-Ansichten

Neu `Data Warehouse Views` kann erstellt werden und vorhandene Ansichten können gelöscht werden, indem Sie zu **[!UICONTROL Manage Data]** > **[!UICONTROL Data Warehouse Views]**, wie unten dargestellt:

![](../../assets/Data_Warehouse_Views.png)

Von hier aus können Sie eine Ansicht erstellen, indem Sie die folgenden Beispielanweisungen befolgen:

1. Wenn Sie eine vorhandene Ansicht beobachten, klicken Sie auf **[!UICONTROL New Data Warehouse View]** um ein leeres Abfragefenster zu öffnen. Wenn bereits ein leeres Abfragefenster geöffnet ist, fahren Sie mit dem nächsten Schritt fort.
1. Geben Sie der Ansicht einen Namen, indem Sie die `View Name` -Feld. Der hier angegebene Name bestimmt den Anzeigenamen für die Ansicht in der Data Warehouse. `View names` sind auf Kleinbuchstaben, Zahlen und Unterstriche (_) beschränkt. Alle anderen Zeichen sind verboten.
1. Geben Sie Ihre Abfrage in das Fenster mit dem Titel `Select Query`, unter Verwendung der standardmäßigen PostgreSQL-Syntax.
   >[!NOTE]
   >
   >Ihre Abfrage muss auf bestimmte Spaltennamen verweisen. Die Verwendung der `*`-Zeichen, um alle Spalten auszuwählen, ist nicht zulässig.

1. Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save]** , um Ihre Ansicht zu speichern. Ihre Ansicht verfügt vorübergehend über `Pending` -Status bis zur Verarbeitung durch den nächsten vollständigen Aktualisierungszyklus, an dem sich der Status in `Active`. Nach der Verarbeitung durch eine Aktualisierung kann Ihre Ansicht in Berichten verwendet werden.

Es ist wichtig zu erwähnen, dass nach dem Speichern die zugrunde liegende Abfrage, die zum Generieren einer `Data Warehouse View` kann nicht bearbeitet werden. Wenn Sie die Struktur eines `Data Warehouse View`müssen Sie eine Ansicht erstellen und berechnete Spalten, Metriken oder Berichte manuell von der ursprünglichen Ansicht zur neuen migrieren. Nach Abschluss der Migration können Sie die Originalansicht sicher löschen. weil `Data Warehouse Views` nicht bearbeitbar sind, empfiehlt Adobe, die Ausgabe Ihrer Abfrage mithilfe der `SQL Report Builder` vor dem Speichern Ihrer Abfrage als Data Warehouse View.

## Beispiel: [!DNL Facebook] und [!DNL Google AdWords] data

Sehen Sie sich eines der oben in diesem Artikel erwähnten Beispiele genauer an: konsolidieren [!DNL Facebook] und [!DNL AdWords] Daten in eine neue konsolidierte Anzeigentabelle investieren. In den meisten Fällen umfasst dies die Konsolidierung von zwei Tabellen mit unten stehenden Beispieldatensätzen:

`Ad source: Google AdWords`

`Table name: campaigns67890`

`Sample data:`

| **`_id`** | **`campaign`** | **`adClicks`** | **`date`** | **`impressions`** | **`adCost`** |
|--- |--- |--- |--- |--- |--- |
| 1 | eee | 60 | 2017-05-05 00:00:00 | 2000 | 10.2 |
| 2 | ggg | 40 | 2017-05-23 00:00:00 | 900 | 4.6 |
| 3 | aaa | 22 | 2017-06-12 00:00:00 | 400 | 2.5 |
| 4 | eee | 350 | 2017-06-30 00:00:00 | 14500 | 35 |
| 5 | fff | 280 | 2017-07-10 00:00:00 | 10200 | 28.5 |

`Ad source: Facebook`

`Table name: facebook_ads_insights_12345`

`Sample data:`

| **`_id`** | **`campaign`** | **`adClicks`** | **`date`** | **`impressions`** | **`adCost`** |
|--- |--- |--- |--- |--- |--- |
| 1 | aaa | 25 | 2017-05-01 00:00:00 | 1200 | 5 |
| 2 | ddd | 12 | 2017-05-15 00:00:00 | 800 | 2.5 |
| 3 | aaa | 40 | 2017-05-22 00:00:00 | 2000 | 7 |
| 4 | aaa | 110 | 2017-06-08 00:00:00 | 6000 | 10 |
| 5 | ccc | 5 | 2017-07-06 00:00:00 | 300 | 1.2 |

So erstellen Sie eine Ausgabentabelle für eine einzelne Anzeige, die beide [!DNL Facebook] und [!DNL AdWords] Kampagnen, müssen Sie eine SQL-Abfrage schreiben und die `UNION ALL` -Funktion. A `UNION ALL` -Anweisung wird meist verwendet, um mehrere verschiedene SQL-Abfragen zu kombinieren und gleichzeitig die Ergebnisse jeder Abfrage an eine einzelne Ausgabe anzuhängen.

Es gibt einige Anforderungen an `UNION` -Anweisung, die erwähnt werden muss, wie in PostgreSQL beschrieben [Dokumentation](https://www.postgresql.org/docs/8.3/queries-union.html):

* Alle Abfragen müssen dieselbe Anzahl von Spalten zurückgeben
* Die entsprechenden Spalten müssen identische Datentypen aufweisen

Beim Ausführen einer `UNION` oder `UNION ALL` -Anweisung, spiegeln die Namen der Spalten in der endgültigen Ausgabe die Spaltenbenennung in Ihrer ersten Abfrage wider.

Normalerweise wird die [!DNL Facebook] und [!DNL Google AdWords] Daten in `Data Warehouse View` die Erstellung einer Tabelle mit sieben Spalten erforderlich, deren Abfrage der folgenden ähnelt:

```sql
    SELECT
        "_id" as id,
        'AdWords' as ad_source,
        "date",
        "campaign",
        "adCost" as spend,
        "impressions",
        "adClicks" as clicks
    FROM campaigns67890
    UNION
    SELECT
        "_id" as id,
        'Facebook' as ad_source,
        "date_start" as date,
        "campaign_name" as campaign,
        "spend",
        "impressions",
        "clicks"
    FROM facebook_ads_insights_12345
```

Einige wichtige Punkte zu den oben genannten Themen:

* Aus Gründen der Klarheit werden alle Spalten oberhalb so alidiert, dass die Namen in allen Abfragen übereinstimmen. Dies ist jedoch nicht erforderlich. Die Reihenfolge, in der Spalten in den SELECT-Abfragen aufgerufen werden, bestimmt, wie sie in der Warteschlange angeordnet sind.
* Eine neue Spalte namens `ad_source` wurde erstellt, um die Filterung nach [!DNL AdWords] oder [!DNL Facebook] Daten. Beachten Sie, dass diese Abfrage alle Daten aus beiden Tabellen kombiniert. Wenn Sie keine Spalte wie `ad_source`gibt es keine einfache Möglichkeit, Ausgaben aus einer bestimmten Quelle zu identifizieren.

Speichern der obigen Abfrage als `Data Warehouse View` erstellt eine Tabelle mit beiden [!DNL Facebook] und [!DNL AdWords] Ausgaben, ähnlich wie im Folgenden:

| **`id`** | **`ad_source`** | **`date`** | **`campaign`** | **`spend`** | **`impressions`** | **`clicks`** |
|--- |--- |--- |--- |--- |--- |--- |
| **1** | [!DNL Facebook] | 2017-05-01 00:00:00 | aaa | 5 | 1200 | 25 |
| **1** | [!DNL Google AdWords] | 2017-05-05 00:00:00 | eee | 10.2 | 2000 | 60 |
| **2** | [!DNL Facebook] | 2017-05-15 00:00:00 | ddd | 2.5 | 800 | 12 |
| **2** | [!DNL Google AdWords] | 2017-05-23 00:00:00 | ggg | 4.6 | 900 | 40 |
| **3** | [!DNL Facebook] | 2017-05-22 00:00:00 | aaa | 7 | 2000 | 40 |
| **3** | [!DNL Google AdWords] | 2017-06-12 00:00:00 | aaa | 2.5 | 400 | 22 |
| **4** | [!DNL Facebook] | 2017-06-08 00:00:00 | aaa | 10 | 6000 | 110 |
| **4** | [!DNL Google AdWords] | 2017-06-30 00:00:00 | eee | 35 | 14500 | 350 |
| **5** | [!DNL Facebook] | 2017-07-06 00:00:00 | ccc | 1.2 | 300 | 5 |
| **5** | [!DNL Google AdWords] | 2017-07-10 00:00:00 | fff | 28.5 | 10200 | 280 |

Anstatt für jede Anzeigenquelle einen separaten Satz von Marketing-Metriken zu erstellen, können Sie jetzt nur einen einzigen Metriksatz mit der obigen Tabelle erstellen, um alle Ihre Anzeigen zu erfassen.

**Suchen Sie weitere Hilfe?**

Schreiben von SQL und Erstellen `Data Warehouse Views` ist nicht im technischen Support enthalten. Das Services-Team bietet jedoch Unterstützung bei der Erstellung von Ansichten an. Von der Migration einer alten Data Warehouse mit einer neuen Datenbank bis hin zur Erstellung einer einzigen Analyseansicht kann das Supportteam Ihnen helfen.

Normalerweise wird durch die Erstellung eines `Data Warehouse View` Für die Konsolidierung von 2-3 ähnlich strukturierten Tabellen sind fünf Stunden Dienstzeit erforderlich, was etwa 1250 Dollar Arbeitszeit entspricht. Im Folgenden finden Sie jedoch einige gemeinsame Faktoren, durch die sich die erforderlichen Investitionen erhöhen können:

* Konsolidierung von mehr als drei Tabellen in einer einzigen Ansicht
* Erstellen von mehr als einer Data Warehouse-Ansicht
* Komplexe Fügelogik oder Filterbedingungen
* Konsolidierung von zwei oder mehr Tabellen mit unterschiedlichen Datenstrukturen
