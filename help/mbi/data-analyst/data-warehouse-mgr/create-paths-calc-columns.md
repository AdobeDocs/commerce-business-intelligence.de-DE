---
title: Erstellen oder Löschen von Pfaden für berechnete Spalten
description: Erfahren Sie, wie Sie einen Pfad definieren, der beschreibt, wie die Tabelle, in der Sie eine Spalte erstellen, mit der Tabelle verknüpft ist, aus der Sie Informationen abrufen.
exl-id: 734a8046-8058-4f03-93a2-8d59b9be6d2d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Erstellen oder Löschen von Pfaden für berechnete Spalten

## Aktualisierung der berechneten Spalten

Beim [Erstellen berechneter Spalten](../data-warehouse-mgr/creating-calculated-columns.md) in Ihrem Data Warehouse werden Sie aufgefordert, einen Pfad zu definieren, der beschreibt, wie die Tabelle, in der Sie eine Spalte erstellen, mit der Tabelle verknüpft ist, aus der Sie Informationen abrufen. Um einen Pfad erfolgreich zu erstellen, müssen Sie zwei Dinge wissen:

1. Beziehung der Tabellen in Ihren Datenbanken zueinander
1. Die primären und Fremdschlüssel, die diese Beziehung definieren

Wenn Sie diese Informationen kennen, können Sie einfach einen Pfad erstellen, der den Anweisungen in diesem Thema folgt. Sie können einen technischen Experten in Ihrer Organisation fragen oder sich an das [Professional Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de) wenden.

## Aktualisierung von Tabellenbeziehungen und Schlüsseltypen {#refresher}

### Tabellenbeziehungen {#relationships}

Dieses Konzept wird im Artikel [Verstehen und Auswerten von Tabellenbeziehungen“ behandelt](../../data-analyst/data-warehouse-mgr/table-relationships.md) aber eine kurze Zusammenfassung schadet niemandem, oder?

Tabellen können auf eine von drei Arten miteinander verknüpft werden:

| **`Relationship Type`** | **`Example`** |
|-----|-----|
| **`one-to-one`** | Die Beziehung zwischen Personen und Führerscheinnummern. Eine Person kann nur eine Führerscheinnummer haben, und eine Führerscheinnummer gehört nur zu einer Person. |
| **`one-to-many`** | Die Beziehung zwischen Bestellungen und Artikeln - eine Bestellung kann viele Artikel enthalten, aber ein Artikel gehört zu einer einzigen Bestellung. In diesem Fall ist die Tabelle Orders die eine Seite und die Tabelle Items die viele Seite. |
| **`many-to-many`** | Die Beziehung zwischen Produkten und Kategorien: Ein Produkt kann zu vielen Kategorien gehören, und eine Kategorie kann viele Produkte enthalten. |

{style="table-layout:auto"}

Wenn eine Beziehung zwischen zwei Tabellen verstanden wird, kann sie verwendet werden, um zu bestimmen, welcher Pfad erstellt werden soll, um Informationen von einer Tabelle zur anderen zu bringen. Für diesen nächsten Schritt müssen Sie die Primär- und Fremdschlüssel kennen, die eine Tabellenbeziehung ermöglichen.

### Primäre und Fremdschlüssel {#keys}

Ein `Primary Key` ist eine unveränderliche Spalte oder ein Satz von Spalten, die bzw. der eindeutige Werte innerhalb einer Tabelle erzeugt. Wenn beispielsweise ein Kunde eine Bestellung auf einer Website aufgibt, wird der `orders`-Tabelle in Ihrem Warenkorb eine neue Zeile mit einer neuen `order_id` hinzugefügt. Auf diese `order_id` können sowohl der Kunde als auch das Unternehmen den Fortschritt dieser spezifischen Bestellung verfolgen. Da die Bestell-ID eindeutig ist, handelt es sich normalerweise um den `Primary Key` einer `orders`.

Ein `Foreign Key` ist eine Spalte, die in einer Tabelle erstellt wird und mit der `Primary Key` Spalte einer anderen Tabelle verknüpft ist. Fremdschlüssel erstellen Verweise zwischen Tabellen, sodass Analysten Datensätze einfach nachschlagen und miteinander verknüpfen können. Angenommen, Sie möchten wissen, welche Bestellungen zu jedem Ihrer Kunden gehören. Die `customer id` Spalte (`Primary Key` der `customers`) und die `order_id` Spalte (`Foreign Key` in der `customers` Tabelle, die auf die `Primary Key` der `orders` Tabelle verweist) ermöglichen es uns, diese Informationen zu verknüpfen und zu analysieren. Beim Erstellen eines Pfads werden Sie aufgefordert, sowohl den `Primary Key` als auch den `Foreign Key` zu definieren.

## Erstellen eines Pfads {#createpath}

Beim Erstellen einer Spalte im Data Warehouse müssen Sie den Pfad definieren, der Informationen von einer Tabelle in eine andere bringt. Manchmal werden Pfade vorab ausgefüllt, da ein Pfad zwischen Tabellen vorhanden ist. Sollte dies jedoch nicht der Fall sein, müssen Sie einen erstellen.

