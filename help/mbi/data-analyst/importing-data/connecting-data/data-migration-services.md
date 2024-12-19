---
title: Datenmigrations-Services
description: Erfahren Sie alles, was Sie benötigen, um eine Anfrage zu senden und mit der Migration zu beginnen.
exl-id: 105cd003-98ef-4358-80b9-b3190c2c57b7
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---

# Datenmigration

Die Migration auf ein neues Datenbankschema, einen neuen Server oder eine neue Berichtsdatenbank ist nicht zwingend. Das [[!DNL Adobe] Services-Team](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html) bietet Unterstützung bei der Migration.

Um sicherzustellen, dass Ihr Übergang so reibungslos wie möglich verläuft, sollten Sie bei der Übermittlung Ihrer Migrationsanfrage so detailliert wie möglich sein. In diesem Thema finden Sie alles, was Sie zum Senden einer Anfrage und für die ersten Schritte mit der Migration benötigen. Wenn Sie uns ein umfassendes Bild Ihrer Bedürfnisse vermitteln, können Sie sicherstellen, dass Ihr Projekt ordnungsgemäß abgewickelt wird und die Schätzung korrekt ist.

## Erste Schritte {#started}

Bevor Sie beginnen, müssen Sie die Antworten auf diese Fragen kennen:

* **Befindet sich die neue Datenbank auf einem neuen Server?** Bevor Sie eine Anfrage senden, aktualisieren Sie die Einstellungen Ihrer Datenverbindung unter **[!UICONTROL Manage Data** > **Connections]**. Wenn Sie die Vorgehensweise aktualisieren müssen, gehen Sie zum Abschnitt [`Integrations`](../integrations/integrations.md) und finden Sie die Anweisungen für den verwendeten Datenbanktyp.

* **Sind alle historischen Daten in der neuen Datenbank vorhanden oder müssen sie migriert werden?** Sie können die historischen und neuen Daten während des Migrationsprozesses konsolidieren. Auch wenn Sie keine Konsolidierung benötigen, lassen Sie es uns in Ihrer Anfrage wissen.

Nachdem Sie die Antworten auf die obigen Fragen erhalten haben, müssen Sie den Migrationstyp kennen. Verfügt die neue Datenbank über das [`same`](#sameschema) oder über ein [`different`](#newschema)? In den folgenden Diskussionen finden Sie detaillierte Anweisungen für jeden Migrationstyp.

## Migration zu einer neuen Datenbank mit demselben Schema {#sameschema}

Teilen Sie uns beim Senden der Anfrage mit, dass sich das Datenbankschema nicht ändert und dass die Verbindung bereits in [!DNL Adobe Commerce Intelligence] eingerichtet ist.

Wenn die Datenbank einen neuen Namen hat, fügen Sie ihn in die Anfrage ein, damit Ihre Dashboards ordnungsgemäß migriert werden können.

Wenn sich der Datenbankname nicht ändert, ist die Migration abgeschlossen. Dashboards und Berichte werden nach Abschluss der nächsten vollständigen Aktualisierung aktualisiert.

## Migration zu einer neuen Datenbank mit einem anderen Schema {#newschema}

>[!IMPORTANT]
>
>Wenn bestimmte Datenspalten in der neuen Datenbank keine entsprechenden Spalten haben, besteht die Möglichkeit, dass bestimmte Analysen dabei verloren gehen.

Um diesen Migrationstyp erfolgreich abzuschließen, müssen vorhandene Datenspalten mit ihren Entsprechungen in der neuen Datenbank abgeglichen werden. Dies ist nicht obligatorisch, aber die Durchführung des Matching für uns hilft, die Durchlaufzeit Ihrer Anfrage zu beschleunigen und den Preis der Migration zu senken.

Wenn Sie sich beim Abgleichen wohl fühlen, befolgen Sie diese Anweisungen und fügen Sie die fertige Tabelle Ihrer Anfrage hinzu:

1. Überprüfen Sie alle Tabellen und Spalten, die derzeit mit Ihrem Data Warehouse (**[!UICONTROL Manage Data** > **Data Warehouse]**) synchronisiert werden.

1. Erstellen Sie in einem Arbeitsblatt für jede Tabelle, die in die neue Datenbank migriert werden soll, eine Registerkarte.

1. Erstellen Sie auf jeder Registerkarte eine Spalte für alle vorhandenen Spalten, die migriert werden müssen. Adobe empfiehlt, ihn so zu benennen wie `Existing column name`.

1. Außerdem müssen Sie auf jeder Registerkarte des Arbeitsblatts eine weitere Spalte für die Spaltenäquivalente in der neuen Datenbank erstellen. Adobe empfiehlt, die Spalte so zu benennen wie `New column name`.

1. Geben Sie die vorhandenen Spalten und ihre Entsprechungen ein. Wenn eine vorhandene Spalte keine neue Entsprechung hat, geben Sie `N/A` ein.

   Wenn es eine neue Möglichkeit gibt, dieselben Informationen in der neuen Datenbank zu berechnen, geben Sie sie in die Spalte [`New column name`] ein.

Im Folgenden finden Sie ein Beispiel:

![](../../../assets/Migration_Spreadsheet.png)

>[!NOTE]
>
>Wenn bestimmte Datenspalten in der neuen Datenbank keine entsprechenden Spalten haben, besteht die Möglichkeit, dass bestimmte Analysen dabei verloren gehen.

## Wie sende ich eine Anfrage? {#submitreq}

Sie können sich an uns wenden, indem Sie [eine Support-Anfrage einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

Vergessen Sie nicht, die Tabelle anzuhängen, wenn Sie die Schritte aus dem vorherigen Abschnitt zum Erstellen der Tabelle mit Spaltenanpassung befolgt haben.

## Wie geht es weiter? {#wrapup}

Um den Umfang des Projekts zu bestimmen, ist eine Zusammenarbeit zwischen Ihnen und dem Analyst aus dem Commerce Services-Team, das die Migration durchführt, erforderlich. Die Komplexität der Änderungen und die Reaktionsfähigkeit von Ihnen und dem Analysten wirken sich direkt auf die Dauer der Migration aus. Nachdem Sie die Details festgehalten haben, wird ein Zeitplan erstellt und mit einer Leistungsbeschreibung an Sie gesendet.
