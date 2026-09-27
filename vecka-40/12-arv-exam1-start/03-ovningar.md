# 03 — Övningar

**Omfång det här paketet:** README-utkast till Examination 1 (Q1 inkapsling, Q2 factory, Q3 stegkedja, AI-reflektion, plan för muntliga delar). Start **eget exam-repo** (checklista — **inte** färdig Kontoapp). Valfri VG-stretch: `SavingsAccount extends Account`. **Ingen** full exam-lösning, **ingen** `interface`, **ingen** Examination 2.

AI får föreslå text och kod. Du måste kunna **peka och förklara** README-svar, repo-struktur och (VG) arv.

**Var du kör:** Eget **exam-repo** (nytt publikt GitHub-repo) + IDE med JDK. Läs [Examination 1 — Kontoappen](../../examination_1_kontoappen.md).

**Bygger på:** [10-inkapsling](../10-inkapsling/), [11-factory-lista](../11-factory-lista/). Saknar du register/factory — gör README-övningarna ändå mot **din** (eller övnings-) kod.

---

## Uppgift 1 — Skapa exam-repo (struktur, inte färdig app)

**Mål:** Ha rätt **behållare** för Examination 1 — innan du fyller all kod.

**Scenario:** Du ska lämna in Kontoappen individuellt. Kurs-hubben räknas **inte**.

**Krav:**
1. Skapa **nytt publikt** GitHub-repo (namn t.ex. `kontoappen-dittnamn`).
2. Nytt Java-projekt i IDE — koppla till repot (`git init` / clone / Git-integration enligt [07-git-github](../../vecka-39/07-git-github/)).
3. Lägg in **minst** tomma/skelett-filer: `Account.java`, `AccountRegister.java`, `Main.java` (innehåll får vara ofärdigt).
4. Skapa `README.md` med **denna rubrikstruktur** (innehåll fyller du i uppgift 2–3):

```markdown
# Kontoappen
Kort: vad programmet ska göra (konsol, bankkonton).

## Köra
JDK + IDE. Main.

## Teori
### 1. Inkapsling
(utkast)

### 2. Factory
(utkast)

### 3. Stegkedja — ett menyval
(utkast)

## AI-reflektion
(utkast)

## Muntligt — mina 2–3 delar
1. fil + vad jag pekar på
2. …
3. … (VG: SavingsAccount)
```

5. **Minst en** begriplig commit + push (t.ex. `add project skeleton and README structure`).

**Klart-check (peka i DIN miljö):**
- [ ] Repot är **ditt** — inte grupp, inte kursmaterial-repo  
- [ ] Tre `.java`-filer syns i IDE och på GitHub  
- [ ] README har alla rubriker ovan  
- [ ] Du kan öppna repot i IDE:n (samma som inspelningen ska använda)

**INTE krav nu:** Färdig meny, fem commits totalt, VG-subklass — det kommer under examinationsveckan.

**Ägarskap:** Du ska kunna säga varför exam kräver **eget** repo.

---

## Uppgift 2 — README Q1–Q3 (egna ord, peka i kod)

**Mål:** Skriv **utkast** (~2–4 meningar per fråga) i exam-repots `README.md`. Text ska matcha **din** (eller övnings-) kod — inte kopierad mall.

**Brief:** Examinationen bedömer att du **förstår** inkapsling, factory och datalogiskt flöde. README tränar det **innan** inspelningen.

### Q1 — Inkapsling

**Krav:**
1. Förklara inkapsling **i Kontoappen**.
2. Peka på **`private`** på `owner` eller `balance` i `Account.java` (rad i README: “se Account.java rad …”).
3. En mening: vad hade hänt om fältet var **publikt**?

**Klart-check:**
- [ ] Ordet **private** och filnamn **Account.java** finns i texten  
- [ ] Du kan peka i IDE:n utan att läsa README ordagrant  

### Q2 — Factory

**Krav:**
1. Beskriv skapande-mönstret: var skapas `Account`-objekt?
2. Peka på **`createAccount`** och raden med **`new Account`** i `AccountRegister.java`.
3. Varför **inte** `new Account` i `Main` när användaren väljer “skapa konto”?

**Klart-check:**
- [ ] **`new Account`** nämns **i register**, inte som huvudidé i `Main`  
- [ ] Du kan säga vad som händer om `new` bara står i menyn utan `add`  

### Q3 — Stegkedja (ett menyval)

**Krav:**
1. Välj **ett** menyval (t.ex. “sätt in pengar” eller “ta ut pengar”).
2. Skriv stegkedja: **inmatning → objekt → metod → utskrift**.
3. Använd **dina** metodnamn (`findAccount`, `deposit`, `withdraw` — som i examinationen).

**Exempelriktning (skriv om med egna ord):**

> Meny “sätt in”: användaren skriver ägare och belopp. `findAccount` returnerar kontot. `deposit` körs på det objektet. Konsolen visar nytt saldo — eller att kontot saknas.

**Klart-check:**
- [ ] Minst **fyra** steg i kedjan  
- [ ] Ett **objekt** och en **metod** namnges  
- [ ] INTE bara “loopen körs”  

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning README (efter eget utkast)</summary>

