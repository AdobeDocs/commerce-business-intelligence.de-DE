---
title: Verwalten von Adobe Commerce-Benutzern und -Berechtigungen
description: Erfahren Sie, wie Sie Ihre Commerce Intelligence-Benutzer verwalten.
exl-id: 2a5eeabb-3c13-4ca1-b845-ed255b389c9f
role: Admin, User
feature: User Management
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Verwalten von Benutzerberechtigungen

[!DNL Adobe Commerce Intelligence] soll in Ihrer Organisation eine einzige Quelle der Wahrheit sein. Jeder Benutzer verfügt über einen eigenen Satz von Dashboards, die er [Freigabe für andere Benutzer](../../data-user/dashboards/share-dashboard-with-users.md).

## Benutzerberechtigungsebenen

In [!DNL Commerce Intelligence]gibt es drei allgemeine Berechtigungsebenen, die für Benutzer gelten und bei der Erstellung eines Kontos ausgewählt werden:

* `Admin`
* `Standard`
* `Read-Only`

Mit diesen Berechtigungen können Benutzer bestimmte Aktionen durchführen oder auf bestimmte Teile von [!DNL Commerce Intelligence]. Die folgende Tabelle zeigt, was die einzelnen Berechtigungsebenen in [!DNL Commerce Intelligence]:

|   | `Admin` | `Standard` | `Read Only` |
| -----|-----|-----|----|
| **Benutzer erstellen/verwalten** | ms |   |   |
| **E-Mail-Zusammenfassungen erstellen** | ✔ | ✔ |   |
| **Dashboards erstellen/bearbeiten/freigeben** | ✔ | ✔ |   |
| **Anzeigen von Dashboards** | ✔ | ✔ | ✔ |
| **Erstellen/Bearbeiten/Löschen visueller Berichte** | ✔ | ✔* |   |
| **SQL-Berichte erstellen/bearbeiten/löschen** | ✔ |  |   |
| **Dashboards klonen** | ✔ |   |   |
| **Integrationen hinzufügen/verwalten** | ✔ |   |   |
| **Zugriff auf Data Warehouse Manager** | ✔ |   |   |
| **Synchronisieren/Aufheben der Synchronisierung von Tabellen und Spalten** | ✔ |   |   |
| **Erstellen/Bearbeiten von Metriken** | ✔ |   |   |
| **Erstellen und Bearbeiten von Filtersätzen** | ✔ |   |   |
| **Berechnete Spalten erstellen/bearbeiten** | ✔ |   |   |
| **Liste der abhängigen Berichte erstellen** | ✔ |   |   |
| **Zugriffssystemzusammenfassung** | ✔ |   |   |
| **Zeitzoneneinstellungen aufrufen** | ✔ |   |   |
| **Zugriffsabrechnung** | ✔ | ✔** |   |
| **Support kontaktieren** | ✔ | ✔ | ✔ |

{style="table-layout:auto"}

>[!NOTE]
>
>_Sie können eine **[!UICONTROL Standard]**des Benutzers [Zugriff auf bestimmte Metriken](../../administrator/user-management/restrict-metric-access.md)._
>
>**[!UICONTROL Standard] _-Benutzer können mit einer zusätzlichen Berechtigungseinstellung auf die Abrechnung zugreifen._
>
>**[!UICONTROL Read-Only]** Benutzer können nur _Ansicht_ Dashboards, die für sie freigegeben wurden; sie können keine Elemente in erstellen oder bearbeiten [!DNL Commerce Intelligence], noch können sie nach neuen Dashboards suchen und zu ihrem Konto hinzufügen. Adobe empfiehlt, einen bestimmten Satz von Dashboards für **[!UICONTROL Read-Only]** Benutzer, die Sie oder ein anderes Mitglied Ihres Teams unterhalten. Klonen Sie keine Dashboards.

## Zusätzliche Berechtigungen: Rechnungsstellung und technische {#billingtech}

Neben den allgemeinen Berechtigungsstufen gibt es auch zwei weitere Benutzerbezeichnungen: `Billing` und `Technical`. Diese Bezeichnungen sollten mit den allgemeinen Berechtigungsstufen verwendet werden.

### Rechnungsstellung

`Billing` -Benutzer haben Zugriff auf die Rechnungsseite und können Zahlungsinformationen ändern. Sie können auch von Adobe für Abrechnungsfragen kontaktiert werden.

`Admin` -Benutzer haben Zugriff auf `Billing` standardmäßig, aber `Standard` Benutzer können auch darauf zugreifen, wenn sie `Billing` aktivieren, das für das jeweilige Profil ausgewählt wurde.

![Abrechnung](../../assets/billing.png)<!--{: width="550" height="363"}-->

### Technisch

`Technical` -Benutzer haben keine spezifischen Berechtigungen. Mit dieser Einstellung wird nur ein technischer Kontakt innerhalb Ihres Unternehmens gekennzeichnet. Diese Benutzer werden von Adobe unter Umständen bei technischen Fragen kontaktiert.

`Admin` Benutzer können ihrem Konto neue Benutzer hinzufügen, indem sie auf **[!UICONTROL Account Settings]** > **[!UICONTROL Create Users]** und den Eingabeaufforderungen folgen. Nachdem der Benutzer in [!DNL Commerce Intelligence], erhält die Glückliche, die Sie einladen, E-Mail-Anweisungen zum Abschluss des Kontoeinrichtungsprozesses.

jederzeit `Admins` Alle Benutzer in ihrem Konto durch Klicken auf **[!UICONTROL Account Settings]** > **[!UICONTROL Manage Users]**. Auf dieser Seite werden die Berechtigungen des Benutzers sowie die Metriken und Dashboards angezeigt, auf die er zugreifen kann.
