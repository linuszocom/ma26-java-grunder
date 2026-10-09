# 03 — Övningar: grupprepo, Pull Request, lokal synk

**Omfång:** Ett gemensamt publikt repo för 2–4 personer. Collaborators. Feature-grenar. Pull Request med code review. `git switch main && git pull origin main` efter varje Merge. `.gitignore` med tre rader. `src/Main.java` med en startkommentar. **Ingen** klass, **ingen** Scanner, **ingen** meny, **ingen** konfliktmarkör.

**Roller:** Bestäm Person A och Person B innan ni börjar. Byt inte mitt i en uppgift. Har ni 3–4 personer gör de uppgift 5 så att varje namn syns under **Commits**.

**Regel efter varje Merge:** Båda kör synken och öppnar filen på sin dator. Nästa gren skapas först då.

---

## Uppgift 1 — Grunden och behörigheter

**Mål:** Gruppen har ett publikt repo, alla kan klona det, och `.gitignore` finns innan någon kompilerar.

**Scenario:** Exam 2 är ett nytt projekt. Ni återanvänder inte Exam 1-repot och ni byter inte namn på `Account`.

**Krav:**

1. En person skapar repot på GitHub. **Public**. Kryssa i att en README ska skapas, så att `main` finns.
2. **Settings → Collaborators.** Bjud in resten av gruppen. Var och en accepterar inbjudan.
3. Alla klonar, med SSH eller HTTPS. Använd gruppens URL, inte ditt Exam 1-repo.

```text
git clone <url-till-gruppens-repo>
cd <mappnamnet>
git remote -v
```

4. `git remote -v` ska visa två rader, `fetch` och `push`, båda med `origin` och gruppens adress.
5. Samma person som skapade repot lägger `.gitignore` i roten via GitHubs webb (**Add file → Create new file**), med exakt dessa rader, och committar den till `main`. Det här är uppstartsfilen, innan någon har en egen gren. Från och med uppgift 2 går varje ändring via Pull Request.

```text
*.class
target/
.idea/
```

6. Alla hämtar hem filen:

```text
git switch main && git pull origin main
```

Öppna `.gitignore` på disk. Tre rader ska ligga där.

**Klart-check (peka i ERT repo och i DIN terminal):**

- [ ] Repot är publikt och alla står som Collaborators
- [ ] `git remote -v` pekar på gruppens URL, inte på Exam 1
- [ ] `.gitignore` innehåller `*.class`, `target/` och `.idea/` både på GitHub och på din dator

---

## Uppgift 2 — Första Pull Requesten (Person A)

**Mål:** Titel och syfte kommer in i originalet via granskning, och bådas datorer har samma `main` efteråt.

**Scenario:** README som GitHub skapade är nästan tom. Person A skriver vad projektet är. Person B läser diffen.

**Krav:**

1. Båda står på en uppdaterad `main` (uppgift 1, steg 6).
2. Person A:

```text
git switch -c feature-titel
```

3. I `README.md`: en projekttitel och en mening om syftet (medlemsregistret, nytt projekt). Spara.
4. Commit med ditt namn. Pusha så att grenen får en spårbar koppling på GitHub:

```text
git add README.md
git commit -m "docs: projekttitel och syfte — Namn"
git push -u origin feature-titel
```

5. På GitHub: **Compare & pull request**. Skriv en kort beskrivning: vilken fil, vad som lades till. Öppna Pull Requesten mot `main`.
6. Person B öppnar **Files changed**, läser diffen rad för rad och klickar **Merge pull request**.
7. Båda:

```text
git switch main && git pull origin main
```

Öppna `README.md` på disk. Titel och syfte ska synas utan att du tittar på webben.

**Klart-check:**

- [ ] Pull Requesten för `feature-titel` är mergad. Person B kan säga vad diffen innehöll
- [ ] `main` på GitHub och `README.md` på bådas datorer visar samma titel
- [ ] Ingen push gick till `main` från terminalen

---

## Uppgift 3 — Rollbyte och andra Pull Requesten (Person B)

