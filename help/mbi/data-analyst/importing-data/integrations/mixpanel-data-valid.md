---
title: Datenvalidierung im Mixpanel
description: Erfahren Sie, wie Sie bestätigen können, dass Sie alle Daten synchronisiert haben, die Ihnen direkt in Mixpanel zur Verfügung stehen.
exl-id: d18ce954-26fe-4440-ad8b-4f266c007b2f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Datenvalidierung in [!DNL Mixpanel]

Wenn [!DNL Adobe Commerce Intelligence] zum ersten Mal eine Verbindung zu Ihren [!DNL Mixpanel] Daten herstellt, kann Ihr Account Manager oder Analyst Sie auffordern, zu Validierungszwecken Datenexporte aus [!DNL Mixpanel] bereitzustellen. Auf diese Weise können Sie bestätigen, dass Sie alle Daten synchronisiert haben, die Ihnen direkt in [!DNL Mixpanel] zur Verfügung stehen.

## Datenexportvorgang: `Events`

1. Besuchen Sie Ihren `Segmentation` Abschnitt und zeigen Sie `Your Top Events` an.

   ![Mixpanel-Dashboard mit Ihren Top-Ereignissen](../../../assets/your-top-events.png)

1. `Past 96 Hours` für den Zeitraum auswählen

   ![Option „Mixpanel-Zeitbereichsauswahl mit Anzeige der letzten 96 Stunden“](../../../assets/past-96-hours.png)

1. Scrollen Sie zum unteren rechten Teil des Berichts und exportieren Sie eine `.csv`:

   ![Option Mixpanel in CSV exportieren im Menü](../../../assets/export-csv-mixpanel.png)

1. Senden Sie die `.csv`-Datei an den Account Manager oder Analyst, mit dem Sie diesen Validierungsprozess durchführen.
