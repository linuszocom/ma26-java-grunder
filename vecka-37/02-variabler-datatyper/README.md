# 02 — Variabler och datatyper

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** Variabler, tilldelning och de fyra datatyperna (`int`, `double`, `String`, `boolean`) — **onsdag 9/9**.

**Omfång:** Deklaration, tilldelning, `System.out.println`. Bara `main`. Ingen `if`, ingen loop, ingen `Scanner`, inga egna metoder.

---

## 🗺️ Veckans körschema

| Dag / Tillfälle | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Tisdag 8/9 — Datalogiskt tänkande + JDK/IDE** | Inget att läsa (kursstart). Ha GitHub + IDE + JDK 21. | Data, handlingar, ordning + första körningen | [01-datalogiskt-ide](../01-datalogiskt-ide/) |
| **Onsdag 9/9 — Variabler och datatyper** | Max ~15 min: läs [01 — Teoriguide](./01-teoriguide.md) (variabler + datatyper) | Deklaration, tilldelning, fyra typer, utskrift | Välj ditt spår nedan (~3–5 h) |
| **Fredag 11/9 — Villkor och logik** | Max ~15 min: [03:s teoriguide](../03-villkor-logik/01-teoriguide.md) | if/else, jämförelser, logik | [03-villkor-logik](../03-villkor-logik/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (lagerinventering + väderstation)
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
- [ ] **Stretch i övningarna:** Byt alla värden i väderstationsprogrammet till ett träningspass (samma fyra typer, nya etiketter) — se [03 — Övningar](./03-ovningar.md)
- [ ] **README-träning:** Skriv tre meningar i anteckningar: vad en variabel är, hur du väljer mellan `int` och `double`, varför `String` kräver citattecken
- [ ] **Dokumentera:** Kör samma variabelnamn två gånger med olika värden (tilldela om) och förklara i en mening varför konsolen visar det *sista* värdet

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När mappen är klar ska du kunna återge dessa med egna ord:

> **Variabel:** "En variabel är en namngiven plats i minnet för ett värde. Deklaration skapar platsen. Tilldelning med `=` fyller den. `System.out.println` tittar på innehållet — det tömmer inte platsen."

> **Datatyper:** "Heltal → `int`. Decimal → `double`. Text → `String` (med citattecken). Ja/nej i Java → `boolean` (`true` eller `false`). Fel typ ger kompileringsfel — javac vägrar blanda innehåll."

> **Metoden:** "Deklarera först, tilldela sedan, skriv ut sist. Läs felmeddelandet: *cannot find symbol* = platsen finns inte. *might not have been initialized* = platsen är tom."

---

## 📝 Examination

Det här paketet är grunden till **Java-syntax** i **Examination 1 (Kontoappen)**. Där möter du `int`/`double` för saldo, `String` för ägare och `boolean` i villkor — men villkoren kommer i [03-villkor-logik](../03-villkor-logik/). Idag: bara spara och skriva ut värden korrekt.

## 🏁 Nästa steg

När du är klar här: [03-villkor-logik](../03-villkor-logik/) (*publiceras i nästa del*) — `if`/`else` och logiska operatorer.
