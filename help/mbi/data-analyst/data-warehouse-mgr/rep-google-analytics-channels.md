---
title: Replizieren von Google Analytics-Kanälen mithilfe von Akquisequellen
description: Erfahren Sie, wie Sie Google Analytics-Kanäle mithilfe von Akquise-Quellen replizieren.
exl-id: e7248fe4-94db-4cdf-8f58-1f65061a207d
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Google Analytics, die Akquise-Quellen verwenden

## Was sind Kanäle? {#channels}

Erstellen benutzerdefinierter Segmente, um zu sehen, wie sich der unterschiedliche Traffic entwickelt, und Trends zu beobachten (zum Guten oder zum Schlechten). ist eine der leistungsstärksten Anwendungen für  [!DNL Google Analytics ]. Eine Klasse von Segmenten, die standardmäßig in [!DNL Google Analytics ] are `Channels`. Kanäle sind eine Gruppierung der gängigen Wege, wie Besucher zu Ihrer Site gelangen.  [!DNL Google Analytics ] sortiert automatisch die vielen Möglichkeiten, einen Benutzer zu gewinnen - egal ob es sich um Social Media, Pay-per-Click, E-Mail oder Verweislinks handelt - und fasst ihn in einem Behälter oder Kanal zusammen.

## Warum sehe ich meine `channels` in MBI? {#nochannels}

