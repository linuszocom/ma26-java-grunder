# 04 — AI-träning: Valv, setters och register-spill

AI kan spotta ur sig “komplett bankapp” på sekunder — med **publika fält igen**, **`setBalance`**, **`createAccount`**, meny och `ArrayList` som typ överallt. Det betyder inte att *du* äger inkapslingen eller Exam README Q1. Här tränar du: **stryk spill**, **behåll valvlåset**, **List inte ArrayList** som deklaration.

Det är inte magi. Det är `private` + getters + konstruktor + registerlista — inget mer i det här paketet.

---

## Scenario — problem först

Du ber AI: *“Gör Account och AccountRegister enligt Exam 1.”*  
Du får tillbaka något i stil med:

```java
public class Account {
    public String owner;
    public double balance;

    public void setBalance(double x) {
        balance = x;
    }

    public Account() { }

    public void deposit(double amount) {
        balance += amount;
    }
}
```

```java
public class AccountRegister {
    public ArrayList<Account> accounts = new ArrayList<>();

    public Account createAccount(String owner, double start) {
        Account a = new Account();
        a.owner = owner;
        a.balance = start;
        accounts.add(a);
        return a;
    }
}
```

```java
// Main — utdrag
Scanner sc = new Scanner(System.in);
while (true) {
    System.out.println("1. Skapa 2. Lista …");
}
```

Svagheter:

- **Publika fält** — inkapsling borta; Exam Q1 omöjlig att svara ärligt.  
- **`setBalance`** — bakdörr; `Main` kan skriva `-99999` igen.  
- **Tom konstruktor + fält utifrån** — mönster från v3, inte v4.  
- **`createAccount` + meny + Scanner** — Pass 2/Exam — **stryk** i det här paketet.  
- **`ArrayList` som deklarerad typ** — kodstandard säger `List<Account>`.  
- **Getter-namn fel** (`getOwnerName`, `balance()`) — Exam låser `getOwner` / `getBalance`.  
- AI **tar bort `private`** när Main klagar — det är att riva valvet, inte fixa Main.

**Vad du tränar:** Feedback + en version *du* kan köra och förklara inför muntligt.  
**Varför:** Examination 1 README Q1 + private/konstruktor/getters.  
**Vad det INTE är:** “AI fixade hela banken” med factory och meny du inte bett om.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en **begränsad** prompt, t.ex.:

> Account med private owner och balance, konstruktor (String, double), getOwner, getBalance, deposit, withdraw med uttagsregel. AccountRegister med List<Account>, add(Account), printAll. Inga setters, ingen createAccount, ingen meny, ingen Scanner.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Publika fält eller `setBalance` / `setOwner`?  
- [ ] Saknas `getOwner` / `getBalance` (Exam-namn)?  
- [ ] `new Account()` utan argument medan du ska ha konstruktor med parametrar?  
- [ ] `createAccount`, `findAccount`, meny, `Scanner` du **inte** bett om?  
- [ ] `ArrayList<Account> accounts` som fälttyp i stället för `List<Account>`?  
- [ ] `Main` som fortfarande skriver `kim.balance = …`?  
- [ ] AI tog bort `private` “för att det skulle kompilera”?  
- [ ] Kan du förklara **Exam Q1** med pekning på `private balance` i svaret?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Skriv en **ren version du äger** — koppla till [03 — Övningar](./03-ovningar.md):

- `private` fält  
- konstruktor med `this`  
- getters  
- `List<Account> accounts = new ArrayList<>();`  
- `add` + `printAll` — minst två konton i test-`Main`  
- **ingen** factory/meny

Testa kompilering och körning. Spara i ditt projekt.

### Steg 4 — Andra AI-felet (setter eller upplåst valv)
Be AI “fixa” detta medvetet dåliga utkast — eller använd:

```java
// AI "fixade" kompileringsfelet:
private double balance;

// ...
kim.balance = 1000;  // AI gjorde fältet package-private eller public igen
```

Skriv **minst en** FEEDBACK-rad om **upplåst valv** (public fält, borttagen private, eller setter). Fixa till `private` + getter.

### Steg 5 — Reflektion (3 meningar)
1. Vilket **Exam Q1**-svar kan du ge med pekning på `private balance`?  
2. Vad **strök** du som spill (factory, meny, setter)?  
3. Varför är `List<Account>` bättre än `ArrayList<Account>` som deklarerad typ i registret?

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade  
- [ ] Peka på **`private balance`** — Exam Q1  
- [ ] Peka på **konstruktor** — var `new Account(...)` fyller fack  
- [ ] Peka på **`List<Account>`** i `AccountRegister`  
- [ ] **Ingen** `createAccount` / meny / `setBalance` kvar  
- [ ] `printAll` visar minst två konton i konsolen  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Kärna i `Account`:

```java
private String owner;
private double balance;

public Account(String owner, double initialBalance) {
    this.owner = owner;
    this.balance = initialBalance;
}

public String getOwner() { return owner; }
public double getBalance() { return balance; }
```

Kärna i `AccountRegister`:

```java
private List<Account> accounts = new ArrayList<>();

public void add(Account account) {
    accounts.add(account);
}
```

Typiska FEEDBACK-rader:

- `FEEDBACK: publikt balance → private + getBalance; Exam Q1 kräver pekbart valvlås.`  
- `FEEDBACK: setBalance tillagd → stryk; ändra via deposit/withdraw.`  
- `FEEDBACK: createAccount + meny → stryk; paketet är add + printAll utan factory.`  
- `FEEDBACK: ArrayList som fälttyp → deklarera List<Account>, new ArrayList<>().`  
- `FEEDBACK: AI tog bort private → lägg tillbaka; fixa Main med getters.`  
- `FEEDBACK: tom Account() + fält utifrån → en konstruktor med this.owner = owner.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-utkast, behåller private och List, stryker factory och setters, och kan peka private balance inför README Q1.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
