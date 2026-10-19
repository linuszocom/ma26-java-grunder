# 17 — Lista i Register (`läggTill` + `listaAlla`)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** pedagogisk **vecka 43, pass 1** — `Register` håller objekten: `private List<Medlem>`, `läggTill`, `listaAlla` (skriv ut namn + nummer). Efteråt: två medlemmar i registret, utskrift av listan, och du pekar på listan **i `Register`**, inte i `Main`.

**Förkunskaper:** Tre filer + `Medlem`-skelett (private, konstruktor, getters) från [15-tre-klasser](../../vecka-42/15-tre-klasser/). List-/ArrayList-idé från [06-arraylist-scanner](../../vecka-38/06-arraylist-scanner/) och [10-inkapsling](../../vecka-40/10-inkapsling/).

**Omfång:** Lista av `Medlem` **i** `Register`. Metoder `läggTill` + `listaAlla`. Två hardkodade medlemmar från `Main`. **Ingen** `sökNamn`, **ingen** meny/`Scanner`, **ingen** factory, **inget** arv. **Inte** Git-fokus i det här paketet.

---

## 🗺️ Veckans körschema (v7 — tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Lista i Register (denna mapp)** | Max ~15 min: skumma [01 — Teoriguide](./01-teoriguide.md) (listan i Register, `List` vs `ArrayList`, `läggTill` / `listaAlla`) — **flipped** | Fält i `Register`, två medlemmar, konsolutskrift | Välj ditt spår nedan (~3–5 h) |
| **Pass 2 — Sök och meny** | Max ~15 min: [01 — Teoriguide](../18-sok-meny/01-teoriguide.md) | `sökNamn` + Scanner-meny 1–4 | [18-sok-meny](../18-sok-meny/) |
| **Pass 3 — README + start Exam 2** | Max ~15 min: läs [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md) + [01](../19-exam2-start/01-teoriguide.md) | README-utkast, start examinationskod | [19-exam2-start](../19-exam2-start/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (flytta listan → `läggTill` + `listaAlla` + två medlemmar)
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
*Om du blev klar snabbt — frivilligt. Exam 2 ger IG/G, ingen VG:*
- [ ] **Stretch i övningarna:** Tredje medlem + bevis `size`/antal rader i konsolen (se [03 — Övningar](./03-ovningar.md))
- [ ] **README-träning:** En mening: *“Listan ligger i Register.java — fältet medlemmar — inte i Main.”* (Exam 2-lista-förebåd)
- [ ] **Dokumentera:** Skillnad `List<Medlem>` (skylt) vs `new ArrayList<>()` (lådans innehåll)

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Listans hem:** "`private List<Medlem> medlemmar` bor i `Register`. `Main` har en `Register`-referens och anropar metoder — inte en egen lista."

> **List vs ArrayList:** "Fälttypen är `List<Medlem>`. Jag skapar med `new ArrayList<>()`. Jag deklarerar inte fältet som `ArrayList`."

> **läggTill + listaAlla:** "`läggTill` stoppar in en `Medlem` med `add`. `listaAlla` loopar och skriver namn + nummer via getters. Efter två `läggTill` och `listaAlla` syns två rader i konsolen."

---

## 📝 Examination

Det här paketet träffar **Examination 2 (Medlemsregistret)** — **listan** i `Register`, lägg till, lista alla (namn + nummer). Sök och meny kommer i [18-sok-meny](../18-sok-meny/). Skelettet du bygger vidare på: [15-tre-klasser](../../vecka-42/15-tre-klasser/).

**Exam-förebåd (lista):** När någon frågar *“Var ligger listan?”* pekar du i `Register.java` på fältet — inte i `Main`.

## 🏁 Nästa steg

När du är klar här: [18-sok-meny](../18-sok-meny/) — `sökNamn` + textbaserad meny. Därefter [19-exam2-start](../19-exam2-start/). Saknar du tre filer / `Medlem`-mur: [15-tre-klasser](../../vecka-42/15-tre-klasser/).
