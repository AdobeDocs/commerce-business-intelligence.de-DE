---
title: Steigerung des ROI bei Werbekampagnen
description: Erfahren Sie mehr über verschiedene Methoden zur Leistungsbewertung Ihrer Kampagne.
exl-id: 4f2bf408-eeaf-4dbf-b62e-89426734640a
role: Admin, User
feature: Data Warehouse Manager, Reports, Campaigns
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 0%

---

# Advertising-Kampagnen und ROI

Mit [!DNL Adobe Commerce Intelligence] können Sie einfach [Werbekostendaten und Umsatzdaten aus Ihrer Datenbank heiraten](../../data-analyst/importing-data/integrations/google-adwords.md). Auf diese Weise können Sie ermitteln, welche Kampagnen den höchsten ROI (Return on Investment) aufweisen. In diesem Thema werden verschiedene Methoden zur Bewertung der Kampagnenleistung untersucht.

## Voraussetzungen

* Importieren Sie Ihre Daten zu Werbekosten:
   * [Verbinden Sie Ihre  [!DNL Google AdWords]  mit  [!DNL Commerce Intelligence]](../importing-data/integrations/google-adwords.md): Synchronisiert Ihre [!DNL Adwords] Ausgaben in [!DNL Commerce Intelligence]
   * [Andere Daten zu Werbekosten hochladen](../importing-data/connecting-data/import-offline-ad-data.md): Dies wird für Kanäle ohne direkten Connector zu [!DNL Commerce Intelligence] empfohlen.
   * Wenn Sie Kostendaten aus mehreren Quellen importieren, können Sie die Daten in [!DNL Commerce Intelligence] [konsolidieren](../../best-practices/consolidating-your-tables.md). Einfach [ein Support-Ticket senden](../../guide-overview.md#Submitting-a-Support-Ticket).
* [Tracking der Benutzerakquisekanaldaten](../analysis/google-track-user-acq.md)

## Benutzerakquise-Kampagnen

Kampagnen, die auf die Benutzerakquise ausgerichtet sind, können aus einer Vielzahl von Perspektiven gemessen werden, darunter:

1. Anzahl der neuen Kampagnenbenutzer
1. Die Konversionsrate von der Registrierung bis zum Kauf von Kampagnen
1. ROI von Kampagnen basierend auf dem durchschnittlichen Lebenszeitwert (LTV) des Benutzers

Die Analysen (1) und (2) oben werden in einem separaten Tutorial zum Thema [Identifizieren Ihrer wichtigsten Marketing-Kanäle](../analysis/most-value-source-channel.md) erläutert. In diesem Beispiel analysieren Sie die Analyse (3), um den ROI der Kampagne im Zeitverlauf zu messen. Auf diese Weise wird ermittelt, ob durch eine bestimmte Kampagne erworbene Benutzer genügend Umsatz während der Lebensdauer generieren, um die Akquisekosten zu decken.

>[!NOTE]
>
>In diesem Beispiel wird davon ausgegangen, dass alle Kampagnenkosten ausschließlich zum Erwerb neuer Benutzer verwendet wurden. In der Realität werden Ihre Kampagnenkosten auch mit dem Erwerb nicht konvertierter Besuche, Wiederholungskäufern usw. geteilt. Wenn man davon ausgeht, dass alle Kosten für die Akquisition neuer registrierter Benutzer verwendet werden, berücksichtigt der resultierende ROI das Worst-Case-Szenario (höchste Kosten pro Akquise). Sie können sicher sein, dass Ihr tatsächlicher ROI höher ist als Ihre Berechnung.
>
>Beispiel: Angenommen, Sie haben 20 USD für eine Kampagne ausgegeben, die 10 neue Benutzer und 10 wiederkehrende Käufer generiert hat, belaufen sich Ihre tatsächlichen Kosten pro neuer Benutzer auf 1 USD. Doch unter der Annahme, dass alle Kosten für den Erwerb neuer Benutzer anfielen, belaufen sich die Kosten pro Akquise auf 2 USD.

**1. Erstellen Sie zunächst ein Diagramm, das Ihre Anzeigenkosten nach Kampagnen segmentiert:**

1. Erstellen Sie einen [!UICONTROL Metric] -Wert, der Ihre Ausgaben im Zeitverlauf zusammenfasst
1. Gehe zu [!UICONTROL Data > Metrics]
1. Wählen Sie `Add New Metric` und wählen Sie die Tabelle [!DNL `Adwords...`] aus, in der Ihre [!DNL AdWords] Kostendaten aufgezeichnet werden.
1. Geben Sie im Metrik-Editor Ihrer Metrik einen Namen (z. B. [!UICONTROL AdWord Cost])
1. Führen Sie mithilfe der Dropdown-Liste eine **Summe** für die Spalte `adCost` in der Tabelle [!DNL Adwords...] (Änderung) durch, die durch die Spalte `date` angeordnet ist.
   ![](../../assets/success-add-new-metric.png)<!--="500" height="303"}-->
