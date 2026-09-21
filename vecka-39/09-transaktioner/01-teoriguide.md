# 01 — Teoriguide: Metoder på objekt — deposit och withdraw

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du har redan en klass `Account` med fält (`owner`, `balance`) och kan skapa objekt med `new`. Nu ska **objektet göra jobbet**: sätta in och ta ut — med en regel som stoppar omöjliga uttag. Det är inte magi. Det är instansmetoder + ett `if`.

**Förutsättning:** Du kan skapa ett `Account`, sätta fält och skriva ut dem (paketet [08-klasser-objekt](../08-klasser-objekt/)). Här: metoder **på** objektet. Ingen `private`, ingen konstruktor, inga getters, ingen registerlista, ingen meny.

---

## Problemet först — alltid minus, aldrig stopp

Många tänker: “Jag kan ju skriva `balance = balance - amount` i `main`.” Andas. Det funkar tills någon tar ut mer än som finns — då blir saldot **negativt** utan att någon stoppade.

**Dåligt läge** — uttag utan regel:

```java
Account nora = new Account();
nora.owner = "Nora";
nora.balance = 300.0;

double amount = 500.0;
nora.balance = nora.balance - amount;   // alltid minus
System.out.println(nora.balance);       // -200.0 — pengar skapades negativt
```

Koden **kör**. Men banken (och Exam 1) kräver: **för stort uttag → saldo oförändrat + meddelande**. Logiken hör hemma i en metod på kontot — så varje anrop följer samma regel.

---

## Metod på objekt — jobbet ligger i `Account`

**Metafor:** En **kassalåda med knapp**. Du trycker “sätt in 50” på *den* lådan — inte på en annan. Knappen finns på lådan; du anropar den från `Main`.

**Vad det är:** En **instansmetod** = metod **utan** `static`, inuti klassen `Account`. Du anropar med `objekt.metod(...)`.  
**Varför den finns:** Ändring av saldo ska alltid gå via samma regel — på rätt objekt.  
**Om den saknas / vad den INTE är:** INTE samma sak som `static`-metoder i `Main` (tidigare paket). INTE `nora.balance = nora.balance + 50` utspridd överallt. INTE en meny. INTE `AccountRegister`.

```java
public class Account {
    String owner;
    double balance;

    public void deposit(double amount) {
        this.balance = this.balance + amount;
    }
}
```

```java
// I Main:
Account nora = new Account();
nora.owner = "Nora";
nora.balance = 300.0;
nora.deposit(50.0);   // Noras saldo blir 350.0
```

**Målsvar (säg högt / skriv i README):**  
*“deposit och withdraw bor i Account. Jag anropar med objekt.metod(belopp). Det är det objektets balance som ändras.”*

---

## `deposit(amount)` — öka saldot

**Vad det är:** Metod som tar ett belopp (`amount`) och **lägger till** det på objektets `balance`.  
**Varför den finns:** Insättning ska vara ett tydligt anrop — inte manuell `+` på fältet från tio ställen.  
**Om den saknas / vad den INTE är:** INTE uttag. INTE utskrift (kan vara `void`). INTE `static`.

```java
public void deposit(double amount) {
    this.balance = this.balance + amount;
}
```

Efter `nora.deposit(50.0)` är Noras `balance` högre. Eriks konto rörs **inte** — anropet gick till `nora`.

---

## `this` — kort

**Metafor:** **“Den här lådan.”** När du trycker knappen på Noras kassa menar `this` Noras fält — inte Eriks.

**Vad det är:** `this` = **det objekt som fick anropet**. `this.balance` = saldot hos just det objektet.  
**Varför det finns:** Inuti metoden ska du tydligt säga “fältet på *det här* objektet”, särskilt när parametern heter något annat (`amount`).  
**Om det saknas / vad det INTE är:** INTE en ny typ. INTE magi. Utan `this` kan `balance` ofta fungera ändå — men `this.balance` gör ägarskapet synligt. `this` är **inte** parametern `amount`.

```java
public void deposit(double amount) {
    this.balance = this.balance + amount;
    // this.balance = objektets fält
    // amount       = värdet som skickades in i anropet
}
```

**Målsvar (säg högt / skriv i README) — this:**  
*“this.balance är saldot hos objektet som fick anropet. amount är beloppet som skickades in.”*

---

## `withdraw(amount)` — minska *bara om* det går

**Vad det är:** Metod som tar ett belopp och **minskar** `balance` **endast** när beloppet inte är större än saldot. Annars: **meddelande** + **oförändrat saldo**.  
**Varför den finns:** Exam 1 (Kontoappen) kräver stoppat uttag — saldo får inte bli negativt “i smyg”.  
**Om den saknas / vad den INTE är:** INTE “alltid minus”. INTE `private`/konstruktor (kommer senare). INTE krav på `boolean` i basen — men `boolean`-retur är OK som tydligt mönster (se stretch).

