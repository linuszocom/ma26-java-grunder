# 01 — Teoriguide: Arv, README och start av Exam 1

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Läs också [Examination 1 — Kontoappen](../../examination_1_kontoappen.md). Se [mappens README](./README.md).

Du har `Account` med mur (`private`), konstruktor, getters, transaktioner, lista och factory. Nu: **VG-spåret** med arv — och **Exam 1** med README, eget repo och muntlig redovisning i IDE:n. Det är inte magi. Det är `extends`, `super`, egna ord i README — och ägarskap.

**Förutsättning:** [10-inkapsling](../10-inkapsling/) + [11-factory-lista](../11-factory-lista/) + transaktioner från vecka 39. Här: arv, exam-artefakter (README, inspelning), repo-start. **Ingen** `interface`, **ingen** Examination 2.

---

## Problemet först — kopia överallt

Många tänker: “Jag lägger bara till `interestRate` i `Account` för alla konton.” Andas. Då bär **vanliga** konton onödig ränta — och varje ny kontotyp blir fler `if` i samma klass.

**Dåligt läge** — allt i en fil:

```java
public class Account {
    private String owner;
    private double balance;
    private double interestRate;  // 0 för vanliga konton — rörigt

    public void applyInterest() { ... }  // bara sparkonton ska ha detta
}
```

**Bättre tanke:** Vanligt konto = G-kravet. Sparkonto = **samma** konto **plus** ränta — utan att sabba `Account` för alla.

---

## Arv — subklass är “samma ritning + tillbyggnad”

**Metafor:** **Husmodell + annex.** `Account` är grundplanen (ägare, saldo, insättning, uttag). `SavingsAccount` är samma hus **med** en räntemotor i annexet — inte ett helt främmande byggnad.

**Vad det är:** **`extends`** = subklassen **ärver** basklassens fält och metoder och lägger till eget.  
**Varför det finns:** Olika kontotyper utan att `Account` sväller. VG i Examination 1.  
**Om det saknas / vad det INTE är:** INTE två orelaterade klasser. INTE `interface` / `implements`. INTE att `Account` försvinner. INTE att arv öppnar `private` luckor.

```java
public class SavingsAccount extends Account {
    private double interestRate;

    public SavingsAccount(String owner, double startBalance, double interestRate) {
        super(owner, startBalance);
        this.interestRate = interestRate;
    }
}
```

**Målsvar (säg högt / skriv i README):**  
*“SavingsAccount extends Account — sparkontot är ett konto plus interestRate och applyInterest. deposit och withdraw följer med.”*

---

## `extends` och filen

**Vad det är:** Första raden i klassen: `public class SavingsAccount extends Account` i filen **`SavingsAccount.java`**.  
**Varför:** Java kräver `public class` = filnamn. Basklassen ligger kvar i `Account.java`.  
**Om det saknas / vad det INTE är:** INTE att klistra in hela `Account` i samma fil. INTE svenska klassnamn (`Sparkonto.java`).

```
src/
  Account.java
  SavingsAccount.java   ← ny
  AccountRegister.java
  Main.java
```

---

## `super` — basklassens konstruktor först

**Metafor:** **Nyckel till grundplanet innan annexet.** `Account` har ingen tom konstruktor — subklassen **måste** anropa den fyllda.

**Vad det är:** **`super(owner, startBalance)`** = anrop till basklassens konstruktor. **Måste** vara **första** satsen i subklassens konstruktor.  
**Varför:** `private` fälten `owner` och `balance` fylls **där** — inte med `this.owner =` i subklassen (luckorna är stängda).  
**Om det saknas / vad det INTE är:** INTE valfritt. INTE efter `this.interestRate =`. javac: *call to super must be first statement*.

```java
public SavingsAccount(String owner, double startBalance, double interestRate) {
    super(owner, startBalance);
    this.interestRate = interestRate;
}
```

**Målsvar (säg högt / skriv i README):**  
*“super(owner, startBalance) fyller Account-delen först. Sedan sätter jag interestRate.”*

---

## `private` gäller fortfarande — använd dörrarna

**Problem först** — subklassen petar i luckan:

```java
public void applyInterest() {
    balance = balance + balance * interestRate;  // javac: private access
}
```

**Metafor:** Annexet står **utanför** muren kring `balance` — precis som `Main`.

**Lösning** — samma dörrar som resten av appen:

```java
public void applyInterest() {
    double extra = getBalance() * interestRate;
    deposit(extra);
}
```

