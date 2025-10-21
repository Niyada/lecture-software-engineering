# 🔄 Übungsaufgaben - VCS

## 📚 Aufgabe 1️⃣
Welche Arten von VCS gibt es und was sind ihre Vor- und Nachteile?


## 📁 Aufgabe 2️⃣
Arbeiten mit `.gitignore` Dateien

### Aufgabe 2️⃣.1️⃣
Welche der folgenden Dateien sollten nicht versioniert werden und warum? Informieren Sie sich ggf. über die Dateien und Ihre Verwendung.
- `src/Main.java`
- `config/database.properties` 
- `logs/app.log`
- `target/Main.class`
- `node_modules/package/index.js`
- `.DS_Store`
- `README.md`

### Aufgabe 2️⃣.2️⃣
Erstellen Sie ein neues Git Repository in einem beliebigen Verzeichnis auf Ihrem Computer und fügen Sie die oben genannten Dateien mit beliebigen oder ohne Inhalt hinzu. Prüfen Sie das Ergebnis mit `git status`.
Erstellen Sie eine entsprechende `.gitignore`. Überprüfen Sie mit `git status`, ob die richtigen Dateien ignoriert werden.



## 🛠️ Aufgabe 3️⃣
Ziel dieser Aufgabe ist es, grundlegende Arbeitsabläufe bei der Verwendung von VCS in Ihrer bevorzugten IDE zu erkunden.

> [!IMPORTANT] 
> Sie benötigen für diese Aufgabe einen GitHub Account, sowie einen SSH-Key, der dort hinterlegt ist. Letzteres ist zu Zwecken der Authentifizierung nötig, um in das remote Repository zu pushen. Eine Anleitung zum Erstellen eines SSH Keys finden Sie [hier](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). Zudem wird [hier](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) erklärt, wie dieser in GitHub hinterlegt werden kann.
> Alternativ können Sie auch HTTPS verwenden, um auf das Repository zuzugreifen. Hierzu können Sie einen [Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) anstelle Ihres Passworts verwenden.
> Außerdem muss Ihr Dozent Sie als Collaborator zu dem Repository hinzufügen, damit Sie Schreibrechte haben.

### Aufgabe 3️⃣.1️⃣
Klonen sie folgendes Repository und öffnen Sie es als Projekt in Ihrer bevorzugten IDE:
- [Tutorial für VS Code](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_open-a-git-repository)
- [IntelliJ IDEA](https://www.jetbrains.com/help/idea/set-up-a-git-repository.html#clone-repo)
- [Eclipse IDE](https://wiki.eclipse.org/EGit/User_Guide/Remote#Cloning_remote_Repositories)
```bash
#SSH URL:
git@github.com:Niyada/WWI25B2-software-engineering-1.git

#HTTPS URL:
https://github.com/Niyada/WWI25B2-software-engineering-1.git
```

### Aufgabe 3️⃣.2️⃣
Finden Sie heraus, wer die Datei `Animal.java` zuletzt geändert hat. Wann wurde die Änderung vorgenommen und was wurde geändert?
Wie sind die Schritte, um diese Information 
- in Ihrer IDE zu finden?
- über die Kommandozeile zu finden?

### Aufgabe 3️⃣.3️⃣
Erstellen Sie einen neuen Branch namens `feature/<IhrName>`. Wechseln Sie in diesen Branch und erstellen Sie ein beliebiges neues Tier als Unterklasse von `Animal` (z.B. `Dog`, `Cat`, `Elephant` etc.). Implementieren Sie die vorgegebenen Methode und einen geeigneten Konstruktor. Synchronisieren Sie anschließend Ihre Änderungen in der Arbeitskopie mit dem lokalen und remote Repository.

### Aufgabe 3️⃣.4️⃣
Wechseln Sie zurück in den `main` Branch und versuchen Sie, Ihren `feature/<IhrName>` Branch in den `main` Branch zu mergen. Achten Sie darauf, dass Sie eventuelle Merge-Konflikte auflösen. Was fällt Ihnen dabei auf?

### Aufgabe 3️⃣.5️⃣
Erstellen Sie ein Pull Request (PR) für Ihren `feature/<IhrName>` Branch im GitHub Repository. Beschreiben Sie kurz, was Sie geändert haben und fordern Sie eine Überprüfung (Review) durch einen Ihrer Kommilitonen an. Mergen Sie anschließend den PR nach erfolgreicher Überprüfung auf den `main`-Branch.
> [!TIP]
> Nutzen Sie die Gelegenheit, um Feedback zu Ihrem Code zu erhalten und geben Sie auch selbst Feedback zu den Änderungen Ihrer Kommilitonen.
> [Hier](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) finden Sie mehr Informationen zu Pull Requests und [hier](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes) eine Anleitung zum Erstellen von Pull Requests.
