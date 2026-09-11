# 06 — Arrayer, ArrayList och Scanner

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v2 Pass 3 — array (`index`, `length`, loopa ut), `ArrayList` (`add`, `get`, skriv ut lista), `Scanner` (`nextLine`, blanda text och tal). Efter passet ska du kunna kombinera array + lista + inläsning i samma `Main`.

**Förkunskaper:** [04 — Loopar och meny-val](../04-loopar-meny/) (`for`, `while`, `Scanner.nextInt()`). [05 — Metoder](../05-metoder/) (`static`-metoder, parametrar, `return` — valfritt men bra i övning 3).

**Omfång:** Bara `Main.java`. Primitiva och `String` i array/lista — **ingen** objektlista (`ArrayList<Account>` kommer senare). Ingen Git i övningarna här.

---

## 🗺️ Veckans körschema (v2 — alla tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Loopar och meny-val** | Skumma loopar i [04 — Teoriguide](../04-loopar-meny/01-teoriguide.md) (~15 min) | `while`, `for`, meny-loop, `Scanner.nextInt()` | [04-loopar-meny](../04-loopar-meny/) |
| **Pass 2 — Metoder** | Skumma metoder i [05 — Teoriguide](../05-metoder/01-teoriguide.md) (~15 min) | Parametrar, retur, `void` | [05-metoder](../05-metoder/) |
| **Pass 3 — Arrayer, ArrayList och Scanner (denna mapp)** | Skumma samlingar i [01 — Teoriguide](./01-teoriguide.md) (~15 min, flipped) | Array, `ArrayList`, `Scanner` text + tal | Välj ditt spår nedan (~3–5 h) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (packlista · spellista · inköpslista)
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
- [ ] **Stretch i övningarna:** I inköpslistan — läs in **tre** rader (produkt + antal) i en `while`-loop tills användaren skriver `klar` som produktnamn. Skriv ut hela listan sist med `for` + `get`
- [ ] **README-träning:** Skriv två meningar: skillnad array vs `ArrayList`, och varför `nextInt()` följt av `nextLine()` kan ge tomt namn
- [ ] **Metod:** Flytta utskrift av en `List<String>` till en `static void skrivLista(List<String> rader)` — anropa från `main` (bygg vidare på [05 — Metoder](../05-metoder/))

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Array:** "En array har fast storlek från början. Index börjar på 0. `length` är antal fack — sista index är length minus 1. Jag loopar med `for (int i = 0; i < tal.length; i++)` och läser `tal[i]`."

> **ArrayList:** "Listan växer med `add`. Jag deklarerar `List<String>` och skapar med `new ArrayList<>()`. `get(i)` läser, `size()` räknar. Samma 0-index som array — men storleken följer add."

> **Scanner blandat:** "`nextLine()` läser en hel rad text. `nextInt()` läser ett tal. Efter `nextInt()` ligger Enter kvar — en extra `nextLine()` som jag inte sparar slänger radbrytningen innan nästa riktiga `nextLine()`."

---

## 📝 Examination

**Exam 1 (Kontoappen)** använder en **lista av konton** i `AccountRegister` — samma idé som din spellista idag, fast med objekt senare i kursen. Meny + `Scanner` + loop kommer från [04](../04-loopar-meny/). Metoder från [05](../05-metoder/) blir `deposit`, getters och listlogik.

**Exam 2 (Medlemsregistret)** bygger vidare: `Register` håller medlemmar i en lista, `Main` läser namn och nummer från konsolen. Det du tränar här — lista, loop, `Scanner`, indexfällor — är direkt förberedelse; klasser och Git kommer i senare veckor.

---

## 🏁 Nästa steg

När du är klar här: vecka 39 i kursen — klasser och objekt (`Account`). Behöver du fräscha loopar eller metoder: [04-loopar-meny](../04-loopar-meny/) · [05-metoder](../05-metoder/).