**Q1:** balance private → Main använder getBalance/deposit → publikt fält kunde kringgå withdraw.  
**Q2:** new Account i createAccount + add → Main anropar bara createAccount.  
**Q3:** inmatning → findAccount → deposit/withdraw → utskrift (saldo/meddelande/fel).

</details>

---

## Uppgift 3 — AI-reflektion + muntlig plan i README

**Mål:** Förbereda examinationens **ägarskapsdel** — skriftligt i README, kopplat till inspelning.

**Krav:**
1. Under **AI-reflektion:** 3–5 meningar. Var körde du fast (eller kan tänka dig att köra fast)? Om AI: **ett exempel** där du **ändrade** förslaget (t.ex. withdraw-ordning, factory-placering, weak README).
2. Under **Muntligt — mina 2–3 delar:** lista **2–3** pekare du ska använda i IDE:n / inspelningen. Format: `Account.java — private balance + varför` / `AccountRegister.java — createAccount och new` / (VG) `SavingsAccount.java — extends och super`.
3. Minst **en** del ska vara OOP (klass/objekt/metod) — inte bara `while`-menyn.

**Klart-check:**
- [ ] AI-texten nämner **en konkret ändring** du gjorde (inte “AI hjälpte”)  
- [ ] Muntlig-sektionen har **filnamn** + **vad du säger**  
- [ ] Du vet vad inspelningen ska **visa** (IDE, kod, markör — inte webbläsare)

**Ägarskap:** README får vara utkast — men du ska kunna **utöka** svaren muntligt utan att läsa upp dem.

---

## Uppgift 4 — Stretch (valfritt, VG): `SavingsAccount`

**Mål:** Träna VG-kravet **innan** examinationsveckan — subklass **används** i appen.

**Brief:** I **samma exam-repo** (eller separat övningsprojekt om du vill):

**Krav:**
1. Ny fil `SavingsAccount.java`: `public class SavingsAccount extends Account`.
2. Fält `private double interestRate`; konstruktor med **`super(owner, startBalance)` först**, sedan `this.interestRate = …`.
3. Metod `applyInterest()` som använder **`getBalance()`** och **`deposit(...)`** — **inte** `this.balance`.
4. `@Override public void printInfo()` med `super.printInfo()` + extra rad (räntesats).
5. I `AccountRegister`: `createSavingsAccount(...)` som `new SavingsAccount`, `add`, `return`.
6. Bevis: minst ett sparkonto syns när du listar konton (`printAll` eller motsvarande loop).

**Klart-check (peka i DIN kod):**
- [ ] **`extends`** på rad 1 i klassen  
- [ ] **`super`** som första sats i konstruktor  
- [ ] **`applyInterest`** utan direct access till `balance`  
- [ ] **`new SavingsAccount`** i register — inte bara fil på disk  
- [ ] Lägg till punkt 3 (eller 4) under **Muntligt** i README: vad du säger om arv  

**INTE krav:** Full Scanner-meny med “skapa sparkonto” — men det ska in **före inlämning** om du siktar VG. Meny kan byggas vecka 41.

**Facit-riktning (efter eget försök):**

<details>
<summary>Visa facit-riktning SavingsAccount (kort)</summary>

```java
public class SavingsAccount extends Account {
    private double interestRate;

    public SavingsAccount(String owner, double startBalance, double interestRate) {
        super(owner, startBalance);
        this.interestRate = interestRate;
    }

    public void applyInterest() {
        double extra = getBalance() * interestRate;
        deposit(extra);
    }

    @Override
    public void printInfo() {
        super.printInfo();
        System.out.println("Räntesats: " + interestRate);
    }
}
```

```java
public SavingsAccount createSavingsAccount(String owner, double startBalance, double interestRate) {
    SavingsAccount created = new SavingsAccount(owner, startBalance, interestRate);
    accounts.add(created);
    return created;
}
```

</details>

---

## Exam Klart-check (referens — inte allt ska vara klart idag)

Använd [examination_1_kontoappen.md](../../examination_1_kontoappen.md) som **målbild**. Markera det du **redan** har efter vecka 40 — resten vecka 41.

**Kod (G) — ska sitta före inlämning:**
- [ ] `Main` körbar i IDE  
- [ ] `private` + konstruktor + getters på `Account`  
- [ ] `deposit` / `withdraw` med spärr  
- [ ] `new Account` **bara** i `createAccount`  
- [ ] Lista, sök, två konton i testkörning  
- [ ] Meny 1–5 (svenska)  
- [ ] ≥5 commits, publikt repo  

**README + redovisning:**
- [ ] Q1–Q3 + AI i README (utkast OK här)  
- [ ] 2–3 muntliga delar planerade  
- [ ] Vet **video eller muntlig redovisning** enligt Moodle  

**VG extra:**
- [ ] `SavingsAccount` i lista + används  
- [ ] Kan förklara arv i IDE:n  

---

## När du kört fast

1. *private access in Account* i subklass → använd `getBalance`/`deposit`.  
2. *call to super must be first* → flytta `super` överst i konstruktor.  
3. README känns tomt → peka en **rad** i kod per fråga, skriv från pekningen.  
4. Osäker på inspelning → öva **högt** med README-listan “Muntligt — mina 2–3 delar”.  
5. Jämför [01-teoriguide](./01-teoriguide.md), [04 — AI-träning](./04-ai-traning.md).

Nästa: [04 — AI-träning](./04-ai-traning.md).
