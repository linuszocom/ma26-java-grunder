# 03 — Övningar

**Omfång det här paketet:** Instansmetoder på `Account`: `deposit(amount)`, `withdraw(amount)`. Fält `owner`, `balance`. Kort `this`. Uttagsregel: för stort belopp → **saldo oförändrat** + tydligt meddelande. Minimal skelett utan `private`, konstruktor, getters. Ingen `AccountRegister`, ingen meny, ingen `Scanner` krävs (hårdkodade anrop).

AI får föreslå rader. Du måste kunna **peka och förklara** metoderna, `this`, och varför stoppat uttag inte ändrar saldot.

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK. Filerna `Account.java` och `Main.java`. Kör `Main` och läs **konsolen**.

**Bygger på:** `Account` från [08-klasser-objekt](../08-klasser-objekt/). Saknar du filen — använd skelettet i uppgift 1.

---

## Uppgift 1 — `deposit` funkar (bygg vidare på Account)

**Mål:** Lägga `deposit` på objektet och visa att saldot ökar efter anrop.

**Scenario / startläge:** Kaféet “BryggBar” har lojalitetssaldo per gäst. Nora har 300.0 poäng. Du ska sätta in 50 via metod — inte bara skriva `balance = …` i `main` varje gång.

**Minimal skelett** (om du startar här — kopiera till `Account.java` / `Main.java`):

```java
// Account.java
public class Account {
    String owner;
    double balance;

    // deposit ska hit
}

// Main.java
public class Main {
    public static void main(String[] args) {
        Account nora = new Account();
        nora.owner = "Nora";
        nora.balance = 300.0;

        // anropa deposit här
        System.out.println(nora.owner + ": " + nora.balance);
    }
}
```

**Krav:**
1. I `Account`: `public void deposit(double amount)` som gör `this.balance = this.balance + amount`.
2. I `Main`: anropa `nora.deposit(50.0)`.
3. Skriv ut saldo **före** och **efter** (eller minst efter) — du ska se `350.0`.
4. Metoden ska ligga i `Account`, **utan** `static`.
5. Ingen `private`, ingen konstruktor, inga getters.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

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
public class Main {
    public static void main(String[] args) {
        Account nora = new Account();
        nora.owner = "Nora";
        nora.balance = 300.0;

        System.out.println("Före: " + nora.balance);
        nora.deposit(50.0);
        System.out.println("Efter: " + nora.balance);
    }
}
```

Konsol: `Före: 300.0` sedan `Efter: 350.0`.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **metodhuvudet** `deposit` — ingen `static`  
- [ ] Peka på **`this.balance`** — säg vad `this` är vid anropet `nora.deposit(50)`  
- [ ] Peka på **anropet** i `Main` — objekt före punkt  
- [ ] Konsolen visar ökat saldo — programmet kompilerar

**Ägarskap:** AI ok som bollplank — du ska kunna förklara varför metoden hör till `Account`.

---

## Uppgift 2 — Problem först: uttag som alltid subtraherar

**Mål:** Känna smärtan när uttag **inte** stoppas — sedan laga med villkor.

**Scenario:** Samma Nora, saldo `300.0`. Någon har skrivit en `withdraw` som **alltid** drar bort beloppet. Du ska först **köra** den trasiga versionen, sedan **laga** den.

**Trasig startkod** (lägg i `Account` — kör och se negativt saldo):

```java
public void withdraw(double amount) {
    this.balance = this.balance - amount;  // alltid minus — fel mot regeln
}
```

I `Main` (efter att Nora har t.ex. 300.0):

```java
nora.withdraw(500.0);
System.out.println("Saldo efter stort uttag: " + nora.balance);
```

**Vad du ska se (problem):** saldot blir negativt (t.ex. `-200.0`). Det är **beteendet du ska döda**.

**Krav (lagningen):**
1. Byt ut kroppen så att: om `amount > this.balance` → skriv ett tydligt meddelande på svenska (t.ex. `"Uttag medges ej — beloppet är större än saldot."`) och **lämna** `balance` orörd.
2. Annars: `this.balance = this.balance - amount`.
3. Testa minst tre fall i `Main` (hårdkodat räcker):
   - lyckat uttag (t.ex. `100` när saldo ≥ 100) — saldo minskar  
   - för stort uttag (t.ex. `999`) — meddelande + **samma** saldo som före anropet  
   - gärna ett `deposit` före/efter så du ser att insättning fortfarande funkar  
4. Returtyp `void` räcker här (boolean = stretch i uppgift 4).

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public void withdraw(double amount) {
    if (amount > this.balance) {
        System.out.println("Uttag medges ej — beloppet är större än saldot.");
    } else {
        this.balance = this.balance - amount;
    }
}
```

