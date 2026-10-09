---
title: Beschränken des Zugriffs auf Ihre Datenbank
description: Erfahren Sie, wie Sie den Zugriff einschränken und so den Zugriff auf den Server einschränken können, auf dem sich Ihre Datenbank befindet.
role: Admin, User
feature: Accounts, User Management
exl-id: 7a0bc0d7-086e-4a6e-b1dd-6db13814710e
TQID: 'https://experienceleague.adobe.com/O2cS-hbhjqktc4LpJD6agxgIwabrypgCY9fnJTCR2XM'
product_v2:
  - id: cc9c1b69-d771-4a04-84d3-df2e3989418f
    internal-label: Commerce Intelligence
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 9e444628-408e-5d74-8cd4-c552f0d5d47f
    internal-label: Accounts
  - id: b6935462-7263-4ced-a703-60de6a5aeb2d
    internal-label: Administration
subfeature_v2:
  - id: d971c7be-3e54-4af9-807c-8d1f9f7b22df
    internal-label: User management
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: fdbaf74705fb224414ac8cb69f6a1b34277e3f79
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%
---

# Zugriff beschränken

Wenn Sie einen SSH-Tunnel zu Ihrem Server erstellen, müssen [!DNL Adobe Commerce Intelligence] auf nichts anderes als auf die Datenbank zugreifen können. Informationen zu Registrierung, Fehlern und Fehlerbehebung für SSH-Hostschlüssel finden Sie unter [SSH-Hostschlüsselüberprüfung](../../data-analyst/importing-data/integrations/ssh-host-key-verification.md). Wenn Sie nicht möchten, dass [!DNL Commerce Intelligence] vollen Zugriff auf den Server haben, auf dem sich Ihre Datenbank befindet, können Sie den Zugriff einschränken, indem Sie den [!DNL Commerce Intelligence Linux] Benutzer in eine [eingeschränkte Bash-Shell“ &#x200B;](https://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html).

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
