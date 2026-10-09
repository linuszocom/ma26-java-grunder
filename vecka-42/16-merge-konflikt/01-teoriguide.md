# 01 — Teoriguide: när två påståenden gäller samma rad

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt eller skriva i README. Tar du materialet från noll: läs klart, titta på [02 — Visuellt](./02-visuell.md), gör sedan [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du kan redan öppna en Pull Request, läsa diffen och hämta hem `main`. Den här guiden tar nästa fall: två grenar har ändrat **samma rad**, och GitHub vägrar merga den andra Pull Requesten. Du löser det på din dator, i `src/Main.java`, och pushar så att Pull Requesten blir grön.

Du jobbar ensam. De två grenarna är två tidslinjer som du själv skapar från samma bas.

**Omfång:** En `println` i `src/Main.java`. Konfliktmarkörer. `javac` innan push. Avsnittet "Ett problem vi löste" i `README.md`. **Ingen** rebase, **ingen** force, **ingen** Scanner, **ingen** lista, **ingen** ny klass. `Medlem.java` och `Register.java` lämnas orörda.

**Förkunskaper:** [14-git-team](../14-git-team/) och skelettet i [15-tre-klasser](../15-tre-klasser/).

---

## Samma rad kräver ett val

Git och GitHub kan sammanfoga mycket utan att fråga dig.

Olika filer går ihop. `README.md` på en gren och `src/Medlem.java` på en annan blir båda kvar på `main`. Olika rader i samma fil går också ihop, så länge raderna inte ligger på varandra.

Samma rad är ett annat läge. Gren A säger att raden ska vara en mening. Gren B säger att samma rad ska vara en annan mening. Båda påståendena utgår från samma äldre rad. Versionshanteringen har inget tredje fakta att luta sig mot. Den **vägrar gissa**. En människa måste skilja: vilket påstående som ska stå kvar.

Det är skiljedom, inte ett fel i Git. Historiken behåller båda commits. Filen som committas efteråt innehåller ett av påståendena, eller en ny mening du skriver själv. Markörerna får inte följa med.

**Målsvar (säg högt / skriv i README):** *"Olika rader kan en Pull Request merga själv. Samma rad är två påståenden. Git gissar inte. Jag väljer meningen."*

---

## Så blir Pull Requesten röd

Båda grenarna skapas från samma commit på `main`.

1. `feature-valkomst-a` byter en `println` till `Välkommen till Klubbens Register!`, pushas, och mergas. Den meningen är nu originalet på GitHub.
2. `feature-valkomst-b` skapades från samma bas, innan den mergade meningen fanns på den lokala `main`. Den byter **samma** `println` till `Medlemsregister v1.0`.
3. Pull Requesten för B jämförs med GitHubs `main`. GitHub skriver: *This branch has conflicts that must be resolved.*

Knappen Merge är då spärrad. Inget är trasigt i repot. De två tidslinjerna har lämnat två oförenliga påståenden om en rad, och arkivet tar inte in B förrän raden är avgjord.

Skapar du B efter att du redan pullat A:s merge finns det ingen krock. B utgår då från meningen som redan ligger på `main`, och den andra meningen skrivs aldrig.

**Målsvar (säg högt / skriv i README):** *"Jag mergar första Pull Requesten. Den andra, från samma bas, ändrar samma println. GitHub spärrar den tills jag avgjort raden."*

---

## Skiljedomen sker där programmet kan köras

GitHub kan visa en knapp för att lösa konflikten i webbläsaren. Den ytan kompilerar inte Java. Du ser text, men du kan inte köra `javac` där. En grön Pull Request betyder att Git är nöjd med historiken. Den betyder inte att programmet startar.

Därför står du kvar på `feature-valkomst-b` och drar in originalet:

```text
git pull origin main
```

`pull` hämtar `main` från GitHub och försöker lägga in den i grenen du står på. På den här raden stannar den. Terminalen skriver ungefär:

```text
CONFLICT (content): Merge conflict in src/Main.java
```

Filen på disk får markörerna. Du läser dem i editorn, väljer, städar, och kör programmet. Sedan committar och pushar du **grenen**. Pull Requesten jämförs på nytt. När konflikten är borta blir den grön, och du kan klicka **Merge pull request**.

**Målsvar (säg högt / skriv i README):** *"Jag löser konflikten på feature-grenen, med git pull origin main, för att jag ska kunna köra javac innan jag pushar."*

---

## De tre markörerna

Efter `git pull origin main` på `feature-valkomst-b` ser raden ut ungefär så här:

```text
<<<<<<< HEAD
        System.out.println("Medlemsregister v1.0");
=======
        System.out.println("Välkommen till Klubbens Register!");
>>>>>>> origin/main
```

| Rad | Vad den är |
| :--- | :--- |
| `<<<<<<< HEAD` | Övre staketet. Allt under den, fram till likamed-raden, är grenen du står på. `HEAD` är `feature-valkomst-b`. |
| `=======` | Gränsen mellan de två påståendena. |
| `>>>>>>> origin/main` | Nedre staketet. Texten ovanför den, under gränsen, är `main` som drogs in. Etiketten kan vara `origin/main` eller en commit-hash. Det är A:s mening, den som redan mergats. |

Sju mindre-än-tecken, sju likamed, sju större-än. De är inte Java. Ligger de kvar kompilerar filen inte.

Du läser båda meningarna. Du behåller en. Du kan också skriva en ny mening om ingen av dem ska gälla. Sedan tar du bort de tre staketraderna, så att filen bara innehåller vanlig kod.

**Målsvar (säg högt / skriv i README):** *"HEAD är grenen jag står på. Under likamed-raden ligger main som jag drog in. Jag tar bort de tre staketraderna och lämnar en println."*

---

## Från städad fil till grön Pull Request

Ordningen efter att du valt mening:

1. Spara `src/Main.java`. Inga `<`, `=` eller `>` från markörerna får ligga kvar.
2. `javac src/*.java && java -cp src Main`. Konsolen visar meningen du valde. Programmet kraschar om ett staket eller en trasig rad ligger kvar.
3. `git add src/Main.java`
4. `git commit -m "fix: lös konflikt i välkomsttext"`
5. `git push`
6. På GitHub är Pull Requesten grön. Klicka **Merge pull request**.
7. `git switch main && git pull origin main`
8. `git log --oneline --graph`

Steg 2 sitter före push med flit. GitHub blir grön av att konflikten är committad, även om `println`-raden är sönder. `javac` är beviset att skiljedomen gick att köra.

`git add` gäller bara `src/Main.java`. En `*.class` från provkörningen hör hemma i `.gitignore`, inte i committen.

Steg 7 behövs även när du mergat din egen Pull Request. Merge uppdaterar GitHub. Nästa gren, den för README, utgår från din lokala `main`. Utan pull saknar den både lösningen och historiken.

**Målsvar (säg högt / skriv i README):** *"Jag städar, kör javac, add, commit, push. Då blir Pull Requesten grön. Efter Merge kör jag git switch main och git pull origin main."*

---

## Vad README ska kunna berätta

Examination 2 ber om ett stycke i stil med **Ett problem vi löste**: vad som strulade, och hur det löstes. I det här paketet är svaret konkret.

Nämn filen `src/Main.java`, att det var samma `println`, att GitHub spärrade Pull Requesten, att `git pull origin main` skrev markörerna, att du läste båda meningarna, tog bort de tre staketraderna, körde `javac`, och pushade så att Pull Requesten blev grön.

"Vi fixade Git" räcker inte. En läsare ska kunna peka på filen och på kommandona.

---

## Vanliga fel

| Vad du ser | Vad som hänt | Vad du gör |
| :--- | :--- | :--- |
| Pull Requesten kan mergas direkt | Gren B skapades efter att A:s merge redan låg på din lokala `main`, eller ni ändrade olika rader | Gör om från samma bas. Byt samma `println`, inte en ny rad under |
| Du löste texten i webbläsaren | Programmet är inte kört | Avbryt den webblösningen om den inte är committad. Städa i editorn och kör `javac` |
| `javac` klagar på `<` | Ett staket ligger kvar | Ta bort de tre raderna. Spara. Kompilera igen |
| Konsolen är tom eller kraschar | Meningen följde med när staketen raderades | Skriv tillbaka en `println`. Kompilera igen |
| Nästa gren saknar lösningen | Du mergade och glömde pull | `git switch main && git pull origin main` |
| Någon föreslår `--force` eller rebase | Det skriver om historiken | Låt bli. Add, commit, push på feature-grenen |

---

## När du tvekar

1. Vilken gren står du på? Det ska vara `feature-valkomst-b` när du kör `git pull origin main`.
2. Vilken mening står under `HEAD`, och vilken står under `origin/main`?
3. Har `javac` gått igenom innan `git push`?
4. Är Pull Requesten grön innan du klickar Merge?
5. Har du pullat `main` innan du skriver README-avsnittet?

När målsvaren sitter: [02 — Visuellt](./02-visuell.md).
