---
title: Build[!DNL Google ECommerce] Dimensionen
description: Erfahren Sie, wie Sie Dimensionen erstellen, die Ihre E-Commerce-Daten mit Ihren Bestellungen und Kundendaten verknüpfen.
exl-id: f8a557ae-01d7-4886-8a1c-c0f245c7bc49
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Build [!DNL Google ECommerce] Dimensionen

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Jetzt, da Sie fertig sind [Verbindung herstellen[!DNL Google ECommerce] account](../../data-analyst/importing-data/integrations/google-ecommerce.md), was Sie mit diesen Daten in tun können [!DNL Commerce Intelligence]? Dieses Thema führt Sie durch die Erstellung von Dimensionen, die Ihre E-Commerce-Daten mit Ihren Bestellungen und Kundendaten verknüpfen.

Mithilfe der erfassten Dimensionen können Sie Analysen erstellen, die Folgendes ermöglichen: [beantworten wichtige Fragen zu Ihren Marketing-Kanälen und -Kampagnen](../../data-analyst/analysis/most-value-source-channel.md). Wie viel Prozent des Umsatzes wird aus den einzelnen Quellen erwirtschaftet? Wie wird der Lebenszeitwert von [!DNL Facebook] erworbene Kunden im Vergleich zu solchen von [!DNL Google]?

## Voraussetzungen und Übersicht

Um die Dimensionen in diesem Thema zu erstellen, benötigen Sie eine [!DNL Google ECommerce] -Tabelle, `orders` und eine `customers` Tabelle. Diese Tabellen müssen [mit Ihrer Data Warehouse synchronisiert](../../data-analyst/data-warehouse-mgr/tour-dwm.md) bevor Dimensionen erstellt werden können. Synchronisierte Tabellen werden im `Synced Tables` Abschnitt `Data Warehouse Manager`.

Hier finden Sie einen kurzen Überblick über die Synchronisierung von Tabellen und Spalten, wenn Sie eine Auffrischung benötigen:

![](../../assets/Syncing_New_Columns.gif)

Nach dem Erstellen eines Joins aus dem `orders` -Tabelle [!DNL Google eCommerce] erstellen Sie die ersten drei Dimensionen in der unten stehenden Liste. Anschließend verwenden Sie diese Dimensionen, um drei Benutzer-/Kundendimensionen in der `customers` Tabelle. Schließen Sie diese Spalten mit der `orders` Tabelle.

Im Folgenden werden die Dimensionen behandelt:

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

Um Dimensionen zu erstellen, öffnen Sie die [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md) durch Klicken auf **[!UICONTROL Data]** > **[!UICONTROL Data Warehouse]**.

### Bestelltabelle, rund 1

In diesem Beispiel wird die **Reihenfolge [!DNL Google Analytics] Quelle** Dimension.

1. Klicken Sie in der Tabellenliste im Data Warehouse auf die Tabelle (hier: `orders`), die Ihre Bestellinformationen enthält.
1. Klicken **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Auswählen `Joined Column` aus dem [Dropdown-Liste für Definitionen](../data-warehouse-mgr/calc-column-types.md). Dieses Beispiel funktioniert mit einer [Eins-zu-Eins-Beziehung](../data-warehouse-mgr/table-relationships.md), die mit dem `eCommerce.transactionID` auf genau eine Zeile der `orders` Tabelle.
1. Als Nächstes müssen Sie den Pfad definieren oder festlegen, wie die verwendete Tabelle und Spalte verbunden werden. Klicken Sie auf `Select a table and column` Dropdown.
1. Der Pfad, den Sie benötigen, ist nicht verfügbar. Daher müssen Sie einen neuen erstellen. Klicken **[!UICONTROL Create new Path]**.
1. Legen Sie im angezeigten Fenster die `Many` Seitenanfang `orders.order\_id`oder die Spalte in `orders` -Tabelle, die die Bestell-ID enthält.
1. Im `One` Seite, suchen Sie die `Google ECommerce` und setzen Sie die Spalte auf `transactionID`.

   ![](../../assets/google-ecommerce-table.png)

1. Klicks **[!UICONTROL Save]** , um den Pfad zu erstellen.
1. Nachdem der Pfad hinzugefügt wurde, klicken Sie auf die **[!UICONTROL Select table and column]** erneut hinunter.
1. Suchen Sie die `ECommerce` und klicken Sie dann auf die `Source` Spalte. Dadurch werden die Bestellungen mit den Quellinformationen verknüpft.
1. Sobald Sie sich wieder im Tabellenschema befinden, klicken Sie auf **[!UICONTROL Save]** erneut, um die Dimension zu erstellen.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../assets/help_center.gif)

