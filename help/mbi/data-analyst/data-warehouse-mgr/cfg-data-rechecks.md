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

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. Beispielsweise könnte es in einer `orders` eine Spalte namens `status` geben. Wenn eine Bestellung erstmals in die Datenbank geschrieben wird, kann die Spalte Status den Wert _Ausstehend_ enthalten. Die Bestellung wird auf Ihrer [Data Warehouse](../data-warehouse-mgr/tour-dwm.md) mit diesem `pending` Wert repliziert.

Der Bestellstatus kann sich ändern, obwohl er nicht immer den Status &quot;`pending`&quot; aufweist. Irgendwann könnte es `complete` oder `cancelled` werden. Um sicherzustellen, dass der Data Warehouse diese Änderung synchronisiert, muss die Spalte erneut auf neue Werte geprüft werden.

Wie passt dies zu den besprochenen [Replikationsmethoden](../data-warehouse-mgr/cfg-replication-methods.md)? Die Verarbeitung der erneuten Prüfungen hängt von der gewählten Replikationsmethode ab. Die `Modified\_At` Replikationsmethode ist die beste Wahl für die Verarbeitung von sich ändernden Werten, da erneute Prüfungen nicht konfiguriert werden müssen. Die `Auto-Incrementing Primary Key`- und `Primary Key Batch Monitoring`-Methoden erfordern eine erneute Überprüfung der Konfiguration.

Bei Verwendung einer dieser Methoden müssen veränderbare Spalten für eine erneute Überprüfung markiert werden. Dazu gibt es drei Möglichkeiten:

1. Ein Auditing-Prozess, der als Teil der Aktualisierungs-Flags ausgeführt wird, die erneut überprüft werden sollen.

   >[!NOTE]
   >
   >Der Prüfer stützt sich auf ein Stichprobenverfahren, und die wechselnden Spalten werden möglicherweise nicht sofort erfasst.

1. Sie können sie selbst festlegen, indem Sie das Kontrollkästchen neben der Spalte im Data Warehouse-Manager aktivieren, auf **[!UICONTROL Set Recheck Frequency]** klicken und ein geeignetes Zeitintervall auswählen, in dem Sie auf Änderungen prüfen sollten.

1. Ein Mitglied des [!DNL Adobe Commerce Intelligence] Data Warehouse-Teams kann die Spalten manuell zum erneuten Überprüfen in Ihrem Data Warehouse markieren. Wenn Sie sich veränderlicher Spalten bewusst sind, wenden Sie sich an das -Team, um das Setzen von erneuten Prüfungen anzufordern. Fügen Sie Ihrer Anfrage eine Liste der Spalten mit der Häufigkeit hinzu.

## Frequenzen erneut überprüfen {#frequency}

**Wussten Sie schon?**
Wenn Sie für eine `primary key` Spalte eine erneute Überprüfung festlegen, wird die Spalte nicht auf geänderte Werte geprüft. Die Tabelle wird auf gelöschte Zeilen überprüft, und alle Löschvorgänge werden von der Data Warehouse bereinigt.

Wenn eine Spalte für eine erneute Überprüfung gekennzeichnet ist, können Sie auch festlegen, wie oft eine erneute Überprüfung erfolgt. Wenn sich eine bestimmte Spalte nicht oft ändert, kann die Auswahl einer weniger häufigen erneuten Überprüfung [den Aktualisierungszyklus optimieren](../../best-practices/reduce-update-cycle-time.md).

Die Häufigkeitsoptionen sind:

* `always` - Bei jeder Aktualisierung wird eine erneute Prüfung durchgeführt
* `daily` - Die erneute Prüfung erfolgt zum ersten Mal nach Mitternacht für die angegebene Zeitzone
* `weekly` - Die erneute Prüfung findet jede Woche nach 21:00 Uhr für die angegebene Zeitzone statt
* `monthly` - Die erneute Prüfung findet alle vier Wochen nach 21 Uhr statt und wird für die angegebene Zeitzone aktualisiert
* `once` - Tritt nur bei der nächsten Aktualisierung auf (eine einmalige Aktualisierung)

Da die Aktualisierungszeiten davon abhängen, wie viele Daten synchronisiert werden müssen, empfiehlt Adobe, anstelle jeder Aktualisierung eine `daily`, `weekly` oder `monthly` zu wählen.

## Verwalten der Häufigkeit der erneuten Prüfungen {#manage}

Die Häufigkeit der erneuten Prüfungen kann im Data Warehouse durch Klicken auf einen Tabellennamen und anschließendes Überprüfen der einzelnen Spalten verwaltet werden. Der Synchronisationsstatus und die Häufigkeit der erneuten Prüfung (**Änderungen?** Spalte) wird für jede Spalte in der Tabelle angezeigt.

Um die Häufigkeit der erneuten Prüfungen zu ändern, aktivieren Sie das Kontrollkästchen neben den Spalten, die Sie ändern möchten. Klicken Sie dann auf das Dropdown-Menü **[!UICONTROL Set Recheck Frequency]** und legen Sie die gewünschte Häufigkeit fest.

![](../../assets/dwm-recheck.png)

Manchmal werden `Paused` in der `Changes?` Spalte angezeigt. Dieser Wert wird angezeigt, wenn die [Replikationsmethode](../../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) der Tabelle auf `Paused` festgelegt ist.

[!DNL Adobe] empfiehlt, diese Spalten zu überprüfen, um sowohl Ihre Aktualisierungen zu optimieren als auch sicherzustellen, dass veränderbare Spalten erneut überprüft werden. Wenn die Häufigkeit der erneuten Überprüfung für eine Spalte aufgrund der Häufigkeit der Datenänderungen hoch ist, empfiehlt Adobe, sie zu verringern, um Ihre Aktualisierungen zu optimieren.

Wenden Sie sich bei Fragen oder Fragen zu aktuellen Replikationsmethoden oder erneuten Prüfungen an uns.

**Related:**

* [Verkürzung der Aktualisierungszeiten](../../best-practices/reduce-update-cycle-time.md)
* [Datenbank für Analysen optimieren](../../best-practices/opt-db-analysis.md)
