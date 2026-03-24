---
title: MongoDB-Datenmodellierung
description: Erfahren Sie, wie Sie Datenmuster vermeiden, die ein Problem darstellen.
exl-id: 556c854b-5d7c-4f72-8ed7-5bc08d9ee5b9
role: Admin, Developer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
TQID: https://experienceleague.adobe.com/L9xlGE4hAQssTHJzzxQD9EGUVaIZFY-2-ALOLM9vym4
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b23e006f-0a29-4f1d-8fd0-77aa56f3d12b
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 129
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
