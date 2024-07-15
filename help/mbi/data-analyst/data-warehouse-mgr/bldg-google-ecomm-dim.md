---
title: Build[!DNL Google ECommerce]-Dimensionen
description: Erfahren Sie, wie Sie Dimensionen erstellen, die Ihre E-Commerce-Daten mit Ihren Bestellungen und Kundendaten verknüpfen.
exl-id: f8a557ae-01d7-4886-8a1c-c0f245c7bc49
role: Admin, Data Architect, Data Engineer, User
feature: Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Build-Dimensionen [!DNL Google ECommerce]

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Was können Sie mit diesen Daten in [!DNL Commerce Intelligence] tun, nachdem Sie [Ihr[!DNL Google ECommerce] Konto](../../data-analyst/importing-data/integrations/google-ecommerce.md) verbunden haben? Dieses Thema führt Sie durch die Erstellung von Dimensionen, die Ihre E-Commerce-Daten mit Ihren Bestellungen und Kundendaten verknüpfen.

Mithilfe der erfassten Dimensionen können Sie Analysen erstellen, die [wichtige Fragen zu Ihren Marketing-Kanälen und Kampagnen beantworten](../../data-analyst/analysis/most-value-source-channel.md). Wie viel Prozent des Umsatzes wird aus den einzelnen Quellen erwirtschaftet? Wie unterscheidet sich der Lebenszeitwert von [!DNL Facebook] erworbenen Kunden von dem von [!DNL Google]?

## Voraussetzungen und Übersicht

Um die Dimensionen in diesem Thema zu erstellen, benötigen Sie eine [!DNL Google ECommerce] Tabelle, eine `orders` Tabelle und eine `customers` Tabelle. Diese Tabellen müssen mit Ihrem Data Warehouse ](../../data-analyst/data-warehouse-mgr/tour-dwm.md) synchronisiert werden, bevor Dimensionen erstellt werden können.[ Synchronisierte Tabellen werden im Abschnitt `Synced Tables` des Abschnitts `Data Warehouse Manager` angezeigt.

Hier finden Sie einen kurzen Überblick über die Synchronisierung von Tabellen und Spalten, wenn Sie eine Auffrischung benötigen:

![](../../assets/Syncing_New_Columns.gif)

Nachdem Sie einen Join von der Tabelle `orders` zur Tabelle [!DNL Google eCommerce] erstellt haben, erstellen Sie die ersten drei Dimensionen in der unten stehenden Liste. Als Nächstes verwenden Sie diese Dimensionen, um drei Benutzer-/Kundendimensionen in der Tabelle `customers` zu erstellen. Abschließend fügen Sie diese Spalten zur Tabelle `orders` hinzu.

Im Folgenden werden die Dimensionen behandelt:

* **Auftragstabelle**

* Quelle der Bestellung [!DNL Google Analytics]
* [!DNL Google Analytics] Medium der Bestellung
* [!DNL Google Analytics]Eine Kampagne bestellen
* Quelle [!DNL Google Analytics] der ersten Bestellung des Kunden
* Medium der ersten Bestellung des Kunden[!DNL Google Analytics]
* Die [!DNL Google Analytics]-Kampagne der ersten Bestellung des Kunden

* **Tabelle &quot;Kunden&quot;**

* Quelle [!DNL Google Analytics] der ersten Bestellung des Kunden
* Medium der ersten Bestellung des Kunden[!DNL Google Analytics]
* Die [!DNL Google Analytics]-Kampagne der ersten Bestellung des Kunden

## Dimensionen erstellen

Um Dimensionen zu erstellen, öffnen Sie den [Data Warehouse-Manager](../data-warehouse-mgr/tour-dwm.md) durch Klicken auf **[!UICONTROL Data]** > **[!UICONTROL Data Warehouse]**.

### Bestelltabelle, rund 1

In diesem Beispiel wird die Dimension [!DNL Google Analytics] Source **der Bestellung erstellt.**

1. Klicken Sie in der Tabellenliste im Data Warehouse auf die Tabelle (in diesem Fall `orders`), die Ihre Bestellinformationen enthält.
1. Klicken Sie auf **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Wählen Sie `Joined Column` aus dem Dropdown-Menü [Definition](../data-warehouse-mgr/calc-column-types.md). Dieses Beispiel funktioniert mit einer [Eins-zu-Eins-Beziehung](../data-warehouse-mgr/table-relationships.md), die der Spalte `eCommerce.transactionID` genau einer Zeile der Tabelle `orders` entspricht.
1. Als Nächstes müssen Sie den Pfad definieren oder festlegen, wie die verwendete Tabelle und Spalte verbunden werden. Klicken Sie auf das Dropdown-Menü `Select a table and column` .
1. Der Pfad, den Sie benötigen, ist nicht verfügbar. Daher müssen Sie einen neuen erstellen. Klicken Sie auf **[!UICONTROL Create new Path]**.
1. Setzen Sie im angezeigten Fenster die Seite `Many` auf `orders.order\_id` oder die Spalte in der Tabelle `orders`, die die Bestell-ID enthält.
1. Suchen Sie auf der Seite `One` die Tabelle `Google ECommerce` und setzen Sie dann die Spalte auf `transactionID`.

   ![](../../assets/google-ecommerce-table.png)

1. Klicken Sie auf **[!UICONTROL Save]** , um den Pfad zu erstellen.
1. Nachdem der Pfad hinzugefügt wurde, klicken Sie erneut auf das Dropdown-Menü **[!UICONTROL Select table and column]** .
1. Suchen Sie die Tabelle `ECommerce` und klicken Sie dann auf die Spalte `Source` . Dadurch werden die Bestellungen mit den Quellinformationen verknüpft.
1. Wenn Sie sich wieder im Tabellenschema befinden, klicken Sie erneut auf **[!UICONTROL Save]** , um die Dimension zu erstellen.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../assets/help_center.gif)