**Vad det INTE är:** INTE `setBalance`. INTE “arv öppnar private”. INTE mutation i `Main` efteråt.

**Målsvar (säg högt / skriv i README):**  
*“Subklassen når balance via getBalance och deposit — inte this.balance.”*

---

## `@Override` — samma metodnamn, specialiserat beteende

**Vad det är:** Subklassen **ersätter** basklassens metod med samma signatur — t.ex. `printInfo()` som också skriver räntesats.  
**Varför:** Listan anropar `printInfo()` på alla konton — sparkontot ska visa extra rad utan `if` i loopen.  
**Om det saknas / vad det INTE är:** INTE en ny metod `printInfo2`. INTE att ta bort `printInfo` i `Account`.

```java
@Override
public void printInfo() {
    super.printInfo();
    System.out.println("Räntesats: " + interestRate);
}
```

**Målsvar (säg högt / skriv i README):**  
*“Override printInfo: super.printInfo() först, sedan min extra rad för sparkontot.”*

---

## Lista och polymorfism — `ArrayList<Account>`

**Vad det är:** Ett `SavingsAccount`-objekt **är** ett `Account`. Samma lista som i factory-paketet kan hålla båda typerna.  
**Varför:** En `printAll`-loop — rätt `printInfo` körs per objekt.  
**Om det saknas / vad det INTE är:** INTE `ArrayList<SavingsAccount>` som **enda** lista (då får vanliga konton inte plats). INTE två separata listor.

```java
ArrayList<Account> accounts = new ArrayList<>();
accounts.add(new Account("Kim", 1000));
accounts.add(new SavingsAccount("Moa", 500, 0.02));
```

Loopen `accounts.get(i).printInfo()` — vanligt konto: en rad; sparkonto: två rader (Override).

---

## VG i registret — skapas och syns

**Problem först:** `SavingsAccount.java` finns på disk men **ingen** `new SavingsAccount` i appen → **inte VG**.

**Lösning:** Syskon-factory i `AccountRegister`:

```java
public SavingsAccount createSavingsAccount(String owner, double startBalance, double interestRate) {
    SavingsAccount created = new SavingsAccount(owner, startBalance, interestRate);
    accounts.add(created);
    return created;
}
```

`new` stannar i registret — samma princip som `createAccount`. Menyn (i **exam-repot**) anropar metoden; här räcker hårdkodat test i `Main` om du tränar.

**Målsvar (säg högt / skriv i README):**  
*“VG kräver SavingsAccount i listan — skapat via createSavingsAccount, inte bara en öde fil.”*

---

## G mot VG — samma examination, olika djup

| | **G** | **VG** |
|---|--------|--------|
| `Account` + `AccountRegister` + `Main` | krav | krav |
| Inkapsling, factory, meny, uttagsregel | krav | krav |
| README Q1–Q3 + AI | krav | krav |
| Muntligt 2–3 delar i IDE:n | krav (övergripande) | krav (**under huven**, inkl. arv om du har det) |
| `SavingsAccount` i appen | nej | **krav** |

G är inte “sämre OOP” — du ska fortfarande kunna `private`, factory och stegkedja. VG lägger till **arv i produktion**.

---

## README till Examination 1 — tre frågor + AI

Examinationen kräver **egna ord på svenska** (~2–4 meningar per fråga). Peka på **engelska** namn i koden.

### Q1 — Inkapsling

**Vad du ska svara:** Vad inkapsling betyder **i din app**. Peka `private` på `owner` eller `balance`. Vad hade hänt om fältet var **publikt**?

**Målsvar (säg högt / skriv i README):**  
*“balance är private. Main når den via getBalance/deposit — inte direkt. Publikt fält hade kunnat sättas till -99999 och kringgå withdraw.”*

**INTE:** “Inkapsling är viktigt” utan pekning i fil.

### Q2 — Factory (skapande-mönster)

**Vad du ska svara:** Var skapas `Account`-objekt (`createAccount`)? Varför **inte** `new Account` i `Main` varje gång användaren väljer nytt konto?

**Målsvar (säg högt / skriv i README):**  
*“new Account står i createAccount i AccountRegister. Där add:as kontot till listan. new i Main riskerar hus som aldrig hamnar i registret.”*

### Q3 — Datalogisk stegkedja (ett menyval)

**Vad du ska svara:** Ett menyval som kedja: **inmatning → vilket objekt → vilken metod → utskrift**.

Exempel “sätt in pengar”:

