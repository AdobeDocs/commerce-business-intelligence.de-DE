---
title: Datenmigrationsdienste
description: Hier erfahren Sie alles, was Sie zum Senden einer Anfrage und zum Einstieg in die Migration benötigen.
exl-id: 105cd003-98ef-4358-80b9-b3190c2c57b7
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# Datenmigration

Die Migration zu einem neuen Datenbankschema, Server oder Reporting-Datenbank muss nicht aufwändig sein. Die **[!DNL Adobe Commerce Services - Analytics]** Team bietet Unterstützung bei der Migration.

Um sicherzustellen, dass Ihre Umstellung so reibungslos wie möglich verläuft, sollten Sie beim Senden Ihrer Migrationsanfrage so detailliert wie möglich sein. In diesem Artikel finden Sie alles, was Sie benötigen, um eine Anfrage zu senden und mit der Migration zu beginnen. Durch ein umfassendes Bild Ihrer Bedürfnisse können Sie sicherstellen, dass Ihr Projekt richtig erfasst wird und dass die Schätzung korrekt ist.

## Erste Schritte {#started}

Bevor Sie beginnen, müssen Sie die Antworten auf diese Fragen kennen:

* **Befindet sich die neue Datenbank auf einem neuen Server?** Aktualisieren Sie vor dem Senden einer Anfrage die Einstellungen Ihrer Datenverbindung unter **[!UICONTROL Manage Data** > **Connections]**. Wenn Sie einen Auffrischungskurs dazu benötigen, gehen Sie zu [`Integrations`](../integrations/integrations.md) und finden Sie die Anweisungen für den verwendeten Datenbanktyp.
* **Sind Ihre historischen Daten in der neuen Datenbank vorhanden oder müssen sie migriert werden?** Sie können die historischen und neuen Daten während des Migrationsprozesses konsolidieren. Auch wenn Sie keine Konsolidierung benötigen, teilen Sie uns dies in Ihrer Anfrage mit.

Nachdem Sie die oben genannten Antworten erhalten haben, müssen Sie den Migrationstyp kennen: wird die neue Datenbank über die [`same`](#sameschema) Schema oder wird es über ein [`different`](#newschema) schema? In den folgenden Abschnitten finden Sie detaillierte Anweisungen für jeden Migrationstyp.

## Migration zu einer neuen Datenbank mit demselben Schema {#sameschema}

Teilen Sie uns beim Senden der Anfrage mit, dass sich das Datenbankschema nicht ändert und die Verbindung bereits in [!DNL MBI].

Wenn die Datenbank einen neuen Namen aufweist, fügen Sie ihn in die Anfrage ein, damit Ihre Dashboards ordnungsgemäß migriert werden können.

Wenn sich der Datenbankname nicht ändert, ist die Migration abgeschlossen. Dashboards und Berichte werden aktualisiert, nachdem die nächste vollständige Aktualisierung abgeschlossen ist. Wenden Sie sich an die Adobe, damit Sie alle Probleme, die sich aus der Migration ergeben könnten, kennen lernen können.

## Migration zu einer neuen Datenbank mit einem anderen Schema {#newschema}

>[!IMPORTANT]
>
>Wenn bestimmte Datenspalten nicht über äquivalente Spalten in der neuen Datenbank verfügen, kann es vorkommen, dass bestimmte Analysen im Prozess verloren gehen.

Um diese Art der Migration erfolgreich abzuschließen, müssen vorhandene Datenspalten mit den entsprechenden Elementen in der neuen Datenbank abgeglichen werden. Dies ist nicht obligatorisch, aber die Durchführung der Abstimmung für uns hilft, die Umkehrzeit Ihrer Anfrage zu beschleunigen und den Preis der Migration zu senken.

Wenn Sie die Zuordnung selbst vornehmen möchten, befolgen Sie diese Anweisungen und fügen Sie das fertige Arbeitsblatt an Ihre Anfrage an:

1. Überprüfen Sie alle Tabellen und Spalten, die derzeit mit Ihrer Data Warehouse synchronisiert werden (**[!UICONTROL Manage Data** > **Data Warehouse]**).
1. Erstellen Sie in einer Tabelle eine Registerkarte für jede Tabelle, die in die neue Datenbank migriert werden soll.
1. Erstellen Sie in jeder Registerkarte eine Spalte für alle vorhandenen Spalten, die migriert werden müssen. Adobe empfiehlt die Benennung in etwa wie folgt: `Existing column name`.
1. Außerdem müssen Sie in jedem Tab des Arbeitsblatts eine weitere Spalte für die Spaltenäquivalente in der neuen Datenbank erstellen. Adobe empfiehlt, die Spalte in etwa wie folgt zu benennen: `New column name`.
1. Geben Sie die vorhandenen Spalten und ihre Entsprechungen ein. Wenn eine vorhandene Spalte keine neue Entsprechung hat, geben Sie `N/A`.

   Wenn es eine neue Möglichkeit gibt, dieselben Informationen in der neuen Datenbank zu berechnen, geben Sie sie auch in die [`New column name`] Spalte.

Im Folgenden finden Sie ein Beispiel:

![](../../../assets/Migration_Spreadsheet.png)

>[!NOTE]
>
>Wenn bestimmte Datenspalten nicht über äquivalente Spalten in der neuen Datenbank verfügen, kann es vorkommen, dass bestimmte Analysen im Prozess verloren gehen.

## Wie sende ich eine Anfrage? {#submitreq}

Sie können uns kontaktieren, indem Sie [Support anfordern](../../../guide-overview.md).

Wenn Sie die Schritte im vorherigen Abschnitt zur Erstellung des Spaltenabgleichs-Arbeitsblatts ausgeführt haben, sollten Sie dieses anhängen.

## Wie geht es weiter? {#wrapup}

Die Bestimmung des Umfangs des Projekts erfordert eine gewisse Zusammenarbeit zwischen Ihnen und dem Analysten des für die Migration zuständigen Teams von Commerce Services. Die Komplexität der Änderungen und die Reaktionsfähigkeit von Ihnen und dem Analysten wirken sich direkt auf die Dauer der Migration aus. Nachdem Sie die Details aufgeschlüsselt haben, wird eine Zeitleiste erstellt und Ihnen mit einer Arbeitserklärung übermittelt.
