# 🧪 Übungsaufgaben - Software Testing - Musterlösungen

## Aufgabe 1️⃣ - Grundlagen des Unit Testing

### Aufgabe 1️⃣.1️⃣ - Warum Testen?

**Mögliche Antworten (drei Vorteile):**

1. **Frühe Fehlererkennung**: Automatisierte Tests hätten den Fehler bereits während der Entwicklung gefunden, bevor die Software an Kunden ausgeliefert wurde. Dadurch wären die Kosten für die Fehlerbehebung deutlich niedriger gewesen.

2. **Dokumentation des erwarteten Verhaltens**: Tests beschreiben konkret, wie die Rabattfunktion bei verschiedenen Eingaben (z.B. genau 100€) funktionieren sollte. Dies hätte dem Entwickler geholfen, alle relevanten Fälle zu berücksichtigen.

3. **Vertrauen bei Änderungen**: Mit Tests kann das Team die Funktion später sicher erweitern oder refactoren, da Tests sofort anzeigen würden, ob durch Änderungen unerwartete Fehler entstehen (Regressionstests).

**Weitere mögliche Antworten:**
- Schnellere Entwicklung auf lange Sicht (Tests sparen Zeit bei der manuellen Überprüfung)
- Bessere Codequalität durch testgetriebenes Design
- Reduzierung des Wartungsaufwands

---

### Aufgabe 1️⃣.2️⃣ - FIRST-Prinzipien verstehen

**a) Independent (Unabhängig)**

Unit-Tests sollten unabhängig voneinander sein, damit sie in beliebiger Reihenfolge und parallel ausgeführt werden können. Wenn Tests voneinander abhängig sind, kann der Fehler in einem Test dazu führen, dass viele andere Tests ebenfalls fehlschlagen, obwohl deren getesteter Code korrekt ist. Dies erschwert die Fehlersuche erheblich und macht die Tests unzuverlässig. Außerdem können abhängige Tests nicht parallel ausgeführt werden, was die Testausführung verlangsamt.

**b) Repeatable (Wiederholbar)**

Hier wird das FIRST-Prinzip **Repeatable (Wiederholbar)** verletzt. Ein Test, der manchmal erfolgreich ist und manchmal fehlschlägt, ohne dass sich der Code geändert hat, ist ein sogenannter "flaky test". Dies ist problematisch, weil man dem Testergebnis nicht vertrauen kann. Ursachen können externe Abhängigkeiten (z.B. Netzwerk, Datenbank), Race Conditions bei paralleler Ausführung oder Abhängigkeiten von Systemzeit/Zufall sein. Solche Tests untergraben das Vertrauen in die gesamte Testsuite.

**c) Self-Validating (Selbstvalidierend)**

Tests sollten selbstvalidierend sein, d.h. automatisch prüfen, ob das Ergebnis korrekt ist (mit Assertions wie `assertEquals`). Die Alternative wäre, dass der Test eine Ausgabe produziert (z.B. mit `System.out.println`) und ein Entwickler manuell prüfen muss, ob die Ausgabe korrekt ist. Dies ist fehleranfällig, zeitaufwändig und nicht automatisierbar. Selbstvalidierende Tests geben ein klares "Grün" (bestanden) oder "Rot" (fehlgeschlagen) zurück, ohne menschliche Interpretation.

---

### Aufgabe 1️⃣.3️⃣ - Test Cases Design

**Beispiel-Testfälle für die Passwort-Validierung:**

