---
title: Neue Architektur
description: Erfahren Sie mehr über die Vorteile der Umstellung auf eine neue Architektur.
exl-id: cbb10673-5704-4a90-9574-5ac114f389b9
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Import/Export
source-git-commit: ddda796c9f32d22b1d679fc245eb11b92cd491cf
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Neue Architektur

[!DNL Adobe Commerce Intelligence] Die Produkt- und Engineering-Teams haben sich darauf konzentriert, im letzten Jahr die umfassendsten und dringend geforderten Verbesserungen zu erzielen. Adobe freut sich, Ihnen die Verfügbarkeit einer neuen [!DNL Commerce Intelligence] -Produktarchitektur mitteilen zu können, die diese Verbesserungen ermöglicht.

## Vorteile der neuen Architektur

* Erstellen Sie Spaltentypen im Data Warehouse, einschließlich berechneter Spalten mit SQL.
* Neue Spalten sind sofort verfügbar.
* Die Datenlatenz wurde erheblich verbessert.

## Technische Vorteile

Die wichtigsten Unterschiede sind oben aufgeführt, aber die Hauptänderung ist die Art und Weise, wie Berechnungen während des Aktualisierungszyklus durchgeführt werden. Berechnungen werden bei jeder Aktualisierung nicht mehr in jeder Spalte ausgeführt, sondern werden stattdessen bei Bedarf über den Visual Report Builder ausgeführt.

### Wechsel zur neuen Architektur

Da die Konten grundlegend anders aufgebaut sind, gibt es keinen automatischen Prozess zur Migration Ihrer Data Warehouse oder Berichte zu einem neuen Architekturkonto. Der Wechsel zur neuen Architektur erfordert eine erneute Implementierung Ihres vorhandenen Kontos.

### Kosten für den Wechsel zur neuen Architektur

Keine zusätzlichen Kosten! Adobe erstellt dieses neue Konto, damit Sie mit der Neuimplementierung beginnen können, die für mindestens einen Monat kostenlos ist. Auf diese Weise haben Sie Zeit, beide Konten zu öffnen, damit Sie die Neuimplementierung einfacher durchführen und sicherstellen können, dass Ihr Team keine Dienstlücke aufweist.

### Erforderliche Zeit für die Neuimplementierung des Kontos in der neuen Architektur

Die Zeiten für die erneute Implementierung hängen davon ab, was Sie neu erstellen möchten. Adobe empfiehlt, dass Sie in Ihrem bestehenden Konto die folgenden Schritte ausführen, um eine Vorstellung davon zu erhalten, was in Ihrer Neuimplementierung involviert sein würde:

* Identifizieren Sie einen Hauptsatz von Berichten/Dashboards.
* Identifizieren Sie Metriken und Dimensionen, die für die Erstellung dieser Berichte erforderlich sind.
* Identifizieren Sie die Spalten, die zum erneuten Erstellen dieser Metriken und Dimensionen erforderlich sind.

Wenn dies abgeschlossen ist, wissen Sie, welche Daten Sie mit der neuen Architektur-Data Warehouse synchronisieren müssen, um diese Kernberichte neu zu erstellen.

### Hilfe erhalten

Das [!DNL Adobe Commerce Intelligence] [Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) kann Ihre Neuimplementierung gegen zusätzliche Kosten durchführen. Kontaktieren Sie Ihr [Adobe Account Team](../../guide-overview.md#Submitting-a-Support-Ticket) und bereiten Sie sich darauf vor, eine Liste der Dashboards/Berichte bereitzustellen, die Sie priorisieren möchten, um in dem neuen Konto zu erstellen.

### Aufenthalt mit vorhandener Architektur

Wenn diese Funktionen für Sie nicht wichtig sind, können Sie bei Ihrem vorhandenen Konto bleiben. Es fallen keine zusätzlichen Kosten an, um Ihr bestehendes Konto zu behalten. Adobe unterstützt diese Konten weiterhin ohne Änderungen.