Versuchen Sie als Nächstes, **Reihenfolge [!DNL Google Analytics] medium** und `campaign`. Da sich diese Dimensionen nicht sehr ändern, versuchen Sie es. Aber wenn man festsitzt, kann man es auschecken [Ende dieses Artikels](#stuck) um zu sehen, was anders ist.

### Kundentabelle {#customers}

In diesem Beispiel wird die **Die erste Bestellung des Kunden [!DNL Google Analytics] source** Dimension.

1. Klicken Sie in der Tabellenliste im Data Warehouse auf die Tabelle (hier: `customers`), die Ihre Kundeninformationen enthält.
1. Klicken **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Wählen Sie für dieses Beispiel die `is MAX` Definition aus [Dropdown-Liste für Definitionen](../../data-analyst/data-warehouse-mgr/calc-column-types.md). Die `is MIN` -Definition auch dann funktioniert, wenn sie auf eine Textspalte mit nur einem möglichen Wert angewendet wird. Wichtig ist, dass die richtigen Filter eingerichtet werden, was Sie später tun.
1. Klicken Sie auf **[!UICONTROL Select a table and column]** Dropdown-Liste und wählen Sie `orders` -Tabelle, dann die `Order's [!DNL Google Analytics] source` Spalte.
1. Klicken **[!UICONTROL Save]**.
1. Sobald Sie sich wieder im Tabellenschema befinden, klicken Sie auf die Schaltfläche `Options` Dropdown, dann `Filters`.
1. Klicks **[!UICONTROL Add Filter Set]** und wählen Sie dann die `Orders we count` festgelegt ist. Sie möchten nur Bestellungen einschließen, die in den Bestellungen enthalten sind, für die Sie den Filtersatz zählen. Daher ist es wichtig, dass dieser Filtersatz ausgewählt wird.
1. Klicken **[!UICONTROL Add Filter]**. Sie möchten die erste Bestellung des Kunden finden [!DNL Google Analytics] -Quelle, sodass Sie einen Filter hinzufügen müssen:

   _orders.Customer&#39;s order number = 1

   _
1. Klicks **[!UICONTROL Save]** , um die Dimension zu erstellen.

Versuchen Sie als Nächstes, **Die erste Bestellung des Kunden [!DNL Google Analytics] medium** und `campaign`. Da sich diese Dimensionen nicht sehr ändern, versuchen Sie es. Aber wenn man festsitzt, kann man es auschecken [Ende dieses Artikels](#stuck) um zu sehen, was anders ist.

### Bonus: Bestellungstisch, rund 2

Sie können hier stoppen, wenn Sie möchten, aber dieser Abschnitt ermöglicht eine weitere Analyse, indem Sie die **Die erste Bestellung des Kunden [!DNL Google Analytics] Dimensionen** die Sie in der [letzter Abschnitt](#customers) in `orders` Tabelle. Wenn Sie die Dimensionen in diesem Abschnitt erstellen, können Sie alle Metriken analysieren, die auf Ihrer `orders` table - `Revenue`, `Number of orders`, `Distinct buyers`usw. - Verwendung der [!DNL Google Analytics] Attribute der ersten Bestellung eines Kunden.

Dieses Beispiel fügt sich in die `Customer's first order's [!DNL Google Analytics] source` Dimension in die `orders` Tabelle.

1. Klicken Sie in der Tabellenliste im Data Warehouse auf die Tabelle (hier: `orders`), die Ihre Bestellinformationen enthält.
1. Klicken **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Auswählen `Joined Column` aus dem Dropdown-Menü Definition . Dadurch werden die Kundendimensionen, die Sie im vorherigen Abschnitt erstellt haben, mit dem `orders` Tabelle.
1. Klicken Sie auf **[!UICONTROL Select a table and column]** Dropdown-Liste und wählen Sie dann die `customers` und `Customer's first order's [!DNL Google Analytics] source` Spalte.
1. Wenn ein Pfad nicht automatisch aufgefüllt wird, wählen Sie den Pfad aus, der die Kunden- und Auftragstabellen am besten verbindet.
1. Klicks **[!UICONTROL Save]** , um die Dimension zu erstellen.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../assets/help_center2.gif)

Beenden Sie den Vorgang, indem Sie der `Customer's first order's` mittel und `campaign` -Dimensionen `orders` Tabelle. Schließen Sie die Dimensionen an, und falls Probleme auftreten, überprüfen Sie sie. [Ende des Artikels](#stuck) wenn Sie Hilfe benötigen.

### Aufwischen

Sie haben die Erstellung der Dimensionen abgeschlossen. Dies bedeutet, dass Sie jetzt leistungsstarke Analysen erstellen können, die die Leistung Ihrer verschiedenen Kanäle und Kampagnen verfolgen. Beachten Sie, dass die Variable **neue Spalten stehen erst nach Abschluss der nächsten Aktualisierung zur Verfügung**.

Einige der beliebtesten Dimensionen werden in diesem Thema behandelt, aber der Himmel ist das Limit - versuchen Sie, Ihre eigene zu erstellen oder Sie können uns gerne pingen, wenn Sie Hilfe beim Erkunden anderer Optionen wünschen. 

### Weitere Hinweise

**`Orders`Tabelle 1**: Beim Erstellen der `Order's [!DNL Google Analytics]` mittel und `campaign` -Dimensionen, ist der Unterschied die in Schritt 12 ausgewählten Spalten. In diesem Beispiel war die Spalte `Source`.

**`Customers`table**: Beim Erstellen der `Customer's first order's [!DNL Google Analytics]` mittel und `campaign` -Dimensionen, ist der Unterschied die in Schritt 5 ausgewählten Spalten. In diesem Beispiel war die Spalte `Order's [!DNL Google Analytics]` -Quelle.

**`Orders`Tabelle 2**: Wenn Sie der `Customer's first order's [!DNL Google Analytics]` mittel und `campaign` -Spalten `orders` -Tabelle die in Schritt 5 ausgewählten Spalten. In diesem Beispiel war die Spalte `Customer's first order's [!DNL Google Analytics]` -Quelle.