### Problem först — alltid subtract

```java
public void withdraw(double amount) {
    this.balance = this.balance - amount;  // FEL mot regeln — ingen koll
}
```

Med saldo `300` och `withdraw(500)` blir saldot `-200`. **Regeln saknas.**

### Lösning — villkor före minus

```java
public void withdraw(double amount) {
    if (amount > this.balance) {
        System.out.println("Uttag medges ej — beloppet är större än saldot.");
        // balance lämnas orörd
    } else {
        this.balance = this.balance - amount;
    }
}
```

| Anrop | Saldo före | Vad händer | Saldo efter |
|-------|------------|------------|-------------|
| `withdraw(100)` | 300 | minus | 200 |
| `withdraw(500)` | 300 | meddelande, **ingen** minus | 300 |

**Målsvar (säg högt / skriv i README) — uttagsregeln:**  
*“Om beloppet är större än saldot ska withdraw inte ändra balance. Den ska skriva ett tydligt meddelande. Saldo oförändrat + meddelande.”*

---

## Anropa från `Main` — objektet först

```java
public class Main {
    public static void main(String[] args) {
        Account nora = new Account();
        nora.owner = "Nora";
        nora.balance = 300.0;

        nora.deposit(50.0);
        System.out.println("Efter insättning: " + nora.balance);  // 350.0

        nora.withdraw(100.0);
        System.out.println("Efter uttag: " + nora.balance);       // 250.0

        nora.withdraw(999.0);
        System.out.println("Efter stoppat uttag: " + nora.balance); // fortfarande 250.0
    }
}
```

**Kom ihåg / INTE:** `Account.deposit(50)` (static-tänk) — du behöver **ett objekt**. Du skriver **inte** en full meny här. Du skapar **inte** `AccountRegister`.

---

## Valfritt mönster — `boolean withdraw` (inom samma regel)

Exam-kravet är **saldo oförändrat + meddelande**. Många lösningar returnerar också `true`/`false` så `Main` kan styra nästa steg:

```java
public boolean withdraw(double amount) {
    if (amount > this.balance) {
        System.out.println("Uttag medges ej — beloppet är större än saldot.");
        return false;
    }
    this.balance = this.balance - amount;
    return true;
}
```

```java
if (nora.withdraw(100.0)) {
    System.out.println("Uttag beviljat.");
} else {
    System.out.println("Uttag stoppat.");
}
```

**Vad det INTE är:** Krav att du *måste* ha `boolean` i basövningarna — men det är samma uttagsregel, plus ett svar till anroparen. `void` + meddelande räcker för Exam-regeln; `boolean` är modern tydlighet.

---

## Valfritt — `printInfo()` (samlad utskrift)

```java
public void printInfo() {
    System.out.println("Ägare: " + this.owner + "  Saldo: " + this.balance);
}
```

Anropa `nora.printInfo();` — samma idé: metoden hör till objektet. Inte obligatoriskt för uttagsregeln, men bra träning.

---

## Metod — när du tvekar

1. **Hör jobbet till kontot?** → Metod i `Account`, anropa med `objekt.metod(...)`.  
2. **Insättning?** → `deposit(amount)` — öka `this.balance`.  
3. **Uttag?** → Fråga först: `amount > this.balance`? Ja → meddelande, **ingen** minus. Nej → minus.  
4. **`this`:** fältet på *det* objektet. **`amount`:** parametern.  
5. **Bevisa:** skriv ut saldo före och efter ett för stort uttag — samma tal.

**Målsvar (säg högt / skriv i README) — metod:**  
*“Objektet gör jobbet. deposit ökar. withdraw stoppar för stora belopp: meddelande och oförändrat saldo.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Alltid `balance - amount` utan `if` | Först fråga — sedan eventuellt minus |
| Meddelande men **ändå** minus | Stoppet måste **hoppa över** tilldelningen |
| `static void deposit` i `Main` | Flytta till `Account` — anropa på objektet |
| Ändrar fel objekts saldo | Kolla vilket namn som står före punkten (`nora.` vs `erik.`) |
| `private` / konstruktor / getters “för säkerhets skull” | Kommer i senare paket — håll fälten enkla här |
| Meny + `AccountRegister` + factory | Utanför det här paketet |
| Tror att `this` är parametern | `this.balance` = fält; `amount` = inskickat belopp |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Varför “alltid minus” bryter uttagsregeln.  
2. Skillnad `nora.deposit(50)` vs `nora.balance = nora.balance + 50` utspridd i `main` (samma effekt idag — men **var** hör regeln hemma?).  
3. Vad `this.balance` betyder vid anropet `nora.withdraw(20)`.  
4. Vad du ska **se** i konsolen och i `balance` efter ett för stort uttag.

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
