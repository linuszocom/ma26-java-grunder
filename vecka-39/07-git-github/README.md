# 07 — Git & GitHub (eget repo)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** vecka 39, **Pass 1** — versionshantering, commit, lokalt vs GitHub, `git add` → `git commit` → `git push`, publikt repo, fliken Commits.

**Förkunskaper:** Du kan skapa och köra ett enkelt Java-program i IDE:n ([vecka 38](../../vecka-38/) — `Main`, konsol). Ingen OOP krävs i det här paketet.

**Omfång:** Individuell Git. Eget publikt repo. **Ingen** `git pull`, **inget** grupprepo, **inga** branches/PR, **inga** klasser/objekt här.

---

## 🗺️ Körschema (vecka 39)

| Pass | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Git & GitHub (denna mapp)** | Skapa konto på [github.com](https://github.com) om du saknar (~10–15 min). Logga in. Skumma [01 — Teoriguide](./01-teoriguide.md) max ~15 min (flipped). | Versionshantering, add → commit → push, Commits-fliken | Välj ditt spår nedan (~3–5 h) |
| **Pass 2 — Klasser och objekt** | Max ~15 min: [01 — Teoriguide](../08-klasser-objekt/01-teoriguide.md) | `Account`, objekt, fält | [08-klasser-objekt](../08-klasser-objekt/) |
| **Pass 3 — Transaktioner** | Max ~15 min: [01 — Teoriguide](../09-transaktioner/01-teoriguide.md) | `deposit` / `withdraw`, stoppat uttag | [09-transaktioner](../09-transaktioner/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (HelloWorld → add → commit → push → Commits)
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
- [ ] **Stretch i övningarna:** andra och tredje commit i [03 — Övningar](./03-ovningar.md) med begripliga meddelanden
- [ ] **README-träning:** i övningsrepot — tre meningar: vad en commit är, Git vs GitHub, varför Exam 1 kräver publikt repo + synlig historik
- [ ] **Dokumentera:** klistra in din repo-URL + beskriv vad du ser under **Commits** (meddelande, författare, tid)

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När Pass 1 är klart ska du kunna återge dessa med egna ord:

> **Varför Git finns:** "Utan versionshantering har jag bara 'senaste filen på disken'. Git sparar en historik av ögonblicksbilder så jag (och examinationen) kan se *vad* som ändrats och *när*."

> **Commit:** "En commit är en sparad ögonblicksbild av projektet med ett meddelande om vad som ändrats. Den blir en punkt i historiken — fortfarande på min dator tills jag pushar."

> **Metoden:** "Har jag en liten, begriplig ändring? Då: `git add` de filerna, `git commit -m \"tydligt meddelande\"`, sedan `git push` — och jag verifierar under Commits på GitHub."

---

## 📝 Examination

**Exam 1 (Kontoappen)** lämnas in som **eget publikt** GitHub-repo. Minst **5 commits** med begripliga meddelanden (`add` → `commit` → `push`). Fliken **Commits** ska visa historiken. Det du tränar här — kedjan och publikt repo — är samma Git-krav som examinationen använder (OOP kommer i Pass 2–3 och senare veckor).

---

## 🏁 Nästa steg

När Pass 1-målen sitter: Pass 2 [`08-klasser-objekt`](../08-klasser-objekt/) (*publiceras i nästa del*). Behöver du fräscha Java-grunder: [vecka 38](../../vecka-38/).
