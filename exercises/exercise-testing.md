# 🧪 Übungsaufgaben - Software Testing

In dieser Übung lernen Sie die Grundlagen des Unit Testing kennen und richten JUnit für Ihre Java-Projekte ein.

## Aufgabe 1️⃣ - Grundlagen des Unit Testing

### Szenario
Ein Entwicklungsteam hat eine neue Funktion für die Berechnung von Rabatten in einem Online-Shop implementiert. Die Funktion wurde erfolgreich ausgeliefert, aber bereits am nächsten Tag melden mehrere Kunden, dass sie falsche Rabatte erhalten haben. Bei der Analyse stellt sich heraus, dass die Funktion bei bestimmten Edge Cases (z.B. wenn der Warenkorbwert genau 100€ beträgt) falsche Ergebnisse liefert. Hätte das Team automatisierte Tests geschrieben, wäre dieser Fehler vor der Auslieferung aufgefallen.

### Aufgabe 1️⃣.1️⃣ - Warum Testen?
Nennen Sie **drei konkrete Vorteile** von automatisierten Tests, die im oben beschriebenen Szenario geholfen hätten, den Fehler zu vermeiden.

### Aufgabe 1️⃣.2️⃣ - FIRST-Prinzipien verstehen

**a)** 
Erklären Sie in 2-3 Sätzen, warum Unit-Tests **unabhängig** voneinander sein sollten. Welche Probleme können entstehen, wenn Tests voneinander abhängig sind?

**b)**
Ein Kollege berichtet: *"Mein Test schlägt manchmal fehl und manchmal ist er erfolgreich, ohne dass ich den Code geändert habe."*  
Welches FIRST-Prinzip wird hier verletzt und warum ist das problematisch? Erklären Sie in 2-3 Sätzen.

**c)**
Warum sollten Tests **selbstvalidierend** sein? Was wäre die Alternative und warum ist diese schlechter? Erklären Sie in 2-3 Sätzen.

### Aufgabe 1️⃣.3️⃣ - Test Cases Design

Gegeben ist folgende Spezifikation für eine Passwort-Validierungsfunktion (Sie müssen diese **nicht implementieren**, sondern nur Testfälle identifizieren):

```java
/**
 * Validiert ein Passwort nach folgenden Regeln:
 * - Mindestens 8 Zeichen lang
 * - Mindestens einen Großbuchstaben enthalten
 * - Mindestens eine Ziffer enthalten
 * - Mindestens ein Sonderzeichen (!@#$%^&*) enthalten
 * 
 * @param password Das zu validierende Passwort
 * @return true wenn das Passwort allen Regeln entspricht, false sonst
 * @throws IllegalArgumentException wenn password null ist
 */
boolean validatePassword(String password)
```

Identifizieren Sie **mindestens 8 verschiedene Testfälle** für diese Funktion. Ordnen Sie jeden Testfall einer der folgenden Kategorien zu:
- ✅ **Positive Testfälle** (gültige Passwörter)
- ❌ **Negative Testfälle** (ungültige Passwörter)
- 📍 **Edge Cases** (Grenzfälle)

Für jeden Testfall geben Sie an:
1. **Eingabe** (das zu testende Passwort)
2. **Erwartetes Ergebnis** (true, false oder Exception)
3. **Kategorie** (Positiv/Negativ/Edge Case)
4. **Begründung** (welche Regel wird getestet/verletzt?)

> [!TIP]
> Denken Sie an **Äquivalenzklassen** und **Grenzwertanalyse**, wie sie in der Vorlesung behandelt wurden.

**Beispiel:**
| Eingabe | Erwartetes Ergebnis | Kategorie | Begründung |
|---------|---------------------|-----------|------------|
| `"Test123!@"` | `true` | ✅ Positiv | Erfüllt alle Regeln |

### Aufgabe 1️⃣.4️⃣ - Arrange-Act-Assert Pattern

Analysieren Sie folgenden Unit-Test und identifizieren Sie die drei Phasen des **Arrange-Act-Assert (AAA)** Patterns:

```java
@Test
void testCalculateDiscount() {
    ShoppingCart cart = new ShoppingCart();
    cart.addItem("Laptop", 1000.0);
    double expectedDiscount = 105.0;
    cart.addItem("Mouse", 50.0);
    double actualDiscount = cart.calculateDiscount();
    assertEquals(expectedDiscount, actualDiscount, 0.01, "Der Rabatt sollte 10% des Gesamtbetrags betragen");
    assertTrue(actualDiscount > 0, "Rabatt muss positiv sein");
}
```

Markieren Sie für jede Zeile, zu welcher Phase sie gehört: `[ARRANGE]`, `[ACT]` oder `[ASSERT]`.

## Aufgabe 2️⃣ - JUnit Einrichtung

Um Tests in Java-Projekten zu implementieren, benötigen wir das Testing-Framework **JUnit**. JUnit ist eine externe Bibliothek, die in Ihr Projekt eingebunden werden muss.

