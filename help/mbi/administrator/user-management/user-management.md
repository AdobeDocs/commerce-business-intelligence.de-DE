---
title: Verwalten von Adobe Commerce-Benutzern und -Berechtigungen
description: Erfahren Sie, wie Sie Ihre Commerce Intelligence-Benutzenden verwalten.
exl-id: 2a5eeabb-3c13-4ca1-b845-ed255b389c9f
role: Admin, User
feature: User Management
TQID: https://experienceleague.adobe.com/T3ZdoQW35n6CAJmDlOlfDVSI1eUA--e4RKZbOMF1BWY
product_v2: id: cc9c1b69-d771-4a04-84d3-df2e3989418fid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b0c4e988-b173-423f-88d4-345071a0bce8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: db7e4a13f32f02292f9c33d8d7d942461fea4bb4
workflow-type: tm+mt
source-wordcount: 406
ht-degree: 0%

---

# Verwalten von Benutzerberechtigungen

[!DNL Adobe Commerce Intelligence] soll in Ihrer gesamten Organisation als zentrale Datenquelle dienen. Jeder Benutzer verfügt über einen eigenen Satz von Dashboards, die er [für andere Benutzer freigeben](../../data-user/dashboards/share-dashboard-with-users.md).

## Berechtigungsebenen des Benutzers

In [!DNL Commerce Intelligence] gibt es drei allgemeine Berechtigungsebenen, die für Benutzende gelten und die beim Erstellen eines Kontos ausgewählt werden:

* `Admin`
* `Standard`
* `Read-Only`

Diese Berechtigungen ermöglichen es Benutzenden, bestimmte Aktionen auszuführen oder auf bestimmte Teile von [!DNL Commerce Intelligence] zuzugreifen. Im Folgenden finden Sie eine Tabelle, was jede Berechtigungsstufe in [!DNL Commerce Intelligence] tun kann:

|   | `Admin` | `Standard` | `Read Only` |
| -----|-----|-----|----|
| **Benutzer erstellen/verwalten** | ✔ |   |   |
| **E-Mail-Zusammenfassungen erstellen** | ✔ | ✔ |   |
| **Erstellen/Bearbeiten/Freigeben von Dashboards** | ✔ | ✔ |   |
| **Anzeigen von Dashboards** | ✔ | ✔ | ✔ |
| **Visuelle Berichte erstellen/bearbeiten/löschen** | ✔ | ✔* |   |
| **SQL-Berichte erstellen/bearbeiten/löschen** | ✔ |  |   |
| **Klonen von Dashboards** | ✔ |   |   |
| **Integrationen hinzufügen/verwalten** | ✔ |   |   |
| **Zugriff auf Data Warehouse Manager** | ✔ |   |   |
| **Synchronisieren/Synchronisieren von Tabellen und Spalten** | ✔ |   |   |
| **Metriken erstellen/bearbeiten** | ✔ |   |   |
| **Filtersätze erstellen/bearbeiten** | ✔ |   |   |
| **Berechnete Spalten erstellen/bearbeiten** | ✔ |   |   |
| **Liste abhängiger Berichte erstellen** | ✔ |   |   |
| **Zugriff auf die Systemübersicht** | ✔ |   |   |
| **Zugriff auf Zeitzoneneinstellungen** | ✔ |   |   |
| **Zugriffsabrechnung** | ✔ | ✔** |   |
| **Support kontaktieren** | ✔ | ✔ | ✔ |

{style="table-layout:auto"}

>[!NOTE]
>
>_Sie können den Zugriff eines **[!UICONTROL Standard]**Benutzers [auf bestimmte Metriken) ](../../administrator/user-management/restrict-metric-access.md)._
>
>**[!UICONTROL Standard] _Benutzer können über eine zusätzliche Berechtigungseinstellung auf Abrechnung zugreifen._
>
>**[!UICONTROL Read-Only]** Benutzer können nur Dashboards _anzeigen_ die für sie freigegeben wurden. Sie können in [!DNL Commerce Intelligence] nichts erstellen oder bearbeiten und auch nicht nach neuen Dashboards suchen und zu ihrem Konto hinzufügen. Adobe empfiehlt, einen bestimmten Satz von Dashboards für **[!UICONTROL Read-Only]** Benutzer freizugeben, die Sie oder ein anderes Teammitglied verwalten. Klonen Sie keinen Satz von Dashboards für sie.

## Zusätzliche Berechtigungen: Abrechnung und technische {#billingtech}

Neben den allgemeinen Berechtigungsebenen gibt es auch zwei weitere Benutzerbezeichnungen: `Billing` und `Technical`. Diese Bezeichnungen sollten zusammen mit den allgemeinen Berechtigungsebenen verwendet werden.

### Fakturierung

`Billing` Benutzer haben Zugriff auf die Seite Abrechnung und können Zahlungsinformationen ändern. Sie können auch von Adobe kontaktiert werden, wenn Sie Fragen zur Rechnungsstellung haben.

`Admin` Benutzer haben standardmäßig Zugriff auf die Registerkarte `Billing` . `Standard` Benutzer können jedoch auch Zugriff erhalten, wenn sie in ihrem Profil das Kontrollkästchen `Billing` aktiviert haben.

![Abrechnungsseite](../../assets/billing.png)<!--{: width="550" height="363"}-->

### Technisch

`Technical` Benutzer haben keine spezifischen Berechtigungen für sie. Mit dieser Einstellung wird nur ein technischer Kontakt innerhalb Ihrer Organisation markiert. Diese Benutzenden können von Adobe bei technischen Fragen kontaktiert werden.

`Admin` Benutzer können neue Benutzer zu ihrem Konto hinzufügen, indem sie auf **[!UICONTROL Account Settings]** > **[!UICONTROL Create Users]** klicken und die entsprechenden Anweisungen befolgen. Nachdem der Benutzer in [!DNL Commerce Intelligence] erstellt wurde, erhält die glückliche Person, die Sie einladen, E-Mail-Anweisungen zum Abschließen des Prozesses zur Kontoeinrichtung.

`Admins` können jederzeit alle Benutzer in ihrem Konto anzeigen, indem Sie auf **[!UICONTROL Account Settings]** > **[!UICONTROL Manage Users]** klicken. Auf dieser Seite werden die Berechtigungen der Benutzenden und die Metriken und Dashboards angezeigt, auf die sie zugreifen können.
