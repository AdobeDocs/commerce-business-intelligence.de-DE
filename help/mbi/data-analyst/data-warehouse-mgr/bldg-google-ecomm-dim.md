---
title: Build[!DNL Google ECommerce]Dimensionen
description: Erfahren Sie, wie Sie Dimensionen erstellen, die Ihre E-Commerce-Daten mit Ihren Bestellungen und Kundendaten verknüpfen.
exl-id: f8a557ae-01d7-4886-8a1c-c0f245c7bc49
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---

# Build [!DNL Google ECommerce] Dimensionen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Jetzt, da Sie fertig sind [Verbinden[!DNL Google ECommerce]account](../../data-analyst/importing-data/integrations/google-ecommerce.md), was Sie mit diesen Daten in tun können [!DNL MBI]? In diesem Artikel führen wir Sie durch die Erstellung von Dimensionen, die Ihre E-Commerce-Daten mit Ihren Bestellungen und Kundendaten verknüpfen.

Die Dimensionen, die wir abdecken, bieten Ihnen die Möglichkeit, Analysen zu erstellen, die [beantworten wichtige Fragen zu Ihren Marketing-Kanälen und -Kampagnen](../../data-analyst/analysis/most-value-source-channel.md). Wie viel Prozent des Umsatzes wird aus den einzelnen Quellen erwirtschaftet? Wie unterscheidet sich der Lebenszeitwert von mit Facebook erworbenen Kunden von dem von [!DNL Google]?

## Voraussetzungen und Übersicht

Um die Dimensionen in diesem Artikel zu erstellen, benötigen Sie eine [!DNL Google ECommerce] Tabelle, `orders` und eine `customers` Tabelle. Diese Tabellen müssen [mit Ihrem Data Warehouse synchronisiert werden](../../data-analyst/data-warehouse-mgr/tour-dwm.md) bevor Dimensionen erstellt werden können. Synchronisierte Tabellen werden im `Synced Tables` Abschnitt `Data Warehouse Manager`.

Hier finden Sie einen kurzen Überblick über die Synchronisierung von Tabellen und Spalten, falls Sie eine Auffrischung benötigen:

![](../../assets/Syncing_New_Columns.gif)

Nach dem Erstellen eines Joins aus dem `orders` -Tabelle [!DNL Google eCommerce] erstellen wir die ersten drei Dimensionen in der folgenden Liste. Als Nächstes verwenden wir diese Dimensionen, um drei Benutzer-/Kundendimensionen in der `customers` Tabelle. Abschließend fügen wir diese Spalten der `orders` Tabelle.

Die folgenden Dimensionen werden abgedeckt:

* **Bestelltabelle**

* Reihenfolge [!DNL Google Analytics] source
* Reihenfolge [!DNL Google Analytics] medium
* Reihenfolge [!DNL Google Analytics]Eine Kampagne
* Die erste Bestellung des Kunden [!DNL Google Analytics] source
* Die erste Bestellung des Kunden [!DNL Google Analytics] medium
* Die erste Bestellung des Kunden [!DNL Google Analytics] Kampagne

* **Kundentabelle**

* Die erste Bestellung des Kunden [!DNL Google Analytics] source
* Die erste Bestellung des Kunden [!DNL Google Analytics] medium
* Die erste Bestellung des Kunden [!DNL Google Analytics] Kampagne

## Dimensionen erstellen

Um Dimensionen zu erstellen, öffnen Sie die [Data Warehouse Manager](../data-warehouse-mgr/tour-dwm.md) durch Klicken auf **[!UICONTROL Data]** > **[!UICONTROL Data Warehouse]**.

### Bestelltabelle, rund 1

In diesem Beispiel erstellen wir die **Reihenfolge [!DNL Google Analytics] Quelle** Dimension.

