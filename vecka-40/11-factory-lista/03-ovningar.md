# 03 — Övningar

**Omfång det här paketet:** Factory (`createAccount` — enda stället för `new Account`). Sök (`findAccount`, `equalsIgnoreCase`, `null`). Meny i `Main` 1–5 med `Scanner`. `List<Account>` i `AccountRegister`. Tre filer. Ingen `SavingsAccount`, inget arv, ingen Git.

AI får föreslå rader. Du måste kunna **peka och förklara** var `new` står, hur sök fungerar, och stegkedjan för ett menyval.

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK 21. Filer: `Account.java`, `AccountRegister.java`, `Main.java`.

**Bygger på:** Inkapslad `Account` + lista från [10-inkapsling](../10-inkapsling/). Saknar du det — använd minimala skelett nedan (samma som Exam 1-kärnan).

---

## Minimal skelett (start om du saknar T1-kod)

```java
// Account.java
public class Account {
    private String owner;
    private double balance;

    public Account(String owner, double balance) {
        this.owner = owner;
        this.balance = balance;
    }

    public String getOwner() { return owner; }
    public double getBalance() { return balance; }

    public void deposit(double amount) {
        this.balance = this.balance + amount;
    }

    public void withdraw(double amount) {
        if (amount > this.balance) {
            System.out.println("Uttag medges ej — beloppet är större än saldot.");
        } else {
            this.balance = this.balance - amount;
        }
    }
}
```

```java
// AccountRegister.java — fyll på i uppgifterna
import java.util.ArrayList;
import java.util.List;

public class AccountRegister {
    private List<Account> accounts = new ArrayList<>();

    public void printAll() {
        for (int i = 0; i < accounts.size(); i++) {
            Account a = accounts.get(i);
            System.out.println(a.getOwner() + ": " + a.getBalance());
        }
    }
}
```

---

## Uppgift 1 — Problem först: flytta `new` till `createAccount`

**Mål:** Känna smärtan med `new Account` i `Main`, implementera `findAccount`, sedan **factory** så `new` bara finns i registret.

**Scenario (unikt — föreningskassa, inte bankdemo):** Föreningen **“Studio 42”** ska hålla reda på medlemmars **kassasaldo** inför en resa. Du börjar med trasig kod där `Main` skapar konton direkt — ett konto hamnar aldrig i listan.

**Trasig startkod** (kopiera till `Main.java` + utöka `AccountRegister` med en enkel `addAccount` om du behöver):

```java
// Main.java — KÖR FÖRST, observera buggen
public class Main {
    public static void main(String[] args) {
        AccountRegister register = new AccountRegister();

        Account leo = new Account("Leo", 150);
        register.addAccount(leo);

        Account mira = new Account("Mira", 60);
        mira.deposit(20);   // Mira får pengar — men finns inte i listan

        register.printAll();
    }
}
```

Lägg till i `AccountRegister` tillfälligt:

```java
public void addAccount(Account account) {
    accounts.add(account);
}
```

**Vad du ska se (problem):** Konsolen visar **bara Leo**. Miras insättning syns inte i `printAll` — hon är **spökkonto**.

**Krav (refaktorering):**
1. Implementera `findAccount(String owner)` — loop, `getOwner().equalsIgnoreCase`, `return null` sist.
2. Implementera `createAccount(String owner, double startBalance)` — **`new Account` + `accounts.add`** här och **ingen annanstans**.
3. Ta bort **alla** `new Account` från `Main`. Ersätt med `register.createAccount("Leo", 150)` och `register.createAccount("Mira", 60)`.
4. Ta bort eller sluta använda `addAccount` från `Main` — skapande ska gå via `createAccount`.
5. Hårdkodad demo i `Main` (tills uppgift 2): efter två `createAccount`, anropa `findAccount("Mira")`, `deposit(20)`, `printAll` — **två** rader ska synas.
6. Sök i projektet efter `new Account` — **en** träff: inuti `createAccount`.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public void createAccount(String owner, double startBalance) {
    Account account = new Account(owner, startBalance);
    accounts.add(account);
}

public Account findAccount(String owner) {
    for (int i = 0; i < accounts.size(); i++) {
        Account a = accounts.get(i);
        if (a.getOwner().equalsIgnoreCase(owner)) {
            return a;
        }
    }
    return null;
}
```

```java
register.createAccount("Leo", 150);
register.createAccount("Mira", 60);

