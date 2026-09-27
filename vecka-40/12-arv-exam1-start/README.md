# 12 — Arv + start Exam 1

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v4 Pass 3 — arv (`SavingsAccount extends Account`, VG-spår), G mot VG, README till Examination 1 (inkapsling, factory, stegkedja, AI-reflektion), start av **eget exam-repo**, och vad **muntlig redovisning / inspelning** ska visa i IDE:n.  
Pass 1 och Pass 2 i samma pedagogiska vecka har egna mappar — se körschemat.

**Flipped (Pass 3):** Ja — läs **[Examination 1 — Kontoappen](../../examination_1_kontoappen.md)** (~15 min) **innan** du kodar här. Du ska känna igen Klart-check, README-frågorna och redovisningsformen.

**Förkunskaper:** `Account` med `private`, konstruktor, getters, `deposit`/`withdraw` ([10-inkapsling](../10-inkapsling/)), `ArrayList<Account>`, `createAccount`, sök ([11-factory-lista](../11-factory-lista/)). Transaktioner och klass/objekt från vecka 39.

**Omfång:** `extends`, `super`, `@Override`, `applyInterest` via `getBalance`/`deposit` (inte `this.balance` i subklass). VG: `SavingsAccount` i lista + factory (`createSavingsAccount`). README-utkast Q1–Q3 + AI + plan för 2–3 muntliga delar. Start exam-repo (struktur, inte färdig app). **Ingen** `interface`, **ingen** gruppgit, **ingen** Examination 2 / `Medlem`.

---

## 🗺️ Veckans körschema (v4 — alla tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Inkapsling och konstruktor** | *Publiceras i* [10-inkapsling](../10-inkapsling/) | `private`, konstruktor, getters | [10-inkapsling](../10-inkapsling/) |
| **Pass 2 — Lista, sök och factory** | *Publiceras i* [11-factory-lista](../11-factory-lista/) | `ArrayList`, `findAccount`, `createAccount` | [11-factory-lista](../11-factory-lista/) |
| **Pass 3 — Arv (VG) + README + start Exam 1 (denna mapp)** | Max ~15 min: läs [Examination 1 — Kontoappen](../../examination_1_kontoappen.md) + skumma [01 — Teoriguide](./01-teoriguide.md) | `extends`/`super`, README-frågor, eget exam-repo | Välj ditt spår nedan (~3–5 h) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (README-utkast + exam-repo-checklista)
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
- [ ] **Stretch i övningarna:** `SavingsAccount` med `applyInterest`, `@Override printInfo`, `createSavingsAccount` — objektet ska synas i `printAll` (se [03 — Övningar](./03-ovningar.md) uppgift 4)
- [ ] **README-träning:** Skriv en fjärde punkt under “Muntligt — mina 2–3 delar”: fil + rad du ska peka på för `extends`/`super`
- [ ] **Dokumentera:** En mening: varför `ArrayList<Account>` kan hålla både `Account` och `SavingsAccount` — och varför **inte** bara `ArrayList<SavingsAccount>`

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Arv:** "`SavingsAccount extends Account` betyder att sparkontot **är** ett konto plus eget — t.ex. `interestRate` och `applyInterest`. `deposit`, `withdraw` och getters följer med. Jag skriver bara tillbyggnaden."

> **`super`:** "Subklassens konstruktor måste anropa basklassens konstruktor med `super(owner, startBalance)` **först** — annars fylls inte `private` fälten i `Account`."

> **G vs VG:** "G = `Account` + register + meny + README + muntligt 2–3 delar. VG = allt det **plus** `SavingsAccount` som **används** i appen (lista + skapande), och att jag kan förklara arvet under huven i IDE:n."

> **README Q1 (inkapsling):** "`owner`/`balance` är `private`. Main når dem via getters/metoder — inte luckan. Publikt fält hade låtit någon hoppa förbi `withdraw`-regeln."

> **README Q2 (factory):** "`new Account(...)` står i `createAccount` i `AccountRegister` — inte utspritt i `Main`. Då hamnar varje konto i listan på samma sätt."

> **README Q3 (stegkedja):** "Ett menyval = inmatning → vilket objekt (`findAccount`) → vilken metod (`deposit`/`withdraw`) → vad som skrivs ut."

---

## 📝 Examination

**Examination 1 tilldelas nu.** Du ska ha **eget publikt GitHub-repo** för Kontoappen (inte kurs-hubben, inte grupp). Vecka 41 (vecka 41): **samma vecka** lämnar du repo-länk i Moodle **och** muntlig redovisning (live **eller** video 4–8 min i IDE:n). Saknas en del = inte klart.

| Leverans | Vad |
|----------|-----|
| **Repo** | Minst tre `.java`, Klart-check i [examination_1_kontoappen.md](../../examination_1_kontoappen.md), README Q1–Q3 + AI-reflektion, ≥5 commits |
| **Redovisning** | Samma repo, IDE öppen, **2–3 delar** (minst en OOP — t.ex. `private`, `createAccount`, `withdraw`-spärr; VG: `SavingsAccount`) |
| **VG i koden** | `SavingsAccount extends Account`, extra metod, **används** via register/meny — inte bara en fil som ligger där |

Det här paketet ger dig **README-utkast**, **exam-repo-start** och **plan för inspelningen** — inte en färdig inlämning. Appen färdigställs under examinationsveckan.

## 🏁 Nästa steg

När du är klar här: vecka 41 — Examination 1 (*publiceras i* `13-exam-1/`). Repetera [examination_1_kontoappen.md](../../examination_1_kontoappen.md) innan deadline.
