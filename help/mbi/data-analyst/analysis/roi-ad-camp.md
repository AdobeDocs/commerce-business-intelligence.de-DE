---
title: Steigern des ROI in Ihren Werbekampagnen
description: Erfahren Sie mehr über einige verschiedene Methoden zur Bewertung der Kampagnenleistung.
exl-id: 4f2bf408-eeaf-4dbf-b62e-89426734640a
role: Admin, User
feature: Data Warehouse Manager, Reports, Campaigns
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 0%

---

# Advertising-Kampagnen und ROI

Mit [!DNL Adobe Commerce Intelligence] können Sie Werbungskosten[&#x200B; und Umsatzdaten einfach aus Ihrer &#x200B;](../../data-analyst/importing-data/integrations/google-adwords.md) zusammenführen. Auf diese Weise können Sie ermitteln, welche Kampagnen den höchsten ROI aufweisen. In diesem Thema werden einige verschiedene Methoden zur Bewertung der Kampagnenleistung untersucht.

## Voraussetzungen

* Importieren Sie Ihre Werbungskostendaten:
   * [Verbinden Sie Ihre [!DNL Google AdWords] mit [!DNL Commerce Intelligence]](../importing-data/integrations/google-adwords.md): Dadurch werden Ihre [!DNL Adwords] in [!DNL Commerce Intelligence] synchronisiert.
   * [Andere Werbungskostendaten hochladen](../importing-data/connecting-data/import-offline-ad-data.md): Dies wird für Kanäle ohne direkten Connector für [!DNL Commerce Intelligence] empfohlen
   * Wenn Sie Kostendaten aus mehreren Quellen importieren, können [&#x200B; die &#x200B;](../../best-practices/consolidating-your-tables.md) in [!DNL Commerce Intelligence] (konsolidieren). Senden [&#x200B; einfach ein Support-Ticket](../../guide-overview.md#Submitting-a-Support-Ticket).
* [Tracking von Kanaldaten zur Benutzerakquise](../analysis/google-track-user-acq.md)

## Kampagnen zur Benutzerakquise

Kampagnen, die auf die Benutzerakquise abzielen, können aus vielen Perspektiven gemessen werden, darunter:

1. Die Anzahl der neu akquirierten Benutzenden von Kampagnen
1. Konversionsrate von der Registrierung bis zum Kauf von Kampagnen
1. Der ROI von Kampagnen auf der Basis des durchschnittlichen Lebenszeitwerts der Benutzenden (LTV)

Die oben unter (1) und (2) genannten Analysen werden in einem separaten Tutorial zum [&#x200B; Ihrer Top-Marketing-Kanäle &#x200B;](../analysis/most-value-source-channel.md). Hier können Sie Analysen (3) zur Messung des Kampagnen-ROI im Zeitverlauf durchführen. Dies beantwortet die Frage, ob die durch eine bestimmte Kampagne erzielten Benutzerinnen und Benutzer über die gesamte Lebensdauer einen Umsatz generierten, der die Anschaffungskosten deckte.

>[!NOTE]
>
>In diesem Beispiel wird davon ausgegangen, dass alle Kampagnenkosten ausschließlich zur Akquise neuer Benutzer verwendet wurden. In Wirklichkeit werden Ihre Kampagnenkosten auch mit der Akquise von nicht konvertierten Besuchen, Wiederholungskäufern und dergleichen geteilt. Unter der Annahme, dass alle Kosten zur Akquise neuer registrierter Benutzer verwendet werden, entspricht der resultierende ROI dem Worst-Case-Szenario (höchste Kosten pro Akquise). Sie können sicher sein, dass Ihr tatsächlicher ROI höher ist als Ihre Berechnung.
>
>Beispiel: Angenommen, Sie haben 20 USD für eine Kampagne ausgegeben, die 10 neue Benutzende und 10 Wiederholungskäufer generiert hat, dann betragen die tatsächlichen Kosten pro neuem Benutzenden 1 USD. Doch unter der Annahme, dass alle Kosten für die Akquise neuer Nutzer aufgewendet wurden, betragen die Kosten pro Akquise 2 Dollar.

**1. Erstellen Sie zunächst ein Diagramm, das Ihre Anzeigenkosten nach Kampagnen segmentiert:**

1. Erstellen Sie eine [!UICONTROL Metric], die Ihre Ausgaben im Zeitverlauf zusammenfasst
1. Zu [!UICONTROL Data > Metrics]
1. Wählen Sie `Add New Metric` aus und wählen Sie die [!DNL `Adwords...`] aus, in der Ihre [!DNL AdWords] Kostendaten erfasst werden.
1. Geben Sie der Metrik im Metrik-Editor einen Namen (z. B. [!UICONTROL AdWord Cost])
1. Führen Sie mithilfe der Dropdown-Listen einen **Summe** für die Spalte `adCost` in der Tabelle [!DNL Adwords...] (Änderung) durch, die nach der Spalte `date` sortiert ist.
   ![Erfolgsmeldung nach dem Hinzufügen einer neuen Metrik](../../assets/success-add-new-metric.png)<!--="500" height="303"}-->
1. Klicken Sie oben auf `Back to Metric List` und wechseln Sie zu einem beliebigen Dashboard.

1. Erstellen eines Berichts zu den Ausgaben von Segmenten nach Kampagnen
1. Klicken Sie in einem beliebigen Dashboard auf [!UICONTROL Add Report > Create report]
1. Wählen Sie die soeben erstellte [!UICONTROL Adword Cost] aus
1. Legen Sie die [!UICONTROL Time period] auf `All-time` und [!UICONTROL Interval] auf `None` fest.
1. Fügen Sie auf der Registerkarte `Group by` die Option `campaign` als [!UICONTROL grouping field] hinzu und klicken Sie in das Feld `Add All` .
1. Dieser Bericht zeigt Ihre [!DNL AdWords] nach Kampagnen an

**2. Erstellen Sie einen Bericht, der neue Benutzer nach Kampagnen zählt:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create report]**
1. Wählen Sie die `New users` Metrik, die die Anzahl der neu registrierten Benutzer im Zeitverlauf zählt
1. Legen Sie die [!UICONTROL Time period] auf `All-time` und [!UICONTROL Interval] auf `None` fest.
1. Fügen Sie auf der Registerkarte `Group by` die `campaign` als `grouping field` hinzu und klicken Sie in das Feld **`Add All`** .
1. Dieser Bericht zeigt die für Sie registrierten Benutzer nach Kampagnen

**3. Erstellen Sie einen Bericht, der durchschnittliche Benutzer-LTV nach Kampagnen segmentiert:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create report]**
1. Wählen Sie die `Average lifetime revenue` Metrik aus, die den Lebensdauerumsatz eines durchschnittlichen Benutzers berechnet
1. Legen Sie die [!UICONTROL Time period] auf `All-time` und [!UICONTROL Interval] auf `None` fest.
1. Fügen Sie auf der Registerkarte `Group by` als `campaign` `utm\_campaign` oder [!UICONTROL grouping field] hinzu und klicken Sie in das Feld `Add All` .
1. Dieser Bericht zeigt den durchschnittlichen Umsatz aus der Nutzungsdauer nach Kampagnen an

