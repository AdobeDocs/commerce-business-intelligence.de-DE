---
title: Report Builder der Kohorte
description: Erfahren Sie mehr über die Analyse von Benutzergruppen, die über ihre Lebenszyklen ähnliche Merkmale aufweisen.
exl-id: d80c5389-7256-40e0-86e0-49903113f93d
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 0%

---

# Report Builder der Kohorte

Wollten Sie schon einmal untersuchen, wie sich unterschiedliche Untergruppen Ihrer Benutzer im Laufe der Zeit verhalten? Haben Sie sich beispielsweise schon einmal gefragt, ob Benutzer, die sich während eines Promo-Zeitraums registrieren, einen höheren durchschnittlichen Lebenszeitumsatz haben als diejenigen, die dies nicht tun? Wenn die Antwort `Yes` ist, ist der `Cohort Report Builder` das perfekte Tool für Sie. [!DNL Adobe Commerce Intelligence] ist so optimiert, dass diese Analyse durchgeführt und für Ihr Unternehmen relevant wird.

## Was ist eine Kohortenanalyse? {#what}

`Cohort` -Analyse kann allgemein definiert werden als die Analyse von Benutzergruppen, die über ihre Lebenszyklen ähnliche Merkmale aufweisen. Damit können Sie Verhaltenstrends über verschiedene Benutzergruppen hinweg identifizieren.

