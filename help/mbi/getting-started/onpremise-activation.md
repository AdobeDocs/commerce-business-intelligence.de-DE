---
title: Activate your [!DNL Adobe Commerce Intelligence] Account
description: Erfahren Sie, an wen Sie sich wenden müssen, um Ihr - [!DNL Commerce Intelligence]  zu aktivieren.
exl-id: 0efac7b4-2457-48c7-947a-d2776b90a1dd
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: ba64de148ad5b3fc44591a10531244cfe670a728
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Aktivieren Ihres [!DNL Commerce Intelligence] Kontos für On-Premise- und Starter-Abonnements

Um [!DNL Commerce Intelligence] für On-Premise-Abonnements zu aktivieren, erstellen Sie zunächst ein [!DNL Commerce Intelligence], geben Sie Ihre Einstellungsinformationen ein und verbinden Sie [!DNL Commerce Intelligence] dann mit Ihrer [!DNL Commerce]. <!-- For information about activation in `Cloud Starter` projects, see [Activating your [!DNL Commerce Intelligence] Account for `Cloud Starter` Subscriptions](../getting-started/cloud-activation.md).-->

## Create your [!DNL Commerce Intelligence] account

To create your account, contact your Adobe Account Team or Customer Technical Advisor.

## Create your password

After your account has been created, check your email for an account notification email from [!DNL The Magento BI Team@rjmetrics.com]. Use the link provided in the email to access your [!DNL Commerce Intelligence] account and create your password. Go to your inbox and verify your email address.