1. Användaren skriver ägare + belopp (Scanner i exam-appen).  
2. `findAccount` hittar objektet (eller null).  
3. `deposit(amount)` på **det** objektet.  
4. Konsolen visar nytt saldo — eller att kontot saknas.

**Målsvar (säg högt / skriv i README):**  
*“Meny sätt in: inmatning → findAccount → deposit på rätt objekt → utskrift av saldo eller fel.”*

**INTE:** “Loopen körs” utan objekt och metod.

### AI-reflektion (3–5 meningar)

**Vad du ska skriva:** Var du körde fast. Om du använde AI: **ett exempel** där du **ändrade** förslaget innan det fungerade.

**Ägarskap:** På redovisningen är det **du** som förklarar i IDE:n. README räddar inte tystnad i inspelningen.

---

## Muntlig redovisning / inspelning — vad som ska synas

Examinationen kräver **samma repo**, **IDE öppen**, **2–3 delar** du valt i förväg. **Video** (4–8 min, skärm + din röst, markör pekar på kod) **eller** muntlig redovisning enligt Moodle — samma krav: du förklarar i IDE:n.

**Godkänd form:** `Account.java` / `AccountRegister.java` / ev. `SavingsAccount.java` — peka `private`, `createAccount` + `new`, `withdraw`-spärr, (VG) `extends`/`super`.

**Underkänd form:** Läsa README rakt av. Bara `while`-menyn utan klass. Webbsida. Någon annan pratar i videon.

**Planera innan inspelning:** Skriv i README-utkastet under rubriken *Muntligt — mina 2–3 delar*: fil + ungefär vad du säger (ex. “Account rad med private balance”, “createAccount rad med new”).

**Klart-check — redovisning (från examinationen):**
- [ ] Repot öppnas i IDE:n  
- [ ] Jag har valt 2–3 delar och vet fil/rad  
- [ ] Jag kan förklara `createAccount` och ett `deposit`/`withdraw`  
- [ ] Jag vet om **video eller muntlig redovisning** enligt Moodle  

---

## Start exam-repo — checklista, inte färdig lösning

1. **Nytt publikt GitHub-repo** — bara Kontoappen (kopiera **inte** hela utbildnings-hubben).  
2. **IDE-projekt** med minst `Account.java`, `AccountRegister.java`, `Main.java`.  
3. **`README.md`** med rubriker: Köra, Teori (1–3), AI-reflektion, Muntligt — mina 2–3 delar.  
4. **Commits under arbetet** — minst 5 totalt innan inlämning (inte en dump sista dagen).  
5. **Klart-check kod** — se [examination_1_kontoappen.md](../../examination_1_kontoappen.md).

Det här paketet stoppar vid **utkast + struktur**. Färdig meny och full körning = examinationsveckan.

---

## Metod — när du tvekar (arv)

1. **`extends Account` + fil `SavingsAccount.java`?**  
2. **`super(...)` först i konstruktor?**  
3. **Ränta/ extra via `getBalance` + `deposit` — inte `this.balance`?**  
4. **Objekt i `ArrayList<Account>` via `createSavingsAccount`?**  
5. **README egna ord — kan du peka i IDE:n utan att läsa upp?**

**Målsvar (säg högt / skriv i README) — metod:**  
*“Arv: extends + super, private via dörrar, subklass i listan. Exam: README Q1–Q3, repo, inspelning med 2–3 pekare.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| `this.balance` i `SavingsAccount` | `getBalance()` + `deposit()` — samma mur som Main |
| Glömmer `super` eller fel ordning | Första satsen i konstruktor |
| `SavingsAccount.java` finns men aldrig `new` | VG = i lista via factory |
| `@Override` med fel signatur (`printinfo`) | Samma namn och parametrar som i `Account` |
| `implements` / interface | NOLL SPILL — bara `extends Account` |
| README = kopierad mall utan pekning | Skriv om med **dina** filer |
| Grupprepo / kurs-hubb som exam-inlämning | Eget individuellt repo |
| Färdig app krävs i det här paketet | Utkast + plan räcker här; app klar vecka 41 |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar:

1. En mening: varför `SavingsAccount extends Account` istället för extra fält i `Account`.  
2. Vad `super(owner, startBalance)` gör i konstruktorn.  
3. README Q1 i **en** mening med `private`.  
4. README Q3 för menyval “ta ut pengar” som stegkedja.  
5. Vilka **2–3 delar** du ska peka på i inspelningen.

När du kan säga svaren högt: gå vidare.

---

## Nästa steg

[02 — Visuellt](./02-visuell.md), sedan [03 — Övningar](./03-ovningar.md).
