---
title: Gastaufträge
description: Erfahren Sie mehr über die Auswirkungen von Gastaufträgen auf Ihre Daten und welche Optionen Sie für Gastaufträge in Ihren [!DNL Commerce Intelligence] Data Warehouse.
exl-id: cd5120ca-454c-4cf4-acb4-3aebe06cdc9a
role: Admin, Data Architect, Data Engineer, User
feature: Data Import/Export, Data Integration, Data Warehouse Manager, Commerce Tables
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Gastbestellungen

Wenn Sie bei der Überprüfung Ihrer Bestellungen feststellen, dass viele `customer\_id` -Werte null sind oder keinen Wert haben, der zum `customers` -Tabelle, ist dies ein Hinweis darauf, dass Ihr Store Gastbestellungen zulässt. Das bedeutet, dass Ihre `customers` -Tabelle ist höchstwahrscheinlich nicht alle Ihre Kunden eingeschlossen.

In diesem Thema werden die Auswirkungen von Gastaufträgen auf Ihre Daten und die Optionen erläutert, die Sie für Gastaufträge in Ihren [!DNL Commerce Intelligence] Data Warehouse.

## Auswirkung von Gastaufträgen auf Daten

In der typischen Commerce-Datenbank gibt es eine `orders` Tabelle, die mit einer `customers` Tabelle. Jede Zeile auf der `orders` -Tabelle enthält `customer\_id` -Spalte, die für eine Zeile auf der `customers` Tabelle.

* **Wenn alle Kunden registriert sind** und Gastaufträge sind nicht zulässig. Das bedeutet, dass jeder Datensatz in der Variablen `orders` -Tabelle einen Wert im `customer\_id` Spalte. Dadurch wird jede Bestellung wieder zum `customers` Tabelle.

  ![](../../assets/guest-orders-4.png)

* **Wenn Gastaufträge zulässig sind** bedeutet dies, dass einige Bestellungen keinen Wert im `customer\_id` Spalte. Nur registrierte Kunden erhalten einen Wert für `customer\_id` in der Spalte `orders` Tabelle. Kunden, die nicht registriert sind, erhalten eine `NULL` (oder leer) für diese Spalte. Daher weisen nicht alle Bestelldatensätze übereinstimmende Datensätze in der `customers` Tabelle.

  >[!NOTE]
  >
  >Um die eindeutige Person zu identifizieren, die die Bestellung aufgegeben hat, muss ein anderes eindeutiges Benutzerattribut vorhanden sein. `customer\_id` an eine Bestellung angehängt. In der Regel wird die E-Mail-Adresse des Kunden verwendet.

## Wie werden Gastaufträge bei der Data Warehouse-Einrichtung berücksichtigt?

Normalerweise berücksichtigt der Sales Engineer, der Ihr Konto implementiert, Gastaufträge bei der Erstellung der Grundlage Ihrer Data Warehouse.

Die optimale Methode zur Berücksichtigung von Gastbestellungen besteht darin, alle Kundenmetriken auf der Grundlage der `orders` Tabelle. Bei dieser Einrichtung wird eine eindeutige Kunden-ID verwendet, die alle Kunden besitzen, einschließlich Gäste (normalerweise wird eine Kunden-E-Mail verwendet). Dadurch werden Registrierungsdaten aus der `customers` Tabelle. Mit dieser Option werden nur Kunden, die mindestens einen Kauf getätigt haben, in Berichte auf Kundenebene aufgenommen. Registrierte Benutzer, die noch keinen Kauf getätigt haben, sind nicht enthalten. Mit dieser Option wird Ihre `New customer` -Metrik basiert auf dem ersten Bestelldatum des Kunden in der `orders` Tabelle.

Sie werden feststellen, dass die Variable `Customers we count` Filtersatz in dieser Art von Einrichtung hat einen Filter für `Customer's order number = 1`.

![](../../assets/guest-orders-filter-set.png)

In einer Situation ohne Gastaufträge existiert jeder Kunde als eindeutige Zeile in der Kundentabelle (siehe Abbildung 1). Eine Metrik wie `New customers` kann einfach die ID dieser Tabelle basierend auf `created\_at` Datum, um neue Kunden basierend auf dem Registrierungsdatum zu verstehen.

Bei einer Einrichtung für Gastbestellungen, bei der alle Kundenmetriken auf der `orders` -Tabelle, um Gastbestellungen zu berücksichtigen, müssen Sie sicherstellen, dass Sie `not counting customers twice`. Wenn Sie die ID der Auftragstabelle zählen, werden alle Bestellungen gezählt. Wenn Sie stattdessen die ID auf der `orders` Tabelle erstellen und einen Filter verwenden, `Customer's order number = 1`, werden Sie jeden Unique Customer zählen `only one time`. Dies gilt für alle Metriken auf Kundenebene, z. B. `Customer's lifetime revenue` oder `Customer's lifetime number of orders`.

Sie können oben sehen, dass null vorhanden ist. `customer\_ids` im `orders` Tabelle. Wenn Sie die `customer\_email` um Unique Customers zu identifizieren, können Sie sehen, dass `erin@test.com` hat drei (3) Bestellungen aufgegeben. Daher können Sie eine `New customers` Metrik auf Ihrer `orders` -Tabelle anhand der folgenden Bedingungen:

* `Operation table = orders`
* `Operation column = id`
* `Operation = count`
* `Timestamp = Customer's first order date`
* `Filter = Customer's we count (where Customer's order number = 1)`
