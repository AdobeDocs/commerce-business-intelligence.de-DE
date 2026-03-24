---
title: Verwenden der berechneten Spalte „Datumsdifferenz“
description: Erfahren Sie mehr über den Zweck und die Verwendung der Spalte „Datumsdifferenz berechnet“.
exl-id: 6ecab794-3466-4b3a-a929-3e56287522aa
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/5SElfBoU6vqCNthFdj96eCNH26dC54ucjqknnhQXQy8
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
source-wordcount: 272
ht-degree: 0%

---

# Berechnete Spalte „Datumsdifferenz“

In diesem Thema werden der Zweck und die Verwendung der `Date Difference` berechneten Spalte auf der **[!DNL Manage Data > Data Warehouse]** Seite beschrieben. Nachfolgend finden Sie eine Erläuterung der Funktionen, gefolgt von einem Beispiel und den Methoden zu seiner Erstellung.

**Erläuterung**

Der `Date Difference` Spaltentyp berechnet die Zeit zwischen zwei Ereignissen, die zu einem einzelnen Datensatz gehören, basierend auf den Ereignis-Zeitstempeln. Der in dieser Spalte berechnete Rohwert beträgt in Sekunden, er wird jedoch automatisch in Minuten, Stunden, Tage usw. konvertiert, um ihn in Berichten anzuzeigen. Bei Verwendung als Filter/Gruppieren nach sollte der Wert jedoch in Sekunden verwendet werden.

Eine `date difference` berechnete Spalte kann verwendet werden, um eine Metrik zu erstellen, die die durchschnittliche oder mediane Zeit zwischen zwei Ereignissen berechnet, z. B. die durchschnittliche Zeit zwischen der Kundenregistrierung und ihren ersten Bestellungen.

**Beispiel**

| **`id`** | **`timestamp_1`** | **`timestamp_2`** | **`Seconds between timestamp_2 and timestamp_1`** |
|--- |--- |--- |--- |
| `A` | 01.01.2015 00:00:00 | 01.01.2015 12:30:00 | 45000 |
| `B` | 01.01.2015 08:00:00 | 01.01.2015 10:00:00 | 7200 |

{style="table-layout:auto"}


Im obigen Beispiel ist die Spalte `Date Difference` die Spalte `Seconds between timestamp_2 and timestamp_1` . Er führt die `timestamp_2 minus timestamp_1` durch.

**Mechanik**

Die folgenden Schritte beschreiben, wie Sie eine `Date Difference` erstellen.

1. Navigieren Sie zur **[!DNL Manage Data > Data Warehouse]**.
1. Navigieren Sie zu der Tabelle, in der Sie diese Spalte erstellen möchten.
1. Klicken Sie auf **[!UICONTROL Create a Column]** und konfigurieren Sie Ihre Spalte wie folgt:
   * Wählen Sie `Column Definition Type` > `Same Table`
   * Wählen Sie `Column Definition Equation` > `DATE_DIFF = (Ending DATETIME - Starting DATETIME)`
   * Wählen Sie `Ending DATETIME` Spalte aus und wählen Sie das Feld Enddatum und -uhrzeit aus, was normalerweise das Ereignis ist, das später auftritt
   * Wählen Sie `Starting DATETIME` Spalte ** > Wählen Sie das Feld Anfangsdatum/Uhrzeit , das normalerweise das früher auftretende Ereignis ist

1. Geben Sie der Spalte einen Namen und klicken Sie auf **[!UICONTROL Save]**.
1. Die Spalte kann (sofort *verwendet*.

Als Beispiel wird das folgende Beispiel konfiguriert, um die `Seconds between order date and customer's creation date` zu berechnen:

![Konfiguration zur Berechnung der Datumsdifferenz mit Spaltenauswahl „Datum/Uhrzeit“](../../assets/date_diff.png)
