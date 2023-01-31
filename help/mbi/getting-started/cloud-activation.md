---
title: Aktivieren Ihrer [!DNL MBI] Konto für Cloud Starter-Abonnements
description: Erfahren Sie, wie Sie [!DNL MBI] für Cloud Starter-Projekte.
exl-id: 172439ee-fa1d-4872-b6a9-c61a212a7cbe
source-git-commit: 82882479d4d6bea712e8dd7c6b2e5b7715022cc3
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Aktivieren Ihrer [!DNL MBI] Konto für `Cloud Starter` Abonnements

So aktivieren [!DNL MBI] für `Cloud Starter` Projekte, erstellen Sie zunächst eine [!DNL MBI] -Konto und erstellen Sie dann eine `SSH` und dann schließlich eine Verbindung zu Ihrer Commerce-Datenbank herstellen. Siehe [Aktivieren von On-Premise-Abonnements](../getting-started/onpremise-activation.md).

>[!NOTE]
>
>Hilfe bei der Aktivierung [!DNL MBI] für `Cloud Pro` Projekte, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater.

1. Erstellen Sie Ihre [!DNL MBI] Konto.

   - Navigieren Sie zu [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login)

   - Navigieren Sie zu **[!UICONTROL My Account** > **My [!DNL MBI] Instances]**.

   - Klicken **[!UICONTROL Create Instance]**. Wenn diese Schaltfläche nicht angezeigt wird, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater.

   - Wählen Sie Ihre `Cloud Starter` Abonnement. Wenn Sie nur `cloud starter` Abonnement wird automatisch ausgewählt.

   - Klicken **[!UICONTROL Continue]**.

   - Geben Sie Ihre Informationen ein, um Ihr Konto zu erstellen.

   ![](../assets/create-account-2.png)

   - Gehen Sie in Ihren Posteingang und überprüfen Sie Ihre E-Mail-Adresse.

   ![](../assets/create-account-3.png)

   - Erstellen Sie Ihr Kennwort.

   ![](../assets/create-account-4.png)

   - Nach der Erstellung Ihres Kontos haben Sie dann die Möglichkeit, Ihrem neuen Konto Benutzer hinzuzufügen. Technische Administratoren können nun hinzugefügt werden, um die folgenden Schritte auszuführen.

   ![](../assets/create-account-5.png)

1. Geben Sie Informationen zu Ihrem Store ein, um Ihre Voreinstellungen festzulegen.

   ![](../assets/create-account-6.png)

   Es gibt einige Informationen, die Sie sammeln müssen, bevor Sie Ihre Datenbank für den dritten Schritt im Onboarding-Prozess verbinden können. Sie werden die `Connect your database` Seite in Schritt 9.

