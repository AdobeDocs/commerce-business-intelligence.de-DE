---
title: Verwalten von Benutzern und Berechtigungen
description: Erfahren Sie, wie Sie Ihre [!DNL MBI] Benutzer.
exl-id: 2a5eeabb-3c13-4ca1-b845-ed255b389c9f
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Verwalten von Benutzerberechtigungen

MBI soll in Ihrer Organisation eine einzige Quelle der Wahrheit sein. Jeder Benutzer verfügt über einen eigenen Satz von Dashboards, die er [Freigabe für andere Benutzer](../../data-user/dashboards/share-dashboard-with-users.md).

## Benutzerberechtigungsebenen

In [!DNL MBI]gibt es drei allgemeine Berechtigungsebenen, die für Benutzer gelten und bei der Erstellung eines Kontos ausgewählt werden:

* `Admin`
* `Standard`
* `Read-Only`

Mit diesen Berechtigungen können Benutzer bestimmte Aktionen durchführen oder auf bestimmte Teile von [!DNL MBI]. Im Folgenden finden Sie eine Tabelle der Möglichkeiten, die die einzelnen Berechtigungsebenen in MBI bieten:

|  | `Admin` | `Standard` | `Read Only` |
| -----|-----|-----|----|
| **Benutzer erstellen/verwalten** | ✔ |  |  |
| **E-Mail-Zusammenfassungen erstellen** | ✔ | ✔ |  |
| **Dashboards erstellen/bearbeiten/freigeben** | ✔ | ✔ |  |
| **Anzeigen von Dashboards** | ✔ | ✔ | ✔ |
| **Erstellen/Bearbeiten/Löschen visueller Berichte** | ✔ | ✔* |  |
| **SQL-Berichte erstellen/bearbeiten/löschen** | ✔ |  |  |
| **Dashboards klonen** | ✔ |  |  |
| **Integrationen hinzufügen/verwalten** | ✔ |  |  |
| **Zugriff auf Data Warehouse Manager** | ✔ |  |  |
| **Synchronisieren/Aufheben der Synchronisierung von Tabellen und Spalten** | ✔ |  |  |
| **Erstellen/Bearbeiten von Metriken** | ✔ |  |  |
| **Erstellen und Bearbeiten von Filtersätzen** | ✔ |  |  |
| **Berechnete Spalten erstellen/bearbeiten** | ✔ |  |  |
| **Liste der abhängigen Berichte erstellen** | ✔ |  |  |
| **Zugriffssystemzusammenfassung** | ✔ |  |  |
| **Zeitzoneneinstellungen aufrufen** | ✔ |  |  |
| **Abrechnung des Zugriffs** | ✔ | ✔** |  |
| **Support kontaktieren** | ✔ | ✔ | ✔ |

{style="table-layout:auto"}

>[!NOTE]
>
>_Sie können eine **[!UICONTROL Standard]**des Benutzers [Zugriff auf bestimmte Metriken](../../administrator/user-management/restrict-metric-access.md)._
>
>**[!UICONTROL Standard] _-Benutzer können mit einer zusätzlichen Berechtigungseinstellung auf die Abrechnung zugreifen._
>
>**[!UICONTROL Read-Only]** Benutzer können nur _Ansicht_ Dashboards, die für sie freigegeben wurden; Sie können keine Elemente in erstellen oder bearbeiten [!DNL MBI], noch können sie nach neuen Dashboards suchen und zu ihrem Konto hinzufügen. Adobe empfiehlt, einen bestimmten Satz von Dashboards für **[!UICONTROL Read-Only]** Benutzer, die Sie oder ein anderes Mitglied Ihres Teams unterhalten. Klonen Sie keine Dashboards.

## Zusätzliche Berechtigungen: Rechnungsstellung und technische {#billingtech}

Neben den allgemeinen Berechtigungsstufen gibt es auch zwei weitere Benutzerbezeichnungen: `Billing` und `Technical`. Diese Bezeichnungen sollten mit den allgemeinen Berechtigungsstufen verwendet werden.

### Rechnungsstellung

`Billing` -Benutzer haben Zugriff auf die Rechnungsseite und können Zahlungsinformationen ändern. Sie können auch von Adobe für Abrechnungsfragen kontaktiert werden.

`Admin` -Benutzer haben Zugriff auf `Billing` standardmäßig, aber `Standard` Benutzer können auch darauf zugreifen, wenn sie `Billing` in ihrem Profil aktiviert wurde.

![Abrechnung](../../assets/billing.png)<!--{: width="550" height="363"}-->

### Technisch

`Technical` -Benutzer haben keine spezifischen Berechtigungen. Mit dieser Einstellung wird nur ein technischer Kontakt innerhalb Ihres Unternehmens gekennzeichnet. Bei technischen Fragen wenden Sie sich bitte an diese Anwender.

`Admin` Benutzer können ihrem Konto neue Benutzer hinzufügen, indem sie auf **[!UICONTROL Account Settings]** > **[!UICONTROL Create Users]** und den Eingabeaufforderungen folgen. Nachdem der Benutzer in [!DNL MBI], erhält die Glückliche, die Sie einladen, E-Mail-Anweisungen zum Abschluss des Kontoeinrichtungsprozesses.

Sie können jederzeit `Admins` Alle Benutzer in ihrem Konto durch Klicken auf **[!UICONTROL Account Settings]** > **[!UICONTROL Manage Users]**. Auf dieser Seite werden die Berechtigungen des Benutzers sowie die Metriken und Dashboards angezeigt, auf die er zugreifen kann.
