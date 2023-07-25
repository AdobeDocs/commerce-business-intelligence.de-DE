---
title: ReportBuilder auswählen
description: Erfahren Sie, wie Sie Ihren ReportBuilder auswählen.
exl-id: ec4204ef-975e-45c3-b09e-fb97ffc2c497
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# ReportBuilder auswählen

>[!NOTE]
>>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Da Sie jetzt mehr Möglichkeiten zum Erstellen von Analysen haben, kann es manchmal schwierig sein, genau zu wissen, welcher Geschmack des Report Builder Ihren Anforderungen entspricht. Dieses Thema führt Sie durch die Auswahl der besten Methode zum Erstellen Ihrer Analyse.

## Wann sollte ich die [!DNL SQL Report Builder]? {#whensql}

Sehen Sie sich einige der häufigsten Gründe an, aus denen Sie die [!DNL SQL Report Builder] über [!DNL traditional Report Builder].

### Wenn Sie [!DNL SQL]-spezifische Funktionen...

Teil der Schönheit der [!DNL SQL Report Builder] ist, dass Sie damit Funktionen verwenden können, die derzeit nicht im Data Warehouse Manager verfügbar sind. In der Vergangenheit musste vielleicht ein Analyste eintreten, um Ihnen bei der vollständigen Verwirklichung Ihrer Vision zu helfen.

Die [!DNL SQL Report Builder] unterstützt Funktionen wie [`LISTAGG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LISTAGG.html) und [`GETDATE`](https://docs.aws.amazon.com/redshift/latest/dg/r_GETDATE.html), die Sie zuvor nicht verwenden konnten. Sie können auf die [`full list`](https://docs.aws.amazon.com/redshift/latest/dg/c_SQL_functions.html), aber einige andere SQL-spezifische Funktionen sind:

* [`Bitwise aggregate` Funktionen](https://docs.aws.amazon.com/redshift/latest/dg/c_bitwise_aggregate_functions.html)
* [`CASE expression`](https://docs.aws.amazon.com/redshift/latest/dg/r_CASE_function.html)
* [`JSON_EXTRACT_PATH_TEXT`](https://docs.aws.amazon.com/redshift/latest/dg/JSON_EXTRACT_PATH_TEXT.html)
* [`LOG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LOG.html)
* [`MONTHS_BETWEEN`](https://docs.aws.amazon.com/redshift/latest/dg/r_MONTHS_BETWEEN_function.html)
* [`REPLACE`](https://docs.aws.amazon.com/redshift/latest/dg/r_REPLACE.html)
* [`SQRT`](https://docs.aws.amazon.com/redshift/latest/dg/r_SQRT.html)
* [`concatenation` operator](https://docs.aws.amazon.com/redshift/latest/dg/r_concat_op.html)

### Wenn Sie einige Tests durchführen möchten...

Wenn Sie verschiedene Techniken und Strategien ausprobieren möchten, um herauszufinden, was für Ihre Analyse am besten geeignet ist, sollten Sie die [!DNL SQL Report Builder]. Das Erstellen von Spalten im Data Warehousen-Manager erfordert Zeit, und die mithilfe des DWM erstellten Spalten hängen von Aktualisierungszyklen ab.

Sie müssen bestenfalls einen Aktualisierungszyklus durchlaufen, bevor Sie Ihre Spalte verwenden können. Wenn Sie feststellen, dass Sie beim Erstellen der Spalte einen Fehler gemacht haben, müssen Sie durchwarten *two* Zyklen: ein , um die Spalte anfänglich zu füllen, und ein anderer Zyklus, in dem die Revisionen propagiert werden.

### Wenn Sie nur einmal eine neue Spalte verwenden...

Wie im obigen Abschnitt erwähnt, dauert das Erstellen einer Spalte im Data Warehousen-Manager. Wenn Sie nur eine Spalte verwenden möchten, die Sie in einem Bericht erstellen, empfiehlt die Adobe, die [!DNL SQL Report Builder]. Dadurch müssen Sie nicht warten, bis ein Aktualisierungszyklus abgeschlossen ist, sodass Sie schneller wieder arbeiten können.

### Wenn Sie mit Daten arbeiten, die eine Eins-zu-viele-Beziehung aufweisen ...

Manchmal kann die Struktur Ihrer Daten die [!DNL SQL Report Builder] eine effizientere und logischere Wahl zur Erstellung Ihrer Analyse. Das Erstellen von Spalten für Eins-zu-Eins-Beziehungen ist im Data Warehousen-Manager unkompliziert, aber die Dinge können etwas verwirrend sein, wenn es um Eins-zu-viele-Beziehungen geht.

Nehmen Sie an, dass ein einzelnes Produkt als Teil mehrerer Produktkategorien betrachtet wird, und Sie möchten den Umsatz sehen, der mit jeder Produktkategorie verbunden ist. Der Versuch, diese Beziehung mithilfe des DWM zu erstellen, kann mühsam und schwierig sein, aber eine [!DNL SQL] -Abfrage kann ein wenig einfacher sein:

![](../../assets/When_should_I_use_the_RB_2.png)

## Wann sollte ich den traditionellen Report Builder verwenden? {#whentraditionalrb}

Während [!DNL SQL Report Builder] bietet Ihnen mehr Kontrolle und Zugriff auf zuvor nicht verfügbare Funktionen. Möglicherweise ist dies nicht immer die richtige Wahl. Die Adobe legt nahe, dass Sie bei der Entscheidung, welche Variante von ReportBuilder verwendet werden soll, auch Folgendes berücksichtigen.

### Wenn Sie einen einfachen Bericht erstellen ...

Wenn das, was Sie erstellen möchten, einfach ist, kann die Verwendung des herkömmlichen Report Builders viel schneller sein, als ein vollständiges [!DNL SQL] Abfrage. Es ist hilfreich, wenn sich die Spalten, die Sie zur Erstellung der Analyse benötigen, bereits im Data Warehousen-Manager befinden.

### Wenn Sie Ihre Arbeit mit anderen Benutzern teilen ...

Verwenden Benutzer in Ihrer gesamten Organisation diese Analyse? Je nachdem, mit wem Sie Ihre Arbeit teilen, kann es manchmal besser sein, an Visual Report Builder zu bleiben. Benutzer können sich die Definition in der [!DNL Visual Report Builder] oder das Lesen einer potenziell langen [!DNL SQL] Abfrage.

Wenn es einige Personen gibt, die den Bericht benötigen, aber nicht mit [!DNL SQL], schlägt Adobe vor, den ursprünglichen Geschmack des Report Builders zu verwenden. Das erleichtert ihnen die Arbeit.

## Aufbrechen {#wrapup}

Beide [!DNL SQL Report Builder] und [!DNL Visual Report Builder] für eine Vielzahl von Anwendungsfällen geeignet sind. Dies hängt in der Regel davon ab, was Ihre Analyseanforderungen sind und wer die Analyse verbraucht.