**Berechnen Sie abschließend den Kampagnen-ROI, indem Sie diese drei Analysen in einem Bericht zusammenführen:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Fügen Sie als Eingabe die drei oben verwendeten Metriken hinzu. Jedem wird ein Buchstabe zugewiesen (z. B.\[`A`\], \[`B`\] und \[`C`\])
1. [!UICONTROL Cost]: Fügen Sie die Metrik AdWords-Kosten hinzu - dies ist die Variable \[A\]. Dadurch werden die Kosten nach Kampagnen zurückgegeben.
1. [!UICONTROL Users]: Fügen Sie die Metrik Neue Benutzer hinzu - dies ist die Variable \[B\]. Gibt die Anzahl der Benutzer nach Kampagnen zurück.
1. [!UICONTROL LTV]: Fügen Sie die Metrik Durchschnittlicher Lebensdauerumsatz hinzu - dies ist die Variable \[`C`\]. Dadurch wird LTV nach Kampagnen zurückgegeben.

1. Klicken Sie auf das Symbol zum Ausblenden neben dem Wortdiagramm, um den Fokus auf die Tabelle zu legen
1. Verwenden Sie jetzt `Add Formula` , um diese Metriken wie folgt zu kombinieren:
1. [!UICONTROL ROI]: Geben Sie die `(\[C\]-\[A\]/\[B\])/(\[A\]/\[B\])` ein, wenn \[`A`\] `Ad Cost by Campaigns`, \[`B`\] `New users by campaigns` und \[`C`\] `LTV by campaigns`. Dies gibt das Verhältnis von (durchschnittliche Benutzer-LTV - durchschnittliche Kosten pro Akquise) / (durchschnittliche Kosten pro Akquise) zurück
1. [!UICONTROL Avg Return per User]: Geben Sie die Formel **\[`C`\]-(\[`A`\]/\[`B`\])**. Dies gibt die durchschnittliche Marge zurück, die ein Benutzer durch Berechnung (durchschnittliche Benutzer-LTV) erzielt hat - (durchschnittliche Kosten pro Akquise).
1. [!UICONTROL CPA]: Geben Sie die **`\[A\]/\[B\]`** ein. Dadurch werden die tatsächlichen Kampagnenkosten pro Akquise zurückgegeben.
1. Zu den weiteren potenziellen Metriken, die aus [!DNL AdWords] Daten einbezogen werden können, gehören Summen von `Impressions` und `adClicks` (aus [!DNL AdWords]) sowie die Gesamtzahl der `number of orders`, die über eine bestimmte Kampagne getätigt wurden.
1. Es kann auch interessant sein, den ROI basierend auf LTV 30 Tage und 90 Tage nach der Registrierung oder dem Erstkauf eines Benutzers zu berechnen.

