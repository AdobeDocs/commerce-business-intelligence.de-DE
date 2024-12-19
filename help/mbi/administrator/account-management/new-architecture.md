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

[!DNL Adobe Commerce Intelligence] Produkt- und Engineering-Teams haben sich darauf konzentriert, im letzten Jahr die umfassendsten und am häufigsten geforderten Verbesserungen vorzunehmen. Adobe freut sich, die Verfügbarkeit einer neuen [!DNL Commerce Intelligence] Produktarchitektur bekannt geben zu können, die diese Verbesserungen Wirklichkeit werden lässt.

## Vorteile der neuen Architektur

* Erstellen Sie Spaltentypen auf der Data Warehouse, einschließlich berechneter Spalten mit SQL.
* Neue Spalten sind sofort verfügbar.
* Die Datenlatenz wurde erheblich verbessert.

## Technische Vorteile

Die wichtigsten Unterschiede sind oben aufgeführt, die wichtigste Änderung besteht jedoch in der Art und Weise, wie die Berechnungen während des Aktualisierungszyklus durchgeführt werden. Berechnungen werden nicht mehr bei jeder Aktualisierung für jede Spalte ausgeführt, sondern bei Bedarf über den Visual Report Builder.

### Wechseln zur neuen Architektur

Da die Konten grundlegend anders aufgebaut sind, gibt es keinen automatischen Prozess zum Migrieren Ihrer Data Warehouse oder Berichte zu einem neuen Architekturkonto. Der Wechsel zur neuen Architektur erfordert eine erneute Implementierung Ihres vorhandenen Kontos.

### Kosten für die Umstellung auf die neue Architektur

Keine zusätzlichen Kosten! Adobe wird dieses neue Konto erstellen, damit Sie mit der erneuten Implementierung beginnen können, die mindestens einen Monat kostenlos ist. Auf diese Weise haben Sie Zeit, beide Konten zu öffnen, sodass Sie die erneute Implementierung einfacher durchführen können, und stellen sicher, dass Ihr Team keine Service-Lücke hat.

### Erforderlicher Zeitaufwand für die Neuimplementierung des Kontos in der neuen Architektur

Die Zeit für die erneute Implementierung hängt davon ab, was neu erstellt werden soll. Adobe empfiehlt, die folgenden Schritte in Ihrem bestehenden Konto auszuführen, um einen Eindruck davon zu gewinnen, was mit Ihrer erneuten Implementierung verbunden wäre:

* Identifizieren Sie einen Kernsatz von Berichten/Dashboards.
* Identifizieren Sie die Metriken und Dimensionen, die zum Erstellen dieser Berichte erforderlich sind.
* Identifizieren Sie die Spalten, die erforderlich sind, um diese Metriken und Dimensionen neu zu erstellen.

Wenn dies abgeschlossen ist, wissen Sie, welche Daten Sie mit der neuen Architektur-Data Warehouse synchronisieren müssen, um diese Kernberichte neu zu erstellen.

### Hilfe wird abgerufen

Das [!DNL Adobe Commerce Intelligence] [Services](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)Team kann die erneute Implementierung gegen Aufpreis durchführen. Wenden Sie sich an Ihr [Adobe-](../../guide-overview.md#Submitting-a-Support-Ticket) und stellen Sie eine Liste der Dashboards/Berichte bereit, die Sie in Ihrem neuen Konto vorrangig erstellen möchten

### Bestehende Architektur beibehalten

Wenn diese Funktionen für Sie nicht wichtig sind, können Sie an Ihrem bestehenden Konto festhalten. Es fallen keine zusätzlichen Kosten für die Führung Ihres bestehenden Kontos an. Adobe unterstützt diese Konten weiterhin ohne Änderungen.
