---
title: Grafiken für Google Analytics erstellen
description: Erfahren Sie, wie Sie Diagramme aus Ihren Google Analytics-Daten erstellen.
exl-id: ee80fd0d-e3b1-4331-853d-3c2c11931d3f
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# [!DNL Google Analytics] Diagramme erstellen

(mit Hilfe zur Regex-Syntax)

Nachdem Sie Ihr [[!DNL Google Analytics] Konto](../../data-analyst/importing-data/integrations/google-analytics.md) verbunden haben, können Sie Diagramme mit Ihren [!DNL Google Analytics] -Daten erstellen.

## [!DNL Google Analytics] Diagramme erstellen

1. Klicken Sie auf **[!UICONTROL Add Chart** > **Create New Chart]**.

1. Scrollen Sie bei der Auswahl einer Metrik im Feld `Chart Builder` zum unteren Rand der Liste, um einen Abschnitt mit Ihren [!DNL Google Analytics] Profilen zu finden. Ein zweites Metrik-Dropdown wird angezeigt. Hier können Sie die Metrik auswählen, die Sie analysieren möchten.

1. Nachdem Sie die Metrik ausgewählt haben, können Sie mit diesem Diagramm wie einem anderen Diagramm fortfahren, indem Sie die gewünschten `time period`, `interval` und Daten `perspectives` auswählen.

1. Der Hauptunterschied besteht darin, dass `√` reguläre Ausdrücke für Filter verwendet. Ein regulärer Ausdruck (kurz regex) ist eine spezielle Textzeichenfolge zur Beschreibung eines Suchmusters. Beispiele für die Regex-Syntax finden Sie im [[!DNL Google] Handbuch zu regulären Ausdrücken in Analytics](https://support.google.com/analytics/answer/1034324?hl=en).

>[!NOTE]
>
>Die einzigen Sonderzeichen, die mit dem Zeichen \ maskiert werden müssen, sind die folgenden Metazeichen:

| | | | | |
|-----|-----|-----|-----|-----|
| `^` | `[` | `]` | `$` | `(` |
| `)` | `.` | `{` | `}` | `*` |
| `+` | `?` | `\` | `\` | `-` |

{style="table-layout:auto"}
