---
title: Report Builder auswählen
description: Erfahren Sie, wie Sie Report Builder auswählen.
exl-id: ec4204ef-975e-45c3-b09e-fb97ffc2c497
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Reports, Data Integration
source-git-commit: 4d04b79d55d02bee6dfc3a810e144073e7353ec0
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Report Builder auswählen

>[!NOTE]
>&#x200B;>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).

Nachdem Sie nun mehr Optionen zum Erstellen von Analysen haben, kann es manchmal schwierig sein, genau zu wissen, welche Variante des Report Builders Ihren Anforderungen entspricht. Dieses Thema führt Sie durch die Auswahl der besten Methode zur Erstellung Ihrer Analyse.

## Wann sollte ich die [!DNL SQL Report Builder] verwenden? {#whensql}

Sehen Sie sich einige der häufigsten Gründe an, warum Sie die [!DNL SQL Report Builder] über die [!DNL traditional Report Builder] hinweg verwenden würden.

### Wenn Sie [!DNL SQL] Funktionen verwenden möchten…

Das Schöne an der [!DNL SQL Report Builder] ist, dass sie Ihnen die Möglichkeit gibt, Funktionen zu verwenden, die derzeit nicht in Data Warehouse Manager verfügbar sind. In der Vergangenheit musste möglicherweise ein Analyst eingreifen, um Ihnen dabei zu helfen, Ihre Vision vollständig zu verwirklichen.

Der [!DNL SQL Report Builder] unterstützt Funktionen wie [`LISTAGG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LISTAGG.html) und [`GETDATE`](https://docs.aws.amazon.com/redshift/latest/dg/r_GETDATE.html), die Sie zuvor nicht verwenden konnten. Sie können auf die [`full list`](https://docs.aws.amazon.com/redshift/latest/dg/c_SQL_functions.html) zugreifen, aber einige andere SQL-spezifische Funktionen umfassen:

* [`Bitwise aggregate` Funktionen](https://docs.aws.amazon.com/redshift/latest/dg/c_bitwise_aggregate_functions.html)
* [`CASE expression`](https://docs.aws.amazon.com/redshift/latest/dg/r_CASE_function.html)
* [`JSON_EXTRACT_PATH_TEXT`](https://docs.aws.amazon.com/redshift/latest/dg/JSON_EXTRACT_PATH_TEXT.html)
* [`LOG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LOG.html)
* [`MONTHS_BETWEEN`](https://docs.aws.amazon.com/redshift/latest/dg/r_MONTHS_BETWEEN_function.html)
* [`REPLACE`](https://docs.aws.amazon.com/redshift/latest/dg/r_REPLACE.html)
* [`SQRT`](https://docs.aws.amazon.com/redshift/latest/dg/r_SQRT.html)
* [`concatenation` Operator](https://docs.aws.amazon.com/redshift/latest/dg/r_concat_op.html)

### Wenn Sie einige Tests durchführen möchten…

Wenn Sie verschiedene Techniken und Strategien ausprobieren möchten, um herauszufinden, was für Ihre Analyse am besten funktioniert, sollten Sie die [!DNL SQL Report Builder] verwenden. Das Erstellen von Spalten in Data Warehouse Manager dauert seine Zeit, und die Spalten, die Sie mit dem DWM erstellen, sind von Aktualisierungszyklen abhängig.

Sie müssen bestenfalls einen Aktualisierungszyklus abwarten, bevor Sie Ihre Spalte verwenden können. Wenn Sie feststellen, dass Sie beim Erstellen der Spalte einen Fehler gemacht haben, müssen Sie *zwei* Zyklen warten: einen, um die Spalte anfänglich zu füllen, und einen weiteren Zyklus, damit die Revisionen weitergegeben werden.

### Wenn Sie eine neue Spalte nur einmal verwenden…

Wie im obigen Abschnitt erwähnt, dauert das Erstellen einer Spalte in Data Warehouse Manager sehr lange. Wenn Sie nur eine Spalte verwenden möchten, die Sie in einem Bericht erstellen, empfiehlt Adobe die Verwendung der [!DNL SQL Report Builder] . Dadurch entfällt die Notwendigkeit, auf den Abschluss eines Aktualisierungszyklus zu warten, sodass Sie schneller wieder arbeiten können.

### Wenn Sie mit Daten arbeiten, die eine Eins-zu-viele-Beziehung haben…

Manchmal kann die Struktur Ihrer Daten die [!DNL SQL Report Builder] zu einer effizienteren und logischeren Wahl für die Erstellung Ihrer Analyse machen. Das Erstellen von Spalten für Eins-zu-eins-Beziehungen ist in Data Warehouse Manager unkompliziert, aber es kann etwas verwirrend werden, wenn Sie es mit Eins-zu-viele-Beziehungen zu tun haben.

Angenommen, ein einzelnes Produkt wird als Teil mehrerer Produktkategorien betrachtet, und Sie möchten den Umsatz für jede Kategorie jedes Produkts anzeigen. Der Versuch, diese Beziehung mit dem DWM zu erstellen, kann mühsam und schwierig sein, aber das Schreiben einer [!DNL SQL] Abfrage kann etwas einfacher sein:

![SQL-Abfrage, die den Umsatz nach Produktkategorie mit Eins-zu-Viele-Beziehungen anzeigt](../../assets/When_should_I_use_the_RB_2.png)

## Wann sollte ich das herkömmliche Report Builder verwenden? {#whentraditionalrb}

Mit dem [!DNL SQL Report Builder] erhalten Sie zwar mehr Kontrolle und Zugriff auf zuvor nicht verfügbare Funktionen, es ist jedoch möglicherweise nicht immer die richtige Wahl. Adobe schlägt vor, bei der Entscheidung, welche Variante von Report Builder verwendet werden soll, auch Folgendes zu berücksichtigen.

### Wenn Sie einen einfachen Bericht erstellen…

Wenn das, was Sie erstellen möchten, einfach ist, kann die Verwendung der herkömmlichen Report Builder viel schneller sein als das Schreiben einer vollständigen [!DNL SQL]. Dies ist hilfreich, wenn alle Spalten, die Sie zum Erstellen der Analyse benötigen, bereits im Data Warehouse Manager vorhanden sind.

### Wenn Sie Ihre Arbeit mit anderen Benutzern teilen…

Verwenden/sehen Benutzende in Ihrer Organisation diese Analyse? Je nachdem, mit wem Sie Ihre Arbeit teilen, kann es manchmal besser sein, bei Visual Report Builder zu bleiben. Benutzer können die Definition im [!DNL Visual Report Builder] schnell überprüfen, anstatt eine potenziell lange [!DNL SQL]-Abfrage zu lesen.

Wenn es einige Personen gibt, die den Bericht benötigen, aber nicht mit [!DNL SQL] vertraut sind, schlägt Adobe vor, das Original-Aroma des Report Builder zu verwenden. Das macht es ihnen leichter.

## Verpackung {#wrapup}

Sowohl die [!DNL SQL Report Builder] als auch die [!DNL Visual Report Builder] eignen sich für eine Vielzahl von Anwendungsfällen. Dies hängt in der Regel davon ab, was Ihre analytischen Anforderungen sind und wer die Analyse verwendet.
