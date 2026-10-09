# 04 — AI-träning: Git i team och ägarskap

AI kan klistra in Git-kommandon på sekunder. Det betyder inte att du äger den delade historiken. Här tränar du samma färdighet som Exam 2 kräver: **se vad som är svagt eller farligt i team, ändra, förklara**.

Metoden är densamma som i [01 — Teoriguide](./01-teoriguide.md) och [03 — Övningar](./03-ovningar.md): kort feature-gren, `git push -u origin`, Pull Request, en kollega som läser diffen och klickar Merge, sedan `git switch main` och `git pull origin main`.

---

## Scenario — problem först

Du ber AI: *"Vi är tre i gruppen och ska sätta upp GitHub inför medlemsregistret. Snabbaste vägen?"*  
Du får tillbaka något i stil med:

```text
cd ~/exam1-kontoappen
git remote set-url origin https://github.com/gruppen/medlemsregister.git
git switch main
git add .
git commit -m "update"
git push origin main
# "Skippa Pull Request — det är bara en README, merga lokalt i stället:"
git merge feature-titel
git push origin main
# "När kompisen redan klickat Merge på webben behöver du inte pull.
#  Din dator hänger med automatiskt."
# "Byt namn så ni slipper skriva om:"
# Account.java → Medlem.java  (sök-ersätt Account → Medlem)
git add src/*.class
git push --force
# "Skippa Collaborators — skicka zip i chatten i stället"
# "Skippa .gitignore — .class-filerna visar att koden kompilerar."
```

Det kan råka se ut att fungera för en person. Det är ändå svagt eller farligt mot det här paketets krav.

| AI-råd | Varför det är svagt eller farligt |
| :--- | :--- |
| Push rakt till `main` | Originalet i arkivet ändras utan remiss och utan att någon läst diffen |
| `git merge` i terminalen, utan Pull Request | Code review på GitHub hoppas över |
| "Slipper pull efter Merge" | Knappen uppdaterar bara GitHub. Nästa gren föds från gammal `main` |
| `git push --force` | Kan ta bort andras commits ur den gemensamma historiken |
| `git add src/*.class` och "skippa .gitignore" | Byggresultat och IDE-filer följer med. Diffen blir oläsbar |
| Jobba kvar i Exam 1-mappen och bara byta remote | Blandar två examinationer |
| Döpa om `Account` till `Medlem` | Exam 2 är ett nytt projekt |
| `git add .` och meddelandet `update` | Tar allt och säger ingenting om vem som gjorde vad |
| Zip i chatten i stället för Collaborators | Ingen gemensam historik. Exam 2 tittar på **Commits** |

**Vad du tränar:** Feedback på AI-råd, plus en kedja du äger.  
**Varför:** Du ska kunna förklara hur gruppen versionshanterade utan att läsa innantill ur chatten.  
**Vad kedjan är:** Feature-gren, push med `-u`, Pull Request, Merge på webben, lokal pull. `.gitignore` med `*.class`, `target/` och `.idea/`. `src/Main.java` är en kommentar, inte en klass.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt

Skriv en egen prompt till AI (eller jobba bara mot snutten ovan) där du ber om hjälp att sätta upp **grupprepo, feature-gren och Pull Request** för ett nytt projekt. Spara prompten.

### Steg 2 — Granska

Gå igenom svaret och kryssa:

- [ ] Föreslås **push rakt till `main`** utan feature-gren? (Stryk.)
- [ ] Föreslås **`git merge` i terminalen** eller att hoppa över Pull Request? (Stryk.)
- [ ] Saknas **code review** — att en kollega läser diffen innan Merge? (Lägg till.)
- [ ] Saknas **`git switch main` och `git pull origin main` efter Merge**? (Lägg till.)
- [ ] Finns **force push**? (Stryk.)
- [ ] Föreslås commit av **`*.class`**, `target/` eller `.idea/`? (Stryk. De tre raderna ska ligga i `.gitignore`.)
- [ ] Föreslås **rename Account → Medlem** eller att kopiera Kontoappen? (Stryk.)
- [ ] Pekar flödet på **gruppens** repo, eller på någons Exam 1-mapp?
- [ ] Finns Collaborators och gemensam clone, eller zip i chatten?
- [ ] Är commit-meddelanden konkreta, med namn?
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst fyra** konkreta punkter i formen:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa

Skriv en ren kedja du äger, mot gruppens repo från [03 — Övningar](./03-ovningar.md):

- Publikt gemensamt repo, Collaborators, `git remote -v` mot gruppens URL
- `.gitignore` med `*.class`, `target/` och `.idea/`
- `git switch -c feature-namn` från en `main` du just pullat
- Specifik fil i `git add`. Meddelande med vad och ditt namn
- `git push -u origin feature-namn`
- Pull Request med kort beskrivning. En kollega läser diffen och klickar **Merge pull request**
- `git switch main && git pull origin main`
- `src/Main.java` innehåller en startkommentar, ingen klass
- Vanlig push av **grenen**. Inte `--force`. Inte push av `main` som genväg

Spara kommandona i `GIT-TEAM.md` i er mapp. En lista. Inga tokens eller lösenord.

### Steg 4 — Reflektion (4 meningar)

Skriv i anteckningar eller i samma fil:

1. Vad var fel eller farligt i AI-förslaget?
2. Vad ändrade du?
3. Varför räcker det inte att kompisen klickat Merge, om du inte pullar?
4. Varför ska `*.class` inte in i det gemensamma repot?

---

## Klart-check (peka i DITT grupprepo)

- [ ] Fyra FEEDBACK-rader sparade
- [ ] Du pekar på en mergad Pull Request och säger vem som läste diffen
- [ ] Du pekar på något du tog bort från AI-listan och säger varför
- [ ] Reflektionens fyra meningar är skrivna
- [ ] Du kan säga målsvaret om gapet mellan GitHub och din dator högt

---

## Facit-riktning (titta efter du granskat själv)

Exempel på giltig feedback. Dina egna ord får skilja sig.

- `FEEDBACK: push origin main → nej, kort gren och git push -u origin feature-namn.`
- `FEEDBACK: git merge i terminalen → öppna Pull Request, låt en kollega klicka Merge pull request.`
- `FEEDBACK: "behöver inte pull efter Merge" → git switch main och git pull origin main, annars föds nästa gren från gammal main.`
- `FEEDBACK: push --force → stryk. Kan ta bort andras commits.`
- `FEEDBACK: git add src/*.class → stryk. Lägg *.class, target/ och .idea/ i .gitignore.`
- `FEEDBACK: rename Account → Medlem → nej, nytt projekt.`
- `FEEDBACK: jobba i exam1-kontoappen och byt remote → clone gruppens nya repo.`
- `FEEDBACK: meddelandet "update" → skriv vad som ändrades och ditt namn.`
- `FEEDBACK: zip i chatten → Collaborators och gemensam historik under Commits.`

**Målsvar (säg högt / skriv i README):** *"Jag tar emot AI-förslag som utkast. Jag stryker push rakt till main, merge i terminalen, glömd pull, force push och commit av .class. Jag behåller bara en kedja jag kan förklara: feature-gren, push -u, Pull Request, Merge, switch main, pull."*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
