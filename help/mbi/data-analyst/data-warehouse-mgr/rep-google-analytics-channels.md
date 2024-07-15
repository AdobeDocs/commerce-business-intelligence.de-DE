---
title: Replizieren von Google Analytics-Kanälen mithilfe von Akquisequellen
description: Erfahren Sie, wie Sie Google Analytics-Kanäle mithilfe von Akquisequellen replizieren.
exl-id: e7248fe4-94db-4cdf-8f58-1f65061a207d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# [!DNL Google Analytics] mit Akquise-Quellen

## Was sind Kanäle? {#channels}

Das Erstellen benutzerdefinierter Segmente, um zu sehen, wie unterschiedliche Traffic-Aufrufe funktionieren und Trends beobachten, ist eine der leistungsstärksten Verwendungen für [!DNL Google Analytics]. Eine Klasse von Segmenten, die standardmäßig in [!DNL Google Analytics] vorhanden sind, ist `Channels`. Kanäle sind eine Gruppierung der gängigen Wege, wie Besucher zu Ihrer Site gelangen.  [!DNL Google Analytics] sortiert automatisch die vielen Möglichkeiten, einen Benutzer zu gewinnen - egal ob es sich um Social Media, Pay-per-Click, E-Mail oder Verweislinks handelt - und fasst ihn in einem Behälter oder Kanal zusammen.

## Warum wird meine `channels` nicht in Commerce Intelligence angezeigt? {#nochannels}