1. Sie können Ihre Metriken und Formeln anklicken und ziehen, um die Spalten Ihres Berichts neu anzuordnen
1. Benennen Sie Ihren Bericht und stellen Sie sicher, dass Sie ihn als Tabelle speichern.

## Produktkampagnen

Führen Sie produktspezifische Anzeigen durch? Wenn ja, können Sie den ROI dieser Kampagnen messen, indem Sie den Umsatz / die Kosten für bestimmte Produkte berechnen.

>[!NOTE]
>
>In diesem Beispiel wird davon ausgegangen, dass alle Kampagnenkosten ausschließlich zur Generierung von Käufen bestimmter Produkte verwendet wurden. Unter der Annahme, dass alle Kosten für die Generierung von Käufen aufgewendet wurden, entfällt der resultierende ROI auf das Worst-Case-Szenario (höchste Kosten pro Kauf). Sie können sicher sein, dass Ihr tatsächlicher ROI höher ist als diese Berechnung. Beispiel: Angenommen, Sie haben 20 USD für eine Kampagne ausgegeben, die 10 neue Benutzende und 10 Käufe generiert hat, dann betragen die tatsächlichen Kosten pro Kauf 1 USD. Unter der Annahme, dass alle Kosten für die Akquise neuer Benutzer aufgewendet wurden, betragen die Kosten pro Kauf 2 USD.

