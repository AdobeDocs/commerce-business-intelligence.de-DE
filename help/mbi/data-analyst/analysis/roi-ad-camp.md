---
title: Steigerung des ROI bei Werbekampagnen
description: Erfahren Sie mehr über verschiedene Methoden zur Leistungsbewertung Ihrer Kampagne.
exl-id: 4f2bf408-eeaf-4dbf-b62e-89426734640a
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 0%

---

# Werbekampagnen und ROI

Mit MBI können Sie [Daten zu den Kosten und Umsatzdaten von Ehewerbung](../../data-analyst/importing-data/integrations/google-adwords.md) aus Ihrer Datenbank. Auf diese Weise können Sie erkennen, welche Kampagnen den höchsten ROI haben. In diesem Artikel werden verschiedene Methoden zur Bewertung der Kampagnenleistung beschrieben.

## Voraussetzungen

* Importieren Sie Ihre Daten zu Werbekosten:
   * [Verbinden Sie Ihre [!DNL Google AdWords] nach [!DNL MBI]](../importing-data/integrations/google-adwords.md): Dadurch wird Ihre [!DNL Adwords] Ausgaben in [!DNL MBI]
   * [Hochladen anderer Daten zu Werbekosten](../importing-data/connecting-data/import-offline-ad-data.md): Dies wird für Kanäle ohne direkten Connector empfohlen, um [!DNL MBI]
   * Wenn Sie Kostendaten aus mehreren Quellen importieren, können Sie [Konsolidierung](../../best-practices/consolidating-your-tables.md) die Daten in [!DNL MBI]. Einfach [Support-Ticket einreichen](../../guide-overview.md).
* [Tracking der Benutzerakquisekanaldaten](../analysis/google-track-user-acq.md)

## Benutzerakquise-Kampagnen

Kampagnen, die auf die Benutzerakquise ausgerichtet sind, können aus einer Vielzahl von Perspektiven gemessen werden, darunter:

1. Anzahl der neuen Kampagnenbenutzer
1. Die Konversionsrate von der Registrierung bis zum Kauf von Kampagnen
1. Der ROI von Kampagnen basierend auf dem durchschnittlichen Lebenszeitwert (LTV) des Benutzers.

Die Analysen (1) und (2) oben werden in einem separaten Tutorial zu [die wichtigsten Marketing-Kanäle identifizieren](../analysis/most-value-source-channel.md). In diesem Beispiel analysieren Sie die Analyse (3), um den ROI der Kampagne im Zeitverlauf zu messen. Auf diese Weise wird ermittelt, ob durch eine bestimmte Kampagne erworbene Benutzer genügend Umsatz während der Lebensdauer generieren, um die Akquisekosten zu decken.

>[!NOTE]
>
>In diesem Beispiel wird davon ausgegangen, dass alle Kampagnenkosten ausschließlich zum Erwerb neuer Benutzer verwendet wurden. In der Realität werden Ihre Kampagnenkosten auch mit dem Erwerb nicht konvertierter Besuche, Wiederholungskäufern usw. geteilt. Wenn man davon ausgeht, dass alle Kosten für die Akquisition neuer registrierter Benutzer verwendet werden, berücksichtigt der resultierende ROI das Worst-Case-Szenario (höchste Kosten pro Akquise). Sie können sicher sein, dass Ihr tatsächlicher ROI höher ist als Ihre Berechnung.
>
>Beispiel: Angenommen, Sie haben 20 USD für eine Kampagne ausgegeben, die 10 neue Benutzer und 10 wiederkehrende Käufer generiert hat, belaufen sich Ihre tatsächlichen Kosten pro neuer Benutzer auf 1 USD. Doch unter der Annahme, dass alle Kosten für den Erwerb neuer Benutzer anfielen, belaufen sich die Kosten pro Akquise auf 2 USD.)

**1. Erstellen Sie zunächst ein Diagramm, das Ihre Anzeigenkosten nach Kampagnen segmentiert:**

