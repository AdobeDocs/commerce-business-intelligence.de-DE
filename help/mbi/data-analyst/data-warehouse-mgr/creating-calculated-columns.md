---
title: Berechnete Spalten erstellen
description: Erfahren Sie, wie Sie Daten aus verschiedenen Quellen zusammenführen.
exl-id: 668cbc77-6a96-4687-9f40-3635b1be5c66
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/dGzhox6Xjuvc3goSxkF2W-5yBlkgKgnOJg7YcuD2Q0s
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 345
ht-degree: 0%

---

# Berechnete Spalten erstellen

Bei der Analyse Ihrer Daten ist es hilfreich, Daten aus verschiedenen Quellen zu konsolidieren. Möchten Sie den Umsatz nach Akquise-Quelle gruppieren, die Daten aus Ihrer `orders`-Tabelle verknüpfen und Daten [!DNL Google Analytics]? Vielleicht möchten Sie den Umsatz nach Kundengeschlecht gruppieren oder einem Kundenattribut Transaktionsdaten für die Segmentierung hinzufügen. In diesem Thema wird erläutert, wie Sie genau dies tun können.

Bevor Sie beginnen, empfiehlt Adobe, das [Handbuch für berechnete Spaltentypen](../../data-analyst/data-warehouse-mgr/calc-column-types.md) zu lesen, um Informationen über die Spaltentypen zu erhalten, die Sie in Data Warehouse Manager erstellen können, einschließlich der Definitionen und Beispiele.

1. Um zu beginnen, klicken Sie auf **[!DNL Manage Data > Data Warehouse]**.

1. Klicken Sie auf die Tabelle, in der Sie eine Spalte erstellen möchten. Wenn Sie beispielsweise eine `Customer Gender` Spalte für die Umsatzsegmentierung erstellen möchten, wählen Sie die Tabelle `sales_flat_order` aus.

1. Das Tabellenschema wird angezeigt. Klicken Sie auf **[!UICONTROL Create New Column]**.

1. Geben Sie der Spalte einen Namen. Beispiel: `Customer Gender`.

1. Wählen Sie die Definition für die Spalte aus. Hier ist die [Anleitung für berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md) praktisch!

1. Bei bestimmten Spaltentypen sind etwas mehr Informationen erforderlich, um die Spalte ordnungsgemäß zu erstellen:

   * Für `One to Many` (verbundene) und `Many to One` (aggregierte) Spalten müssen Sie die Tabellen und Spalten auswählen.

   * Für einen `Same Table calculation` müssen Sie das gewünschte Datumsfeld aus der Dropdown-Liste auswählen.

Wenn Sie eine `One to Many` (verbundene) oder `Many to One` (aggregierte) Spalte erstellen, müssen Sie einen Pfad auswählen, um die beiden Tabellen zu verbinden. In diesem Schritt können Sie entweder einen vorhandenen Pfad verwenden oder einen erstellen.

>[!NOTE]
>
>Denken Sie daran, die Tabelle richtig als viele oder eine zu definieren!

* Bei Bedarf können Sie [Filter](../../data-user/reports/ess-manage-data-filters.md) auf die neue Spalte anwenden.

* Klicken Sie abschließend auf **[!UICONTROL Save]**.

Ihre neue Spalte wird in der aktuellen Tabelle mit dem Status `Pending` angezeigt. Nach Abschluss der nächsten Aktualisierung ist Ihre Spalte für die Verwendung in Metriken und Berichten verfügbar.

## Praktische Referenzkarte {#map}

Wenn Sie beim Erstellen einer berechneten Spalte Schwierigkeiten haben, sich an alle Eingaben zu erinnern, versuchen Sie, diese Referenzzuordnung beim Erstellen von praktisch zu halten:

![Beispielkonfiguration für berechnete Spalten in Data Warehouse Manager](../../assets/Calculated_Columns_Example.png)

## Verwandte Dokumentation

* [Berechnete Spaltentypen](../data-warehouse-mgr/calc-column-types.md)
* [Erweiterte berechnete Spaltentypen](../data-warehouse-mgr/adv-calc-columns.md)
* [&#x200B; [!DNL Google ECommerce]  mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
