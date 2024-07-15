---
title: Aktivieren Ihres [!DNL Adobe Commerce Intelligence] Kontos
description: Erfahren Sie, wen Sie kontaktieren müssen, um Ihr [!DNL Commerce Intelligence] Konto zu aktivieren.
exl-id: 0efac7b4-2457-48c7-947a-d2776b90a1dd
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: cdd2373c2b9afd85427d437c6d8450f4d4e03350
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Aktivieren Sie Ihr [!DNL Commerce Intelligence]-Konto für On-Premise- und Starteranmeldungen

Um [!DNL Commerce Intelligence] für On-Premise-Abonnements zu aktivieren, erstellen Sie zunächst ein [!DNL Commerce Intelligence] -Konto, geben Sie Ihre Einstellungsinformationen ein und verbinden Sie dann [!DNL Commerce Intelligence] mit Ihrer [!DNL Commerce] -Datenbank. <!-- For information about activation in `Cloud Starter` projects, see [Activating your [!DNL Commerce Intelligence] Account for `Cloud Starter` Subscriptions](../getting-started/cloud-activation.md).-->

## Erstellen Sie Ihr [!DNL Commerce Intelligence]-Konto

Wenden Sie sich zur Erstellung Ihres Kontos an Ihr Adobe Account-Team oder Ihren technischen Kundenberater.

## Kennwort erstellen

Nachdem Ihr Konto erstellt wurde, überprüfen Sie Ihre E-Mail auf eine E-Mail mit einer Kontobenachrichtigung von [!DNL The Magento BI Team@rjmetrics.com]. Verwenden Sie den in der E-Mail angegebenen Link, um auf Ihr [!DNL Commerce Intelligence] -Konto zuzugreifen und Ihr Kennwort zu erstellen. Gehen Sie in Ihren Posteingang und überprüfen Sie Ihre E-Mail-Adresse.

Wenn Sie keine E-Mail erhalten haben, kontaktieren Sie [den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).

![](../assets/create-account-4.png)

## Festlegen von Store-Voreinstellungen

Bevor Sie die Datenbankverbindung konfigurieren, füllen Sie das Formular mit den Speicherinformationen aus. Diese Informationen sind erforderlich, um das **[!UICONTROL Connect your Database]**-Setup abzuschließen.

![](../assets/create-account-6.png)

## Hinzufügen von [!DNL Commerce Intelligence] Benutzern

Nachdem Sie Ihr Kennwort festgelegt und sich bei [!DNL Commerce Intelligence] angemeldet haben, können Sie weitere Benutzer zu Ihrem [!DNL Commerce Intelligence] -Konto hinzufügen. Fügen Sie beim Hinzufügen von Benutzern Admin-Benutzer mit entsprechenden Berechtigungen hinzu, um den Aktivierungsprozess abzuschließen.

![](../assets/create-account-5.png)

## Erstellen Sie einen dedizierten [!DNL Commerce Intelligence] -Benutzer im [!DNL Commerce] -Administrator.

Um [!DNL Commerce Intelligence] zu verwenden, müssen Sie dem [!DNL Commerce] -Projekt einen permanenten und dedizierten Benutzer hinzufügen. Dieser dedizierte Benutzer dient als permanente Verbindung zu [!DNL Commerce] , wodurch neue Daten abgerufen und an die [!DNL Commerce Intelligence] -Data Warehouse des Kontos übertragen werden können.

Durch die Konfiguration eines dedizierten [!DNL Commerce Intelligence] -Benutzers wird sichergestellt, dass das Konto nicht deaktiviert oder gelöscht wird, sodass die [!DNL Commerce Intelligence] -Verbindung gestoppt wird.


>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines Kontonamens, der seinen permanenten Status angibt (z. B. ACI-dedizierte, ACI-database-connector usw.).

Nachdem Sie den dedizierten Benutzer für [!DNL Commerce Intelligence] in der Admin-Umgebung erstellt haben, fügen Sie denselben Benutzer zur primären Umgebung des [!DNL Commerce] -Projekts mit der Einstellung **[!UICONTROL Master]** von `Contributor` hinzu.

![](../assets/commerce-add-user-settings.png)

## Commerce Intelligence SSH-Schlüssel abrufen

1. Scrollen Sie auf der Seite [!UICONTROL Connect your database] für das [!DNL Commerce Intelligence]-Setup nach unten und wählen Sie **[!UICONTROL Encryption settings]** aus.

1. Wählen Sie für **Verschlüsselungstyp** die Option `SSH Tunnel` aus.

1. Kopieren Sie aus der Dropdown-Liste den bereitgestellten öffentlichen Schlüssel.

   ![](../assets/encryption-setting-new-account.png)

## Fügen Sie Ihren öffentlichen Schlüssel zum [!DNL Commerce Intelligence] hinzu.

1. Melden Sie sich über die [!DNL Commerce Admin] mit den Anmeldeinformationen für den soeben erstellten [!DNL Commerce Intelligence] -Benutzer an.

1. Wählen Sie die Registerkarte **Kontoeinstellungen** aus.

