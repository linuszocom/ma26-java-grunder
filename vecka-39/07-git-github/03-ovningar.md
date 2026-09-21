# 03 — Övningar

**Omfång det här paketet:** Eget publikt GitHub-repo, `git add` → `git commit` → `git push`, verifiera fliken **Commits**. En enkel Java-`Main` (HelloWorld eller liknande) så kedjan har något att spara.

**Gör inte här:** `git pull`, grupprepo, branches, pull requests, klasser/objekt (`Account` kommer senare).

AI får hjälpa dig knappa kommandon. Du måste kunna **peka och förklara** varje steg du kör.

---

## Uppgift 1 — Rädda “det ligger ju i IDE:n”

**Mål:** Förstå problemet när Spara ≠ GitHub. Köra kedjan tills Java-filen syns på github.com och under **Commits**.

**Problem först:** Du har (eller skapar) den här klassen lokalt. Den *finns* i IDE:n. Den finns **inte** som commit och **inte** på GitHub. Det är läget du ska ta dig ur.

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hej från verkstaden");
    }
}
```

**Krav:**
1. Skapa ett **nytt publikt** repo på GitHub (t.ex. `fornamn-java-git-ovning`). Gärna **utan** README först, så clone ger en tom mapp — eller skapa med README om du hellre kopplar via `remote` senare.
2. Antingen:
   - `git clone` URL:en och öppna mappen i IDE:n, **eller**
   - skapa projektmappen lokalt → `git init` → koppla `remote` till ditt repo.
3. Sätt `user.name` och `user.email` om de saknas (`git config --global …`).
4. Skapa `Main.java` med innehållet ovan (eller egen hälsning — samma idé).
5. Kör: `git status` → `git add` → `git commit -m "…"` → `git push`.
6. Öppna github.com: filen syns **och** fliken **Commits** visar meddelandet + ditt namn.

**Commit-meddelande:** konkret, t.ex. `"Lägg till Main.java med konsolhälsning"` — inte `fix` / `asdf`.

**Klart-check (peka i DITT flöde):**
- [ ] Repo-URL fungerar i webbläsaren (publikt)  
- [ ] Peka: vilket kommando var *välj*, vilket var *spara ögonblicksbild*, vilket var *skicka* — och *varför* den ordningen  
- [ ] Peka i **Commits**: meddelandet går att förstå  
- [ ] Du kan säga skillnaden Git vs GitHub i en mening  

**Ägarskap:**
- Utan AI: skriv kommandona själv.  
- Med AI: tillåtet som bollplank — spara prompten och **en mening** om vad du ändrade om AI gissade fel. Du ska kunna förklara varje kommando.

---

## Uppgift 2 — Andra stämpeln (och gärna en tredje)

**Mål:** Upprepa kedjan. Träna meddelanden. Bygga historik som liknar Exam 1 (≥5 commits totalt över tid — här börjar du med 2–3).

Många tänker nu: “En commit räcker för alltid.” Nej. En begriplig ändring = en ny stämpel i journalen.

**Brief A (andra commit):** Ändra utskriften i `Main.java` (t.ex. lägg till ditt förnamn i hälsningen). Spara i IDE:n.

**Brief B (stretch / tredje commit):** Lägg till en kort `README.md` i samma repo med tre meningar: (a) vad en commit är, (b) Git vs GitHub, (c) varför Exam 1 kräver publikt repo + synlig historik. Egna ord.

**Krav:**
1. För varje brief: ändra → spara → `status` → `add` → `commit -m "…"` → `push`.  
2. Minst **två** commits syns under **Commits** (helst tre om du gör stretch).  
3. Meddelanden beskriver *vad* som ändrades.  
4. I anteckningar: tre meningar — (a) vad en commit är, (b) varför push behövdes *igen*, (c) var Exam 1 tittar (publikt + Commits + ≥5).

**Exempel på bra meddelanden:**
- `"Uppdatera hälsning med förnamn i Main"`
- `"Lägg till README med Git-målsvar"`

**Klart-check (peka i DIN historik):**
- [ ] Minst två synliga commits under **Commits**  
- [ ] Inget meddelande är `asdf` / `fix` / `final`  
- [ ] Anteckningarnas tre meningar är *dina* ord  
- [ ] (Stretch) Tredje commit + README syns på GitHub  

**Ägarskap:** Samma regel som uppgift 1. Om AI skriver meddelandena åt dig: skriv om dem så *du* kan stå för dem.

---

## Uppgift 3 — Stretch (valfritt): sikta mot fem

Exam 1 vill ha **minst 5** commits. Fortsätt i samma övningsrepo med små, begripliga steg, t.ex.:

1. Lägg till en andra `println` (eller en kommentar som förklarar `main`).  
2. Byt hälsningstexten igen.  
3. Fyll på README med en rad: “Så kör jag: Run i IDE:n”.

Varje steg = egen commit + push. Räkna under **Commits**.

**Klart-check:** Kan du öppna Commits och peka på fem rader med meddelanden du förstår? Då har du Exam-Git i mini-format.

---

## När du kört fast

1. `git status` — läs vad den faktiskt säger.  
2. Kör metoden högt: liten ändring? add? commit? push? Commits?  
3. Jämför med [01-teoriguide](./01-teoriguide.md) — särskilt tabellen och målsvaren.  
4. Autentisering / “failed to push”: det är inloggning eller fel remote — inte att kedjan i sig är fel. Logga in på github.com, kolla URL:en, kör `push` igen.  
5. `not a git repository`: fel mapp — `cd` till projektmappen.  
6. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
