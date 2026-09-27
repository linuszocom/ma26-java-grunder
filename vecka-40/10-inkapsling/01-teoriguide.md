# 01 — Teoriguide: Inkapsling, konstruktor och registerlista

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du har redan `Account` med `deposit` och `withdraw` — metoder som följer uttagsregeln. Fälten har varit **öppna**: `Main` kunde skriva `nora.balance = -99999` utan att javac protesterade. Nu låser du **bankvalvet**, fyller konton via **konstruktorn**, läser genom **getters**, och samlar flera konton i **`AccountRegister`**. Det är inte magi. Det är `private`, `this` i konstruktorn, och `List<Account>`.

**Förutsättning:** Du kan skapa `Account`, anropa `deposit` / `withdraw` och förklara uttagsregeln ([09-transaktioner](../../vecka-39/09-transaktioner/)). Här: **låsa**, **föda** objekt korrekt, **läsa** utifrån, **samla** i register. Ingen factory, ingen meny, inget arv.

---

## Problemet först — bakdörren till saldot

Många tänker: “Jag använder ju `deposit` och `withdraw` — varför bry sig om `private`?” Andas. Så länge fälten är synliga kan **någon rad i `Main`** fortfarande göra det värsta:

```java
Account kim = new Account();
kim.owner = "Kim";
kim.balance = 1000.0;

kim.balance = -99999;   // javac säger inget — banken är ruin
System.out.println(kim.balance);
```

Koden **kompilerar och kör**. Men Examination 1 kräver att du **förstår varför** det är farligt — och att du **pekar på `private`** i README. Lösningen: state sitter **inuti** objektet; utifrån går du bara via **tillåtna dörrar** (getters och affärsmetoder).

---

## Inkapsling — bankvalv med låsta fack

**Metafor:** Ett **bankvalv** med **låsta fack** för `owner` och `balance`. Du som står i foajén (`Main`) får inte sticka in handen i facket. Du visar **legitimation vid luckan** (getter) eller använder **kassörens rutiner** (`deposit` / `withdraw`).

**Vad det är:** **Inkapsling** = objektets data (`owner`, `balance`) är **dolda** (`private`) och nås utifrån via **kontrollerade metoder**.  
**Varför den finns:** Samma regler för alla anropare. Ingen “snabb rad” i `Main` som saboterar saldot.  
**Om den saknas / vad den INTE är:** INTE att fälten försvinner — de finns kvar **inuti** `Account.java`. INTE `setBalance` (det är samma bakdörr med ett finare namn). INTE factory eller meny (kommer i andra paket). INTE arv.

**Målsvar (säg högt / skriv i README — Exam Q1):**  
*“Inkapsling betyder att owner och balance är private. Main läser med getOwner och getBalance och ändrar med deposit och withdraw. Publikt fält hade låtit Main skriva balance = -99999 — det pekar jag på som bakdörren.”*

---

## `private` — lås på facket

**Vad det är:** Nyckelordet `private` framför fältet = **bara kod inuti samma klass** (`Account.java`) får läsa/skriva fältet direkt.  
**Varför det finns:** `Main.java` är en **annan fil**. Utan `private` såg `Main` fälten — med `private` stoppar **javac** innan programmet körs.  
**Om det saknas / vad det INTE är:** INTE `static`. INTE samma sak som “hemlig metod” — det gäller **fält**. INTE att `deposit` slutar fungera — metoder **inuti** `Account` ser fortfarande `balance`.

```java
public class Account {
    private String owner;
    private double balance;

    // deposit, withdraw, getters — här inne
}
```

| Var du står | Ser `owner` / `balance` direkt? |
|-------------|----------------------------------|
| Inuti `Account.java` | Ja — `deposit`, `withdraw`, konstruktor |
| `Main.java` | Nej — `has private access in Account` |

---

## Kompileringsfelet du ska kunna läsa — `has private access`

