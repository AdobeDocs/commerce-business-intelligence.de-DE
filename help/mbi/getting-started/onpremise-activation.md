---
title: Aktivieren Ihrer [!DNL MBI] Konto für On-Premise-Abonnements
description: Erfahren Sie mehr über das Aktivieren Ihrer [!DNL MBI] für On-Premise-Abonnements.
exl-id: 0efac7b4-2457-48c7-947a-d2776b90a1dd
source-git-commit: 9974cc5c5cf89829ca522ba620b8c0c2d509610c
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Aktivieren Ihrer [!DNL MBI] Konto für On-Premise-Abonnements

So aktivieren [!DNL MBI] für On-Premise-Abonnements erstellen Sie zunächst eine [!DNL MBI] Konto, dann verbinden [!DNL MBI] in Ihre Commerce-Datenbank. Informationen zur Aktivierung in `Cloud Starter` Projekte, siehe [Aktivieren Ihrer [!DNL MBI] Konto für `Cloud Starter` Abonnements](../getting-started/cloud-activation.md).

1. Erstellen Sie Ihre [!DNL MBI] Konto.

   - Gehen Sie zu [Anmeldung für Adobe Commerce-Konten](https://account.magento.com/customer/account/login)

   - Navigieren Sie zu **[!UICONTROL My Account** > **My [!DNL MBI] Instances]**.

   - Klicken **[!UICONTROL Create Instance]**. Wenn diese Schaltfläche nicht angezeigt wird, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater.

   - Geben Sie Ihre Informationen ein, um Ihr Konto zu erstellen.

   ![](../assets/create-account-2.png)

   - Gehen Sie in Ihren Posteingang und überprüfen Sie Ihre E-Mail-Adresse. Wenn Sie keine E-Mail erhalten haben, [Support kontaktieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en).

   - Erstellen Sie Ihr Kennwort.

   ![](../assets/create-account-4.png)

   - Nachdem Sie Ihr Konto erstellt haben, haben Sie die Möglichkeit, Ihrem neuen Konto Benutzer hinzuzufügen. Technische Administratoren können nun hinzugefügt werden, um die folgenden Schritte auszuführen.

   ![](../assets/create-account-5.png)

1. Geben Sie Informationen zu Ihrem Store ein, um Ihre Voreinstellungen festzulegen.

   ![](../assets/create-account-6.png)

1. Verbinden [!DNL MBI] mit einer verschlüsselten Verbindung zu Ihrer Commerce-Datenbank hinzugefügt.

   Commerce empfiehlt dringend, eine Verbindung mit einer [`SSH tunnel`](../data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md). Wenn dies jedoch keine Option ist, können Sie weiterhin eine Verknüpfung [!DNL MBI] zu Ihrer Datenbank mithilfe von [`direct connection`](../data-analyst/importing-data/integrations/mysql-via-a-direct-connection.md).

1. Nachdem Sie erfolgreich eine Verbindung hergestellt haben [!DNL MBI] Wenden Sie sich an Ihren Customer Success Manager, um die nächsten Schritte zu koordinieren, z. B. das Einrichten von Integrationen und anderen Konfigurationsschritten.

1. Wenn Sie die Konfiguration abgeschlossen haben, können Sie [Anmelden](../getting-started/sign-in.md) auf [!DNL MBI] -Konto.
