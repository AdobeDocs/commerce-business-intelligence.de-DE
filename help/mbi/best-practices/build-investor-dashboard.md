---
title: Erstellen eines Dashboards für Anleger
description: Erfahren Sie, wie Sie ein Dashboard für Investoren erstellen.
exl-id: 917e7628-3498-4413-a7e1-61799989a7dd
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Erstellen des Anleger-Dashboards

Viele unserer Kunden arbeiten mit Anlegern zusammen und müssen Informationen aus der Plattform mit ihnen teilen, aber die Dashboards, die Sie für alltägliche Geschäftsentscheidungen erstellen, sind möglicherweise nicht das, wonach ein Investor sucht. Hier werden einige Best Practices für die Erstellung eines Dashboards vorgestellt, das umfassend, aber einfach ist und sich ideal für die gemeinsame Nutzung mit aktiven und potenziellen Investoren eignet.

Im Folgenden finden Sie Informationen zum Erstellen von Berichten für Ihr Investor-Dashboard:

## Skalarberichte

* **[!UICONTROL All-time revenue]**
* **[!UICONTROL Distinct buyers]**
* **[!UICONTROL All-time number of orders]**
* **[!UICONTROL AOV]**
* **[!UICONTROL Items sold]**

## Visuelle Berichte

* **[!UICONTROL Revenue by quarter]**
   * Metrik - Umsatz
* **[!UICONTROL Revenue from 1st time orders vs repeat orders]**
   * Metrik - Umsatz der ersten Bestellung
   * Filter - Die Ordnungsnummer des Benutzers ist gleich 1
   * Metrik 2 - Auftragsumsatz wiederholen
      * Filter - Die Bestellnummer des Benutzers ist größer als 1
   * Deaktivieren Sie das Kontrollkästchen für mehrere Y-Achsen .
   * Ändern in ein gestapeltes Spaltendiagramm
* **[!UICONTROL AOV by quarter]**
   * Metrik 1 - Umsatz
      * Diese Metrik ausblenden
   * Metrik 2 - Anzahl der Bestellungen
      * Diese Metrik ausblenden
   * Formel - AOV
      * A/B
* **[!UICONTROL All-time revenue by source]**
   * Metrik - Umsatz
   * Gruppe nach Kunden `utm_source`
* **[!UICONTROL Revenue from top 10 products]**
   * Metrik - Produktumsatz
      * Diagramm ausblenden
      * Gruppieren nach Produktname. Wählen Sie alle Produkte aus.
      * Legen Sie den Zeitraum auf &quot;All Time&quot;fest
      * Legen Sie das Zeitintervall auf &quot;Ohne&quot;fest.
      * Zeigen Sie in &quot;Oben/Unten anzeigen&quot;nur die 10 Top-Artikel, sortiert nach Produktgewinn
* **[!UICONTROL Cumulative distinct buyers by quarter]**
   * Metrik - Unique Buyer
      * Perspektive - kumulativ
* **[!UICONTROL Site visits - New vs. repeat by month]**
* Sitzungen

Mit [!DNL Google Analytics] -Integration können Sie Berichte zu folgenden Themen einbeziehen:

* Site-Besuche
* Konversionsrate

Mit dem [Commerce-Datenanreicherungsdienste](https://business.adobe.com/products/magento/magento-commerce.html)können Sie Berichte zu folgenden Themen einbeziehen:

* Unique Customers nach Bundesland/Region, Alter, Geschlecht.

## Weitere Tipps

* Verwenden Sie eine klare und knappe [Namenskonvention](../best-practices/naming-elements.md)
* Dashboard für Anleger-Benutzer freigeben
* Oder senden Sie es über **[!UICONTROL Automated email summary]**(../data-user/export-data/email-summaries.md)
* Erstellen Sie nur ein Dashboard. Dies erleichtert die Pflege des Inhalts, und Sie werden genau wissen, was Ihre Investoren sehen.

Organisieren Sie Ihre Berichte sorgfältig und achten Sie auf Details. Nach Abschluss sieht das Dashboard wie folgt aus:

![](../../mbi/assets/investor-dboard-example.png)
