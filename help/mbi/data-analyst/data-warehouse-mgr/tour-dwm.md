---
title: Data Warehouse-Manager
description: Erfahren Sie, wie Sie die Synchronisierungseinstellungen für Tabellen und Spalten verwalten, einen Drilldown im Schema einer Tabelle durchführen und berechnete Spalten für die Verwendung in Berichten erstellen.
exl-id: b9577919-0db0-47f1-a426-1abe48443ac0
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 0%

---

# Data Warehouse-Manager

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md)

Der Data Warehouse-Manager, auf den Sie durch Klicken auf **[!UICONTROL Manage Data > Data Warehouse]** zugreifen können, ist das Portal zu Ihrer [!DNL Adobe Commerce Intelligence] -Data Warehouse. Mithilfe des Data Warehouse-Managers können Sie Einstellungen für die Tabellen- und Spaltensynchronisierung verwalten, einen Drilldown im Schema einer Tabelle durchführen und berechnete Spalten für die Verwendung in Berichten erstellen.

Dieses Thema behandelt:

* [Weg lernen](#learning)
* [Tabellen und Spalten synchronisieren](#syncing)
* [Berechnete Spalten erstellen](#calculated)
* [Tabellen löschen und Spalten entfernen](#delete)
* [Synchronisieren neuer Tabellen im Hintergrund](#syncnew)
* [Wann kann ich meine neuen Spalten verwenden?](#when)

## Weg lernen {#learning}

Die linke Seite der Seite &quot;`Data Warehouse Manager`&quot; enthält die Tabellenliste, mit der Sie mühelos zwischen Tabellen umschalten können. Wenn Sie eine Tabelle aus der Liste auswählen, wird der Tabellenverwaltungsbereich mit dem Schema der Tabelle gefüllt, in dem Sie die ausgewählte Tabelle ändern können.

In der Tabellenliste werden Tabellen nach ihrer Verbindungsquelle gruppiert. Diese Quellen werden unter [!UICONTROL Manage Data > Integrations] hinzugefügt und können entweder eine Datenbank, eine [API](https://developer.adobe.com/commerce/services/reporting/) oder ein Drittanbieter-Connector sein. Oben in der Tabellenliste befindet sich ein Suchfeld, mit dem Sie die gewünschten Tabellen leicht finden können.

Unter dem Suchfeld sehen Sie zwei Optionen: `All Tables` und `Synced Tables`. Die Option &quot;`All Tables`&quot; listet alle Tabellen auf, die Sie Ihrer Data Warehouse zur Verfügung gestellt haben und die sowohl synchronisierte als auch nicht synchronisierte Tabellen enthalten.

Die Option `Synced Tables` zeigt alle Tabellen an, die bereits zu Ihrer Data Warehouse hinzugefügt wurden und deren Daten aus den ausgewählten Spalten repliziert werden.

Sehen Sie die Tabelle, nach der Sie suchen, nicht in der Liste `All Tables`? Dafür gibt es einige mögliche Gründe:

* Die Datenquelle wurde noch nicht hinzugefügt
* Die Datenquelle ist eine Datenbank und der von Ihnen erstellte Benutzer &quot;[!DNL Commerce Intelligence]&quot; hat keinen Zugriff. In diesem Fall müssen Sie oder Ihr Datenbankadministrator den Zugriff gewähren.
* Die Datenquelle oder Tabelle wurde kürzlich hinzugefügt und noch nicht synchronisiert.

## Tabellen und Spalten synchronisieren {#syncing}

### Synchronisieren neuer Tabellen und nativer Spalten

Der Data Warehouse Manager bietet Ihnen nicht nur die Möglichkeit, Ihre Datenquellen einfach anzuzeigen und zu verwalten, sondern Sie können auch die einzelnen Tabellen und Spalten auswählen, die Sie synchronisieren möchten.

1. Klicken Sie auf die Option `All Tables` und suchen Sie die Tabelle, die Sie synchronisieren möchten.
1. Klicken Sie auf den Namen der Tabelle, um eine Vorschau des Schemas anzuzeigen. Wenn die Tabelle neu ist, werden alle Spalten als `Unsynced` angezeigt.
1. Überprüfen Sie die Spalten, die Sie synchronisieren möchten.

   >[!NOTE]
   >
   >Spalten, die in einer Tabelle nativ sind, haben Aus Ihrer Datenbank in der Spalte `Location` .

1. Achten Sie darauf, die Spalten &quot;`Primary Key`&quot; zu aktivieren. Diese Spalten haben ein Schlüsselsymbol neben dem Spaltennamen. Zum ordnungsgemäßen Synchronisieren der Daten auf der Data Warehouse ist ein `Primary Key` erforderlich.

   Wenn Sie eine Tabelle synchronisieren, die direkt aus Ihrer Datenbank stammt, kann es sein, dass `Primary Keys` nicht angezeigt wird. Wenden Sie sich in diesem Fall an Ihren Datenbankadministrator, um das Hinzufügen eines Primärschlüssels zur Tabelle anzufordern.
1. Klicken Sie abschließend auf die Schaltfläche ![button](../../assets/button.png) .

Ein *Erfolg!Die Meldung* wird angezeigt und der Status ändert sich für die ausgewählten Spalten in `Pending` . Nach Abschluss der nächsten vollständigen Aktualisierung stehen die neu synchronisierten Tabellen und Spalten zur Verwendung in Berichten zur Verfügung. Sie können auch nach der ersten Synchronisierung neue [Replikationsmethoden](./cfg-replication-methods.md) festlegen.

Im Folgenden finden Sie einen kurzen Überblick über den gesamten Prozess:

![Hinzufügen von Spalten zu Ihrem Data Warehouse](../../assets/DW_sync.gif)

### Synchronisieren neuer Tabellen im Hintergrund {#syncnew}

Wenn Sie eine große Tabelle zum ersten Mal synchronisieren, muss Ihr Data Warehouse rückwirkend alle Datenpunkte in der Tabelle erfassen, bevor Sie fortlaufend neue Daten erfassen. Wenn Ihre Tabelle groß ist, sollten Sie diese anfängliche Synchronisierung nicht in der Reihenfolge mit Ihrem **Aktualisierungszyklus** ausführen lassen. In diesem Fall soll die anfängliche Synchronisierung im Hintergrund in *parallel* mit einem derzeit ausgeführten Update erfolgen.

Um dies sicherzustellen, sollten Sie die Option `Save and Sync Data Immediately` zum ersten Mal zum Synchronisieren dieser Tabelle auswählen.

### Überprüfen auf neue Tabellen und Spalten {#forceupdate}

Ihre Data Warehouse erkennt nicht automatisch neue Quellen, Tabellen oder Spalten, sobald sie hinzugefügt werden. Ein Synchronisierungsprozess läuft die ganze Woche über, um neue Ergänzungen zu finden und sie verfügbar zu machen. Sie können jedoch eine Struktursynchronisierung erzwingen, wenn Sie vor Ausführung des Prozesses auf neu hinzugefügte Tabellen und Spalten zugreifen möchten.

Unter der Suchleiste in der Tabellenliste befindet sich ein `Check for new tables and columns` -Link. Durch Klicken auf diesen Link wird der Prozess der Struktursynchronisierung erzwungen und gestartet. Nach 10 Minuten sind in der Regel neue Ergänzungen verfügbar. Aktualisieren Sie die Seite, um die neue Quelle, Tabelle oder Spalte anzuzeigen.

## Erstellen berechneter Spalten {#calculated}

Die einfache Möglichkeit, Daten aus all Ihren Quellen zu sehen und zu verwalten, erleichtert das Auffinden von Einblicken in Ihr Unternehmen. Im Data Warehouse-Manager können Sie jedoch noch einen Schritt weiter gehen, indem Sie berechnete Spalten in Ihren Tabellen erstellen. `Calculated` -Spalten leiten neue Informationen aus Ihren vorhandenen Daten ab.

Angenommen, Sie möchten Ihrer `users`-Tabelle `user's lifetime revenue` hinzufügen, um Benutzer mit hohem Wert zu finden. Oder wenn Sie Umsätze nach Geschlecht segmentieren möchten, können Sie Ihrer `orders` Tabelle `customer's gender` hinzufügen.

Weitere Informationen finden Sie in diesem [Tutorial](../../data-analyst/data-warehouse-mgr/creating-calculated-columns.md).

## Tabellen löschen und Spalten entfernen {#delete}

So wie Sie Tabellen und Spalten auswählen können, um sie mit Ihrer Data Warehouse zu synchronisieren, können Sie sie auch ablegen oder entfernen.

>[!NOTE]
>
>Wenn Sie eine Tabelle löschen oder Spalten entfernen, werden alle abhängigen Berichte, Metriken, Filtersätze und Spalten gelöscht, sobald Sie den Löschvorgang bestätigt haben. Stellen Sie sicher, dass Sie dies tun möchten - **Diese Aktion kann nicht rückgängig gemacht werden.**

Machen Sie sich keine Gedanken, wenn Sie versehentlich auf **[!UICONTROL Delete]** klicken. Eine Abhängigkeitsprüfung wird ausgeführt, bevor etwas gelöscht wird. Daher haben Sie die Möglichkeit, alles zu überprüfen, bevor Sie bestätigen.

Um Spalten zu entfernen, klicken Sie auf die Tabelle, zu der die Spalte gehört. Markieren Sie die Spalten, die Sie entfernen möchten, und klicken Sie auf die Schaltfläche ![button\_1.png](../../assets/button_1.png) .

Um eine synchronisierte Tabelle zu entfernen, wählen Sie alle Spalten in der Tabelle aus und klicken Sie erneut auf die Schaltfläche ![button](../../assets/button_1.png) . Dadurch werden alle nativen und berechneten Spalten, die diese Tabelle verwenden, aus Ihrer Data Warehouse entfernt.

### Änderungen bestätigen

Unabhängig davon, ob Sie eine Tabelle ablegen oder Spalten entfernen, wird eine Abhängigkeitsprüfung ausgeführt, bevor der Löschvorgang abgeschlossen ist. Abhängigkeiten sind berechnete Spalten, Metriken, Filtersätze und Berichte, die die zu entfernende Tabelle oder Spalte(n) verwenden. Alle erkannten Abhängigkeiten werden angezeigt - an dieser Stelle können Sie den Prozess abbrechen oder auf **[!UICONTROL Confirm Changes]** klicken, um die Tabelle/die Spalten abzulegen.

Während gelöschte Abhängigkeiten nicht wiederhergestellt werden können, sind die Tabellen und Spalten weiterhin verfügbar, wenn Sie in Zukunft eine erneute Synchronisierung nativer Spalten benötigen.

Hier finden Sie einen kurzen Überblick über das Entfernen einer Spalte:

![Entfernen einer Spalte aus Ihrem Data Warehouse](../../assets/DW_delete.gif)

## Wann kann ich meine neuen Spalten verwenden? {#when}

Neue synchronisierte Spalten und neue/aktualisierte berechnete Spalten können nach Abschluss der nächsten vollständigen Aktualisierung verwendet werden. Wenn noch keine Aktualisierung ausgeführt wird, können Sie eine Aktualisierung erzwingen, indem Sie oben auf der Seite `Data Warehouse` oder `Integrations` auf **[!UICONTROL Force update]** klicken. Sie können auch eine E-Mail-Benachrichtigung nach Abschluss der Aktualisierung planen, indem Sie auf **[!UICONTROL Email me when complete]** klicken.

Wenn Sie bereit sind, Ihre neuen Spalten in Berichten zu verwenden, [müssen Sie sie zuerst zu den Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md). Auch wenn die Daten erst nach Abschluss der Aktualisierung verfügbar sind, können Sie in Berichten weiterhin neue Spalten verwenden. Daten im Bericht werden nach Abschluss der Aktualisierung angezeigt.

## Aufwischen

Dieser Artikel deckte eine Menge Material ab. Jetzt sollten Sie genau wissen, was eine Datenbank ist, wie Daten organisiert sind, wie Tabellen miteinander in Beziehung stehen und was Sie mit dem Data Warehouse Manager tun können.

Testen Sie Ihr Wissen, indem Sie [eine berechnete Spalte erstellen](../data-warehouse-mgr/creating-calculated-columns.md) oder [ einige interessante Berichte erstellen](../../tutorials/using-visual-report-builder.md).
