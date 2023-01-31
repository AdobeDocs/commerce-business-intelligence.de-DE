---
title: Neue Architektur
description: Erfahren Sie mehr über die Vorteile der Umstellung auf eine neue Architektur.
exl-id: cbb10673-5704-4a90-9574-5ac114f389b9
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Neue Architektur

Unsere Produkt- und Engineering-Teams haben sich darauf konzentriert, im letzten Jahr die umfassendsten und dringend geforderten Verbesserungen zu erzielen. Wir freuen uns, die Verfügbarkeit eines neuen [!DNL MBI] -Produktarchitektur, die diese Verbesserungen zur Realität werden lässt.

## Vorteile der neuen Architektur

* Erstellen Sie neue Spaltentypen im Data Warehouse, einschließlich berechneter Spalten mit SQL.
* Neue Spalten sind sofort verfügbar.
* Die Datenlatenz wurde erheblich verbessert.

## Technische Vorteile

Die wichtigsten Unterschiede sind oben aufgeführt, aber technisch hat sich die Art und Weise, wie wir Berechnungen während des Aktualisierungszyklus durchführen, geändert. Berechnungen werden bei jeder Aktualisierung nicht mehr in jeder Spalte ausgeführt. Sie werden stattdessen bei Bedarf vom Visual Report Builder ausgeführt.

### Wechsel zur neuen Architektur

Da die Konten grundsätzlich unterschiedlich erstellt sind, gibt es keinen automatischen Prozess, den wir verwenden können, um Ihre Data Warehouse- oder Berichte in ein neues Architekturkonto zu migrieren. Daher erfordert der Wechsel zur neuen Architektur eine erneute Implementierung Ihres vorhandenen Kontos.

### Kosten für den Wechsel zur neuen Architektur

Keine zusätzlichen Kosten! Wir erstellen ein neues Konto für Sie, um die Neuimplementierung zu starten, die für mindestens einen Monat kostenlos ist. Auf diese Weise haben Sie Zeit, beide Konten zu öffnen, damit Sie die Neuimplementierung einfacher durchführen und sicherstellen können, dass Ihr Team keine Dienstlücke aufweist.

### Erforderliche Zeit für die erneute Implementierung des Kontos in der neuen Architektur

Die Zeiten für die erneute Implementierung hängen davon ab, was Sie neu erstellen möchten. Wir empfehlen Ihnen, die folgenden Schritte in Ihrem vorhandenen Konto auszuführen, um eine Vorstellung davon zu erhalten, was in Ihrer Neuimplementierung involviert sein würde:

* Identifizieren Sie einen Hauptsatz von Berichten/Dashboards.
* Identifizieren Sie Metriken und Dimensionen, die für die Erstellung dieser Berichte erforderlich sind.
* Identifizieren Sie die Spalten, die zum erneuten Erstellen dieser Metriken und Dimensionen erforderlich sind.

Wenn dies abgeschlossen ist, wissen Sie, welche Daten Sie mit dem neuen Architektur-Data Warehouse synchronisieren müssen, um diese Core-Berichte neu zu erstellen.

### Hilfe erhalten

Die [!DNL MBI] Das Serviceteam kann Ihre erneute Implementierung gegen zusätzliche Kosten durchführen. Kontakt [Customer Success Team](../../guide-overview.md) und sind bereit, eine Liste von Dashboards/Berichten bereitzustellen, die Sie priorisieren möchten, um sie in dem neuen Konto zu erstellen

### Aufenthalt mit vorhandener Architektur

Wenn diese Funktionen für Sie nicht wichtig sind, können Sie bei Ihrem vorhandenen Konto bleiben. Es fallen keine zusätzlichen Kosten an, um Ihr bestehendes Konto zu behalten, und wir werden diese Konten weiterhin ohne Änderungen unterstützen.