`Channels` sind einfache, aggregierte Datenbehälter. Um Ihre Akquisen in Channel-Buckets zu sortieren, legt Google mithilfe bestimmter Parameter unterschiedliche Regeln und Definitionen fest: eine Kombination aus Akquisition [Quelle](https://support.google.com/analytics/answer/1033173?hl=en) (die Herkunft Ihres Traffics) und die Akquise [Mittel](https://support.google.com/analytics/answer/6099206?hl=en) (allgemeine Kategorie der Quelle).

Diese Behälter können Ihnen dabei helfen, festzustellen, woher Ihr Traffic stammt. Diese Daten werden jedoch nicht nach Kanal getaggt, sondern durch eine Kombination aus Quelle und Medium. Da Google Kanalinformationen als zwei separate Datenpunkte sendet, werden Kanalgruppierungen nicht automatisch in [!DNL MBI].

## Was sind die standardmäßigen Kanalgruppierungen? Wie werden sie erstellt?

Google bietet standardmäßig acht Kanäle. Sehen wir uns die Regeln an, die bestimmen, wie sie erstellt werden:

| Kanal | Was ist es? | Wie wird es erstellt? |
|---|---|---|
| Direkt | Jeder, der direkt auf Ihre Site gelangt. | Quelle = `Direct`<br>AND Medium = `(not set); OR Medium = (none)` |
| Organische Suche | Traffic, der organisch in unbezahlten Suchmaschinen eingestuft wurde. | Medium = `organic` |
| Verweis | Traffic, der von einem externen Link stammt, der nicht &quot;Kostenlose Suche&quot;ist, oder von Websites, bei denen es sich nicht um soziale Netzwerke handelt. | Medium = `referral` |
| Gebührenpflichtige Suche | Traffic mit einem UTM-Trackingcode, bei dem das Medium entweder &quot;cpc&quot;, &quot;ppc&quot;oder &quot;paidsearch&quot;ist UND ein Anzeigenverteilungsnetzwerk ist, das nicht mit &quot;Content&quot;übereinstimmt. | Medium = `^(cpc|ppc|paidsearch)$`<br>UND-Anzeigenverteilungs-Netzwerk `Content` |
| Social | Verweisverkehr, der aus einem beliebigen [400 soziale Netzwerke](https://www.annielytics.com/blog/analytics/sites-google-analytics-includes-in-social-reports/) und werden nicht als Anzeigen getaggt. | Social Source-Verweis = `Yes`<br>ODER Medium = `^(social|social-network|social-media|sm|social network|social media)$` |
| Email | Traffic aus Sitzungen, die mit dem Medium &quot;E-Mail&quot;getaggt sind. | UTM-Trackingcode von Medium = `email` |
| Anzeige | Traffic mit einem UTM-Trackingcode, bei dem das Medium entweder &quot;display&quot;oder &quot;cpm&quot;ist. Enthält auch AdWords-Interaktionen, bei denen das Werbenetzwerk mit &quot;Inhalt&quot;übereinstimmt | Medium = `^(display|cpm|banner)$`<br>ODER Ad Distribution Network = `Content`<br>AND Ad Format ≠ `Text` |
| Sonstiges | Sitzungen von anderen Werbekanälen, ausgenommen gebührenpflichtige Suche, die mit dem Medium &quot;cpc&quot;, &quot;ppc&quot;, &quot;cpm, &quot;cpv&quot;, &quot;cpa&quot;, &quot;cpp&quot;, &quot;Affiliate&quot; getaggt sind. | Medium = `^(cpv|cpa|cpp|content-text)$` |

{style=&quot;table-layout:auto&quot;}

## Wie kann ich diese Kanalgruppierungen in meiner Data Warehouse neu erstellen? {#recreate}

Da Sie wissen, dass Kanäle nur eine Kombination aus Quellen und Medien sind, ist es einfach, diese Gruppierungen in Ihrer Data Warehouse in drei Schritten neu zu erstellen.

1. **Aktivieren Sie Ihre[!DNL Google ECommerce]Integration**

   [Einmal aktiviert](../importing-data/integrations/google-ecommerce.md), stellen Sie sicher, dass [Synchronisieren](.../{{ site.baseurl }}/data-analyst/data-warehouse-mgr/tour-dwm.html#syncing) die **medium** und **source** -Felder in Ihrer Data Warehouse. Nach Abschluss werden Medium- und Quellakquisedaten in Ihre Data Warehouse übertragen.

1. **Hochladen einer Zuordnung der Kanalgruppierungen von Google**

   Um Zeit zu sparen, hat Commerce bereits eine Tabelle mit den Standardgruppierungen erstellt, die als Datei zugeordnet sind und die Sie [herunterladen](../../assets/ga-channel-mapping.csv).

   Wenn Sie Google Analytics sind und eigene Kanäle erstellt haben, sollten Sie Ihre spezifischen Regeln zur Zuordnungstabelle hinzufügen, bevor Sie die Datei in hochladen [!DNL MBI].

   Einbinden in Ihre Data Warehouse als [Datei-Upload](../importing-data/connecting-data/using-file-uploader.md).

   ![](../../assets/Setting_Primary_Keys.png)

1. **Beziehung herstellen zwischen[!DNL Google ECommerce]und Mappings-Datei-Upload**

   So erstellen Sie eine Beziehung zwischen[!DNL Google ECommerce]und der Zuordnungstabelle, [Support-Anfrage senden](../../guide-overview.md) an unser Data Analyst-Team weiterleiten und diesen Artikel lesen. Der Analyst erstellt eine neue berechnete Spalte mit dem Namen **Kanal** in der EG-Commerce-Tabelle. **Nach einem vollständigen Aktualisierungszyklus**, kann diese Spalte in einem Filter oder einer Gruppe nach verwendet werden.

Herzlichen Glückwunsch! Jetzt befinden sich in Ihrer Data Warehouse Google Analytics-Kanalgruppierungen, sodass Sie Ihre Daten aus einer neuen Perspektive analysieren können:

![Segmentieren der Metrik Anzahl Bestellungen nach Kanal](../../assets/GA_Channel_Gif.gif)

In diesem Beispiel haben wir mit der einfachen Segmentierung der **Anzahl Bestellungen** Metrik nach **Kanal**. Jetzt sind Sie an der Reihe - testen Sie Ihre neue Spalte und sehen Sie, welche Trends Sie in Ihren Google Analytics-Kanaldaten identifizieren können!

## Verwandte Dokumentation

* [Verwenden des Report Builders](../../tutorials/using-visual-report-builder.md)
* [Erwartet[!DNL Google ECommerce]data](../importing-data/integrations/google-ecommerce-data.md)
* [Erstellen[!DNL Google ECommerce]Dimensionen mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
* [Welche Akquisequellen und -kanäle sind Ihre wertvollsten?](../analysis/most-value-source-channel.md)
