# 15 — Tre klasser (`Medlem` / `Register` / `Main`)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa. Klicka på länkarna i webbläsaren.

**Den här mappen täcker:** vecka 42, **Pass 2**. Tre klasser med ett ansvar var. `Medlem` är entitetsmodellen. `Register` är domänens samlingsägare, tom i det här skedet. `Main` är applikationsentrén. Du jobbar ensam genom övningarna: feature-gren, push, Pull Request, egen granskning av diffen, Merge, `git switch main && git pull origin main`.

**Förkunskaper:** Inkapsling från [10-inkapsling](../../vecka-40/10-inkapsling/). Klass och objekt från [08-klasser-objekt](../../vecka-39/08-klasser-objekt/). Pull Request-flödet från [14-git-team](../14-git-team/).

**Omfång:** `src/Medlem.java`, `src/Register.java`, `src/Main.java`. Ett objekt: `new Medlem("Kim", 1001)`. Utskrift via `getNamn()` och `getMedlemsnummer()`. **Ingen** lista, **ingen** sökmetod, **ingen** Scanner, **ingen** meny, **inget** arv, **ingen** factory. **Ingen** omdöpning av Kontoappen.

---

## 🗺️ Körschema (vecka 42)

| Pass | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Git i team** | Max ~15 min: [01 — Teoriguide](../14-git-team/01-teoriguide.md) | Gemensamt repo, Pull Request, lokal synk | [14-git-team](../14-git-team/) |
| **Pass 2 — Tre klasser (denna mapp)** | Max ~15 min: [01 — Teoriguide](./01-teoriguide.md) (tre ansvar, `private`, tom `Register`) | Skelett, ett `Medlem`-objekt, getters | Välj ditt spår nedan (~3–5 h) |
| **Pass 3 — Merge och konflikt** | Max ~15 min: [01 — Teoriguide](../16-merge-konflikt/01-teoriguide.md) | Konflikt i en Pull Request, lös lokalt | [16-merge-konflikt](../16-merge-konflikt/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)

1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (`feature-skelett` → `feature-main-start` → `feature-medlemsnummer` → README fråga 2)
2. [ ] **Träna kritiskt tänkande:** [04 — AI-träning](./04-ai-traning.md)
3. [ ] **Kontrollera dina målsvar:** [05 — Självtest](./05-sjalvtest.md) utan facit först

[01 — Teoriguide](./01-teoriguide.md) är uppslagsverket om du kör fast.

---

### 🟡 2. Du missade passet eller börjar från noll (Ta ikapp-spåret)

1. [ ] **Förstå koncepten:** [01 — Teoriguide](./01-teoriguide.md) från start till mål
2. [ ] **Få överblick:** [02 — Visuellt](./02-visuell.md)
3. [ ] **Koda själv:** [03 — Övningar](./03-ovningar.md). Ingen partner behövs
4. [ ] **Granska och anpassa:** [04 — AI-träning](./04-ai-traning.md)
5. [ ] **Slutkontroll:** [05 — Självtest](./05-sjalvtest.md)

---

### 🟣 3. Du siktar på VG / vill fördjupa dig (Stretch)

Exam 2 ger IG/G. Stretch här stannar inom kursplanen:

- [ ] **Andra instansen:** `feature-andra-medlem` med `new Medlem("Moa", 1002)`, utskrift via getters, egen Pull Request. `Register` förblir tom. Se slutet av [03 — Övningar](./03-ovningar.md)
- [ ] **README-träning:** fråga 2 är redan uppgift 5. Skriv om den en gång till med egna exempel på två instanser, om stretch-grenen är mergad
- [ ] **En mening:** varför `Register.java` finns när klassen inte anropas

---

## 🗣️ Målsvar att kunna utantill inför examinationen

> **Tre ansvar:** "Medlem är databäraren, med private fält, konstruktor och getters. Register är samlingsägaren, tom i det här skedet. Main är applikationsentrén. Lösa namn och nummer i Main kan glida isär."

> **Inkapsling:** "new Medlem(\"Kim\", 1001) sätter fälten i konstruktorn. Main läser med getNamn och getMedlemsnummer. kim.namn kompilerar inte, och jag tar inte bort private."

> **Tom Register:** "Register.java är adressen för samlingen. Utan filen hamnar det ansvaret i Main."

> **Egen Pull Request:** "Jag pushar feature-grenen, läser diffen själv och klickar Merge. Sedan git switch main och git pull origin main, så nästa gren utgår från det som mergats."

> **Klass och objekt:** "Medlem är klassen, mallen. kim är objektet, instansen efter new."

> **Nytt projekt:** "Examination 2 är ett nytt projekt. Jag döper inte om Account till Medlem."

---

## 📝 Examination

Paketet träffar **Examination 2 (Medlemsregistret)**: tre filer, `Medlem` med private, konstruktor och getters, och svaret på README-fråga 2 (klass och objekt). Lista, sök och meny kommer senare: [17-lista-register](../../vecka-43/17-lista-register/), [18-sok-meny](../../vecka-43/18-sok-meny/). Git i grupp: [14-git-team](../14-git-team/), [16-merge-konflikt](../16-merge-konflikt/).

Brief: [examination_2_medlemsregistret.md](../../../examination_2_medlemsregistret.md).

## 🏁 Nästa steg

När målen sitter: [16-merge-konflikt](../16-merge-konflikt/). Därefter samlingen i `Register`: [17-lista-register](../../vecka-43/17-lista-register/).
