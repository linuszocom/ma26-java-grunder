# 05 — Metoder

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** Metoder, parametrar, returvärde och anrop — **vecka 38, pass 2**.  
Pass i samma kalendervecka utan filer här får en rad i körschemat (*publiceras i nästa del*).

**Omfång:** `static`-metoder i samma klass (`Main.java`). Parametrar och `return`. `void` och metoder som ger tillbaka värde. Loopar från föregående paket är OK. Ingen egen klass (`Account`), inget objekt-OOP, ingen `ArrayList` krävs här.

---

## 🗺️ Veckans körschema

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Vecka 38, pass 1 — Loopar och meny-val** | *Publiceras i* [04-loopar-meny](../04-loopar-meny/) | `while`, `for`, meny-loop | [04-loopar-meny](../04-loopar-meny/) |
| **Vecka 38, pass 2 — Metoder** | Max ~15 min: läs [01 — Teoriguide](./01-teoriguide.md) (metod, parameter, return, anrop) | Flytta logik ur `main`, parametrar, `return` | Välj ditt spår nedan (~3–5 h) |
| **Vecka 38, pass 3 — Arrayer, ArrayList och Scanner** | Skumma samlingar i [06 — Teoriguide](../06-arraylist-scanner/01-teoriguide.md) (~15 min) | Array, `ArrayList`, `Scanner` text + tal | [06-arraylist-scanner](../06-arraylist-scanner/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (fraktrefaktorering + enhetsomvandling + BMI-liknande)
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
- [ ] **Stretch i övningarna:** Lägg till en `void`-metod `skrivOrderSammanfattning(...)` som tar ordernummer och totalpris som parametrar och skriver en rad — anropa den från en `for`-loop över tre ordrar (se [03 — Övningar](./03-ovningar.md))
- [ ] **README-träning:** Skriv två meningar: varför `deposit`-liknande logik senare blir en metod med parameter, och varför du sparar returvärdet i en variabel i stället för att bara `println` inuti metoden
- [ ] **Dokumentera:** Byt scenario i uppgift 2 (t.ex. tum till cm) — samma metod-signatur-mönster, ny formel. En mening: vad som är **samma struktur** och vad som bara är **ny matematik**

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Metod:** "En metod är ett namngivet kodblock utanför `main` som gör ett jobb. Jag anropar det med `metodnamn(...);`. Samma kropp kan köras många gånger utan att kopiera rader."

> **Parameter och retur:** "Parametrar i parentesen tar emot data när metoden anropas. `return` skickar tillbaka ett värde till den som anropade — om returtypen inte är `void`. Argument i anropet måste matcha antal och typ."

> **Varför metoder:** "Jag undviker duplicerad kod, ändrar logiken på ett ställe och kan testa en beräkning separat. I Kontoappen blir insättning, uttag och getters metoder — samma idé som min `return`-metod idag, fast på ett kontoobjekt senare."

---

## 📝 Examination

Det här paketet förbereder **Examination 1 (Kontoappen)**. Där skriver du metoder som `deposit` och `withdraw` med parametrar, och getters som **returnerar** värden — du ska kunna förklara *varför* logiken inte ska ligga kopierad tre gånger i `main`. Idag: bara `static`-metoder i `Main`; klassen `Account` kommer i senare veckor.

## 🏁 Nästa steg

När du är klar här: [06-arraylist-scanner](../06-arraylist-scanner/) — arrayer, `ArrayList` och `Scanner`.
