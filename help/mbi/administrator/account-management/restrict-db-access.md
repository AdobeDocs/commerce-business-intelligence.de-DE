---
title: Beschränken des Zugriffs auf Ihre Datenbank
description: Erfahren Sie, wie Sie den Zugriff einschränken und so den Zugriff auf den Server einschränken können, auf dem sich Ihre Datenbank befindet.
exl-id: 7a0bc0d7-086e-4a6e-b1dd-6db13814710e
role: Admin, User
feature: Accounts, User Management
source-git-commit: adb7aaef1cf914d43348abf5c7e4bec7c51bed0c
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Zugriff beschränken

Wenn Sie einen SSH-Tunnel zu Ihrem Server erstellen, müssen [!DNL Adobe Commerce Intelligence] auf nichts anderes als auf die Datenbank zugreifen können. Wenn Sie nicht möchten, dass [!DNL Commerce Intelligence] vollen Zugriff auf den Server haben, auf dem sich Ihre Datenbank befindet, können Sie den Zugriff einschränken, indem Sie den [!DNL Commerce Intelligence Linux] Benutzer in eine [eingeschränkte Bash-Shell“ &#x200B;](https://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html).

Sie können den Namen bereits erraten haben, aber eine eingeschränkte Bash-Shell wird verwendet, um eine Umgebung einzurichten, die kontrollierter ist als die Standard-Shell. Das Wichtige an dieser Art von Shell ist, dass eingeschränkte Shell-Benutzer nicht auf Systemfunktionen zugreifen oder irgendwelche Änderungen vornehmen können.

Um den [!DNL Commerce Intelligence Linux] Benutzer einzuschränken, müssen Sie zwei Dinge tun:

1. Ändern Sie die PATH-Umgebungsvariable in die leere Zeichenfolge. Das bedeutet, dass der Benutzer nicht auf ausführbare Dateien des Systems zugreifen kann.

1. Stellen Sie sicher, dass die ausgeführte Shell `bash -r` ist

Beide Aktionen können in der `authorized_keys`-Datei im `dir/.ssh` des Benutzers als Teil des Befehls ausgeführt werden, der bei der Anmeldung des Benutzers ausgeführt wird. Er sieht in etwa so aus:

```bash
... other keys ...
command="env PATH="" /bin/bash -r" <rjmetrics public key goes here>
... other keys ...
```

Wenn dies abgeschlossen ist, kann der Benutzer, den Sie für [!DNL Commerce Intelligence] erstellt haben, keine Änderungen an Ihrem System vornehmen.
