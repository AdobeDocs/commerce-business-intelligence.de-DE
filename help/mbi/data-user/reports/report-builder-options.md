---
title: ReportBuilder auswählen
description: Erfahren Sie, wie Sie Ihren ReportBuilder auswählen.
exl-id: ec4204ef-975e-45c3-b09e-fb97ffc2c497
source-git-commit: 03a5161930cafcbe600b96465ee0fc0ecb25cae8
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# ReportBuilder auswählen

>[!NOTE]
>>Erfordert [Administratorberechtigungen](../../administrator/user-management/user-management.md).


Wir haben alle gerne Optionen. Aber wenn wir mit Entscheidungen konfrontiert sind, könnten einige von uns davor zurückschrecken, eine Entscheidung zu treffen. Optionen sind großartig, aber sie können auch überwältigend und verwirrend sein.

Da Sie jetzt mehr Möglichkeiten zum Erstellen von Analysen haben, kann es manchmal schwierig sein, genau zu wissen, welcher Geschmack von ReportBuilder Ihren Anforderungen entspricht. Wenn Sie Anleitungen zur Auswahl der besten Methode zum Erstellen Ihrer Analyse benötigen, ist dieser Artikel für Sie bestimmt.

## Wann sollte ich die `SQL Report Builder`? {#whensql}

Schauen Sie sich einige der häufigsten Gründe an, warum Sie den SQL-Report Builder gegenüber dem herkömmlichen Report Builder verwenden würden.

### Wenn Sie SQL-spezifische Funktionen verwenden möchten...

Teil der Schönheit der `SQL Report Builder` ist, dass Sie damit Funktionen verwenden können, die derzeit nicht im Data Warehouse Manager verfügbar sind. In der Vergangenheit musste vielleicht ein Analyste eintreten, um Ihnen bei der vollständigen Verwirklichung Ihrer Vision zu helfen.

SQL Report Builder unterstützt Funktionen wie [`LISTAGG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LISTAGG.html) und [`GETDATE`](https://docs.aws.amazon.com/redshift/latest/dg/r_GETDATE.html), die Sie zuvor nicht verwenden konnten. Sie können auf die [`full list`](https://docs.aws.amazon.com/redshift/latest/dg/c_SQL_functions.html), aber einige andere SQL-spezifische Funktionen sind:

* [`Bitwise aggregate` Funktionen](https://docs.aws.amazon.com/redshift/latest/dg/c_bitwise_aggregate_functions.html)
* [`CASE expression`](https://docs.aws.amazon.com/redshift/latest/dg/r_CASE_function.html)
* [`JSON_EXTRACT_PATH_TEXT`](https://docs.aws.amazon.com/redshift/latest/dg/JSON_EXTRACT_PATH_TEXT.html)
* [`LOG`](https://docs.aws.amazon.com/redshift/latest/dg/r_LOG.html)
* [`MONTHS_BETWEEN`](https://docs.aws.amazon.com/redshift/latest/dg/r_MONTHS_BETWEEN_function.html)
* [`REPLACE`](https://docs.aws.amazon.com/redshift/latest/dg/r_REPLACE.html)
* [`SQRT`](https://docs.aws.amazon.com/redshift/latest/dg/r_SQRT.html)
* [`concatenation` operator](https://docs.aws.amazon.com/redshift/latest/dg/r_concat_op.html)

### Wenn Sie einige Tests durchführen möchten...

Wenn Sie verschiedene Techniken und Strategien ausprobieren möchten, um herauszufinden, was für Ihre Analyse am besten geeignet ist, sollten Sie die `SQL Report Builder`. Das Erstellen von Spalten im Data Warehousen-Manager nimmt Zeit in Anspruch, und die mithilfe des DWM erstellten Spalten hängen von Aktualisierungszyklen ab.

Sie müssen bestenfalls einen Aktualisierungszyklus durchlaufen, bevor Sie Ihre Spalte verwenden können. Wenn Sie merken, dass Sie beim Erstellen der Spalte einen Fehler gemacht haben, müssen Sie durchwarten *two* Zyklen: ein , um die Spalte anfänglich zu füllen, und ein anderer Zyklus, in dem die Revisionen propagiert werden.

### Wenn Sie nur einmal eine neue Spalte verwenden...

Wie wir im obigen Abschnitt erwähnt haben, dauert das Erstellen einer neuen Spalte im Data Warehousen-Manager. Wenn Sie nur eine Spalte verwenden möchten, die Sie in einem Bericht erstellen, empfehlen wir die Verwendung der `SQL Report Builder`. Auf diese Weise müssen Sie nicht warten, bis ein Aktualisierungszyklus abgeschlossen ist, sodass Sie schneller wieder arbeiten können.

### Wenn Sie mit Daten arbeiten, die eine Eins-zu-viele-Beziehung aufweisen ...

In einigen Fällen kann die Struktur Ihrer Daten die `SQL Report Builder` eine effizientere und logischere Wahl zur Erstellung Ihrer Analyse. Das Erstellen von Spalten für Eins-zu-Eins-Beziehungen ist im Data Warehousen-Manager recht unkompliziert, aber die Dinge können etwas verwirrend sein, wenn Sie es mit Eins-zu-viele-Beziehungen zu tun haben.

Angenommen, ein einzelnes Produkt wird als Teil mehrerer Produktkategorien betrachtet und Sie möchten den Umsatz sehen, der mit jeder Produktkategorie verbunden ist. Der Versuch, diese Beziehung mithilfe des DWM zu erstellen, kann mühsam und schwierig sein, aber das Schreiben einer SQL-Abfrage kann ein wenig einfacher sein:

![](../../assets/When_should_I_use_the_RB_2.png)

## Wann sollte ich den traditionellen Report Builder verwenden? {#whentraditionalrb}

Während `SQL Report Builder` bietet Ihnen mehr Kontrolle und Zugriff auf zuvor nicht verfügbare Funktionen. Möglicherweise ist dies nicht immer die richtige Wahl. Wir empfehlen Ihnen, bei der Entscheidung, welche Variante des Report Builder verwendet werden soll, auch Folgendes zu beachten.

### Wenn Sie einen einfachen Bericht erstellen ...

Wenn das, was Sie erstellen möchten, einfach ist, kann die Verwendung des herkömmlichen Report Builders viel schneller sein, als eine vollständige SQL-Abfrage zu schreiben. Es ist auch hilfreich, wenn sich die Spalten, die Sie zur Erstellung der Analyse benötigen, bereits im Data Warehousen-Manager befinden.

### Wenn Sie Ihre Arbeit mit anderen Benutzern teilen ...

Nutzen/nutzen Benutzer in Ihrer gesamten Organisation diese Analyse? Je nachdem, mit wem Sie Ihre Arbeit teilen, kann es in einigen Fällen besser sein, an Visual Report Builder zu bleiben. Benutzer können sich die Definition im Visual Report Builder schnell ansehen oder eine potenziell lange SQL-Abfrage lesen.

Wenn es einige Personen gibt, die den Bericht benötigen, aber nicht mit SQL vertraut sind, empfehlen wir, den Originalgeschmack des Report Builders zu verwenden. Das wird ihnen die Arbeit erleichtern.

## Aufbrechen {#wrapup}

Beide `SQL Report Builder` und `Visual Report Builder` für eine Vielzahl von Anwendungsfällen geeignet sind. Dies hängt in der Regel davon ab, was Ihre Analyseanforderungen sind und wer die Analyse nutzen wird.