1. Erstellen Sie eine [!UICONTROL Metric] das Ihre Ausgaben über einen bestimmten Zeitraum zusammenfasst
1. Navigieren Sie zu [!UICONTROL Data > Metrics]
1. Auswählen `Add New Metric` und wählen Sie die [!DNL `Adwords...`] -Tabelle, die Ihre [!DNL AdWords] Kostendaten.
1. Geben Sie im Metrik-Editor Ihrer Metrik einen Namen (z. B. [!UICONTROL AdWord Cost])
1. Führen Sie mithilfe der Dropdown-Liste eine **Summe** auf `adCost` in der Spalte [!DNL Adwords...] Tabelle (Änderung), geordnet nach `date` Spalte.
   ![](../../assets/success-add-new-metric.png)<!--="500" height="303"}-->
1. Klicken `Back to Metric List` oben und gehen Sie zu einem beliebigen Dashboard.

1. Erstellen Sie einen Bericht, der die Ausgaben der Segmente nach Kampagnen angibt.
1. Klicken Sie in einem beliebigen Dashboard auf [!UICONTROL Add Report > Create report]
1. Wählen Sie die [!UICONTROL Adword Cost] Metrik, die Sie gerade erstellt haben
1. Legen Sie die [!UICONTROL Time period] nach `All-time`und [!UICONTROL Interval] nach `None`
1. Unter dem `Group by` Registerkarte hinzufügen `campaign` as [!UICONTROL grouping field]und klicken Sie auf `Add All` in das Feld ein.
1. Dieser Bericht zeigt Ihre Allzeit [!DNL AdWords] Kosten nach Kampagnen

**2. Erstellen Sie einen Bericht, der neue Benutzer nach Kampagnen zählt:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create report]**
1. Wählen Sie die `New users` Metrik, die die Anzahl neuer registrierter Benutzer im Zeitverlauf zählt
1. Legen Sie die [!UICONTROL Time period] nach `All-time`und [!UICONTROL Interval] nach `None`
1. Unter dem `Group by` Registerkarte hinzufügen `campaign` as `grouping field`und klicken Sie auf **`Add All`** im Feld
1. Dieser Bericht zeigt Ihre gesamten registrierten Benutzer nach Kampagnen

**3. Erstellen Sie einen Bericht, der die durchschnittliche LTV-Nutzung nach Kampagnen segmentiert:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create report]**
1. Wählen Sie die `Average lifetime revenue` Metrik, die den durchschnittlichen Lebensdauerumsatz eines Benutzers berechnet
1. Legen Sie die [!UICONTROL Time period] nach `All-time`und [!UICONTROL Interval] nach `None`
1. Unter dem `Group by` Registerkarte hinzufügen `campaign` oder `utm\_campaign` as [!UICONTROL grouping field]und klicken Sie auf `Add All` im Feld
1. Dieser Bericht zeigt den durchschnittlichen Umsatz der Benutzer während der Lebensdauer nach Kampagnen.

**Berechnen Sie schließlich den Kampagnen-ROI, indem Sie diese drei Analysen in einem Bericht zusammenführen:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Fügen Sie als Eingabe hinzu und verwenden Sie die drei oben verwendeten Metriken. Jedem wird ein Brief zugewiesen (z. B.\[`A`\], \[`B`\] und \[`C`\])
1. [!UICONTROL Cost]: Fügen Sie die Metrik AdWords-Kosten hinzu - dies ist die Variable \[A\]. Dadurch werden Kosten nach Kampagnen zurückgegeben.
1. [!UICONTROL Users]: Fügen Sie die Metrik Neue Benutzer hinzu - dies ist die Variable \[B\]. Dadurch wird die Anzahl der Benutzer nach Kampagnen zurückgegeben.
1. [!UICONTROL LTV]: Metrik &quot;Durchschnittlicher Lebensdauerumsatz&quot;hinzufügen - dies ist Variable \[`C`\]. Dadurch wird LTV nach Kampagnen zurückgegeben.

