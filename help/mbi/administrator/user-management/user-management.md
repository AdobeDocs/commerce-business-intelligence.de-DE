---
title: Verwalten von Adobe Commerce-Benutzern und -Berechtigungen
description: Erfahren Sie, wie Sie Ihre Commerce Intelligence-Benutzer verwalten.
exl-id: 2a5eeabb-3c13-4ca1-b845-ed255b389c9f
role: Admin, User
feature: User Management
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Verwalten von Benutzerberechtigungen

[!DNL Adobe Commerce Intelligence] ist als eine einzige Quelle der Wahrheit in Ihrer Organisation gedacht. Jeder Benutzer verfügt über einen eigenen Satz von Dashboards, die er [für andere Benutzer freigeben kann](../../data-user/dashboards/share-dashboard-with-users.md).

## Benutzerberechtigungsebenen

In [!DNL Commerce Intelligence] gibt es drei allgemeine Berechtigungsebenen, die für Benutzer gelten und bei der Erstellung eines Kontos ausgewählt werden:

* `Admin`
* `Standard`
* `Read-Only`

Mit diesen Berechtigungen können Benutzer bestimmte Aktionen durchführen oder auf bestimmte Teile von [!DNL Commerce Intelligence] zugreifen. Die folgende Tabelle zeigt, was die einzelnen Berechtigungsebenen in [!DNL Commerce Intelligence] tun können:

|   | `Admin` | `Standard` | `Read Only` |
| -----|-----|-----|----|
| **Benutzer erstellen/verwalten** | ms |   |   |
| **E-Mail-Zusammenfassungen erstellen** | ms | ms |   |
| **Dashboards erstellen/bearbeiten/freigeben** | ms | ms |   |
| **Anzeigen von Dashboards** | ms | ms | ms |
| **Erstellen/Bearbeiten/Löschen visueller Berichte** | ms | * |   |
| **SQL-Berichte erstellen/bearbeiten/löschen** | ms |  |   |
| **Dashboards klonen** | ms |   |   |
| **Integrationen hinzufügen/verwalten** | ms |   |   |
| **Zugriff auf den Data Warehouse-Manager** | ms |   |   |
| **Synchronisieren/Aufheben der Synchronisierung von Tabellen und Spalten** | ms |   |   |
| **Erstellen/Bearbeiten von Metriken** | ms |   |   |
| **Erstellen/Bearbeiten von Filtersätzen** | ms |   |   |
| **Berechnete Spalten erstellen/bearbeiten** | ms |   |   |
| **Liste der abhängigen Berichte erstellen** | ms |   |   |
| **Systemzusammenfassung aufrufen** | ms |   |   |
| **Zugriff auf Zeitzoneneinstellungen** | ms |   |   |
| **Zugriff auf Abrechnung** | ms | * |   |
| **Support kontaktieren** | ms | ms | ms |

{style="table-layout:auto"}

>[!NOTE]
>
>_Sie können den [ -Zugriff eines **[!UICONTROL Standard]**Benutzers auf bestimmte Metriken beschränken](../../administrator/user-management/restrict-metric-access.md)._
>
>**[!UICONTROL Standard] _Benutzer können mit einer zusätzlichen Berechtigungseinstellung auf die Abrechnung zugreifen._
>
>**[!UICONTROL Read-Only]** Benutzer können nur Dashboards anzeigen, die für sie freigegeben wurden. Sie können keine Dashboards in [!DNL Commerce Intelligence] erstellen oder bearbeiten. Sie können auch keine neuen Dashboards suchen und zu ihrem Konto hinzufügen. __ Adobe empfiehlt, einen bestimmten Satz von Dashboards für **[!UICONTROL Read-Only]** -Benutzer freizugeben, den Sie oder ein anderes Team-Mitglied verwalten. Klonen Sie keine Dashboards.

## Zusätzliche Berechtigungen: Rechnungsstellung und technische {#billingtech}

Zusätzlich zu den allgemeinen Berechtigungsstufen gibt es auch zwei weitere Benutzerbezeichnungen: `Billing` und `Technical`. Diese Bezeichnungen sollten mit den allgemeinen Berechtigungsstufen verwendet werden.

### Rechnungsstellung

`Billing` -Benutzer haben Zugriff auf die Rechnungsseite und können Zahlungsinformationen ändern. Sie können auch von Adobe für Abrechnungsfragen kontaktiert werden.

`Admin` -Benutzer haben standardmäßig Zugriff auf die Registerkarte `Billing` , aber `Standard` -Benutzer können auch Zugriff erhalten, wenn in ihrem Profil das Kontrollkästchen `Billing` aktiviert ist.

![billing](../../assets/billing.png)<!--{: width="550" height="363"}-->

### Technisch

`Technical` -Benutzer haben keine spezifischen Berechtigungen. Diese Einstellung kennzeichnet nur einen technischen Kontakt innerhalb Ihrer Organisation. Diese Benutzer werden von Adobe unter Umständen bei technischen Fragen kontaktiert.

`Admin` -Benutzer können neue Benutzer zu ihrem Konto hinzufügen, indem sie auf **[!UICONTROL Account Settings]** > **[!UICONTROL Create Users]** klicken und den Anweisungen folgen. Nachdem der Benutzer in [!DNL Commerce Intelligence] erstellt wurde, erhält die glückliche Person, die Sie einladen, E-Mail-Anweisungen zum Abschluss des Kontoeinrichtungsprozesses.

`Admins` kann jederzeit alle Benutzer in ihrem Konto anzeigen, indem er auf **[!UICONTROL Account Settings]** > **[!UICONTROL Manage Users]** klickt. Auf dieser Seite werden die Berechtigungen des Benutzers sowie die Metriken und Dashboards angezeigt, auf die er zugreifen kann.
