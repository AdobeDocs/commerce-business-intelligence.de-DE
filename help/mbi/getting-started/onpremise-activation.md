---
title: Aktivieren Ihrer [!DNL Adobe Commerce Intelligence] Konto
description: Erfahren Sie, an wen Sie sich wenden können, um Ihre [!DNL Commerce Intelligence] -Konto.
exl-id: 0efac7b4-2457-48c7-947a-d2776b90a1dd
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: cdd2373c2b9afd85427d437c6d8450f4d4e03350
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Aktivieren Ihrer [!DNL Commerce Intelligence] Konto für On-Premise- und Starteranmeldungen

So aktivieren [!DNL Commerce Intelligence] für On-Premise-Abonnements erstellen Sie zunächst eine [!DNL Commerce Intelligence] Konto, geben Sie Ihre Einstellungsinformationen ein und verbinden Sie dann [!DNL Commerce Intelligence] auf [!DNL Commerce] Datenbank. <!-- For information about activation in `Cloud Starter` projects, see [Activating your [!DNL Commerce Intelligence] Account for `Cloud Starter` Subscriptions](../getting-started/cloud-activation.md).-->

## Erstellen Sie Ihre [!DNL Commerce Intelligence] account

Wenden Sie sich zur Erstellung Ihres Kontos an Ihr Adobe Account-Team oder Ihren technischen Kundenberater.

## Kennwort erstellen

Nachdem Ihr Konto erstellt wurde, überprüfen Sie Ihre E-Mail auf eine E-Mail mit einer Kontobenachrichtigung von [!DNL The Magento BI Team@rjmetrics.com]. Verwenden Sie den in der E-Mail angegebenen Link, um auf Ihre [!DNL Commerce Intelligence] und erstellen Sie Ihr Passwort. Gehen Sie in Ihren Posteingang und überprüfen Sie Ihre E-Mail-Adresse.

Wenn Sie keine E-Mail erhalten haben, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).

![](../assets/create-account-4.png)

## Festlegen von Store-Voreinstellungen

Bevor Sie die Datenbankverbindung konfigurieren, füllen Sie das Formular mit den Speicherinformationen aus. Diese Informationen sind erforderlich, um die **[!UICONTROL Connect your Database]** einrichten.

![](../assets/create-account-6.png)

## Hinzufügen [!DNL Commerce Intelligence] Benutzer

Nachdem Sie Ihr Kennwort festgelegt und sich bei [!DNL Commerce Intelligence]können Sie weitere Benutzer zu Ihrem [!DNL Commerce Intelligence] -Konto. Fügen Sie beim Hinzufügen von Benutzern Admin-Benutzer mit entsprechenden Berechtigungen hinzu, um den Aktivierungsprozess abzuschließen.

![](../assets/create-account-5.png)

## Erstellen Sie eine dedizierte [!DNL Commerce Intelligence] -Benutzer in [!DNL Commerce] admin

Verwendung [!DNL Commerce Intelligence], müssen Sie einen permanenten und dedizierten Benutzer zum [!DNL Commerce] Projekt. Dieser dedizierte Benutzer dient als ständige Verbindung zu [!DNL Commerce] , das den Abruf und die Übertragung neuer Daten an das Konto ermöglicht, [!DNL Commerce Intelligence] Data Warehouse.

Konfigurieren eines dedizierten [!DNL Commerce Intelligence] Der Benutzer stellt sicher, dass das Konto nicht deaktiviert oder gelöscht wird, sodass das [!DNL Commerce Intelligence] Verbindung herzustellen.


>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines Kontonamens, der seinen permanenten Status angibt (z. B. ACI-dedizierte, ACI-database-connector usw.).

Nachdem Sie den dedizierten Benutzer für [!DNL Commerce Intelligence] Fügen Sie in der Admin-Umgebung denselben Benutzer zur primären Umgebung der [!DNL Commerce] Projekt mit **[!UICONTROL Master]** Einstellung von `Contributor`.

![](../assets/commerce-add-user-settings.png)

## Commerce Intelligence SSH-Schlüssel abrufen

1. Im [!UICONTROL Connect your database] Seite für [!DNL Commerce Intelligence] Setup, scrollen Sie nach unten und wählen Sie **[!UICONTROL Encryption settings]**.

1. Für **Verschlüsselungstyp** auswählen `SSH Tunnel`.

1. Kopieren Sie aus der Dropdown-Liste den bereitgestellten öffentlichen Schlüssel.

   ![](../assets/encryption-setting-new-account.png)

## Fügen Sie Ihren öffentlichen Schlüssel zum [!DNL Commerce Intelligence]

1. Aus dem [!DNL Commerce Admin], melden Sie sich mit den Anmeldeinformationen für die [!DNL Commerce Intelligence] -Benutzer, den Sie gerade erstellt haben.

1. Wählen Sie die **Kontoeinstellungen** Registerkarte.

