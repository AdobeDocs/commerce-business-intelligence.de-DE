---
title: MongoDB-Datenmodellierung
description: Erfahren Sie, wie Sie Datenmuster vermeiden, die ein Problem darstellen.
exl-id: 556c854b-5d7c-4f72-8ed7-5bc08d9ee5b9
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 1%

---

# [!DNL MongoDB] Datenmodellierung

Wann [!DNL Adobe Commerce Intelligence] abruft [!DNL MongoDB] -Daten in ein relationales Modell übersetzt werden.

Die schlechte Nachricht: Die meisten Datenmuster werfen zwar kein Problem auf, es gibt jedoch einige wenige, die von [!DNL Commerce Intelligence], da die Übersetzung in ein relationales Modell erfolgt.

Die gute Nachricht: All diese Muster lassen sich vermeiden.

## Subverschachtelte Arrays {#subnested}

Wenn Ihre Sammlung wie im folgenden Beispiel aussieht: [!DNL Commerce Intelligence] repliziert nur die Daten im Elemente-Array. Daten aus dem Array der Unterelemente werden nicht abgerufen.

```bash
    {
        _id: 0000000000000001
        items: [
            {
                _id: 0000000000000002
               subItems: [
                   {
                       _id: 0000000000000003
                      name: "Donut"
                      description: "glazed"
                   }
               ]
            }
        ]
    }
```

## Variablenobjektschlüssel {#varobjectkeys}

Sammlungen, die Objekte mit variablen Objektschlüsseln enthalten, werden nicht repliziert in [!DNL Commerce Intelligence]. Beispiel:

```bash
    {
        _id: 0000000000000001
        friends: {
            0000000000000002: "Jimmy",
            0000000000000004: "Roger",
            0000000000000005: "Susan"
        },
    }
```

Dies tritt normalerweise dann auf, wenn ein Objekt verwendet wird und ein Array angemessener wäre. Nacharbeiten Sie nun das obige Beispiel:

```bash
    {
        _id: 0000000000000001
        friends: [
            { friend_id: 0000000000000002, name: "Jimmy" },
            { friend_id: 0000000000000004, name: "Roger" },
            { friend_id: 0000000000000005, name: "Susan"}
        ]
    }
```
