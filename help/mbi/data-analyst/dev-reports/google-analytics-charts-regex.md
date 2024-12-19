---
title: Erstellen von Google Analytics-Diagrammen
description: Erfahren Sie, wie Sie aus Ihren Google Analytics-Daten Diagramme erstellen.
exl-id: ee80fd0d-e3b1-4331-853d-3c2c11931d3f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '160'
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