Verwenden Sie die Beziehung zwischen **Kunden** und **Bestellungen**, um Ihnen zu zeigen, wie dies geschieht. Aufschlüsselung:

* Die Beziehung ist `one-to-many`: Ein Kunde kann viele Bestellungen haben, aber eine Bestellung kann nur einen Kunden haben. Dies gibt Aufschluss über die Richtung der Beziehung oder darüber, wo die berechnete Spalte erstellt werden soll. In diesem Fall bedeutet dies, dass Informationen aus der `orders` Tabelle in die `customers` Tabelle eingebracht werden können.
* Der `primary key`, den Sie verwenden möchten, ist `customers.customerid` oder die `customer ID` Spalte in der `customers`.
* Der `foreign key`, den Sie verwenden möchten, ist `orders.customerid` oder die `customer ID` Spalte in der `orders`.

Jetzt können Sie den Pfad erstellen.

1. Klicken Sie auf **[!UICONTROL Data > Data Warehouse]**.
1. Klicken Sie in der Tabellenliste auf die Tabelle, in der Sie die Spalte erstellen möchten. In diesem Beispiel ist es die `customers`.
1. Das Tabellenschema wird angezeigt. Klicken Sie auf **[!UICONTROL Create New Column]**.
1. Geben Sie der Spalte einen Namen, z. B. `Customer's orders`.
1. Wählen Sie die Definition für die Spalte aus. Im [Leitfaden für berechnete Spalten](../data-warehouse-mgr/creating-calculated-columns.md) finden Sie eine praktische Anleitung.
1. Klicken Sie in der Dropdown-Liste [!UICONTROL Select table and column] auf die Option **[!UICONTROL Create new path]** .

   ![Erstellen von Pfaden für modale berechnete Spalten](../../assets/Creating_Paths_modal.png)

1. Wählen Sie mithilfe der Dropdown-Listen die Primär- und Fremdschlüssel für jede Tabelle aus.

   Auf der `Many` Seite wählen Sie `orders.customerid` aus - denken Sie daran, dass Kunden viele Bestellungen haben können.

   Auf der `One` Seite wählen Sie `customers.customerid` aus. Eine Bestellung kann nur einen Kunden haben.

1. Klicken Sie auf **[!UICONTROL Save]** , um den Pfad zu speichern und die Erstellung der Spalte abzuschließen.

### Einschränkungen beim Erstellen von Pfaden {#limits}

* **[!DNL Commerce Intelligence]kann keine Primär-/Fremdschlüsselbeziehungen erraten**. Sie möchten keine falschen Daten in Ihr Konto einschleusen. Daher müssen Pfade manuell erstellt werden.

* **Derzeit können Pfade nur zwischen zwei verschiedenen Tabellen angegeben werden**. Enthält die Logik, die Sie wiederherstellen möchten, mehr als zwei Tabellen? Es kann dann sinnvoll sein, (1) die Spalten zuerst mit einer Zwischentabelle und dann mit der Tabelle „Endziel“ zu verbinden, oder (2) sich mit dem [Professional Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de) beraten, um den besten Ansatz für Ihre Ziele zu finden.

* **Eine Spalte kann jeweils nur die Fremdschlüsselreferenz für einen Pfad sein**. Wenn `order_items.order_id` beispielsweise auf `orders.id` verweist, kann `order_items.order_id` auf nichts anderes verweisen.

* **`Many-to-many`Pfade können zwar technisch gesehen erstellt werden, erzeugen aber häufig fehlerhafte Daten, da keine Seite ein echter `one-to-many` Fremdschlüssel ist**. Die beste Herangehensweise an diese Pfade hängt immer von der gewünschten Analyse ab. Beraten Sie sich mit dem RJ-Analyst-Team, um die beste Lösung zu finden.

Wenn Sie aufgrund einer oder mehrerer der oben genannten Einschränkungen keine berechnete Spalte erstellen können, wenden Sie sich mit einer Beschreibung der entsprechenden Spalte an den Support

## Löschen eines berechneten Spaltenpfads {#delete}

Sie haben einen falschen Pfad in Ihrem Data Warehouse erstellt? Oder Sie machen vielleicht einen kleinen Frühjahrsputz und wollen aufräumen? Wenn Sie einen Pfad aus Ihrem Konto löschen müssen, können Sie [ein Ticket an den Adobe-Support senden](../../guide-overview.md#Submitting-a-Support-Ticket). **Stellen Sie sicher, dass Sie den Namen des Pfads angeben!**

## Verpackung {#wrapup}

Jetzt, da Sie mit dem Erstellen von Pfaden für berechnete Spalten in Ihrem Data Warehouse vertraut sind. Wenn Sie sich bezüglich eines bestimmten Pfads immer noch nicht sicher sind, denken Sie daran, dass Sie in Ihrem [!DNL Commerce Intelligence]-Konto immer auf **[!UICONTROL Support]** klicken können, um Hilfe zu erhalten.

## verwandt

* [Verstehen und Auswerten von Tabellenbeziehungen](../data-warehouse-mgr/table-relationships.md)
* [Erstellen von Pfaden für berechnete Spalten](../data-warehouse-mgr/create-paths-calc-columns.md)
* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md) Versuch der Erstellung.