1. Klicken Sie oben auf `Back to Metric List` und gehen Sie zu einem beliebigen Dashboard.

1. Erstellen eines Berichts, der die Ausgaben der Segmente nach Kampagnen angibt
1. Klicken Sie in einem beliebigen Dashboard auf [!UICONTROL Add Report > Create report]
1. Wählen Sie die soeben erstellte Metrik [!UICONTROL Adword Cost] aus
1. Setzen Sie den [!UICONTROL Time period] auf `All-time` und den [!UICONTROL Interval] auf `None`
1. Fügen Sie auf der Registerkarte `Group by` den Wert `campaign` als [!UICONTROL grouping field] hinzu und klicken Sie im Feld auf `Add All` .
1. Dieser Bericht zeigt Ihre All-Time [!DNL AdWords]-Kosten nach Kampagnen

**2. Erstellen Sie einen Bericht, der neue Benutzer nach Kampagnen zählt:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create report]**
1. Wählen Sie die Metrik `New users` aus, die die Anzahl neuer registrierter Benutzer im Zeitverlauf zählt.
1. Setzen Sie den [!UICONTROL Time period] auf `All-time` und den [!UICONTROL Interval] auf `None`
1. Fügen Sie auf der Registerkarte `Group by` den Wert `campaign` als `grouping field` hinzu und klicken Sie im Feld auf **`Add All`** .
1. Dieser Bericht zeigt Ihre gesamten registrierten Benutzer nach Kampagnen

**3. Erstellen Sie einen Bericht, der die durchschnittliche Benutzer-LTV nach Kampagnen segmentiert:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create report]**
1. Wählen Sie die Metrik `Average lifetime revenue` aus, die den durchschnittlichen Umsatz des Benutzers während der Lebensdauer berechnet
1. Setzen Sie den [!UICONTROL Time period] auf `All-time` und den [!UICONTROL Interval] auf `None`
1. Fügen Sie auf der Registerkarte `Group by` den Wert `campaign` oder den Wert `utm\_campaign` als [!UICONTROL grouping field] hinzu und klicken Sie in das Feld auf `Add All`
1. Dieser Bericht zeigt den durchschnittlichen Umsatz der Benutzer während der Lebensdauer nach Kampagnen.

**Berechnen Sie schließlich den Kampagnen-ROI, indem Sie diese drei Analysen in einem Bericht zusammenführen:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Fügen Sie als Eingabe hinzu und verwenden Sie die drei oben verwendeten Metriken. Jedem wird ein Brief zugewiesen (z. B.\[`A`\], \[`B`\] und \[`C`\])
1. [!UICONTROL Cost]: Fügen Sie die Metrik AdWords-Kosten hinzu - dies ist die Variable \[A\]. Dadurch werden Kosten nach Kampagnen zurückgegeben.
1. [!UICONTROL Users]: Fügen Sie die Metrik Neue Benutzer hinzu - dies ist die Variable \[B\]. Dadurch wird die Anzahl der Benutzer nach Kampagnen zurückgegeben.
1. [!UICONTROL LTV]: Fügen Sie die Metrik Durchschnittlicher Lebensdauerumsatz hinzu - dies ist Variable \[`C`\]. Dadurch wird LTV nach Kampagnen zurückgegeben.

