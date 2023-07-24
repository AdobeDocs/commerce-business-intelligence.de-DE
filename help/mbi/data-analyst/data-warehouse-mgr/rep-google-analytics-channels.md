---
title: Replizieren von Google Analytics-Kanälen mithilfe von Akquisequellen
description: Erfahren Sie, wie Sie Google Analytics-Kanäle mithilfe von Akquise-Quellen replizieren.
exl-id: e7248fe4-94db-4cdf-8f58-1f65061a207d
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# [!DNL Google Analytics] mithilfe von Akquise-Quellen

## Was sind Kanäle? {#channels}

Das Erstellen benutzerdefinierter Segmente, um zu sehen, wie unterschiedliche Traffic-Aufrufe funktionieren und Trends beobachten, ist eine der leistungsstärksten Anwendungen für [!DNL Google Analytics]. Eine Klasse von Segmenten, die standardmäßig in [!DNL Google Analytics] are `Channels`. Kanäle sind eine Gruppierung der gängigen Wege, wie Besucher zu Ihrer Site gelangen.  [!DNL Google Analytics] sortiert automatisch die vielen Möglichkeiten, einen Benutzer zu gewinnen - egal ob es sich um Social Media, Pay-per-Click, E-Mail oder Verweislinks handelt - und fasst ihn in einem Behälter oder Kanal zusammen.

## Warum sehe ich meine `channels` in Commerce Intelligence? {#nochannels}

