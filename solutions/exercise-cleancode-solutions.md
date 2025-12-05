# 🧹 Clean Code Übungen - Musterlösungen

## 🏷️ Aufgabe 1️⃣ (Naming Conventions) - Lösung

### Teil A: E-Commerce Bestellverarbeitung - Lösung

**Ursprünglich:**
```java
public class DataManager {
    private String statusMsg;
    private int qty;
    private double price;
    private boolean processed;
    
    public void processIfReady(int threshold) { ... }
    public double calcTax(double netAmount, double taxRate) { ... }
    public boolean isValid(String input) { ... }
}
```

**Verbessert:**
```java
public class OrderProcessor {
    private static final double TAX_RATE = 0.19;
    
    private String orderStatus;
    private int itemQuantity;
    private double itemPriceInEuros;
    private boolean isProcessed;
    
    public void processOrder(int minimumQuantity) {
        if (isProcessed && itemQuantity > minimumQuantity) {
            orderStatus = "completed";
        }
    }
    
    public double calculateTaxAmount(double netAmount, double taxRate) {
        return netAmount * taxRate * TAX_RATE;
    }
    
    public boolean isValidInput(String input) {
        return input != null && input.length() > 0;
    }
}
```

**Verbesserungen:**
- `DataManager` → `OrderProcessor` (spezifischer Kontext: E-Commerce)
- `statusMsg` → `orderStatus` (vollständiger, aussagekräftiger Name)
- `qty` → `itemQuantity` (keine Abkürzung, klar was gezählt wird)
- `price` → `itemPriceInEuros` (mit Einheit für Klarheit)
- `processed` → `isProcessed` (boolean-Präfix `is`)
- `processIfReady` → `processOrder` (Verb + Objekt, klarer Zweck)
- `calcTax` → `calculateTaxAmount` (vollständig, spezifischer)
- Magic Number `0.19` → `TAX_RATE` Konstante

### Teil B: User Management System - Lösung

**Ursprünglich:**
```java
public class Helper {
    public static final int MAX = 100;
    public static final String STR = "pending";
    public static final double FACTOR = 1.5;
    public static final int TIMEOUT = 300;
}

public class ProcessorUtils {
    public void doStuff() { }
    public String getData() { }
    public void handleInfo() { }
}
```

**Verbessert:**
```java
public class UserConfig {
    public static final int MAX_USERNAME_LENGTH = 100;
    public static final String DEFAULT_USER_STATUS = "pending";
    public static final double PREMIUM_PRICE_MULTIPLIER = 1.5;
    public static final int SESSION_TIMEOUT_SECONDS = 300;
}

public class UserService {
    public void createUser() { }
    public String getUserDetails() { }
    public void updateUserProfile() { }
}
```

**Verbesserungen:**
- `Helper` → `UserConfig` (spezifischer Zweck statt generisches "Helper")
- `MAX` → `MAX_USERNAME_LENGTH` (was ist das Maximum?)
- `STR` → `DEFAULT_USER_STATUS` (was für ein String?)
- `FACTOR` → `PREMIUM_PRICE_MULTIPLIER` (was für ein Faktor?)
- `TIMEOUT` → `SESSION_TIMEOUT_SECONDS` (Einheit im Namen!)
- `ProcessorUtils` → `UserService` (Domain-spezifisch statt generisch)
- `doStuff` → `createUser` (was wird getan?)
- `getData` → `getUserDetails` (welche Daten?)
- `handleInfo` → `updateUserProfile` (wie wird Information behandelt?)


## 🔄 Aufgabe 2️⃣ (Guard-Clauses) - Lösung

**Verbessert:**
```java
public class UserValidator {
    
    public boolean validateUser(User user, String password) {
        if (user == null) {
            System.out.println("User required");
            return false;
        }
        
        if (!user.isActive()) {
            System.out.println("User not active");
            return false;
        }
        
        if (password == null) {
            System.out.println("Password required");
            return false;
        }
        
        if (password.length() < 8) {
            System.out.println("Password too short");
            return false;
        }
        
        if (user.getEmail() == null || !user.getEmail().contains("@")) {
            System.out.println("Invalid email");
            return false;
        }
        
        return true;
    }
}
```

**Verbesserungen:**
- Reduzierte Verschachtelung von 5 auf 0 Ebenen
- Frühe Rückgabe bei Fehlern (Fail Fast Prinzip)
- Deutlich bessere Lesbarkeit
- Einfacher zu erweitern und zu testen

## 📐 Aufgabe 3️⃣ (Formatting) - Lösung