1. Klicken Sie auf das Symbol zum Ausblenden neben dem Wortdiagramm, damit Sie sich auf die Tabelle konzentrieren können.
1. Verwenden Sie nun `Add Formula` , um diese Metriken wie folgt zu kombinieren:
1. [!UICONTROL ROI]: Geben Sie die Formel `(\[C\]-\[A\]/\[B\])/(\[A\]/\[B\])` ein, wenn \[`A`\] für `Ad Cost by Campaigns` steht, \[`B`\] für `New users by campaigns` und \[`C`\] `LTV by campaigns`. Dadurch wird das Verhältnis von (durchschnittlicher Benutzer-LTV - durchschnittliche Kosten pro Akquise) / (durchschnittliche Kosten pro Akquise) zurückgegeben.
1. [!UICONTROL Avg Return per User]: Geben Sie die Formel **\[`C`\]-(\[`A`\]/\[`B`\])** ein. Dadurch wird die durchschnittliche Spanne zurückgegeben, die ein Benutzer durch Berechnung (durchschnittliche LTV-Nutzer) - (durchschnittliche Kosten pro Akquisition) ermittelt hat.
1. [!UICONTROL CPA]: Geben Sie die Formel **`\[A\]/\[B\]`** ein. Dadurch werden die tatsächlichen Kampagnenkosten pro Akquise zurückgegeben.
1. Andere mögliche Metriken, die aus [!DNL AdWords] -Daten einbezogen werden können, umfassen Summen von `Impressions` und `adClicks` (aus [!DNL AdWords] -Daten) sowie die Gesamtsumme von `number of orders`, die über eine bestimmte Kampagne vorgenommen wurde.
1. Es kann auch interessant sein, den ROI auf Basis von LTV 30 Tage und 90 Tage nach der Registrierung oder Erstkauf eines Benutzers zu berechnen.

1. Sie können einfach auf Ihre Metriken und Formeln klicken und ziehen, um die Spalten Ihres Berichts neu anzuordnen.
1. Benennen Sie Ihren Bericht und achten Sie darauf, ihn als Tabelle zu speichern.

## Produktkampagnen

Führen Sie produktspezifische Werbung durch? Wenn ja, können Sie den ROI für diese Kampagnen messen, indem Sie den Umsatz/die Kosten für bestimmte Produkte berechnen.

>[!NOTE]
>
>In diesem Beispiel wird davon ausgegangen, dass alle Kampagnenkosten ausschließlich zur Generierung von Käufen für bestimmte Produkte verwendet wurden. Wenn man davon ausgeht, dass alle Kosten für die Generierung von Käufen ausgegeben wurden, berücksichtigt der resultierende ROI das Worst-Case-Szenario (höchste Kosten pro Kauf). Sie können sicher sein, dass Ihr tatsächlicher ROI höher ist als diese Berechnung. Beispiel: Angenommen, Sie haben 20 USD für eine Kampagne ausgegeben, aus der 10 neue Benutzer und 10 Käufe stammen, belaufen sich Ihre tatsächlichen Kosten pro Kauf auf 1 USD. Unter der Annahme, dass alle Kosten für den Erwerb neuer Benutzer anfielen, belaufen sich die Kosten pro Kauf auf 2 USD.

Bevor Sie beginnen, senden Sie [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html), um die folgenden Dimensionen an Ihre Tabelle der Zeileneinträge (`sales\_flat\_order\_item, order\_item`) anzuschließen:

* Quelle der Bestellung (wenn Sie nur die Verweisquelle auf Benutzerebene verfolgen und dann der Quelle des Benutzers beitreten)
* Bestellungskampagne (wenn Sie nur die Verweisquelle auf Benutzerebene verfolgen und dann der Kampagne des Benutzers beitreten)
* Bestellmedium (wenn Sie nur die Verweisquelle auf Benutzerebene verfolgen und dann dem Medium des Benutzers beitreten)

**1. Erstellen Sie nun ein Diagramm, das den Umsatz pro Kampagne für bestimmte Produkte zurückgibt:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Wählen Sie die Metrik `Revenue by items` aus, die den Umsatz auf Zeileneinträgen berechnet
1. Setzen Sie den [!UICONTROL Time period] auf `All-time` und den [!UICONTROL Interval] auf `None`
1. Fügen Sie auf der Registerkarte `Filter by` den Wert `product name 'IN'` Produkt `A`, Produkt `B`, Produkt `C`, ...&quot;hinzu und fügen Sie alle Produktnamen ein, die auf Ihre Kampagne abzielen, getrennt durch ein Komma (z. B. `product name 'IN' yellow t-shirt`, `red t-shirt, blue t-shirt`)
1. Fügen Sie auf der Registerkarte `Group by` `order's campaign` oder `order's utm\_campaign` als Feld `grouping` hinzu und klicken Sie im Feld auf **[!UICONTROL Add All]**
1. Dieser Bericht zeigt Ihnen den Umsatz für bestimmte Produkte nach Kampagnen

**2. Um den ROI zu berechnen, kombinieren Sie erneut Metriken in einem Bericht:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Fügen Sie die Metrik `Revenue by items` hinzu, folgen Sie dem Filter und der Gruppe nach Anweisungen aus der Kampagne für bestimmte Produkte oben und klicken Sie auf **[!UICONTROL Hide]** unter dem Skalarwert der Metrik.
1. Fügen Sie nun die Metrik [!DNL AdWords Cost] hinzu, folgen Sie dem Filter und der Gruppe nach Anweisungen aus dem Bericht `Ad cost by campaigns` , den Sie oben im Abschnitt `User acquisition campaigns` untersucht haben. Klicken Sie dann unter dem Skalarwert der Metrik auf **[!UICONTROL Hide]**
1. Fügen Sie bei diesen Metriken Formeln hinzu:
1. [!UICONTROL ROI]: Geben Sie die Formel `\[A\]/\[B\]` ein, wenn `\[A\]` für `Revenue per campaign for specific product(s)` und `\[B\]` für `Ad cost by campaigns` steht. Dadurch wird das Verhältnis von (Umsatz für bestimmte Produkte) / (Kampagnenkosten) zurückgegeben.
1. [!UICONTROL Return]: Geben Sie die Formel `\[A\]-\[B\]` ein. Dadurch wird die durchschnittliche Spanne zurückgegeben, die ein Benutzer durch Berechnung (durchschnittliche LTV-Nutzer) - (durchschnittliche Kosten pro Akquise) erzielt hat.
1. (Optional) [!UICONTROL Revenue]: Blendet die Metrik `Revenue by items` ein, um den Umsatz für bestimmte Produkte pro Kampagnen anzuzeigen.
1. (Optional) [!UICONTROL Cost]: Blendet die Metrik `AdWords Cost` ein, um die Kosten für Kampagnen anzuzeigen.

1. Benennen Sie den Bericht und speichern Sie ihn als Tabelle

**3. Wiederholen Sie die obigen Schritte 1 und 2 für jedes Ihrer beworbenen Produkte oder Produktgruppen.**

## Verwandte Dokumentation

* [Verfolgen der Verweisquelle für Bestellungen über [!DNL Google Analytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](../analysis/track-usr-dev-browser.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)
* [ [!DNL Google Adwords] Konto verbinden](../importing-data/integrations/google-adwords.md)
* [Wie funktioniert die  [!DNL Google Analytics] UTM-Attribution?](../analysis/utm-attributes.md)
* [Fünf Best Practices für das UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