Versuchen Sie als Nächstes, **das [!DNL Google Analytics] Medium** und `campaign` der Bestellung zu erstellen. Da sich diese Dimensionen nicht sehr ändern, versuchen Sie es. Wenn Sie jedoch feststecken, können Sie [das Ende dieses Artikels](#stuck) auschecken, um zu sehen, was anders ist.

### Kundentabelle {#customers}

In diesem Beispiel wird die Dimension [!DNL Google Analytics] Quelle **der ersten Bestellung des Kunden erstellt.**

1. Klicken Sie in der Tabellenliste im Data Warehouse auf die Tabelle (in diesem Fall `customers`), die Ihre Kundeninformationen enthält.
1. Klicken Sie auf **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Wählen Sie für dieses Beispiel die Definition `is MAX` aus dem Dropdown-Menü [Definition](../../data-analyst/data-warehouse-mgr/calc-column-types.md) aus. Die Definition `is MIN` kann auch funktionieren, wenn sie auf eine Textspalte mit nur einem möglichen Wert angewendet wird. Wichtig ist, dass die richtigen Filter eingerichtet werden, was Sie später tun.
1. Klicken Sie auf das Dropdown-Menü **[!UICONTROL Select a table and column]** und wählen Sie die Tabelle `orders` und dann die Spalte `Order's [!DNL Google Analytics] source` aus.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. Sobald Sie sich wieder im Tabellenschema befinden, klicken Sie auf das Dropdown-Menü `Options` und dann auf `Filters`.
1. Klicken Sie auf **[!UICONTROL Add Filter Set]** und wählen Sie dann den Satz `Orders we count` aus. Sie möchten nur Bestellungen einschließen, die in den Bestellungen enthalten sind, für die Sie den Filtersatz zählen. Daher ist es wichtig, dass dieser Filtersatz ausgewählt wird.
1. Klicken Sie auf **[!UICONTROL Add Filter]**. Sie möchten die Quelle [!DNL Google Analytics] der ersten Bestellung des Kunden finden, sodass Sie einen Filter hinzufügen müssen:

   _orders.Customer&#39;s order number = 1

   _
1. Klicken Sie auf **[!UICONTROL Save]** , um die Dimension zu erstellen.

Versuchen Sie als Nächstes, die [!DNL Google Analytics] Medium **und `campaign` der ersten Bestellung des Kunden zu erstellen.** Da sich diese Dimensionen nicht sehr ändern, versuchen Sie es. Wenn Sie jedoch feststecken, können Sie [das Ende dieses Artikels](#stuck) auschecken, um zu sehen, was anders ist.

### Bonus: Bestellungstisch, rund 2

Sie können hier stoppen, wenn Sie möchten. Dieser Abschnitt ermöglicht jedoch eine weitere Analyse, indem Sie die [!DNL Google Analytics] Dimensionen **der ersten Bestellung des Kunden** in die Tabelle `orders` einschließen. [](#customers) Wenn Sie die Dimensionen in diesem Abschnitt erstellen, können Sie alle Metriken analysieren, die auf Ihrer `orders` Tabelle - `Revenue`, `Number of orders`, `Distinct buyers` usw. basieren, und zwar mithilfe der Attribute [!DNL Google Analytics] der ersten Bestellung eines Kunden.

Dieses Beispiel fügt die Dimension `Customer's first order's [!DNL Google Analytics] source` in die Tabelle `orders` ein.

1. Klicken Sie in der Tabellenliste im Data Warehouse auf die Tabelle (in diesem Fall `orders`), die Ihre Bestellinformationen enthält.
1. Klicken Sie auf **[!UICONTROL Create a Column]**.
1. Benennen Sie die Spalte.
1. Wählen Sie `Joined Column` aus dem Dropdown-Menü Definition . Dadurch werden die Kundendimensionen, die Sie im vorherigen Abschnitt erstellt haben, mit der Tabelle `orders` verknüpft.
1. Klicken Sie auf das Dropdown-Menü **[!UICONTROL Select a table and column]** und wählen Sie dann die Tabelle `customers` und die Spalte `Customer's first order's [!DNL Google Analytics] source` aus.
1. Wenn ein Pfad nicht automatisch aufgefüllt wird, wählen Sie den Pfad aus, der die Kunden- und Auftragstabellen am besten verbindet.
1. Klicken Sie auf **[!UICONTROL Save]** , um die Dimension zu erstellen.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../assets/help_center2.gif)

Schließen Sie den Vorgang ab, indem Sie die Dimensionen `Customer's first order's` medium und `campaign` an die Tabelle `orders` anschließen. Schließen Sie die Dimensionen an, und überprüfen Sie bei Problemen [das Ende des Artikels](#stuck), ob Sie Hilfe benötigen.

### Aufwischen

Sie haben die Erstellung der Dimensionen abgeschlossen. Dies bedeutet, dass Sie jetzt leistungsstarke Analysen erstellen können, die die Leistung Ihrer verschiedenen Kanäle und Kampagnen verfolgen. Beachten Sie, dass die **neuen Spalten erst verfügbar sind, nachdem das nächste Update abgeschlossen ist**.

Einige der beliebtesten Dimensionen werden in diesem Thema behandelt, aber der Himmel ist das Limit - versuchen Sie, Ihre eigene zu erstellen oder Sie können uns gerne pingen, wenn Sie Hilfe beim Erkunden anderer Optionen wünschen. 

### Weitere Hinweise

**`Orders`Tabelle 1**: Beim Erstellen der Dimensionen `Order's [!DNL Google Analytics]` Medium und `campaign` besteht der Unterschied zwischen den in Schritt 12 ausgewählten Spalten. In diesem Beispiel war die Spalte `Source`.

**`Customers`table**: Beim Erstellen der Dimensionen `Customer's first order's [!DNL Google Analytics]` medium und `campaign` ist der Unterschied die in Schritt 5 ausgewählte Spalte. In diesem Beispiel war die Spalte die Quelle `Order's [!DNL Google Analytics]`.

**`Orders`Tabelle 2**: Beim Verbinden der Spalten `Customer's first order's [!DNL Google Analytics]` Medium und `campaign` mit der Tabelle `orders` besteht der Unterschied aus den in Schritt 5 ausgewählten Spalten. In diesem Beispiel war die Spalte die Quelle `Customer's first order's [!DNL Google Analytics]`.
