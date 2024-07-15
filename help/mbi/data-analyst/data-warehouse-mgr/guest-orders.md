---
title: Gastaufträge
description: Erfahren Sie, welche Auswirkungen Gastaufträge auf Ihre Daten haben und welche Optionen Sie für Gastaufträge in Ihrer [!DNL Commerce Intelligence] Data Warehouse richtig berücksichtigen müssen.
exl-id: cd5120ca-454c-4cf4-acb4-3aebe06cdc9a
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Gastbestellungen

Wenn Sie bei der Überprüfung Ihrer Bestellungen feststellen, dass viele `customer\_id` -Werte null sind oder keinen Wert haben, der der `customers` -Tabelle zugeordnet werden kann, deutet dies darauf hin, dass Ihr Store Gastbestellungen zulässt. Das bedeutet, dass Ihre `customers`-Tabelle aller Ihrer Kunden aller Wahrscheinlichkeit nach nicht eingeschlossen ist.

In diesem Thema werden die Auswirkungen von Gastaufträgen auf Ihre Daten und die Optionen erläutert, die Sie für Gastaufträge in Ihrer [!DNL Commerce Intelligence] -Data Warehouse richtig berücksichtigen müssen.

## Auswirkung von Gastaufträgen auf Daten

In der typischen Commerce-Datenbank gibt es eine `orders` -Tabelle, die mit einer `customers` -Tabelle verknüpft ist. Jede Zeile der Tabelle `orders` enthält eine Spalte `customer\_id`, die für eine Zeile in der Tabelle `customers` eindeutig ist.

* **Wenn alle Kunden registriert sind** und Gastaufträge nicht zulässig sind, bedeutet dies, dass jeder Datensatz in der Tabelle `orders` einen Wert in der Spalte `customer\_id` enthält. Daher wird jede Bestellung wieder in die Tabelle `customers` aufgenommen.

  ![](../../assets/guest-orders-4.png)

* **Wenn Gastaufträge** erlaubt sind, bedeutet dies, dass einige Bestellungen keinen Wert in der Spalte `customer\_id` haben. Nur registrierte Kunden erhalten einen Wert für die Spalte `customer\_id` in der Tabelle `orders`. Kunden, die nicht registriert sind, erhalten für diese Spalte den Wert `NULL` (oder leer). Daher verfügen nicht alle Bestelldatensätze über übereinstimmende Datensätze in der Tabelle `customers`.

  >[!NOTE]
  >
  >Um die eindeutige Person zu identifizieren, die die Bestellung aufgegeben hat, muss neben `customer\_id` ein weiteres eindeutiges Benutzerattribut an eine Bestellung angehängt werden. In der Regel wird die E-Mail-Adresse des Kunden verwendet.

## Wie werden Gastaufträge bei der Data Warehouse-Einrichtung berücksichtigt?

Normalerweise berücksichtigt der Sales Engineer, der Ihr Konto implementiert, Gastaufträge bei der Erstellung der Grundlage Ihrer Data Warehouse.

Die beste Methode zur Berücksichtigung von Gastbestellungen besteht darin, alle Metriken auf Kundenebene auf der `orders` -Tabelle zu basieren. Bei dieser Einrichtung wird eine eindeutige Kunden-ID verwendet, die alle Kunden besitzen, einschließlich Gäste (normalerweise wird eine Kunden-E-Mail verwendet). Dadurch werden Registrierungsdaten aus der Tabelle `customers` ignoriert. Mit dieser Option werden nur Kunden, die mindestens einen Kauf getätigt haben, in Berichte auf Kundenebene aufgenommen. Registrierte Benutzer, die noch keinen Kauf getätigt haben, sind nicht enthalten. Mit dieser Option basiert Ihre `New customer` -Metrik auf dem ersten Bestelldatum des Kunden in der `orders` -Tabelle.

Sie werden feststellen, dass der `Customers we count`-Filtersatz in diesem Setup-Typ einen Filter für `Customer's order number = 1` aufweist.

![](../../assets/guest-orders-filter-set.png)

In einer Situation ohne Gastaufträge existiert jeder Kunde als eindeutige Zeile in der Kundentabelle (siehe Abbildung 1). Eine Metrik wie `New customers` kann die ID dieser Tabelle einfach anhand des `created\_at` -Datums zählen, um neue Kunden basierend auf dem Registrierungsdatum zu verstehen.

Bei einer Einrichtung von Gastbestellungen, bei der alle Kundenmetriken auf der `orders` -Tabelle basieren, um Gastbestellungen zu berücksichtigen, müssen Sie sicherstellen, dass Sie `not counting customers twice` sind. Wenn Sie die ID der Auftragstabelle zählen, werden alle Bestellungen gezählt. Wenn Sie stattdessen die ID auf der Tabelle `orders` zählen und einen Filter, `Customer's order number = 1`, verwenden, werden Sie jeden Unique Customer `only one time` zählen. Dies gilt für alle Metriken auf Kundenebene wie `Customer's lifetime revenue` oder `Customer's lifetime number of orders`.

Sie können oben sehen, dass die Tabelle `orders` null `customer\_ids` enthält. Wenn Sie mit dem `customer\_email` Unique Customers identifizieren, können Sie sehen, dass `erin@test.com` drei (3) Bestellungen aufgegeben hat. Daher können Sie eine `New customers` -Metrik für Ihre `orders` -Tabelle anhand der folgenden Bedingungen erstellen:

* `Operation table = orders`
* `Operation column = id`
* `Operation = count`
* `Timestamp = Customer's first order date`
* `Filter = Customer's we count (where Customer's order number = 1)`