`Channels` sind einfache, aggregierte Datenbehälter. Um Ihre Akquise in Kanalbehälter zu sortieren, legt [!DNL Google] mithilfe bestimmter Parameter unterschiedliche Regeln und Definitionen fest: eine Kombination aus Akquise [Source](https://support.google.com/analytics/answer/1033173?hl=en) (Ursprung Ihres Traffics) und Akquise [Medium](https://support.google.com/analytics/answer/6099206?hl=en) (allgemeine Kategorie der Quelle).

Diese Behälter können Ihnen dabei helfen, festzustellen, woher Ihr Traffic stammt. Diese Daten werden jedoch nicht über verschiedene Kanäle, sondern durch eine Kombination aus Source und Medium getaggt. Da [!DNL Google] Kanalinformationen als zwei separate Datenpunkte sendet, werden Kanalgruppierungen nicht automatisch in [!DNL Commerce Intelligence] angezeigt.

## Was sind die standardmäßigen Kanalgruppierungen? Wie werden sie erstellt?

Standardmäßig richtet [!DNL Google] acht verschiedene Kanäle ein. Die Regeln, die bestimmen, wie Kanäle erstellt werden, sind unten aufgeführt.

| **Kanal** | **Was ist das?** | **Wie wird es erstellt?** |
|---|---|---|
| Direkt | Jeder, der direkt auf Ihre Site gelangt. | Source = `Direct`<br>UND Medium = `(not set); OR Medium = (none)` |
| Organische Suche | Traffic, der organisch in unbezahlten Suchmaschinen eingestuft wurde. | Medium = `organic` |
| Verweis | Traffic, der von einem externen Link stammt, der nicht &quot;Kostenlose Suche&quot;ist, oder von Websites, bei denen es sich nicht um soziale Netzwerke handelt. | Medium = `referral` |
| Gebührenpflichtige Suche | Traffic mit einem UTM-Trackingcode, bei dem das Medium entweder &quot;cpc&quot;, &quot;ppc&quot;oder &quot;paidsearch&quot;ist UND ein Anzeigenverteilungsnetzwerk ist, das nicht mit &quot;Content&quot;übereinstimmt. | Medium = `^(cpc|ppc|paidsearch)$`<br>AND Ad Distribution Network ≠ `Content` |
| Social | Verweis-Traffic, der von ungefähr [400 sozialen Netzwerken](https://www.annielytics.com/blog/analytics/sites-google-analytics-includes-in-social-reports/) stammt und nicht als Anzeigen getaggt wird. | Social Source-Verweis = `Yes`<br>ODER Medium = `^(social|social-network|social-media|sm|social network|social media)$` |
| E-Mail | Traffic aus Sitzungen, die mit dem Medium &quot;E-Mail&quot;getaggt sind. | UTM-Trackingcode von Medium = `email` |
| Anzeige | Traffic mit einem UTM-Trackingcode, bei dem das Medium entweder &quot;display&quot;oder &quot;cpm&quot;ist. Enthält auch AdWords-Interaktionen, bei denen das Werbenetzwerk mit &quot;Inhalt&quot;übereinstimmt | Medium = `^(display|cpm|banner)$`<br>ODER Ad Distribution Network = `Content`<br>AND Ad Format ≠ `Text` |
| Sonstiges | Sitzungen von anderen Werbekanälen (ohne gebührenpflichtige Suche), die mit dem Medium &quot;cpc&quot;, &quot;ppc&quot;, &quot;cpm, &quot;cpv&quot;, &quot;cpa&quot;, &quot;cpp&quot;, &quot;Affiliate&quot; getaggt sind. | Medium = `^(cpv|cpa|cpp|content-text)$` |

{style="table-layout:auto"}

## Wie kann ich diese Kanalgruppierungen in meiner Data Warehouse nachstellen? {#recreate}

Da Sie wissen, dass Kanäle nur eine Kombination von Quellen und Medien sind, ist es einfach, diese Gruppierungen in Ihrem Data Warehouse in drei Schritten neu zu erstellen.

1. **Aktivieren Sie Ihre[!DNL Google ECommerce]Integration**

   [Wenn aktiviert](../importing-data/integrations/google-ecommerce.md), stellen Sie sicher, dass Sie die Felder [sync](../{{ site.baseurl }}/data-analyst/data-warehouse-mgr/tour-dwm.html#syncing) in Ihrem Data Warehouse auf die Felder **medium** und **source** synchronisieren. Nach Abschluss werden Medium- und Quellakquisedaten in Ihre Data Warehouse übertragen.

1. **Laden Sie eine Zuordnung der Kanalgruppierungen von Google hoch**

   Adobe Commerce erstellt eine Tabelle mit den Standardgruppierungen, die als Datei zugeordnet sind und die Sie [herunterladen](../../assets/ga-channel-mapping.csv) können.

   Wenn Sie ein [!DNL Google Analytics] -Profi sind und Ihre eigenen Kanäle erstellt haben, möchten Sie Ihre spezifischen Regeln zur Zuordnungstabelle hinzufügen, bevor Sie die Datei in [!DNL Commerce Intelligence] hochladen.

   Bringen Sie es als [Datei-Upload](../importing-data/connecting-data/using-file-uploader.md) in Ihre Data Warehouse.

   ![](../../assets/Setting_Primary_Keys.png)

1. **Einrichten einer Beziehung zwischen [!DNL Google ECommerce] und dem Hochladen der Zuordnungsdatei**

   Um eine Beziehung zwischen [!DNL Google ECommerce] und der Zuordnungstabelle herzustellen, senden [Sie eine Support-Anfrage](../../guide-overview.md#Submitting-a-Support-Ticket) an Ihr Data Analyst-Team und verweisen auf dieses Thema. Der Analyst erstellt eine neue berechnete Spalte namens **Kanal** in der ECCommerce-Tabelle. **Nach einem vollständigen Aktualisierungszyklus** kann diese Spalte in einem `Filter` oder `Group by` verwendet werden.

Sie verfügen nun über [!DNL Google Analytics Channel] -Gruppierungen in Ihrer Data Warehouse, was bedeutet, dass Sie Ihre Daten aus einer neuen Perspektive analysieren können:

![Segmentieren der Metrik &quot;Anzahl Bestellungen&quot;nach Kanal](../../assets/GA_Channel_Gif.gif)

In diesem Beispiel haben Sie mit der Segmentierung der Metrik **Anzahl der Bestellungen** nach **Kanal** begonnen. Testen Sie Ihre neue Spalte und sehen Sie, welche Trends Sie in Ihren [!DNL Google Analytics Channel] -Daten identifizieren können!

## Verwandte Dokumentation

* [Verwenden des Report Builders](../../tutorials/using-visual-report-builder.md)
* [Erwartete[!DNL Google ECommerce]Daten](../importing-data/integrations/google-ecommerce-data.md)
* [Erstellen von[!DNL Google ECommerce]Dimensionen mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
* [Welche Akquisequellen und -kanäle sind Ihre wertvollsten?](../analysis/most-value-source-channel.md)
