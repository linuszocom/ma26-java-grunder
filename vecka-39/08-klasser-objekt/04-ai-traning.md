# 04 — AI-träning: Klass vs objekt & ägarskap

AI kan spotta ur sig en “Account-klass” på sekunder. Det betyder inte att *du* äger skillnaden klass/objekt eller filnamnsregeln. Här tränar du: **blandad klass/objekt**, **fel filnamn**, **glömt `new`** — ändra, förklara.

Det är inte magi. Det är rätt fil + `new` + fält via punkt.

---

## Scenario — problem först

Du ber AI: *“Skriv Java med en Account-klass som har owner och balance. Skapa ett konto för Alex med 500 i saldo och skriv ut fälten.”*  
Du får tillbaka något i stil med:

```java
// AI la allt i Main.java och döpte filen till account.java i chatten
public class Main {
    public static void main(String[] args) {
        Account alex = new Account();
        // AI blandar ihop: "klassen Alex har saldo 500"
        alex.owner = "Alex";
        System.out.println(alex);  // skriver ut objektet, inte fälten
    }
}

public class account {   // fel: litet a, och två public classes i samma fil
    String owner;
    double balance;
}
```

Det *ser ut* som OOP — men det är trasigt eller förvirrande. Svagheter:

- **Klass vs objekt blandas i förklaringen** — AI säger “klassen Alex” när `alex` är **objektet**. Klassen heter `Account`.  
- **Fel filnamn:** `account.java` / `Accounts.java` / allt klistrat i `Main.java` med två `public class`.  
- **`println(alex)`** i stället för `alex.owner` / `alex.balance`.  
- **Glömt `new`:** `Account alex; alex.owner = "Alex";` → `NullPointerException`.  
- **Spill:** AI lägger till `deposit`, `private`, konstruktor, `ArrayList<Account>` “för Exam 1” — **stryk** i det här paketet.  
- **Svenska namn:** `class Konto` — hör inte hemma i Exam 1.

**Vad du tränar:** Feedback + en version *du* kan köra i IDE:n med **två filer**.  
**Varför:** Examination 1 kräver `Account.java` — du måste se när AI blandar mall och instans.  
**Vad det INTE är:** “AI fixade så det körde” utan att du kan peka på klassfilen och `new`.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt (eller jobba mot snutten ovan) där du ber om:
- separat fil **`Account.java`** med `public class Account` och fälten `owner` + `balance`;
- i **`Main`**: `new`, sätt fält, skriv ut **fälten**.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] AI kallar **objektet** för “klassen”?  
- [ ] Filnamn ≠ `Account.java`?  
- [ ] Två `public class` i **samma** fil?  
- [ ] Saknas **`new`** före punkt?  
- [ ] `println(objekt)` utan fält?  
- [ ] `deposit` / `private` / konstruktor / lista som du **inte** bett om?  
- [ ] Svenska klassnamn (`Konto`)?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Skriv en **ren version du äger** — koppla gärna till [03 — Uppgift 1](./03-ovningar.md):

```java
// Account.java
public class Account {
    String owner;
    double balance;
}
```

```java
// Main.java
public class Main {
    public static void main(String[] args) {
        Account card = new Account();
        card.owner = "Alex";
        card.balance = 500.0;
        System.out.println(card.owner);
        System.out.println(card.balance);
    }
}
```

Spara i ditt Java-projekt. **Två filer.** Inga metoder på `Account` än.

### Steg 4 — Andra AI-felet (filnamn / NPE)
Be AI igen — eller använd denna medvetet trasiga variant:

```java
Account card;
card.owner = "Sam";
card.balance = 100.0;
```

Skriv **minst en** FEEDBACK-rad om **saknad `new`** (eller om AI sparade klassen som `account.java`). Fixa så det kompilerar och kör.

### Steg 5 — Reflektion (3 meningar)
1. Hur blandade AI ihop **klass** och **objekt** (eller filnamn)?  
2. Vad ändrade du (peka på **fil** **och** `new`)?  
3. Varför måste Exam 1 ha en fil som heter exakt `Account.java` — inte “nästan rätt”?

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade (inkl. klass/objekt **eller** filnamn **eller** `new`)  
- [ ] Peka på **`public class Account`** i rätt fil  
- [ ] Peka på **`new Account()`** och fält-tilldelning  
- [ ] Peka på något du *tog bort* (deposit, private, lista, fel `println`)  
- [ ] Programmet **kompilerar och kör** — ägare och saldo syns  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Ren minimiversion: se Steg 3 ovan. Konsol: `Alex` och `500.0`.

Typiska FEEDBACK-rader:

- `FEEDBACK: AI sa "klassen Alex" → Alex är objektet; klassen heter Account.`  
- `FEEDBACK: filen account.java / Konto.java → döp till Account.java med public class Account.`  
- `FEEDBACK: två public class i Main.java → flytta Account till egen fil.`  
- `FEEDBACK: Account card; utan new → card = new Account(); innan punkt.`  
- `FEEDBACK: println(card) → skriv card.owner och card.balance.`  
- `FEEDBACK: deposit/private/konstruktor tillagt → stryk; paketet är bara fält + new.`  
- `FEEDBACK: ArrayList<Account> → stryk; ett eller två objekt med egna variabler räcker.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-utkast, rättar filnamn och new, och behåller bara kod där jag kan peka: här är klassen, här är objektet, här är fälten.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
