# 04 — AI-träning: Uttagsregel & ägarskap

AI kan spotta ur sig `deposit`/`withdraw` på sekunder. Det betyder inte att *du* äger stoppvillkoret eller vilket objekts `balance` som ändras. Här tränar du: **ignorerad saldo-koll** och **fel mutation** — ändra, förklara.

Det är inte magi. Det är `if` före minus + anrop på rätt objekt.

---

## Scenario — problem först

Du ber AI: *“Skriv Java Account med deposit och withdraw. Saldo 200. Testa uttag på 500.”*  
Du får tillbaka något i stil med:

```java
public class Account {
    String owner;
    double balance;

    public void deposit(double amount) {
        this.balance = this.balance + amount;
    }

    public void withdraw(double amount) {
        this.balance = this.balance - amount;
        if (amount > this.balance) {
            System.out.println("Uttag medges ej");
        }
    }
}
```

```java
// Main (utdrag)
Account nora = new Account();
nora.balance = 200.0;
nora.withdraw(500.0);
System.out.println(nora.balance);
```

Det *ser ut* som det finns en koll — men ordningen är fel. Svagheter:

- **Minus före `if`** — saldot är redan ändrat när du frågar; jämförelsen använder **fel** värde.  
- **Meddelande men ändå mutation** — Exam-regeln kräver **oförändrat** saldo vid stopp.  
- **Koll saknas helt** i andra AI-svar — alltid `balance - amount`.  
- **Fel objekt:** AI muterar `erik.balance` i `Main` medan anropet var `nora.withdraw` — eller sätter `nora.balance = …` *efter* metoden och saboterar regeln.  
- **`static` withdraw i `Main`** som tar `Account` som parameter “för enkelhet” — stryk om du tränar instansmetod.  
- **`private` / konstruktor / getters / `AccountRegister` / meny** AI lägger till “komplett bank” — stryk (utanför paketet).  
- **`boolean` utan meddelande** — returvärde räcker **inte** ensamt för Exam-kravet om konsolen ska visa varför det stoppades (meddelande + oförändrat saldo).

**Vad du tränar:** Feedback + en version *du* kan köra i IDE:n.  
**Varför:** Examination 1 — uttagsregeln. Du måste se när AI “nästan” har en `if` men muterar fel.  
**Vad det INTE är:** “AI fixade så det körde” utan att du kan peka på stoppgrenen.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt (eller jobba mot snutten ovan) där du ber om:
- klass `Account` med `owner`, `balance`;
- `deposit(amount)` och `withdraw(amount)` som **instansmetoder**;
- uttag större än saldo → **meddelande** och **oförändrat** saldo.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Subtraktion **före** villkoret?  
- [ ] Meddelande i `if` men **minus körs ändå** (fel gren / saknad `else`)?  
- [ ] Jämförelse mot **redan muterat** saldo?  
- [ ] `static` metod eller logik kvar bara i `Main`?  
- [ ] Fel objekts fält skrivs i `Main` efter anropet?  
- [ ] `private` / konstruktor / `AccountRegister` / meny du **inte** bett om?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Skriv en **ren version du äger** — koppla till [03 — Uppgift 2](./03-ovningar.md):

```java
public void withdraw(double amount) {
    if (amount > this.balance) {
        System.out.println("Uttag medges ej — beloppet är större än saldot.");
    } else {
        this.balance = this.balance - amount;
    }
}
```

Testa med saldo `200` och `withdraw(500)` — förväntat: meddelande, saldo kvar `200`. Spara i ditt projekt.

### Steg 4 — Andra AI-felet (fel mutation / fel objekt)
Be AI om två konton — eller använd denna medvetet trasiga variant:

```java
Account nora = new Account();
nora.owner = "Nora";
nora.balance = 200.0;

Account erik = new Account();
erik.owner = "Erik";
erik.balance = 80.0;

nora.withdraw(50.0);
erik.balance = erik.balance - 50.0;   // AI "synkade" fel konto manuellt
```

Skriv **minst en** FEEDBACK-rad om **fel mutation** (manuell `balance =` på fel objekt, eller bypass av metoden). Fixa så **bara** metodanrop ändrar saldo vid uttag/insättning i testet.

### Steg 5 — Reflektion (3 meningar)
1. Vilket regelbrott hade AI gjort (ordning, saknad `if`, mutation trots meddelande)?  
2. Vad ändrade du (peka på `if`-raden **och** var minus står)?  
3. Varför ska Exam 1:s `withdraw` kunna förklaras som “saldo oförändrat + meddelande” — inte bara “det finns en if någonstans”?

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade (inkl. balans-koll **eller** fel mutation)  
- [ ] Peka på **stoppgrenen** — ingen tilldelning till `balance`  
- [ ] Peka på **lyckad gren** — här får minus finnas  
- [ ] Peka på något du *tog bort* (static, private, register, manuell fel-mutation)  
- [ ] Programmet **kompilerar och kör** — för stort uttag lämnar samma saldo  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Ren `withdraw` (`void`):

```java
public void withdraw(double amount) {
    if (amount > this.balance) {
        System.out.println("Uttag medges ej — beloppet är större än saldot.");
    } else {
        this.balance = this.balance - amount;
    }
}
```

Alternativ med `boolean` (samma regel + svar till Main):

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

Typiska FEEDBACK-rader:

- `FEEDBACK: minus före if → flytta subtraktion till else; annars är saldot redan fel när du jämför.`  
- `FEEDBACK: println i if men balance minskar ändå → ta bort minus i stoppgrenen.`  
- `FEEDBACK: ingen koll alls → lägg amount > this.balance före mutation.`  
- `FEEDBACK: erik.balance = … efter nora.withdraw → stryk manuell mutation; anropa erik.withdraw om Erik ska ändras.`  
- `FEEDBACK: static withdraw i Main → flytta till Account som instansmetod.`  
- `FEEDBACK: AccountRegister/meny/private tillagt → stryk; paketet är deposit/withdraw på Account.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-utkast, rättar ordningen if → meddelande utan minus, och behåller bara kod jag kan förklara rad för rad.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
