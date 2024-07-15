---
title: ReportBuilder auswählen
description: Erfahren Sie, wie Sie Ihren ReportBuilder auswählen.
exl-id: ec4204ef-975e-45c3-b09e-fb97ffc2c497
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# ReportBuilder auswählen

>[!NOTE]
>>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Da Sie jetzt mehr Möglichkeiten zum Erstellen von Analysen haben, kann es manchmal schwierig sein, genau zu wissen, welcher Geschmack des Report Builder Ihren Anforderungen entspricht. Dieses Thema führt Sie durch die Auswahl der besten Methode zum Erstellen Ihrer Analyse.

## Wann sollte ich den [!DNL SQL Report Builder] verwenden? {#whensql}

Sehen Sie sich einige der häufigsten Gründe an, warum Sie die [!DNL SQL Report Builder] gegenüber der [!DNL traditional Report Builder] verwenden würden.

### Wenn Sie [!DNL SQL]-spezifische Funktionen verwenden möchten ...

Ein weiterer Vorteil des [!DNL SQL Report Builder] besteht darin, dass Sie Funktionen verwenden können, die derzeit nicht im Data Warehouse-Manager verfügbar sind. In der Vergangenheit musste vielleicht ein Analyste eintreten, um Ihnen bei der vollständigen Verwirklichung Ihrer Vision zu helfen.

Die [!DNL SQL Report Builder] unterstützt Funktionen wie [`LISTAGG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LISTAGG.html) und [`GETDATE`](https://docs.aws.amazon.com/redshift/latest/dg/r_GETDATE.html), die Sie zuvor nicht verwenden konnten. Sie können auf [`full list`](https://docs.aws.amazon.com/redshift/latest/dg/c_SQL_functions.html) zugreifen, aber einige andere SQL-spezifische Funktionen umfassen:

* [`Bitwise aggregate` Funktionen](https://docs.aws.amazon.com/redshift/latest/dg/c_bitwise_aggregate_functions.html)
* [`CASE expression`](https://docs.aws.amazon.com/redshift/latest/dg/r_CASE_function.html)
* [`JSON_EXTRACT_PATH_TEXT`](https://docs.aws.amazon.com/redshift/latest/dg/JSON_EXTRACT_PATH_TEXT.html)
* [`LOG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LOG.html)
* [`MONTHS_BETWEEN`](https://docs.aws.amazon.com/redshift/latest/dg/r_MONTHS_BETWEEN_function.html)
* [`REPLACE`](https://docs.aws.amazon.com/redshift/latest/dg/r_REPLACE.html)
* [`SQRT`](https://docs.aws.amazon.com/redshift/latest/dg/r_SQRT.html)
* [`concatenation` operator](https://docs.aws.amazon.com/redshift/latest/dg/r_concat_op.html)

### Wenn Sie einige Tests durchführen möchten...

Wenn Sie verschiedene Techniken und Strategien ausprobieren möchten, um herauszufinden, was für Ihre Analyse am besten geeignet ist, sollten Sie den [!DNL SQL Report Builder] verwenden. Das Erstellen von Spalten im Data Warehouse-Manager erfordert Zeit, und die mithilfe des DWM erstellten Spalten hängen von Aktualisierungszyklen ab.

Sie müssen bestenfalls einen Aktualisierungszyklus durchlaufen, bevor Sie Ihre Spalte verwenden können. Wenn Sie feststellen, dass Sie beim Erstellen der Spalte einen Fehler gemacht haben, müssen Sie die Zyklen *zwei* durchwarten: einen, um die Spalte zunächst zu füllen, und einen weiteren Zyklus, um die Revisionen zu propagieren.

### Wenn Sie nur einmal eine neue Spalte verwenden...

Wie im obigen Abschnitt erwähnt, dauert das Erstellen einer Spalte im Data Warehouse-Manager. Wenn Sie nur die Verwendung einer Spalte planen, die Sie in einem Bericht erstellen, schlägt Adobe vor, den [!DNL SQL Report Builder] zu verwenden. Dadurch müssen Sie nicht warten, bis ein Aktualisierungszyklus abgeschlossen ist, sodass Sie schneller wieder arbeiten können.

### Wenn Sie mit Daten arbeiten, die eine Eins-zu-viele-Beziehung aufweisen ...

Manchmal kann die Struktur Ihrer Daten die [!DNL SQL Report Builder] zu einer effizienteren und logischeren Entscheidung für die Erstellung Ihrer Analyse machen. Das Erstellen von Spalten für Eins-zu-Eins-Beziehungen ist im Data Warehouse-Manager unkompliziert, aber die Dinge können etwas verwirrend sein, wenn Sie es mit Eins-zu-viele-Beziehungen zu tun haben.

Nehmen Sie an, dass ein einzelnes Produkt als Teil mehrerer Produktkategorien betrachtet wird, und Sie möchten den Umsatz sehen, der mit jeder Produktkategorie verbunden ist. Der Versuch, diese Beziehung mithilfe des DWM zu erstellen, kann mühsam und schwierig sein, aber das Schreiben einer [!DNL SQL] -Abfrage kann ein wenig einfacher sein:

![](../../assets/When_should_I_use_the_RB_2.png)

## Wann sollte ich den traditionellen Report Builder verwenden? {#whentraditionalrb}

Die [!DNL SQL Report Builder] gibt Ihnen zwar mehr Kontrolle und Zugriff auf zuvor nicht verfügbare Funktionen, ist aber möglicherweise nicht immer die richtige Wahl. Adobe legt nahe, dass Sie auch Folgendes berücksichtigen, wenn Sie entscheiden, welchen Geschmack der Report Builder verwenden soll.

### Wenn Sie einen einfachen Bericht erstellen ...

Wenn das, was Sie erstellen möchten, einfach ist, kann die Verwendung des herkömmlichen Report Builders viel schneller sein, als eine vollständige [!DNL SQL] -Abfrage zu schreiben. Es ist hilfreich, wenn sich die Spalten, die Sie zur Erstellung der Analyse benötigen, bereits im Data Warehouse-Manager befinden.

### Wenn Sie Ihre Arbeit mit anderen Benutzern teilen ...

Verwenden Benutzer in Ihrer gesamten Organisation diese Analyse? Je nachdem, mit wem Sie Ihre Arbeit teilen, kann es manchmal besser sein, an Visual Report Builder zu bleiben. Benutzer können sich die Definition in der [!DNL Visual Report Builder]-Abfrage schnell ansehen und eine potenziell lange [!DNL SQL]-Abfrage lesen.

Wenn es einige Personen gibt, die den Bericht benötigen, aber nicht mit [!DNL SQL] vertraut sind, schlägt Adobe vor, den Originalgeschmack des Report Builders zu verwenden. Das erleichtert ihnen die Arbeit.

## Aufwischen {#wrapup}

Sowohl [!DNL SQL Report Builder] als auch [!DNL Visual Report Builder] sind für eine Vielzahl von Anwendungsfällen geeignet. Dies hängt in der Regel davon ab, was Ihre Analyseanforderungen sind und wer die Analyse verbraucht.
