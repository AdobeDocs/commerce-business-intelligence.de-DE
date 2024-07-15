---
title: Erstellen und Verwenden von Data Warehouse-Ansichten
description: Erfahren Sie mehr über eine Methode zum Erstellen neuer in Lagern gespeicherter Tabellen durch Ändern einer vorhandenen Tabelle oder durch Zusammenführen oder Konsolidieren mehrerer Tabellen mithilfe von SQL.
exl-id: 5aa571c9-7f38-462c-8f1b-76a826c9dc55
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 6%

---

# Arbeiten mit Data Warehouse-Ansichten

In diesem Dokument werden Zweck und Verwendung von `Data Warehouse Views` beschrieben, auf die durch Navigieren zu **[!UICONTROL Manage Data]** > **[!UICONTROL Data Warehouse Views]** zugegriffen werden kann. Im Folgenden finden Sie eine Erläuterung dessen, was es tut und wie Ansichten erstellt werden, sowie ein Beispiel dafür, wie Sie mit `Data Warehouse Views` [!DNL Facebook] und [!DNL AdWords] Ausgabedaten konsolidieren können.

## Allgemeiner Zweck

Die Funktion &quot;`Data Warehouse Views`&quot; ist eine Methode zum Erstellen neuer in Lagern gespeicherter Tabellen durch Ändern einer vorhandenen Tabelle oder durch Zusammenführen oder Konsolidieren mehrerer Tabellen mithilfe von SQL. Nachdem ein `Data Warehouse View` durch einen Aktualisierungszyklus erstellt und verarbeitet wurde, wird es in Ihrer Data Warehouse als neue Tabelle unter dem Dropdown-Menü `Data Warehouse Views` ausgefüllt, wie unten dargestellt:

![](../../assets/Data_Warehouse.png)

Von hier aus funktioniert Ihre neue Ansicht wie jede andere Tabelle, sodass Sie neue berechnete Spalten erstellen oder Metriken und Berichte darüber erstellen können.

`Data Warehouse Views` wird hauptsächlich verwendet, um mehrere ähnliche, aber unterschiedliche Tabellen zusammenzufassen, sodass alle Berichte auf einer einzigen neuen Tabelle erstellt werden können. Einige gängige Beispiele sind das Konsolidieren der Tabellen aus einer Legacy-Datenbank und einer Live-Datenbank, um historische und aktuelle Daten zu kombinieren, oder das Kombinieren mehrerer Anzeigenquellen wie Facebook und AdWords zu einer einzigen `Consolidated ad spend` -Tabelle.

Wenn Sie mit SQL vertraut sind, verwenden beide dieser Konsolidierungsbeispiele die Funktion `UNION`, Sie können jedoch beim Erstellen einer neuen Ansicht jede PostgreSQL-Syntax und -Funktionen verwenden.

## Erstellen und Verwalten von Data Warehouse-Ansichten

Neue `Data Warehouse Views` -Ansichten können erstellt und vorhandene gelöscht werden, indem Sie zu **[!UICONTROL Manage Data]** > **[!UICONTROL Data Warehouse Views]** navigieren, wie unten dargestellt:

![](../../assets/Data_Warehouse_Views.png)

Von hier aus können Sie eine Ansicht erstellen, indem Sie die folgenden Beispielanweisungen befolgen:

1. Wenn Sie eine vorhandene Ansicht beobachten, klicken Sie auf **[!UICONTROL New Data Warehouse View]** , um ein leeres Abfragefenster zu öffnen. Wenn bereits ein leeres Abfragefenster geöffnet ist, fahren Sie mit dem nächsten Schritt fort.
1. Geben Sie im Feld `View Name` einen Namen für die Ansicht ein. Der hier angegebene Name bestimmt den Anzeigenamen für die Ansicht auf der Data Warehouse. `View names` ist auf Kleinbuchstaben, Zahlen und Unterstriche (_) beschränkt. Alle anderen Zeichen sind verboten.
1. Geben Sie Ihre Abfrage mit der standardmäßigen PostgreSQL-Syntax in das Fenster mit dem Titel `Select Query` ein.

   >[!NOTE]
   >
   >Ihre Abfrage muss auf bestimmte Spaltennamen verweisen. Die Verwendung des Zeichens `*`zur Auswahl aller Spalten ist nicht zulässig.

1. Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Save]** , um Ihre Ansicht zu speichern. Ihre Ansicht hat vorübergehend den Status &quot;`Pending`&quot;, bis sie durch den nächsten vollständigen Aktualisierungszyklus verarbeitet wird. Ab diesem Zeitpunkt erhält der Status den Status &quot;`Active`&quot;. Nach der Verarbeitung durch eine Aktualisierung kann Ihre Ansicht in Berichten verwendet werden.

Es ist wichtig zu erwähnen, dass die zugrunde liegende Abfrage, die zum Generieren eines `Data Warehouse View` verwendet wird, nach dem Speichern nicht bearbeitet werden kann. Wenn Sie die Struktur eines `Data Warehouse View` anpassen müssen, müssen Sie eine Ansicht erstellen und alle berechneten Spalten, Metriken oder Berichte manuell von der ursprünglichen Ansicht zur neuen migrieren. Nach Abschluss der Migration können Sie die Originalansicht sicher löschen. Da `Data Warehouse Views` nicht bearbeitbar ist, empfiehlt Adobe, die Ausgabe Ihrer Abfrage mit dem `SQL Report Builder` zu testen, bevor Sie Ihre Abfrage als Data Warehouse-Ansicht speichern.

## Beispiel: [!DNL Facebook] - und [!DNL Google AdWords] -Daten

Sehen Sie sich eines der oben in diesem Artikel erwähnten Beispiele an: Konsolidierung von [!DNL Facebook] und [!DNL AdWords] Ausgabedaten in einer neuen konsolidierten Anzeigentabelle. In den meisten Fällen umfasst dies die Konsolidierung von zwei Tabellen mit unten stehenden Beispieldatensätzen:

`Ad source: Google AdWords`

`Table name: campaigns67890`

`Sample data:`

| **`_id`** | **`campaign`** | **`adClicks`** | **`date`** | **`impressions`** | **`adCost`** |
|--- |--- |--- |--- |--- |--- |
| 1 | eee | 60 | 05.05.2017 00:00:00 | 2000 | 10,2 |
| 2 | ggg | 40 | 23.05.2017 00:00:00 | 900 | 4,6 |
| 3 | aaa | 22 | 06.06.2017 00:00:00 | 400 | 2,5 |
| 4 | eee | 350 | 30.06.2017:00:00 | 14500 | 35 |
| 5 | fff | 280 | 00.07.2017:00:00 | 10200 | 28,5 |

`Ad source: Facebook`

`Table name: facebook_ads_insights_12345`

`Sample data:`

| **`_id`** | **`campaign`** | **`adClicks`** | **`date`** | **`impressions`** | **`adCost`** |
|--- |--- |--- |--- |--- |--- |
| 1 | aaa | 25 | 01.05.2017 00:00:00 | 1200 | 5 |
| 2 | ddd | 12 | 05.05.2017 00:00:00 | 800 | 2,5 |
| 3 | aaa | 40 | 22.05.2017:00:00 | 2000 | 7 |
| 4 | aaa | 110 | 08.06.2017 00:00:00 | 6000 | 10 |
| 5 | ccc | 5 | 06.07.2017 00:00:00 | 300 | 1,2 |

Um eine einzelne Tabelle mit Werbeausgaben zu erstellen, die sowohl [!DNL Facebook] als auch [!DNL Google AdWords] -Kampagnen enthält, müssen Sie eine SQL-Abfrage schreiben und die Funktion `UNION ALL` verwenden. Eine `UNION ALL` -Anweisung wird meist verwendet, um mehrere verschiedene SQL-Abfragen zu kombinieren und gleichzeitig die Ergebnisse jeder Abfrage an eine einzelne Ausgabe anzuhängen.

