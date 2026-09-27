# 03 — Övningar

**Omfång det här paketet:** `private` fält på `Account`, konstruktor `Account(String owner, double initialBalance)`, getters `getOwner()` / `getBalance()`, befintliga `deposit` / `withdraw`. `AccountRegister` med `List<Account>`, `add`, `printAll` — minst **två** konton. **Ingen** `createAccount`, **ingen** meny, **ingen** `Scanner` krävs.

AI får föreslå rader. Du måste kunna **peka och förklara** `private`, getters, konstruktorn, listan — och skriva **Exam README Q1** (inkapsling).

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK. Tre filer: `Account.java`, `AccountRegister.java`, `Main.java`.

**Bygger på:** `Account` med `deposit` / `withdraw` från [09-transaktioner](../../vecka-39/09-transaktioner/). Saknar du metoderna — inkludera dem i `Account` (uttagsregeln ska fortfarande gälla).

---

## Uppgift 1 — Lås valvet: `private`, konstruktor, getters

**Mål:** Refaktorera `Account` från öppna fält till inkapslad klass med konstruktor och getters. Känn `has private access` — fixa utan att ta bort `private`.

**Scenario:** “NordBank” kräver att saldo **inte** kan skrivas från foajén (`Main`). Du migrerar från `nora.owner = ...` till `new Account(...)` + getters.

**Startpunkt** (öppen `Account` — byt ut enligt krav):

```java
// Account.java — före
public class Account {
    String owner;
    double balance;

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

**Krav:**
1. Gör `owner` och `balance` **`private`**.
2. Lägg till konstruktor: `public Account(String owner, double initialBalance)` med `this.owner = owner` och `this.balance = initialBalance`.
3. Lägg till `getOwner()` och `getBalance()` (Exam-namn).
4. Behåll `deposit` / `withdraw` — de ska fortfarande fungera **inuti** klassen.
5. I `Main`: skapa `Account nora = new Account("Nora", 300.0);` — **inte** `nora.owner = ...`.
6. Skriv med flit **en rad** `System.out.println(nora.balance);` — kompilera, **läs** felet (`has private access`), kommentera bort raden, byt till `nora.getBalance()`.
7. **Ingen** `setBalance` / `setOwner`.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public class Account {
    private String owner;
    private double balance;

    public Account(String owner, double initialBalance) {
        this.owner = owner;
        this.balance = initialBalance;
    }

    public String getOwner() {
        return owner;
    }

    public double getBalance() {
        return balance;
    }

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
public class Main {
    public static void main(String[] args) {
        Account nora = new Account("Nora", 300.0);
        // System.out.println(nora.balance);  // has private access — medvetet borttaget
        System.out.println(nora.getOwner() + ": " + nora.getBalance());
        nora.deposit(50.0);
        System.out.println("Efter deposit: " + nora.getBalance());
    }
}
```

Konsol (ungefär): `Nora: 300.0` sedan `Efter deposit: 350.0`.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`private`** framför `balance` — vad hade hänt utan det? (Exam Q1)  
- [ ] Peka på **konstruktorn** — var sätts startvärdet?  
- [ ] Peka på **`getBalance()`** — varför inte `nora.balance` i `Main`?  
- [ ] Peka på **`withdraw`** — fungerar den fortfarande inuti klassen trots `private`?  
- [ ] Programmet kompilerar och kör

**Ägarskap:** Du ska kunna förklara inkapsling som bankvalv med låsta fack — inte “AI la till private”.

---

## Uppgift 2 — `AccountRegister`: minst två konton i listan

**Mål:** Skapa `AccountRegister` med `List<Account>`, lägg till **minst två** konton, skriv ut alla med `printAll`.

**Scenario:** NordBank ska visa **hela valvboken** — inte bara ett konto i taget i `Main`.

**Krav:**
1. Ny fil `AccountRegister.java` med:
   - `import java.util.ArrayList;` och `import java.util.List;`
   - `private List<Account> accounts = new ArrayList<>();` (**inte** `ArrayList` som deklarerad typ)
   - `public void add(Account account)` som gör `accounts.add(account)`
   - `public void printAll()` som loopar `0 … size()-1` och skriver `getOwner()` + `getBalance()` per rad (eller anropar en metod på kontot)
2. I `Main`: `AccountRegister register = new AccountRegister();`
3. Lägg till minst **två** konton, t.ex. `register.add(new Account("Kim", 500.0));` och ett till.
4. Anropa `register.printAll();` — konsolen ska visa **båda** ägare och saldo tydligt.
5. **Ingen** `createAccount`. **Ingen** meny. `new Account(...)` får stå i `Main` vid `add`.
6. Efter `printAll`: skriv **två meningar** (i README eller kommentar) = **Exam README Q1** — inkapsling + peka `private balance`.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
import java.util.ArrayList;
import java.util.List;

public class AccountRegister {
    private List<Account> accounts = new ArrayList<>();

    public void add(Account account) {
        accounts.add(account);
    }

    public void printAll() {
        for (int i = 0; i < accounts.size(); i++) {
            Account a = accounts.get(i);
            System.out.println(a.getOwner() + ": " + a.getBalance());
        }
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        AccountRegister register = new AccountRegister();
        register.add(new Account("Kim", 500.0));
        register.add(new Account("Moa", 50.0));
        register.printAll();
    }
}
```

Konsol (ungefär):

```
Kim: 500.0
Moa: 50.0
```

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`List<Account>`** vs **`new ArrayList<>()`**  
- [ ] Peka på **`add`** — vad läggs i listan? (pekare till objekt)  
- [ ] Peka på **loopen** i `printAll` — varför `get(i)` och inte `println(accounts)`?  
- [ ] Minst **två** rader i konsolen med ägare + saldo  
- [ ] Exam Q1-skrivet: inkapsling + `private balance` pekat

**Ägarskap:** Muntligt: “listan bor i AccountRegister, inte som tre lösa variabler i Main.”

---

## Uppgift 3 — Stretch (valfritt)

Välj **en** (inom paketet — ingen factory/meny):

### A) README Q1 färdig
Skriv **2–4 meningar** på svenska i projektets `README.md` (fråga 1 från Examination 1): inkapsling, peka `private balance`, bakdörren om publikt.

### B) Transaktion via listan
Efter `printAll`, hämta första kontot (`accounts.get(0)` **inuti** `AccountRegister` i en ny metod, eller exponera säkert), kör `deposit(100)` och `printAll` igen — bevisa att saldo ändrats via **metod**, inte `=`.

**Klart-check:** Peka var `deposit` anropades — fortfarande **inte** `setBalance`.

---

## När du kört fast

1. *has private access in Account* → du står i `Main` — byt till getter eller flytta kod till `Account`. Ta **inte** bort `private`.  
2. *cannot find symbol: List* → `import java.util.List;`  
3. *cannot find symbol: ArrayList* → `import java.util.ArrayList;`  
4. *constructor Account cannot be applied* → du glömde argument till `new Account("Namn", saldo)`.  
5. Konsolen visar `Account@…` → använd getters, inte `println(konto)`.  
6. `withdraw` “slutat fungera” → kolla att den fortfarande är i `Account` och använder `this.balance` **inuti** klassen.  
7. Jämför med [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
8. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
