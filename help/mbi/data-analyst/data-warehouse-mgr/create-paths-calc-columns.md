---
title: Erstellen oder Löschen von Pfaden für berechnete Spalten
description: Erfahren Sie, wie Sie einen Pfad definieren, der beschreibt, wie die Tabelle, in der Sie eine Spalte erstellen, mit der Tabelle zusammenhängt, aus der Sie Informationen abrufen.
exl-id: 734a8046-8058-4f03-93a2-8d59b9be6d2d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Erstellen oder Löschen von Pfaden für berechnete Spalten

## Neuerung berechneter Spalten

Beim Erstellen von [berechneten Spalten](../data-warehouse-mgr/creating-calculated-columns.md) in Ihrer Data Warehouse werden Sie aufgefordert, einen Pfad zu definieren, der beschreibt, wie die Tabelle, in der Sie eine Spalte erstellen, mit der Tabelle verbunden ist, aus der Sie Informationen abrufen. Um einen Pfad erfolgreich zu erstellen, müssen Sie zwei Dinge wissen:

1. Beziehung der Tabellen in Ihren Datenbanken
1. Die primären und Fremdschlüssel, die diese Beziehung definieren

Wenn Sie diese Informationen kennen, können Sie einfach einen Pfad entsprechend den Anweisungen in diesem Thema erstellen. Sie können einen technischen Experten in Ihrem Unternehmen fragen oder sich an das [Professional Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) wenden.

## Aktualisierung von Tabellenbeziehungen und Schlüsseltypen {#refresher}

### Tabellenbeziehungen {#relationships}

Dieses Konzept wird im Artikel [Grundlegendes und Auswerten von Tabellenbeziehungen](../../data-analyst/data-warehouse-mgr/table-relationships.md) behandelt, aber eine schnelle Zusammenfassung schadet niemandem, oder?

Tabellen können auf drei Arten miteinander verbunden werden:

| **`Relationship Type`** | **`Example`** |
|-----|-----|
| **`one-to-one`** | Das Verhältnis zwischen Personen und Führerscheinnummern. Eine Person kann nur eine Führerscheinnummer besitzen, und eine Führerscheinnummer gehört nur einer Person. |
| **`one-to-many`** | Die Beziehung zwischen Bestellungen und Artikeln - eine Bestellung kann viele Elemente enthalten, aber ein Artikel gehört zu einer Bestellung. In diesem Fall ist die Auftragstabelle die eine Seite und die Artikeltabelle die n Seite. |
| **`many-to-many`** | Die Beziehung zwischen Produkten und Kategorien: Ein Produkt kann zu vielen Kategorien gehören und eine Kategorie kann viele Produkte enthalten. |

{style="table-layout:auto"}

Wenn eine Beziehung zwischen zwei Tabellen verstanden wird, kann damit bestimmt werden, welcher Pfad erstellt werden soll, um Informationen von einer Tabelle zur anderen zu bringen. Für diesen nächsten Schritt müssen die Primärschlüssel und Fremdschlüssel bekannt sein, die eine Tabellenbeziehung ermöglichen.

### Primäre und Fremdschlüssel {#keys}

Ein `Primary Key` ist eine unveränderliche Spalte oder ein Satz von Spalten, die eindeutige Werte in einer Tabelle erzeugt. Wenn ein Kunde beispielsweise eine Bestellung auf einer Website tätigt, wird der Tabelle `orders` in Ihrem Warenkorb eine neue Zeile mit dem neuen Wert `order_id` hinzugefügt. Mit diesem `order_id` können sowohl der Kunde als auch das Unternehmen den Fortschritt dieser bestimmten Bestellung verfolgen. Da die Bestell-ID eindeutig ist, ist sie normalerweise der `Primary Key` einer `orders` -Tabelle.