Es gibt einige Anforderungen an eine `UNION` -Anweisung, die erwähnt werden müssen, wie in der PostgreSQL- [Dokumentation](https://www.postgresql.org/docs/8.3/queries-union.html) beschrieben:

* Alle Abfragen müssen dieselbe Anzahl von Spalten zurückgeben
* Die entsprechenden Spalten müssen identische Datentypen aufweisen

Beim Ausführen einer `UNION` - oder `UNION ALL` -Anweisung spiegeln die Namen der Spalten in der endgültigen Ausgabe die Spaltenbenennung in Ihrer ersten Abfrage wider.

Normalerweise erfordert die Konsolidierung Ihrer [!DNL Facebook]- und [!DNL Google AdWords]-Ausgabedaten in einem `Data Warehouse View` die Erstellung einer Tabelle mit sieben Spalten, wobei eine Abfrage ähnlich der folgenden erstellt wird:

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
* Eine neue Spalte mit dem Namen `ad_source` wird erstellt, um die Filterung nach [!DNL AdWords] - oder [!DNL Facebook] -Daten zu vereinfachen. Beachten Sie, dass diese Abfrage alle Daten aus beiden Tabellen kombiniert. Wenn Sie keine Spalte wie `ad_source` erstellen, ist es nicht einfach, Ausgaben aus einer bestimmten Quelle zu identifizieren.

Durch das Speichern der obigen Abfrage als `Data Warehouse View` wird eine Tabelle mit den Ausgaben [!DNL Facebook] und [!DNL AdWords] erstellt, die der folgenden ähnelt:

| **`id`** | **`ad_source`** | **`date`** | **`campaign`** | **`spend`** | **`impressions`** | **`clicks`** |
|--- |--- |--- |--- |--- |--- |--- |
| **1** | [!DNL Facebook] | 01.05.2017 00:00:00 | aaa | 5 | 1200 | 25 |
| **1** | [!DNL Google AdWords] | 05.05.2017 00:00:00 | eee | 10,2 | 2000 | 60 |
| **2** | [!DNL Facebook] | 05.05.2017 00:00:00 | ddd | 2,5 | 800 | 12 |
| **2** | [!DNL Google AdWords] | 23.05.2017 00:00:00 | ggg | 4,6 | 900 | 40 |
| **3** | [!DNL Facebook] | 22.05.2017:00:00 | aaa | 7 | 2000 | 40 |
| **3** | [!DNL Google AdWords] | 06.06.2017 00:00:00 | aaa | 2,5 | 400 | 22 |
| **4** | [!DNL Facebook] | 08.06.2017 00:00:00 | aaa | 10 | 6000 | 110 |
| **4** | [!DNL Google AdWords] | 30.06.2017:00:00 | eee | 35 | 14500 | 350 |
| **5** | [!DNL Facebook] | 06.07.2017 00:00:00 | ccc | 1,2 | 300 | 5 |
| **5** | [!DNL Google AdWords] | 00.07.2017:00:00 | fff | 28,5 | 10200 | 280 |

Anstatt für jede Anzeigenquelle einen separaten Satz von Marketing-Metriken zu erstellen, können Sie mit der obigen Tabelle nur einen einzigen Metriksatz erstellen, um alle Ihre Anzeigen zu erfassen.

**Suchen Sie weitere Hilfe?**

Das Schreiben von SQL und Erstellen von `Data Warehouse Views` ist nicht im technischen Support enthalten. Das [Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) bietet jedoch Unterstützung bei der Erstellung von Ansichten. Von der Migration einer alten Datenbank mit einer neuen Datenbank bis hin zur Erstellung einer einzigen Data Warehouse-Ansicht für eine bestimmte Analyse kann das Supportteam behilflich sein.

Normalerweise erfordert die Erstellung eines neuen `Data Warehouse View` zur Konsolidierung von zwei bis drei ähnlich strukturierten Tabellen fünf Stunden Dienstzeit, was etwa 1.250 Dollar Arbeitszeit entspricht. Im Folgenden finden Sie jedoch einige gemeinsame Faktoren, durch die sich die erforderlichen Investitionen erhöhen können:

* Konsolidierung von mehr als drei Tabellen in einer einzigen Ansicht
* Erstellung mehrerer Data Warehouse-Ansichten
* Komplexe Fügelogik oder Filterbedingungen
* Konsolidierung von zwei oder mehr Tabellen mit unterschiedlichen Datenstrukturen