**Metafor:** Du försöker öppna valvfacket med skruvmejsel från gatan. Vakten (`javac`) stoppar dig **innan** banken öppnar.

```java
// Main.java — efter private
System.out.println(kim.owner);
kim.balance = 500.0;
```

**Konsol / javac (ungefär):**

```
error: owner has private access in Account
error: balance has private access in Account
```

**Vad det INTE är:** Inte `Exception` vid körning. Inte “JDK trasigt”. Det är **avsiktligt** — valvlåset fungerar.

**Metodregel:** Ta **inte** bort `private` för att felet ska försvinna. Byt till **getter** (läsa) eller **deposit/withdraw** (ändra).

---

## Getters — `getOwner()` och `getBalance()`

**Metafor:** **Nyckelkort vid luckan** — du får **titta** på värdet, inte flytta in möbler i facket från foajén.

**Vad det är:** Publika metoder utan parametrar som **returnerar** en kopia av värdet (för `String` / `double`). Exam 1 **låser namnen** `getOwner` och `getBalance`.  
**Varför de finns:** `Main` ska kunna **skriva ut** ägare och saldo utan att nå fältet direkt.  
**Om de saknas / vad de INTE är:** INTE `printInfo` (den skriver — getters **returnerar**). INTE setters. INTE att `Main` får ändra saldo — bara **läsa**.

```java
public String getOwner() {
    return owner;
}

public double getBalance() {
    return balance;
}
```

```java
// Main.java — tillåtet
System.out.println(kim.getOwner());
System.out.println(kim.getBalance());
kim.deposit(200.0);
System.out.println(kim.getBalance());   // 1200.0 om start var 1000
```

**Målsvar (säg högt / skriv i README):**  
*“getOwner och getBalance är dörrarna för att läsa. Jag anropar kim.getBalance(), inte kim.balance.”*

---

## `deposit` / `withdraw` inuti valvet — låset gäller utåt

**Vad det är:** Metoder i `Account` **ser** `private`-fält eftersom de står **inuti samma klass**.  
**Varför det spelar roll:** Du behöver **inte** getters **inuti** `withdraw` — du skriver `this.balance` direkt.  
**Om det saknas / vad det INTE är:** INTE att `private` “stänger av” klassen för sig själv.

```java
public void withdraw(double amount) {
    if (amount > this.balance) {
        System.out.println("Uttag medges ej — beloppet är större än saldot.");
    } else {
        this.balance = this.balance - amount;
    }
}
```

**Kom ihåg / INTE:** Utifrån (`Main`) = getters + transaktionsmetoder. Inuti (`Account`) = direkt access till fält OK.

---

## Ingen `setBalance` — samma hål, annat skylt

**Problem först:** AI (och stress) föreslår gärna:

```java
public void setBalance(double x) {
    balance = x;
}
kim.setBalance(-99999);   // javac nöjd — banken ruin
```

**Vad det INTE är:** Inte inkapsling i praktiken. Det är **publikt fält i förklädnad**.

**Metodregel:** Exam 1 kräver getters — **inte** setters på saldo. **Ändra** via `deposit` / `withdraw` som redan har regler.

---

## Cliff efter lås — hur fylls facket första gången?

Efter `private` fungerar **inte** längre:

```java
Account kim = new Account();
kim.owner = "Kim";      // has private access
kim.balance = 1000.0;   // has private access
```

**Vad som saknas:** Ett sätt att sätta startvärden **inifrån** klassen när objektet föds. Det är **konstruktorn**.

---

## Konstruktor — registrering vid kontots födelse

**Metafor:** När ett konto **öppnas** i banken fyller kassören **låsta fack** direkt — ägare och startsaldo — innan kunden lämnar diskens båda sidor.