1. Klicken Sie in der Tabellenliste in der Data Warehouse auf die Tabelle (in unserem Beispiel `orders`), die Ihre Bestellinformationen enthält.
1. Klicken **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Auswählen `Joined Column` von [Dropdown-Liste für Definitionen](../data-warehouse-mgr/calc-column-types.md). In diesem Beispiel arbeiten wir mit einem [Eins-zu-Eins-Beziehung](../data-warehouse-mgr/table-relationships.md), die mit dem `eCommerce.transactionID` auf genau eine Zeile der `orders` Tabelle.
1. Als Nächstes müssen wir den Pfad definieren oder festlegen, wie die verwendete Tabelle und Spalte verbunden werden. Klicken Sie auf `Select a table and column` Dropdown-Liste.
1. Der Pfad, den wir brauchen, ist nicht verfügbar, daher müssen wir einen neuen erstellen. Klicken **[!UICONTROL Create new Path]**.
1. Legen Sie im angezeigten Fenster die `Many` side to `orders.order\_id`oder die Spalte in `orders` -Tabelle, die die Bestell-ID enthält.
1. Im `One` Seite, suchen Sie die `Google ECommerce` Tabelle und setzen Sie dann die Spalte auf `transactionID`.

   ![](../../assets/google-ecommerce-table.png)

1. Klicken **[!UICONTROL Save]** , um den Pfad zu erstellen.
1. Nachdem der Pfad hinzugefügt wurde, klicken Sie auf die **[!UICONTROL Select table and column]** erneut hinunter.
1. Suchen Sie die `ECommerce` und klicken Sie dann auf die `Source` Spalte. Dadurch werden die Bestellungen mit den Quellinformationen verknüpft.
1. Sobald Sie sich wieder im Tabellenschema befinden, klicken Sie auf **[!UICONTROL Save]** erneut, um die Dimension zu erstellen.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../assets/help_center.gif)

