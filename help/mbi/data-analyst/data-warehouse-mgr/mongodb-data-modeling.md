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

Wenn [!DNL Adobe Commerce Intelligence] [!DNL MongoDB] Daten abruft, werden diese Daten in ein relationales Modell übersetzt.

Die schlechte Nachricht: Während die meisten Datenmuster kein Problem darstellen, gibt es einige, die von [!DNL Commerce Intelligence] aufgrund der Übersetzung in ein relationales Modell nicht unterstützt werden.

Die gute Nachricht: All diese Muster können vermieden werden.

## Unterverschachtelte Arrays {#subnested}

Wenn Ihre Auflistung dem folgenden Beispiel entspricht, repliziert [!DNL Commerce Intelligence] die Daten nur im Element-Array. Daten aus dem Unterelement-Array werden nicht abgerufen.

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

## Schlüssel des variablen Objekts {#varobjectkeys}

Sammlungen, die Objekte mit variablen Objektschlüsseln enthalten, werden nicht in [!DNL Commerce Intelligence] repliziert. Beispiel:

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

Dies tritt normalerweise auf, wenn ein -Objekt verwendet wird und ein Array geeigneter wäre. Überarbeiten Sie nun das obige Beispiel:

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
