---
title: Data Warehouse-Manager
description: Erfahren Sie, wie Sie die Synchronisierungseinstellungen für Tabellen und Spalten verwalten, das Schema einer Tabelle aufschlüsseln und berechnete Spalten für die Verwendung in Berichten erstellen.
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

Der Data Warehouse-Manager, auf den durch Klicken auf **[!UICONTROL Manage Data > Data Warehouse]** zugegriffen wird, ist das Portal zu Ihrer [!DNL Adobe Commerce Intelligence] Data Warehouse. Mit dem Data Warehouse-Manager können Sie die Synchronisierungseinstellungen für Tabellen und Spalten verwalten, das Schema einer Tabelle aufschlüsseln und berechnete Spalten erstellen, die in Berichten verwendet werden sollen.

Dieses Thema behandelt:

* [Lernen](#learning)
* [Synchronisieren von Tabellen und Spalten](#syncing)
* [Berechnete Spalten erstellen](#calculated)
* [Tabellen ablegen und Spalten entfernen](#delete)
* [Synchronisieren neuer Tabellen im Hintergrund](#syncnew)
* [Wann kann ich meine neuen Spalten verwenden?](#when)

## Lernen {#learning}

Links auf `Data Warehouse Manager` Seite finden Sie die Tabellenliste, mit der Sie einfach zwischen Tabellen wechseln können. Wenn Sie eine Tabelle aus der Liste auswählen, wird der Bereich Tabellenverwaltung mit dem Schema der Tabelle gefüllt, in dem Sie die ausgewählte Tabelle ändern können.

Innerhalb der Tabellenliste werden Tabellen nach ihrer Verbindungsquelle gruppiert. Diese Quellen werden unter [!UICONTROL Manage Data > Integrations] hinzugefügt und können entweder eine Datenbank, eine [API](https://developer.adobe.com/commerce/services/reporting/) oder ein Connector eines Drittanbieters sein. Oben in der Tabellenliste gibt es ein Suchfeld, mit dem Sie die gewünschten Tabellen leicht finden können.

Unter dem Suchfeld werden zwei Optionen angezeigt: `All Tables` und `Synced Tables`. Die Option `All Tables` listet alle Tabellen auf, die Sie für Ihren Data Warehouse zur Verfügung gestellt haben, einschließlich synchronisierter und nicht synchronisierter Tabellen.

Die Option `Synced Tables` zeigt alle Tabellen an, die bereits zum Data Warehouse hinzugefügt wurden und deren Daten aus den ausgewählten Spalten repliziert werden.

Wird die Tabelle, nach der Sie suchen, nicht in der `All Tables` angezeigt? Dafür gibt es einige mögliche Gründe:

* Die Datenquelle wurde noch nicht hinzugefügt
* Die Datenquelle ist eine Datenbank, und der von Ihnen erstellte [!DNL Commerce Intelligence] hat keinen Zugriff. In diesem Fall müssen Sie oder Ihr Datenbankadministrator den Zugriff gewähren.
* Die Datenquelle oder Tabelle wurde kürzlich hinzugefügt und noch nicht synchronisiert

## Synchronisieren von Tabellen und Spalten {#syncing}

### Synchronisieren neuer Tabellen und nativer Spalten

Mit dem Data Warehouse-Manager können Sie nicht nur Ihre Datenquellen einfach anzeigen und verwalten, sondern auch die einzelnen Tabellen und Spalten auswählen, die Sie synchronisieren möchten.

1. Klicken Sie auf die Option `All Tables` und suchen Sie die Tabelle, die Sie synchronisieren möchten.
1. Klicken Sie auf den Namen der Tabelle, um eine Vorschau des Schemas anzuzeigen. Wenn die Tabelle neu ist, werden alle Spalten als `Unsynced` angezeigt.
1. Markieren Sie die Spalten, die Sie synchronisieren möchten.

   >[!NOTE]
   >
   >Native Spalten einer Tabelle enthalten in der `Location` Spalte Von Ihrer Datenbank .

1. Stellen Sie sicher, dass Sie die `Primary Key` Spalten überprüfen. Diese Spalten haben ein Schlüsselsymbol neben dem Spaltennamen. Ein `Primary Key` ist erforderlich, um Daten ordnungsgemäß mit der Data Warehouse zu synchronisieren.

   Wenn Sie eine Tabelle synchronisieren, die direkt aus Ihrer Datenbank stammt, ist es möglich, dass `Primary Keys` nicht gekennzeichnet wird. Wenden Sie sich in diesem Fall an Ihren Datenbankadministrator, um das Hinzufügen eines Primärschlüssels oder von Primärschlüsseln zur Tabelle anzufordern.
1. Klicken Sie abschließend auf die ![Schaltfläche](../../assets/button.png).

Ein *Erfolg!* wird eine Meldung angezeigt und der Status ändert sich für die ausgewählten Spalten in `Pending`. Nach Abschluss der nächsten vollständigen Aktualisierung stehen die neu synchronisierten Tabellen und Spalten zur Verwendung in Berichten zur Verfügung. Sie können auch neue [Replikationsmethoden](./cfg-replication-methods.md) nach der ersten Synchronisierung festlegen.

Im Folgenden finden Sie einen kurzen Überblick über den gesamten Prozess:

![Hinzufügen von Spalten zu Ihrem Data Warehouse](../../assets/DW_sync.gif)

### Synchronisieren neuer Tabellen im Hintergrund {#syncnew}

Wenn Sie eine große Tabelle zum ersten Mal synchronisieren, muss Ihr Data Warehouse rückwirkend alle Datenpunkte in der Tabelle erfassen, bevor Sie neue Daten laufend erfassen können. Wenn Ihre Tabelle groß ist, möchten Sie möglicherweise nicht, dass diese anfängliche Synchronisierung nacheinander mit Ihrem **Aktualisierungszyklus“ ausgeführt**. In diesem Fall soll die anfängliche Synchronisierung im Hintergrund (*)* alle derzeit ausgeführten Aktualisierungen erfolgen.

Um sicherzustellen, dass dies geschieht, sollten Sie die Option `Save and Sync Data Immediately` auswählen, mit der diese Tabelle zum ersten Mal synchronisiert wird.

### Überprüfung auf neue Tabellen und Spalten {#forceupdate}

Ihr Data Warehouse erkennt neue Quellen, Tabellen oder Spalten nicht automatisch, wenn sie hinzugefügt werden. Ein Synchronisierungsprozess läuft die ganze Woche, um neue Ergänzungen zu finden und verfügbar zu machen. Sie können jedoch eine Struktursynchronisierung erzwingen, wenn Sie auf neu hinzugefügte Tabellen und Spalten zugreifen möchten, bevor der Prozess ausgeführt wird.

Unter der Suchleiste in der Tabellenliste befindet sich ein `Check for new tables and columns` Link. Wenn Sie auf diesen Link klicken, wird der Struktursynchronisierungsprozess erzwungen. Neue Ergänzungen sind in der Regel nach 10 Minuten verfügbar. Aktualisieren Sie die Seite, um die neue Quelle, Tabelle oder Spalte anzuzeigen.

## Erstellen von berechneten Spalten {#calculated}

Die einfache Möglichkeit, Daten aus all Ihren Quellen zu sehen und zu verwalten, macht es viel einfacher, Einblicke in Ihr Unternehmen zu gewinnen. Im Data Warehouse-Manager können Sie jedoch einen Schritt weiter gehen, indem Sie in Ihren Tabellen berechnete Spalten erstellen. `Calculated` Spalten leiten neue Informationen aus Ihren vorhandenen Daten ab.

Angenommen, Sie möchten Ihrer `users`-Tabelle `user's lifetime revenue` hinzufügen, um Benutzer mit hohem Wert zu finden. Wenn Sie den Umsatz nach Geschlecht segmentieren möchten, können Sie `customer's gender` zu Ihrer `orders` hinzufügen.

Weitere Informationen finden Sie in diesem [Tutorial](../../data-analyst/data-warehouse-mgr/creating-calculated-columns.md).

## Tabellen ablegen und Spalten entfernen {#delete}

So wie Sie Tabellen und Spalten auswählen können, um sie mit Ihrem Data Warehouse zu synchronisieren, können Sie sie auch ablegen oder entfernen.

>[!NOTE]
>
>Durch Ablegen einer Tabelle oder Entfernen von Spalten werden alle abhängigen Berichte, Metriken, Filtersätze und Spalten gelöscht, sobald Sie den Löschvorgang bestätigen. Möchten Sie dies wirklich tun? (**Aktion kann nicht rückgängig gemacht werden.**

Machen Sie sich keine Sorgen, wenn Sie versehentlich auf **[!UICONTROL Delete]** klicken. Eine Abhängigkeitsprüfung wird ausgeführt, bevor etwas gelöscht wird, sodass Sie die Möglichkeit haben, alles zu überprüfen, bevor Sie es bestätigen.

Um Spalten zu entfernen, klicken Sie auf die Tabelle, zu der die Spalte gehört. Markieren Sie die Spalten, die Sie entfernen möchten, und klicken Sie auf die Schaltfläche ![button\_1.png](../../assets/button_1.png).

Um eine synchronisierte Tabelle zu entfernen, wählen Sie alle Spalten in der Tabelle aus und klicken Sie erneut auf die ![Schaltfläche](../../assets/button_1.png). Dadurch werden alle nativen und berechneten Spalten, die diese Tabelle verwenden, von Ihrem Data Warehouse entfernt.

### Bestätigen von Änderungen

Unabhängig davon, ob Sie eine Tabelle ablegen oder Spalten entfernen, wird eine Abhängigkeitsprüfung ausgeführt, bevor der Löschvorgang abgeschlossen ist. Abhängigkeiten sind berechnete Spalten, Metriken, Filtersätze und Berichte, die die zu entfernende Tabelle oder Spalte(n) verwenden. Alle erkannten Abhängigkeiten werden angezeigt. An dieser Stelle können Sie den Vorgang entweder abbrechen oder auf **[!UICONTROL Confirm Changes]** klicken, um die Tabelle abzulegen oder die Spalte(n) zu entfernen.

Gelöschte Abhängigkeiten können zwar nicht wiederhergestellt werden, aber die Tabellen und Spalten sind weiterhin verfügbar, wenn Sie in Zukunft native Spalten neu synchronisieren müssen.

Im Folgenden finden Sie einen kurzen Überblick über das Entfernen einer Spalte:

![Entfernen einer Spalte aus Ihrem Data Warehouse](../../assets/DW_delete.gif)

## Wann kann ich meine neuen Spalten verwenden? {#when}

Neue synchronisierte Spalten und neue/aktualisierte berechnete Spalten sind nach Abschluss der nächsten vollständigen Aktualisierung einsatzbereit. Wenn noch keine Aktualisierung in Bearbeitung ist, können Sie eine Aktualisierung erzwingen, indem Sie oben auf der `Data Warehouse`- oder `Integrations` auf **[!UICONTROL Force update]** klicken. Sie können auch eine E-Mail-Benachrichtigung nach Abschluss der Aktualisierung planen, indem Sie auf **[!UICONTROL Email me when complete]** klicken.

Wenn Sie bereit sind, Ihre neuen Spalten in Berichten zu verwenden [müssen Sie sie zuerst zu Metriken hinzufügen](../data-warehouse-mgr/manage-data-dimensions-metrics.md). Obwohl Daten erst nach Abschluss einer Aktualisierung verfügbar sind, können Sie in Berichten dennoch neue Spalten verwenden. Daten innerhalb des Berichts werden angezeigt, wenn die Aktualisierung abgeschlossen ist.

## Verpackung

Dieser Artikel behandelt eine Menge Material. Mittlerweile sollten Sie ein solides Verständnis davon haben, was eine Datenbank ist, wie Daten organisiert sind, wie Tabellen miteinander in Beziehung stehen und was Sie mit dem Data Warehouse-Manager tun können.

Testen Sie Ihr Wissen, indem Sie [eine berechnete Spalte erstellen](../data-warehouse-mgr/creating-calculated-columns.md) oder [einige interessante Berichte erstellen](../../tutorials/using-visual-report-builder.md).
