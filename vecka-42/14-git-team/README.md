# 14 — Git i team (feature-gren och Pull Request)

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa — klicka på länkarna i webbläsaren.

**Den här mappen täcker:** vecka 42, **Pass 1** — gemensamt grupprepo, korta feature-grenar, Pull Request med code review, och lokal synk med `git switch main && git pull origin main`. **Nytt** projekt (inte Kontoappen).

**Förkunskaper:** Individuell Git (`add` → `commit` → `push`, publikt repo) från [07-git-github](../../vecka-39/07-git-github/). Exam 1 är klar: [13-exam-1](../../vecka-41/13-exam-1/) / [vecka-41](../../vecka-41/).

**Omfång:** Grupp **2–4**. Ett gemensamt publikt repo. Flöde: `git switch -c feature-namn` → ändra, `add`, `commit` med namn → `git push -u origin feature-namn` → Pull Request på GitHub → en kollega läser diffen och klickar **Merge pull request** → `git switch main && git pull origin main`. `.gitignore` med `*.class`, `target/` och `.idea/`. `src/Main.java` med en startkommentar. Alla syns under **Commits**. **Ingen** konfliktmarkör-lösning, **ingen** klass, **ingen** Scanner, **ingen** meny, **ingen** Account-kopia.

**Flipped:** Ja — skumma [01 — Teoriguide](./01-teoriguide.md) max ~15 min före passet.

---

## 🗺️ Körschema (vecka 42)

| Pass | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Git i team (denna mapp)** | Max ~15 min: [01 — Teoriguide](./01-teoriguide.md) (feature-gren, Pull Request, pull efter Merge) | Gemensamt repo, Collaborators/clone, kort gren, PR, granskning, lokal synk | Välj ditt spår nedan (~3–5 h) |
| **Pass 2 — Tre klasser** | Max ~15 min: [01 — Teoriguide](../15-tre-klasser/01-teoriguide.md) | Ansvar mellan filer, `Medlem`-mur | [15-tre-klasser](../15-tre-klasser/) |
| **Pass 3 — Merge & konflikt** | Max ~15 min: [01 — Teoriguide](../16-merge-konflikt/01-teoriguide.md) | Undvik överskrivning, dokumentera löst problem | [16-merge-konflikt](../16-merge-konflikt/) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)
*Om du hängde med på skärmen och förstod koncepten:*
1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (Collaborators och `.gitignore` → `feature-titel` → `feature-medlemmar` → `feature-src-start` → `git log --oneline --graph`)
2. [ ] **Träna kritiskt tänkande:** [04 — AI-träning](./04-ai-traning.md)
3. [ ] **Kontrollera dina målsvar:** [05 — Självtest](./05-sjalvtest.md) utan facit först  
*( [01 — Teoriguide](./01-teoriguide.md) som uppslagsverk bara om du kör fast.)*

---

### 🟡 2. Du missade passet eller börjar från noll (Ta ikapp-spåret)
*Om du var sjuk, hade förhinder eller känner att team-Git inte sitter:*
1. [ ] **Förstå koncepten:** [01 — Teoriguide](./01-teoriguide.md) från start till mål
2. [ ] **Få överblick:** [02 — Visuellt](./02-visuell.md)
3. [ ] **Koda själv:** [03 — Övningar](./03-ovningar.md) med din grupp (2–4)
4. [ ] **Granska & anpassa:** [04 — AI-träning](./04-ai-traning.md)
5. [ ] **Slutkontroll:** [05 — Självtest](./05-sjalvtest.md)

---

### 🟣 3. Du siktar på VG / vill fördjupa dig (Stretch)
*Exam 2 ger IG/G — stretch här = mer teamvana, inom kursplanen:*
- [ ] **Stretch i övningarna:** är ni 3–4 gör varje person som ännu inte syns en egen kort feature-gren och Pull Request (uppgift 5), så att **alla** har en mergad commit under **Commits** — se [03 — Övningar](./03-ovningar.md)
- [ ] **README-träning:** tre meningar i gruppens repo: (a) varför en kort feature-gren, (b) varför `git pull origin main` efter att Pull Requesten mergats, (c) hur ni ser att alla syns i historiken
- [ ] **Dokumentera:** klistra in grupprepo-URL + skärmdump/lista av namn under **Commits** i anteckningar

---

## 🗣️ Målsvar att kunna utantill inför examinationen

När Pass 1 är klart ska du kunna återge dessa med egna ord:

> **Feature-gren och Pull Request:** "main är originalet i arkivet. Jag skriver på en feature-gren, pushar med git push -u origin och öppnar en Pull Request. En kollega läser diffen och klickar Merge. Jag pushar inte rakt till main."

> **Pull efter Merge:** "Merge uppdaterar bara GitHub. Utan git switch main och git pull origin main föds nästa feature-gren från en gammal main."

> **Gitignore:** "*.class, target/ och .idea/ är resultat på min dator. De ska ligga i .gitignore, inte i committen."

> **Synlig medverkan:** "I det gemensamma repot syns jag under Commits — egen commit, med mitt namn i meddelandet."

> **Nytt projekt:** "Exam 2 är ett nytt projekt. Vi kopierar inte Kontoappen och byter inte namn på Account — vi startar rent för medlemsregistret."

---

## 📝 Examination

**Exam 2 (Medlemsregistret)** är **grupp** (2–4). Ett **gemensamt publikt** GitHub-repo. **Alla** ska synas under **Commits**. Flöde: kort feature-gren → `push -u origin` → Pull Request → granskning och Merge på GitHub → `git switch main && git pull origin main`. Det du tränar här — gemensam historik, granskning innan originalet rörs, lokal synk efter Merge, `.gitignore`, nytt repo — är samma Git-krav som examinationen använder (tre klassfiler kommer i Pass 2; konflikt-dokumentation i Pass 3).

Brief (när du behöver den): [examination_2_medlemsregistret.md](../../../examination_2_medlemsregistret.md).

---

## 🏁 Nästa steg

När Pass 1-målen sitter: Pass 2 [`15-tre-klasser`](../15-tre-klasser/). Bakåt: Exam 1 stängd i [vecka-41](../../vecka-41/).