**Verbessert:**
```java
public class DiscountCalculator {
    
    private static final double STUDENT_DISCOUNT = 0.1;
    private static final double SENIOR_DISCOUNT = 0.15;
    private static final double EMPLOYEE_DISCOUNT = 0.2;
    
    public double calculateDiscount(Customer customer, double amount) {
        if (customer.getType() == CustomerType.STUDENT) {
            return amount * STUDENT_DISCOUNT;
        }
        
        if (customer.getType() == CustomerType.SENIOR) {
            return amount * SENIOR_DISCOUNT;
        }
        
        if (customer.getType() == CustomerType.EMPLOYEE) {
            return amount * EMPLOYEE_DISCOUNT;
        }
        
        return 0.0;
    }
    
    public boolean isEligibleForDiscount(Customer customer) {
        return customer.getType() == CustomerType.STUDENT 
            || customer.getType() == CustomerType.SENIOR
            || customer.getType() == CustomerType.EMPLOYEE;
    }
}
```

**Verbesserungen:**
- Konsistente Einrückung und Leerzeichen
- Leerzeilen zur Strukturierung
- Aufgebrochene lange Zeilen
- Konsistente Klammern-Platzierung

## 💬 Aufgabe 4️⃣ (Kommentare) - Lösung

**Verbessert:**
```java
public class BankAccount {
    
    private static final double MINIMUM_BALANCE = 10.0;
    
    private double balance;
    private String accountNumber;
    
    public BankAccount(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }
    
    /**
     * Withdraws the specified amount from the account.
     * Maintains minimum balance requirement.
     * 
     * @param amount the amount to withdraw (must be positive)
     * @return true if withdrawal was successful, false otherwise
     */
    public boolean withdraw(double amount) {
        if (amount <= 0) {
            return false;
        }
        
        if (balance - amount < MINIMUM_BALANCE) {
            return false;
        }
        
        balance -= amount;
        return true;
    }
    
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
}
```

**Verbesserungen:**
- Überflüssige Kommentare entfernt
- Magic Number durch Konstante ersetzt
- Sinnvolle Javadoc für öffentliche API
- TODO entfernt und Methode implementiert

## 🔧 Aufgabe 5️⃣ (Comprehensive Refactoring) - Lösung

**Verbessert:**
```java
public class CustomerDiscountCalculator {
    
    // Customer types
    private static final int BRONZE_CUSTOMER = 1;
    private static final int SILVER_CUSTOMER = 2;
    private static final int GOLD_CUSTOMER = 3;
    
    // Discount rates
    private static final double BRONZE_DISCOUNT_RATE = 0.05;
    private static final double SILVER_DISCOUNT_RATE = 0.1;
    private static final double SILVER_BASE_RATE = 0.05;
    private static final double GOLD_DISCOUNT_RATE = 0.15;
    
    // Thresholds
    private static final int BRONZE_YEARS_THRESHOLD = 2;
    private static final int SILVER_YEARS_THRESHOLD = 5;
    private static final double GOLD_AMOUNT_THRESHOLD = 1000.0;
    private static final double GOLD_BONUS = 100.0;
    
    public double calculateDiscount(int customerType, double orderAmount, int yearsAsCustomer) {
        if (customerType == BRONZE_CUSTOMER) {
            return calculateBronzeDiscount(orderAmount, yearsAsCustomer);
        }
        
        if (customerType == SILVER_CUSTOMER) {
            return calculateSilverDiscount(orderAmount, yearsAsCustomer);
        }
        
        if (customerType == GOLD_CUSTOMER) {
            return calculateGoldDiscount(orderAmount);
        }
        
        return 0.0;
    }
    
    private double calculateBronzeDiscount(double amount, int years) {
        if (years <= BRONZE_YEARS_THRESHOLD) {
            return 0.0;
        }
        return amount * BRONZE_DISCOUNT_RATE;
    }
    
    private double calculateSilverDiscount(double amount, int years) {
        if (years > SILVER_YEARS_THRESHOLD) {
            return amount * SILVER_DISCOUNT_RATE;
        }
        return amount * SILVER_BASE_RATE;
    }
    
    private double calculateGoldDiscount(double amount) {
        double discount = amount * GOLD_DISCOUNT_RATE;
        
        if (amount > GOLD_AMOUNT_THRESHOLD) {
            discount += GOLD_BONUS;
        }
        
        return discount;
    }
    
    public boolean isValidCustomerType(int customerType) {
        return customerType >= BRONZE_CUSTOMER && customerType <= GOLD_CUSTOMER;
    }
}
```

**Verbesserungen:**

1. **Naming:** 
   - `CalcMgr` → `CustomerDiscountCalculator`
   - `calc` → `calculateDiscount`
   - `chk` → `isValidCustomerType`
   - `bsal` → Entfernt (da nicht benötigt, genauso wie der Konstruktor)

2. **Verschachtelung:** 
   - Guard clauses implementiert
   - Komplexe Logik in kleinere Methoden aufgeteilt

3. **Formatierung:** 
   - Konsistente Einrückung und Leerzeichen
   - Strukturierung durch Leerzeilen und Kommentarblöcke

4. **Kommentare:** 
   - Überflüssige Kommentare entfernt
   - Code ist durch bessere Namen selbsterklärend

5. **Konstanten:** 
   - Alle Magic Numbers durch aussagekräftige Konstanten ersetzt
   - Logische Gruppierung der Konstanten

