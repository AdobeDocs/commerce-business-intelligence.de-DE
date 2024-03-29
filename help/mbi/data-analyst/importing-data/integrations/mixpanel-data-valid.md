---
title: Datenvalidierung in Mixpanel
description: Erfahren Sie, wie Sie bestätigen, dass Sie alle gleichen Daten synchronisiert haben, die Ihnen direkt in Mixpanel zur Verfügung stehen.
exl-id: d18ce954-26fe-4440-ad8b-4f266c007b2f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Datenvalidierung in [!DNL Mixpanel]

Wann [!DNL Adobe Commerce Intelligence] erste Verbindungen zu Ihrer [!DNL Mixpanel] -Daten, kann Ihr Kundenbetreuer oder Analyst anfordern, dass Sie Datenexporte von [!DNL Mixpanel] für Validierungszwecke. Auf diese Weise können Sie bestätigen, dass Sie alle Daten synchronisiert haben, die Ihnen direkt in [!DNL Mixpanel].

## Datenexportprozess: `Events`

1. Besuchen Sie Ihre `Segmentation` Abschnitt und Ansicht `Your Top Events`.

   ![](../../../assets/your-top-events.png)

1. Auswählen `Past 96 Hours` für den Zeitraum

   ![](../../../assets/past-96-hours.png)

1. Scrollen Sie zum unteren rechten Teil des Berichts und exportieren Sie eine `.csv` Datei:

   ![](../../../assets/export-csv-mixpanel.png)

1. Senden Sie die `.csv` -Datei an den Kundenbetreuer oder -analyst weiterleiten, mit dem Sie an diesem Validierungsprozess arbeiten.
