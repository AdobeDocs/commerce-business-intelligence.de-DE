---
title: Löschen Ihres [!DNL Commerce Intelligence] Kontos
description: Erfahren Sie, wie Sie Ihr [!DNL Commerce Intelligence] Konto bereinigen.
exl-id: 5fcdac2d-41ca-4011-b646-a699d9ecc6e4
role: Admin, User
feature: Accounts
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 0%

---

# Bereinigen Sie Ihr [!DNL Adobe Commerce Intelligence]-Konto.

Unabhängig davon, ob Sie seit sechs Monaten oder sechs Jahren mit [!DNL Commerce Intelligence] arbeiten, ist die Verwaltung eines ordentlichen Kontos von größter Bedeutung, damit Ihr Unternehmen die Plattform optimal nutzen kann. Im Laufe der Zeit ist es natürlich, dass es Benutzer, Dashboards, Berichte, Metriken und Spalten gibt, die nicht mehr benötigt werden. Vielleicht haben Sie einen Bericht für die einmalige Verwendung erstellt und ihn vergessen, oder ein Benutzer, der Ihr Unternehmen verlassen hat, hat sein Konto nie deaktiviert.

Mit [standardisierter, eindeutiger Benennung für alle Elemente](../best-practices/naming-elements.md)) Ihres [!DNL Commerce Intelligence]-Kontos können Sie mit den nachfolgenden Kontoprüfungsschritten die Übersichtlichkeit und unnötige Analysen für Ihre Benutzer reduzieren. Ein weiterer Vorteil besteht darin, dass [potenziell schnellere Aktualisierungszyklen](../best-practices/reduce-update-cycle-time.md) erzielt werden können.

## Schritt 1: Identifizieren Ihrer nicht aktiven Benutzer

Der erste Schritt bei der Bereinigung Ihres Kontos besteht darin, die Konten Ihrer nicht aktiven Benutzer zu deaktivieren, z. B. Personen, die das Unternehmen verlassen haben oder [!DNL Commerce Intelligence] nicht mehr in ihren aktuellen Rollen verwenden.

Klicken Sie dazu in der Navigationsleiste oben rechts auf den Namen Ihres Unternehmens und wählen Sie dann **[!UICONTROL Manage Users]** aus. Wählen Sie als Nächstes den Benutzer aus, den Sie deaktivieren möchten, und klicken Sie auf **[!UICONTROL Deactivate User]**.

>[!NOTE]
>
>Dazu benötigen Sie [Administratorberechtigungen](../administrator/user-management/user-management.md).

>[!WARNING]
>
>Durch das Deaktivieren eines Benutzers werden die Diagramme, Dashboards und anderen von diesem Benutzer erstellten Assets entfernt. Wenn Sie diese Assets beibehalten möchten, wenden Sie sich an das Team [!DNL Commerce Intelligence] [support](../guide-overview.md#Submitting-a-Support-Ticket) , bevor Sie den Benutzer deaktivieren. Die Unterstützung kann Ihnen dabei helfen, diese Assets an einen anderen Benutzer zu übertragen.

### Benutzer erneut aktivieren

Um einen Benutzer zu reaktivieren, laden Sie ihn erneut ein, indem Sie sein Konto mit der deaktivierten E-Mail-Adresse neu erstellen und seinen Zugriff sowie die Daten, die ihm gehören, bei der Anmeldung wiederherstellen.

## Schritt 2: Löschen nicht verwendeter Dashboards und Berichte

Der nächste Schritt bei der Prüfung Ihres Kontos besteht darin, nicht verwendete Dashboards und Berichte zu löschen.

>[!NOTE]
>
>Dazu benötigen Sie `Admin` oder `Standard` [Benutzerberechtigungen](../administrator/user-management/user-management.md).

Jeder Benutzer mit Zugriff auf `Admin` oder `Standard` kann Berichte und Dashboards erstellen. Aus diesem Grund müssen alle Benutzer mit diesen Berechtigungen die folgenden Schritte ausführen, um nicht verwendete Berichte zu identifizieren und zu entfernen.

### Überprüfen Ihrer Dashboards und Berichte

Bevor Sie irgendetwas löschen, sollten Sie Ihre Berichte und Dashboards überprüfen, um zu bewerten, was aktuell verwendet wird. Sie können zwar die unten beschriebene **[!UICONTROL find unused reports]**-Funktion verwenden, jedoch werden Ihre Bereinigungsbemühungen bei jeder ersten Überprüfung deutlich produktiver.

### Löschen von Dashboards und Berichten

Nachdem Sie auf Ihre Dashboards und Berichte zugreifen, können Sie mit der Kontobereinigung beginnen.

**So entfernen Sie einen Bericht aus einem Dashboard**

1. Suchen Sie den Bericht, den Sie entfernen möchten, im Dashboard.
1. Wählen Sie oben rechts im Bericht **[!UICONTROL Options]** aus.
1. Klicken Sie auf **[!UICONTROL Remove From Dashboard]**.

**So löschen Sie ein ganzes Dashboard**

1. Wählen Sie **[!UICONTROL Manage Data]** und dann **[!UICONTROL Dashboards**].
1. Klicken Sie auf das Dashboard, das Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL Delete Dashboard]**.

