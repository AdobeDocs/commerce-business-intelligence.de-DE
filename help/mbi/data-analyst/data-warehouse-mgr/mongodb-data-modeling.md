---
title: MongoDB-Datenmodellierung
description: Erfahren Sie, wie Sie Datenmuster vermeiden, die ein Problem darstellen.
exl-id: 556c854b-5d7c-4f72-8ed7-5bc08d9ee5b9
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# [!DNL MongoDB] Datenmodellierung

Wann [!DNL MBI] abruft [!DNL MongoDB] -Daten in ein relationales Modell übersetzt werden.

Die schlechte Nachricht: Obwohl die meisten Datenmuster kein Problem darstellen, gibt es einige, die aufgrund der Übersetzung in ein relationales Modell [!DNL MBI] unterstützt nicht.

Die gute Nachricht: All diese Muster lassen sich vermeiden.

## Übergeordnete Arrays {#subnested}

Wenn Ihre Sammlung wie im folgenden Beispiel aussieht: [!DNL MBI] repliziert nur die Daten im Elemente-Array. Daten aus dem Array der Unterelemente werden nicht abgerufen.

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

Sammlungen, die Objekte mit variablen Objektschlüsseln enthalten, werden nicht repliziert in [!DNL MBI]. Beispiel:

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
