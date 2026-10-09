---
title: Freigeben von Dashboards für andere Benutzer
description: Geben Sie ein Commerce Intelligence-Dashboard für Ihr Team frei, um alle Beteiligten auf dem Laufenden zu halten. Erfahren Sie mehr über die Empfehlungen von Adobe für die Gewährung von Bearbeitungsrechten für einige ausgewählte Benutzende.
exl-id: 6279b049-d1b2-4d40-b30b-ee8772e990f4
role: Admin, Developer, User
feature: Commerce Tables, Data Warehouse Manager, Dashboards
TQID: 'https://experienceleague.adobe.com/19tCk4327YLMnSrgQ0xHBinwiK2XHd7QU6l5rO-B6-k'
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
    internal-label: Commerce Intelligence
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b0c4e988-b173-423f-88d4-345071a0bce8
    internal-label: Data Warehouse Manager
  - id: 5d2a63cb-5675-5572-9de5-bc904157ef45
    internal-label: Commerce Tables
  - id: 06e518d4-11ae-5c20-98b0-ce8ab05d7166
    internal-label: Dashboards
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: fdbaf74705fb224414ac8cb69f6a1b34277e3f79
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# Freigeben von Dashboards für andere Benutzer

Die Freigabe von Dashboards ist eine hervorragende Möglichkeit, Ihr Team auf dem Laufenden zu halten und gemeinsame Diskussionen zu fördern. Durch die Erstellung und Freigabe eines zentralen Dashboards können Sie Ihrem Team die benötigten Informationen bereitstellen und gleichzeitig die Kontrolle behalten. [[!DNL Adobe] empfiehlt](../../best-practices/share-dashboard-best-practice.md){: target="_blank"} einigen wenigen ausgewählten Benutzern `Edit` zu gewähren, um versehentliche Änderungen zu minimieren.

>[!NOTE]
>
>Wenn das Dashboard, das Sie freigeben, Berichte enthält, die mit Metriken erstellt wurden, auf die ein bestimmter Benutzer keinen Zugriff hat, zeigen die Berichte eine `Error Loading Data` an. Wenn die Daten dem jeweiligen Benutzer angezeigt werden sollen, muss ein [Admin-Benutzer](../../administrator/user-management/user-management.md) Zugriff auf alle in diesen Berichten verwendeten Metriken gewähren.

## Dashboard freigeben

1. Klicken Sie oben im Bildschirm auf **[!UICONTROL Share Dashboard]** .

   Eine Liste aller Benutzer in Ihrem [!DNL Commerce Intelligence]-Konto wird angezeigt.

1. Um einen Benutzer auszuwählen, für den das Dashboard freigegeben werden soll, aktivieren Sie das Kontrollkästchen links neben seinem Namen.

   Um alle Benutzer auszuwählen bzw. deren Auswahl aufzuheben, klicken Sie auf **[!UICONTROL Select]** und wählen Sie `Everyone` bzw. `None` aus.

1. Berechtigungen können benutzerspezifisch oder massenweise festgelegt werden.

   *Um individuelle Berechtigungen festzulegen* klicken Sie auf **[!UICONTROL None]** rechts neben dem Namen des Benutzers. Wählen Sie aus diesem Dropdown-Menü den Berechtigungstyp aus, den der Benutzer haben soll.

   *Um Berechtigungen massenweise festzulegen* klicken Sie auf **[!UICONTROL Set Permissions]**. Wählen Sie aus diesem Dropdown-Menü den Berechtigungstyp aus, den die ausgewählten Benutzer haben sollen.

   >[!NOTE]
   >
   >Sie können diese Funktion auch verwenden, um zuvor festgelegte Berechtigungen zu aktualisieren. Wenn Sie beispielsweise die Freigabe des Dashboards für eine andere Person beenden möchten, legen Sie deren Berechtigungen auf `None` fest.

1. Um das Dashboard freizugeben, klicken Sie auf **[!UICONTROL Save Changes]**. Der/die ausgewählte(n) Benutzer(n) erhält/erhalten eine E-Mail, in der er/sie aufgefordert wird/werden, das Dashboard anzuzeigen.

Beispiel:

![Dashboard freigeben](../../assets/Share_Dashboards.gif)
