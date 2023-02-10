---
title: Deklarieren der [!DNL MBI] Konto
description: Erfahren Sie, wie Sie Ihre [!DNL MBI] -Konto.
exl-id: 5fcdac2d-41ca-4011-b646-a699d9ecc6e4
source-git-commit: fa954868177b79d703a601a55b9e549ec1bd425e
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# Bereinigen Sie Ihre [!DNL MBI] Konto

Ob Sie mit [!DNL MBI] 6 Monate oder 6 Jahre lang ist die Führung eines ordentlichen Kontos von größter Bedeutung, damit Ihr Unternehmen die Plattform optimal nutzen kann. Im Laufe der Zeit ist es natürlich, dass es Benutzer, Dashboards, Berichte, Metriken und Spalten gibt, die nicht mehr benötigt werden. Vielleicht haben Sie einen Bericht für die einmalige Verwendung erstellt und ihn vergessen, oder ein Benutzer, der Ihr Unternehmen verlassen hat, hat sein Konto nie deaktiviert.

In Verbindung mit [standardisierte, eindeutige Benennung aller Elemente](../best-practices/naming-elements.md)) Ihrer [!DNL MBI] -Konto verwenden, helfen Ihnen die nachfolgenden Schritte zur Kontoprüfung dabei, die Übersichtlichkeit und unnötige Analysen für Ihre Benutzer zu reduzieren. Ein weiterer Vorteil umfasst [potenziell schnellere Aktualisierungszyklen](../best-practices/reduce-update-cycle-time.md).

## Schritt 1: Nicht aktive Benutzer identifizieren

Der erste Schritt bei der Bereinigung Ihres Kontos besteht darin, die Konten Ihrer nicht aktiven Benutzer zu deaktivieren, z. B. Personen, die das Unternehmen verlassen oder nicht mehr verwenden [!DNL MBI] in ihren aktuellen Rollen.

Klicken Sie dazu in der oberen rechten Ecke der Navigationsleiste auf den Namen Ihres Unternehmens und wählen Sie **[!UICONTROL Manage Users]**. Wählen Sie anschließend den Benutzer aus, den Sie deaktivieren möchten, und klicken Sie auf **[!UICONTROL Deactivate User]**.

>[!NOTE]
>
>Sie benötigen [Administratorberechtigungen](../administrator/user-management/user-management.md) um dies zu tun.

>[!WARNING]
>
>Durch das Deaktivieren eines Benutzers werden auch die Diagramme, Dashboards und anderen Assets entfernt, die von diesem Benutzer erstellt wurden. Wenn Sie diese Assets beibehalten möchten, wenden Sie sich an die [!DNL MBI] [Support](../guide-overview.md) Team vor der Deaktivierung des Benutzers. Die Unterstützung kann Ihnen dabei helfen, diese Assets an einen anderen Benutzer zu übertragen.

### Benutzer erneut aktivieren

Um einen Benutzer wieder zu aktivieren, laden Sie ihn erneut ein, indem Sie sein Konto mit der deaktivierten E-Mail-Adresse neu erstellen. Der Zugriff auf den Benutzer und die Daten, die ihm gehören, werden bei der Anmeldung wiederhergestellt.

## Schritt 2: Nicht verwendete Dashboards und Berichte löschen

Der nächste Schritt bei der Prüfung Ihres Kontos besteht darin, nicht verwendete Dashboards und Berichte zu löschen.

>[!NOTE]
>
>Sie benötigen `Admin` oder `Standard` [Benutzerberechtigungen](../administrator/user-management/user-management.md) um dies zu tun.

Jeder Benutzer mit `Admin` oder `Standard` -Zugriff kann Berichte und Dashboards erstellen. Aus diesem Grund müssen alle Benutzer mit diesen Berechtigungen die folgenden Schritte ausführen, um nicht verwendete Berichte zu identifizieren und zu entfernen.

### Überprüfen Ihrer Dashboards und Berichte

Bevor Sie etwas löschen, sollten Sie Ihre Berichte und Dashboards überprüfen, um zu bewerten, was derzeit verwendet wird. Während Sie die **[!UICONTROL find unused reports]** weiter unten beschrieben ist, werden Ihre Bereinigungsbemühungen durch eine erste Überprüfung wesentlich produktiver.

### Löschen von Dashboards und Berichten

Nachdem Sie auf Ihre Dashboards und Berichte zugreifen, können Sie mit der Kontobereinigung beginnen.

**So entfernen Sie einen Bericht aus einem Dashboard**

1. Suchen Sie den Bericht, den Sie entfernen möchten, im Dashboard.
1. Auswählen **[!UICONTROL Options]** in der oberen rechten Ecke des Berichts.
1. Klicken **[!UICONTROL Remove From Dashboard]**.

**So löschen Sie ein ganzes Dashboard**

1. Auswählen **[!UICONTROL Manage Data]**, dann **[!UICONTROL Dashboards**].
1. Klicken Sie auf das Dashboard, das Sie löschen möchten.
1. Klicken **[!UICONTROL Delete Dashboard]**.

