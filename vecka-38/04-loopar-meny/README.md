# 04 — Loopar och meny-val

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v2 T1 — `while`, `for`, `count++`, loop-villkor, oändlig vs avslutande loop, off-by-one (`<` vs `<=`), `Scanner` + `nextInt()` för menyval, meny-loop tills avsluta (`0`).

**Förkunskaper:** [03 — Villkor och logik](../vecka-37/03-villkor-logik/) (`if`, jämförelser). Variabler och datatyper: [02 — Variabler](../vecka-37/02-variabler-datatyper/).

---

## 🗺️ Veckans körschema

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Loopar och meny-val (denna mapp)** | Skumma loopar i [01-teoriguide](./01-teoriguide.md) (~15 min) | `while`, `for`, meny-loop, `Scanner` | Välj ditt spår nedan (~3–5 h) |
| **Pass 2 — Metoder** | Skumma metoder i nästa paket (~15 min) | Parametrar, retur, `void` | *Publiceras i nästa del* |
| **Pass 3 — Arrayer, ArrayList och Scanner** | Skumma samlingar i [06 — Teoriguide](../06-arraylist-scanner/01-teoriguide.md) (~15 min) | Array, `ArrayList`, `Scanner` text + tal | [06-arraylist-scanner](../06-arraylist-scanner/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md)
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
- [ ] **Stretch i övningar:** Lägg till en fjärde menyval i parkeringsautomaten (t.ex. “Visa total intäkt”) — fortfarande bara `main`, ingen `switch`, ingen `ArrayList`
- [ ] **README-träning:** Skriv tre meningar: skillnad `while` vs `for`, vad off-by-one betyder, varför `while (val != 0)` passar en meny
- [ ] **Dokumentera:** Rita på papper en meny-loop med tre val + avsluta — markera var programmet “hoppar tillbaka” och var det bryter

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **While:** "while frågar om villkoret är true, kör kroppen, hoppar tillbaka och frågar igen. När villkoret blir false lämnar loopen. Det är INTE ett if som bara körs en gång."

> **Meny-loop:** "while (val != 0) visar menyn, läser val med Scanner.nextInt(), hanterar valet, och loopar tills användaren väljer 0. Programmet stannar inte av sig själv — avslut är ett medvetet val."

> **For / off-by-one:** "for har start, villkor och steg i en rad. Jag väljer < eller <= utifrån om sista talet ska ingå. Ett steg fel ger en extra eller en saknad iteration."

---

## 📝 Examination

**Exam 1 (Kontoappen)** bygger på samma meny-loop: `Main` kör `while (val != 0)`, visar alternativ, läser `nextInt()`, anropar rätt logik (skapa konto, lista, sätt in, ta ut) tills användaren väljer avsluta. Här lär du dig **själva loopen och Scanner-valet** — klasser och factory kommer senare i kursen.

---

## 🏁 Nästa steg

När du är klar här: Pass 2 i samma pedagogiska vecka — metoder (`05-metoder`, publiceras separat). Behöver du fräscha villkor först: [03 — Villkor och logik](../vecka-37/03-villkor-logik/).