**Vad det är:** En **specialmetod** med **samma namn som klassen**, **ingen returtyp** (inte ens `void`). Java kör den automatiskt vid `new Account(...)`.  
**Varför den finns:** Efter `private` måste **Account själv** sätta fälten vid skapande.  
**Om den saknas / vad den INTE är:** INTE `createAccount` i register (factory = Pass 2). INTE en metod du anropar med `kim.Account(...)`. INTE `void Account(...)` — javac vägrar.

```java
public Account(String owner, double initialBalance) {
    this.owner = owner;
    this.balance = initialBalance;
}
```

```java
// Main.java
Account kim = new Account("Kim", 1000.0);
System.out.println(kim.getOwner());    // Kim
System.out.println(kim.getBalance());    // 1000.0
```

**Målsvar (säg högt / skriv i README):**  
*“new Account("Kim", 1000) kör konstruktorn. this.owner och this.balance fylls innan kim pekar klart. Main sätter inte fält direkt.”*

---

## `this` i konstruktorn — vilket fack menar du?

**Metafor:** **`this`** = **det här kontot** som just öppnas. Vänster sida = facket i valvet. Höger sida = pappret du skickade in (`"Kim"`, `1000`).

**Vad det är:** `this.owner = owner` — vänster `owner` är **fältet**, höger `owner` är **parametern**.  
**Varför det finns:** Parametern och fältet kan ha **samma namn**. Utan `this` blir `owner = owner` meningslöst (parametern till sig själv).  
**Om det saknas / vad det INTE är:** INTE samma `this` som i `deposit` — samma **idé**, annat tillfälle (födelse vs transaktion).

```java
public Account(String owner, double initialBalance) {
    this.owner = owner;           // fält ← parameter
    this.balance = initialBalance;
}
```

---

## Default-konstruktor försvinner

**Vad det är:** I [08-klasser-objekt](../../vecka-39/08-klasser-objekt/) funkade `new Account()` utan argument — Java gav en **osynlig tom** konstruktor.  
**Varför det ändras:** När **du** skriver en egen konstruktor med parametrar **försvinner** den tomma.  
**Vad du ska se:**

```java
Account kim = new Account();   // FEL efter er konstruktor
```

```
error: constructor Account cannot be applied to given types
  required: String, double
  found:    no arguments
```

**Metodregel:** Exam kräver konstruktor med `owner` + startsaldo — använd `new Account("Kim", 1000)`.

---

## `AccountRegister` — valvbok med flera konton

**Metafor:** En **valvbok** (register) med **rad numrerade fack** — varje fack håller en **nyckel** till ett `Account` på heapen, inte en kopia av hela kontot.

**Vad det är:** Klassen `AccountRegister` äger **`List<Account>`** — listan av alla konton.  
**Varför den finns:** Examination 1 har **tre filer** — `Main` ska inte hålla tre lösa variabler (`kim`, `moa`, `sam`). Samlingen bor i registret.  
**Om den saknas / vad den INTE är:** INTE factory än (`createAccount` = Pass 2). INTE meny. INTE att listan **måste** vara publik — den är `private` i registret.

### Kodstandard — `List`, inte `ArrayList` som typ

```java
import java.util.ArrayList;
import java.util.List;

public class AccountRegister {
    private List<Account> accounts = new ArrayList<>();
}
```

**Varför:** Variabeln är deklarerad som **`List`** (interface). **`ArrayList`** används bara vid **`new`**. Samma mönster som i [06-arraylist-scanner](../../vecka-38/06-arraylist-scanner/) — modern Java.

---

## `add` — lägg nyckel i nästa fack

**Vad det är:** Metod som tar ett färdigt `Account` och lägger det i listan.  
**Varför idag:** Factory flyttar `new` senare — **nu** får `new Account(...)` stå i `Main` (eller i `add`-anropet).  
**Om det saknas / vad det INTE är:** INTE `createAccount(String, int)` än.

```java
public void add(Account account) {
    accounts.add(account);
}
```