Sie können auch **[!UICONTROL Dashboard Options]**, dann **[!UICONTROL Delete]** aus dem Dashboard selbst.

![](../../mbi/assets/Delete_from_dashboard.png)

>[!NOTE]
>
>Durch das Löschen eines Dashboards werden die darin enthaltenen Berichte nicht gelöscht. Daher müssen Sie einen weiteren Schritt unternehmen, um die Berichte zu löschen.

**So löschen Sie nicht verwendete Berichte**

1. Auswählen **[!UICONTROL Manage Data]**, dann **[!UICONTROL Reports]**.
1. Überprüfen Sie die **Nur nicht verwendete Berichte anzeigen** unter der Metrikliste. Dadurch wird eine Liste von Berichten erstellt, die nicht in einem Dashboard oder einer E-Mail-Zusammenfassung verwendet werden.
1. Wählen Sie die Berichte aus, die Sie löschen möchten. Sie können alle auswählen, indem Sie auf das Kontrollkästchen über der Berichtsliste klicken.
1. Klicken **[!UICONTROL Delete Selected]**.

Im Folgenden finden Sie einen Überblick über den nicht verwendeten Löschvorgang von Berichten:

![](../../mbi/assets/unused_reports.png)

## Schritt 3: Nicht verwendete Metriken löschen

Nachdem Sie die Benutzerliste, die Dashboards und Berichte bereinigt haben, können Sie zur Prüfung Ihrer Metrikenliste übergehen. Auf diese Weise können Sie alles identifizieren, was veraltet sein könnte - z. B. wurde eine neue Metrik mit einer anderen Definition erstellt - oder nicht verwendet wird.

1. Um eine Liste der abhängigen Berichte für eine Metrik zu erstellen, gehen Sie zu **[!DNL Manage Data]** Klicken Sie auf Klicken **[!UICONTROL Metrics]**.
1. Klicken **[!UICONTROL Edit]** neben einer Metrik.
1. Unten auf der Seite wird ein Abschnitt mit dem Namen **[!UICONTROL Dependent Charts]**. Klicken Sie auf den Link, um eine Liste der abhängigen Berichte für diese Metrik zu erstellen.
1. Nachdem das System die Prüfung abgeschlossen hat, [!DNL MBI] zeigt eine Liste der Dashboards, Berichte und Benutzer an, die diese Metrik verwenden.

![](../../mbi/assets/report_dependecies.png)

Wenn Sie entscheiden, dass die Metrik nicht mehr benötigt wird, navigieren Sie zurück zum **[!UICONTROL Metrics]** Seite durch Klicken auf **[!UICONTROL Back to Metric List]** oben auf der Seite und suchen Sie die Metrik, die Sie löschen möchten. Klicken **[!UICONTROL Delete]**.

## Schritt 4: Prüfen der synchronisierten Spalten

Der letzte Schritt besteht darin, die Spalten zu bewerten, die derzeit in Ihrem Data Warehouse synchronisiert werden. Die Aufhebung der Synchronisierung von Spalten kann Ihr Konto nicht nur deklarieren, sondern auch die Aktualisierungszeit verkürzen.

Wenn Sie dies fortsetzen möchten, wenden Sie sich an [!DNL MBI] [Support](../guide-overview.md). Das Supportteam kann einen Bericht erstellen, der alle Spalten enthält, die in keinem Dashboard für einen Benutzer verwendet werden und nicht in E-Mail-Zusammenfassungen verwendet werden, mit Ausnahme von SQL-Berichten. Anschließend können Sie diesen Bericht als Anleitung zur Auswahl der Spalten verwenden, die über den Data Warehousen-Manager aufgehoben werden sollen.

>[!NOTE]
>
>Sie können diese Spalten in Zukunft immer wieder synchronisieren. Durch das Aufheben der Synchronisierung einer Spalte werden keine Daten aus Ihrem Data Warehouse entfernt. Dies bedeutet nur, dass diese Spalte während des Aktualisierungszyklus nicht auf neue oder aktualisierte Werte überprüft wird.

**So heben Sie die Synchronisierung einer Spalte (oder Spalten) auf**

1. Navigieren Sie zu **[!DNL Manage Data]**, dann **[!UICONTROL Data Warehouse]**.
1. Im **[!UICONTROL Synced Tables]** und navigieren Sie zur Tabelle, die die Spalte enthält.
1. Aktivieren Sie die Kontrollkästchen neben den Spalten, die Sie aufheben möchten.
   >[!NOTE]
   >
   >Sie können die Synchronisierung einer Primären Schlüsselspalte nicht aufheben, ohne die gesamte Tabelle abzulegen.

1. Klicken **[!UICONTROL Remove]** , um die Synchronisierung der Spalten aufzuheben.

Im Folgenden finden Sie einen Überblick über den gesamten Prozess:

![](../../mbi/assets/drop_column.png)

## Aufbrechen

Das ist es! Ihre [!DNL MBI] -Konto sollte jetzt tidier und einfacher zu navigieren für Sie und Ihr Team.
