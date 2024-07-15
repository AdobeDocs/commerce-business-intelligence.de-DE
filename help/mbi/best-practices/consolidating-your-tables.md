---
title: Tabellen zusammenfassen
description: Erfahren Sie, wie Sie Ihre Tabellen und Datenbanken konsolidieren.
exl-id: 6065bed3-fb84-4147-a223-92dc3e1b15a5
role: Admin, User
feature: Commerce Tables, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Tabellen zusammenfassen

Wenn Sie mehrere Storefronts oder mehrere Märkte betreiben, können ähnliche Datenbanken separat gespeichert werden. In [!DNL Adobe Commerce Intelligence] ist es einfach, ähnliche Tabellen aus verschiedenen Datenbanken zusammenzufassen.

Sie können beispielsweise eine `orders` Tabelle für `Market A` und eine ähnliche `orders` Tabelle für `Market B` haben. [!DNL Commerce Intelligence] kann beide Tabellen konsolidieren und Ihnen erlauben, die aggregierten Bestelldaten sowohl aus `Market A` als auch aus `B` anzuzeigen, und zwar zusätzlich zur Segmentierung nach spezifischen Märkten.

Damit die Konsolidierung von Tabellen funktioniert, müssen Eingabetabellen **ähnlich strukturiert** sein. Anders ausgedrückt: Alle Eingabetabellen müssen die in der konsolidierten Tabelle erforderlichen Datenspalten enthalten.

In diesem Thema werden einige der häufigsten Anwendungsfälle für konsolidierte Tabellen und die nächsten Schritte erläutert, die für die Erstellung eigener Tabellen erforderlich sind.

## Recommendations für die Verwendung konsolidierter Tabellen

Im Folgenden wird erläutert, wann es sinnvoll sein könnte, konsolidierte Tabellen in Ihrem System zu verwenden.

### Integrieren von Daten aus mehreren Websites

Wenn Sie Ihre Produkte unter verschiedenen Marken und Websites verkaufen, sind die Tabellen für jede Marke oder Website wahrscheinlich ähnlich strukturiert.

Sie können beispielsweise eine `orders` Tabelle für Website `A` und eine separate, aber ähnliche `orders` Tabelle für Website `B` haben. In diesem Fall kann es nützlich sein, die `orders` -Tabellen von der Website `A` und `B` zu konsolidieren. Auf diese Weise können Sie sich den konsolidierten Umsatz und die Anzahl der Bestellungen von der Website `A` und `B` ansehen und außerdem Metriken nach diesen beiden Websites segmentieren.

### Integrieren älterer Daten

Viele Unternehmen haben ihre Datenbanken an der einen oder anderen Stelle umstrukturiert, und die Daten aus der alten Datenbank werden nicht immer in das neue System konvertiert. Sie können konsolidierte Tabellen verwenden, um die Schlüsselspalten aus älteren Tabellen mit denen aus dem aktiven System zu verbinden. Auf diese Weise können Sie Ihre Daten im Verlauf einer einheitlichen Analyse unterziehen.

### Kombinieren von Ereignissen für die Analyse aktiver Benutzer

Stellen Sie sich eine Website vor, auf der Benutzer mehrere Dinge tun können: Umfragen durchführen, ein Spiel spielen, einen Kauf tätigen, Freunde kennenlernen usw. Normalerweise wird jedes dieser Ereignisse in einer eigenen Tabelle gespeichert. Dies erschwert die Durchführung einer Analyse, wie viele verschiedene Benutzer in einem bestimmten Zeitraum mindestens eine Aktion irgendeiner Art ergriffen haben.

Sie können konsolidierte Tabellen verwenden, um eine einheitliche Liste aller Benutzer und wann eines dieser Ereignisse stattgefunden hat. Sie können dann Abfragen auf die konsolidierte Tabelle ausführen, um eine solche Analyse einfach durchzuführen.

Wie bei allen anderen Tabellen in Ihrer Data Warehouse können Sie zusätzliche Spalten hinzufügen, um verschiedene Arten von Diagrammen und Analysen zu ermöglichen.

## Erstellen, Anzeigen oder Aktualisieren einer konsolidierten Tabelle

Wenn Sie eine konsolidierte Tabelle zu Ihrer Data Warehouse hinzufügen möchten, wenden Sie sich an [!DNL Commerce Intelligence] [support](../guide-overview.md#Submitting-a-Support-Ticket).

>[!NOTE]
>
>Da konsolidierte Tabellen nicht im `Data Warehouse Manager` angezeigt werden können, können diese Tabellen nur durch die Unterstützung von [!DNL Commerce Intelligence] angezeigt und aktualisiert werden.