Sie können auch &quot;**[!UICONTROL Dashboard Options]**&quot; und &quot;**[!UICONTROL Delete]**&quot; aus dem Dashboard selbst auswählen.

![](../../mbi/assets/Delete_from_dashboard.png)

>[!NOTE]
>
>Durch das Löschen eines Dashboards werden die darin enthaltenen Berichte nicht gelöscht. Daher müssen Sie einen weiteren Schritt unternehmen, um die Berichte zu löschen.

**So löschen Sie nicht verwendete Berichte**

1. Wählen Sie **[!UICONTROL Manage Data]** und dann **[!UICONTROL Reports]** aus.
1. Aktivieren Sie die Option **Nur nicht verwendete Berichte anzeigen** , die sich unter der Metrikliste befindet. Dadurch wird eine Liste von Berichten erstellt, die nicht in einem Dashboard oder einer E-Mail-Zusammenfassung verwendet werden.
1. Wählen Sie die Berichte aus, die Sie löschen möchten. Sie können alle auswählen, indem Sie auf das Kontrollkästchen über der Berichtsliste klicken.
1. Klicken Sie auf **[!UICONTROL Delete Selected]**.

Im Folgenden finden Sie einen Überblick über den nicht verwendeten Löschvorgang von Berichten:

![](../../mbi/assets/unused_reports.png)

## Schritt 3: Nicht verwendete Metriken löschen

Nachdem Sie die Benutzerliste, die Dashboards und Berichte bereinigt haben, können Sie zur Prüfung Ihrer Metrikenliste übergehen. Auf diese Weise können Sie alles identifizieren, was veraltet sein könnte - z. B. wurde eine neue Metrik mit einer anderen Definition erstellt - oder nicht verwendet wird.

1. Um eine Liste der abhängigen Berichte für eine Metrik zu generieren, gehen Sie zu &quot;**[!DNL Manage Data]**&quot;und wählen Sie dann &quot;Klick **[!UICONTROL Metrics]**&quot;.
1. Klicken Sie neben einer Metrik auf **[!UICONTROL Edit]** .
1. Unten auf der Seite sehen Sie einen Abschnitt mit dem Namen **[!UICONTROL Dependent Charts]**. Klicken Sie auf den Link, um eine Liste der abhängigen Berichte für diese Metrik zu erstellen.
1. Nachdem das System die Prüfung abgeschlossen hat, zeigt [!DNL Commerce Intelligence] eine Liste der Dashboards, Berichte und Benutzer an, die diese Metrik verwenden.

![](../../mbi/assets/report_dependecies.png)

Wenn Sie entscheiden, dass die Metrik nicht mehr benötigt wird, navigieren Sie zur Seite &quot;**[!UICONTROL Metrics]**&quot;, indem Sie auf &quot;**[!UICONTROL Back to Metric List]**&quot;klicken, um die Metrik zu finden, die Sie löschen möchten. Klicken Sie auf **[!UICONTROL Delete]**.

## Schritt 4: Prüfen der synchronisierten Spalten

Der letzte Schritt besteht darin, die derzeit in Ihrer Data Warehouse synchronisierten Spalten zu bewerten. Die Aufhebung der Synchronisierung von Spalten kann Ihr Konto nicht nur deklarieren, sondern auch die Aktualisierungszeit verkürzen.

Wenn Sie dies fortsetzen möchten, wenden Sie sich an [!DNL Commerce Intelligence] [Support](../guide-overview.md#Submitting-a-Support-Ticket). Das Supportteam kann einen Bericht erstellen, der alle Spalten enthält, die in keinem Dashboard für einen Benutzer verwendet werden und nicht in E-Mail-Zusammenfassungen verwendet werden, mit Ausnahme von SQL-Berichten. Anschließend können Sie diesen Bericht als Anleitung für die Auswahl von Spalten verwenden, die über den Data Warehouse-Manager aufgehoben werden sollen.

>[!NOTE]
>
>Sie können diese Spalten in Zukunft immer wieder synchronisieren. Wenn Sie die Synchronisierung einer Spalte aufheben, werden alle Daten von Ihrer Data Warehouse entfernt. Dies bedeutet nur, dass diese Spalte während des Aktualisierungszyklus nicht auf neue oder aktualisierte Werte überprüft wird.

**So heben Sie die Synchronisierung einer Spalte (oder Spalten) auf**

1. Gehe zu **[!DNL Manage Data]** und dann zu **[!UICONTROL Data Warehouse]**.
1. Navigieren Sie in der Liste **[!UICONTROL Synced Tables]** zur Tabelle, die die Spalte enthält.
1. Aktivieren Sie ein oder mehrere Kontrollkästchen neben einer oder mehreren Spalten, deren Synchronisierung Sie aufheben möchten.
   >[!NOTE]
   >
   >Sie können die Synchronisierung einer Primären Schlüsselspalte nicht aufheben, ohne die gesamte Tabelle abzulegen.

1. Klicken Sie auf **[!UICONTROL Remove]** , um die Synchronisierung zwischen einer oder mehreren Spalten aufzuheben.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../mbi/assets/drop_column.png)

## Aufwischen

Ihr [!DNL Commerce Intelligence] -Konto sollte jetzt tidier sein und für Sie und Ihr Team leichter navigieren können.
