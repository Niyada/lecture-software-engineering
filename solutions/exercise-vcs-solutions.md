# 🔄 VCS Übungen - Musterlösungen

## 📝 Aufgabe 1️⃣ - Lösung

### Arten von Version Control Systems (VCS):

#### 🗂️ **Lokale VCS**
- **Beispiele:** RCS (Revision Control System)
- **Funktionsweise:** Versionen werden lokal in einer Datenbank gespeichert
- **Vorteile:**
  - Einfach zu verstehen und einzurichten
  - Keine Netzwerkverbindung erforderlich
  - Schneller Zugriff auf Versionen
- **Nachteile:**
  - Keine Zusammenarbeit möglich
  - Kein Backup - bei Datenverlust sind alle Versionen weg
  - Nur ein Entwickler kann am Projekt arbeiten

#### 🌐 **Zentrale VCS (CVCS - Centralized Version Control Systems)**
- **Beispiele:** CVS, Subversion (SVN), Perforce
- **Funktionsweise:** Ein zentraler Server speichert alle Versionen, Clients checken Dateien aus/ein
- **Vorteile:**
  - Teamzusammenarbeit möglich
  - Administratoren haben Kontrolle über Berechtigungen
  - Einfache Verwaltung von großen Teams
  - Backup des zentralen Servers schützt alle Versionen
- **Nachteile:**
  - Single Point of Failure - fällt Server aus, kann niemand arbeiten
  - Netzwerkverbindung erforderlich
  - Langsame Operationen über Netzwerk
  - Konflikte beim gleichzeitigen Bearbeiten

#### 🔀 **Verteilte VCS (DVCS - Distributed Version Control Systems)**
- **Beispiele:** Git, Mercurial, Bazaar
- **Funktionsweise:** Jeder Client hat eine vollständige Kopie der Repository-Geschichte
- **Vorteile:**
  - Kein Single Point of Failure
  - Offline-Arbeit möglich
  - Sehr schnelle lokale Operationen
  - Flexible Workflows (Feature-Branches, etc.)
  - Mehrere Backup-Strategien möglich
  - Einfaches Branching und Merging
- **Nachteile:**
  - Komplexer für Anfänger
  - Mehr Speicherplatz benötigt
  - Kann bei sehr großen Repositories langsam werden

## 📁 Aufgabe 2️⃣ (Gitignore) - Lösung

### 🎯 Aufgabe 2️⃣.1️⃣ - Dateien-Analyse

**Sollten NICHT versioniert werden:**

❌ **`logs/app.log`** 
- **Grund:** Log-Dateien werden zur Laufzeit generiert und enthalten temporäre Informationen
- **Problem:** Werden ständig geändert, würden Repository aufblähen

❌ **`target/Main.class`**
- **Grund:** Kompilierte Dateien (Build-Artefakte) werden automatisch aus Quellcode generiert
- **Problem:** Binärdateien, plattformabhängig, können jederzeit neu erstellt werden

❌ **`node_modules/package/index.js`**
- **Grund:** Dependencies/Bibliotheken werden über Package Manager (npm) verwaltet
- **Problem:** Sehr groß, werden über `package.json` definiert und können neu installiert werden

❌ **`.DS_Store`**
- **Grund:** macOS-spezifische Metadaten-Datei für Finder-Ansichten
- **Problem:** Betriebssystem-spezifisch, für andere Entwickler irrelevant

**✅ Sollten versioniert werden:**

✅ **`src/Main.java`**
- **Grund:** Quellcode ist das Herzstück des Projekts
- **Wichtig:** Muss versioniert werden für Nachverfolgung von Änderungen

✅ **`README.md`**
- **Grund:** Dokumentation ist wichtig für andere Entwickler
- **Wichtig:** Beschreibt Projekt, Installation, Nutzung

❓ **`config/database.properties`**
- **Kommt darauf an:** 
  - **Template-Version:** JA (ohne echte Credentials)
  - **Mit echten Passwörtern:** NEIN (Sicherheitsrisiko)

### 🎯 Aufgabe 2️⃣.2️⃣ - Praktische Umsetzung

#### Schritt 1: Repository erstellen
```bash
mkdir vcs-exercise  # Verzeichnis erstellen
cd vcs-exercise     # In das Verzeichnis wechseln
git init            # Git-Repository initialisieren
```

#### Schritt 2: Dateien erstellen
Hier via bash Befehle, manuell ist aber ebenfalls möglich.
```bash
# Verzeichnisse erstellen
mkdir -p src config logs target node_modules/package

# Dateien erstellen
touch src/Main.java
touch config/database.properties
touch logs/app.log
touch target/Main.class
touch node_modules/package/index.js
touch .DS_Store
touch README.md
```

