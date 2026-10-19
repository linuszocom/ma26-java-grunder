# 18 — Sök och meny (`sökNamn` + Scanner 1–4)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v43 Pass 2 — sök på namn (**träff / saknas**) i `Register`, och textmeny i `Main` med `Scanner` tills avsluta (val **1–4**). **Vecka 43, pass 2.** Flipped: ja — skumma teoriguiden innan passet.

**Förkunskaper:** Lista i `Register`, `läggTill` och `listaAlla` från [17-lista-register](../17-lista-register/). Tre filer och `Medlem`-mur från [15-tre-klasser](../../vecka-42/15-tre-klasser/). Meny-loop/`Scanner` från [04-loopar-meny](../../vecka-38/04-loopar-meny/).

**Omfång:** `public void sökNamn(String namn)` i `Register` (for-each, `equalsIgnoreCase`, hit → utskrift + `return`, miss → `"Medlemmen saknas"` efter loopen). `Main`: `while` + `Scanner` + **switch expression** (`case n ->`) med 1 lägg till · 2 lista · 3 sök · 4 avsluta. Exam-körning: två medlemmar, lista, sök träff, sök miss, avsluta — peka på `sökNamn`. **Ingen** README-uppsats (det är [19-exam2-start](../19-exam2-start/)). **Ingen** factory. **Inget** arv. **Ingen** VG-nivå (Exam 2 = IG/G).

---

## 🗺️ Veckans körschema (v7 — tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Lista i Register** | Max ~15 min: [01 — Teoriguide](../17-lista-register/01-teoriguide.md) | `List<Medlem>`, `läggTill`, `listaAlla` | [17-lista-register](../17-lista-register/) |
| **Pass 2 — Sök och meny (denna mapp)** | Max ~15 min: skumma [01 — Teoriguide](./01-teoriguide.md) (sök i Register, meny i Main, nextInt/nextLine) — **flipped** | `sökNamn` hit/miss + meny 1–4 + Exam-körning | Välj ditt spår nedan (~3–5 h) |
| **Pass 3 — README + start Exam 2** | Max ~15 min: läs Exam 2-krav (README-frågor) | Gemensam README, gap mot Klart-check | [19-exam2-start](../19-exam2-start/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (`sökNamn` + full meny-demo)
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

### 🟣 3. Du blev klar snabbt (Stretch — frivilligt, ingen VG här)
*Exam 2 ger IG/G — ingen VG. Stretch = mer ägarskap inom samma VAD:*
- [ ] **Stretch i övningarna:** sök med `"elsa"` när namnet är `"Elsa"`; sök i tom lista; ogiltigt menyval (se [03 — Övningar](./03-ovningar.md))
- [ ] **Peka högt:** Visa `sökNamn` i `Register.java` och säg: *“Här söker programmet — Main bara frågar.”*
- [ ] **Dokumentera:** En mening i anteckningar om varför `nextLine()` efter `nextInt()` behövs

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Sök:** "`sökNamn` bor i `Register`. Den loopar listan, jämför med `equalsIgnoreCase`, skriver träff och returnerar — eller skriver Medlemmen saknas efter loopen. Main anropar bara metoden."

> **Meny:** "`Main` har Scanner och while tills val 4. Switch med case n -> anropar läggTill, listaAlla eller sökNamn. Registret äger listlogiken — Main äger I/O."

> **Exam-körning:** "Två medlemmar via menyn, lista, sök träff, sök miss, avsluta. När någon frågar vilken metod som söker pekar jag på `sökNamn` i `Register.java`."

---

## 📝 Examination

Det här paketet träffar **Examination 2 (Medlemsregistret)** — **funktion**: sök på namn (träff + saknas) och meny 1–4 med `Scanner` tills avsluta. Du ska kunna **köra** två medlemmar → lista → hit → miss → exit och **peka** på sökmetoden. README-text och exam-start: [19-exam2-start](../19-exam2-start/). Lista-grunden: [17-lista-register](../17-lista-register/).

## 🏁 Nästa steg

När sök + meny sitter: [19-exam2-start](../19-exam2-start/) — gemensam README och gap mot Klart-check. Saknar du listan: [17-lista-register](../17-lista-register/). Saknar du tre filer: [15-tre-klasser](../../vecka-42/15-tre-klasser/).
