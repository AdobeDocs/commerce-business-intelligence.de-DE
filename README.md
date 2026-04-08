---
source-git-commit: 4557430537492370a52030b60750950db8b245da
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 6%

---
# Technische Dokumentation zu Adobe Commerce Intelligence

Wir freuen uns über Beiträge von der Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentations-Teams.

## Adobe Open Source-Verhaltenskodex

Dieses Projekt beachtet den [Adobe Open Source Code of Conduct](code-of-conduct.md) bzw. den [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie in [diesem Artikel](contributing.md).

## Über Ihre Beiträge zu Adobe-Inhalten

Siehe das [Handbuch für Mitwirkende an Adobe-Dokumenten](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie kleinere Aktualisierungen beitragen möchten, besuchen Sie den Artikel und klicken Sie auf den Feedback-Bereich unten im Artikel, klicken Sie auf **Detaillierte Feedback-Optionen** und dann auf **Bearbeiten vorschlagen**, um zur Markdown-Quelldatei auf GitHub zu gelangen. Verwenden Sie die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Weitere Informationen finden Sie im allgemeinen Leitfaden für Beitragende zu Adobe[Dokumenten .](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)

Kleinere Korrekturen oder Erläuterungen, die Sie zur Dokumentation und zu Code-Beispielen in diesem Repository eingeben, werden von den Adobe-Nutzungsbedingungen abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Teil der Adobe-Community sind und einen neuen Artikel erstellen oder wichtige Änderungen vornehmen möchten, verwenden Sie im Git-Repository die Registerkarte „Probleme“, um ein Problem zu senden und eine Konversation mit dem Dokumentations-Team zu beginnen. Nachdem Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diese neuen Inhalte durch eine Kombination von Arbeiten in den öffentlichen und privaten Repositorys einzubringen.

### Wesentliche Veränderungen durch Adobe Mitarbeiter

Wenn Sie technischer Redakteur, Programmmanager oder Entwickler des Produktteams für eine Adobe Experience Cloud-Lösung sind und es Ihre Aufgabe ist, technische Artikel zu erstellen oder zu diesen beizutragen, sollten Sie das private Repository von GHEC verwenden.

## Tools und Einrichtung

Community-Mitwirkende können für eine einfache Bearbeitung die GitHub-Benutzeroberfläche oder für wichtige Beiträge das Repository nutzen.

Weitere Informationen finden Sie im Adobe-Handbuch für Mitwirkende [ Dokumenten .](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)

## Verwenden von Markdown zum Formatieren des Themas

Alle Artikel in diesem Repository verwenden GitHub-Markdown. Wenn Sie mit Markdown nicht vertraut sind, lesen Sie:

- [Markdown-Syntaxhandbuch](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax)
- [Markdown-Syntax-Schnellübersicht](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/cheatsheet)

## Pre-commit-Hooks für die Bildoptimierung

Dieses Repository enthält automatisierte Hooks zur Vorabbestätigung, mit denen Bilder vor dem Commit optimiert werden. **Alle Mitwirkenden sollten diese Erweiterungspunkte aktivieren** um eine konsistente Bildoptimierung und eine reduzierte Repository-Größe sicherzustellen.

### Schnelleinrichtung

Führen Sie nach dem Klonen des Repositorys Folgendes aus:

```bash
.githooks/setup-hooks.sh
```

### Was die Haken tun

- Gestaffelte Bilddateien automatisch erkennen (PNG, JPG, JPEG, GIF, SVG)
- `image_optim` ausführen, um Bilder zu komprimieren und zu optimieren
- Optimierte Bilder automatisch neu inszenieren
- Sicherstellen, dass alle übergebenen Bilder ordnungsgemäß optimiert sind

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

- [Workflow für selten Mitwirkende](https://experienceleague.adobe.com/en/docs/authoring-guide/using/editing/git-workflow-infrequent-user)
- [GitHub-Pull-Anforderungen](https://experienceleague.adobe.com/en/docs/authoring-guide/using/editing/public-github)

### Authoring

- [Best Practices für die Inhaltserstellung](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/authoring-best-practices)
- [Markdown-Syntaxhandbuch](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax)
- [Markdown-Syntax-Schnellübersicht](https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/cheatsheet)
- [Arbeiten mit Tabellen](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/tables)
- [Links hinzufügen](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/linking)
- [Inhalte verschieben und neu strukturieren](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/restructure-new)