| # | Eingabe | Erwartetes Ergebnis | Kategorie | Begründung |
|---|---------|---------------------|-----------|------------|
| 1 | `"Password1!"` | `true` | ✅ Positiv | Erfüllt alle Regeln: 10 Zeichen, Großbuchstabe (P), Ziffer (1), Sonderzeichen (!) |
| 2 | `"Secure@2024"` | `true` | ✅ Positiv | Erfüllt alle Regeln: 12 Zeichen, Großbuchstabe (S), Ziffern (2024), Sonderzeichen (@) |
| 3 | `"short1!"` | `false` | ❌ Negativ | Zu kurz - nur 7 Zeichen (Regel: mindestens 8) |
| 4 | `"password123!"` | `false` | ❌ Negativ | Kein Großbuchstabe vorhanden |
| 5 | `"Password!"` | `false` | ❌ Negativ | Keine Ziffer vorhanden |
| 6 | `"Password123"` | `false` | ❌ Negativ | Kein Sonderzeichen vorhanden |
| 7 | `null` | `IllegalArgumentException` | 📍 Edge Case | Gemäß Spezifikation soll eine Exception geworfen werden |
| 8 | `""` (leerer String) | `false` | 📍 Edge Case | Grenzfall: 0 Zeichen, verletzt Mindestlänge |
| 9 | `"PassWD1!"` | `true` | 📍 Edge Case | Exakt 8 Zeichen (Grenzwert der Mindestlänge) - **Grenzwertanalyse** |
| 10 | `"PASSWOR1!"` | `true` | 📍 Edge Case | Nur Großbuchstaben, aber ein Großbuchstabe ist ausreichend |
| 11 | `"Password111!"` | `true` | 📍 Edge Case | Mehrere Ziffern - testet, dass "mindestens eine" auch bei mehreren funktioniert |
| 12 | `"Pass!@#$%1"` | `true` | 📍 Edge Case | Mehrere Sonderzeichen - testet alle erlaubten Sonderzeichen |

---

### Aufgabe 1️⃣.4️⃣ - Arrange-Act-Assert Pattern

```java
@Test
void testCalculateDiscount() {
    // [ARRANGE] - Vorbereitung der Testdaten
    ShoppingCart cart = new ShoppingCart();
    cart.addItem("Laptop", 1000.0);
    // [ARRANGE] - Vorbereitung (expectedDiscount gehört zur Vorbereitung)
    double expectedDiscount = 105.0;
    // [ARRANGE] - Vorbereitung (weiteres Item hinzufügen)
    cart.addItem("Mouse", 50.0);
    
    // [ACT] - Ausführung der zu testenden Methode
    double actualDiscount = cart.calculateDiscount();
    
    // [ASSERT] - Überprüfung des Ergebnisses
    assertEquals(expectedDiscount, actualDiscount, 0.01, "Der Rabatt sollte 10% des Gesamtbetrags betragen");
    // [ASSERT] - Weitere Überprüfung
    assertTrue(actualDiscount > 0, "Rabatt muss positiv sein");
}
```

**Warum ist diese Strukturierung sinnvoll?**

Die AAA-Strukturierung macht Tests übersichtlich und leicht verständlich. Jeder Test folgt dem gleichen Muster, was das Lesen und Warten erleichtert. Wichtig: Nicht alle Zeilen stehen in der "logischen" Reihenfolge - `expectedDiscount` steht zwischen zwei `addItem()` Aufrufen, gehört aber konzeptionell zur Arrange-Phase.

---

## Aufgabe 2️⃣ - JUnit Einrichtung

### Aufgabe 2️⃣.1️⃣ - Maven-Projekt erstellen

**Projektstruktur nach erfolgreicher Erstellung:**

```
junit-test-project/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── de/
│   │           └── dhbw/
│   │               └── ka/
│   └── test/
│       └── java/
│           └── de/
│               └── dhbw/
│                   └── ka/
├── pom.xml
└── target/
```

---

### Aufgabe 2️⃣.2️⃣ - pom.xml konfigurieren

Die JUnit-Abhängigkeit sollte korrekt hinzugefügt worden sein. Falls Probleme auftreten, überprüfen Sie:
- Maven hat Internetzugriff
- Die pom.xml ist korrekt formatiert (valides XML)
- Maven Update wurde durchgeführt

---

### Aufgabe 2️⃣.3️⃣ - Setup verifizieren

Der Test sollte erfolgreich durchlaufen (grün). Falls nicht:
- Überprüfen Sie, ob JUnit korrekt in der pom.xml eingebunden ist
- Führen Sie Maven Update durch
- Stellen Sie sicher, dass die Test-Klasse in `src/test/java/` liegt

---

## Aufgabe 3️⃣ - Tests für AnagramChecker schreiben

### Musterlösung - AnagramCheckerTest