```java
// Main.java
AccountRegister register = new AccountRegister();
register.add(new Account("Kim", 500.0));
register.add(new Account("Moa", 50.0));
```

Efter två `add`: `accounts.size()` är 2.

---

## `printAll` — loopa valvboken

**Vad det är:** Loop från `0` till `accounts.size() - 1`, hämta varje konto, skriv ut via getter eller `printInfo`.  
**Varför den finns:** Du ska **se** alla konton — inte `println(listan)` som ger adresser.

```java
public void printAll() {
    for (int i = 0; i < accounts.size(); i++) {
        Account a = accounts.get(i);
        System.out.println(a.getOwner() + ": " + a.getBalance());
    }
}
```

**Kom ihåg / INTE:** `System.out.println(accounts.get(0))` skriver **`Account@7a81197d`** — hex-adress, inte “Kim”. Använd **getter** eller metod på objektet.

**Målsvar (säg högt / skriv i README):**  
*“AccountRegister har List<Account>. Jag add:ar new Account(...) och printAll loopar get(i) och skriver getOwner/getBalance.”*

---

## Tre filer — vem äger vad?

| Fil | Ansvar |
|-----|--------|
| `Account.java` | Ett konto: private fält, konstruktor, getters, deposit/withdraw |
| `AccountRegister.java` | Listan, add, printAll |
| `Main.java` | Skapar register, lägger till konton, anropar printAll |

**Main orkestrerar.** Registret **äger** listan. Kontot **äger** sitt saldo.

---

## Exam README fråga 1 — träna redan nu

I Examination 1 ska README svara (svenska, egna ord):

1. Vad är **inkapsling**?  
2. Peka på **`private balance`** (eller `owner`).  
3. Vad hade hänt om fältet varit **publikt**?

**Facit-nivå (kort):** Inkapsling = data dold, access via metoder. Publikt = `Main` kunde skriva negativt saldo direkt. `private` + getters + deposit/withdraw = kontrollerade dörrar.

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Tar bort `private` när Main blir röd | Valvlåset ska stå — byt till getter |
| `setBalance` “för enkelhet” | Samma bakdörr — stryk |
| Getter i `Main` som `static` | Flytta till `Account` |
| `ArrayList<Account> accounts` som deklaration | Skriv `List<Account> accounts = new ArrayList<>()` |
| `println(accounts.get(0))` för att lista | Anropa getOwner/getBalance |
| Glömmer `import java.util.ArrayList` / `List` | Samma som v2-listor |
| `new Account()` efter egen konstruktor | Skicka owner + startsaldo |
| `createAccount` / meny / arv “för att vara klar” | Utanför det här paketet |
| Tror `private` stoppar `withdraw` inuti Account | Bara **andra filer** stoppas |

---

## Metod — när du tvekar

1. **Läsa utifrån?** → `getOwner()` / `getBalance()`.  
2. **Ändra saldo utifrån?** → `deposit` / `withdraw` — inte `=`.  
3. **Skapa konto?** → `new Account("Namn", saldo)` — konstruktor fyller fack.  
4. **Flera konton?** → `AccountRegister`, `add`, `printAll`.  
5. **Rött i Main på `.owner`?** → Läs `has private access` — det är valvet som fungerar.  
6. **Exam Q1?** → Peka `private balance`, förklara bakdörren.

**Målsvar (säg högt / skriv i README) — helhet:**  
*“Private låser fälten. Konstruktor fyller vid new. Getters läser. Register samlar List<Account>. Factory och meny kommer senare.”*

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Skillnad `kim.balance` vs `kim.getBalance()` efter `private`.  
2. Varför `this.owner = owner` i konstruktorn.  
3. Vad `has private access in Account` betyder — och vad du **inte** ska göra.  
4. Varför `List<Account>` deklareras men `new ArrayList<>()` skapas.  
5. Två meningar Exam README Q1 med pekning på `private balance`.

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
