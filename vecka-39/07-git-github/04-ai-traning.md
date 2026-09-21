# 04 — AI-träning: Git-kedjan & ägarskap

AI kan klistra in Git-kommandon på sekunder. Det betyder inte att *du* äger historiken. Här tränar du samma färdighet som Exam 1 kräver: **se vad som är svagt eller farligt, ändra, förklara**.

Det är inte magi att “granska AI”. Det är samma metod som i teoriguiden — status → add → commit → push → Commits.

---

## Scenario — problem först

Du ber AI: *“Hjälp mig lägga upp mitt Java-projekt på GitHub inför examinationen.”*  
Du får tillbaka något i stil med:

```text
git init
git add .
git commit -m "update"
git branch -M main
git remote add origin https://github.com/någon/okänt-repo.git
git push -u origin main --force
git checkout -b feature/account
echo "API_KEY=sk-hemlig123" >> secrets.env
git add secrets.env
git commit -m "config"
# "Sätt repot till Private så ingen stjäl koden"
```

Det *kan* råka “fungera” tekniskt. Det är ändå **svagt eller farligt** mot det här paketets krav:

| AI-råd | Varför det är svagt / farligt |
|--------|-------------------------------|
| `git add .` | Tar **allt** i mappen — ibland skräp, build-mappar, hemligheter |
| `"update"` / `"config"` | Säger ingenting i historiken |
| `git push --force` | Kan **skriva över** historik. Använd inte “för att fixa” om du inte förstår konsekvensen |
| Fel `origin`-URL | Push till någon annans (eller påhittat) repo |
| Branch / checkout | Hör **inte** hit — extra knappar du inte behöver försvara |
| Commita `secrets.env` / API-nycklar | Hemligheter hamnar i historiken — svåra att ta bort |
| “Sätt Private” | Exam 1 kräver **publikt** repo — privat = fel leveransform |

**Vad du tränar:** Feedback på AI-råd + en kedja *du* äger.  
**Varför:** Exam 1 och muntligt kräver att *du* kan peka: add vs commit vs push, publikt vs privat, och varför force/secrets är fel.  
**Vad det INTE är:** “AI sa force push, alltså är det proffsigt.”

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt till AI (eller jobba bara mot snutten ovan utan ny AI) där du ber om hjälp att publicera ett enkelt Java-`Main`-projekt. Spara prompten.

### Steg 2 — Granska (checklist)
Gå igenom svaret (AI:ns eller snutten) och kryssa:

- [ ] Tar `add` *specifika* filer — eller `.` / hela världen?  
- [ ] Är commit-meddelandet konkret?  
- [ ] Finns **force push**? (Stryk om du inte har ett mycket tydligt, säkert skäl — i det här paketet: stryk.)  
- [ ] Finns steg som **commitar hemligheter** (`.env`, nycklar, lösenord)?  
- [ ] Föreslås **privat** repo trots Exam 1 publikt?  
- [ ] Pekar `remote`/`clone` på **ditt** repo?  
- [ ] Finns steg du **inte** behöver (branch, merge, pull request, `pull`)?  
- [ ] Förklaras skillnaden Git vs GitHub — eller bara en kommandolista?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst fyra** konkreta feedback-punkter i formen:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Kör (eller skriv upp) en **ren kedja du äger** mot *ditt* övningsrepo från [03](./03-ovningar.md) — eller ett nytt mini-repo:

- Publikt repo  
- Specifika filer i `add` (t.ex. `Main.java`, eventuellt `README.md`)  
- Tydligt meddelande  
- Vanlig `git push` (**inte** `--force`)  
- Inga hemligheter i commit  
- Inga branches / PR / pull  

Spara kommandona du faktiskt körde i `GIT-KEDJA.md` i mappen (en lista, **inga** tokens/lösenord).

### Steg 4 — Reflektion (4 meningar)
Skriv i anteckningar eller samma `GIT-KEDJA.md`:

1. Vad var fel eller farligt i AI-förslaget (eller snutten)?  
2. Vad ändrade du?  
3. Varför är publikt repo + begripliga commits viktigt inför Exam 1?  
4. Varför är force push och commitade hemligheter dåliga idéer även “bara för övning”?

---

## Klart-check (peka i DITT repo)

- [ ] Fyra FEEDBACK-rader sparade  
- [ ] Peka på en commit på GitHub och säg *varför* meddelandet duger  
- [ ] Peka på något du *tog bort* från AI-listan — varför behövdes det inte / varför var det farligt?  
- [ ] Reflektionens fyra meningar klara  
- [ ] Repot är **publikt** (eller du kan förklara varför övningsrepot är publikt inför Exam-vanan)

---

## Facit-riktning (titta efter du granskat själv)

Exempel på giltig feedback (dina egna ord får skilja sig):

- `FEEDBACK: git add . → lägg bara till de filer jag menar, t.ex. Main.java.`  
- `FEEDBACK: meddelandet "update" → skriv vad som ändrades.`  
- `FEEDBACK: push --force → stryk; vanlig push räcker och är säkrare här.`  
- `FEEDBACK: secrets.env / API-nyckel → committa aldrig hemligheter.`  
- `FEEDBACK: Private-repo → Exam 1 ska vara publikt.`  
- `FEEDBACK: origin-URL:en är inte mitt repo → clone/push mot min GitHub-adress.`  
- `FEEDBACK: branch/checkout → stryk; repo + add/commit/push räcker här.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-förslag som utkast, granskar kommando för kommando, och behåller bara det jag kan förklara — utan force push, utan hemligheter, med publikt repo när examinationen kräver det.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