#### Schritt 3: Status ohne .gitignore prüfen
```bash
git status
```
**Ergebnis:** Alle Dateien werden als _"untracked"_ angezeigt

#### Schritt 4: .gitignore erstellen
```gitignore
# Build-Artefakte
target/
*.class
*.jar
*.war

# Logs
logs/
*.log

# Dependencies
node_modules/

# OS-spezifische Dateien
.DS_Store
Thumbs.db

# IDE-spezifische Dateien
.idea/
.vscode/
*.iml

# Temporäre Dateien
*.tmp
*.temp

# Credentials (bei echten Projekten)
*.properties
!*.properties.template
```

#### Schritt 5: Status mit .gitignore prüfen
```bash
git status
```
**Ergebnis:** Nur noch `src/Main.java`, `README.md` und `.gitignore` werden angezeigt

## 🔧 Aufgabe 3️⃣ (IDE-Integration) - Lösung

### 🎯 Aufgabe 3️⃣.1️⃣ - Repository klonen

#### Via Kommandozeile:
```bash
# SSH
git clone git@github.com:Niyada/WWI25B2-software-engineering-1.git <target-directory>

# HTTPS (mit PAT)
git clone https://github.com/Niyada/WWI25B2-software-engineering-1.git <target-directory>
```

#### In der IDE:
- **VS Code:** `Ctrl+Shift+P` → "Git: Clone" → URL eingeben
- **IntelliJ:** File → New → Project from Version Control → URL eingeben
- **Eclipse:**  Search bar (Lupensymbol oben rechts) → "Clone a Git Repository"

### 🎯 Aufgabe 3️⃣.2️⃣ - Git History analysieren

#### In der IDE:
- **VS Code:** 
  1. Source Control Panel → "View History"
  2. Oder: GitLens Extension installieren
  3. Rechtsklick auf `Animal.java` → "File History"

- **IntelliJ:**
  1. Rechtsklick auf `Animal.java` → Git → Show History
  2. Oder: VCS → Git → Show History

- **Eclipse:**
  1. Rechtsklick auf `Animal.java` → Team → Show in History
  2. History View öffnet sich

#### Via Kommandozeile:
```bash
# Letzten Commit für spezifische Datei anzeigen
git log -1 Animal.java

# Detaillierte History mit Änderungen
git log -p Animal.java

# Kompakte History
git log --oneline Animal.java

# Wer hat was wann geändert (blame)
git blame Animal.java
```

### 🎯 Aufgabe 3️⃣.3️⃣ - Feature Branch Workflow

#### Schritt 1: Neuen Branch erstellen und wechseln
```bash
git checkout -b feature/max-mustermann
# oder moderner:
git switch -c feature/max-mustermann
```

#### Schritt 2: Neue Tier-Klasse erstellen
```java
package animals;

public class Cat extends Animal {
    public Cat(String name) {
        super(name);
    }

    @Override
    public void makeSound() {
        System.out.println(this.getName() + " (Cat): Meow!");
    }
}
```

#### Schritt 3: Änderungen committen
```bash
git add Cat.java
git commit -m "adds Cat class implementation extending Animal"
```

#### Schritt 4: Branch zu Remote Repository pushen
```bash
git push -u origin feature/max-mustermann
```

### 🎯 Aufgabe 3️⃣.4️⃣ - Merging und Konflikte

#### Schritt 1: Zurück zu main Branch
```bash
git checkout main
# oder:
git switch main
```

#### Schritt 2: Merge versuchen
```bash
git merge feature/max-mustermann
```
Die sogenannten Branch Protection Rules des Repositories verbieten Ihnen direkt auf den `main`-Branch zu comitten.

### 🎯 Aufgabe 3️⃣.5️⃣ - Pull Request erstellen

#### Schritt 1: Auf GitHub navigieren
1. Repository öffnen: `https://github.com/Niyada/WWI25B2-software-engineering-1`
2. "Compare & pull request" Button (erscheint nach Push)
3. Oder: "Pull requests" Tab → "New pull request"

#### Schritt 2: PR konfigurieren
- **Base branch:** `main`
- **Compare branch:** `feature/max-mustermann`
- **Title:** "Add Cat class"
- **Description:**
```markdown
## 🐈 Feature: Cat Class Implementation
@kommilitone123 Could you please review this implementation?
```
#### Schritt 3: Reviewer hinzufügen
- Im "Reviewers" Bereich Kommilitonen auswählen
- Optional Labels hinzufügen (z.B. "enhancement", "new-feature")

#### Schritt 4: PR erstellen
- "Create pull request" klicken