1. Klicken Sie auf das Symbol zum Ausblenden neben dem Wortdiagramm, damit Sie sich auf die Tabelle konzentrieren können.
1. Jetzt verwenden `Add Formula` , um diese Metriken wie folgt zu kombinieren:
1. [!UICONTROL ROI]: Formel eingeben `(\[C\]-\[A\]/\[B\])/(\[A\]/\[B\])`, wenn \[`A`\] steht für `Ad Cost by Campaigns`, \[`B`\] steht für `New users by campaigns`, und \[`C`\] `LTV by campaigns`. Dadurch wird das Verhältnis von (durchschnittlicher Benutzer-LTV - durchschnittliche Kosten pro Akquise) / (durchschnittliche Kosten pro Akquise) zurückgegeben.
1. [!UICONTROL Avg Return per User]: Formel eingeben **\[`C`\]-(\[`A`\]/\[`B`\])**. Dadurch wird die durchschnittliche Spanne zurückgegeben, die ein Benutzer durch Berechnung (durchschnittliche LTV-Nutzer) - (durchschnittliche Kosten pro Akquisition) ermittelt hat.
1. [!UICONTROL CPA]: Formel eingeben **`\[A\]/\[B\]`**. Dadurch werden die tatsächlichen Kampagnenkosten pro Akquise zurückgegeben.
1. Andere potenzielle Metriken, die aus einbezogen werden können [!DNL AdWords] -Daten umfassen Summen von  `Impressions` und `adClicks` (von [!DNL AdWords] Daten) zusammen mit der Gesamtsumme `number of orders` über eine bestimmte Kampagne erstellt werden.
1. Es kann auch interessant sein, den ROI auf Basis von LTV 30 Tage und 90 Tage nach der Registrierung oder Erstkauf eines Benutzers zu berechnen.

1. Sie können einfach auf Ihre Metriken und Formeln klicken und ziehen, um die Spalten Ihres Berichts neu anzuordnen.
1. Benennen Sie Ihren Bericht und achten Sie darauf, ihn als Tabelle zu speichern.

## Produktkampagnen

Führen Sie produktspezifische Werbung durch? Wenn ja, können Sie den ROI für diese Kampagnen messen, indem Sie den Umsatz/die Kosten für bestimmte Produkte berechnen.

>[!NOTE]
>
>In diesem Beispiel wird davon ausgegangen, dass alle Kampagnenkosten ausschließlich zur Generierung von Käufen für bestimmte Produkte verwendet wurden. Wenn man davon ausgeht, dass alle Kosten für die Generierung von Käufen ausgegeben wurden, berücksichtigt der resultierende ROI das Worst-Case-Szenario (höchste Kosten pro Kauf). Sie können sicher sein, dass Ihr tatsächlicher ROI höher ist als diese Berechnung. Beispiel: Angenommen, Sie haben 20 USD für eine Kampagne ausgegeben, aus der 10 neue Benutzer und 10 Käufe stammen, belaufen sich Ihre tatsächlichen Kosten pro Kauf auf 1 USD. Unter der Annahme, dass alle Kosten für den Erwerb neuer Benutzer anfielen, belaufen sich die Kosten pro Kauf auf 2 USD.)*

Bevor Sie beginnen, [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=en) , um die folgenden Dimensionen mit der Tabelle der Zeileneinträge zu verknüpfen (`sales\_flat\_order\_item, order\_item`):

* Quelle der Bestellung (wenn Sie nur die Verweisquelle auf Benutzerebene verfolgen und dann der Quelle des Benutzers beitreten)
* Bestellungskampagne (wenn Sie nur die Verweisquelle auf Benutzerebene verfolgen und dann der Kampagne des Benutzers beitreten)
* Bestellmedium (wenn Sie nur die Verweisquelle auf Benutzerebene verfolgen und dann dem Medium des Benutzers beitreten)