Account mira = register.findAccount("Mira");
if (mira != null) {
    mira.deposit(20);
}
register.printAll();
```

Konsol ungefär: `Leo: 150.0` och `Mira: 80.0`.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **raden med `new Account`** — säg varför den bara får stå här  
- [ ] Peka på **`return null`** i `findAccount`  
- [ ] Peka i `Main` — **noll** `new Account`  
- [ ] Förklara spökkontot: vad hade `Mira` utan `add` i listan?

**Ägarskap:** Säg Exam Q2-högt: *“Objekten skapas i createAccount, inte i Main, så listan alltid får varje konto.”*

---

## Uppgift 2 — Mini-meny: två konton, insättning, stoppat uttag

**Mål:** Full meny 1–5 med `Scanner`. Köra testkedjan som Exam 1 kräver — via menyn, inte hårdkodat.

**Scenario (unikt — matlådsfond på jobbet):** Kontoret **“Nordkanten”** har en enkel **lunchfond** per kollega. Samma tre filer — nu interaktivt.

**Meny:**

| Val | Text | Handling |
|-----|------|----------|
| 1 | Skapa konto | Läs ägare + startsaldo → `createAccount` |
| 2 | Lista konton | `printAll` |
| 3 | Sätt in pengar | Läs ägare + belopp → `findAccount` → `deposit` |
| 4 | Ta ut pengar | Läs ägare + belopp → `findAccount` → `withdraw` |
| 5 | Avsluta | Lämna `while`-loopen |

**Krav:**
1. `while (choice != 5)` (eller motsvarande tydlig avslutning på val 5).
2. `Scanner` — **en** instans före loopen. Hantera `nextInt` / `nextDouble` + `nextLine` (släng radbrytning efter tal om ägarnamn läses med `nextLine`).
3. `switch (choice) { case 1 -> … }` **eller** `if` / `else if` — du ska kunna förklara ditt val.
4. Vid 3 och 4: **`if (found != null)`** innan `deposit` / `withdraw`; annars `"Kontot finns inte."`
5. Ogiltigt val (t.ex. 9) — meddelande, programmet fortsätter.
6. **Manuell testkörning** (skriv vilka val du tryckte):
   - Skapa **Leo** med startsaldo **150**
   - Skapa **Mira** med startsaldo **60**
   - Lista → **två** rader
   - Sätt in **40** på Leo → lista visar **190** på Leo
   - Ta ut **200** på Mira → **meddelande**, Miras saldo fortfarande **60**
   - Avsluta med 5

**Facit-riktning — utdrag `Main` (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        AccountRegister register = new AccountRegister();
        Scanner scanner = new Scanner(System.in);
        int choice = 0;

        while (choice != 5) {
            System.out.println("1. Skapa konto");
            System.out.println("2. Lista konton");
            System.out.println("3. Sätt in pengar");
            System.out.println("4. Ta ut pengar");
            System.out.println("5. Avsluta");
            System.out.print("Val: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1 -> {
                    scanner.nextLine();
                    System.out.print("Ägare: ");
                    String owner = scanner.nextLine();
                    System.out.print("Startsaldo: ");
                    double start = scanner.nextDouble();
                    register.createAccount(owner, start);
                }
                case 2 -> register.printAll();
                case 3 -> {
                    scanner.nextLine();
                    System.out.print("Ägare: ");
                    String owner = scanner.nextLine();
                    System.out.print("Belopp: ");
                    double amount = scanner.nextDouble();
                    Account found = register.findAccount(owner);
                    if (found != null) {
                        found.deposit(amount);
                    } else {
                        System.out.println("Kontot finns inte.");
                    }
                }
                case 4 -> {
                    scanner.nextLine();
                    System.out.print("Ägare: ");
                    String owner = scanner.nextLine();
                    System.out.print("Belopp: ");
                    double amount = scanner.nextDouble();
                    Account found = register.findAccount(owner);
                    if (found != null) {
                        found.withdraw(amount);
                    } else {
                        System.out.println("Kontot finns inte.");
                    }
                }
                case 5 -> System.out.println("Nordkanten — fond avslutad.");
                default -> System.out.println("Ogiltigt val.");
            }
        }
        scanner.close();
    }
}
```

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`createAccount`-anropet** i case 1 — inte `new Account`  
- [ ] Peka på **null-grenen** i case 3 eller 4  
- [ ] Peka på **`withdraw`-anropet** efter lyckad sök — uttagsregeln sitter i `Account`  
- [ ] Beskriv **stegkedja** för val 4 i 4 steg (Exam README Q3-träning)  
- [ ] Bekräfta testkörning: två konton, insättning, stoppat uttag, avslut

**Ägarskap:** Du ska kunna köra demon **utan att läsa facit** och förklara var `new` finns om någon frågar i IDE.

---

## Stretch (frivilligt, inom VAD)

- Testa sök med `"leo"` när kontot skapades som `"Leo"` — dokumentera i en kommentar (eller anteckning) varför det funkar.  
- Skriv **README Q2-utkast** (2–4 meningar) om factory — peka på `createAccount` i din fil.  
- Lägg till tom-lista-meddelande i `printAll`: `"Inga konton registrerade."` när `size() == 0`.

**INTE i stretch här:** `SavingsAccount`, arv, Git-commit, PR.

---

## När du kört fast

1. *missing return statement* i `findAccount` → lägg `return null` efter loopen.  
2. *cannot find symbol equalsIgnoreCase on Account* → du glömde `getOwner()`.  
3. `NullPointerException` vid insättning → `findAccount` gav `null` — lägg null-koll.  
4. `new Account` kvar i `Main` → flytta till `createAccount`.  
5. Tom rad efter `nextInt` “äter” ägarnamn → extra `nextLine()` efter tal.  
6. Lista visar ett konto → andra skapades utan `add` i `createAccount`.  
7. Jämför [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
8. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
