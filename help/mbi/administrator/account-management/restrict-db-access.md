---
title: Einschränken des Zugriffs auf Ihre Datenbank
description: Erfahren Sie, wie Sie den Zugriff einschränken und den Zugriff auf den Server beschränken können, auf dem sich Ihre Datenbank befindet.
exl-id: 7a0bc0d7-086e-4a6e-b1dd-6db13814710e
source-git-commit: 14777b216bf7aaeea0fb2d0513cc94539034a359
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Zugriff beschränken

Wenn Sie einen SSH-Tunnel zu Ihrem Server erstellen, müssen Sie [!DNL MBI] um Zugriff auf alles außer der Datenbank zu haben. Wenn Sie nicht möchten [!DNL MBI] um vollen Zugriff auf den Server zu haben, auf dem Ihre Datenbank gespeichert ist, können Sie den Zugriff einschränken, indem Sie die [!DNL MBI Linux®] Benutzer in [beschränkte Bash-Shell](https://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html).

Sie haben vielleicht vom Namen aus erraten, aber eine beschränkte Bash-Shell wird verwendet, um eine Umgebung einzurichten, die besser kontrolliert ist als die Standard-Shell. Wichtig an dieser Art von Shell ist, dass beschränkte Shell-Benutzer nicht auf Systemfunktionen zugreifen oder irgendwelche Änderungen vornehmen können.

So beschränken Sie die [!DNL MBI Linux®] -Benutzer verwenden, müssen Sie zwei Dinge tun:

1. Ändern Sie die Umgebungsvariable PATH in die leere Zeichenfolge. Das bedeutet, dass der Benutzer nicht auf ausführbare Systemtabellen zugreifen kann.

1. Stellen Sie sicher, dass die ausgeführte Shell `bash -r`

Beide können innerhalb der `authorized_keys` Datei auf der Startseite des Benutzers `dir/.ssh` -Ordner als Teil des Befehls, der ausgeführt wird, wenn sich der Benutzer anmeldet. Es sieht ungefähr so aus:

```bash
... other keys ...
command="env PATH="" /bin/bash -r" <rjmetrics public key goes here>
... other keys ...
```

Sobald dies abgeschlossen ist, der Benutzer, für den Sie erstellt haben [!DNL MBI] kann keine Änderungen an Ihrem System vornehmen.
