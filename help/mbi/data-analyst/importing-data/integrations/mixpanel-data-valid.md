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

Wenn [!DNL Adobe Commerce Intelligence] zum ersten Mal eine Verbindung zu Ihren [!DNL Mixpanel] -Daten herstellt, kann Ihr Kundenbetreuer oder Analyst anfordern, Datenexporte aus [!DNL Mixpanel] zu Überprüfungszwecken bereitzustellen. Auf diese Weise können Sie überprüfen, ob Sie alle Daten synchronisiert haben, die Ihnen direkt in [!DNL Mixpanel] zur Verfügung stehen.

## Datenexport-Prozess: `Events`

1. Besuchen Sie Ihren Abschnitt `Segmentation` und zeigen Sie `Your Top Events` an.

   ![](../../../assets/your-top-events.png)

1. Wählen Sie `Past 96 Hours` für den Zeitraum aus

   ![](../../../assets/past-96-hours.png)

1. Scrollen Sie zum unteren rechten Teil des Berichts und exportieren Sie eine `.csv` -Datei:

   ![](../../../assets/export-csv-mixpanel.png)

1. Senden Sie die Datei &quot;`.csv`&quot;an den Kundenbetreuer oder -analyst, mit dem Sie diesen Validierungsprozess durchführen.
