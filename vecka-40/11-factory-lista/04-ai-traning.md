# 04 — AI-träning: Factory, sök och meny

AI kan generera hela `AccountRegister` på sekunder — med `new Account` kvar i `Main`, `get(0).deposit`, eller `SavingsAccount` du inte bett om. Det betyder inte att *du* äger factory-mönstret eller null-hanteringen. Här tränar du: **utspritt `new`**, **sök utan null**, **meny som gissar index** — ändra, förklara.

Det är inte magi. Det är en dörr för `new` + linjär sökning + null före punkt.

---

## Scenario — problem först

Du ber AI: *“Skriv AccountRegister med createAccount, findAccount och Main-meny för konton Leo och Mira.”*  
Du får tillbaka något i stil med:

```java
public class AccountRegister {
    private List<Account> accounts = new ArrayList<>();

    public void createAccount(String owner, double startBalance) {
        accounts.add(new Account(owner, startBalance));
    }

    public Account findAccount(String owner) {
        for (int i = 0; i < accounts.size(); i++) {
            if (accounts.get(i).getOwner().equals(owner)) {
                return accounts.get(i);
            }
        }
        return null;
    }
}
```

```java
// Main (utdrag)
case 1 -> {
    System.out.print("Ägare: ");
    String owner = scanner.nextLine();
    System.out.print("Startsaldo: ");
    double start = scanner.nextDouble();
    register.createAccount(owner, start);
    Account extra = new Account("Temp", 1);  // AI "för test"
}
case 3 -> {
    register.getAccounts().get(0).deposit(amount);  // AI gissar index
}
```

Svagheter:

- **`new Account` kvar i `Main`** — bryter factory / Exam Q2.  
- **`get(0).deposit`** — ignorerar `findAccount` och ägarnamn.  
- **`equals` istället för `equalsIgnoreCase`** — `"leo"` missar `"Leo"`.  
- **`getAccounts()` eller publik lista** — AI exponerar listan “för enkelhet”.  
- **`SavingsAccount` / arv / Git-commit-instruktioner** — NOLL SPILL; stryk.  
- **`deposit` utan null-koll** när AI skriver `findAccount(...).deposit(...)` direkt.  
- **Dubbel `new`:** både `createAccount` och `new Account` i samma `case 1`.

**Vad du tränar:** Feedback + en version *du* kan köra och peka på i IDE.  
**Varför:** Exam 1 — factory, sök, meny. Du måste se när AI “nästan” har rätt arkitektur men läcker `new` i Main.  
**Vad det INTE är:** “AI fixade så det körde” utan att du kan säga var `new` ska stå.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt (eller jobba mot snutten ovan) där du ber om:
- tre filer: `Account`, `AccountRegister`, `Main`;
- `List<Account>` i registret;
- `createAccount` som **enda** stället för `new Account`;
- `findAccount` med `equalsIgnoreCase` och `null` vid miss;
- meny 1–5 med `Scanner`.

**Uttryckligen:** ingen arv, ingen Git, ingen `SavingsAccount`.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Finns `new Account` i `Main`?  
- [ ] Anropas `get(0)` eller hårdkodat index för transaktioner?  
- [ ] Saknas `return null` i `findAccount`?  
- [ ] `findAccount(...).deposit(...)` utan null-koll?  
- [ ] Jämförelse med `==` på strängar eller `equals` utan `IgnoreCase`?  
- [ ] Lista publik / `getAccounts()` som låter Main mutera direkt?  
- [ ] `SavingsAccount`, `extends`, Git, README-mall du inte bett om?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa factory
Skriv en **ren `createAccount` du äger** — koppla till [03 — Uppgift 1](./03-ovningar.md):

```java
public void createAccount(String owner, double startBalance) {
    Account account = new Account(owner, startBalance);
    accounts.add(account);
}
```

Sök i hela projektet: `new Account` ska **bara** träffa den metoden (plus ev. konstruktordefinitionen i `Account.java` — det räknas inte som “skapa i Main”).

### Steg 4 — Anpassa sök + null
Fixa `findAccount` och ett menyfall (3 eller 4):

```java
Account found = register.findAccount(owner);
if (found != null) {
    found.deposit(amount);
} else {
    System.out.println("Kontot finns inte.");
}
```

Testa miss: sök `"Zara"` när hon inte finns — programmet ska **inte** krascha.

### Steg 5 — Andra AI-felet (index eller dubbel new)
Be AI om meny — eller använd denna medvetet trasiga variant:

```java
case 4 -> {
    double amount = scanner.nextDouble();
    register.getAccounts().get(0).withdraw(amount);
}
```

Skriv **minst en** FEEDBACK-rad om **index-gissning**. Ersätt med `findAccount` + null-koll + `withdraw` på rätt objekt.

### Steg 6 — Reflektion (3 meningar)
1. Vilket factory-brott hade AI gjort (`new` i Main, glömd `add`, dubbel skapelse)?  
2. Vad ändrade du i sök (`equalsIgnoreCase`, `return null`, null-koll)?  
3. Varför är Exam Q2 inte “jag har en createAccount någonstans” om `new` fortfarande finns i `Main`?

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade (factory **och** sök/meny)  
- [ ] Peka på **`new Account`** — endast i `createAccount`  
- [ ] Peka på **null-gren** före `deposit` / `withdraw`  
- [ ] Peka på något du *tog bort* (index, arv, Git, extra `new`)  
- [ ] Testkörning: två konton via meny, stoppat uttag, avslut  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Ren factory + sök (utdrag):

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

Typiska FEEDBACK-rader:

- `FEEDBACK: new Account i Main case 1 → stryk; all skapelse via createAccount.`  
- `FEEDBACK: get(0).deposit → läs owner, findAccount, null-koll, sedan deposit.`  
- `FEEDBACK: equals utan IgnoreCase → equalsIgnoreCase så leo hittar Leo.`  
- `FEEDBACK: findAccount(...).withdraw direkt → spara i variabel, if != null.`  
- `FEEDBACK: SavingsAccount tillagt → stryk; paketet är G-kärna utan arv.`  
- `FEEDBACK: publik ArrayList → private List<Account>, metoder i registret.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-utkast, flyttar all new till createAccount, ersätter index med findAccount, och behåller bara kod jag kan förklara rad för rad.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