Wenn Sie keine E-Mail erhalten haben, wenden [&#x200B; sich an den Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

![Bildschirm zum Erstellen eines Kennworts für ein neues Commerce Intelligence-Konto](../assets/create-account-4.png)

## Festlegen der Store-Voreinstellungen

Füllen Sie vor dem Konfigurieren der Datenbankverbindung das Formular Informationen speichern aus. Diese Informationen sind erforderlich, um die **[!UICONTROL Connect your Database]** Einrichtung abzuschließen.

![Formular mit Feldern für Geschäftsnamen, Währung und Zeitzone speichern](../assets/create-account-6.png)

## [!DNL Commerce Intelligence] Benutzer hinzufügen

Nachdem Sie Ihr Kennwort festgelegt und sich bei [!DNL Commerce Intelligence] angemeldet haben, können Sie weitere Benutzer zu Ihrem [!DNL Commerce Intelligence]-Konto hinzufügen. Fügen Sie beim Hinzufügen von Benutzern Admin-Benutzer mit entsprechenden Berechtigungen hinzu, um den Aktivierungsprozess abzuschließen.

![Benutzerformular mit Feldern für E-Mail-Adresse und Berechtigungsstufe hinzufügen](../assets/create-account-5.png)

## Erstellen Sie einen dedizierten [!DNL Commerce Intelligence]-Benutzer im [!DNL Commerce] Admin

Um [!DNL Commerce Intelligence] verwenden zu können, müssen Sie dem [!DNL Commerce]-Projekt einen permanenten und dedizierten Benutzer hinzufügen. Dieser dedizierte Benutzer dient als permanente Verbindung zu [!DNL Commerce], die den Abruf und die Übertragung neuer Daten an die [!DNL Commerce Intelligence] Data Warehouse des Kontos ermöglicht.

Configuring a dedicated [!DNL Commerce Intelligence] user ensures that the account is not deactivated or deleted, thus stopping the [!DNL Commerce Intelligence] connection.


>[!NOTE]
>
>Adobe encourages using an account name that indicate its permanent status (e.g., ACI-dedicated, ACI-database-connector, and so forth).

After you created the dedicated user for [!DNL Commerce Intelligence] in the Admin, add the same user to the primary environment of the [!DNL Commerce] project with a **[!UICONTROL Master]** setting of `Contributor`.

![Commerce fügt eine Benutzeroberfläche hinzu, deren Rolle auf „Mitwirkender“ festgelegt ist](../assets/commerce-add-user-settings.png)

## Commerce Intelligence SSH-Schlüssel abrufen

1. On the [!UICONTROL Connect your database] page for [!DNL Commerce Intelligence] setup,  scroll down and select **[!UICONTROL Encryption settings]**.

1. For **Encryption Type**, select `SSH Tunnel`.

1. From the drop-down, copy the public key that is provided.

   ![Encryption settings page showing SSH Tunnel type and public key field](../assets/encryption-setting-new-account.png)

## Add your public key to the [!DNL Commerce Intelligence]

1. From the [!DNL Commerce Admin], sign in using the login information for the [!DNL Commerce Intelligence] user you just created.

1. Wählen Sie die **Kontoeinstellungen** aus.

1. Scrollen Sie nach unten und erweitern Sie die Dropdown-Liste **[!UICONTROL SSH Keys]** . Wählen Sie dann **[!UICONTROL Add a public key]** aus.

   ![Seite Kontoeinstellungen mit Abschnitt SSH-Schlüssel und Schaltfläche Öffentlichen Schlüssel hinzufügen](../assets/add-public-key.png)

1. Fügen Sie den öffentlichen Schlüssel ein, den Sie im obigen [!DNL Encryption Type] kopiert haben.

   ![Formular mit öffentlichem Schlüssel mit Textfeld und Schaltfläche „Senden“ hinzufügen](../assets/paste-public-key.png)

## Bereitstellen von [!DNL Commerce Intelligence] Essentials-`MySQL`

1. Aktualisieren Sie Ihre `.magento/services.yaml`.

   ![Code, der die MySQL-Dienstkonfiguration in der Datei services.yaml anzeigt](../assets/update-magento-services-yaml.png)

1. Aktualisieren Sie Ihre `.magento.app.yaml`.

   ![Code, der die Datenbankbeziehungskonfiguration in der Datei app.yaml anzeigt](../assets/magento-app-yaml-relationships.png)

## Get database connection information

Abrufen der Informationen zur Datenbankverbindung mit der zu [!DNL Commerce] [!DNL Commerce Intelligence] Datenbank

1. Führen Sie die folgenden Schritte aus, um Ihre Informationen zu erhalten.

   `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp`

1. Überprüfen Sie die Datenbankinformationen, die dem folgenden Beispiel ähneln sollten.

   ![JSON-Ausgabe mit Anmeldeinformationen für die Datenbankverbindung, einschließlich Host, Port und Benutzername](../assets/example-database-information.png)

## [!DNL Commerce Intelligence] mithilfe einer verschlüsselten Verbindung mit Ihrer [!DNL Commerce] Datenbank verbinden

>[!NOTE]
>
>Adobe empfiehlt dringend, zur Herstellung der Datenbankverbindung einen [`SSH tunnel`](../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md) zu verwenden. Wenn diese Methode jedoch keine Option ist, können Sie [!DNL Commerce Intelligence] mithilfe einer [`direct connection`](../data-analyst/importing-data/integrations/mysql-via-a-direct-connection.md) mit Ihrer Datenbank verknüpfen.

Geben Sie Ihre [!DNL Commerce Intelligence] im [!UICONTROL Connect your Magento Database] ein.

![Verbinden Sie Ihr Datenbankformular mit Feldern für Integrationsnamen, Host, Port, Benutzernamen, Kennwort und Datenbanknamen](../assets/connect-magento-db.png)

**Eingänge:**

[!UICONTROL Integration Name]: [Wählen Sie einen Namen für Ihre [!DNL Commerce Intelligence]]

[!UICONTROL Host]: `mbi.internal`

[!UICONTROL Port]: `3306`

[!UICONTROL Benutzername]: `mbi`

[!UICONTROL Password]: [Eingabekennwort im vorherigen Abschnitt angezeigt]

[!UICONTROL Database Name]: `main`

[!UICONTROL Table Prefixes]: [Leer lassen, wenn keine Tabellenpräfixe vorhanden sind]

## Einstellungen für [!UICONTROL **Zeitzone**] festlegen

![Zeitzoneneinstellungen-Formular mit Dropdown-Feldern für die Datenbank-Zeitzone und die gewünschte Zeitzone](../assets/time-zone-settings.png)

**Inputs:**

[!UICONTROL Database Timezone]: `UTC`

[!UICONTROL Desired Timezone]: [choose the time zone for which you want your data to display]

## Abrufen von Informationen zu Verschlüsselungseinstellungen

Die Projekt-Benutzeroberfläche bietet eine SSH-Zugriffszeichenfolge. Diese Zeichenfolge kann verwendet werden, um die für „Remote [!UICONTROL **Adresse“**] &quot;[!UICONTROL **&quot;**] Informationen zu erfassen. Verwenden Sie die SSH-Zugriffszeichenfolge, indem Sie auf die Schaltfläche „Zugriff auf Site“ im Master-Zweig der Projekt-Benutzeroberfläche klicken. Suchen Sie dann Ihre [!UICONTROL User Name] und [!UICONTROL Remote Address] wie unten dargestellt.

![Project UI showing SSH access information with username and remote address](../assets/master-branch-settings.png)

## Input your [!DNL Encryption] settings

![Encryption settings form with fields for encryption type, remote address, username, and port](../assets/encryption-settings-2.png)

**Inputs:**

[!UICONTROL Encryption Type]: `SSH Tunnel`

[!UICONTROL Remote Address]: `ssh.us-3.magento.cloud`  [from the previous step]

[!UICONTROL Username]: `vfbfui4vmfez6-master-7rqtwti—mymagento` [aus dem vorherigen Schritt]

[!UICONTROL Port]: `22`

## Speichern Sie Ihre Integration.

Wenden Sie nach Abschluss der Konfigurationsschritte die Änderungen an, indem Sie [!UICONTROL **Integration speichern**] auswählen.

Sie haben jetzt Ihre [!DNL Commerce]-Datenbank erfolgreich mit Ihrem [!DNL Commerce Intelligence]-Konto verbunden.

>[!NOTE]
>
>Wenn Sie [!DNL Adobe Commerce Intelligence Pro] sind, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater, um die nächsten Schritte zu koordinieren.

Nachdem Sie die Konfiguration abgeschlossen haben, [&#x200B; Sie sich &#x200B;](../getting-started/sign-in.md) Ihrem [!DNL Commerce Intelligence] Konto an.

<!--
# Activate your [!DNL Commerce Intelligence] Account

To activate [!DNL Commerce Intelligence] for on-premise or `Cloud Pro` subscriptions, [contact support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de).

>[!NOTE]
>
>Adobe no longer supports new `Cloud Starter` subscriptions.
-->
