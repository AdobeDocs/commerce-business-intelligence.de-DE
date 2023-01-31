---
title: Berechnete Spalten erstellen
description: Erfahren Sie, wie Sie Daten aus verschiedenen Quellen zusammenführen.
exl-id: 668cbc77-6a96-4687-9f40-3635b1be5c66
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Berechnete Spalten erstellen

Bei der Analyse Ihrer Daten ist es von Vorteil, Daten aus verschiedenen Quellen zu konsolidieren. Möchten Sie den Umsatz nach Akquisequelle gruppieren und Daten aus Ihrer Auftragstabelle und Ihren Google Analytics verknüpfen? Oder wie wäre es mit der Gruppierung des Umsatzes nach Kundengeschlecht oder der Verknüpfung eines Kundenattributs zu Transaktionsdaten zur Segmentierung?

In diesem Handbuch lernen Sie, wie man genau das macht. Bevor Sie beginnen, empfehlen wir Ihnen, die [Handbuch zu berechneten Spaltentypen](../../data-analyst/data-warehouse-mgr/calc-column-types.md). Die _Handbuch zu berechneten Spaltentypen_ skizziert die Spaltentypen, die Sie im Data Warehousen-Manager erstellen können, sowie ihre Definitionen und Beispiele.

1. Um zu beginnen, klicken Sie auf **[!DNL Manage Data > Data Warehouse]** in der Seitenleiste.

1. Klicken Sie auf die Tabelle, in der Sie eine Spalte erstellen möchten. Wenn wir beispielsweise eine `Customer Gender` -Spalte für die Umsatzsegmentierung wählen wir die `sales_flat_order` Tabelle.

1. Das Tabellenschema wird angezeigt. Klicken **[!UICONTROL Create New Column]**.

1. Geben Sie der Spalte einen Namen - z. B. `Customer Gender`.

1. Wählen Sie die Definition für die Spalte aus. Hier ist die [Handbuch zu berechneten Spaltentypen](../data-warehouse-mgr/calc-column-types.md) wird praktisch sein!

1. Für bestimmte Spaltentypen sind etwas mehr Informationen erforderlich, um die Spalte korrekt zu erstellen:
   * Für `One to Many` (verbunden) und `Many to One` Spalten (Aggregat) auswählen, müssen die Tabellen und Spalten ausgewählt werden.
   * Für `Same Table calculation`müssen Sie das gewünschte Datumsfeld aus der Dropdown-Liste auswählen.

Wenn Sie eine `One to Many` (verbunden) oder `Many to One` (aggregierte) Spalte, müssen Sie einen Pfad auswählen, um die beiden Tabellen zu verbinden. In diesem Schritt können Sie entweder einen vorhandenen Pfad verwenden oder einen neuen erstellen.

>[!NOTE]
>
>Denken Sie daran, die Tabelle ordnungsgemäß als viele oder eine Tabelle zu definieren!

* Bei Bedarf können Sie [Filter](../../data-user/reports/ess-manage-data-filters.md) in die neue Spalte ein.
* Klicken Sie abschließend auf **[!UICONTROL Save]**.

Das ist es! Ihre neue Spalte wird in der aktuellen Tabelle mit einer `Pending` Status. Nach Abschluss der nächsten Aktualisierung ist Ihre Spalte für die Verwendung in Metriken und Berichten verfügbar.

## Praktische Referenzzuordnung {#map}

Wenn Sie bei der Erstellung einer berechneten Spalte ein wenig Schwierigkeiten dabei haben, sich zu merken, was alle Eingaben enthalten, sollten Sie diese Referenzkarte beim Erstellen verwenden:

![](../../assets/Calculated_Columns_Example.png)

## Verwandte Dokumentation

* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md)
* [Erweiterte berechnete Spaltentypen](../data-warehouse-mgr/adv-calc-columns.md)
* [Erstellen [!DNL Google ECommerce] Dimensionen mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
