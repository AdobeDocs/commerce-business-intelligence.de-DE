---
title: Filtersätze für Metriken erstellen
description: Erfahren Sie, wie Sie gespeicherte Filtersätze erstellen und auf die Metriken anwenden.
exl-id: 6ef8b67c-bebd-45eb-bca7-95832ec34fc8
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Erstellen von Filtersätzen

Wenn Sie mehrere Metriken in [!DNL MBI] die auf ähnliche Weise gefiltert werden müssen (z. B. um Testaufträge herauszufiltern), können Sie gespeicherte Filtersätze erstellen und auf die Metriken anwenden. So sparen Sie Zeit, da Sie beim Erstellen oder Bearbeiten einer Metrik keine individuellen Filter hinzufügen müssen.

Siehe [Schulungsvideo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-filter-sets.html?lang=en) , um mehr zu erfahren.

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

1. Klicken **[!DNL Manage Data** > **Filter Sets]** in der Seitenleiste.

   ![](../../assets/create-filter-sets.png)

1. Klicken **[!UICONTROL Add Filter Set]** oben auf der Seite.

1. Wählen Sie die Tabelle aus, die die Metriken enthält, die Sie filtern möchten.

   Wenn Sie beispielsweise Ihre `Total number of orders` und basiert auf der `orders` -Tabelle auswählen.

1. Benennen Sie die `Filter Set`.

1. Fügen Sie alle relevanten Filter hinzu.

   Wenn wir beispielsweise nur Bestellungen mit dem Status &quot;complete&quot;in die `Total number of orders` Metrik, würden wir einen Filter anwenden, der alle Bestellungen ausschließt, die nicht über den Status = verfügen. `complete`.

1. Überprüfen Sie die Filterlogik und stellen Sie sicher, dass Klammern und Operatoren richtig platziert sind: Beispiel: `\[A\] AND \[B\]; (\[A\] OR \[B\]) AND \[C\]`.

   Ein falscher Filter ist häufig die Ursache für Datendiskrepanzen zwischen [!DNL MBI] Berichte und die erwarteten Ergebnisse.

1. Speichern Sie die `Filter Set`.

Nachdem ein Filtersatz gespeichert wurde, können Sie ihn auf jede Metrik anwenden, die dieselbe Tabelle verwendet. Wenn Sie beispielsweise eine `Filter Set` auf `orders` -Tabelle können Sie sie auf *beliebige Metriken* auf dieser Tabelle aufbauen, z. B. `Revenue`.

>[!NOTE]
>
>`Filter Sets` kann auch auf berechnete Spalten in [!DNL MBI]. Sie können die Anwendung eines Filtersatzes auf eine Datendimension anfordern, die in [!DNL MBI] über kontaktieren Sie den Support.

## Verwandte

* [Best Practices für Segmentierung und Filterung](../../best-practices/segment-filter.md)
