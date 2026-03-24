---
title: Erstellen eines Dashboards für Investoren
description: Erfahren Sie, wie Sie ein Dashboard für Investoren erstellen.
exl-id: 917e7628-3498-4413-a7e1-61799989a7dd
role: Admin, Developer, User
feature: Dashboards, Data Integration
TQID: https://experienceleague.adobe.com/0G3u84SK-CvA7Pvb5bI-uEkUkbi9oiYvWwJHRwd-568
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
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
source-wordcount: 289
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

Mit den [Commerce Data Enrichment-Services](https://business.adobe.com/de/products/magento/magento-commerce.html) können Sie Berichte zu folgenden Themen einbeziehen:

* Unique Customers nach Bundesland/Region, Alter, Geschlecht.

## Weitere Tipps

* Verwenden Sie eine klare und knappe [Namenskonvention](../best-practices/naming-elements.md)
* Freigeben des Dashboards für Investoren
* Oder senden Sie es über **[!UICONTROL Automated email summary]**(../data-user/export-data/email-summaries.md)
* Nur ein Dashboard erstellen. Dies erleichtert die Pflege des Inhalts und Sie wissen genau, was Ihre Investoren anschauen.

Organisieren Sie Ihre Berichte sorgfältig und achten Sie auf Details. Nach Abschluss des Vorgangs sieht das Dashboard wie folgt aus:

![Build Investor Dashboard](../../mbi/assets/investor-dboard-example.png)
