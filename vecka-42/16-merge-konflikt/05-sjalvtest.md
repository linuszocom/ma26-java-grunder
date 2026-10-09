# 05 — Självtest

Svara först utan facit. Skriv i anteckningar. Sikta på meningar du kan säga högt.

Öppna facit efteråt och rätta dig.

---

## Frågor

1. När kan GitHub merga en Pull Request själv, och när spärrar den den?
2. Hur skapar du krocken med två grenar från samma bas, när du jobbar ensam?
3. Vad betyder de tre raderna `<<<<<<< HEAD`, `=======` och `>>>>>>> origin/main` när du står på `feature-valkomst-b` och har kört `git pull origin main`?
4. Varför löser du inte konflikten i GitHubs webbläsare?
5. Vilken ordning gäller från städad fil till grön Pull Request?
6. Varför kör du `javac` innan `git push`?
7. Pull Requesten är mergad. Din lokala `src/Main.java` har fortfarande den gamla meningen. Vilka kommandon kör du?
8. Vad händer om du skapar `feature-valkomst-b` efter att du redan pullat A:s merge?
9. `javac` stannar och pekar på ett `<`. Vad ligger kvar i filen?
10. Vad ska avsnittet "Ett problem vi löste" innehålla för att duga inför Examination 2?
11. Nämn två AI-råd du stryker, och varför.
12. Peka i ditt repo: den spärrade Pull Requesten, committen som löste den, och meningen som blev kvar.

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. Olika filer och olika rader kan GitHub sammanfoga. Samma rad är två påståenden om en cell i filen. Versionshanteringen vägrar gissa. Pull Requesten får texten *This branch has conflicts that must be resolved*.
2. Från en ren `main`: `feature-valkomst-a` byter `println`, pushas och mergas. Utan att pulla den mergade `main` skapar du `feature-valkomst-b` från samma bascommit och byter samma `println` till den andra meningen. B:s Pull Request blir då röd.
3. `HEAD` är grenen du står på, så den övre meningen är `Medlemsregister v1.0`. Likamed-raden är gränsen. Under den ligger `main` som drogs in, A:s mening. Etiketten är ofta `origin/main` eller en hash. De tre staketraderna ska bort. En `println` ska vara kvar.
4. Webbläsaren kompilerar inte Java. Du ser texten, men du kan inte köra `javac` där. Skiljedomen sker i editorn, på feature-grenen.
5. Spara den städade filen. `javac src/*.java && java -cp src Main`. `git add src/Main.java`. `git commit -m "fix: lös konflikt i välkomsttext"`. `git push`. När Pull Requesten är grön: **Merge pull request**.
6. GitHub blir grön när Git-konflikten är borta, även om raden inte kompilerar. `javac` är beviset att meningen går att köra, innan den pushas.
7. `git switch main && git pull origin main`. Merge uppdaterade bara GitHub. Utan pull föds nästa gren, till exempel `feature-problem-doc`, från den gamla lokala `main`.
8. B utgår från meningen som redan ligger på `main`. Det finns bara ett påstående om raden. Pull Requesten kan mergas, och du får ingen konflikt att träna på.
9. Ett staket ligger kvar, oftast `<<<<<<< HEAD`. Ta bort de tre markörraderna, spara, kompilera igen. Skriv tillbaka `println` om den följde med i raderingen.
10. Filen `src/Main.java`, att det var samma `println`, att GitHub spärrade Pull Requesten, att `git pull origin main` skrev markörerna, att du läste båda meningarna, tog bort de tre staketraderna, körde `javac`, och pushade så att Pull Requesten blev grön. "Vi fixade Git" ensamt räcker inte.
11. Exempel: lös i webbläsaren (ingen `javac`), `git push --force` (kan ta bort historik), rebase, `git merge` på `main` i stället för den gröna Pull Requesten, Scanner eller en ny klass (hör inte till den här raden). Två räcker om de är rätt.
12. Rimligt om du pekar på `feature-valkomst-b`, på committen `fix: lös konflikt i välkomsttext`, och på en `println` utan staket. Fel om svaret är "AI klickade" eller om markörerna ligger kvar i filen på `main`.

</details>

---

## Klart för paketet?

- [ ] Målsvar om samma rad och skiljedom, egna ord, högt
- [ ] Målsvar om `HEAD` och `origin/main`, egna ord, högt
- [ ] Målsvar om `javac` före push, egna ord, högt
- [ ] Målsvar om pull efter Merge, egna ord, högt
- [ ] En Pull Request som var spärrad och sedan mergades grön
- [ ] `src/Main.java` på `main` har en välkomstmening och inga staket
- [ ] README har avsnittet "Ett problem vi löste"
- [ ] AI-träningen har minst fyra FEEDBACK-rader

Nästa paket: [17-lista-register](../../vecka-43/17-lista-register/). Behöver du repetera Pull Request-flödet: [14-git-team](../14-git-team/). Klasserna: [15-tre-klasser](../15-tre-klasser/).
