---
title: Verkürzen des Aktualisierungszyklus
description: Erfahren Sie, wie Sie die Zykluszeit für Aktualisierungen reduzieren können.
exl-id: 0b211e2d-770f-480d-a7fb-8d10e3e7272e
role: Admin, User
feature: Data Integration, Data Import/Export, Data Warehouse Manager, Dashboards
TQID: https://experienceleague.adobe.com/DFlzL9E95teiWI31j7qWRU8Ab6GkbFX7iPPdaxGq48A
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 398
ht-degree: 0%

---

# Verkürzen der Verarbeitungszeit für den Aktualisierungszyklus

[!DNL Adobe Commerce Intelligence] synchronisiert den ganzen Tag lang mit Ihrer Datenbank, um neue Daten zu replizieren, sodass Ihre Dashboards immer die neuesten Informationen anzeigen.

Zu einer bereits langen Aktualisierungszeit können viele Faktoren hinzukommen. Bestimmte Replikationsmethoden, höhere Häufigkeit der erneuten Prüfungen und die Anzahl der Dashboards und Diagramme sind nur einige wenige Faktoren. In diesem Abschnitt werden einige Best Practices erläutert, mit denen Sie die Aktualisierungszeit verkürzen können.

## Häufigkeit der erneuten Prüfung verringern

In einer Datenbanktabelle können Datenspalten mit veränderlichen Werten vorhanden sein. Beispiel: In einer Tabelle **Bestellungen** kann es eine Spalte namens **Status** geben. Wenn eine Bestellung erstmals in die Datenbank geschrieben wird, kann die Statusspalte den Wert `pending` enthalten. Die Bestellung wird in Ihrer [Data Warehouse](../data-analyst/data-warehouse-mgr/tour-dwm.md) mit diesem `pending` Wert repliziert.

Änderbare Spalten müssen im [&#x200B; auf aktualisierte Werte &#x200B;](../data-analyst/data-warehouse-mgr/cfg-data-rechecks.md) werden. Standardmäßig überprüft [!DNL Commerce Intelligence] diese Spalten bei jeder Aktualisierung neu. Wenn jedoch eine große Datenmenge erneut überprüft und repliziert werden muss, kann dies negative Auswirkungen auf die Aktualisierungszeit haben. Anstatt während jeder Aktualisierung erneute Prüfungen durchzuführen, empfiehlt Adobe, die Häufigkeit der erneuten Prüfungen auf täglich, wöchentlich oder monatlich festzulegen.

## Verwenden von inkrementellen Replikationsmethoden

Wie bereits erwähnt, hängen lange Aktualisierungszeiten direkt damit zusammen, wie viele Daten erneut überprüft und repliziert werden müssen. [Inkrementelle Replikationsmethoden](../data-analyst/data-warehouse-mgr/cfg-replication-methods.md) können die Menge der während des Aktualisierungszyklus verarbeiteten Daten erheblich reduzieren. Wenn möglich, empfiehlt Adobe die Verwendung dieser Methoden oder die Änderung Ihrer Datenbank, um eine inkrementelle Methode zu unterstützen.

## Entfernen nicht verwendeter Diagramme aus Dashboards

Am Ende des Aktualisierungszyklus führt [!DNL Commerce Intelligence] einen Cache-Vorgang für alle Diagramme durch. Ein Cache speichert Daten, damit zukünftige Informationsanfragen schneller erledigt werden können. [!DNL Commerce Intelligence] bedeutet dies, dass Dashboards schnell geladen werden, da Diagramme nicht bei jedem Laden Daten abfragen müssen.

Da [!DNL Commerce Intelligence] nur Cache-Vorgänge für Diagramme ausführt, die in einem Dashboard gefunden wurden, reduziert das Entfernen nicht verwendeter Diagramme aus Ihren Dashboards die Aktualisierungszeit. Denken Sie daran, dass dasselbe Diagramm in mehreren Dashboards angezeigt werden kann. Wenden Sie sich an Ihr Team, um sicherzustellen, dass auch nicht verwendete Diagramme entfernt wurden.

>[!NOTE]
>
>Beim Entfernen von Diagrammen aus dem Dashboard wird das Diagramm nicht gelöscht. Sie können [jederzeit wieder hinzufügen](../data-user/dashboards/add-charts-dashboard.md).

## Datenbank für Analysen optimieren

Neben der Neubewertung der Häufigkeit der erneuten Prüfungen, der Replikationsmethoden und der Nützlichkeit des Diagramms können Sie auch [Ihre Datenbank für Analysen optimieren](../best-practices/opt-db-analysis.md).

## Verpackung

Wenn Ihre Aktualisierungszeit auch nach der Implementierung dieser Empfehlungen immer noch langsam zu sein scheint, [wenden Sie sich an das Support-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).
