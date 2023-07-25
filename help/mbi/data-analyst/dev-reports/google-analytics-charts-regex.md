---
title: Google Analytics-Diagramme erstellen
description: Erfahren Sie, wie Sie Diagramme aus Ihren Google Analytics-Daten erstellen.
exl-id: ee80fd0d-e3b1-4331-853d-3c2c11931d3f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Erstellen [!DNL Google Analytics] charts

(mit Hilfe zur Regex-Syntax)

Nachdem Sie Ihre [[!DNL Google Analytics] account](../../data-analyst/importing-data/integrations/google-analytics.md)können Sie Diagramme mit [!DNL Google Analytics] Daten.

## Erstellen [!DNL Google Analytics] Diagramme

1. Klicken **[!UICONTROL Add Chart** > **Create New Chart]**.

1. Bei der Auswahl einer Metrik im `Chart Builder`, scrollen Sie zum unteren Rand der Liste, um einen Abschnitt mit Ihrer [!DNL Google Analytics] Profile. Ein zweites Metrik-Dropdown wird angezeigt. Hier können Sie die Metrik auswählen, die Sie analysieren möchten.

1. Nachdem Sie die Metrik ausgewählt haben, können Sie mit diesem Diagramm wie einem anderen Diagramm fortfahren, indem Sie die `time period`, `interval`und Daten `perspectives` das Sie gerne sehen würden.

1. Der einzige große Unterschied besteht darin, dass `√` verwendet reguläre Ausdrücke für Filter. Ein regulärer Ausdruck (kurz regex) ist eine spezielle Textzeichenfolge zur Beschreibung eines Suchmusters. Beispiele für die Regex-Syntax finden Sie in der [[!DNL Google] Handbuch zu regulären Ausdrücken in Analytics](https://support.google.com/analytics/answer/1034324?hl=en).

>[!NOTE]
>
>Die einzigen Sonderzeichen, die mit dem Zeichen \ maskiert werden müssen, sind die folgenden Metazeichen:

| | | | | |
|-----|-----|-----|-----|-----|
| `^` | `[` | `]` | `$` | `(` |
| `)` | `.` | `{` | `}` | `*` |
| `+` | `?` | `\` | `\` | `-` |

{style="table-layout:auto"}
