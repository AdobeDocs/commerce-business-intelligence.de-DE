---
title: Einschränken des Zugriffs auf Ihre Datenbank
description: Erfahren Sie, wie Sie den Zugriff einschränken und den Zugriff auf den Server beschränken können, auf dem sich Ihre Datenbank befindet.
exl-id: 7a0bc0d7-086e-4a6e-b1dd-6db13814710e
role: Admin, User
feature: Accounts, User Management
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Zugriff beschränken

Wenn Sie einen SSH-Tunnel zu Ihrem Server erstellen, muss [!DNL Adobe Commerce Intelligence] nur auf die Datenbank zugreifen können. Wenn Sie nicht möchten, dass [!DNL Commerce Intelligence] vollen Zugriff auf den Server hat, auf dem Ihre Datenbank gespeichert ist, können Sie den Zugriff beschränken, indem Sie den Benutzer [!DNL Commerce Intelligence Linux] in eine [beschränkte Bash-Shell](https://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html) zwingen.

Sie haben vielleicht vom Namen aus erraten, aber eine beschränkte Bash-Shell wird verwendet, um eine Umgebung einzurichten, die besser kontrolliert ist als die Standard-Shell. Wichtig an dieser Art von Shell ist, dass beschränkte Shell-Benutzer nicht auf Systemfunktionen zugreifen oder irgendwelche Änderungen vornehmen können.

Um den Benutzer [!DNL Commerce Intelligence Linux] zu beschränken, müssen Sie zwei Schritte durchführen:

1. Ändern Sie die Umgebungsvariable PATH in die leere Zeichenfolge. Das bedeutet, dass der Benutzer nicht auf ausführbare Systemtabellen zugreifen kann.

1. Stellen Sie sicher, dass die ausgeführte Shell `bash -r` ist.

Beide können innerhalb der Datei `authorized_keys` im Home `dir/.ssh`-Verzeichnis des Benutzers im Rahmen des Befehls ausgeführt werden, der bei der Anmeldung des Benutzers ausgeführt wird. Es sieht ungefähr so aus:

```bash
... other keys ...
command="env PATH="" /bin/bash -r" <rjmetrics public key goes here>
... other keys ...
```

Wenn dies abgeschlossen ist, kann der Benutzer, den Sie für [!DNL Commerce Intelligence] erstellt haben, keine Änderungen an Ihrem System vornehmen.
