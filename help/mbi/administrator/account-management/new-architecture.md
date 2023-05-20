---
title: Neue Architektur
description: Erfahren Sie mehr über die Vorteile der Umstellung auf eine neue Architektur.
exl-id: cbb10673-5704-4a90-9574-5ac114f389b9
source-git-commit: c7f6bacd49487cd13c4347fe6dd46d6a10613942
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Neue Architektur

[!DNL Adobe Commerce Intelligence] Die Produkt- und Engineering-Teams haben sich darauf konzentriert, im letzten Jahr die umfassendsten und dringend geforderten Verbesserungen zu erzielen. Adobe freut sich, Ihnen die Verfügbarkeit eines neuen [!DNL Commerce Intelligence] -Produktarchitektur, die diese Verbesserungen zur Realität werden lässt.

## Vorteile der neuen Architektur

* Erstellen Sie Spaltentypen in der Data Warehouse, einschließlich berechneter Spalten mit SQL.
* Neue Spalten sind sofort verfügbar.
* Die Datenlatenz wurde erheblich verbessert.

## Technische Vorteile

Die wichtigsten Unterschiede sind oben aufgeführt, aber die Hauptänderung ist die Art und Weise, wie Berechnungen während des Aktualisierungszyklus durchgeführt werden. Berechnungen werden bei jeder Aktualisierung nicht mehr in jeder Spalte ausgeführt. Sie werden stattdessen bei Bedarf vom Visual Report Builder ausgeführt.

### Wechsel zur neuen Architektur

Da die Konten grundlegend anders aufgebaut sind, gibt es keinen automatischen Prozess, um Ihre Data Warehouse oder Berichte in ein neues Architekturkonto zu migrieren. Der Wechsel zur neuen Architektur erfordert eine erneute Implementierung Ihres vorhandenen Kontos.

### Kosten für den Wechsel zur neuen Architektur

Keine zusätzlichen Kosten! Adobe wird dieses neue Konto erstellen, damit Sie mit der Neuimplementierung beginnen können, die mindestens einen Monat lang kostenlos ist. Auf diese Weise haben Sie Zeit, beide Konten zu öffnen, damit Sie die Neuimplementierung einfacher durchführen und sicherstellen können, dass Ihr Team keine Dienstlücke aufweist.

### Erforderliche Zeit für die Neuimplementierung des Kontos in der neuen Architektur

Die Zeiten für die erneute Implementierung hängen davon ab, was Sie neu erstellen möchten. Adobe empfiehlt, dass Sie in Ihrem bestehenden Konto die folgenden Schritte ausführen, um eine Vorstellung davon zu erhalten, was in Ihrer Neuimplementierung involviert sein würde:

* Identifizieren Sie einen Hauptsatz von Berichten/Dashboards.
* Identifizieren Sie Metriken und Dimensionen, die für die Erstellung dieser Berichte erforderlich sind.
* Identifizieren Sie die Spalten, die zum erneuten Erstellen dieser Metriken und Dimensionen erforderlich sind.

Wenn dies abgeschlossen ist, wissen Sie, welche Daten Sie mit der neuen Architektur-Data Warehouse synchronisieren müssen, um diese Kernberichte neu zu erstellen.

### Hilfe erhalten

Die [!DNL Adobe Commerce Intelligence] [Serviceteam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) kann Ihre erneute Implementierung gegen zusätzliche Kosten durchführen. Wenden Sie sich an [Adobe Account Team](../../guide-overview.md#Submitting-a-Support-Ticket) und sind bereit, eine Liste von Dashboards/Berichten bereitzustellen, die Sie priorisieren möchten, um sie in dem neuen Konto zu erstellen

### Aufenthalt mit vorhandener Architektur

Wenn diese Funktionen für Sie nicht wichtig sind, können Sie bei Ihrem vorhandenen Konto bleiben. Es fallen keine zusätzlichen Kosten an, um Ihr bestehendes Konto zu behalten. Adobe unterstützt diese Konten weiterhin ohne Änderungen.