1. Scrollen Sie nach unten und erweitern Sie die **[!UICONTROL SSH Keys]** angezeigt. Wählen Sie anschließend **[!UICONTROL Add a public key]**.

   ![](../assets/add-public-key.png)

1. Fügen Sie den öffentlichen Schlüssel ein, den Sie in den [!DNL Encryption Type] Schritt weiter oben.

   ![](../assets/paste-public-key.png)

## Bereitstellung [!DNL Commerce Intelligence] Grundlagen `MySQL` Anmeldeinformationen

1. Aktualisieren Sie Ihre `.magento/services.yaml`.

   ![](../assets/update-magento-services-yaml.png)

1. Aktualisieren Sie Ihre `.magento.app.yaml`.

   ![](../assets/magento-app-yaml-relationships.png)

## Abrufen von Informationen zur Datenbankverbindung

Informationen zur Datenbankverbindung zum [!DNL Commerce] Datenbank zu [!DNL Commerce Intelligence]

1. Führen Sie die folgenden Schritte aus, um Ihre Informationen abzurufen.

   `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp`

1. Überprüfen Sie die Datenbankinformationen, die in etwa wie im folgenden Beispiel aussehen sollten.

   ![](../assets/example-database-information.png)

## Verbinden [!DNL Commerce Intelligence] auf [!DNL Commerce] Datenbank mit einer verschlüsselten Verbindung

>[!NOTE]
>
>Adobe empfiehlt dringend, eine [`SSH tunnel`](../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md) Tunnel zur Herstellung der Datenbankverbindung. Wenn diese Methode jedoch keine Option ist, können Sie weiterhin eine Verknüpfung [!DNL Commerce Intelligence] zu Ihrer Datenbank mithilfe von [`direct connection`](../data-analyst/importing-data/integrations/mysql-via-a-direct-connection.md).

Geben Sie Ihre [!DNL Commerce Intelligence] Informationen in [!UICONTROL Connect your Magento Database] angezeigt.

![](../assets/connect-magento-db.png)

**Eingaben:**

[!UICONTROL Integration Name]: [Benennen Sie Ihre [!DNL Commerce Intelligence] instance]

[!UICONTROL Host]: `mbi.internal`

[!UICONTROL Port]: `3306`

[!UICONTROL Benutzername]: `mbi`

[!UICONTROL Password]: [Eingabe-Kennwort angezeigt im vorherigen Abschnitt]

[!UICONTROL Database Name]: `main`

[!UICONTROL Table Prefixes]: [leer lassen, wenn keine Tabellenpräfixe vorhanden sind]

## Legen Sie Ihre [!UICONTROL **Zeitzone**] settings

![](../assets/time-zone-settings.png)

**Eingaben:**

[!UICONTROL Database Timezone]: `UTC`

[!UICONTROL Desired Timezone]: [Wählen Sie die Zeitzone aus, für die Ihre Daten angezeigt werden sollen]

## Informationen zu den Verschlüsselungseinstellungen abrufen

Die Projekt-Benutzeroberfläche bietet eine SSH-Zugriffszeichenfolge. Diese Zeichenfolge kann zum Erfassen der für die [!UICONTROL **Remote-Adresse**] und [!UICONTROL **Benutzername**]. Verwenden Sie die SSH Access-Zeichenfolge, indem Sie auf der Master-Verzweigung der Projekt-Benutzeroberfläche die Schaltfläche Access Site auswählen. Suchen Sie dann Ihre [!UICONTROL User Name] und [!UICONTROL Remote Address] wie unten dargestellt.

![](../assets/master-branch-settings.png)

## Geben Sie Ihre [!DNL Encryption] settings

![](../assets/encryption-settings-2.png)

**Eingaben:**

[!UICONTROL Encryption Type]: `SSH Tunnel`

[!UICONTROL Remote Address]: `ssh.us-3.magento.cloud`  [aus dem vorherigen Schritt]

[!UICONTROL Username]: `vfbfui4vmfez6-master-7rqtwti—mymagento`  [aus dem vorherigen Schritt]

[!UICONTROL Port]: `22`

## Speichern Sie Ihre Integration.

Wenden Sie nach Abschluss der Konfigurationsschritte die Änderungen an, indem Sie [!UICONTROL **Integration speichern**].

Sie haben jetzt Ihre [!DNL Commerce] Datenbank [!DNL Commerce Intelligence] -Konto.

>[!NOTE]
>
>Wenn Sie [!DNL Adobe Commerce Intelligence Pro] wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater, um die nächsten Schritte zu koordinieren.

Nach Abschluss der Konfiguration [Anmelden](../getting-started/sign-in.md) auf [!DNL Commerce Intelligence] -Konto.

<!---# Activate your [!DNL Commerce Intelligence] Account 

To activate [!DNL Commerce Intelligence] for on-premise or `Cloud Pro` subscriptions, [contact support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html).

>[!NOTE]
>
>Adobe no longer supports new `Cloud Starter` subscriptions.--->