Eine ausführliche Einführung in die `cohort` Analyse finden Sie auf [dieser Seite](https://www.cohortanalysis.com/).

Im Dashboard [!DNL Commerce Intelligence] können Sie Benutzer `cohorts` einfach basierend auf einem `cohort` -Datum und einer Metrik in Ihrem Konto erstellen.

## Warum ist die Kohortenanalyse wichtig? {#important}

Wie oben erwähnt, können Sie mit der `cohort`-Analyse Verhaltenstrends zwischen verschiedenen Benutzergruppen identifizieren. Mit einem soliden Verständnis, wie sich bestimmte Gruppen verhalten, können Sie Ihre Entscheidungen und Ausgaben so anpassen, dass Sie Ihren Umsatz maximieren können. Nehmen wir beispielsweise eine Analyse des Lebensdauerumsatzes `cohort` - obwohl diese Art von Analyse aus vielen Gründen von Vorteil ist, sind die unmittelbaren Entscheidungen über die Kundenakquise besser.

## Wie erstelle ich meine eigene `cohort`-Analyse?

### Neue Architektur

Dies sind die Anweisungen für die Verwendung des `Cohort Report Builder` auf der [neuen Architektur](../../administrator/account-management/new-architecture.md).

1. Klicken Sie auf der linken Registerkarte auf **[!UICONTROL Report Builder]** oder auf **[!UICONTROL Add Report** > **Create Report]** in einem beliebigen Dashboard.

1. Klicken Sie im Auswahlbildschirm `Report Builder` neben der Option `Visual Report Builder` auf **[!UICONTROL Create Report]** .

**Hinzufügen einer Metrik**

Fügen Sie nun die Metrik hinzu, für die Sie die Analyse durchführen möchten (Beispiel: `Revenue` oder `Orders`).`Report Builder`

>[!NOTE]
>
>Native [!DNL Google Analytics] -Metriken sind nicht mit dem `Cohort Report Builder` kompatibel.

**Umschalten der Metrikansicht auf`Cohort`**

![](../../assets/visual-report-builder-cohort-toggle.png)

Dadurch wird ein neues Fenster geöffnet, in dem die Details des `Cohort` Berichts konfiguriert werden.

### Zum Erstellen eines `Cohort` -Berichts sind fünf Spezifikationen erforderlich:

1. Gruppieren der `cohorts`
1. Der Zeitraum `cohort`
1. Die Anzahl der anzuzeigenden `cohorts`
1. Die Mindestmenge an Daten, die jeder `cohort` enthalten muss
1. Zeitraum nach dem Auftreten von `cohort`

#### 1. Gruppierung `cohorts`

`Cohorts` werden nach einem Zeitstempel gruppiert, z. B. dem **Registrierungsdatum** oder dem **Datum der ersten Bestellung**.

>[!NOTE]
>
>Sie können nicht denselben Zeitstempel verwenden, auf dem die Metrik für das Datum `cohort` basiert. Für eine Analyse, für die dies erforderlich ist, können Sie stattdessen die `Standard report builder` verwenden.

#### 2. `Cohort` Zeitraum

Wählen Sie den Zeitraum aus, nach dem `cohorts` gruppiert werden soll. Mit anderen Worten, welcher Teil des Zeitstempels, den Sie oben ausgewählt haben, ist am wichtigsten: der `week`, `month`, `quarter` oder `year`? Ihr Bericht zeigt Daten in den von Ihnen ausgewählten Intervallen an

#### 3. und 4. Legen Sie die Anzahl der anzuzeigenden `cohorts` fest und wie viele Daten jeder `cohort` aufweisen muss.

Mit diesen Parametern können Sie nur die `cohorts` anzeigen, die Sie interessieren, und das praktische Feld `Preview` am unteren Rand des Fensters zeigt Ihnen genau, welche Kohorten in Ihrem Bericht angezeigt werden.

Standardmäßig ist der aktuelle `cohort` nicht enthalten, es sei denn, Sie ändern den Mindestwert der für jeden `cohort` erforderlichen Daten in `0`. In diesem Fall enthält der `cohort` für den aktuellen Zeitraum nur teilweise Daten.

#### 5. Zeitraum nach `Cohort` Vorkommen

Mit dieser Funktion können Sie den Datumsbereich festlegen, den Sie für den ausgewählten `cohorts` anzeigen. Wenn Sie beispielsweise 24 monatliche `cohorts` basierend auf `customer's first order date` anzeigen möchten, aber nur an den ersten drei Monaten der Daten für jeden `cohort` interessiert sind, können Sie die `number of cohorts to view` auf `24` und die `time range after cohort occurrence` auf `3` setzen.

Das Intervall für diesen Wert ändert sich mit dem, was Sie in `cohort time period` ausgewählt haben, und der Wert ist standardmäßig auf `12` eingestellt. Der Wert ändert sich nur, wenn Sie auf das Kalendersymbol klicken, um ihn zu bearbeiten.

![](../../assets/cohort-time-range.png)

#### Sonstige Hinweise

* [!UICONTROL Filters]: Wird auf Ihre Metriken angewendet, bleiben sie intakt, wenn Sie zwischen `Standard` und `Cohort` Ansichten wechseln.

* Siehe [`Perspectives`](#perspectives).

#### Beispiel

Hier ist ein Beispiel, um alles zusammenzuziehen. In diesem Beispiel möchte ich das Bestellverhalten nach dem ersten Kauf eines `cohort` überprüfen, um zu sehen, ob diese Kohorte in den nächsten sechs Monaten zurückkehrt und Wiederholungskäufe tätigt.

![Auftragskohorte](../../assets/crb_example.gif)

### Alte Architektur

#### Alte Architektur {#personalinfo}

Im Folgenden finden Sie Anweisungen, die speziell für die ältere Version von `Cohort Report Builder` gelten. Wenn Sie an der Verwendung der neuen Version interessiert sind, finden Sie unter [Neue Architektur](../../administrator/account-management/new-architecture.md) weitere Informationen zur Migration auf ein [!DNL Commerce Intelligence] Konto für neue Architektur.

#### Wie erstelle ich meine eigene `cohort`-Analyse? {#create}

![](../../assets/create-cohort-analysis.png)

`Cohort` Analyse in Aktion! Hier können Sie sehen, dass der Umsatz im Laufe der Zeit kumuliert und pro Benutzer zunimmt.

Dieser Abschnitt erläutert Ihnen schrittweise, wie Sie Ihre eigene `cohort` -Analyse erstellen. Beispiele (und animierte GIF, die den Prozess demonstrieren) finden Sie im Abschnitt [Beispiele](#examples) dieses Themas.

1. Klicken Sie auf der linken Registerkarte auf **[!UICONTROL Report Builder]** oder auf **[!UICONTROL Add Report** > **Create Report]** in einem beliebigen Dashboard.

1. Klicken Sie im Bildschirm `Report Builder Selection` auf **[!UICONTROL Create Report]** neben der Option `Cohort Analysis` .

#### Hinzufügen einer Metrik

Fügen Sie nun die Metrik (Beispiel: `Revenue` oder `Number of orders`) hinzu, für die Sie die Analyse durchführen möchten.`Cohort Report Builder`

>[!NOTE]
>
>Native [!DNL Google Analytics] -Metriken sind nicht mit dem `Cohort Report Builder` kompatibel.

#### Kohortendatum auswählen {#date}

Der nächste Schritt besteht darin, den `cohort date` anzugeben. Dies ist das Datum, nach dem Ihre Benutzer gruppiert werden. Dies kann beispielsweise `User's first order date` oder `User's registration date` sein.

>[!NOTE]
>
>Sie können nicht dasselbe Datum verwenden, an dem die Metrik erstellt wurde (Beispiel: `created at`), wie die `cohort date`.

#### Festlegen von Intervall und Zeitraum

Legen Sie als Nächstes die `Interval` und die `Time Period` fest.

`Interval`
Mit der Option `Interval` können Sie die `length` Ihres `cohorts` festlegen. Wenn dies beispielsweise auf &quot;`Month`&quot;festgelegt ist, wird Ihr Bericht in Monaten gemessen.

Über das Menü **Dauer** können Sie die Darstellung dieser Intervalle auf der X-Achse ändern.

`Time Period`
Verwenden Sie das Menü `Time Period` , um den zu analysierenden Benutzer `cohorts` auszuwählen. Sie können jeden `cohort` anzeigen, aus einer Liste auswählen, einen Zeitraum angeben oder einen rollierenden Zeitraum von `cohorts` festlegen, der eingeschlossen werden soll. Wenn Sie beispielsweise die Option `Specific Cohorts` verwendet haben, können Sie bestimmte Monate auswählen, die in die Analyse einbezogen werden sollen:

![Verwenden des `Time Period` -Menüs zum Hinzufügen von spezifischem `Cohorts`](../../assets/Cohort_Time_Period.gif)

Wenn Sie Sie `cohorts` nach Registrierungsdatum gruppieren und dann April, Mai und Juni in der Liste `Specific Cohorts` auswählen, werden alle Benutzer einbezogen, die sich in diesen Monaten registriert haben.

#### X-Achse definieren

Unter &quot;`duration`&quot; können Sie die X-Achsen-Einstellungen des Diagramms definieren. Das heißt, wie viele Zeiträume jeder Datenpunkt darstellt und wie viele Datenpunkte in die Analyse einbezogen werden sollen.

#### Auswählen der `counting members`-Tabelle

Wenn Sie sich dafür entschieden haben, Benutzer mit einer `cohort date` zu gruppieren, die von einer anderen Tabelle verbunden wurde, wird möglicherweise eine `counting members in the … table` -Option angezeigt.

![](../../assets/Cohort_Counting_Members_option.png)

Sehen Sie sich ein Beispiel an, um diese Einstellung zu verstehen. Angenommen, Sie haben einen Bericht erstellt, der eine `Revenue` -Metrik durch `Customer's registration date` kohortet. Sie wollten auch die Perspektive `Average value per cohort member` verwenden, um den Umsatz pro Käufer im Zeitverlauf anzuzeigen. Um den Durchschnittswert pro Käufer zu ermitteln, müssen Sie entscheiden, nach wie vielen Käufern Sie unterteilen. Ist dies die Anzahl der registrierten Kunden in Ihrer `customers`-Tabelle oder die Anzahl unterschiedlicher Käufer in Ihrem `orders table` für den gleichen Zeitraum?

Diese Einstellung beantwortet diese Frage. Mitglieder in der `customers` -Tabelle zählen alle Kunden (unabhängig davon, ob sie einen Kauf getätigt haben) im Durchschnitt. Die Zählung der Mitglieder in der Tabelle `orders` umfasst nur Kunden, die einen Kauf getätigt haben.

#### Perspektive auswählen {#perspective}

Nachdem Sie die Metrik definiert haben und wie Sie sie analysieren möchten, können Sie den zu verwendenden `perspective` auswählen.

Direkt über der Berichtvisualisierung befindet sich ein Dropdown-Menü mit `perspective` -Einstellungen.

Siehe [Perspektiven](#perspectives).

![](../../assets/Cohort_Perspective_Menu.png)

## Beispiele für Kohortenanalysen {#examples}

Nachdem Sie nun durchgemacht haben, wie Sie eine `cohort` -Analyse erstellen, sehen Sie sich einige Beispiele an.

### Ich möchte wissen, wie mein Benutzer &quot;`cohorts`&quot; im Laufe der Zeit wächst.

![Benutzer `cohorts`, der im Laufe der Zeit wächst](../../assets/cohort1.gif)

In diesem Beispiel haben Sie die Metrik `Revenue` analysiert, Ihre Kohorten nach `customer's first order date` gruppiert und die 8 neuesten `cohorts` (definiert im Menü `Time Period`) ausgewählt, die in die Analyse aufgenommen werden sollen. Um zu sehen, wie die Kohorten im Laufe der Zeit gewachsen sind, haben Sie die `Cumulative Average Value per Cohort Member` `perspective` verwendet.

### Ich möchte im Durchschnitt wissen, wie viele Bestellungen ein Benutzer an verschiedenen Punkten seines Lebens tätigt.

(../../assets/cohort2.gif

In diesem Beispiel haben Sie die Metrik `Number of orders` analysiert, Ihre Kohorten nach `customer's first order date` gruppiert und die acht neuesten Kohorten (definiert im Menü `Time Period` ) in die Analyse aufgenommen. Um die durchschnittliche Anzahl der Bestellungen für jede Kohorte anzuzeigen, haben Sie die `perspective` in `Average Value per Cohort Member` geändert.

### Ich möchte verstehen, wie die zukünftige Kaufaktivität eines Benutzers mit der Aktivität des ersten Monats im Unternehmen verglichen wird.

![Vergleich der künftigen Kaufaktivität eines Benutzers mit seiner ersten Aktivitätsmonat](../../assets/cohort3.gif)

## `Perspectives` {#perspectives}

`Standard`
Dies zeigt den inkrementellen Beitrag einer bestimmten Kohortengruppe zu einem beliebigen Zeitpunkt ihres Lebenszyklus. (Beispiel: Der Punkt &quot;Woche 6&quot;zeigt alle Datenpunkte an, die von Benutzern in ihrer sechsten Woche erstellt wurden.)

`Average Value per Cohort Member`
Dadurch wird die `Standard cohort` Analyse in (1) durch die Anzahl der Benutzer in jeder `cohort` Gruppe dividiert. Dies kann für den Vergleich der Kohortenleistung von Äpfeln mit Äpfeln nützlich sein, da nicht alle Kohortengruppen die gleiche Anzahl von Benutzern umfassen können. Beispielsweise der durchschnittliche Umsatz in Woche 6 pro Benutzer mit einem bestimmten `cohort`.

`Cumulative`
Diese `perspective` zeigt die traditionelle `cohort` Analyse auf `cumulative` Basis. Mit anderen Worten, er zeigt den Gesamtbeitrag einer bestimmten Kohorte zu einem beliebigen Zeitpunkt ihres Lebenszyklus an. Beispielsweise der kumulative Umsatz von Benutzern aus einer bestimmten Kohorte nach sechs Wochen.

`Cumulative Average Value per Cohort Member`
Dadurch wird die `Cumulative` Analyse in (3) durch die Anzahl der Benutzer in jeder `cohort` Gruppe dividiert. Er zeigt den durchschnittlichen Lebenszeitbeitrag (oft durchschnittlicher Lebensdauerumsatz) pro `cohort`-Mitglied für jeden Zeitraum im `cohort's` -Lebenszyklus an. Beispielsweise der durchschnittliche Umsatz während der Lebensdauer nach sechs Monaten mit Benutzern, die im Juni beigetreten sind.

`Percent of First Value (show first value)`
Dadurch wird der aggregierte `cohort` Beitrag zu einem bestimmten Zeitpunkt in einem `cohort's` Lebenszyklus als Prozentsatz seines Beitrags im ersten Zeitraum analysiert. Beispiel: Der Umsatz für Monat 6 dividiert durch den Umsatz für Monat 1 aus Benutzern, die im Juni beigetreten sind.

`Percent of First Value (hide first value)`
Dies entspricht dem obigen `perspective` , allerdings wird der Wert des ersten Zeitraums von 100 % ausgeblendet.

## Aufwischen {#finish}

Der `Cohort Report Builder` ist für die Gruppierung von Benutzern mit dem gemeinsamen `cohort date` optimiert. Möglicherweise möchten Sie die Benutzer nach einer ähnlichen Aktivität oder einem ähnlichen Attribut gruppieren. Adobe empfiehlt, [dieses Tutorial zu qualitativen Kohorten](../dev-reports/create-qual-cohort-analysis.md) auszuprobieren, um zu beginnen.
