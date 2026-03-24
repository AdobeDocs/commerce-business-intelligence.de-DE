---
title: Erstellen von Google Analytics-Diagrammen
description: Erfahren Sie, wie Sie aus Ihren Google Analytics-Daten Diagramme erstellen.
exl-id: ee80fd0d-e3b1-4331-853d-3c2c11931d3f
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
TQID: https://experienceleague.adobe.com/xfh0BjVasnSNP9mic7ps4jckaGpjF7INFNi2lSaKi-o
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 160
ht-degree: 0%

---

# [!DNL Google Analytics] erstellen

(mit Regex-Syntax-Hilfe)

Nachdem Sie Ihr [[!DNL Google Analytics] Konto](../../data-analyst/importing-data/integrations/google-analytics.md) verbunden haben, können Sie Diagramme mit Ihren [!DNL Google Analytics] Daten erstellen.

## [!DNL Google Analytics] erstellen

1. Klicken Sie auf **[!UICONTROL Add Chart** > **Create New Chart]**.

1. Wenn Sie eine Metrik im `Chart Builder` auswählen, scrollen Sie zum unteren Rand der Liste, um einen Abschnitt mit Ihren [!DNL Google Analytics] Profilen zu finden. Eine zweite Metrik -Dropdown-Liste wird angezeigt. Hier können Sie die Metrik auswählen, die Sie analysieren möchten.

1. Nachdem Sie die Metrik ausgewählt haben, können Sie mit diesem Diagramm wie mit einem anderen Diagramm fortfahren, indem Sie die gewünschten `time period`-, `interval`- und `perspectives` auswählen.

1. Der einzige wesentliche Unterschied besteht darin, dass `√` reguläre Ausdrücke für Filter verwendet. Ein regulärer Ausdruck (kurz Regex) ist eine spezielle Zeichenfolge zur Beschreibung eines Suchmusters. Beispiele für Regex-Syntax finden Sie im [[!DNL Google] Handbuch zu regulären Ausdrücken in Analytics](https://support.google.com/analytics/answer/1034324?hl=en).

>[!NOTE]
>
>Die einzigen Sonderzeichen, die mit dem Zeichen \ maskiert werden müssen, sind die folgenden Metazeichen:

| | | | | |
|-----|-----|-----|-----|-----|
| `^` | `[` | `]` | `$` | `(` |
| `)` | `.` | `{` | `}` | `*` |
| `+` | `?` | `\` | `\` | `-` |

{style="table-layout:auto"}
