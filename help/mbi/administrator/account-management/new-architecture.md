---
title: Neue Architektur
description: Erfahren Sie mehr über die Vorteile der Umstellung auf eine neue Architektur.
exl-id: cbb10673-5704-4a90-9574-5ac114f389b9
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Data Import/Export
TQID: https://experienceleague.adobe.com/EtbKFT7OKaTZQ55XNz0NwpxQNSXyazk47dGwKhETNjM
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 390
ht-degree: 0%

---

# Neue Architektur

[!DNL Adobe Commerce Intelligence] Produkt- und Engineering-Teams haben sich darauf konzentriert, im letzten Jahr die umfassendsten und am häufigsten geforderten Verbesserungen vorzunehmen. Adobe freut sich, die Verfügbarkeit einer neuen [!DNL Commerce Intelligence] Produktarchitektur bekannt geben zu können, mit der diese Verbesserungen Realität werden.

## Vorteile der neuen Architektur

* Erstellen Sie Spaltentypen in der Data Warehouse, einschließlich berechneter Spalten mit SQL.
* Neue Spalten sind sofort verfügbar.
* Die Datenlatenz wurde erheblich verbessert.

## Technische Vorteile

Die wichtigsten Unterschiede sind oben aufgeführt, die wichtigste Änderung besteht jedoch in der Art und Weise, wie die Berechnungen während des Aktualisierungszyklus durchgeführt werden. Berechnungen werden nicht mehr bei jeder Aktualisierung für jede Spalte ausgeführt, sondern bei Bedarf über Visual Report Builder.

### Wechseln zur neuen Architektur

Da die Konten grundlegend anders aufgebaut sind, gibt es keinen automatischen Prozess zum Migrieren Ihrer Data Warehouse- oder -Berichte zu einem neuen Kontoarchitektur-Konto. Der Wechsel zur neuen Architektur erfordert eine erneute Implementierung Ihres vorhandenen Kontos.

### Kosten für die Umstellung auf die neue Architektur

Keine zusätzlichen Kosten! Adobe erstellt dieses neue Konto, damit Sie mit der erneuten Implementierung beginnen können, die mindestens einen Monat kostenlos ist. Auf diese Weise haben Sie Zeit, beide Konten zu öffnen, sodass Sie die erneute Implementierung einfacher durchführen können, und stellen sicher, dass Ihr Team keine Service-Lücke hat.

### Erforderlicher Zeitaufwand für die Neuimplementierung des Kontos in der neuen Architektur

Die Zeit für die erneute Implementierung hängt davon ab, was neu erstellt werden soll. Adobe empfiehlt, die folgenden Schritte in Ihrem bestehenden Konto auszuführen, um einen Eindruck davon zu gewinnen, was mit Ihrer erneuten Implementierung verbunden wäre:

* Identifizieren Sie einen Kernsatz von Berichten/Dashboards.
* Identifizieren Sie die Metriken und Dimensionen, die zum Erstellen dieser Berichte erforderlich sind.
* Identifizieren Sie die Spalten, die erforderlich sind, um diese Metriken und Dimensionen neu zu erstellen.

Wenn dies abgeschlossen ist, wissen Sie, welche Daten Sie mit der neuen Data Warehouse-Architektur synchronisieren müssen, um diese Kernberichte neu zu erstellen.

### Hilfe wird abgerufen

Das [!DNL Adobe Commerce Intelligence] [Services](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html)Team kann die erneute Implementierung gegen Aufpreis durchführen. Wenden Sie sich an Ihr [Adobe-](../../guide-overview.md#Submitting-a-Support-Ticket) und stellen Sie eine Liste der Dashboards/Berichte bereit, die Sie in Ihrem neuen Konto vorrangig erstellen möchten

### Bestehende Architektur beibehalten

Wenn diese Funktionen für Sie nicht wichtig sind, können Sie an Ihrem bestehenden Konto festhalten. Es fallen keine zusätzlichen Kosten für die Führung Ihres bestehenden Kontos an. Adobe unterstützt diese Konten weiterhin ohne Änderungen.
