---
title: Berechnete Spalten erstellen
description: Erfahren Sie, wie Sie Daten aus verschiedenen Quellen zusammenführen.
exl-id: 668cbc77-6a96-4687-9f40-3635b1be5c66
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Berechnete Spalten erstellen

Bei der Analyse Ihrer Daten ist es hilfreich, Daten aus verschiedenen Quellen zu bündeln. Möchten Sie den Umsatz nach Akquisequelle gruppieren und die Daten aus Ihrer `orders` Tabelle und Ihren [!DNL Google Analytics] Daten verknüpfen? Vielleicht möchten Sie den Umsatz nach Kundengeschlecht gruppieren oder ein Kundenattribut zu Transaktionsdaten für die Segmentierung hinzufügen. In diesem Thema wird erläutert, wie man genau das macht.

Bevor Sie beginnen, empfiehlt Adobe, dass Sie das [Handbuch zu berechneten Spaltentypen](../../data-analyst/data-warehouse-mgr/calc-column-types.md) lesen, um Informationen zu den Spaltentypen zu erhalten, die Sie im Data Warehouse-Manager erstellen können, sowie deren Definitionen und Beispiele.

1. Klicken Sie zunächst auf **[!DNL Manage Data > Data Warehouse]**.

1. Klicken Sie auf die Tabelle, in der Sie eine Spalte erstellen möchten. Wenn Sie z. B. eine `Customer Gender` -Spalte für die Umsatzsegmentierung erstellen möchten, wählen Sie die `sales_flat_order` -Tabelle aus.

1. Das Tabellenschema wird angezeigt. Klicken Sie auf **[!UICONTROL Create New Column]**.

1. Geben Sie Ihrer Spalte einen Namen. Beispiel: `Customer Gender`.

1. Wählen Sie die Spaltendefinition aus. Hier ist der Leitfaden [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md) praktisch!

1. Für bestimmte Spaltentypen sind etwas mehr Informationen erforderlich, um die Spalte korrekt zu erstellen:

   * Für die Spalten `One to Many` (zusammengefügt) und `Many to One` (Aggregat) müssen Sie die Tabellen und Spalten auswählen.

   * Für einen `Same Table calculation` müssen Sie das gewünschte Datumsfeld aus der Dropdown-Liste auswählen.

Wenn Sie eine Spalte vom Typ &quot;`One to Many`&quot;(verbunden) oder &quot;`Many to One`&quot;(Aggregat) erstellen, müssen Sie einen Pfad auswählen, um die beiden Tabellen zu verbinden. In diesem Schritt können Sie entweder einen vorhandenen Pfad verwenden oder einen Pfad erstellen.

>[!NOTE]
>
>Denken Sie daran, die Tabelle ordnungsgemäß als viele oder eine Tabelle zu definieren!

* Bei Bedarf können Sie [Filter](../../data-user/reports/ess-manage-data-filters.md) auf die neue Spalte anwenden.

* Klicken Sie abschließend auf **[!UICONTROL Save]**.

Ihre neue Spalte wird in der aktuellen Tabelle mit dem Status `Pending` angezeigt. Nach Abschluss der nächsten Aktualisierung ist Ihre Spalte für die Verwendung in Metriken und Berichten verfügbar.

## Praktische Referenzzuordnung {#map}

Wenn Sie beim Erstellen einer berechneten Spalte Schwierigkeiten haben, sich zu merken, was alle Eingaben enthalten, versuchen Sie, diese Referenzkarte beim Erstellen hilfreich zu halten:

![](../../assets/Calculated_Columns_Example.png)

## Verwandte Dokumentation

* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md)
* [Erweiterte berechnete Spaltentypen](../data-warehouse-mgr/adv-calc-columns.md)
* [Erstellen von [!DNL Google ECommerce] Dimensionen mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