**Mål:** Teamsektionen byggs ovanpå den titel som redan finns i arkivet.

**Scenario:** Person B äger nästa remiss. Person A granskar. Startar B från en gammal `main` saknas titeln på den nya grenen.

**Krav:**

1. Bekräfta att uppgift 2:s pull är gjord. `README.md` på disk har titeln.
2. Person B:

```text
git switch main && git pull origin main
git switch -c feature-medlemmar
```

3. Lägg en sektion i `README.md` med teamets namn. Skriv inte om titeln.
4. Commit, push, Pull Request:

```text
git add README.md
git commit -m "docs: teamsektion — Namn"
git push -u origin feature-medlemmar
```

5. Kort beskrivning på Pull Requesten. Person A läser diffen och klickar **Merge pull request**.
6. Båda:

```text
git switch main && git pull origin main
```

**Klart-check:**

- [ ] Grenen skapades efter pull, så titeln fanns redan i filen
- [ ] Person A mergade. Diffen visar teamsektionen och lämnar titeln kvar
- [ ] Bådas `README.md` på disk har titel och team

---

## Uppgift 4 — Projektstart för Java (Person A)

**Mål:** `src/Main.java` finns i originalet, med en kommentar och inget mer. Grafen visar mötena.

**Scenario:** Git sparar filer, inte tomma mappar. Kommentaren är det som gör att `src/` följer med. Klasser, Scanner och meny kommer senare.

**Krav:**

1. Båda har pullat efter uppgift 3. Person A:

```text
git switch main && git pull origin main
git switch -c feature-src-start
```

2. Skapa `src/Main.java` med bara en kommentar, till exempel:

```java
// Medlemsregistret. Startpunkt. Inga klasser i den här filen ännu.
```

3. Commit, push, Pull Request. Person B läser diffen och mergar.

```text
git add src/Main.java
git commit -m "docs: startkommentar i src/Main.java — Namn"
git push -u origin feature-src-start
```

4. Båda synkar och läser grafen:

```text
git switch main && git pull origin main
git log --oneline --graph
```

**Klart-check:**

- [ ] `src/Main.java` på disk är en kommentar. Ingen `class`, ingen `main`-metod, ingen Scanner
- [ ] Filen syns på GitHub under `main`
- [ ] `git log --oneline --graph` visar flera commits. Namn sitter i meddelandena. En skarv betyder att en gren mött `main`, oftast vid Merge

---

## Uppgift 5 — Stretch / tredje person

**Mål:** Varje person i gruppen har minst en egen commit som är mergad och syns under **Commits**.

**Scenario:** Är ni 2 räcker ofta A:s och B:s commits från uppgift 2–4. Är ni 3–4 saknas någon tills hen ägt en egen remiss.

**Krav:**

1. Den som ännu inte syns under **Commits** kör `git switch main && git pull origin main`.
2. Ny kort gren, till exempel `feature-readme-detalj`. En konkret detalj i `README.md`: en mening om hur gruppen jobbar, eller vem som granskar vems Pull Request. Rör inte `src/Main.java`.
3. `git push -u origin` plus grennamnet. Pull Request med kort beskrivning. En annan person läser diffen och klickar **Merge pull request**.
4. Alla:

```text
git switch main && git pull origin main
```

5. Öppna fliken **Commits** på GitHub. Läs namnen i meddelandena.

**Klart-check:**

- [ ] Varje gruppmedlem pekar på minst en mergad commit med sitt namn
- [ ] Den committen ligger på `main`, inte bara på en omergad gren
- [ ] `git log --oneline --graph` på din dator visar samma meddelanden efter pull

---

## När hela sviten är klar

- [ ] Ni kan säga de sju stegen utan att läsa innantill
- [ ] Ni kan förklara varför nästa gren blir fel om pullen hoppas över
- [ ] `.gitignore` har de tre raderna, och ingen `.class` ligger i repot
- [ ] Exam 1-repot är orört

Nästa: [04 — AI-träning](./04-ai-traning.md).
