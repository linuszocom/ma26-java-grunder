# 11 — Factory, sök och meny (`createAccount` / `findAccount`)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** Skapande-mönster (factory) — `createAccount` som enda ställe för `new Account`. Sök på ägare med `findAccount` (träff / `null`). Meny i `Main` med `Scanner`: skapa, lista, sätt in, ta ut, avsluta — **vecka 40, pass 2**.

**Omfång:** Tre filer: `Account.java`, `AccountRegister.java`, `Main.java`. `List<Account>` i registret. `new Account` **bara** i `createAccount`. Meny 1–5. Bygger på inkapslad `Account` + lista från [10-inkapsling](../10-inkapsling/). Ingen `SavingsAccount`, inget arv, ingen Git i övningarna här.

---

## 🗺️ Veckans körschema (v4 — pass 10, 11, 12)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Inkapsling och objektlista** | *Publiceras i* [10-inkapsling](../10-inkapsling/) | `private`, konstruktor, getters, `List<Account>` | [10-inkapsling](../10-inkapsling/) |
| **Pass 2 — Factory, sök och meny (denna mapp)** | Max ~15 min: läs [01 — Teoriguide](./01-teoriguide.md) (factory, `findAccount`, meny 1–5) — **flipped** | `createAccount`, sök, meny mot rätt objekt | Välj ditt spår nedan (~3–5 h) |
| **Pass 3 — Arv (VG) och start Exam 1** | Max ~15 min: läs [examination_1_kontoappen.md](../../examination_1_kontoappen.md) + [01 — Teoriguide](../12-arv-exam1-start/01-teoriguide.md) | `SavingsAccount`, README, muntlig form | [12-arv-exam1-start](../12-arv-exam1-start/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (refaktorera `new` → `createAccount` · mini-meny två konton)
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
- [ ] **README-träning (Exam 1 Q2):** Skriv 2–4 meningar: var `new Account` står i din kod, varför inte i `Main`, vad som händer om någon glömmer `add` efter `new`
- [ ] **Stegkedja (Exam 1 Q3):** Beskriv menyval 4 (ta ut) som kedja: inmatning → `findAccount` → `withdraw` → utskrift
- [ ] **Robust sök:** Testa `findAccount("alva")` när ägaren är `"Alva"` — förklara `equalsIgnoreCase` i README-utkast
- [ ] **Nästa paket:** [12-arv-exam1-start](../12-arv-exam1-start/) när factory + meny sitter

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Factory:** "`new Account` skapas bara i `createAccount` i `AccountRegister`. Main anropar `register.createAccount(owner, startBalance)` — Main skapar inte konton själv. Då hamnar varje konto i listan och Exam Q2 är uppfyllt."

> **Sök:** "`findAccount(owner)` loopar listan, jämför `getOwner()` med `equalsIgnoreCase`, returnerar pekaren vid träff eller `null` vid miss. Innan `deposit`/`withdraw` kollar jag `if (found != null)`."

> **Meny mot rätt objekt:** "Main läser val och namn/belopp. Registret hittar objektet. Transaktionen körs på det objektet — inte på hårdkodat index 0."

---

## 📝 Examination

Det här paketet träffar **Examination 1 (Kontoappen) — README fråga 2 (factory)** och kärnflödet skapa/lista/sätt in/ta ut:

- **`createAccount`** — skapande-mönster; `new Account` ska synas där, **inte** i `Main`
- **`findAccount`** — hitta rätt konto innan `deposit` / `withdraw`
- **Meny 1–5** — samma fem val som examinationen (avsluta på 5)

Inkapsling och README Q1 kommer från [10-inkapsling](../10-inkapsling/). Arv (VG) och full Exam-start i [12-arv-exam1-start](../12-arv-exam1-start/).

---

## 🏁 Nästa steg

När du är klar här: [12-arv-exam1-start](../12-arv-exam1-start/) — eller börja ditt Exam 1-repo om du redan har factory + meny under kontroll. Saknar du `private` / konstruktor / lista: gör [10-inkapsling](../10-inkapsling/) först.
