# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i anteckningar, privat, för dig. Sikta på målsvar du kan säga högt.

Sedan öppnar du facit och rättar dig.

---

## Frågor

1. Vad är skillnaden mellan `main` och en kort feature-gren?
2. Varför öppnar ni en **Pull Request** och låter en kollega göra **code review**, i stället för att pusha rakt till `main`?
3. Beskriv de sju stegen från `git switch -c` tills ändringen finns både på GitHubs `main` och på din dator.
4. Kollegan har klickat **Merge pull request**. Din README saknar fortfarande titeln. Vad har hänt, och vilka två kommandon kör du?
5. Vad händer om du skapar nästa feature-gren utan att pulla efter Merge?
6. Vad tittar du efter i `git log --oneline --graph`, och var på GitHub ska samma meddelanden synas?
7. Vad är skillnaden mellan ditt Exam 1-repo och gruppens gemensamma repo?
8. Vad menas med synlig medverkan under fliken **Commits**?
9. Du får *rejected* / *non-fast-forward* vid en push. Vad är den första tanken, och vad ska du låta bli?
10. Varför är Exam 2 ett nytt projekt? Vad får finnas i repot i det här paketet?
11. Varför ska `*.class`, `target/` och `.idea/` ligga i `.gitignore`?
12. Nämn två farliga AI-råd kring team-Git och varför du stryker dem.
13. Peka i ert grupprepo: en Pull Request, en pull efter Merge, och varför. Inte "AI sa åt mig".

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. `main` är originalet i arkivet, den kopia gruppen litar på. En feature-gren är en egen tidslinje: ett namn som pekar på en commit. Dina commits flyttar den pekaren. `main` står kvar tills en Pull Request mergats.
2. Pull Requesten visar diffen rad för rad. En kollega läser innan raderna blir originalet. Push rakt till `main` gör experimentet till gruppens sanning utan den granskningen.
3. `git switch -c feature/<namn>` → ändra, `git add`, `git commit -m "… — Namn"` → `git push -u origin feature/<namn>` → öppna Pull Request med kort beskrivning → kollegan läser diffen och klickar **Merge pull request** → `git switch main` → `git pull origin main`. I övningarna heter grenarna `feature-titel`, `feature-medlemmar` och `feature-src-start`.
4. Merge uppdaterade bara GitHub. Din dator har den gamla kopian. Kör `git switch main` och `git pull origin main`.
5. Den nya grenen utgår från din gamla `main`. Den föds i det förflutna. Arbete som redan finns i arkivet saknas på den tidslinjen. Nästa Pull Request kan se ut att ta bort det gruppen redan godkänt.
6. Varje rad är en commit. Namnet ska sitta i meddelandet. En skarv betyder att en gren mött `main`, ofta vid Merge, och är inte en konflikt i filen. Samma texter ska synas under **Commits**.
7. Exam 1 är ditt eget publika repo. Teamarbetet är ett gemensamt publikt repo, med feature-grenar och Pull Requests mot samma `main`. `git remote -v` ska peka på gruppens URL.
8. Alla i gruppen syns under **Commits**: egen commit, med namn i meddelandet, på `main` efter att Pull Requesten mergats. En omergad gren räknas inte som färdig.
9. Först: någon annan har commits du saknar, eller din lokala `main` är gammal. Hämta och förstå. Låt bli `git push --force`.
10. Exam 2 är en annan uppgift och ett grupparbete. Kopiera eller döp om Kontoappen blandar examinationerna. I det här paketet: `README.md` med titel, syfte och team, `.gitignore` med tre rader, och `src/Main.java` med en startkommentar. Ingen klass, ingen Scanner, ingen meny.
11. De är resultat på din dator: kompilerad kod, byggmapp och IDE-inställningar. I repot gör de diffen oläsbar och kan skriva över en kollegas lokala miljö. `.gitignore` ska finnas innan någon kompilerar.
12. Exempel: **push rakt till main** (ingen granskning), **`git merge` i terminalen** (ingen Pull Request), **"behöver inte pull efter Merge"** (nästa gren föds från gammal `main`), **`push --force`** (kan ta bort andras historik), **committa `.class`** (byggresultat hör inte hemma i arkivet). Två räcker om de är korrekta.
13. Rimligt om du pekar på en mergad Pull Request, säger vem som läste diffen, och kan säga att `git pull origin main` var det som fick din dator ikapp. Fel om svaret bara är "AI skrev det" eller "vi skickade filer i chatten".

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna är gjorda, och du kan peka i grupprepots:

- [ ] Målsvar om feature-gren och Pull Request, egna ord, högt
- [ ] Målsvar om gapet: `git switch main` och `git pull origin main` efter Merge, egna ord, högt
- [ ] Målsvar om `.gitignore`, egna ord, högt
- [ ] Målsvar om synlig medverkan, egna ord, högt
- [ ] Målsvar om nytt projekt, egna ord, högt
- [ ] Gemensamt publikt repo, minst en mergad Pull Request, minst en synlig commit kopplad till dig
- [ ] Alla i gruppen (2–4) syns under **Commits** efter pull

Då har du landat team-Git för det här paketet. Nästa paket i veckan: [`15-tre-klasser`](../15-tre-klasser/). Bakåt: Exam 1 i [vecka-41](../../vecka-41/).
