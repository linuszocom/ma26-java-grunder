# 01 — Teoriguide: samarbete i Git och GitHub

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt eller skriva i README. Tar du materialet från noll: läs klart, titta på [02 — Visuellt](./02-visuell.md), gör sedan [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du kan redan spara en commit och pusha ett eget repo. Det räckte när du var ensam. I en grupp på 2–4 personer är `main` ett dokument ni delar. Den här guiden handlar om hur en ändring får komma in där utan att skriva över någon annan.

**Omfång:** Ett gemensamt publikt repo. Korta feature-grenar. Pull Request med code review. Lokal synk efter Merge. `.gitignore` för `*.class`, `target/` och `.idea/`. En startkommentar i `src/Main.java`. **Ingen** konfliktlösning, **ingen** klass, **ingen** Scanner, **ingen** meny.

Förkunskapen sitter i [07-git-github](../../vecka-39/07-git-github/): `add`, `commit`, `push`, publikt repo, fliken Commits.

---

## Originalet får inte redigeras på plats

Många tänker: "Vi har ett repo. Jag pushar till `main`, så har alla min fil." Det är det snabbaste sättet att göra gruppens kopia opålitlig.

`main` på GitHub är den kopia nästa person klonar, och den historik en granskare läser. Ligger ett halvfärdigt försök där, är det försöket gruppens sanning. Ingen annan hann se raderna. Commit-meddelandet "update" säger inte vem som bestämde vad.

Två personer som pushar till samma `main` krockar också i praktiken. Den som är sist får avvisning, eller skriver över den andras arbete om hen tar till `--force`. Force kan ta bort commits som redan finns i den gemensamma historiken. Den knappen hör inte hemma i det här flödet.

**Vad det är:** Direktpush till `main` betyder att din dator skriver in i originalet utan att någon annan läst diffen.  
**Varför det är farligt:** Stabiliteten försvinner, eftersom ett experiment blir originalet direkt. Granskningen försvinner, eftersom ingen sett raderna. Historiken blir svår att lita på, eftersom det inte syns att en annan person godkände ändringen.  
**Vad som gäller i stället:** Du arbetar på en egen tidslinje. Originalet uppdateras först när en teammedlem godkänt diffen på GitHub.

**Målsvar (säg högt / skriv i README):** *"Jag pushar inte rakt till main. Ett experiment där skulle bli gruppens original utan att någon granskat raderna."*

---

## Den mentala modellen: original i arkiv, kopia på remiss

**Metafor:** Tänk ett **master-dokument i ett skyddat arkiv**. Originalet heter `main` och ligger på GitHub. Ingen går in i arkivet och suddar i originalet.

När du ska ändra något tar du ut en **arbetskopia på remiss**. Det är din feature-gren. Du skriver på kopian. Originalet ligger kvar, orört, medan kopian är ute.

Remissen är inte klar för att du är nöjd. Den ska tillbaka till arkivet med ett följebrev: vad som ändrats, och en kollega som läser raderna. Det följebrevet är en **Pull Request**. Först när kollegan godkänt och klickat Merge skrivs innehållet in i originalet.

Det arbetssättet kallas **feature-isolerad utveckling**: varje ändring lever på en egen tidslinje tills den är granskad.

**Vad det är:** `main` är originalet i arkivet. Feature-grenen är arbetskopian. Pull Requesten är remissen.  
**Varför den finns:** Gruppen ska kunna prova text och kod utan att originalet rör sig.  
**Om modellen saknas:** Alla skriver i samma kopia. Då finns ingen remiss, och ingen kan säga vilken version som gäller.

**Målsvar (säg högt / skriv i README):** *"main är originalet i arkivet. Jag skriver på en arbetskopia. En Pull Request är remissen, där en kollega läser raderna innan originalet uppdateras."*

---

## En feature-gren är en egen tidslinje

En gren är ett namn som pekar på en commit. En commit är ett sparat läge, med en förälder: committen som fanns innan. Kedjan av föräldrar är tidslinjen.

`main` pekar på originalets senaste commit. `feature-titel` pekar på en annan commit, den du skapade på arbetskopian. De två namnen kan peka på olika ställen samtidigt. Det är isoleringen.

När du står på feature-grenen och gör `git commit` flyttas bara den grenens pekare framåt. `main` står kvar. Originalet har inte sett din mening än.

`git switch -c feature/<namn>` gör två saker: skapar ett nytt namn, och ställer det namnet på den commit du står på just nu. Därför spelar startpunkten roll. Skapar du grenen från en gammal `main`, börjar den nya tidslinjen där den gamla kopian slutade.

I övningarna heter grenarna konkret `feature-titel`, `feature-medlemmar` och `feature-src-start`. Snedstrecket i mallen `feature/<namn>` är en namnkonvention. Bindestrecket i övningarna är samma sak: en kort gren för en avgränsad ändring.

**Vad det är:** En feature-gren är en pekare till en commit, och därmed en egen kedja av sparade lägen.  
**Varför den finns:** Så ditt försök kan pushas och granskas utan att `main` flyttar sig.  
**Om den saknas:** Committen hamnar på den gren du råkar stå på. Står du på `main`, är det originalet du just flyttade.

**Målsvar (säg högt / skriv i README):** *"En feature-gren är en egen tidslinje. Namnet pekar på en commit. Mina commits flyttar den pekaren, inte main."*

---

## En Pull Request är granskningen

När grenen finns på GitHub öppnar du en Pull Request mot `main`. Det är en sida i repot, inte ett kommando som kopierar filer åt dig.

Sidan är ett **diskussionsforum** och en **granskningsyta**. GitHub visar en **diff**: vilka rader som lagts till och vilka som tagits bort, fil för fil. En teammedlem läser den diffen. Hen kan kommentera en rad. Ser diffen rätt ut klickar hen **Merge pull request**.

Merge-klicket uppdaterar `main` **på GitHub**. Arbetskopian är då insläppt i arkivet. Din laptop har inte fått det beskedet ännu. Det kommer i nästa avsnitt.

Du mergar din egen Pull Request bara om gruppen uttryckligen bestämt det. I övningarna är regeln: den som inte skrev raderna klickar Merge.

**Vad det är:** En Pull Request är ett förslag att ta in en grens commits i `main`, med diffen synlig.  
**Varför den finns:** Code review sker innan originalet ändras. Gruppen ser exakt vilka rader som följer med.  
**Om den saknas:** Koden kan ligga på en gren som ingen läst, eller så har någon pushat rakt in i originalet.

**Målsvar (säg högt / skriv i README):** *"En Pull Request visar diffen rad för rad. En teammedlem läser och klickar Merge. Först då uppdateras main på GitHub."*

---

## Molnet och skrivbordet är två exemplar

Det här gapet kallas ibland *the cloud vs local gap*. Det är den vanligaste anledningen till att nästa uppgift "saknar" en fil som kompisen redan ser på webben.

Sekunden efter att Merge klickats finns två olika sanningar:

| | GitHub | Din dator |
| :--- | :--- | :--- |
| `main` | Har den nya committen | Har fortfarande den gamla committen |
| Pull Requesten | Stängd, mergad | Syns inte i dina filer förrän du hämtat |
| Var du står | Spelar ingen roll för molnet | Ofta kvar på feature-grenen |

`git switch main` byter bara vilken pekare du står på **lokalt**. Den hämtar ingenting. `git pull origin main` är hämtningen: Git läser `main` på GitHub och flyttar din lokala `main` dit.

Hoppar du över de två kommandona och kör `git switch -c` direkt, föds nästa feature-gren **i det förflutna**. Den pekar på din gamla `main`. Titel, teamsektion eller `src/Main.java` som redan finns i arkivet saknas på den nya tidslinjen. Nästa Pull Request ser då ut att ta bort arbete som gruppen redan godkänt, eller så saknas filen när du ska bygga vidare.

Båda i gruppen kör synken. Det räcker att en person pullar. Den som inte pullat startar sitt nästa arbete från ett gammalt original.

**Målsvar (säg högt / skriv i README):** *"Merge uppdaterar bara GitHub. Jag kör git switch main och git pull origin main. Utan det föds nästa feature-gren från en gammal main."*

---

## Sju steg, varje gång

Samma ordning för varje ändring efter att repot finns och alla har klonat.

1. **`git switch -c feature/<namn>`**  
   Ny tidslinje från den `main` du just pullat.

2. **Gör ändringen. `git add` på filen. `git commit -m "…"`**  
   Meddelandet säger vad som ändrades och vem du är. Exempel: `docs: projekttitel och syfte — Kim`.

3. **`git push -u origin feature/<namn>`**  
   `-u` kopplar din lokala gren till samma namn på GitHub. Nästa `git push` på den grenen vet vart den ska.

4. **Öppna en Pull Request på GitHub.**  
   Kort beskrivning: vilken fil, vad som ändrades, varför.

5. **Code review.**  
   En teammedlem öppnar diffen, läser raderna och klickar **Merge pull request**.

6. **`git switch main`**  
   Tillbaka till originalets namn på din dator.

7. **`git pull origin main`**  
   Hämta det arkivet nu innehåller. Båda gör steg 6 och 7.

Sedan får nästa person skapa sin gren. Inte innan.

**Målsvar (säg högt / skriv i README):** *"switch -c, add, commit med namn, push -u origin, Pull Request, en kollega mergar, switch main, pull origin main."*

---

## Det som aldrig får in i arkivet

Java-kompilatorn skriver `*.class`. Byggverktyg skriver `target/`. IntelliJ skriver `.idea/`. De filerna är resultat av din maskin, inte källkod gruppen ska läsa.

Committar du dem händer tre saker. Diffen fylls av binärt brus, så granskningen drunknar. En klasskompis får din IDE-konfiguration i sitt projekt. Nästa `javac` på en annan dator skriver över eller krockar med filer som inte borde vara delade.

`.gitignore` är en textfil i repots rot. Varje rad är ett mönster Git ska låta bli när du tittar efter nya filer. I det här projektet räcker tre rader:

```text
*.class
target/
.idea/
```

Ignore gäller filer som ännu inte är committade. Har en `.class` redan hamnat i historiken tar ignore inte bort den. Därför ska raderna finnas innan någon kompilerar.

**Målsvar (säg högt / skriv i README):** *".gitignore håller byggda filer och IDE-mappar borta. *.class, target/ och .idea/ är resultat på min dator, inte källkod gruppen delar."*

---

## Vanliga fallgropar

| Vad som hände | Vad som är fel | Vad du gör |
| :--- | :--- | :--- |
| Nästa gren saknar kompisen titel | Du pullade inte efter Merge. Grenen föddes från gammal `main` | `git switch main` och `git pull origin main`, skapa grenen igen från den |
| `git push origin main` | Originalet uppdaterades utan diff och utan review | Arbeta på en feature-gren och öppna en Pull Request |
| `git merge` i terminalen | Ni hoppade över granskningsytan på GitHub | Pusha grenen, öppna Pull Request, låt en kollega klicka Merge |
| `.class` eller `.idea/` i committen | Byggresultat och IDE-filer följde med | Lägg mönstren i `.gitignore`. Ta inte till `--force` för att städa historiken i det här flödet |
| Meddelandet är `update` | Historiken säger inte vad som ändrades eller vem som gjorde det | Skriv om i nästa commit: vad, och ditt namn |
| Du jobbar i Exam 1-mappen | Två examinationer delar historik | Klona gruppens nya repo. Det är ett nytt projekt |
| `src/` syns inte på GitHub | Git sparar filer, inte tomma mappar | Lägg kommentaren i `src/Main.java` och få in den via Pull Request |

---

## När du tvekar

1. `git status`. Vilken gren står du på?
2. `git pull origin main` på `main`, innan du skapar en ny gren.
3. En fil i taget i `git add`. Meddelande med vad och ditt namn.
4. `git push -u origin` plus grennamnet. Öppna Pull Request. Peka på diffen.
5. Efter Merge: `git switch main` och `git pull origin main`. Öppna filen på disk och jämför med GitHub.

**Målsvar (säg högt / skriv i README):** *"Jag förväntade mig att main på min dator matchade GitHub. Status och filen på disk visade något annat. Jag bytte till main, pullade, och kontrollerade att nästa gren utgick därifrån."*