Bevor Sie beginnen, [&#x200B; Sie ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies.html?lang=de), um die folgenden Dimensionen mit Ihrer Zeileneintragstabelle zu verbinden (`sales\_flat\_order\_item, order\_item`):

* Quelle der Bestellung (wenn Sie nur die Empfehlungsquelle auf Benutzerebene verfolgen, dann fügen Sie die Quelle des Benutzers hinzu)
* Kampagne des Auftrags (wenn Sie nur die Empfehlungsquelle auf Benutzerebene verfolgen, dann der Kampagne des Benutzers beitreten)
* Medium der Bestellung (wenn Sie nur die Empfehlungsquelle auf Benutzerebene verfolgen, verbinden Sie dann das Medium des Benutzers)

**1. Erstellen Sie nun zunächst ein Diagramm, das den Umsatz pro Kampagne für bestimmte Produkte zurückgibt:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Wählen Sie die `Revenue by items`, die den Umsatz auf der Ebene der Zeileneinträge berechnet
1. Legen Sie die [!UICONTROL Time period] auf `All-time` und [!UICONTROL Interval] auf `None` fest.
1. Fügen Sie auf der Registerkarte &quot;`Filter by`&quot; `product name 'IN'` &quot;`A`, `B`, `C`, …“ hinzu und fügen Sie alle Produktnamen, auf die Ihre Kampagne abzielt, durch ein Komma getrennt ein (z. B. `product name 'IN' yellow t-shirt`, `red t-shirt, blue t-shirt`)
1. Fügen Sie auf der Registerkarte `Group by` `order's campaign` oder `order's utm\_campaign` als `grouping` Feld hinzu und klicken Sie in das Feld **[!UICONTROL Add All]** .
1. Dieser Bericht zeigt den Umsatz für bestimmte Produkte nach Kampagnen an

**2. Um den ROI zu berechnen, kombinieren Sie die Metriken erneut in einem Bericht:**

1. Klicken Sie in einem beliebigen Dashboard auf **[!UICONTROL Add Report > Create new report]**
1. Fügen Sie die `Revenue by items` Metrik hinzu, indem Sie dem obigen Bericht Filtern und Gruppieren nach Anweisungen aus der Kampagne für bestimmte Produkte folgen, und klicken Sie **[!UICONTROL Hide]** unter dem Skalarwert der Metrik
1. Fügen Sie nun die [!DNL AdWords Cost] Metrik hinzu und folgen Sie den Anweisungen in Filtern und Gruppieren nach aus dem `Ad cost by campaigns` Bericht, den Sie im obigen Abschnitt `User acquisition campaigns` untersucht haben. Klicken Sie dann unter dem Skalarwert der Metrik auf **[!UICONTROL Hide]**
1. Fügen Sie mit diesen Metriken Formeln hinzu:
1. [!UICONTROL ROI]: Geben Sie die `\[A\]/\[B\]` ein, wenn `\[A\]` für `Revenue per campaign for specific product(s)` und `\[B\]` für `Ad cost by campaigns` steht. Gibt das Verhältnis von (Umsatz für bestimmte Produkte) zu (Kampagnenkosten) zurück.
1. [!UICONTROL Return]: Geben Sie die `\[A\]-\[B\]` ein. Dies gibt die durchschnittliche Spanne zurück, die ein Benutzer durch Berechnung erzielt hat (durchschnittliche Benutzerkosten pro Akquise)
   1. (Optional) [!UICONTROL Revenue]: Blenden Sie die `Revenue by items` ein, um den Umsatz für bestimmte Produkte pro Kampagne anzuzeigen
   1. (Optional) [!UICONTROL Cost]: Blenden Sie die `AdWords Cost` ein, um die Kosten für Kampagnen anzuzeigen

1. Geben Sie Ihrem Bericht einen Namen und speichern Sie ihn unbedingt als Tabelle

**3. Wiederholen Sie die obigen Schritte 1 und 2 für jedes Ihrer beworbenen Produkte oder jede Produktgruppe.**

## Verwandte Dokumentation

* [Verfolgen Sie die Quelle der Bestellungsreferenz über  [!DNL Google Analytics] E-Commerce](../importing-data/integrations/google-ecommerce.md)
* [Verfolgen Sie die Quelle der Benutzerreferenz in Ihrer Datenbank](../analysis/google-track-user-acq.md)
* [Benutzergeräte-, Browser- und Betriebssystemdaten in der Datenbank tracken](../analysis/track-usr-dev-browser.md)
* [Entdecken Sie Ihre wertvollsten Akquisitionsquellen und -kanäle](../analysis/most-value-source-channel.md)
* [Konto  [!DNL Google Adwords] &#x200B;](../importing-data/integrations/google-adwords.md)
* [Wie funktioniert  [!DNL Google Analytics]  UTM-Attribution?](../analysis/utm-attributes.md)
* [Fünf Best Practices für UTM-Tagging in [!DNL Google Analytics]](../../best-practices/utm-tagging-google.md)