> [!IMPORTANT]
> **Was ist Maven?** Maven ist ein Build-Management-Tool, das uns hilft, externe Bibliotheken (wie JUnit) automatisch herunterzuladen und in unser Projekt einzubinden. Stellen Sie sich Maven wie einen "Paketmanager" vor - ähnlich wie ein App Store, der die benötigte Software für uns verwaltet.
> 
> **Warum verwenden wir Maven?** Ohne Maven müssten Sie JUnit manuell herunterladen, die JAR-Dateien in Ihr Projekt kopieren und den Classpath konfigurieren - ein fehleranfälliger Prozess. Mit Maven reicht es, die Abhängigkeit in der `pom.xml` zu definieren, und Maven erledigt den Rest automatisch.
> 
> **Wichtig:** Maven selbst ist **nicht** Thema dieser Übung. Wir nutzen es nur als praktisches Werkzeug, um JUnit einzubinden - ähnlich wie Sie einen Schraubenzieher verwenden, ohne seine Metallurgie studieren zu müssen.

### Aufgabe 2️⃣.1️⃣ - Maven-Projekt erstellen

Ein Maven-Projekt folgt dieser Struktur:

```
mein-projekt/
├── src/
│   ├── main/java/     # Produktivcode
│   └── test/java/     # Test-Klassen
└── pom.xml            # Maven-Konfiguration
```

Erstellen Sie ein neues Maven-Projekt in Ihrer IDE. Beim Anlegen können die sogenannten GAV-Koordinaten (GroupId, ArtifactId, Version) wie folgt gesetzt werden:
- **Group ID:** `de.dhbw.ka`
- **Artifact ID:** `junit-test-project`
- **Version:** `1.0`
Sie können aber auch beliebige andere Werte verwenden.

**Eclipse:**  
`File` → `New` → `Maven Project` → `Create a simple project` aktivieren  
Group ID: `de.dhbw.ka`, Artifact ID: `junit-test-project`

**IntelliJ IDEA:**  
`File` → `New` → `Project` → `Maven` auswählen  
Group ID: `de.dhbw.ka`, Artifact ID: `junit-test-project`

**Visual Studio Code:**  
Command Palette (`Ctrl+Shift+P`) → `Java: Create Java Project` → `Maven`  
Group ID: `de.dhbw.ka`, Artifact ID: `junit-test-project`

> [!TIP]
> **Hilfreiche Ressourcen für JUnit-Testing in Ihrer IDE:**
> - **Eclipse:** [Vogella JUnit 5 Tutorial](https://www.vogella.com/tutorials/JUnit/article.html), [Eclipse JUnit5 User Guide](https://www.eclipse.org/community/eclipse_newsletter/2017/october/article5.php)
> - **IntelliJ:** [JetBrains Testing in IntelliJ](https://www.jetbrains.com/help/idea/testing.html), [JetBrains Create Tests in IntelliJ](https://www.jetbrains.com/help/idea/create-tests.html), [JetBrains Run Tests in IntelliJ](https://www.jetbrains.com/help/idea/performing-tests.html)
> - **VS Code:** [Java Testing in VS Code](https://code.visualstudio.com/docs/java/java-testing), [Java VSCode Test Runner Extension](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-test)

### Aufgabe 2️⃣.2️⃣ - pom.xml konfigurieren

Öffnen Sie die `pom.xml` Datei in Ihrem Projekt. Diese Datei wurde automatisch beim Erstellen des Maven-Projekts angelegt und enthält bereits grundlegende Konfigurationen.

**Suchen Sie** in der Datei nach dem `<dependencies>` Abschnitt. Falls dieser noch nicht existiert, fügen Sie ihn nach dem `<properties>` Block (falls vorhanden) oder nach dem `<version>` Tag hinzu.

**Fügen Sie** die folgende JUnit-Abhängigkeit in den `<dependencies>` Block ein:

```xml
<dependencies>
    <!-- JUnit Jupiter (JUnit 5) für Unit-Tests -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.9.1</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

> [!NOTE]
> Falls bereits ein `<dependencies>` Block existiert, fügen Sie nur das `<dependency>` Element (ohne das umschließende `<dependencies>` Tag) zu den bestehenden Dependencies hinzu.

**Wichtige Erklärungen:**
- `<dependencies>`: Hier werden alle externe Abhängigkeiten (Bibliotheken) definiert, die das Projekt benötigt. In diesem Fall wird JUnit Jupiter (JUnit 5) eingebunden.
- `<scope>test</scope>`: Diese Angabe bedeutet, dass die Abhängigkeit nur für den Test-Code benötigt wird und nicht im Produktionscode enthalten sein muss.

**Maven-Abhängigkeiten laden:**
- **Eclipse:** Rechtsklick auf Projekt → `Maven` → `Update Project`
- **IntelliJ:** Maven-Tab → `Reload All Maven Projects` (🔄)
- **VS Code:** Sollte automatisch synchronisieren

### Aufgabe 2️⃣.3️⃣ - Setup verifizieren

Erstellen Sie eine neue Klasse `SetupTest.java` in `src/test/java/` mit folgendem Inhalt:

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class SetupTest {
    
    @Test
    void testSetup() {
        assertEquals(4, 2 + 2, "If this test passes, your setup is correct!");
    }
}
```

Führen Sie den Test aus:
- **Eclipse:** Rechtsklick → `Run As` → `JUnit Test`
- **IntelliJ:** Grüner Pfeil (▶) neben der Methode
- **VS Code:** Test-Symbol im Editor

✅ **Erfolg:** Test wird grün → Setup korrekt!  
❌ **Fehler:** Überprüfen Sie pom.xml und ob Maven die Abhängigkeiten geladen hat

> [!TIP]
> Diese Aufgabe dient nur der technischen Einrichtung. In späteren Aufgaben lernen Sie, eigene Tests zu schreiben!
