---
title: Konfigurieren von Datenprüfungen
description: Erfahren Sie, wie Sie Datenspalten mit veränderlichen Werten konfigurieren.
exl-id: c31ef32e-ba5a-4902-b632-fbab551cc632
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# Konfigurieren von Datenprüfungen

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. In einer `orders` -Tabelle kann es beispielsweise eine Spalte mit dem Namen `status` geben. Wenn eine Bestellung anfänglich in die Datenbank geschrieben wird, kann die Statusspalte den Wert _pending_ enthalten. Die Reihenfolge wird in Ihrem [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) mit diesem `pending` -Wert repliziert.

Der Bestellstatus kann sich ändern, obwohl sie sich nicht immer im Status `pending` befinden. Letztlich könnte es `complete` oder `cancelled` werden. Um sicherzustellen, dass Ihre Data Warehouse diese Änderung synchronisiert, muss die Spalte auf neue Werte überprüft werden.

Wie passt dies zu den besprochenen [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md)? Die Verarbeitung der Überprüfungen variiert je nach ausgewählter Replikationsmethode. Die Replikationsmethode `Modified\_At` eignet sich am besten für die Verarbeitung von sich ändernden Werten, da keine erneuten Überprüfungen konfiguriert werden müssen. Die Methoden `Auto-Incrementing Primary Key` und `Primary Key Batch Monitoring` müssen erneut konfiguriert werden.

Bei Verwendung einer dieser Methoden müssen veränderliche Spalten zur erneuten Überprüfung gekennzeichnet werden. Hierfür gibt es drei Möglichkeiten:

1. Ein Auditing-Prozess, der als Teil der Aktualisierungsmarkierungen ausgeführt wird und erneut überprüft werden soll.

   >[!NOTE]
   >
   >Der Prüfer stützt sich auf ein Probenahmeverfahren, und die sich ändernden Spalten dürfen nicht sofort erfasst werden.

1. Sie können sie selbst festlegen, indem Sie im Data Warehouse-Manager das Kontrollkästchen neben der Spalte aktivieren, auf **[!UICONTROL Set Recheck Frequency]** klicken und ein entsprechendes Zeitintervall auswählen, in dem Sie nach Änderungen suchen sollen.

1. Ein Mitglied des [!DNL Adobe Commerce Intelligence]-Data Warehouse-Teams kann die Spalten manuell markieren, um sie erneut auf Ihrem Data Warehouse zu überprüfen. Wenn Sie über veränderliche Spalten informiert sind, wenden Sie sich an das Team, um anzufordern, dass die Überprüfungen durchgeführt werden. Fügen Sie Ihrer Anforderung eine Liste von Spalten sowie die Häufigkeit bei.

## Recherche-Frequenzen {#frequency}

**Wusstest du das?**
Wenn Sie eine erneute Überprüfung auf eine `primary key` -Spalte einstellen, wird die Spalte nicht auf geänderte Werte überprüft. Die Tabelle wird auf gelöschte Zeilen überprüft und alle Löschungen werden aus der Data Warehouse gelöscht.

Wenn eine Spalte zur erneuten Überprüfung markiert wird, können Sie auch festlegen, wie oft ein erneutes Überprüfen auftritt. Wenn sich eine bestimmte Spalte nicht häufig ändert, kann die Auswahl eines weniger häufigen Wiederholungsvorgangs [Ihren Aktualisierungszyklus optimieren](../../best-practices/reduce-update-cycle-time.md).

Häufigkeitsoptionen sind:

* `always` - Während jeder Aktualisierung wird erneut überprüft.
* `daily` - Erneutes Überprüfen tritt nach Mitternacht für Ihre deklarierte Zeitzone auf
* `weekly` - Überprüfung findet nach 21:00 Uhr Freitags-Update jede Woche für Ihre deklarierte Zeitzone statt
* `monthly` - Überprüfung findet nach 21:00 Uhr Freitagsupdate alle vier Wochen für Ihre deklarierte Zeitzone statt
* `once` - Tritt nur bei der nächsten Aktualisierung auf (einmalige Aktualisierung)

Da die Aktualisierungszeiten mit der zu synchronisierenden Datenmenge korrelieren, empfiehlt Adobe, anstelle jedes Updates eine erneute Überprüfung von `daily`, `weekly` oder `monthly` zu wählen.

## Verwaltung der Kontrollfrequenzen {#manage}

Über die Data Warehouse können die Frequenzen erneut verwaltet werden, indem Sie auf einen Tabellennamen klicken und die einzelnen Spalten überprüfen. Der Synchronisierungsstatus und die Häufigkeit der erneuten Überprüfung (die **ändert sich?** Spalte) für jede Spalte in der Tabelle angezeigt.

Um die Häufigkeit der erneuten Überprüfungen zu ändern, aktivieren Sie das Kontrollkästchen neben den Spalten, die Sie ändern möchten. Klicken Sie dann auf das Dropdown-Menü **[!UICONTROL Set Recheck Frequency]** und legen Sie die gewünschte Häufigkeit fest.

![](../../assets/dwm-recheck.png)

Manchmal wird in der Spalte `Changes?` `Paused` angezeigt. Dieser Wert wird angezeigt, wenn die [Replikationsmethode](../../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) der Tabelle auf `Paused` gesetzt ist.

[!DNL Adobe] empfiehlt, diese Spalten zu überprüfen, um sowohl Ihre Aktualisierungen zu optimieren als auch sicherzustellen, dass veränderliche Spalten erneut überprüft werden. Wenn die Wiederholungshäufigkeit für eine Spalte angesichts der Häufigkeit der Datenänderungen hoch ist, empfiehlt Adobe, sie zu reduzieren, um Ihre Aktualisierungen zu optimieren.

Kontaktieren Sie uns bei Fragen oder um aktuelle Replikationsmethoden oder Nachprüfungen zu erhalten.

**Related:**

* [Verkürzen der Aktualisierungszeiten](../../best-practices/reduce-update-cycle-time.md)
* [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md)
