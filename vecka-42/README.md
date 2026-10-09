# Vecka 42 — Git i team + flerklassarkitektur

> **📖 Hur du använder detta material:** Detta GitHub-repo är din digitala kursbok. Klicka på länkarna i webbläsaren. Följ körschemat pass för pass.

**Block 2 startar här.** Exam 1 (Kontoappen) är klar. Nu: **nytt** grupprojekt — medlemsregistret. Ingen ny OOP — samma mönster, **svenska** namn.

---

## 🗺️ Veckans roadmap (pass för pass)

### Pass 1 — Git i team (gemensamt repo)
Mapp: [14-git-team](./14-git-team/)

* **Före passet:** Max ~15 min — [01 — Teoriguide](./14-git-team/01-teoriguide.md) (feature-gren, Pull Request, pull efter Merge).
* **Live i Teams:** Gemensamt repo (2–4), kort gren, PR och granskning, `git switch main && git pull origin main`.
* **Efter passet:**

> 🟢 **Du var med:** [03 — Övningar](./14-git-team/03-ovningar.md) → [05 — Självtest](./14-git-team/05-sjalvtest.md).

> 🟡 **Om du missade:** Hela kedjan i [14-git-team](./14-git-team/).

---

### Pass 2 — Tre klasser (`Medlem` / `Register` / `Main`)
Mapp: [15-tre-klasser](./15-tre-klasser/)

* **Före passet:** Max ~15 min — [01 — Teoriguide](./15-tre-klasser/01-teoriguide.md) (tre ansvar, `private`, tom `Register`).
* **Live i Teams:** Skelett tre filer + ett `Medlem`-objekt (ingen full sök ännu).
* **Efter passet:**

> 🟢 **Du var med:** [03 — Övningar](./15-tre-klasser/03-ovningar.md) → [05 — Självtest](./15-tre-klasser/05-sjalvtest.md).

> 🟡 **Om du missade:** Hela kedjan i [15-tre-klasser](./15-tre-klasser/).

---

### Pass 3 — Merge och konflikt (grundnivå)
Mapp: [16-merge-konflikt](./16-merge-konflikt/)

* **Före passet:** Max ~15 min — [01 — Teoriguide](./16-merge-konflikt/01-teoriguide.md) (samma rad, markörer, javac före push).
* **Live i Teams:** Röd Pull Request, städning i editorn, grön PR.
* **Efter passet / veckans mål:**

> 🟢 **Du var med:** [03 — Övningar](./16-merge-konflikt/03-ovningar.md) → [05 — Självtest](./16-merge-konflikt/05-sjalvtest.md).

> 🟡 **Om du missade:** Hela kedjan i [16-merge-konflikt](./16-merge-konflikt/).

---

## 🎯 Veckans checklista (klar inför vecka 43?)

- [ ] Vi har ett **gemensamt publikt** grupprepo (inte Exam 1-repot)
- [ ] Jag kan förklara **varför `git pull origin main` efter en Pull Request** (annars desynk)
- [ ] **Alla** i gruppen syns under Commits
- [ ] Tre filer finns: `Medlem.java`, `Register.java`, `Main.java` (svenska namn)
- [ ] `Medlem` har **private** + konstruktor + `getNamn` — och minst **ett** objekt skapas
- [ ] Jag kan förklara varför samma rad gör en Pull Request röd, och hur `git pull origin main` på feature-grenen tar ner staketen
- [ ] Vi har **dokumenterat** minst ett löst samarbetsproblem (träning inför Exam 2 README)

---

## 🏁 Nästa steg

Vecka 43 = [vecka-43/](../vecka-43/) — lista i Register ([17-lista-register](../vecka-43/17-lista-register/)), sedan sök + meny och start Exam 2.
