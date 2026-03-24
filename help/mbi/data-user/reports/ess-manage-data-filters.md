---
title: Erstellen von Filtersätzen für Metriken
description: Erfahren Sie, wie Sie gespeicherte Filtersätze erstellen und auf die Metriken anwenden.
exl-id: 6ef8b67c-bebd-45eb-bca7-95832ec34fc8
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: https://experienceleague.adobe.com/Y3SA-ypB62c0mwZ6uqAOQUyrISc5Tu8yqClrGwXspoU
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 277
ht-degree: 0%

---

# Erstellen von Filtersätzen

Wenn Sie mehrere Metriken in [!DNL Commerce Intelligence] haben, die auf ähnliche Weise gefiltert werden müssen (z. B. Filtern von Testaufträgen), können Sie gespeicherte Filtersätze erstellen und sie auf die Metriken anwenden. Dies spart Ihnen Zeit, da Sie beim Erstellen oder Bearbeiten einer Metrik keine individuellen Filter hinzufügen müssen.

Weitere Informationen finden [ im ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/mbi-training-video-filter-sets.html)Schulungsvideo“.

>[!NOTE]
>
>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

1. Klicken Sie in der Seitenleiste auf **[!DNL Manage Data** > **Filter Sets]** .

   ![Erstellen Sie die Schnittstelle Filtersätze mit der Option Filtersatz hinzufügen](../../assets/create-filter-sets.png)

1. Klicken Sie oben auf der Seite auf **[!UICONTROL Add Filter Set]** .

1. Wählen Sie die Tabelle aus, die die Metriken enthält, die Sie filtern möchten.

   Wenn Sie beispielsweise Ihre `Total number of orders` filtern möchten und sie auf der `orders`-Tabelle aufbaut, wählen Sie diese Tabelle aus.

1. Benennen Sie die `Filter Set`.

1. Alle relevanten Filter hinzufügen.

   Wenn Sie beispielsweise nur Bestellungen mit dem Status „Abgeschlossen“ in Ihrer `Total number of orders` Metrik einbeziehen möchten, wenden Sie einen Filter an, der alle Bestellungen ausschließt, die keinen Status = `complete` haben.

1. Überprüfen Sie Ihre Filterlogik und stellen Sie sicher, dass Klammern und Operatoren korrekt platziert sind: z. B. `\[A\] AND \[B\]; (\[A\] OR \[B\]) AND \[C\]`.

   Ein falscher Filter ist oft die Ursache für Datendiskrepanzen zwischen [!DNL Commerce Intelligence] Berichten und den erwarteten Ergebnissen.

1. Speichern Sie die `Filter Set`.

Nachdem ein Filtersatz gespeichert wurde, können Sie ihn auf jede Metrik anwenden, die dieselbe Tabelle verwendet. Wenn Sie beispielsweise ein `Filter Set` in der `orders`-Tabelle erstellt haben, können Sie es auf *beliebige Metriken) anwenden,* auf dieser Tabelle erstellt wurden, z. B. `Revenue`.

>[!NOTE]
>
>`Filter Sets` können auch auf berechnete Spalten in [!DNL Commerce Intelligence] angewendet werden. Sie können über einen Filtersatz auf eine in [!DNL Commerce Intelligence] erstellte Datendimension anwenden, indem Sie sich an den Support wenden.

## verwandt

* [Best Practices für Segmentierung und Filterung](../../best-practices/segment-filter.md)