Exempelkörning med start `300`:
- `withdraw(100)` → saldo `200`
- `withdraw(500)` → meddelande, saldo fortfarande `200`

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`if (amount > this.balance)`** — varför **före** minus?  
- [ ] Peka på grenen där **ingen** tilldelning till `balance` sker  
- [ ] Visa i konsolen: samma saldo före/efter för stort uttag  
- [ ] Säg Exam-kopplingen högt: *“saldo oförändrat + meddelande”*

**Ägarskap:** Du ska kunna förklara skillnaden mellan “kompilerar” och “följer uttagsregeln”.

---

## Uppgift 3 — Två objekt: rätt konto får anropet

**Mål:** Bevisa att anropet väljer objekt — Eriks saldo rörs inte när Nora tar ut.

**Brief:** Nora startar på `400.0`, Erik på `150.0`. Gör `nora.deposit(50)`, `nora.withdraw(100)`, och ett **stoppat** `nora.withdraw(999)`. Skriv ut båda saldona efteråt.

**Krav:**
1. Två `Account`-objekt (`nora`, `erik`) med olika `owner` / `balance`.
2. Alla ändringar via `deposit` / `withdraw` — inte `nora.balance = …` för själva transaktionerna (startvärden får du sätta på fälten).
3. Efter stoppat uttag: Noras saldo oförändrat jämfört med strax före det anropet; Eriks saldo **identiskt** med start (om du inte anropat Erik).
4. Utskrift som gör det synligt (två rader räcker).

**Klart-check (peka i DIN kod):**
- [ ] Peka på **vilket namn** som står före `.withdraw` vid stoppet  
- [ ] Förklara **varför** Erik inte ändrades  
- [ ] Peka på `this` i metoden — vilket objekt är `this` när anropet är `nora.withdraw(...)`?

**Ägarskap:** Muntligt: “punkten väljer objektet.”

---

## Uppgift 4 — Stretch (valfritt)

Välj **en eller båda** (inom kursens VAD — ingen inkapsling, ingen meny):

### A) `printInfo()`
`public void printInfo()` som skriver ägare + saldo (gärna med `this.owner` / `this.balance`). Anropa på båda objekten.

### B) `boolean withdraw`
Byt till `public boolean withdraw(double amount)`:
- för stort → meddelande, **return false**, saldo orört  
- lyckat → minus, **return true**  

I `Main`: `if (nora.withdraw(100.0)) { … } else { … }`.

**Klart-check:** Peka på alla `return`-vägar — varje väg ger en `boolean`. Bekräfta att Exam-regeln fortfarande håller (meddelande + oförändrat saldo).

---

## När du kört fast

1. *cannot find symbol: method deposit* → metoden saknas i `Account`, eller stavfel, eller du anropar på fel typ.  
2. *non-static method cannot be referenced from a static context* → du skrev `Account.deposit(...)` — använd `nora.deposit(...)`.  
3. Saldo blir negativt → `if` saknas eller minus står **utanför**/före villkoret.  
4. Meddelande syns men saldot ändras ändå → du subtraherar **också** i stoppgrenen — ta bort den raden.  
5. Jämför med [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
6. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