Versuchen Sie als Nächstes, **Reihenfolge [!DNL Google Analytics] medium** und `campaign`. Für diese Dimensionen wird sich nicht viel ändern. Versuchen Sie es also. Aber wenn man festsitzt, kann man es auschecken [Ende dieses Artikels](#stuck) um zu sehen, was anders ist.

### Kundentabelle {#customers}

In diesem Beispiel erstellen wir die **Die erste Bestellung des Kunden [!DNL Google Analytics] source** Dimension.

1. Klicken Sie in der Tabellenliste in der Data Warehouse auf die Tabelle (in unserem Beispiel `customers`), die Ihre Kundeninformationen enthält.
1. Klicken **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. In diesem Beispiel wählen wir die `is MAX` Definition aus [Dropdown-Liste für Definitionen](../../data-analyst/data-warehouse-mgr/calc-column-types.md). Die `is MIN` -Definition auch dann funktioniert, wenn sie auf eine Textspalte mit nur einem möglichen Wert angewendet wird. Wichtig ist, dass geeignete Filter festgelegt werden, was wir später tun.
1. Klicken Sie auf **[!UICONTROL Select a table and column]** Dropdown-Liste und wählen Sie die `orders` -Tabelle, dann die `Order's [!DNL Google Analytics] source` Spalte.
1. Klicken **[!UICONTROL Save]**.
1. Sobald Sie sich wieder im Tabellenschema befinden, klicken Sie auf die Schaltfläche `Options` Dropdown, dann `Filters`.
1. Klicken **[!UICONTROL Add Filter Set]** und wählen Sie dann die `Orders we count` gesetzt. Wir möchten nur, dass Bestellungen in den Bestellungen enthalten sind, für die wir einen Filtersatz zählen. Daher ist es wichtig, dass dieser Filtersatz ausgewählt wird.
1. Klicken **[!UICONTROL Add Filter]**. Wir möchten die erste Bestellung des Kunden finden. [!DNL Google Analytics] -Quelle, sodass wir einen Filter hinzufügen müssen:

   _orders.Customer&#39;s order number = 1

   _
1. Klicken **[!UICONTROL Save]** , um die Dimension zu erstellen.

Versuchen Sie als Nächstes, **Die erste Bestellung des Kunden [!DNL Google Analytics] medium** und `campaign`. Für diese Dimensionen wird sich nicht viel ändern. Versuchen Sie es also. Aber wenn man festsitzt, kann man es auschecken [Ende dieses Artikels](#stuck) um zu sehen, was anders ist.

### Bonus: Bestelltisch, rund 2

Sie können hier stoppen, wenn Sie möchten, aber dieser Abschnitt ermöglicht eine weitere Analyse, indem Sie die **Die erste Bestellung des Kunden [!DNL Google Analytics] Dimensionen** Wir haben in der [letzter Abschnitt](#customers) in `orders` Tabelle. Wenn Sie die Dimensionen in diesem Abschnitt erstellen, können Sie alle Metriken analysieren, die auf Ihrer `orders` table - `Revenue`, `Number of orders`, `Distinct buyers`usw. - Verwendung der [!DNL Google Analytics] Attribute der ersten Bestellung eines Kunden.

In diesem Beispiel schließen wir uns der `Customer's first order's [!DNL Google Analytics] source` Dimension in `orders` Tabelle.

1. Klicken Sie in der Tabellenliste in der Data Warehouse auf die Tabelle (in unserem Beispiel `orders`), die Ihre Bestellinformationen enthält.
1. Klicken **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Auswählen `Joined Column` aus dem Dropdown-Menü Definition . Dies fügt sich in die Kundendimensionen ein, die Sie im vorherigen Abschnitt erstellt haben. `orders` Tabelle.
1. Klicken Sie auf **[!UICONTROL Select a table and column]** Dropdown-Liste und wählen Sie dann die `customers` und `Customer's first order's [!DNL Google Analytics] source` Spalte.
1. Wenn ein Pfad nicht automatisch aufgefüllt wird, wählen Sie den Pfad aus, der die Kunden- und Auftragstabellen am besten verbindet.
1. Klicken **[!UICONTROL Save]** , um die Dimension zu erstellen.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../assets/help_center2.gif)

Beenden Sie den Vorgang durch Teilnahme am `Customer's first order's` mittel und `campaign` -Dimensionen `orders` Tabelle. Probieren Sie es aus und schauen Sie sich, wie wir bereits erwähnt haben, an [Ende des Artikels](#stuck) wenn Sie Hilfe benötigen.

### Aufbrechen

Wir haben die Erstellung der Dimensionen abgeschlossen. Das bedeutet, dass wir jetzt leistungsstarke Analysen erstellen können, die die Leistung unserer verschiedenen Kanäle und Kampagnen verfolgen. Wir wissen, dass du begierig darauf bist zu beginnen, aber erinnere dich an die **neue Spalten stehen erst nach Abschluss der nächsten Aktualisierung zur Verfügung**.

Wir haben einige der beliebtesten Dimensionen in diesem Artikel behandelt, aber der Himmel ist das Limit - versuchen Sie, Ihre eigene zu erstellen oder Sie können uns gerne pingen, wenn Sie Hilfe beim Erkunden anderer Optionen wollen. 

### Ich bin steckengeblieben. Was ist anders? {#stuck}

**`Orders`Tabelle 1:** Beim Erstellen der `Order's [!DNL Google Analytics]` mittel und `campaign` -Dimensionen, wird die Differenz aus den in Schritt 12 ausgewählten Spalten bestehen. In unserem Beispiel war die Spalte `Source`.

**`Customers`table:** Beim Erstellen der `Customer's first order's [!DNL Google Analytics]` mittel und `campaign` -Dimensionen, wird die Differenz aus den in Schritt 5 ausgewählten Spalten bestehen. In unserem Beispiel war die Spalte `Order's [!DNL Google Analytics]` -Quelle.

**`Orders`Tabelle 2:** Wenn Sie `Customer's first order's [!DNL Google Analytics]` mittel und `campaign` -Spalten `orders` -Tabelle die in Schritt 5 ausgewählten Spalten. In unserem Beispiel war die Spalte `Customer's first order's [!DNL Google Analytics]` -Quelle.
