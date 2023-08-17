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

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. Beispiel: in einer `orders` Tabelle gibt es möglicherweise eine Spalte namens `status`. Wenn eine Bestellung ursprünglich in die Datenbank geschrieben wurde, kann die Statusspalte den Wert enthalten _pending_. Die Bestellung wird in Ihrer [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) mit diesem `pending` -Wert.

Der Bestellstatus kann sich ändern, ist jedoch nicht immer in einer `pending` -Status. Letztlich könnte es `complete` oder `cancelled`. Um sicherzustellen, dass Ihre Data Warehouse diese Änderung synchronisiert, muss die Spalte auf neue Werte überprüft werden.

Wie passt dies in die [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md) darüber diskutiert wurde? Die Verarbeitung der Überprüfungen variiert je nach ausgewählter Replikationsmethode. Die `Modified\_At` Die Replikationsmethode eignet sich am besten für die Verarbeitung von sich ändernden Werten, da keine erneuten Überprüfungen konfiguriert werden müssen. Die `Auto-Incrementing Primary Key` und `Primary Key Batch Monitoring` -Methoden müssen erneut konfiguriert werden.

Bei Verwendung einer dieser Methoden müssen veränderliche Spalten zur erneuten Überprüfung gekennzeichnet werden. Hierfür gibt es drei Möglichkeiten:

1. Ein Auditing-Prozess, der als Teil der Aktualisierungsmarkierungen ausgeführt wird und erneut überprüft werden soll.

   >[!NOTE]
   >
   >Der Prüfer stützt sich auf ein Probenahmeverfahren, und die sich ändernden Spalten dürfen nicht sofort erfasst werden.

1. Sie können sie selbst festlegen, indem Sie das Kontrollkästchen neben der Spalte im Data Warehouse-Manager aktivieren und auf **[!UICONTROL Set Recheck Frequency]** und wählen Sie ein passendes Zeitintervall für den Zeitpunkt aus, zu dem Sie nach Änderungen suchen sollten.

1. Ein Mitglied der [!DNL Adobe Commerce Intelligence] Das Data Warehouse-Team kann die Spalten manuell markieren, um sie erneut in Ihrem Data Warehouse zu überprüfen. Wenn Sie über veränderliche Spalten informiert sind, wenden Sie sich an das Team, um anzufordern, dass die Überprüfungen durchgeführt werden. Fügen Sie Ihrer Anforderung eine Liste von Spalten sowie die Häufigkeit bei.

## Recherche-Frequenzen {#frequency}

**Wusstest du das?**
Setzen einer erneuten Überprüfung auf eine `primary key` überprüft die Spalte nicht auf geänderte Werte. Die Tabelle wird auf gelöschte Zeilen überprüft und alle Löschungen werden aus der Data Warehouse gelöscht.

Wenn eine Spalte zur erneuten Überprüfung markiert wird, können Sie auch festlegen, wie oft ein erneutes Überprüfen auftritt. Wenn sich eine bestimmte Spalte nicht häufig ändert, kann die Auswahl einer weniger häufigen Wiederholung [den Aktualisierungszyklus optimieren](../../best-practices/reduce-update-cycle-time.md).

Häufigkeitsoptionen sind:

* `always` - Wiederholung bei jeder Aktualisierung
* `daily` - das erste Update nach Mitternacht für Ihre deklarierte Zeitzone durchgeführt wird
* `weekly` - Das erneute Aktivieren erfolgt nach 21 Uhr Freitagupdate jede Woche für Ihre deklarierte Zeitzone
* `monthly` - Das erneute Aktivieren erfolgt nach 21 Uhr Freitagsaktualisierungen alle vier Wochen für Ihre deklarierte Zeitzone
* `once` - tritt nur bei der nächsten Aktualisierung auf (einmalige Aktualisierung)

Da die Aktualisierungszeiten mit der zu synchronisierenden Datenmenge korrelieren, empfiehlt Adobe, eine `daily`, `weekly`oder `monthly` anstelle jedes Updates erneut überprüfen.

## Verwaltung der Kontrollfrequenzen {#manage}

Über die Data Warehouse können die Frequenzen erneut verwaltet werden, indem Sie auf einen Tabellennamen klicken und die einzelnen Spalten überprüfen. Der Synchronisierungsstatus und die Häufigkeit der erneuten Überprüfung (die **Änderungen?** Spalte) für jede Spalte in der Tabelle angezeigt.

Um die Häufigkeit der erneuten Überprüfungen zu ändern, aktivieren Sie das Kontrollkästchen neben den Spalten, die Sie ändern möchten. Klicken Sie anschließend auf **[!UICONTROL Set Recheck Frequency]** und legen Sie die gewünschte Häufigkeit fest.

![](../../assets/dwm-recheck.png)

Manchmal wird `Paused` im `Changes?` Spalte. Dieser Wert wird angezeigt, wenn die [Replikationsmethode](../../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) auf `Paused`.

[!DNL Adobe] empfiehlt, diese Spalten zu überprüfen, um sowohl Ihre Aktualisierungen zu optimieren als auch sicherzustellen, dass veränderliche Spalten erneut überprüft werden. Wenn die Wiederholungshäufigkeit für eine Spalte angesichts der Häufigkeit der Datenänderungen hoch ist, empfiehlt Adobe, sie zu reduzieren, um Ihre Aktualisierungen zu optimieren.

Kontaktieren Sie uns bei Fragen oder um aktuelle Replikationsmethoden oder Nachprüfungen zu erhalten.

**Verwandte:**

* [Verkürzen der Aktualisierungszeiten](../../best-practices/reduce-update-cycle-time.md)
* [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md)
