# 09 — Transaktioner (`deposit` / `withdraw`)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** Metoder på objekt — `deposit` och `withdraw`, kort om `this`, uttagsregeln — **vecka 39, pass 3**.  
Pass 1 och pass 2 i samma pedagogiska vecka har egna mappar — se körschemat.

**Omfång:** Instansmetoder på `Account` (`deposit(amount)`, `withdraw(amount)`). Fälten `owner` och `balance`. Kort `this`. Regel: för stort uttag → **saldo oförändrat** + tydligt meddelande. Bygger vidare på `Account` från [08-klasser-objekt](../08-klasser-objekt/). Ingen `private`, ingen konstruktor, inga getters, ingen `AccountRegister`, ingen meny, ingen Git i grupp.

---

## 🗺️ Veckans körschema

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Vecka 39, pass 1 — Git och GitHub** | *Publiceras i* [07-git-github](../07-git-github/) | add → commit → push, eget repo | [07-git-github](../07-git-github/) |
| **Vecka 39, pass 2 — Klass och objekt (`Account`)** | *Publiceras i* [08-klasser-objekt](../08-klasser-objekt/) | Klass vs objekt, fält, `new` | [08-klasser-objekt](../08-klasser-objekt/) |
| **Vecka 39, pass 3 — `deposit` / `withdraw`** | Max ~15 min: läs [01 — Teoriguide](./01-teoriguide.md) (metod på objekt, `this`, uttagsregeln) | Anropa `deposit`/`withdraw`, förklara stoppat uttag | Välj ditt spår nedan (~3–5 h) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (deposit + stoppat uttag)
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
- [ ] **Stretch i övningarna:** `printInfo()` och/eller `boolean withdraw` (saldo oförändrat + meddelande + `return false`/`true`) — se [03 — Övningar](./03-ovningar.md)
- [ ] **README-träning:** Skriv två meningar: vad som händer när uttaget är större än saldot, och varför du anropar `nora.deposit(50)` på objektet — inte en `static`-metod i `Main`
- [ ] **Dokumentera:** En mening om `this.balance` vs parametern `amount` — vad som hör till *objektet* och vad som kom in i anropet

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Metod på objekt:** "`deposit` och `withdraw` bor i `Account`. Jag anropar dem med `objekt.metod(belopp)`. Det är det här objektets `balance` som ändras — inte en global variabel i `Main`."

> **Uttagsregeln:** "Om beloppet är större än saldot ska `withdraw` *inte* ändra `balance`. Den ska skriva ett tydligt meddelande. Saldo oförändrat + meddelande — det är Exam 1-kravet."

> **`this` (kort):** "`this.balance` är saldot hos just det objekt som fick anropet. Parametern `amount` är beloppet som skickades in."

---

## 📝 Examination

Det här paketet träffar **Examination 1 (Kontoappen) — uttagsregeln**: `deposit` ökar `balance`; för stort `withdraw` **ändrar inte** `balance` och ger ett meddelande. Du ska kunna anropa metoderna på rätt objekt och förklara stoppet muntligt. (Inkapsling, konstruktor, factory och meny kommer i senare paket.)

## 🏁 Nästa steg

När du är klar här: vecka 40 — inkapsling, konstruktor och lista (*publiceras i nästa del*). Se till att [08-klasser-objekt](../08-klasser-objekt/) sitter innan du bygger vidare.
