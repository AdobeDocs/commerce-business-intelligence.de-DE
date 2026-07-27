---
source-git-commit: aa7acd0d863a3cd48ff83675b72c2a96eae02b4d
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---
# Technische Dokumentation zu Adobe Commerce Intelligence

Wir freuen uns über Beiträge von der Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentations-Teams.

## Adobe Open Source-Verhaltenskodex

Dieses Projekt hat den [Open Source-Verhaltenskodex für Adobe ](code-of-conduct.md) den [.NET Foundation-Verhaltenskodex ](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie im Artikel [Beitragende](contributing.md) .

## Über Ihre Beiträge zu Adobe-Inhalten

Siehe das [Handbuch für Mitwirkende an Adobe-Dokumenten](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie kleinere Aktualisierungen beitragen möchten, besuchen Sie den Artikel und klicken Sie auf den Feedback-Bereich unten im Artikel, klicken Sie auf **Detaillierte Feedback-Optionen** und dann auf **Bearbeiten vorschlagen**, um zur Markdown-Quelldatei auf GitHub zu gelangen. Verwenden Sie die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Weitere Informationen finden Sie im allgemeinen Leitfaden für Beitragende zu Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)Dokumenten .[

Kleinere Korrekturen oder Erläuterungen, die Sie zur Dokumentation und zu Code-Beispielen in diesem Repository eingeben, werden von den Adobe-Nutzungsbedingungen abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Teil der Adobe-Community sind und einen neuen Artikel erstellen oder wichtige Änderungen vornehmen möchten, verwenden Sie im Git-Repository die Registerkarte „Probleme“, um ein Problem zu senden und eine Konversation mit dem Dokumentations-Team zu beginnen. Nachdem Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diese neuen Inhalte durch eine Kombination von Arbeiten in den öffentlichen und privaten Repositorys einzubringen.

### Wesentliche Veränderungen durch Adobe Mitarbeiter

Wenn Sie technischer Redakteur/technische Redakteurin, Programm-Manager oder Entwickler(in) des Produkt-Teams für eine Adobe Experience Cloud-Lösung sind und es Ihre Aufgabe ist, technische Artikel zu erstellen oder zu diesen beizutragen, sollten Sie das private Repository von GHEC verwenden.

## Tools und Einrichtung

Community-Mitwirkende können für eine einfache Bearbeitung die GitHub-Benutzeroberfläche oder für wichtige Beiträge das Repository nutzen.

Weitere Informationen finden Sie im Adobe-Handbuch für Mitwirkende ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) Dokumenten .[

## Verwenden von Markdown zum Formatieren des Themas

Alle Artikel in diesem Repository verwenden GitHub-Markdown. Wenn Sie mit Markdown nicht vertraut sind, lesen Sie:

- [Handbuch zur Markdown-Syntax](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax)
- [Markdown-Syntax-Schnellübersicht](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/cheatsheet)

## Pre-commit-Hooks für die Bildoptimierung

Dieses Repository enthält automatisierte Hooks zur Vorabbestätigung, mit denen Bilder vor dem Commit optimiert werden. **Alle Mitwirkenden sollten diese Erweiterungspunkte aktivieren** um eine konsistente Bildoptimierung und eine reduzierte Repository-Größe sicherzustellen.

### Schnelleinrichtung

Führen Sie nach dem Klonen des Repositorys Folgendes aus:

```bash
.githooks/setup-hooks.sh
```

### Was die Haken tun

- Erkennen gestaffelter Bilddateien (`.png`, `.jpeg`, `.jpg`, `.gif`, `.svg`) automatisch
- Führen Sie `image_optim` aus, um Rasterbilder (`.png`, `.jpeg`, `.jpg`, `.gif`) zu komprimieren und zu optimieren
- Optimierte Bilder automatisch neu inszenieren
- Sicherstellen, dass alle übergebenen Rasterbilder ordnungsgemäß optimiert sind
- Überprüfen Sie gestaffelte SVGs auf eine Größenbeschränkung und brechen Sie den Commit ab, wenn eine übergroße SVG von `help/` referenziert wird (andernfalls einfach warnen).

### Vorteile

- Verringerte Repository-Größe
- Schnelleres Laden von Seiten für die Dokumentation
- Konsistente Bildqualität für alle Mitwirkenden
- Keine manuelle Optimierung erforderlich

Detaillierte Setup-Anweisungen, Fehlerbehebung und Konfiguration finden Sie unter [`.githooks/README.md`](.githooks/README.md).

## Experience League Authoring-Handbuch

### Erste Schritte

- [Erste Schritte - Überblick](https://experienceleague.adobe.com/en/docs/authoring-guide/using/getting-started/getting-started)
- [Git-Einrichtung](https://experienceleague.adobe.com/en/docs/authoring-guide/using/setup/tools/git-setup)
- [Grundlagen zur Git- und GitHub-Dokumentation](https://experienceleague.adobe.com/en/docs/authoring-guide/using/setup/tools/git-fundamentals)
- [Schnellstartvideos](https://experienceleague.adobe.com/en/docs/authoring-guide/using/getting-started/quick-start-guides/quick-start-overview)

### Workflows

- [Arbeitsablauf für selten Mitwirkende](https://experienceleague.adobe.com/en/docs/authoring-guide/using/editing/git-workflow-infrequent-user)
- [GitHub-Pull-Anforderungen](https://experienceleague.adobe.com/en/docs/authoring-guide/using/editing/public-github)

### Authoring

- [Best Practices für die Inhaltserstellung](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/authoring-best-practices)
- [Handbuch zur Markdown-Syntax](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax)
- [Markdown-Syntax-Schnellübersicht](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/cheatsheet)
- [Arbeiten mit Tabellen](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/tables)
- [Links hinzufügen](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/linking)
- [Inhalte verschieben und neu strukturieren](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/restructure-new)
