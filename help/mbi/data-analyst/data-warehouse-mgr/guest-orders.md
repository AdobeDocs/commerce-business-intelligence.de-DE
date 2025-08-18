---
title: Gastbestellungen
description: Erfahren Sie mehr über die Auswirkungen von Gastbestellungen auf Ihre Daten und welche Optionen Sie haben, um Gastbestellungen in Ihrer [!DNL Commerce Intelligence] Data Warehouse ordnungsgemäß zu berücksichtigen.
exl-id: cd5120ca-454c-4cf4-acb4-3aebe06cdc9a
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Gastbestellungen

Wenn Sie bei der Überprüfung Ihrer Bestellungen feststellen, dass viele `customer\_id`-Werte null sind oder keinen Wert haben, um wieder zur `customers`-Tabelle hinzuzufügen, ist dies ein Hinweis darauf, dass Ihr Store Gastbestellungen zulässt. Das bedeutet, dass Ihre `customers` höchstwahrscheinlich nicht alle Ihre Kunden einschließt.

In diesem Abschnitt wird erläutert, wie sich Gastbestellungen auf Ihre Daten auswirken und welche Optionen Sie haben, um Gastbestellungen in Ihrer [!DNL Commerce Intelligence] Data Warehouse ordnungsgemäß zu berücksichtigen.

## Auswirkungen von Gastaufträgen auf Daten

In der typischen Commerce-Datenbank gibt es eine `orders`, die mit einer `customers` verknüpft ist. Jede Zeile in der `orders` Tabelle verfügt über eine `customer\_id` Spalte, die für eine Zeile in der `customers` Tabelle eindeutig ist.

* **Wenn alle Kunden registriert** und keine Gastbestellungen zulässig sind, bedeutet dies, dass jeder Datensatz in der `orders`-Tabelle einen -Wert in der `customer\_id` Spalte aufweist. Dadurch wird jede Bestellung wieder an die `customers`-Tabelle angefügt.

  ![](../../assets/guest-orders-4.png)

* **Wenn Gastbestellungen zulässig sind** bedeutet dies, dass einige Bestellungen in der Spalte &quot;`customer\_id`&quot; keinen Wert aufweisen. Nur registrierte Kunden erhalten einen Wert für die Spalte `customer\_id` in der `orders`. Kunden, die nicht registriert sind, erhalten einen `NULL` Wert (oder ein leeres Feld) für diese Spalte. Infolgedessen verfügen nicht alle Bestelldatensätze über übereinstimmende Datensätze in der `customers`.

  >[!NOTE]
  >
  >Um die eindeutige Person zu identifizieren, die die Bestellung getätigt hat, muss neben `customer\_id` ein weiteres eindeutiges Benutzerattribut an eine Bestellung angehängt sein. Normalerweise wird die E-Mail-Adresse des Kunden verwendet.

## Verbuchen von Gastaufträgen im Data Warehouse-Setup

In der Regel berücksichtigt der Sales Engineer, der Ihr Konto implementiert, Gastaufträge beim Aufbau der Grundlage für Ihre Data Warehouse.

Die beste Möglichkeit, Gastaufträge zu berücksichtigen, besteht darin, alle Metriken auf Kundenebene auf der `orders`-Tabelle zu basieren. Bei dieser Einrichtung wird eine eindeutige Kunden-ID verwendet, die alle Kunden besitzen, einschließlich Gäste (normalerweise wird Kunden-E-Mail verwendet). Registrierungsdaten aus der `customers` werden dabei ignoriert. Mit dieser Option werden nur Kunden, die mindestens einen Kauf getätigt haben, in Berichte auf Kundenebene aufgenommen. Registrierte Benutzer, die noch keinen Kauf getätigt haben, sind nicht eingeschlossen. Bei dieser Option basiert Ihre `New customer`-Metrik auf dem Datum der ersten Bestellung des Kunden in der `orders`.

Sie werden möglicherweise feststellen, dass der in diesem Einrichtungstyp festgelegte `Customers we count`-Filter einen Filter für `Customer's order number = 1` enthält.

![](../../assets/guest-orders-filter-set.png)

In einer Situation ohne Gastaufträge ist jeder Kunde als eindeutige Zeile in der Kundentabelle vorhanden (siehe Abbildung 1). Eine Metrik wie `New customers` kann einfach die ID dieser Tabelle basierend auf `created\_at` Datum zählen, um neue Kunden anhand des Registrierungsdatums zu verstehen.

Bei einer Einrichtung für Gastaufträge, bei der alle Kundenmetriken auf der `orders` basieren, um Gastaufträge zu berücksichtigen, müssen Sie sicherstellen, dass Sie `not counting customers twice` sind. Wenn Sie die Kennung der Tabelle Bestellungen zählen, zählen Sie jede Bestellung. Wenn Sie stattdessen die ID in der `orders` Tabelle zählen und einen Filter verwenden, `Customer's order number = 1`, zählen Sie jede eindeutige Kunden-`only one time`. Dies gilt für alle Metriken auf Kundenebene, wie `Customer's lifetime revenue` oder `Customer's lifetime number of orders`.

Oben sehen Sie, dass die `customer\_ids`-Tabelle Null-`orders` enthält. Wenn Sie die `customer\_email` verwenden, um Unique Customers zu identifizieren, können Sie sehen, dass `erin@test.com` drei (3) Bestellungen aufgegeben hat. Daher können Sie basierend auf den folgenden Bedingungen eine `New customers` Metrik in Ihrer `orders` erstellen:

* `Operation table = orders`
* `Operation column = id`
* `Operation = count`
* `Timestamp = Customer's first order date`
* `Filter = Customer's we count (where Customer's order number = 1)`
