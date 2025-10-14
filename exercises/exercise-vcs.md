# Übungsaufgaben - Versionsverwaltungssysteme (VCS)

## Aufgabe 1️⃣
Was sind die Hauptaufgaben von Versionskontrollsystemen?

## Aufgabe 2️⃣
Welche Arten von VCS gibt es und was sind ihre Vor- und Nachteile?

## Aufgabe 3️⃣
Ziel dieser Aufgabe ist es, grundlegende Arbeitsabläufe bei der Verwendung von VCS in Ihrer bevorzugten IDE zu erkunden.

> [!IMPORTANT] 
> Sie benötigen für diese Aufgabe einen GitHub Account, sowie einen SSH-Key, der dort hinterlegt ist. Letzteres ist zu Zwecken der Authentifizierung nötig, um in das remote Repository zu pushen. Eine Anleitung zum Erstellen eines SSH Keys finden Sie [hier](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). Zudem wird [hier](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) erklärt, wie dieser in GitHub hinterlegt werden kann.

### Aufgabe 3️⃣.1️⃣
Klonen sie folgendes Repository und öffnen Sie es als Projekt in Ihrer bevorzugten IDE:
- [Tutorial für VS Code](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_open-a-git-repository)
- [IntelliJ IDEA](https://www.jetbrains.com/help/idea/set-up-a-git-repository.html#clone-repo)
- [Eclipse IDE](https://wiki.eclipse.org/EGit/User_Guide/Remote#Cloning_remote_Repositories)
```
git@github.com:...
```

### Aufgabe 3️⃣.2️⃣
Finden Sie heraus, wer die Datei `Animal.java` zuletzt geändert hat. Wann wurde die Änderung vorgenommen und was wurde geändert?

### Aufgabe 3️⃣.3️⃣
Erstellen Sie einen neuen Branch namens `feature/<IhrName>`. Wechseln Sie in diesen Branch und erstellen Sie ein beliebiges neues Tier als Unterklasse von `Animal` (z.B. `Dog`, `Cat`, `Elephant` etc.). Implementieren Sie die vorgegebenen Methode und einen geeigneten Konstruktor. Synchronisieren Sie anschließend Ihre Änderungen in der Arbeitskopie mit dem lokalen und remote Repository.

### Aufgabe 3️⃣.4️⃣
Wechseln Sie zurück in den `main` Branch und versuchen Sie, Ihren `feature/<IhrName>` Branch in den `main` Branch zu mergen. Achten Sie darauf, dass Sie eventuelle Merge-Konflikte auflösen. Was fällt Ihnen dabei auf?

### Aufgabe 3️⃣.5️⃣
Erstellen Sie ein Pull Request (PR) für Ihren `feature/<IhrName>` Branch im GitHub Repository. Beschreiben Sie kurz, was Sie geändert haben und fordern Sie eine Überprüfung (Review) durch einen Ihrer Kommilitonen an.
> [!TIP]
> Nutzen Sie die Gelegenheit, um Feedback zu Ihrem Code zu erhalten und geben Sie auch selbst Feedback zu den Änderungen Ihrer Kommilitonen.
> [Hier](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) finden Sie mehr Informationen zu Pull Requests und [hier](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes) eine Anleitung zum Erstellen von Pull Requests.
