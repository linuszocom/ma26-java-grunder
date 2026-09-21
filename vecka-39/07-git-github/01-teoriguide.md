# 01 — Teoriguide: Git & GitHub (eget repo)

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **vad som går sönder** när du bara trycker Spara i IDE:n — sedan bygger vi upp hur du tar en riktig ögonblicksbild och får den till GitHub. Det är inte magi. Det är en metod.

**Omfång:** Individuell Git. `git add`, `git commit`, `git push`. Publikt repo. Fliken Commits. **Ingen** `git pull`, **inget** grupprepo, **inga** branches eller pull requests, **ingen** OOP i den här guiden.

---

## Problemet först — “jag sparade ju i IDE:n”

Många tänker nu: “`Main.java` ligger i projektet. Det räcker.” Andas.

**Dåligt läge:** Du har ett litet Java-program. Du sparar. Datorn dör, du byter laptop, eller du ska lämna Exam 1 — och på GitHub finns **ingenting**. Eller: filerna finns, men historiken är en enda commit med meddelandet `asdf`, så ingen (inklusive du om tre veckor) förstår vad som hände.

Det är två olika problem:

1. **Ingen versionshistorik** — bara “senaste filen på disken”.  
2. **Ingen synlig leverans** — Exam 1 kräver ett **publikt** repo där fliken **Commits** visar minst **5** begripliga commits.

Git löser (1). GitHub + ärliga meddelanden + push löser (2).

**Målsvar (säg högt / skriv i README) — varför Git finns:**  
*“Utan versionshantering har jag bara 'senaste filen på disken'. Git sparar en historik av ögonblicksbilder så jag (och examinationen) kan se vad som ändrats och när.”*

---

## Verkstadens journal — metaforen för hela paketet

**Metafor:** Tänk en **verkstad**. På bänken ligger dina Java-filer (det du jobbar med just nu). Vid sidan har du en **lokal journal** där du stämplar varje färdig delmoment: *vad* du just låste, *när*, och en kort rad om *vad som ändrats*. Det är **Git**.

I kontorets **arkivskåp** ligger samma journal synlig för andra — och för den som bedömer Exam 1. Det är **GitHub**. Du flyttar inte arkivet genom att spara i IDE:n. Du **stämplar** (commit) och **lämnar in till arkivet** (push).

**Vad det är:** Versionshantering = spåra ändringar över tid, inte bara “senaste läget”.  
**Varför det finns:** Så du kan återvända till en känd punkt, förklara historiken, och lämna in något som går att granska.  
**Om det saknas / vad det INTE är:** Det är INTE “Spara” i IntelliJ/VS Code. Det är INTE magi i molnet. Det är INTE grupparbete, pull eller PR i det här paketet.

---

## Git vs GitHub — lokal journal vs arkivskåp

**Vad det är:**  
- **Git** = verktyget och historiken **på din dator**.  
- **GitHub** = tjänsten på nätet där en **kopia** av historiken kan synas publikt.

**Varför skillnaden finns:** Du kan stämpla lokalt utan att något syns på github.com. Examinationen tittar på **GitHub**, inte på din hårddisk.

**Om det saknas / vad det INTE är:** Git ≠ GitHub. Utan `push` finns stämplarna bara hos dig. GitHub är INTE samma sak som att skapa en mapp i IDE:n. GitHub är heller INTE “jag har konto” — kontot räcker inte utan repo + commits + push.

**Målsvar (säg högt / skriv i README):**  
*“Git sparar historiken på min dator. GitHub är kopian på nätet där examinationen kan öppna fliken Commits.”*

---

## Repository — projektet under journalen

**Vad det är:** Ett **repo** (repository) = projektmappen **plus** Git-historiken.  
**Varför det finns:** Annars vet Git inte *vilket* projekt du stämplar i.  
**Om det saknas:** Felmeddelandet `not a git repository` betyder: du står i fel mapp, eller mappen är inte kopplad till Git än. Det är INTE att “Git är trasigt”.

Två vanliga sätt att få ett repo:

1. Skapa ett **tomt publikt** repo på GitHub → **`git clone`** URL:en (hämtar mappen + kopplingen dit).  
2. Har du redan en projektmapp: `git init` + koppla `remote` till ditt GitHub-repo — samma kedja efteråt.

**Identitet:** `git config user.name` och `user.email` = namnet/mejlen som syns på *dina* commits. Utan dem blir historiken anonym eller varnande. Det är INTE samma sak som att vara inloggad på github.com i webbläsaren.

**Publikt vs privat:** Exam 1 kräver **publikt** repo så länken går att öppna utan inbjudan. Ett privat repo kan se “rätt” ut hos dig — och ändå vara fel för inlämningen.

**Målsvar (säg högt / skriv i README) — repo:**  
*“Ett repo är projektet under Git: filerna plus historiken. Exam 1 ska ligga i mitt egna publika GitHub-repo.”*

---

## Kedjan — tre knappar, inte en

Många tänker: “Jag vill bara få upp det på GitHub.” Stopp. Det är tre steg med olika jobb — plus en koll före och efter.

| Steg | Kommando | Vad det är (+ bild) | Varför | Om saknas / INTE |
|------|----------|---------------------|--------|------------------|
| Kolla | `git status` | Titta i journalen: vad är nytt, vad är valt | Du gissar inte | INTE samma sak som push |
| Välj | `git add …` | Lägg filer i “att stämpla”-facket | Du styr innehållet | INTE att spara ögonblicksbilden än |
| Spara | `git commit -m "…"` | Stämpla + skriv raden i journalen | Historiken ska gå att läsa | Fortfarande **lokalt** — INTE GitHub |
| Publicera | `git push` | Bär journalen till arkivskåpet | Annars syns inget på github.com | INTE samma sak som Spara i IDE:n |
| Verifiera | Fliken **Commits** | Titta i arkivet | Exam tittar här | INTE “filerna syns i Code” räcker ensamt |

