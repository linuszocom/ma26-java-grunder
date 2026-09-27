# 04 — AI-träning: Svag README, fel `extends`/`super` & ägarskap

AI kan skriva README som **låter** rätt och kod som **nästan** kompilerar. Det betyder inte att du äger Examination 1. Här tränar du: **tom mall-README**, **fel arv** (`extends` utan `super`, `this.balance` i subklass) — granska, ändra, förklara.

Det är inte magi. Det är egna ord + `super` först + getBalance/deposit.

---

## Scenario A — problem först: README utan pekning

Du ber AI: *“Skriv README till min Java bankapp för examination.”* Du får:

```markdown
## 1. Inkapsling
Inkapsling är viktigt inom OOP. Det skyddar data.

## 2. Factory
Jag använder factory pattern för att skapa objekt.

## 3. Stegkedja
Programmet kör en loop tills användaren avslutar.
```

**Svagheter:**
- **Q1:** Inga **`private`**, inget filnamn, ingen “vad om publikt”.  
- **Q2:** **`createAccount`** / **`new Account`** saknas — bara buzzwords.  
- **Q3:** **Loop** ≠ stegkedja (inget objekt, ingen metod).  
- **AI-reflektion** saknas helt.  
- **Muntlig plan** saknas — inspelning blir improvisation → IG-risk.

**Vad du tränar:** Feedback + README du kan **peka** i IDE:n.  
**Varför:** Examinationen bedömer README **och** muntligt — malltext utan kodkoppling räcker inte.  
**Vad det INTE är:** “AI skrev README klart.”

---

## Scenario B — problem först: fel `extends` / `super`

AI föreslår:

```java
public class SavingsAccount extends Account {
    private double interestRate;

    public SavingsAccount(String owner, double startBalance, double interestRate) {
        this.interestRate = interestRate;
        super(owner, startBalance);
    }

    public void applyInterest() {
        balance = getBalance() * interestRate + getBalance();
    }
}
```

**Svagheter:**
- **`super` efter `this`** → *call to super must be first statement*.  
- **`balance =`** i subklass → *balance has private access in Account*.  
- Räntelogik oklar — ska gå via **`deposit`**.  
- **`implements Interestable`** i samma svar → stryk (NOLL SPILL).  
- **`new SavingsAccount` i `Main`** utan `add` → fil finns, **inte VG**.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv egen prompt (eller använd scenariorna) där du ber om:
- README Q1–Q3 + AI-reflektion till Kontoappen;
- `SavingsAccount extends Account` med `applyInterest`.

Spara prompten.

### Steg 2 — Granska README (checklist)
- [ ] Nämner **`private`** och **`Account.java`**?  
- [ ] Nämner **`createAccount`** och var **`new Account`** står?  
- [ ] Q3 = **inmatning → objekt → metod → utskrift**?  
- [ ] AI-reflektion med **konkret ändring**?  
- [ ] Kan du peka i **din** kod utan att läsa mallen?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

**Exempel:**
- `FEEDBACK: Q1 säger bara "viktigt" → lägg private balance + rad i Account.java + publikt scenario.`  
- `FEEDBACK: Q3 beskriver while → skriv findAccount + deposit för menyval sätt in.`  
- `FEEDBACK: saknar AI-reflektion → 3 meningar om withdraw-if jag ändrade.`

### Steg 3 — Skriv om README (egna ord)
I **exam-repots** `README.md`: ersätt AI-mallen med utkast enligt [03 — Uppgift 2](./03-ovningar.md). Max ~2–4 meningar per fråga. Lägg till **Muntligt — mina 2–3 delar**.

### Steg 4 — Granska arv-kod (checklist)
- [ ] `super(...)` **första** satsen i konstruktor?  
- [ ] Ingen **`this.balance`** / **`balance =`** i `SavingsAccount`?  
- [ ] `applyInterest` via **`getBalance()` + `deposit(...)`**?  
- [ ] `@Override` med **samma** signatur som basklassen (om printInfo)?  
- [ ] **`implements` / interface** borttaget?  
- [ ] `createSavingsAccount` + **`add`** — inte bara fil?

Skriv **minst två** FEEDBACK-rader om koden.

**Exempel:**
- `FEEDBACK: super efter this → flytta super(owner, startBalance) först.`  
- `FEEDBACK: balance = i applyInterest → räkna extra, deposit(extra) istället.`

### Steg 5 — Anpassa kod du äger
Korrigera till något i denna riktning (VG-övning — anpassa till ditt repo):

```java
public SavingsAccount(String owner, double startBalance, double interestRate) {
    super(owner, startBalance);
    this.interestRate = interestRate;
}

public void applyInterest() {
    double extra = getBalance() * interestRate;
    deposit(extra);
}
```

Kompilera. Om du inte bygger subklass än — skriv ändå **vad** du skulle ändra och varför.

### Steg 6 — Reflektion (3 meningar)
1. Vilket README-bristfall hade AI (tom fras, fel Q3)?  
2. Vilket arv-fel (super-ordning, private access)?  
3. Varför räcker inte “det kompilerar nästan” för examinationen?

---

## Klart-check (peka i DINA filer)

- [ ] Minst **tre** FEEDBACK-rader om README  
- [ ] Minst **två** FEEDBACK-rader om arv (eller planerad fix)  
- [ ] README-utkast med **private**, **createAccount/new**, **stegkedja**  
- [ ] **Muntligt — mina 2–3 delar** ifylld  
- [ ] Ingen **`interface`** kvar i AI-svar du behållit  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

**README Q1 (kort):**

> balance är private i Account.java. Main läser via getBalance och ändrar via deposit/withdraw. Hade balance varit public kunde Main sätta negativt saldo utan withdraw-regeln.

**README Q3 (kort):**

> Meny ta ut: användaren skriver ägare och belopp. findAccount hittar kontot. withdraw körs — vid för stort belopp meddelande och oförändrat saldo, annars nytt saldo i utskriften.

**Ren konstruktor + applyInterest:** se [03 — Uppgift 4 facit](./03-ovningar.md).

Typiska FEEDBACK-rader (arv):

- `FEEDBACK: super sist → första raden super(owner, startBalance).`  
- `FEEDBACK: balance private → deposit(getBalance()*rate), inte balance =.`  
- `FEEDBACK: @Override printinfo → samma stavning printInfo() som Account.`  
- `FEEDBACK: SavingsAccount.java utan createSavingsAccount → add till lista i register.`  
- `FEEDBACK: implements InterestAccount → stryk, bara extends Account.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag granskar AI-README mot pekning i kod och AI-arv mot super + private-dörrar. Behåller bara det jag kan förklara i inspelningen.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