1. Scrollen Sie nach unten und erweitern Sie die Dropdown-Liste **[!UICONTROL SSH Keys]** . Wählen Sie dann **[!UICONTROL Add a public key]** aus.

   ![](../assets/add-public-key.png)

1. Fügen Sie den öffentlichen Schlüssel ein, den Sie im obigen Schritt [!DNL Encryption Type] kopiert haben.

   ![](../assets/paste-public-key.png)

## Stellen Sie die [!DNL Commerce Intelligence] Grundlagen `MySQL`-Anmeldedaten bereit.

1. Aktualisieren Sie Ihre `.magento/services.yaml`.

   ![](../assets/update-magento-services-yaml.png)

1. Aktualisieren Sie Ihre `.magento.app.yaml`.

   ![](../assets/magento-app-yaml-relationships.png)

## Abrufen von Informationen zur Datenbankverbindung

Abrufen der Informationen zur Datenbankverbindung zur [!DNL Commerce]-Datenbank zu [!DNL Commerce Intelligence]

1. Führen Sie die folgenden Schritte aus, um Ihre Informationen abzurufen.

   `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp`

1. Überprüfen Sie die Datenbankinformationen, die in etwa wie im folgenden Beispiel aussehen sollten.

   ![](../assets/example-database-information.png)

## [!DNL Commerce Intelligence] über eine verschlüsselte Verbindung mit Ihrer [!DNL Commerce]-Datenbank verbinden

>[!NOTE]
>
>Adobe empfiehlt dringend, einen [`SSH tunnel`](../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md)-Tunnel zu verwenden, um die Datenbankverbindung herzustellen. Wenn diese Methode jedoch keine Option ist, können Sie mit einem [`direct connection`](../data-analyst/importing-data/integrations/mysql-via-a-direct-connection.md) weiterhin [!DNL Commerce Intelligence] mit Ihrer Datenbank verknüpfen.

Geben Sie Ihre [!DNL Commerce Intelligence] -Informationen in den [!UICONTROL Connect your Magento Database]-Bildschirm ein.

![](../assets/connect-magento-db.png)

**Input:**

[!UICONTROL Integration Name]: [Wählen Sie einen Namen für Ihre [!DNL Commerce Intelligence]-Instanz aus]

[!UICONTROL Host]: `mbi.internal`

[!UICONTROL Port]: `3306`

[!UICONTROL Benutzername]: `mbi`

[!UICONTROL Password]: [im vorherigen Abschnitt angezeigtes Eingabedokument]

[!UICONTROL Database Name]: `main`

[!UICONTROL Table Prefixes]: [leer lassen, wenn keine Tabellenpräfixe vorhanden sind]

## Legen Sie Ihre Einstellungen für [!UICONTROL **Zeitzone**] fest.

![](../assets/time-zone-settings.png)

**Input:**

[!UICONTROL Database Timezone]: `UTC`

[!UICONTROL Desired Timezone]: [Wählen Sie die Zeitzone aus, für die Ihre Daten angezeigt werden sollen]

## Informationen zu den Verschlüsselungseinstellungen abrufen

Die Projekt-Benutzeroberfläche bietet eine SSH-Zugriffszeichenfolge. Diese Zeichenfolge kann zum Erfassen der für die [!UICONTROL **Remote-Adresse**] und den [!UICONTROL **Benutzernamen**] erforderlichen Informationen verwendet werden. Verwenden Sie die SSH Access-Zeichenfolge, indem Sie auf der Master-Verzweigung der Projekt-Benutzeroberfläche die Schaltfläche Access Site auswählen. Suchen Sie dann Ihren [!UICONTROL User Name] und Ihren [!UICONTROL Remote Address] wie unten dargestellt.

![](../assets/master-branch-settings.png)

## Geben Sie Ihre [!DNL Encryption]-Einstellungen ein.

![](../assets/encryption-settings-2.png)

**Input:**

[!UICONTROL Encryption Type]: `SSH Tunnel`

[!UICONTROL Remote Address]: `ssh.us-3.magento.cloud` [aus dem vorherigen Schritt]

[!UICONTROL Username]: `vfbfui4vmfez6-master-7rqtwti—mymagento` [aus dem vorherigen Schritt]

[!UICONTROL Port]: `22`

## Speichern Sie Ihre Integration.

Wenden Sie nach Abschluss der Konfigurationsschritte die Änderungen an, indem Sie [!UICONTROL **Integration speichern**] auswählen.

Sie haben Ihre [!DNL Commerce] -Datenbank jetzt erfolgreich mit Ihrem [!DNL Commerce Intelligence] -Konto verbunden.

>[!NOTE]
>
>Wenn Sie ein [!DNL Adobe Commerce Intelligence Pro] -Kunde sind, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater, um die nächsten Schritte zu koordinieren.

Nachdem Sie die Konfiguration abgeschlossen haben, melden Sie sich [bei Ihrem [!DNL Commerce Intelligence] -Konto an.](../getting-started/sign-in.md)

<!---# Activate your [!DNL Commerce Intelligence] Account 

To activate [!DNL Commerce Intelligence] for on-premise or `Cloud Pro` subscriptions, [contact support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

>[!NOTE]
>
>Adobe no longer supports new `Cloud Starter` subscriptions.--->
