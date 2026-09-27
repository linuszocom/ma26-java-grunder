# 10 — Inkapsling, konstruktor och registerlista

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v4 Pass 1 — `private` fält, konstruktor, `getOwner` / `getBalance`, `AccountRegister` med `List<Account>`, lägga till minst två konton och skriva ut. **Vecka 40, pass 1.**

**Förkunskaper:** `Account` med `deposit` / `withdraw` från [09-transaktioner](../../vecka-39/09-transaktioner/). Klass/objekt från [08-klasser-objekt](../../vecka-39/08-klasser-objekt/). `ArrayList` från [06-arraylist-scanner](../../vecka-38/06-arraylist-scanner/) hjälper för listan.

**Omfång:** `Account.java` (private, konstruktor, getters, befintliga transaktionsmetoder), `AccountRegister.java` (lista + `add` + `printAll`), `Main.java`. Engelska klass- och fältnamn. **Ingen** `createAccount` / factory (Pass 2). **Ingen** full Exam-meny, **inget** arv, **inget** Git-fokus här.

---

## 🗺️ Veckans körschema (v4 — tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Inkapsling och konstruktor (denna mapp)** | Max ~15 min: läs [01 — Teoriguide](./01-teoriguide.md) (private, getters, konstruktor, registerlista) | Lås fält, getters, `new Account(...)`, två konton i register | Välj ditt spår nedan (~3–5 h) |
| **Pass 2 — Factory och sökning** | Max ~15 min: [01 — Teoriguide](../11-factory-lista/01-teoriguide.md) | `createAccount`, hitta konto på `owner` | [11-factory-lista](../11-factory-lista/) |
| **Pass 3 — Arv (VG) och Exam 1-start** | Max ~15 min: läs [examination_1_kontoappen.md](../../examination_1_kontoappen.md) + [01 — Teoriguide](../12-arv-exam1-start/01-teoriguide.md) | README Q1–Q3, repo-struktur, arv (VG) | [12-arv-exam1-start](../12-arv-exam1-start/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (private + register med två konton)
2. [ ] **Träna kritiskt tänkande:** [04 — AI-träning](./04-ai-traning.md)
3. [ ] **Kontrollera dina målsvar:** [05 — Självtest](./05-sjalvtest.md) utan facit först  
*( [01 — Teoriguide](./01-teoriguide.md) som uppslagsverk bara om du kör fast.)*

---

### 🟡 2. Du missade passet eller börjar från noll (Ta ikapp-spåret)
*Om du var sjuk, hade förhinder eller känner att grunderna inte sitter:*
1. [ ] **Förstå koncepten:** [01 — Teoriguide](./01-teoriguide.md) från start till mål
2. [ ] **Få överblick:** [02 — Visuellt](./02-visuell.md)
3. [ ] **Koda själv:** [03 — Övningar](./03-ovningar.md)
4. [ ] **Granska & anpassa:** [04 — AI-träning](./04-ai-traning.md)
5. [ ] **Slutkontroll:** [05 — Självtest](./05-sjalvtest.md)

---

### 🟣 3. Du siktar på VG / vill fördjupa dig (Stretch)
*Om du blev klar snabbt — frivilligt, inom kursplanen:*
- [ ] **Stretch i övningarna:** Skriv Exam 1 README **fråga 1** (inkapsling) i ditt projekt — peka på `private balance` och förklara bakdörren (se [03 — Övningar](./03-ovningar.md))
- [ ] **Tre konton + transaktion:** Efter `printAll`, kör `deposit` på ett konto i listan via `register.getAccount(0)` eller motsvarande — bevisa att getters fortfarande fungerar
- [ ] **Felsökningskarta:** Skriv med flit `kim.balance = -999` i `Main` — läs `has private access` högt och dokumentera fixen i en mening

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Inkapsulation (Exam README Q1):** "`owner` och `balance` är `private` — bankvalvet är låst utifrån. Main läser med `getOwner` / `getBalance` och ändrar med `deposit` / `withdraw`. Hade fälten varit publika kunde Main skriva `balance = -99999` direkt — det är bakdörren jag pekar bort från."

> **Konstruktor:** "`new Account("Kim", 1000)` kör konstruktorn som sätter `this.owner` och `this.balance` i ett steg. Main får inte längre skriva `kim.owner = ...` efter `private`."

> **Registerlista:** "`AccountRegister` äger `List<Account>`. Jag lägger till med `add(new Account(...))` och skriver ut alla med en loop i `printAll` — listan bor i registret, inte som lösa variabler i `Main`."

---

## 📝 Examination

Det här paketet träffar **Examination 1 (Kontoappen)** — **README fråga 1 (inkapsling)**, private fält, konstruktor, getters, och grunden till `AccountRegister` med lista. Factory (`createAccount`), sökning och meny kommer i senare pass ([11-factory-lista](../11-factory-lista/), [12-arv-exam1-start](../12-arv-exam1-start/), [13-exam-1](../vecka-41/13-exam-1/)).

## 🏁 Nästa steg

När du är klar här: [11-factory-lista](../11-factory-lista/) — factory och hitta konto (*publiceras i nästa del*).
