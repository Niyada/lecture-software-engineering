# 🧹 Clean Code Übungen

Diese Aufgaben helfen Ihnen dabei, die Prinzipien von Clean Code zu verstehen und anzuwenden.

## Aufgabe 1️⃣ (Naming Conventions)

### Teil A: E-Commerce Bestellverarbeitung
Die folgende Klasse verarbeitet Bestellungen in einem Online-Shop. Analysieren Sie die Namen und schlagen Sie bessere Alternativen vor.

```java
public class DataManager {
    private String statusMsg;
    private int qty;
    private double price;
    private boolean processed;
    
    public void processIfReady(int threshold) {
        if (processed && qty > threshold) {
            statusMsg = "completed";
        }
    }
    
    public double calcTax(double netAmount, double taxRate) {
        return netAmount * taxRate * 0.19;
    }
    
    public boolean isValid(String input) {
        return input != null && input.length() > 0;
    }
}
```

**Ihre Aufgabe:** 
1. Identifizieren Sie alle problematischen Namen
2. Schlagen Sie bessere Namen vor basierend auf dem Kontext (E-Commerce)
3. Begründen Sie Ihre Entscheidungen

### Teil B: User Management System 
Das folgende System verwaltet Benutzer einer Web-Anwendung. Bewerten Sie die Namen und schlagen Sie Verbesserungen vor:

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

## 🔄 Aufgabe 2️⃣ (Readability - Verschachtelung und Guard-Clauses)

Refaktorieren Sie die folgende Methode mit Guard-Clauses, um die Verschachtelung zu reduzieren:

```java
public class UserValidator {
    
    public boolean validateUser(User user, String password) {
        if (user != null) {
            if (user.isActive()) {
                if (password != null) {
                    if (password.length() >= 8) {
                        if (user.getEmail() != null && user.getEmail().contains("@")) {
                            return true;
                        } else {
                            System.out.println("Invalid email");
                            return false;
                        }
                    } else {
                        System.out.println("Password too short");
                        return false;
                    }
                } else {
                    System.out.println("Password required");
                    return false;
                }
            } else {
                System.out.println("User not active");
                return false;
            }
        } else {
            System.out.println("User required");
            return false;
        }
    }
}
```

**Ihre Aufgabe:** Verbessern Sie die Lesbarkeit indem sie die Verschachtelung reduzieren.

> [!TIP]
> Verwenden Sie Guard-Clauses, um die Lesbarkeit zu verbessern.

## 📐 Aufgabe 3️⃣ (Readability - Formatting)

Verbessern Sie die Formatierung des folgenden Codes:

```java
public class DiscountCalculator{
private static final double STUDENT_DISCOUNT=0.1;private static final double SENIOR_DISCOUNT = 0.15;
private static final double EMPLOYEE_DISCOUNT=0.2;
public double calculateDiscount(Customer customer,double amount){
if(customer.getType()==CustomerType.STUDENT){return amount*STUDENT_DISCOUNT;
}else if(customer.getType()==CustomerType.SENIOR){
return amount*SENIOR_DISCOUNT;}else if(customer.getType()==CustomerType.EMPLOYEE)
{return amount*EMPLOYEE_DISCOUNT;}else{return 0.0;}}
public boolean isEligibleForDiscount(Customer customer) {return customer.getType() == CustomerType.STUDENT || customer.getType() == CustomerType.SENIOR||customer.getType()==CustomerType.EMPLOYEE;}
}
```

**Ihre Aufgabe:** Formatieren Sie den Code korrekt und strukturieren Sie ihn übersichtlich.

## 💬 Aufgabe 4️⃣ (Readability - Kommentare)

Verbessern Sie die Kommentare in folgendem Code:

```java
public class BankAccount {
    private double balance; // balance variable
    private String accountNumber; // account number
    
    /**
     * Constructor for BankAccount
     * @param accountNumber the account number
     * @param initialBalance the initial balance
     */
    public BankAccount(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber; // set account number
        this.balance = initialBalance; // set balance
    }
    
    // Method to withdraw money
    public boolean withdraw(double amount) {
        // Check if amount is positive
        if (amount <= 0) {
            return false; // return false if amount is not positive
        }
        
        // Magic number: minimum balance must be maintained
        if (balance - amount < 10.0) {
            return false; // insufficient funds
        }
        
        balance -= amount; // subtract amount from balance
        return true; // return true if successful
    }
    
    // TODO: Implement deposit method
    public void deposit(double amount) {
        // Implementation pending
    }
}
```

**Ihre Aufgabe:** 
1. Entfernen Sie überflüssige Kommentare
2. Verbessern Sie nötige Kommentare
3. Ersetzen Sie Magic Numbers durch benannte Konstanten

## 🔧 Aufgabe 5️⃣ (Comprehensive Refactoring)

Die folgende Klasse berechnet Kundenrabatte basierend auf Kundentyp, Bestellbetrag und Kundentreue. Refaktorieren Sie die Klasse nach allen Clean Code Prinzipien:

```java
public class CalcMgr {
    private double bsal;
    
    public CalcMgr() {
        bsal = 3000.0;
    }
    
    // calculates discount for customer
    public double calc(int type, double amt, int yrs) {
        double disc = 0; // discount amount
        
        if (type == 1) { // bronze customer
            if (yrs > 2) {
                disc = amt * 0.05;
            }
        } else if (type == 2) { // silver customer  
            if (yrs > 5) {
                disc = amt * 0.1;
            } else {
                disc = amt * 0.05;
            }
        } else if (type == 3) { // gold customer
            if (amt > 1000) {
                disc = amt * 0.15 + 100; // extra bonus
            } else {
                disc = amt * 0.15;
            }
        }
        
        return disc;
    }
    
    public boolean chk(int type) { // checks if customer type is valid
        return type >= 1 && type <= 3;
    }
}
```

**Ihre Aufgabe:** 
1. Verbessern Sie alle Namen (Klasse, Methoden, Variablen)
2. Reduzieren Sie Verschachtelung durch Guard-Clauses
3. Formatieren Sie den Code korrekt
4. Entfernen Sie überflüssige Kommentare und verbessern Sie nötige
5. Extrahieren Sie Konstanten für Magic Numbers

## 💭 Reflexionsfragen

### 🎯 Ziele:
- Welche Prinzipien von Clean Code fanden Sie am wichtigsten?
- Welche Herausforderungen sind Ihnen beim Refaktorisieren begegnet?
- Welche Verbesserungen haben Sie als am wertvollsten empfunden?