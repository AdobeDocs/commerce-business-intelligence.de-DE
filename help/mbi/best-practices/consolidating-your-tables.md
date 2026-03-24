---
title: Konsolidieren von Tabellen
description: Erfahren Sie, wie Sie Ihre Tabellen und Datenbanken konsolidieren.
exl-id: 6065bed3-fb84-4147-a223-92dc3e1b15a5
role: Admin, User
feature: Commerce Tables, Data Integration
TQID: https://experienceleague.adobe.com/HC5REx483htdfFigZPxcrZeD5byyJKk-beQqnEARt1E
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 469
ht-degree: 0%

---

# Konsolidieren von Tabellen

Wenn Sie mehrere Storefronts oder in mehreren Märkten betreiben, können ähnliche Datenbanken separat gespeichert werden. In [!DNL Adobe Commerce Intelligence] ist es einfach, ähnliche Tabellen aus verschiedenen Datenbanken zusammenzufassen.

Sie können beispielsweise eine `orders` für `Market A` und eine ähnliche `orders` für `Market B` haben. [!DNL Commerce Intelligence] können beide Tabellen konsolidieren und die aggregierten Auftragsdaten sowohl aus `Market A` als auch aus `B` anzeigen sowie sie nach bestimmten Märkten segmentieren.

Damit die Konsolidierung von Tabellen funktioniert, müssen die Eingabetabellen (**strukturiert)**. Mit anderen Worten: Alle Eingabetabellen müssen die in der konsolidierten Tabelle erforderlichen Datenspalten enthalten.

In diesem Abschnitt werden einige der häufigsten Anwendungsfälle für konsolidierte Tabellen sowie die nächsten Schritte, die zum Erstellen eigener Tabellen erforderlich sind, erläutert.

## Empfehlungen für die Verwendung konsolidierter Tabellen

Im Folgenden wird erläutert, wann die Verwendung konsolidierter Tabellen in Ihrem System sinnvoll sein könnte.

### Integrieren von Daten aus mehreren Websites

Wenn Sie Ihre Produkte unter verschiedenen Marken und Websites verkaufen, sind die Tabellen für jede Marke oder Website wahrscheinlich ähnlich strukturiert.

Sie können beispielsweise eine `orders` für Website-`A` und eine separate, aber ähnliche `orders` für Website-`B` haben. In diesem Fall kann es nützlich sein, die `orders` von Website-`A` und -`B` zu konsolidieren. Auf diese Weise können Sie sich den konsolidierten Umsatz und die Anzahl der Bestellungen von Website-`A` und -`B` ansehen und die Metriken nach diesen beiden Websites segmentieren.

### Integrieren von veralteten Daten

Viele Unternehmen haben ihre Datenbanken zu einem bestimmten Zeitpunkt umgestaltet, und die Daten aus der alten Datenbank werden nicht immer in das neue System konvertiert. Sie können konsolidierte Tabellen verwenden, um die Schlüsselspalten aus den alten Tabellen mit denen aus dem aktiven System zu verbinden. Auf diese Weise können Sie Ihre Daten während des gesamten Verlaufs einheitlich analysieren.

### Kombinieren von Ereignissen für die Analyse aktiver Benutzer

Stellen Sie sich eine Website vor, auf der Benutzer verschiedene Dinge tun können: eine Umfrage durchführen, ein Spiel spielen, einen Kauf tätigen, einen Freund weiterempfehlen usw. Normalerweise wird jedes dieser Ereignisse in einer eigenen Tabelle gespeichert. Dadurch ist es schwierig, zu analysieren, wie viele verschiedene Benutzende in einem bestimmten Zeitraum mindestens eine Aktion irgendeiner Art durchgeführt haben.

Sie können konsolidierte Tabellen verwenden, um eine einheitliche Liste aller Benutzer zu erstellen und festzustellen, wann eines dieser Ereignisse stattgefunden hat. Sie können dann Abfragen für die konsolidierte Tabelle ausführen, um eine solche Analyse einfach durchzuführen.

Wie bei allen anderen Tabellen in Ihrer Data Warehouse können Sie zusätzliche Spalten hinzufügen, um verschiedene Arten von Diagrammen und Analysen zu ermöglichen.

## Erstellen, Anzeigen oder Aktualisieren einer konsolidierten Tabelle

Wenn Sie eine konsolidierte Tabelle zu Ihrer Data Warehouse hinzufügen möchten, wenden Sie sich an den [!DNL Commerce Intelligence] [Support](../guide-overview.md#Submitting-a-Support-Ticket).

>[!NOTE]
>
>Da konsolidierte Tabellen in der `Data Warehouse Manager` nicht angezeigt werden können, kann das Anzeigen und Aktualisieren dieser Tabellen nur über [!DNL Commerce Intelligence] Unterstützung erfolgen.
