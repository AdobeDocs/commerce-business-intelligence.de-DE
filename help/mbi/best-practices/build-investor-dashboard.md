---
title: Erstellen eines Dashboards für Investoren
description: Erfahren Sie, wie Sie ein Dashboard für Investoren erstellen.
exl-id: 917e7628-3498-4413-a7e1-61799989a7dd
role: Admin, Data Architect, Data Engineer, User
feature: Dashboards, Data Integration
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Investor Dashboard erstellen

Viele Kunden arbeiten mit Investoren zusammen und müssen Informationen über die Plattform austauschen, aber die Dashboards, die Sie für alltägliche Geschäftsentscheidungen erstellen, sind möglicherweise nicht das, was ein Investor sucht. Nachfolgend werden einige Best Practices für die Erstellung eines umfassenden, aber einfachen Dashboards beschrieben, das sich ideal für die Freigabe mit aktiven und potenziellen Investoren eignet.

So erstellen Sie Berichte für Ihr Investor-Dashboard:

## Skalare Berichte

* **[!UICONTROL All-time revenue]**
* **[!UICONTROL Distinct buyers]**
* **[!UICONTROL All-time number of orders]**
* **[!UICONTROL AOV]**
* **[!UICONTROL Items sold]**

## Visuelle Berichte

* **[!UICONTROL Revenue by quarter]**
   * Metrik - Umsatz
* **[!UICONTROL Revenue from 1st time orders vs repeat orders]**
   * Metrik - Erster Bestellumsatz
   * Filter - Die Bestellnummer des Benutzers ist gleich 1
   * Metrik 2 - Umsatz der Wiederholungsaufträge
      * Filter - Die Bestellnummer des Benutzers ist größer als 1
   * Deaktivieren Sie das Kontrollkästchen für Mehrere Y-Achsen
   * Wechseln zu einem gestapelten Säulendiagramm
* **[!UICONTROL AOV by quarter]**
   * Metrik 1 - Umsatz
      * Diese Metrik ausblenden
   * Metrik 2 - Anzahl der Bestellungen
      * Diese Metrik ausblenden
   * Formel - AOV
      * A/B
* **[!UICONTROL All-time revenue by source]**
   * Metrik - Umsatz
   * Nach `utm_source` des Kunden gruppieren
* **[!UICONTROL Revenue from top 10 products]**
   * Metrik - Produktumsatz
      * Diagramm ausblenden
      * Nach Produktnamen gruppieren. Alle Produkte auswählen.
      * Zeitbereich auf „Gesamte Zeit“ einstellen
      * Legen Sie das Zeitintervall auf Keine fest.
      * In „Oben/Unten anzeigen“ nur die 10 obersten sortiert nach Produktgewinn anzeigen
* **[!UICONTROL Cumulative distinct buyers by quarter]**
   * Metrik - Unterschiedliche Käufer
      * Perspektive - Kumulativ
* **[!UICONTROL Site visits - New vs. repeat by month]**
* Sitzungen

Mit einer [!DNL Google Analytics] Integration können Sie Berichte zu folgenden Themen einbeziehen:

* Site-Besuche
* Konversionsrate

Mit den [Commerce Data Enrichment-Services](https://business.adobe.com/products/magento/magento-commerce.html) können Sie Berichte zu folgenden Themen einbeziehen:

* Unique Customers nach Bundesland/Region, Alter, Geschlecht.

## Weitere Tipps

* Verwenden Sie eine klare und knappe [Namenskonvention](../best-practices/naming-elements.md)
* Freigeben des Dashboards für Investoren
* Oder senden Sie es über **[!UICONTROL Automated email summary]**(../data-user/export-data/email-summaries.md)
* Nur ein Dashboard erstellen. Dies erleichtert die Pflege des Inhalts und Sie wissen genau, was Ihre Investoren anschauen.

Organisieren Sie Ihre Berichte sorgfältig und achten Sie auf Details. Nach Abschluss des Vorgangs sieht das Dashboard wie folgt aus:

![](../../mbi/assets/investor-dboard-example.png)