**1. Erstellen Sie zunächst ein Diagramm, das den Umsatz pro Kampagne für bestimmte Produkte zurückgibt:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Wählen Sie die `Revenue by items` Metrik zur Berechnung des Umsatzes auf der Ebene der Zeileneinträge
1. Legen Sie die [!UICONTROL Time period] nach `All-time`und [!UICONTROL Interval] nach `None`
1. Unter dem `Filter by` Registerkarte hinzufügen `product name 'IN'` Produkt `A`, Produkt `B`, Produkt `C`, ...&quot; und alle Produktnamen einschließen, die in der Zielgruppe Ihrer Kampagne durch Kommas getrennt sind (z. B. `product name 'IN' yellow t-shirt`, `red t-shirt, blue t-shirt`)
1. Unter dem `Group by` Registerkarte hinzufügen `order's campaign` oder `order's utm\_campaign` as `grouping` und klicken Sie auf **[!UICONTROL Add All]** im Feld
1. Dieser Bericht zeigt Ihnen den Umsatz für bestimmte Produkte nach Kampagnen

**2. Um den ROI zu berechnen, kombinieren Sie erneut Metriken in einem Bericht:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Fügen Sie die `Revenue by items` Metrik, dem Filter und der Gruppe nach Anweisungen aus dem obigen Kampagnenbericht für bestimmte Produkte folgen und auf **[!UICONTROL Hide]** unterhalb des Skalarwerts der Metrik
1. Fügen Sie nun die [!DNL AdWords Cost] Metrik, folgen Sie dem Filter und der Gruppe nach Anweisungen aus dem `Ad cost by campaigns` Bericht, den Sie im `User acquisition campaigns` Abschnitt oben; Klicken Sie dann auf **[!UICONTROL Hide]** unterhalb des Skalarwerts der Metrik
1. Fügen Sie bei diesen Metriken Formeln hinzu:
1. [!UICONTROL ROI]: Formel eingeben `\[A\]/\[B\]`, wenn `\[A\]` Stellt `Revenue per campaign for specific product(s)` und `\[B\]` Stellt `Ad cost by campaigns`. Dadurch wird das Verhältnis von (Umsatz für bestimmte Produkte) / (Kampagnenkosten) zurückgegeben.
1. [!UICONTROL Return]: Formel eingeben `\[A\]-\[B\]`. Dadurch wird die durchschnittliche Spanne zurückgegeben, die ein Benutzer durch Berechnung (durchschnittliche LTV-Nutzer) - (durchschnittliche Kosten pro Akquise) erzielt hat.
1. (Optional) [!UICONTROL Revenue]: Einblenden des `Revenue by items` Metrik zum Anzeigen des Umsatzes für bestimmte Produkte pro Kampagnen
1. (Optional) [!UICONTROL Cost]: Einblenden des `AdWords Cost` Metrik, um die Kosten für Kampagnen anzuzeigen

1. Benennen Sie den Bericht und speichern Sie ihn als Tabelle

**3. Wiederholen Sie die obigen Schritte 1 und 2 für jedes Ihrer beworbenen Produkte oder Produktgruppen.**

## Verwandte Dokumentation

* [Verweisquelle für Bestellungen verfolgen über [!DNL Google Analytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Tracking der Verweisquelle von Benutzern in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Tracking von Benutzergeräte-, Browser- und Betriebssystemdaten in Ihrer Datenbank](../analysis/track-usr-dev-browser.md)
* [Entdecken Sie Ihre wertvollsten Akquisequellen und -kanäle](../analysis/most-value-source-channel.md)
* [Verbinden Sie Ihre [!DNL Google Adwords] account](../importing-data/integrations/google-adwords.md)
* [Wie funktioniert [!DNL Google Analytics] UTM-Attribution funktioniert?](../analysis/utm-attributes.md)
* [Fünf Best Practices für das UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