Ein `Foreign Key` ist eine Spalte, die innerhalb einer Tabelle erstellt wird und mit der Spalte `Primary Key` einer anderen Tabelle verknüpft ist. Fremdschlüssel erstellen Verweise zwischen Tabellen, sodass Analysten Datensätze einfach nachschlagen und verknüpfen können. Sagen Sie, Sie wollten wissen, welche Bestellungen zu den einzelnen Kunden gehörten. Die Spalte `customer id` (`Primary Key` der Tabelle `customers`) und die Spalte `order_id` (`Foreign Key` in der Tabelle `customers`, die auf die Tabelle `Primary Key` der Tabelle `orders` verweisen, ermöglichen es uns, diese Informationen zu verknüpfen und zu analysieren. Beim Erstellen eines Pfads werden Sie aufgefordert, sowohl `Primary Key` als auch `Foreign Key` zu definieren.

## Erstellen eines Pfads {#createpath}

Beim Erstellen einer Spalte in Ihrer Data Warehouse müssen Sie den Pfad definieren, der Informationen aus einer Tabelle in eine andere bringt. Manchmal werden Pfade vorbelegt, da ein Pfad zwischen Tabellen vorhanden ist. Wenn dies nicht der Fall ist, müssen Sie einen Pfad erstellen.

Verwenden Sie die Beziehung zwischen **Kunden** und **Bestellungen**, um Ihnen anzuzeigen, wie es funktioniert. Aufschlüsselung:

* Die Beziehung ist `one-to-many` - Ein Kunde kann viele Bestellungen haben, eine Bestellung kann jedoch nur einen Kunden haben. Dies gibt die Richtung der Beziehung an oder gibt an, wo die berechnete Spalte erstellt werden soll. In diesem Fall bedeutet dies, dass Informationen aus der `orders`-Tabelle in die `customers`-Tabelle aufgenommen werden können.
* Die `primary key`, die Sie verwenden möchten, ist `customers.customerid` oder die `customer ID` -Spalte in der `customers` -Tabelle.
* Die `foreign key`, die Sie verwenden möchten, ist `orders.customerid` oder die `customer ID` -Spalte in der `orders` -Tabelle.

Jetzt können Sie den Pfad erstellen.

1. Klicken Sie auf **[!UICONTROL Data > Data Warehouse]**.
1. Klicken Sie in der Tabellenliste auf die Tabelle, in der Sie die Spalte erstellen möchten. In diesem Beispiel handelt es sich um die Tabelle `customers`.
1. Das Tabellenschema wird angezeigt. Klicken Sie auf **[!UICONTROL Create New Column]**.
1. Geben Sie Ihrer Spalte einen Namen, z. B. `Customer's orders`.
1. Wählen Sie die Spaltendefinition aus. Sehen Sie sich den [Leitfaden für berechnete Spalten](../data-warehouse-mgr/creating-calculated-columns.md) für ein praktisches Cheatsheet an.
1. Klicken Sie im Dropdown-Menü [!UICONTROL Select table and column] auf die Option **[!UICONTROL Create new path]** .

   ![Pfade für berechnete Spalten-Modal erstellen](../../assets/Creating_Paths_modal.png)

1. Wählen Sie mithilfe der Dropdown-Liste die primären und ausländischen Schlüssel für jede Tabelle aus.

   Auf der Seite `Many` wählen Sie `orders.customerid` - denken Sie daran, Kunden können viele Bestellungen haben.

   Auf der Seite `One` wählen Sie `customers.customerid` - eine Bestellung kann nur einen Kunden enthalten.

1. Klicken Sie auf **[!UICONTROL Save]** , um den Pfad zu speichern und die Erstellung der Spalte abzuschließen.

### Einschränkungen beim Erstellen von Pfaden {#limits}

* **[!DNL Commerce Intelligence]kann keine Primär-/Fremdschlüsselbeziehungen erraten**. Sie möchten keine falschen Daten in Ihr Konto einführen. Daher müssen Pfade manuell erstellt werden.

* **Derzeit können Pfade nur zwischen zwei verschiedenen Tabellen angegeben werden**. Sind mehr als zwei Tabellen an der Logik beteiligt, die Sie nachbilden möchten? Dann kann es sinnvoll sein, (1) zuerst eine zwischengeschaltete Tabelle zu verwenden und dann die Tabelle &quot;endgültiges Ziel&quot; zu öffnen, oder (2) mit dem [Professional Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) Kontakt aufzunehmen, um den besten Ansatz für Ihre Ziele zu finden.

* **Eine Spalte kann nur die Fremdschlüsselreferenz für EINEN Pfad gleichzeitig sein**. Wenn beispielsweise `order_items.order_id` auf `orders.id` verweist, kann `order_items.order_id` nicht auf irgendetwas anderes verweisen.

* **`Many-to-many`-Pfade können technisch erstellt werden, führen aber oft zu schlechten Daten, da keine der Seiten ein echter `one-to-many` Fremdschlüssel** ist. Die beste Methode, diese Pfade zu erreichen, hängt immer von der gewünschten spezifischen Analyse ab. Wenden Sie sich an das RJ-Analyseteam, um die beste Lösung zu ermitteln.

Wenn Sie aufgrund einer oder mehrerer der oben genannten Einschränkungen keine berechnete Spalte erstellen können, wenden Sie sich an den Support mit einer Beschreibung der Spalte, die Sie sind

## Berechneten Spaltenpfad löschen {#delete}

einen falschen Pfad in Ihrem Data Warehouse erstellt? Oder vielleicht machen Sie eine kleine Frühlingsreinigung und wollen aufräumen? Wenn Sie einen Pfad aus Ihrem Konto löschen müssen, können Sie [ein Ticket an Adobe Support-Analysten senden](../../guide-overview.md#Submitting-a-Support-Ticket). **Stellen Sie sicher, dass Sie den Namen des Pfads einschließen!**

## Aufwischen {#wrapup}

Jetzt ist es Ihnen bequem, Pfade für berechnete Spalten in Ihrer Data Warehouse zu erstellen. Wenn Sie sich bezüglich eines bestimmten Pfads immer noch unsicher sind, können Sie immer auf **[!UICONTROL Support]** in Ihrem [!DNL Commerce Intelligence]-Konto klicken, um Hilfe zu erhalten.

## Verwandte

* [Grundlegendes zu und Auswerten von Tabellenbeziehungen](../data-warehouse-mgr/table-relationships.md)
* [Erstellen von Pfaden für berechnete Spalten](../data-warehouse-mgr/create-paths-calc-columns.md)
* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md), die erstellt werden sollen.
