---
title: Erstellen oder Löschen von Pfaden für berechnete Spalten
description: Erfahren Sie, wie Sie einen Pfad definieren, der beschreibt, wie die Tabelle, in der Sie eine Spalte erstellen, mit der Tabelle zusammenhängt, aus der Sie Informationen abrufen.
exl-id: 734a8046-8058-4f03-93a2-8d59b9be6d2d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Erstellen oder Löschen von Pfaden für berechnete Spalten

## Neuerung berechneter Spalten

Wann [berechnete Spalten erstellen](../data-warehouse-mgr/creating-calculated-columns.md) In Ihrer Data Warehouse werden Sie aufgefordert, einen Pfad zu definieren, der beschreibt, wie die Tabelle, in der Sie eine Spalte erstellen, mit der Tabelle zusammenhängt, aus der Sie Informationen abrufen. Um einen Pfad erfolgreich zu erstellen, müssen Sie zwei Dinge wissen:

1. Beziehung der Tabellen in Ihren Datenbanken
1. Die primären und Fremdschlüssel, die diese Beziehung definieren

Wenn Sie diese Informationen kennen, können Sie einfach einen Pfad entsprechend den Anweisungen in diesem Thema erstellen. Sie können einen technischen Experten in Ihrer Organisation fragen oder sich an die [Professional Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

## Aktualisierung von Tabellenbeziehungen und Schlüsseltypen {#refresher}

### Tabellenbeziehungen {#relationships}

Dieses Konzept wird im Abschnitt [Artikel zum Verstehen und Auswerten von Tabellenbeziehungen](../../data-analyst/data-warehouse-mgr/table-relationships.md), aber eine kurze Zusammenfassung schadet nie jemandem, nicht wahr?

Tabellen können auf drei Arten miteinander verbunden werden:

| **`Relationship Type`** | **`Example`** |
|-----|-----|
| **`one-to-one`** | Das Verhältnis zwischen Personen und Führerscheinnummern. Eine Person kann nur eine Führerscheinnummer besitzen, und eine Führerscheinnummer gehört nur einer Person. |
| **`one-to-many`** | Die Beziehung zwischen Bestellungen und Artikeln - eine Bestellung kann viele Elemente enthalten, aber ein Artikel gehört zu einer Bestellung. In diesem Fall ist die Auftragstabelle die eine Seite und die Artikeltabelle die n Seite. |
| **`many-to-many`** | Die Beziehung zwischen Produkten und Kategorien: Ein Produkt kann zu vielen Kategorien gehören und eine Kategorie kann viele Produkte enthalten. |

{style="table-layout:auto"}

Wenn eine Beziehung zwischen zwei Tabellen verstanden wird, kann damit bestimmt werden, welcher Pfad erstellt werden soll, um Informationen von einer Tabelle zur anderen zu bringen. Für diesen nächsten Schritt müssen die Primärschlüssel und Fremdschlüssel bekannt sein, die eine Tabellenbeziehung ermöglichen.

### Primäre und Fremdschlüssel {#keys}

A `Primary Key` ist eine unveränderliche Spalte oder ein Satz von Spalten, die eindeutige Werte in einer Tabelle erzeugt. Wenn beispielsweise ein Kunde eine Bestellung auf einer Website tätigt, wird dem `orders` mit einem neuen `order_id`. Diese `order_id` ermöglicht es sowohl dem Kunden als auch dem Unternehmen, den Fortschritt dieser bestimmten Bestellung zu verfolgen. Da die Bestell-ID eindeutig ist, ist normalerweise der `Primary Key` von `orders` Tabelle.

A `Foreign Key` ist eine Spalte, die innerhalb einer Tabelle erstellt wird, die mit dem `Primary Key` Spalte einer anderen Tabelle. Fremdschlüssel erstellen Verweise zwischen Tabellen, sodass Analysten Datensätze einfach nachschlagen und verknüpfen können. Sagen Sie, Sie wollten wissen, welche Bestellungen zu den einzelnen Kunden gehörten. Die `customer id` column (`Primary Key` des `customers` und der `order_id` column (`Foreign Key` im `customers` -Tabelle, die auf die `Primary Key` des `orders` -Tabelle) können wir diese Informationen verknüpfen und analysieren. Beim Erstellen eines Pfads werden Sie aufgefordert, beide `Primary Key` und `Foreign Key`.

## Erstellen eines Pfads {#createpath}

Beim Erstellen einer Spalte in Ihrer Data Warehouse müssen Sie den Pfad definieren, der Informationen aus einer Tabelle in eine andere bringt. Manchmal werden Pfade vorbelegt, da ein Pfad zwischen Tabellen vorhanden ist. Wenn dies nicht der Fall ist, müssen Sie einen Pfad erstellen.

Verwenden Sie die Beziehung zwischen **Kunden** und **Bestellungen** um Ihnen zu zeigen, wie es gemacht wird. Aufschlüsselung:

* Die Beziehung lautet `one-to-many` - ein Kunde kann viele Bestellungen haben, aber eine Bestellung kann nur einen Kunden haben. Dies gibt die Richtung der Beziehung an oder gibt an, wo die berechnete Spalte erstellt werden soll. In diesem Fall bedeutet dies Informationen aus dem `orders` -Tabelle kann in die `customers` Tabelle.
* Die `primary key` Sie verwenden möchten, ist `customers.customerid`oder die `customer ID` in der `customers` Tabelle.
* Die `foreign key` Sie verwenden möchten, ist `orders.customerid`oder die `customer ID` in der `orders` Tabelle.

Jetzt können Sie den Pfad erstellen.

1. Klicken **[!UICONTROL Data > Data Warehouse]**.
1. Klicken Sie in der Tabellenliste auf die Tabelle, in der Sie die Spalte erstellen möchten. In diesem Beispiel ist dies die `customers` Tabelle.
1. Das Tabellenschema wird angezeigt. Klicken **[!UICONTROL Create New Column]**.
1. Benennen Sie die Spalte beispielsweise `Customer's orders`.
1. Wählen Sie die Spaltendefinition aus. Sehen Sie sich die [Berechnete Spaltenanleitung](../data-warehouse-mgr/creating-calculated-columns.md) für ein praktisches Cheatsheet.
1. Im [!UICONTROL Select table and column] Dropdown-Liste klicken Sie auf die **[!UICONTROL Create new path]** -Option.

   ![Erstellen von Pfaden für berechnete Spalten modal](../../assets/Creating_Paths_modal.png)

1. Wählen Sie mithilfe der Dropdown-Liste die primären und ausländischen Schlüssel für jede Tabelle aus.

   Im `Many` side, wählen Sie `orders.customerid` - Denken Sie daran, Kunden können viele Bestellungen haben.

   Im `One` side, wählen Sie `customers.customerid` - eine Bestellung kann nur einen Kunden haben.

1. Klicks **[!UICONTROL Save]** , um den Pfad zu speichern und die Erstellung der Spalte abzuschließen.

### Einschränkungen beim Erstellen von Pfaden {#limits}

* **[!DNL Commerce Intelligence]Primär-/Fremdschlüsselbeziehungen nicht erraten**. Sie möchten keine falschen Daten in Ihr Konto einführen. Daher müssen Pfade manuell erstellt werden.

* **Derzeit können Pfade nur zwischen zwei verschiedenen Tabellen angegeben werden**. Sind mehr als zwei Tabellen an der Logik beteiligt, die Sie nachbilden möchten? Dann kann es sinnvoll sein, (1) zuerst eine zwischengeschaltete Tabelle zu verwenden, dann die Tabelle &quot;endgültiges Ziel&quot;, oder (2) mit der [Professional Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) um den besten Ansatz für Ihre Ziele zu finden.

* **Eine Spalte kann nur die Fremdschlüsselreferenz für EINEN Pfad gleichzeitig sein.**. Wenn beispielsweise `order_items.order_id` weist auf `orders.id`, dann `order_items.order_id` kann auf nichts anderes verweisen.

* **`Many-to-many`Pfade können technisch erstellt werden, führen aber oft zu schlechten Daten, da keine Seite wahr ist `one-to-many` Fremdschlüssel**. Die beste Methode, diese Pfade zu erreichen, hängt immer von der gewünschten spezifischen Analyse ab. Wenden Sie sich an das RJ-Analyseteam, um die beste Lösung zu ermitteln.

Wenn Sie aufgrund einer oder mehrerer der oben genannten Einschränkungen keine berechnete Spalte erstellen können, wenden Sie sich an den Support mit einer Beschreibung der Spalte, die Sie sind

## Berechneten Spaltenpfad löschen {#delete}

einen falschen Pfad in Ihrem Data Warehouse erstellt? Oder vielleicht machen Sie eine kleine Frühlingsreinigung und wollen aufräumen? Wenn Sie einen Pfad aus Ihrem Konto löschen müssen, können Sie [Senden eines Tickets an Adobe-Support-Analysten](../../guide-overview.md#Submitting-a-Support-Ticket). **Stellen Sie sicher, dass Sie den Namen des Pfads einschließen!**

## Aufwischen {#wrapup}

Jetzt ist es Ihnen bequem, Pfade für berechnete Spalten in Ihrer Data Warehouse zu erstellen. Wenn Sie sich bei einem bestimmten Pfad immer noch unsicher sind, können Sie immer auf **[!UICONTROL Support]** in [!DNL Commerce Intelligence] -Konto, um Hilfe zu erhalten.

## Verwandte

* [Grundlegendes zu und Auswerten von Tabellenbeziehungen](../data-warehouse-mgr/table-relationships.md)
* [Erstellen von Pfaden für berechnete Spalten](../data-warehouse-mgr/create-paths-calc-columns.md)
* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md) Versuchen Sie zu erstellen.
