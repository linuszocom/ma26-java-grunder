# 19 — README + start Exam 2

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v43 Pass 3 — datalogiskt tänkande för registret (data → klasser → meny), Exam 2-krav (meny, sök träff/miss, ≥6 commits, alla syns, gemensamt publikt repo), gemensam `README.md` (datalogiskt, klass/objekt, Git i grupp, problem+lösning, AI), och **start/fortsätt** examinationskod i **grupprepots**.  
Pass 1 och Pass 2 i samma pedagogiska vecka har egna mappar — se körschemat.

**Flipped (Pass 3):** Ja — läs **[Examination 2 — Medlemsregistret](../../examination_2_medlemsregistret.md)** (~15 min) **innan** du kodar här. Du ska känna igen Klart-check, README-frågorna och vad som **inte** ingår (ingen VG, ingen muntlig).

**Förkunskaper:** Gemensamt grupprepo + pull/push ([14-git-team](../../vecka-42/14-git-team/)). Tre filer `Medlem` / `Register` / `Main` ([15-tre-klasser](../../vecka-42/15-tre-klasser/)). Konflikt/dokumenterat problem ([16-merge-konflikt](../../vecka-42/16-merge-konflikt/)). Lista i Register ([17-lista-register](../17-lista-register/)). Sök + meny ([18-sok-meny](../18-sok-meny/)).

**Omfång:** README-utkast Q1–Q3 + problem + AI. Gap mot Klart-check. Påbörjad examinationskod i **grupprepo**. **Ingen** ny Java-syntax. **Ingen** factory/arv. **Ingen** `Account`-kopia. **Ingen** muntlig redovisning för Exam 2. Betyg **IG/G** — **ingen VG**.

---

## 🗺️ Veckans körschema (v7 — alla tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Lista: lägg till och lista** | *Publiceras i* [17-lista-register](../17-lista-register/) | `läggTill`, `listaAlla`, `List<Medlem>` | [17-lista-register](../17-lista-register/) |
| **Pass 2 — Sök och meny** | *Publiceras i* [18-sok-meny](../18-sok-meny/) | Sök träff/miss, Scanner-meny | [18-sok-meny](../18-sok-meny/) |
| **Pass 3 — README + start Exam 2 (denna mapp)** | Max ~15 min: läs [Examination 2 — Medlemsregistret](../../examination_2_medlemsregistret.md) + skumma [01 — Teoriguide](./01-teoriguide.md) | Exam 2-krav, README-utkast, fortsätt i grupprepo | Välj ditt spår nedan (~3–5 h) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (README-utkast + Klart-check mot grupprepo)
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

### 🟣 3. Du vill fördjupa dig (Stretch — inom G)
*Exam 2 ger IG/G — ingen VG. Stretch här = polera README och historik, inte ett VG-spår.*
- [ ] **Stretch i övningarna:** fyll **problem + AI** med konkret fil/händelse och minst ett exempel där ni **ändrade** AI-förslag (se [03 — Övningar](./03-ovningar.md))
- [ ] **README-träning:** skriv om varje vag fras (“vi samarbetade bra”) till en mening med **steg, fil eller commit**
- [ ] **Dokumentera:** planera att **alla** syns under Commits innan v8 — inte sex dump-commits sista kvällen

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Datalogiskt (README Q1):** "Vi bröt ner registret i steg innan kod: vilken data (namn, nummer) → vilka klasser (`Medlem`, `Register`, `Main`) → vilken meny (lägg till, lista, sök, avsluta). Det är datalogiskt tänkande — inte ‘allt i Main på en gång’."

> **Klass/objekt (README Q2):** "`Medlem` är klassen — mallen. Ett objekt är en konkret medlem i listan, skapad med `new`. Variabler bara i `Main` räcker inte: då saknas objektansvar och `Register` kan inte hålla `List<Medlem>`."

> **Git i grupp (README Q3):** "Ändra → `add` → `commit` → `pull` före `push`. Vi delar filansvar och synkar ofta så vi inte skriver över varandra. Alla syns under Commits."

> **Exam 2 i en mening:** "Gruppens konsolapp: `Medlem`/`Register`/`Main`, meny med Scanner, sök träff och miss, gemensamt publikt repo, minst 6 commits där alla syns, README Q1–Q3 + problem + AI — betyg IG eller G, ingen VG, ingen muntlig."

---

## 📝 Examination

**Examination 2 tilldelas nu.** Ni fortsätter i **gruppens publika GitHub-repo** (inte Exam 1-repot, inte kurs-hubben).  
**Inlämning:** GitHub-länk i Moodle under **examinationsveckan (v8)** — deadline enligt schema. **Ingen muntlig redovisning** för Exam 2.

| Leverans | Vad |
|----------|-----|
| **Repo** | Klart-check i [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md): tre `.java`, meny, sök träff+miss, ≥6 commits, alla syns, README |
| **Moodle** | Länk till grupprepots — **v44** |
| **Betyg** | **IG / G** — **ingen VG** |

Det här paketet ger dig **README-utkast**, **Klart-check i huvudet** och **påbörjad examinationskod** — inte en färdig inlämning. Appen färdigställs under examinationsveckan.

## 🏁 Nästa steg

När du är klar här: vecka 44 — Examination 2 (*publiceras i* `20-exam-2/`). Repetera [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md) innan deadline. Inga nya teknikmoment i v44 — färdigställ + lämna in.
