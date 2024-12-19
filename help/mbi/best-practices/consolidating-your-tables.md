---
title: Konsolidieren von Tabellen
description: Erfahren Sie, wie Sie Ihre Tabellen und Datenbanken konsolidieren.
exl-id: 6065bed3-fb84-4147-a223-92dc3e1b15a5
role: Admin, User
feature: Commerce Tables, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Konsolidieren von Tabellen

Wenn Sie mehrere Storefronts oder in mehreren Märkten betreiben, können ähnliche Datenbanken separat gespeichert werden. In [!DNL Adobe Commerce Intelligence] ist es einfach, ähnliche Tabellen aus verschiedenen Datenbanken zusammenzufassen.

Sie können beispielsweise eine `orders` für `Market A` und eine ähnliche `orders` für `Market B` haben. [!DNL Commerce Intelligence] können beide Tabellen konsolidieren und die aggregierten Auftragsdaten sowohl aus `Market A` als auch aus `B` anzeigen sowie sie nach bestimmten Märkten segmentieren.

Damit die Konsolidierung von Tabellen funktioniert, müssen die Eingabetabellen (**strukturiert)**. Mit anderen Worten: Alle Eingabetabellen müssen die in der konsolidierten Tabelle erforderlichen Datenspalten enthalten.

In diesem Abschnitt werden einige der häufigsten Anwendungsfälle für konsolidierte Tabellen sowie die nächsten Schritte, die zum Erstellen eigener Tabellen erforderlich sind, erläutert.

## Recommendations für die Verwendung konsolidierter Tabellen

Im Folgenden wird erläutert, wann die Verwendung konsolidierter Tabellen in Ihrem System sinnvoll sein könnte.

### Integrieren von Daten aus mehreren Websites

Wenn Sie Ihre Produkte unter verschiedenen Marken und Websites verkaufen, sind die Tabellen für jede Marke oder Website wahrscheinlich ähnlich strukturiert.

Sie können beispielsweise eine `orders` für Website-`A` und eine separate, aber ähnliche `orders` für Website-`B` haben. In diesem Fall kann es nützlich sein, die `orders` von Website-`A` und -`B` zu konsolidieren. Auf diese Weise können Sie sich den konsolidierten Umsatz und die Anzahl der Bestellungen von Website-`A` und -`B` ansehen und die Metriken nach diesen beiden Websites segmentieren.

### Integrieren von veralteten Daten

Viele Unternehmen haben ihre Datenbanken zu einem bestimmten Zeitpunkt umgestaltet, und die Daten aus der alten Datenbank werden nicht immer in das neue System konvertiert. Sie können konsolidierte Tabellen verwenden, um die Schlüsselspalten aus den alten Tabellen mit denen aus dem aktiven System zu verbinden. Auf diese Weise können Sie Ihre Daten während des gesamten Verlaufs einheitlich analysieren.

### Kombinieren von Ereignissen für die Analyse aktiver Benutzer

Stellen Sie sich eine Website vor, auf der Benutzer verschiedene Dinge tun können: eine Umfrage durchführen, ein Spiel spielen, einen Kauf tätigen, einen Freund weiterempfehlen usw. Normalerweise wird jedes dieser Ereignisse in einer eigenen Tabelle gespeichert. Dadurch ist es schwierig, zu analysieren, wie viele verschiedene Benutzende in einem bestimmten Zeitraum mindestens eine Aktion irgendeiner Art durchgeführt haben.

Sie können konsolidierte Tabellen verwenden, um eine einheitliche Liste aller Benutzer zu erstellen und festzustellen, wann eines dieser Ereignisse stattgefunden hat. Sie können dann Abfragen für die konsolidierte Tabelle ausführen, um eine solche Analyse einfach durchzuführen.

Wie bei allen anderen Tabellen in Ihrem Data Warehouse können Sie zusätzliche Spalten hinzufügen, um verschiedene Arten von Diagrammen und Analysen zu ermöglichen.

## Erstellen, Anzeigen oder Aktualisieren einer konsolidierten Tabelle

Wenn Sie eine konsolidierte Tabelle zu Ihrem Data Warehouse hinzufügen möchten, wenden Sie sich an [!DNL Commerce Intelligence] [Support](../guide-overview.md#Submitting-a-Support-Ticket).

>[!NOTE]
>
>Da konsolidierte Tabellen in der `Data Warehouse Manager` nicht angezeigt werden können, kann das Anzeigen und Aktualisieren dieser Tabellen nur über [!DNL Commerce Intelligence] Unterstützung erfolgen.