1. Erstellen eines dedizierten [!DNL MBI] Benutzer.

   - Neuen Benutzer erstellen auf [https://accounts.magento.com](https://accounts.magento.com).

   - _Warum ein neuer Benutzer?_ [!DNL MBI] benötigt einen Benutzer, der zum Projekt hinzugefügt wurde, um kontinuierlich neue Daten abzurufen, die an das Konto übertragen werden. [!DNL MBI] Data Warehouse. Dieser Benutzer dient als diese Verbindung. Das Hinzufügen dieses Benutzers zum Projekt erfolgt in Schritt 4.

   - Der Grund für die Verwendung einer [!DNL MBI] Der Benutzer soll verhindern, dass der hinzugefügte Benutzer versehentlich deaktiviert oder gelöscht wird und die [!DNL MBI] Verbindung.

1. Fügen Sie den neu erstellten Benutzer zur primären Umgebung des Projekts als `Contributor`.

   ![](../assets/create-account-7.png)

1. Holen Sie sich [!DNL MBI] `SSH` Schlüssel.

   - Navigieren Sie zu `Connect your database` der [!DNL MBI] Einrichten der Benutzeroberfläche und Scrollen Sie nach unten zu `Encryption settings`.

   - Für `Encryption Type` Feld, wählen Sie `SSH Tunnel`.

   - Sie können die bereitgestellte [!DNL MBI] `Public Key`.

   ![](../assets/create-account-8.png)

1. Neue hinzufügen [!DNL MBI] `Public key` der [!DNL MBI] Benutzer, der in Schritt 5 erstellt wurde.

   - Navigieren Sie zu [https://accounts.magento.cloud/](https://accounts.magento.cloud/). Melden Sie sich mit den Anmeldedaten für Ihr Konto an. [!DNL MBI] Benutzer erstellt. Gehen Sie dann zu `Account Settings` Registerkarte.

   - Scrollen Sie nach unten und erweitern Sie das Dropdown-Menü für `SSH` Schlüssel. Klicken Sie anschließend auf **[!UICONTROL Add a public key]**.

   ![](../assets/create-account-9.png)

   - Fügen Sie die [!DNL MBI] `SSH Public Key` von oben.

   ![](../assets/create-account-10.png)

1. Bereitstellung [!DNL MBI] MySQL-Anmeldeinformationen.

   - Aktualisieren Sie Ihre `.magento/services.yaml`

   ```sql
   mysql:
       type: mysql:10.0
       disk: 2048
       configuration:
           schemas:
               - main
           endpoints:
               mysql:
                   default_schema: main
                   privileges:
                       main: admin
               mbi:
                   default_schema: main
                   privileges:
                       main: ro
   ```

   - Aktualisieren Sie Ihre `.magento.app.yaml`

   ```sql
           relationships:
               database: "mysql:mysql"
               mbi: "mysql:mbi"
               redis: "redis:redis"
   ```

1. Informationen zum Verbinden Ihrer Datenbank mit [!DNL MBI].

   Ausführen
   `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp`

   um Informationen zum Verbinden Ihrer Datenbank zu erhalten.

   Sie sollten Informationen erhalten, die der folgenden Ausgabe ähneln:

   ```json
           "mbi" : [
                 {
                    "scheme" : "mysql",
                    "rel" : "mbi",
                    "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                    "query" : {
                       "is_master" : true
                    },
                    "ip" : "169.254.169.143",
                    "path" : "main",
                    "host" : "[!DNL MBI].internal",
                    "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                    "username" : "mbi",
                    "service" : "mysql",
                    "port" : 3306,
                    "password" : "[password]"
                 }
              ],
   ```

1. Commerce-Datenbank verbinden

   ![](../assets/create-account-11.png)

   - `Integration Name`: [Wählen Sie einen Namen für Ihre Integration aus.]

   - `Host`: `[!DNL MBI].internal`

   - `Port`: `3306`

   - `Username`: `mbi`

   - `Password`: [Eingabe-Kennwort, das in der Ausgabe für Schritt 8 angegeben ist.]

   - `Database Name`: `main`

   - `Table Prefixes`: [leer lassen, wenn keine Tabellenpräfixe vorhanden sind]

1. Legen Sie Ihre Zeitzoneneinstellungen fest.

   ![Eingaben](../assets/create-account-12.png)

   - `Database`: `Timezone: UTC`

   - `Desired Timezone`: [Wählen Sie die Zeitzone aus, in der Ihre Daten angezeigt werden sollen.]

1. Hier erhalten Sie Informationen zu Ihren Verschlüsselungseinstellungen.

   - Die Projektoberfläche bietet eine `SSH` Zugriffszeichenfolge. Diese Zeichenfolge kann zum Erfassen der für `Remote Address` und `Username` bei der Einrichtung der `Encryption` -Einstellungen. Verwenden Sie die `SSH Access` durch Klicken auf die Schaltfläche für den Zugriff auf die Website in Ihrem Übergeordneten Zweig der Projektoberfläche gefundene Zeichenfolge und suchen Sie Ihre `User Name` und `Remote Address` wie unten dargestellt.

   ![](../assets/create-account-13.png)

   ![](../assets/create-account-14.png)

1. Eingabedaten für Ihre `Encryption` settings

   ![](../assets/create-account-15.png)

   **Eingaben**

   - `Encryption Type`: `SSH Tunnel`

   - `Remote Address`: `ssh.us-3.magento.cloud`

   - `Username`: `vfbfui4vmfez6-master-7rqtwti--mymagento`

   - `Port`: `22`

1. Klicken **[!UICONTROL Save Integration]**.

1. Sie haben jetzt erfolgreich eine Verbindung zu Ihrem [!DNL MBI] -Konto.

1. Nachdem Sie erfolgreich eine Verbindung hergestellt haben [!DNL MBI] Wenden Sie sich an Ihren Customer Success Manager, um die nächsten Schritte zu koordinieren, z. B. das Einrichten von Integrationen und anderen Konfigurationsschritten.

1. Wenn Sie die Konfiguration abgeschlossen haben, können Sie [Anmelden](../getting-started/sign-in.md) auf [!DNL MBI] -Konto.
