# 16 — Konflikt i en Pull Request

> **📖 Hur du använder materialet:** Detta GitHub-repo fungerar som din digitala kursbok. Du behöver inte klona något för att läsa. Klicka på länkarna i webbläsaren.

**Den här mappen täcker:** vecka 42, **Pass 3**. Två feature-grenar ändrar samma `println` i `src/Main.java`. GitHub spärrar den andra Pull Requesten. Du löser raden lokalt på feature-grenen, kör `javac`, och pushar så att Pull Requesten blir grön. Du jobbar ensam.

**Förkunskaper:** Pull Request och lokal synk från [14-git-team](../14-git-team/). `Medlem`, `Register` och `Main` från [15-tre-klasser](../15-tre-klasser/).

**Omfång:** `feature-valkomst-a`, `feature-valkomst-b`, `git pull origin main` på feature-grenen, tre konfliktmarkörer, `javac`, `git commit -m "fix: lös konflikt i välkomsttext"`, `git push`, Merge, `git switch main && git pull origin main`. README-avsnittet "Ett problem vi löste" på `feature-problem-doc`. **Ingen** rebase, **ingen** force, **ingen** Scanner, **ingen** lista, **ingen** ny klass.

---

## 🗺️ Körschema (vecka 42)

| Pass | Före passet (Förberedelse) | Live i Teams | Efter passet (Eget arbete) |
| :--- | :--- | :--- | :--- |
| **Pass 1 — Git i team** | Max ~15 min: [01 — Teoriguide](../14-git-team/01-teoriguide.md) | Gemensamt repo, Pull Request, lokal synk | [14-git-team](../14-git-team/) |
| **Pass 2 — Tre klasser** | Max ~15 min: [01 — Teoriguide](../15-tre-klasser/01-teoriguide.md) | Tre ansvar, ett `Medlem`-objekt | [15-tre-klasser](../15-tre-klasser/) |
| **Pass 3 — Konflikt (denna mapp)** | Max ~15 min: [01 — Teoriguide](./01-teoriguide.md) (samma rad, markörer, javac före push) | Röd Pull Request, städning i editorn, grön PR | Välj ditt spår nedan (~3–5 h) |

---

## 🎯 Välj din väg i materialet

### 🟢 1. Du var med på live-passet (Repetition & Praktik)

1. [ ] **Bygg med fingrarna:** [03 — Övningar](./03-ovningar.md) (två grenar, lokal städning, grön Pull Request, README)
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

- [ ] I README-avsnittet: skriv vilken mening som låg under `HEAD` och vilken som låg under `origin/main`, och varför den sidan är den
- [ ] Peka i `git log --oneline --graph` på mötet och säg vilka två commits som krockade
- [ ] En mening om varför `javac` sitter före `git push` även när GitHub redan skulle kunna bli grön

---

## 🗣️ Målsvar att kunna utantill inför examinationen

> **Samma rad:** "Olika rader kan en Pull Request merga själv. Samma println är två påståenden. Git gissar inte. Jag väljer meningen."

> **Markörerna:** "Efter git pull origin main på feature-grenen är HEAD min gren. Under likamed-raden ligger origin/main. Jag tar bort de tre staketraderna."

> **Grön Pull Request:** "Jag städar i editorn, kör javac, add, commit och push. Då blir Pull Requesten grön och kan mergas. Webbläsaren kompilerar inte koden."

> **Efter Merge:** "Merge uppdaterar GitHub. Jag kör git switch main och git pull origin main innan nästa gren."

> **Dokumentation:** "Ett problem vi löste nämner src/Main.java, samma println, att GitHub spärrade Pull Requesten, markörerna, javac och pushen som gjorde den grön."

---

## 📝 Examination

Paketet träffar **Examination 2**, stycket **Ett problem vi löste**, och frågan om hur ni versionshanterade utan att skriva över varandra. Brief: [examination_2_medlemsregistret.md](../../../examination_2_medlemsregistret.md).

## 🏁 Nästa steg

När målen sitter: [17-lista-register](../../vecka-43/17-lista-register/). Pull Request-flödet igen: [14-git-team](../14-git-team/). Klasserna: [15-tre-klasser](../15-tre-klasser/).