**Problem först:**

- Bara `commit` utan `add` → ofta `nothing to commit` (facket är tomt).  
- Bara `add` utan `commit` → filerna är valda men ingen punkt i historiken.  
- Bara `commit` utan `push` → du har stämplar lokalt, men GitHub (och Exam 1) ser dem inte.  
- `push` utan commits → ofta inget nytt att skicka, eller fel remote.

**Målsvar (säg högt / skriv i README) — commit:**  
*“En commit är en sparad ögonblicksbild av projektet med ett meddelande om vad som ändrats. Den blir en punkt i historiken — fortfarande på min dator tills jag pushar.”*

**Målsvar (säg högt / skriv i README) — kedjan:**  
*“Add väljer, commit sparar ögonblicksbilden, push skickar den till GitHub. Sedan kollar jag fliken Commits.”*

---

## Commit-meddelanden — raden i journalen

**Vad det är:** Texten efter `-m` — en kort beskrivning av *denna* ändring.  
**Varför det finns:** Historiken ska gå att skumma. Exam 1 kräver begripliga meddelanden, inte bara “att det finns commits”.  
**Om det saknas / vad det INTE är:** `fix`, `asdf`, `fix` säger ingenting. Det är INTE platsen för lösenord, tokens eller personnummer.

Bra exempel:

```text
git commit -m "Lägg till Main.java med HelloWorld"
git commit -m "Ändra utskrift till namn + hälsning"
git commit -m "Lägg till README med körinstruktion"
```

Dåligt exempel:

```text
git commit -m "fix"
git commit -m "asdf"
git commit -m "fix 2"
```

---

## Metod — när du tvekar “ska jag spara i Git nu?”

Det är inte magi. Fyra frågor:

1. **Har jag en liten, begriplig ändring?** (en grej du kan beskriva i en mening — inte hela Exam 1 på en gång)  
2. **`git status`** — vad är nytt?  
3. **`git add` just de filerna.** Kolla `status` igen.  
4. **`git commit -m "tydligt meddelande"`** → **`git push`** → öppna **Commits** på GitHub.

**Vad metoden är:** Ett sätt att bygga historik utan att dumpa allt eller glömma push.  
**Varför den finns:** Exam 1 bedömer synlig historik (≥5 commits), inte bara att zip:en “finns någonstans”.  
**Om den saknas:** Du pushar aldrig, gör en enda jättecommit, eller lämnar privat repo.

**Målsvar (säg högt / skriv i README) — metod:**  
*“Har jag en liten, begriplig ändring? Då: git add de filerna, git commit med tydligt meddelande, sedan git push — och jag verifierar under Commits på GitHub.”*

---

## Publikt repo + fliken Commits — vad Exam 1 tittar på

**Vad det är:** På github.com öppnar du ditt repo → fliken **Commits**. Där syns meddelande, författare och tid för varje stämpel.  
**Varför det finns:** Inlämningen är en **länk**. Bedömningen ska kunna öppna historiken utan din laptop.  
**Om det saknas / vad det INTE är:** Det räcker INTE att “filerna syns under Code”. Det räcker INTE med privat repo. Det räcker INTE med en commit som heter `final`.

**Klart-bild för Exam 1 (Git-delen):**

- Eget repo (inte gruppens)  
- **Publikt**  
- Minst **5** commits  
- Begripliga meddelanden  
- Synliga under **Commits** efter push

**Målsvar (säg högt / skriv i README) — Exam Git:**  
*“Exam 1 lämnas som mitt egna publika GitHub-repo. Under Commits ska det synas minst fem commits med meddelanden som går att förstå.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Spara i IDE:n = versionshanterat | Spara = fil på disk. Git = stämpel/commit. GitHub = efter push |
| Git och GitHub är samma sak | Git lokalt, GitHub på nätet |
| `git add` = uppladdning | Add = välj. Commit = spara. Push = skicka |
| Meddelandet `update` / `asdf` | Skriv vad som ändrades |
| Privat repo “för säkerhets skull” | Exam 1 kräver publikt — annars går länken inte att öppna |
| En jättecommit i slutet | Bygg historik successivt (≥5) |
| Kör Git i fel mapp | `cd` in i projektmappen först. `status` när du är osäker |
| Branches, merge, pull, PR “för att göra rätt” | Inte i det här paketet. Repo + kedjan räcker |
| Lägga `.env`, lösenord, API-nycklar i commit | Aldrig. Historiken sparar dem |
| `git push --force` för att “fixa” | Farligt. Lös problem utan att skriva över historik du inte förstår |

---

## Mini-exempel — samma Java-fil, tre stämplar

Tänk att du börjar med:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

Commit 1: `"Lägg till Main.java med Hello-utskrift"`  
Sedan ändrar du texten till en hälsning med namn → commit 2.  
Sedan lägger du till en `README.md` → commit 3.

Varje gång: spara i IDE:n → `status` → `add` → `commit` → `push` → kolla **Commits**.

Det är **samma** kedja du senare använder när projektet har fler `.java`-filer — bara fler filer. Tekniken är densamma.

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Varför finns Git? (sikta på målsvaret)  
2. Skillnad Git vs GitHub i en mening  
3. Vad gör `add`, vad gör `commit`, vad gör `push`?  
4. Var tittar Exam 1 (publikt + Commits + ≥5)?  
5. Metodens steg när du tvekar

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