`Channels` sind einfache, aggregierte Datenbehälter. So sortieren Sie Ihre Akquisen in Kanalbehälter: [!DNL Google] legt mithilfe spezifischer Parameter unterschiedliche Regeln und Definitionen fest: eine Kombination aus Akquisition [Quelle](https://support.google.com/analytics/answer/1033173?hl=en) (die Herkunft Ihres Traffics) und die Akquise [Mittel](https://support.google.com/analytics/answer/6099206?hl=en) (allgemeine Kategorie der Quelle).

Diese Behälter können Ihnen dabei helfen, den Ursprung Ihres Traffics zu ermitteln. Diese Daten werden jedoch nicht nach Kanal, sondern durch eine Kombination aus Quelle und Medium getaggt. weil [!DNL Google] Sendet Kanalinformationen als zwei separate Datenpunkte, werden Kanalgruppierungen nicht automatisch in [!DNL Commerce Intelligence].

## Was sind die standardmäßigen Kanalgruppierungen? Wie werden sie erstellt?

Standardmäßig [!DNL Google] richtet acht verschiedene Kanäle ein. Die Regeln, die bestimmen, wie Kanäle erstellt werden, sind unten aufgeführt.

| **Kanal** | **Was ist es?** | **Wie wird es erstellt?** |
|---|---|---|
| Direkt | Jeder, der direkt auf Ihre Site gelangt. | Quelle = `Direct`<br>AND Medium = `(not set); OR Medium = (none)` |
| Organische Suche | Traffic, der organisch in unbezahlten Suchmaschinen eingestuft wurde. | Medium = `organic` |
| Verweis | Traffic, der von einem externen Link stammt, der nicht &quot;Kostenlose Suche&quot;ist, oder von Websites, bei denen es sich nicht um soziale Netzwerke handelt. | Medium = `referral` |
| Gebührenpflichtige Suche | Traffic mit einem UTM-Trackingcode, bei dem das Medium entweder &quot;cpc&quot;, &quot;ppc&quot;oder &quot;paidsearch&quot;ist UND ein Anzeigenverteilungsnetzwerk ist, das nicht mit &quot;Content&quot;übereinstimmt. | Medium = `^(cpc|ppc|paidsearch)$`<br>UND-Anzeigenverteilungs-Netzwerk `Content` |
| Social | Verweisverkehr, der aus einem beliebigen [400 soziale Netzwerke](https://www.annielytics.com/blog/analytics/sites-google-analytics-includes-in-social-reports/) und werden nicht als Anzeigen getaggt. | Social Source-Verweis = `Yes`<br>ODER Medium = `^(social|social-network|social-media|sm|social network|social media)$` |
| Email | Traffic aus Sitzungen, die mit dem Medium &quot;E-Mail&quot;getaggt sind. | UTM-Trackingcode von Medium = `email` |
| Anzeige | Traffic mit einem UTM-Trackingcode, bei dem das Medium entweder &quot;display&quot;oder &quot;cpm&quot;ist. Enthält auch AdWords-Interaktionen, bei denen das Werbenetzwerk mit &quot;Inhalt&quot;übereinstimmt | Medium = `^(display|cpm|banner)$`<br>ODER Ad Distribution Network = `Content`<br>AND Ad Format ≠ `Text` |
| Sonstiges | Sitzungen von anderen Werbekanälen (ohne gebührenpflichtige Suche), die mit dem Medium &quot;cpc&quot;, &quot;ppc&quot;, &quot;cpm, &quot;cpv&quot;, &quot;cpa&quot;, &quot;cpp&quot;, &quot;Affiliate&quot; getaggt sind. | Medium = `^(cpv|cpa|cpp|content-text)$` |

{style="table-layout:auto"}

## Wie kann ich diese Kanalgruppierungen in meiner Data Warehouse neu erstellen? {#recreate}

Da Sie wissen, dass Kanäle nur eine Kombination aus Quellen und Medien sind, ist es einfach, diese Gruppierungen in Ihrer Data Warehouse in drei Schritten neu zu erstellen.

1. **Aktivieren Sie Ihre[!DNL Google ECommerce]Integration**

   [Bei Aktivierung](../importing-data/integrations/google-ecommerce.md), stellen Sie sicher, dass [Synchronisieren](.../{{ site.baseurl }}/data-analyst/data-warehouse-mgr/tour-dwm.html#syncing) die **medium** und **source** -Felder in Ihrer Data Warehouse. Nach Abschluss werden Medium- und Quellakquisedaten in Ihre Data Warehouse übertragen.

1. **Hochladen einer Zuordnung der Kanalgruppierungen von Google**

   Adobe Commerce erstellt eine Tabelle mit den Standardgruppierungen, die als Datei zugeordnet sind und die Sie [herunterladen](../../assets/ga-channel-mapping.csv).

   Wenn Sie [!DNL Google Analytics] Pro und Ihre eigenen Kanäle erstellt haben, möchten Sie Ihre spezifischen Regeln zur Zuordnungstabelle hinzufügen, bevor Sie die Datei in hochladen. [!DNL Commerce Intelligence].

   Einbinden in Ihre Data Warehouse als [Datei-Upload](../importing-data/connecting-data/using-file-uploader.md).

   ![](../../assets/Setting_Primary_Keys.png)

1. **Beziehung herstellen zwischen[!DNL Google ECommerce]und Mappings-Datei-Upload**

   So erstellen Sie eine Beziehung zwischen[!DNL Google ECommerce] und der Zuordnungstabelle, [Support-Anfrage senden](../../guide-overview.md#Submitting-a-Support-Ticket) an Ihr Data Analyst-Team weiterleiten und auf dieses Thema verweisen. Der Analyst erstellt eine neue berechnete Spalte mit dem Namen **Kanal** in der EG-Commerce-Tabelle. **Nach einem vollständigen Aktualisierungszyklus**, kann diese Spalte in einer `Filter` oder `Group by`.

Sie haben jetzt [!DNL Google Analytics Channel] -Gruppierungen in Ihrer Data Warehouse verwenden, sodass Sie Ihre Daten aus einer neuen Perspektive analysieren können:

![Segmentieren der Metrik Anzahl Bestellungen nach Kanal](../../assets/GA_Channel_Gif.gif)

In diesem Beispiel haben Sie mit der Segmentierung der **Anzahl Bestellungen** Metrik nach **Kanal**. Testen Sie Ihre neue Spalte und sehen Sie, welche Trends Sie in Ihrer [!DNL Google Analytics Channel] data!

## Verwandte Dokumentation

* [Verwenden des Report Builders](../../tutorials/using-visual-report-builder.md)
* [Erwartet[!DNL Google ECommerce]data](../importing-data/integrations/google-ecommerce-data.md)
* [Erstellen[!DNL Google ECommerce]Dimensionen mit Bestell- und Kundendaten](../data-warehouse-mgr/bldg-google-ecomm-dim.md)
* [Welche Akquisequellen und -kanäle sind Ihre wertvollsten?](../analysis/most-value-source-channel.md)
