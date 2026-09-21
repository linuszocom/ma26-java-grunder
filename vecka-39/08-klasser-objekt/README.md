# 08 — Klasser och objekt (`Account`)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** v3 Pass 2 — klass som mall, objekt som instans, fält `owner` / `balance`, `new`, filen `Account.java`. Efter passet ska du kunna förklara klass vs objekt och skapa minst ett `Account`-objekt som du skriver ut fält från.

**Förkunskaper:** Variabler, `main`, `System.out.println`. Metoder från [05-metoder](../../vecka-38/05-metoder/) är bra bakgrund men krävs inte för att skapa fält. Git från Pass 1 behövs **inte** i övningarna här.

**Omfång:** `Account.java` + `Main.java`. Engelska namn. Fält som du kan sätta och läsa (`owner`, `balance`). **Ingen** `deposit` / `withdraw` än (det är Pass 3). **Ingen** `private`, konstruktor, factory eller lista av objekt.

---

## 🗺️ Veckans körschema (v3 — alla tre pass)

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Git och GitHub** | *Publiceras i* [07-git-github](../07-git-github/) | `add` → `commit` → `push`, eget repo | [07-git-github](../07-git-github/) |
| **Pass 2 — Klasser och objekt (denna mapp)** | Max ~15 min: skumma [01 — Teoriguide](./01-teoriguide.md) (klass vs objekt, fält, `new`) | `Account.java`, skapa objekt, skriv ut fält | Välj ditt spår nedan (~3–5 h) |
| **Pass 3 — Transaktioner (`deposit` / `withdraw`)** | Max ~15 min: [01 — Teoriguide](../09-transaktioner/01-teoriguide.md) | Metoder på objekt, stoppat uttag | [09-transaktioner](../09-transaktioner/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (lösa variabler → `Account` + två objekt)
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
- [ ] **Stretch i övningarna:** Tredje `Account`-objektet + bevis att ändring på ett objekt inte rör de andra (se [03 — Övningar](./03-ovningar.md))
- [ ] **README-träning:** Skriv två meningar du kan använda inför Exam 1: vad är klassen `Account`, och vad är *ett* kontoobjekt?
- [ ] **Dokumentera:** En mening om varför filen måste heta `Account.java` när klassen heter `Account`

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Klass vs objekt:** "Klassen `Account` är mallen i filen. Ett objekt är en konkret instans i minnet efter `new Account()`. Flera objekt delar samma mall men har egna värden i fälten."

> **Fält och `new`:** "Fälten `owner` och `balance` hör till varje objekt. Jag skapar objektet med `new`, sätter fälten via punkten (`konto.owner = ...`) och skriver ut fälten — inte bara variabelnamnet."

> **Fil vs klass:** "`public class Account` måste ligga i filen `Account.java`. Fel filnamn ger kompileringsfel. Klassen är inte samma sak som `Main`."

---

## 📝 Examination

Det här paketet är första steget mot **Examination 1 (Kontoappen)**. Där ska du ha en riktig `Account.java`. Idag: skapa klassen, skapa objekt med `new`, visa `owner` och `balance`. Senare kommer `private`, konstruktor, `deposit` / `withdraw` och register — **inte** i den här mappen.

## 🏁 Nästa steg

När du är klar här: [09-transaktioner](../09-transaktioner/) — metoder på objekt (`deposit` / `withdraw`) (*publiceras i nästa del*).
