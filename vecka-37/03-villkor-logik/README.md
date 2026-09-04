# 03 — Villkor och logik

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** Fredag 11/9 — `if` / `else` / `else if`, jämförelser (`>`, `<`, `==`, `!=`, `>=`, `<=`), logiska operatorer (`&&`, `||`, `!`), död gren och `=` vs `==`.  
Värden hårdkodas i `main` — ingen loop, ingen `Scanner`, inga egna metoder utöver `main`.

---

## 🗺️ Veckans körschema

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Tisdag 8/9 — Datalogiskt tänkande + JDK/IDE** | Inget att läsa i förväg (kursstart) | Sekvens, IDE, första körning | [01-datalogiskt-ide](../01-datalogiskt-ide/) |
| **Onsdag 9/9 — Variabler och datatyper** | Skumma variabler i [02:s 01](../02-variabler-datatyper/01-teoriguide.md) (~15 min) | Burkar, typer, utskrift | [02-variabler-datatyper](../02-variabler-datatyper/) |
| **Fredag 11/9 — Villkor och logik (denna mapp)** | Skumma villkor i [01-teoriguide](./01-teoriguide.md) (~15 min) | Grenar, jämförelser, `&&` \|\| `!` | Välj ditt spår nedan (~3–5 h) |

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
- [ ] **Stretch i övningarna:** Lägg till en extra `else if`-gren i [03 — Övningar](./03-ovningar.md) (t.ex. fjärde temperaturzon), eller använd **nästlade `if`** (ett villkor inuti en gren) — fortfarande hårdkodade värden, ingen loop
- [ ] **README-träning:** Skriv tre meningar: vad en död gren är, skillnaden `=` vs `==` i `if`, när du väljer `&&` framför `||`
- [ ] **Dokumentera:** Rita på papper en `else if`-stege för ett scenario du själv hittat på — markera vilken gren som körs för ett givet värde

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Villkor (`if`):** "Ett `if` är en fråga som blir true eller false. Programmet tar bara grenen där svaret är true — annars hoppar det över eller tar `else`."

> **Logiska operatorer:** "`&&` kräver att båda sidor är true. `||` räcker med en true. `!` vänder — true blir false och tvärtom."

> **Metoden:** "Skriv frågan i parentesen. Peka: kan den här grenen nås? Jämför med `==`, tilldela med `=`."

---

## 📝 Examination

**Exam 1 (Kontoappen)** bygger på villkor: uttag stoppas när beloppet är större än saldot, menyn ska reagera på rätt val. Själva **meny-loopen** (`while` + `Scanner`) kommer i vecka 2 — här lär du dig grenarna som loopen sen ska anropa.

---

## 🏁 Nästa steg

När du är klar här: vecka 2 börjar med loopar och meny-val — samma villkor, men programmet frågar om och om igen tills användaren avslutar.
