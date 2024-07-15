---
title: Filtersätze für Metriken erstellen
description: Erfahren Sie, wie Sie gespeicherte Filtersätze erstellen und auf die Metriken anwenden.
exl-id: 6ef8b67c-bebd-45eb-bca7-95832ec34fc8
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Erstellen von Filtersätzen

Wenn Sie mehrere Metriken in [!DNL Commerce Intelligence] haben, die auf ähnliche Weise gefiltert werden müssen (z. B. Testreihenfolge herausfiltern), können Sie gespeicherte Filtersätze erstellen und diese auf die Metriken anwenden. So sparen Sie Zeit, da Sie beim Erstellen oder Bearbeiten einer Metrik keine individuellen Filter hinzufügen müssen.

Weitere Informationen finden Sie im [Schulungsvideo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-filter-sets.html) .

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

1. Klicken Sie in der Seitenleiste auf &quot;**[!DNL Manage Data** > **Filter Sets]**&quot;.

   ![](../../assets/create-filter-sets.png)

1. Klicken Sie oben auf der Seite auf **[!UICONTROL Add Filter Set]** .

1. Wählen Sie die Tabelle aus, die die Metriken enthält, die Sie filtern möchten.

   Wenn Sie beispielsweise Ihre `Total number of orders` -Metrik filtern möchten und sie auf der `orders` -Tabelle basiert, wählen Sie diese Tabelle aus.

1. Nennen Sie die &quot;`Filter Set`&quot;.

1. Fügen Sie alle relevanten Filter hinzu.

   Wenn Sie beispielsweise nur Bestellungen mit dem Status &quot;complete&quot;in Ihre `Total number of orders` -Metrik aufnehmen möchten, wenden Sie einen Filter an, der alle Bestellungen ohne Status = `complete` ausschließt.

1. Überprüfen Sie Ihre Filterlogik und stellen Sie sicher, dass Klammern und Operatoren richtig platziert sind, z. B. `\[A\] AND \[B\]; (\[A\] OR \[B\]) AND \[C\]`.

   Ein falscher Filter ist häufig die Ursache für Datendiskrepanzen zwischen [!DNL Commerce Intelligence] Berichten und Ihren erwarteten Ergebnissen.

1. Speichern Sie die `Filter Set`.

Nachdem ein Filtersatz gespeichert wurde, können Sie ihn auf jede Metrik anwenden, die dieselbe Tabelle verwendet. Wenn Sie beispielsweise eine `Filter Set` für die Tabelle `orders` erstellt haben, können Sie sie auf *alle auf dieser Tabelle erstellten Metriken* anwenden, z. B. `Revenue`.

>[!NOTE]
>
>`Filter Sets` kann auch auf berechnete Spalten in [!DNL Commerce Intelligence] angewendet werden. Wenden Sie sich an den Support, um einen Filtersatz auf eine in [!DNL Commerce Intelligence] erstellte Datendimension anzuwenden.

## Verwandte

* [Best Practices für Segmentierung und Filterung](../../best-practices/segment-filter.md)
