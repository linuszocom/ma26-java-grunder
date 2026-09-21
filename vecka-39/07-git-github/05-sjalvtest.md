# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför finns Git — vilket problem löser versionshantering jämfört med bara “Spara” i IDE:n?  
2. Vad är skillnaden mellan Git och GitHub på en mening?  
3. Vad är en **commit**?  
4. Vad gör `git add` som `git commit` *inte* gör?  
5. Du har committat men github.com är tomt under Commits. Vilket steg saknas — och varför räcker inte IDE-Spara?  
6. Beskriv metoden när du tvekar: ska jag spara i Git nu?  
7. Exam 1: vilka tre Git-krav måste ditt repo uppfylla (utöver själva Java-koden)?  
8. Varför är det fel att sätta Exam 1-repot till **Private** “för säkerhets skull”?  
9. Nämn två farliga AI-råd kring Git och varför du stryker dem (t.ex. force push, committa hemligheter, fel remote).  
10. Peka i *ditt* repo: nämn tre steg du körde (add/commit/push eller status) och **varför** — inte “AI sa åt mig”.

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. Utan versionshantering har du bara senaste filen på disken. Git sparar en historik av ögonblicksbilder så du (och examinationen) kan se *vad* som ändrats och *när*.  
2. **Git** = historik/journal på din dator. **GitHub** = kopian på nätet där andra och examinationen kan öppna fliken Commits.  
3. En commit = sparad ögonblicksbild + meddelande — en punkt i historiken (lokalt tills du pushar).  
4. **`add`** = välj vilka filer som ska med i *nästa* ögonblicksbild. **`commit`** = spara den bilden. Add laddar inte upp.  
5. **`git push`**. Spara i IDE:n = fil på disk, ingen GitHub-kopia och ingen synlig Commit-rad.  
6. (1) Liten, begriplig ändring? (2) `git status` / `git add` de filerna. (3) `git commit -m "…"` sedan `git push` och kolla **Commits**.  
7. Eget **publikt** repo, minst **5** commits, **begripliga** meddelanden (synliga under Commits efter push).  
8. Bedömningen ska öppna länken utan inbjudan. Privat repo blockerar eller försvårar inlämningen även om koden “finns”.  
9. Exempel: **`git push --force`** kan skriva över historik — stryk i det här flödet. **Committa `.env`/API-nycklar** — hemligheter fastnar i historiken. **Fel remote** — push till fel repo. **Private trots Exam** — fel leveransform. (Två räcker om de är korrekta.)  
10. Subjektivt — rimligt om du kopplar kommando → effekt. Fel om svaret bara är “AI skrev det” eller “jag klickade runt”.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna är gjorda, och du kan peka i eget repo:

- [ ] Målsvar varför Git finns — egna ord, högt  
- [ ] Målsvar commit — egna ord, högt  
- [ ] Målsvar metod (add → commit → push → Commits) — egna ord, högt  
- [ ] Publikt övningsrepo med synliga commits  
- [ ] Du kan förklara varför Exam 1 vill ha ≥5 begripliga commits  

Då har du landat Git-målet för Pass 1. Nästa paket i veckan: [`08-klasser-objekt`](../08-klasser-objekt/) (*publiceras i nästa del*). Behöver du Java-grunder: [vecka 38](../../vecka-38/).