```java
package de.dhbw.ka;

import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class AnagramCheckerTest {

    AnagramChecker anagramChecker = new AnagramChecker();

    // ========== Teil 3.1: Geführte Tests ==========

    @Test
    @DisplayName("Should return true for simple anagram")
    void shouldReturnTrueForSimpleAnagram() {
        assertTrue(anagramChecker.check("listen", "silent"));
    }

    @Test
    @DisplayName("Should return false for non-anagram")
    void shouldReturnFalseForNonAnagram() {
        assertFalse(anagramChecker.check("hello", "world"));
    }

    @Test
    @DisplayName("Should return false for different lengths")
    void shouldReturnFalseForDifferentLengths() {
        assertFalse(anagramChecker.check("test", "tests"));
    }

    @Test
    @DisplayName("Should return true for anagram with spaces")
    void shouldReturnTrueForAnagramWithSpaces() {
        assertTrue(anagramChecker.check("conversation", "voices rant on"));
    }

    @Test
    @DisplayName("Should return true for anagram with different cases")
    void shouldReturnTrueForAnagramWithDifferentCases() {
        assertTrue(anagramChecker.check("Listen", "Silent"));
    }

    @Test
    @DisplayName("Should return false when both inputs are null")
    void shouldReturnFalseForBothNull() {
        assertFalse(anagramChecker.check(null, null));
    }

    @Test
    @DisplayName("Should return false when first input is null")
    void shouldReturnFalseForFirstNull() {
        assertFalse(anagramChecker.check(null, "silent"));
    }

    @Test
    @DisplayName("Should return false when second input is null")
    void shouldReturnFalseForSecondNull() {
        assertFalse(anagramChecker.check("listen", null));
    }

    @Test
    @DisplayName("Should return true for empty strings")
    void shouldReturnTrueForEmptyStrings() {
        assertTrue(anagramChecker.check("", ""));
    }

    @Test
    @DisplayName("Should return false when only one string is empty")
    void shouldReturnFalseForOneEmptyString() {
        assertFalse(anagramChecker.check("", "a"));
        assertFalse(anagramChecker.check("a", ""));
    }

    // ========== Teil 3.2: Eigene Tests ==========

    @Test
    @DisplayName("Should return true for the same word")
    void shouldReturnTrueForTheSameWord() {
        assertTrue(anagramChecker.check("word", "word"));
    }

    @Test
    @DisplayName("Should return true for longer anagram")
    void shouldReturnTrueForLongerAnagram() {
        assertTrue(anagramChecker.check("astronomer", "moon starer"));
    }

    @Test
    @DisplayName("Should return true for anagram with different cases")
    void shouldReturnTrueForAnagrammWithDifferentCases() {
        assertTrue(anagramChecker.check("Listen", "Silent"));
    }

    // ========== Zusätzliche interessante Tests ==========

    @Test
    @DisplayName("Should return true for anagram with multiple spaces")
    void shouldReturnTrueForMultipleSpaces() {
        assertTrue(anagramChecker.check("a   b   c", "c  b  a"));
    }

    @Test
    @DisplayName("Should return true for single character")
    void shouldReturnTrueForSingleCharacter() {
        assertTrue(anagramChecker.check("a", "a"));
    }
}
```

---

## 📝 Hinweise zur Implementierung

### **Wichtig für Dozenten: Limitation der AnagramChecker Implementierung**

⚠️ **Die AnagramChecker Implementierung hat eine bewusste Einschränkung:**

Die Zeile `characterCounts[character - 'a']++` nimmt an, dass **alle** Zeichen im Bereich 'a'-'z' liegen (nach Normalisierung).

**Was passiert bei nicht unterstützten Zeichen:**
- **Umlaute**: `"café"` → `ArrayIndexOutOfBoundsException` 
- **Zahlen**: `"test123"` → `ArrayIndexOutOfBoundsException`
- **Sonderzeichen**: `"hello!"` → `ArrayIndexOutOfBoundsException`

**Didaktischer Wert:**
- Studenten, die diese Edge Cases selbst testen, entdecken die Limitation
- Lehrt, dass Code oft undokumentierte Annahmen hat
- Fördert defensive Testing-Strategien
- Realitätsnah - echte Software hat ähnliche Einschränkungen

**Wenn Studenten danach fragen:**
Die Implementierung unterstützt bewusst nur englische Buchstaben (a-z). In einer Produktionsumgebung würde man entweder:
1. Die Limitation dokumentieren, oder
2. Nicht-unterstützte Zeichen filtern: `normalizedWord.replaceAll("[^a-z]", "")`

